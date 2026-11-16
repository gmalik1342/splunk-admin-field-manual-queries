# Splunk Administrator Field Manual — SPL Queries

Companion repository for **Splunk Administrator Field Manual: Real-World SPL Recipes for Troubleshooting, Root Cause Analysis, and Cluster Triage** by Gaurav Malik.

Every query from the book, one file per query, ready to paste into the Splunk search bar.
The printed book explains what each query targets, which fields to read, and how to tell a
healthy result from a failing one. This repository is the copy-paste supplement.

## Layout

- [Cluster & Peer Management (CL)](queries/10-cluster-peer-management/) — 12 entries
- [Index & Storage Health (IX)](queries/20-index-storage-health/) — 12 entries
- [Search Performance & User Auditing (SR)](queries/30-search-performance-user-auditing/) — 12 entries
- [KV Store & REST API Troubleshooting (KV)](queries/40-kvstore-rest-api/) — 12 entries
- [License & Forwarder Management (LF)](queries/50-license-forwarder-management/) — 12 entries

Files are named by entry ID, the same ID printed in the book (`CL-01`, `IX-08`, …).
Entries with more than one query use `a`, `b`, `c` suffixes; `a` is the main query.

## Using the files

- Each file starts with a comment block (inside triple backticks) giving the entry ID,
  the use case, and where to run it. SPL inline comments need Splunk 8.0 or later. On older
  versions, delete the comment block before running.
- Queries that start with `| rest` must run on the instance named in the "Run on" line,
  usually the cluster manager, license manager, or the search head itself.
- Replace anything in `<angle brackets>` (for example `<peer_host>`) with your own values.
- Start with the short time ranges in the queries. Internal indexes are large.


## When a query returns nothing

An empty result is only useful if the query could see its data. Every entry has a matching
probe in [`probes/`](probes/): `probes/<ID>-probe.spl` returns one row per data source the
entry reads, marked `OK` or `MISSING`, and `probes/<ID>-probe-rest*.spl` lists the fields a
REST endpoint returns on your instance. [`probes/README.md`](probes/README.md) walks through
the general checks (forwarding, role access, component names, field names) in order.

## Index

