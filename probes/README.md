# Probes: When a Query Returns Nothing

An empty result means one of two things. The condition is not happening, which is the answer you want. Or the query cannot see the data it needs, and the empty result tells you nothing. Before trusting an empty result during an incident, spend two minutes proving the data is there.

Work down the probes in order. Stop at the first one that fails; that is your problem.

## P-1 — Is the instance's telemetry reaching this search head?

```spl
| tstats latest(_time) as last_event count
    where (index=_internal OR index=_introspection OR index=_audit) earliest=-1h
    by index host
| eval minutes_ago=round((now() - last_event) / 60, 1)
| sort index host
```

Every instance an entry depends on (cluster manager, peers, license manager, deployment server, forwarders) must appear here for `_internal`. A missing host, or one with a large `minutes_ago`, is not forwarding its internal logs. Most queries in this book will return nothing for it. Fix `outputs.conf` on that instance first.

## P-2 — Can your role read the internal indexes?

```spl
| rest splunk_server=local /services/authentication/current-context
| table username roles
```
```spl
| eventcount summarize=false index=_internal index=_audit index=_introspection
| stats sum(count) as events by index
```

The second search returns nothing for an index your role cannot search. The `user` role cannot read `_internal`, `_audit`, or `_introspection` by default. Run the book's queries as an admin-level role, or add those indexes to your role's `srchIndexesAllowed`.

## P-3 — Is the component or message on your version spelled the way the query expects?

```spl
index=_internal sourcetype=splunkd earliest=-24h "<keyword from the query>"
| stats count by component log_level
| sort - count
```

Component names and message wording change between Splunk versions. Put a distinctive word from the query in the quotes (`replication`, `bundle`, `maintenance`, `freeze`) and see which components actually log it on your version. If the component differs from the one in the query, substitute yours.

## P-4 — Are the field names what the query expects?

```spl
index=_internal sourcetype=<sourcetype> earliest=-1h
| head 1
| transpose 0
| rename column as field, "row 1" as value
```

For `_introspection` sources, use `index=_introspection component=<component>`. Fields under `data.*` are the ones the book's queries read. A query that uses a field your version does not produce returns blank columns or nothing at all.

## P-5 — Does the REST endpoint exist here, and what does it return?

```spl
| rest splunk_server=local <endpoint from the query> count=1
| transpose 0
| rename column as field, "row 1" as value
```

An error means the endpoint does not exist on this instance. Usually the query is being run on the wrong server: cluster endpoints only answer on the cluster manager, license endpoints on the license manager, `deployment/server` endpoints on the deployment server. An empty result means the endpoint exists but has nothing to report.

## Ready-made probes

The companion repository has a probe for every entry (`probes/<ID>-probe.spl`). It checks each data source the entry reads and returns one row per source marked `OK` or `MISSING`, plus a field listing for every REST endpoint the entry calls. The table below lists the same data sources for use offline.
