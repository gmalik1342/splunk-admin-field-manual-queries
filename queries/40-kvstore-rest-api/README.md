# KV Store & REST API Troubleshooting (KV)

Queries from the **KV Store & REST API Troubleshooting** section of *Splunk Administrator Field Manual*.

| ID | Use case | Files |
|---|---|---|
| KV-01 | Lookups backed by the KV Store return nothing, apps show KV Store errors, or the bulletin board says the KV Store is not ready; check status on every search head and flag any member not in ready. | [main](KV-01a-kv-store-status-across-every-member.spl) · [b](KV-01b-kv-store-status-across-every-member.spl) |
| KV-02 | KV Store-backed lookups return different results depending on which search head serves the request; measure replication lag across the SHC replica set and identify the stale member. | [main](KV-02-kv-store-replication-lag-between-shc-members.spl) |
| KV-03 | The KV Store status is failed or stuck in starting after a restart or upgrade; find the reason mongod exited or refused to start. | [main](KV-03-why-crashed-restarted-or-will-not-start.spl) |
| KV-04 | The KV Store data directory is growing, initial sync takes hours, or memory use on the search head keeps climbing; rank collections by size and by growth over the last week. | [main](KV-04-largest-and-fastest-growing-kv-store-collections.spl) |
| KV-05 | Lookups against KV Store collections time out or dashboards that use them are slow; find the slow operations, the collections they hit, and whether mongod is queueing on locks. | [main](KV-05a-slow-kv-store-operations-and-lock-contention.spl) · [b](KV-05b-slow-kv-store-operations-and-lock-contention.spl) |
| KV-06 | Confirm who ran a KV Store backup or restore, when, and whether it finished, especially after collections lost data or reverted to old contents. | [main](KV-06-kv-store-backup-and-restore-audit.spl) |
| KV-07 | The management port is busy and splunkd is slow to answer; profile REST API traffic to see which users, client IPs, and endpoints generate the load. | [main](KV-07-rest-api-traffic-by-user-client-and.spl) |
| KV-08 | Integrations report REST errors or the UI shows intermittent failures; find when 4xx and 5xx responses spiked, which endpoints returned them, and which clients received them. | [main](KV-08-spikes-in-rest-4xx-and-5xx-responses.spl) |
| KV-09 | A setting changed without a ticket; trace configuration changes made through the REST API (conf files, inputs, indexes, server settings, app installs) back to the user and client that made them. | [main](KV-09-configuration-changes-made-through-rest.spl) |
| KV-10 | Audit Splunk authentication tokens: who created them, which are unused or never expire, which belong to disabled users, and when each was last used. | [main](KV-10a-authentication-tokens-created-used-expiring.spl) · [b](KV-10b-authentication-tokens-created-used-expiring.spl) |
| KV-11 | Senders report HEC errors or data from HEC stops arriving; break down HEC failures by reply code, token, and source IP to see whether the problem is the token, the data, or the indexers. | [main](KV-11-http-event-collector-failures.spl) |
| KV-12 | Splunk Web pages and REST calls are slow but searches are fine; find which management-port endpoints respond slowest and which callers send the most expensive requests. | [main](KV-12-slow-rest-endpoints-on-the-management-port.spl) |
