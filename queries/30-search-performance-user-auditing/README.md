# Search Performance & User Auditing (SR)

Queries from the **Search Performance & User Auditing** section of *Splunk Administrator Field Manual*.

| ID | Use case | Files |
|---|---|---|
| SR-01 | The search head or the indexers are pinned on memory or CPU and splunkd is slow to respond; identify the searches, users, and apps consuming the most resources right now and over the last few hours. | [main](SR-01-which-user-s-search-is-eating-memory.spl) |
| SR-02 | Alerts did not fire and reports are missing runs; list every skipped scheduled search with its skip reason, owning app, and skip ratio. | [main](SR-02-skipped-scheduled-searches-and-why.spl) |
| SR-03 | Skips are climbing and the scheduler appears saturated; measure actual concurrent scheduled-search load against the limit and find the long-running searches holding the slots. | [main](SR-03a-scheduler-hitting-its-concurrency-limit.spl) · [b](SR-03b-scheduler-hitting-its-concurrency-limit.spl) |
| SR-04 | The cluster is slow at this moment; list every search currently running, how long it has been running, who owns it, and what it is scanning, so the right sid can be cancelled. | [main](SR-04-long-running-searches-right-now-and-which.spl) |
| SR-05 | The dispatch directory on the search head is filling the disk or holding thousands of artifacts; identify which users and saved searches are leaving the largest and longest-lived artifacts. | [main](SR-05a-dispatch-directory-bloat.spl) · [b](SR-05b-dispatch-directory-bloat.spl) |
| SR-06 | The indexers are under heavy search load from unscoped queries; find the users running searches with index=*, no index filter at all, or an all-time range. | [main](SR-06-searches-using-all-time-or-no-index.spl) |
| SR-07 | Audit who ran search commands that destroy data, run code, send data out of Splunk, or overwrite lookups and summary indexes. | [main](SR-07-dangerous-search-commands.spl) |
| SR-08 | Identify who created or modified users and roles, and which accounts currently hold capabilities that allow privilege escalation. | [main](SR-08a-role-and-capability-changes-privilege-escalation.spl) · [b](SR-08b-role-and-capability-changes-privilege-escalation.spl) |
| SR-09 | Detect repeated failed logins against Splunk Web or the REST API, distinguish password spraying from a single brute-forced account, and find locked-out users. | [main](SR-09-failed-logins-brute-force-and-account-lockouts.spl) |
| SR-10 | Users report searches refusing to run with quota errors; identify which users are hitting srchDiskQuota or srchJobsQuota and how much of the quota they are using. | [main](SR-10a-users-blocked-by-search-disk-quota-or.spl) · [b](SR-10b-users-blocked-by-search-disk-quota-or.spl) |
| SR-11 | An alert stopped firing, a lookup was emptied, or a dashboard disappeared; identify who changed or deleted the saved search, lookup, macro, view, or field extraction and when. | [main](SR-11-who-modified-disabled-or-deleted-a-knowledge.spl) |
| SR-12 | Searches return stale field extractions or warn that peers have an out-of-date bundle; measure how long knowledge bundle replication takes, how large the bundle is, and which peers are failing. | [main](SR-12-slow-or-failing-knowledge-bundle-replication-to.spl) |