| ID | Entry | Section | |
|---|---|---|---|
| [CL-01](queries/10-cluster-peer-management/CL-01a-rolling-restart-started-in-progress-or-finished.spl) | Rolling Restart: Started, In Progress, or Finished | Cluster & Peer Management | ⚠ |
| [CL-02](queries/10-cluster-peer-management/CL-02a-which-peer-dropped-during-a-network-partition.spl) | Which Peer Dropped During a Network Partition | Cluster & Peer Management | |
| [CL-03](queries/10-cluster-peer-management/CL-03a-search-factor-replication-factor-not-met-which.spl) | Search Factor / Replication Factor Not Met: Which Buckets, Which Peers | Cluster & Peer Management | |
| [CL-04](queries/10-cluster-peer-management/CL-04a-fixup-backlog-stuck-which-fixup-level-is.spl) | Fixup Backlog Stuck: Which Fixup Level Is Not Draining | Cluster & Peer Management | |
| [CL-05](queries/10-cluster-peer-management/CL-05a-maintenance-mode-audit-who-when-still-on.spl) | Maintenance Mode Audit: Who, When, Still On? | Cluster & Peer Management | ⚠ |
| [CL-06](queries/10-cluster-peer-management/CL-06a-cluster-bundle-push-failed-or-partially-applied.spl) | Cluster Bundle Push Failed or Partially Applied | Cluster & Peer Management | |
| [CL-07](queries/10-cluster-peer-management/CL-07a-peer-stuck-in-decommissioning-after.spl) | Peer Stuck in Decommissioning After offline --enforce-counts | Cluster & Peer Management | |
| [CL-08](queries/10-cluster-peer-management/CL-08a-flapping-peer-up-pending-up-cycling.spl) | Flapping Peer: Up → Pending → Up Cycling | Cluster & Peer Management | |
| [CL-09](queries/10-cluster-peer-management/CL-09a-search-head-cluster-captain-election-churn.spl) | Search Head Cluster Captain Election Churn | Cluster & Peer Management | ⚠ |
| [CL-10](queries/10-cluster-peer-management/CL-10-shc-member-out-of-sync-on-configuration.spl) | SHC Member Out of Sync on Configuration Replication | Cluster & Peer Management | |
| [CL-11](queries/10-cluster-peer-management/CL-11-shc-deployer-push-audit.spl) | SHC Deployer Push Audit | Cluster & Peer Management | ⚠ |
| [CL-12](queries/10-cluster-peer-management/CL-12-multisite-down-site-or-cross-site-replication.spl) | Multisite: Down Site or Cross-Site Replication Imbalance | Cluster & Peer Management | |
| [IX-01](queries/20-index-storage-health/IX-01a-bucket-replication-lag-between-peers.spl) | Bucket Replication Lag Between Peers | Index & Storage Health | ⚠ |
| [IX-02](queries/20-index-storage-health/IX-02-index-freezing-buckets-early-size-cap-hit.spl) | Index Freezing Buckets Early: Size Cap Hit Before Retention | Index & Storage Health | ⚠ |
| [IX-03](queries/20-index-storage-health/IX-03-hot-bucket-roll-storm.spl) | Hot Bucket Roll Storm | Index & Storage Health | |
| [IX-04](queries/20-index-storage-health/IX-04a-partition-approaching-indexing-about-to-pause.spl) | Partition Approaching minFreeSpace: Indexing About to Pause | Index & Storage Health | |
| [IX-05](queries/20-index-storage-health/IX-05-volume-and-index-caps-forcing-premature-cold.spl) | Volume and Index Caps Forcing Premature Cold-to-Frozen | Index & Storage Health | |
| [IX-06](queries/20-index-storage-health/IX-06a-events-landing-with-future-or-ancient-timestamps.spl) | Events Landing With Future or Ancient Timestamps | Index & Storage Health | |
| [IX-07](queries/20-index-storage-health/IX-07-line-breaking-and-truncation-errors-per-sourcetype.spl) | Line-Breaking and Truncation Errors per Sourcetype | Index & Storage Health | |
| [IX-08](queries/20-index-storage-health/IX-08-which-indexing-queue-is-blocked-and-since.spl) | Which Indexing Queue Is Blocked, and Since When | Index & Storage Health | |
| [IX-09](queries/20-index-storage-health/IX-09-silent-index-or-sourcetype-data-stopped-arriving.spl) | Silent Index or Sourcetype: Data Stopped Arriving | Index & Storage Health | |
| [IX-10](queries/20-index-storage-health/IX-10-index-time-latency-forwarding-delay-vs-clock.spl) | Index-Time Latency: Forwarding Delay vs. Clock Drift | Index & Storage Health | |
| [IX-11](queries/20-index-storage-health/IX-11-smartstore-cache-thrash-and-remote-storage-failures.spl) | SmartStore Cache Thrash and Remote Storage Failures | Index & Storage Health | ⚠ |
| [IX-12](queries/20-index-storage-health/IX-12a-corrupt-buckets-tsidx-errors-and-failed-rebuilds.spl) | Corrupt Buckets, tsidx Errors, and Failed Rebuilds | Index & Storage Health | |
| [SR-01](queries/30-search-performance-user-auditing/SR-01-which-user-s-search-is-eating-memory.spl) | Which User's Search Is Eating Memory and CPU | Search Performance & User Auditing | |
| [SR-02](queries/30-search-performance-user-auditing/SR-02-skipped-scheduled-searches-and-why.spl) | Skipped Scheduled Searches and Why | Search Performance & User Auditing | |
| [SR-03](queries/30-search-performance-user-auditing/SR-03a-scheduler-hitting-its-concurrency-limit.spl) | Scheduler Hitting Its Concurrency Limit | Search Performance & User Auditing | |
| [SR-04](queries/30-search-performance-user-auditing/SR-04-long-running-searches-right-now-and-which.spl) | Long-Running Searches Right Now, and Which to Kill | Search Performance & User Auditing | |
| [SR-05](queries/30-search-performance-user-auditing/SR-05a-dispatch-directory-bloat.spl) | Dispatch Directory Bloat | Search Performance & User Auditing | |
| [SR-06](queries/30-search-performance-user-auditing/SR-06-searches-using-all-time-or-no-index.spl) | Searches Using index=*, All Time, or No Index | Search Performance & User Auditing | |
| [SR-07](queries/30-search-performance-user-auditing/SR-07-dangerous-search-commands.spl) | Dangerous Search Commands: delete, script, sendemail, outputlookup, collect, map | Search Performance & User Auditing | |
| [SR-08](queries/30-search-performance-user-auditing/SR-08a-role-and-capability-changes-privilege-escalation.spl) | Role and Capability Changes: Privilege Escalation | Search Performance & User Auditing | |
| [SR-09](queries/30-search-performance-user-auditing/SR-09-failed-logins-brute-force-and-account-lockouts.spl) | Failed Logins, Brute Force, and Account Lockouts | Search Performance & User Auditing | |
| [SR-10](queries/30-search-performance-user-auditing/SR-10a-users-blocked-by-search-disk-quota-or.spl) | Users Blocked by Search Disk Quota or Concurrency Limits | Search Performance & User Auditing | ⚠ |
| [SR-11](queries/30-search-performance-user-auditing/SR-11-who-modified-disabled-or-deleted-a-knowledge.spl) | Who Modified, Disabled, or Deleted a Knowledge Object | Search Performance & User Auditing | |
| [SR-12](queries/30-search-performance-user-auditing/SR-12-slow-or-failing-knowledge-bundle-replication-to.spl) | Slow or Failing Knowledge Bundle Replication to Peers | Search Performance & User Auditing | ⚠ |
| [KV-01](queries/40-kvstore-rest-api/KV-01a-kv-store-status-across-every-member.spl) | KV Store Status Across Every Member | KV Store & REST API Troubleshooting | |
| [KV-02](queries/40-kvstore-rest-api/KV-02-kv-store-replication-lag-between-shc-members.spl) | KV Store Replication Lag Between SHC Members | KV Store & REST API Troubleshooting | ⚠ |
| [KV-03](queries/40-kvstore-rest-api/KV-03-why-crashed-restarted-or-will-not-start.spl) | Why mongod Crashed, Restarted, or Will Not Start | KV Store & REST API Troubleshooting | ⚠ |
| [KV-04](queries/40-kvstore-rest-api/KV-04-largest-and-fastest-growing-kv-store-collections.spl) | Largest and Fastest-Growing KV Store Collections | KV Store & REST API Troubleshooting | ⚠ |
| [KV-05](queries/40-kvstore-rest-api/KV-05a-slow-kv-store-operations-and-lock-contention.spl) | Slow KV Store Operations and Lock Contention | KV Store & REST API Troubleshooting | ⚠ |
| [KV-06](queries/40-kvstore-rest-api/KV-06-kv-store-backup-and-restore-audit.spl) | KV Store Backup and Restore Audit | KV Store & REST API Troubleshooting | ⚠ |
| [KV-07](queries/40-kvstore-rest-api/KV-07-rest-api-traffic-by-user-client-and.spl) | REST API Traffic by User, Client, and Endpoint | KV Store & REST API Troubleshooting | |
| [KV-08](queries/40-kvstore-rest-api/KV-08-spikes-in-rest-4xx-and-5xx-responses.spl) | Spikes in REST 4xx and 5xx Responses | KV Store & REST API Troubleshooting | |
| [KV-09](queries/40-kvstore-rest-api/KV-09-configuration-changes-made-through-rest.spl) | Configuration Changes Made Through REST | KV Store & REST API Troubleshooting | |
| [KV-10](queries/40-kvstore-rest-api/KV-10a-authentication-tokens-created-used-expiring.spl) | Authentication Tokens: Created, Used, Expiring | KV Store & REST API Troubleshooting | ⚠ |
| [KV-11](queries/40-kvstore-rest-api/KV-11-http-event-collector-failures.spl) | HTTP Event Collector Failures | KV Store & REST API Troubleshooting | ⚠ |
| [KV-12](queries/40-kvstore-rest-api/KV-12-slow-rest-endpoints-on-the-management-port.spl) | Slow REST Endpoints on the Management Port | KV Store & REST API Troubleshooting | |
| [LF-01](queries/50-license-forwarder-management/LF-01a-daily-license-usage-by-index-sourcetype-and.spl) | Daily License Usage by Index, Sourcetype, and Host vs. Quota | License & Forwarder Management | |
| [LF-02](queries/50-license-forwarder-management/LF-02a-license-warnings-and-violations-which-day-which.spl) | License Warnings and Violations: Which Day, Which Pool | License & Forwarder Management | |
| [LF-03](queries/50-license-forwarder-management/LF-03-license-peer-cannot-reach-the-license-manager.spl) | License Peer Cannot Reach the License Manager | License & Forwarder Management | ⚠ |
| [LF-04](queries/50-license-forwarder-management/LF-04-sudden-ingestion-spike-which-host-or-sourcetype.spl) | Sudden Ingestion Spike: Which Host or Sourcetype | License & Forwarder Management | |
| [LF-05](queries/50-license-forwarder-management/LF-05a-host-and-source-missing-from-license-usage.spl) | Host and Source Missing From License Usage (Squashing) | License & Forwarder Management | |
| [LF-06](queries/50-license-forwarder-management/LF-06-forwarders-that-stopped-sending-data.spl) | Forwarders That Stopped Sending Data | License & Forwarder Management | |
| [LF-07](queries/50-license-forwarder-management/LF-07a-heavy-forwarder-backpressure-output-blocked-to-indexers.spl) | Heavy Forwarder Backpressure: Output Blocked to Indexers | License & Forwarder Management | |
| [LF-08](queries/50-license-forwarder-management/LF-08-forwarder-version-os-and-architecture-inventory.spl) | Forwarder Version, OS, and Architecture Inventory | License & Forwarder Management | |
| [LF-09](queries/50-license-forwarder-management/LF-09a-deployment-clients-not-phoning-home-or-failing.spl) | Deployment Clients Not Phoning Home or Failing App Installs | License & Forwarder Management | ⚠ |
| [LF-10](queries/50-license-forwarder-management/LF-10-forwarder-to-indexer-ssl-and-certificate-failures.spl) | Forwarder-to-Indexer SSL and Certificate Failures | License & Forwarder Management | ⚠ |
| [LF-11](queries/50-license-forwarder-management/LF-11a-forwarders-pinned-to-one-indexer-uneven-load.spl) | Forwarders Pinned to One Indexer: Uneven Load Balancing | License & Forwarder Management | |
| [LF-12](queries/50-license-forwarder-management/LF-12a-forwarder-throughput-throttling-and-parsing-bottlenecks.spl) | Forwarder Throughput Throttling and Parsing Bottlenecks | License & Forwarder Management | |

## Feedback

Found a query that does not match the log format on your version? Open an issue with the
entry ID, your Splunk version, and a sample of the raw event (mask hostnames and IPs).

## License

The SPL queries are released under the MIT License (see `LICENSE`). The book text is not
included here and remains © 2026 Gaurav Malik. All rights reserved.

Splunk® is a registered trademark of its owner. This repository is independent and is not
affiliated with, endorsed by, or sponsored by Splunk or Cisco.
