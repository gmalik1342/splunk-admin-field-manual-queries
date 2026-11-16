# Cluster & Peer Management (CL)

Queries from the **Cluster & Peer Management** section of *Splunk Administrator Field Manual*.

| ID | Use case | Files |
|---|---|---|
| CL-01 | Check if a cluster rolling restart has started, is currently in progress, or has finished, including the user who triggered it. | [main](CL-01a-rolling-restart-started-in-progress-or-finished.spl) · [b](CL-01b-rolling-restart-started-in-progress-or-finished.spl) |
| CL-02 | Identify which peer node dropped out of the cluster during a network partition, and the exact second the cluster manager marked it Down. | [main](CL-02a-which-peer-dropped-during-a-network-partition.spl) · [b](CL-02b-which-peer-dropped-during-a-network-partition.spl) |
| CL-03 | The cluster manager reports Search Factor or Replication Factor Not Met; identify the affected indexes and the peers that originated the under-replicated buckets. | [main](CL-03a-search-factor-replication-factor-not-met-which.spl) · [b](CL-03b-search-factor-replication-factor-not-met-which.spl) |
| CL-04 | Bucket fixup tasks are piling up after a peer outage; determine which fixup level is stuck and the error preventing progress. | [main](CL-04a-fixup-backlog-stuck-which-fixup-level-is.spl) · [b](CL-04b-fixup-backlog-stuck-which-fixup-level-is.spl) |
| CL-05 | Audit who enabled cluster maintenance mode, when it was set, and whether it was left on after the change window closed. | [main](CL-05a-maintenance-mode-audit-who-when-still-on.spl) · [b](CL-05b-maintenance-mode-audit-who-when-still-on.spl) |
| CL-06 | Trace a failed or partially applied apply cluster-bundle to the peer that rejected it and the validation error it threw. | [main](CL-06a-cluster-bundle-push-failed-or-partially-applied.spl) · [b](CL-06b-cluster-bundle-push-failed-or-partially-applied.spl) |
| CL-07 | A peer was taken offline with splunk offline --enforce-counts and has sat in Decommissioning for hours; determine what is blocking completion. | [main](CL-07a-peer-stuck-in-decommissioning-after.spl) · [b](CL-07b-peer-stuck-in-decommissioning-after.spl) |
| CL-08 | A peer repeatedly cycles between Up, Pending, and Down; correlate the transitions with heartbeat loss or host resource exhaustion. | [main](CL-08a-flapping-peer-up-pending-up-cycling.spl) · [b](CL-08b-flapping-peer-up-pending-up-cycling.spl) |
| CL-09 | SHC captaincy keeps moving between members, scheduled searches are being skipped during handoffs, and the cause of the elections needs to be found. | [main](CL-09a-search-head-cluster-captain-election-churn.spl) · [b](CL-09b-search-head-cluster-captain-election-churn.spl) |
| CL-10 | A search head cluster member is serving stale knowledge objects because configuration replication with the captain is failing; identify the member and the failure mode. | [main](CL-10-shc-member-out-of-sync-on-configuration.spl) |
| CL-11 | Audit who ran apply shcluster-bundle, when, and which SHC members failed to take the push. | [main](CL-11-shc-deployer-push-audit.spl) |
| CL-12 | In a multisite indexer cluster, confirm per-site health and detect a down site or a site carrying a disproportionate share of buckets. | [main](CL-12-multisite-down-site-or-cross-site-replication.spl) |
