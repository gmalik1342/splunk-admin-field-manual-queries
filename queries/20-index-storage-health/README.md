# Index & Storage Health (IX)

Queries from the **Index & Storage Health** section of *Splunk Administrator Field Manual*.

| ID | Use case | Files |
|---|---|---|
| IX-01 | Replication fixups are not draining and peers report replication timeouts; measure where bucket replication is failing or slow and which source-to-target link is responsible. | [main](IX-01a-bucket-replication-lag-between-peers.spl) · [b](IX-01b-bucket-replication-lag-between-peers.spl) |
| IX-02 | Users report data missing well inside the documented retention window; confirm whether an index is freezing buckets because it hit maxTotalDataSizeMB instead of aging out on frozenTimePeriodInSecs. | [main](IX-02-index-freezing-buckets-early-size-cap-hit.spl) |
| IX-03 | An index is producing thousands of tiny warm buckets, bucket counts are exploding, and search performance on that index is collapsing; identify the roll reason. | [main](IX-03-hot-bucket-roll-storm.spl) |
| IX-04 | Warn before splunkd pauses indexing on a peer because a partition is approaching the minFreeSpace threshold, and confirm whether indexing has already stopped. | [main](IX-04a-partition-approaching-indexing-about-to-pause.spl) · [b](IX-04b-partition-approaching-indexing-about-to-pause.spl) |
| IX-05 | Compare configured retention to actual retention for every index on every peer to find indexes whose size or volume caps are cutting data off early. | [main](IX-05-volume-and-index-caps-forcing-premature-cold.spl) |
| IX-06 | Searches over "last 24 hours" miss data, or bucket roll storms appear on an index; locate the sources, hosts, and sourcetypes producing unparseable or out-of-window timestamps. | [main](IX-06a-events-landing-with-future-or-ancient-timestamps.spl) · [b](IX-06b-events-landing-with-future-or-ancient-timestamps.spl) |
| IX-07 | Events are being cut off mid-record or multiple records are merged into one event; identify which sourcetypes are hitting TRUNCATE or MAX_EVENTS limits and from which hosts. | [main](IX-07-line-breaking-and-truncation-errors-per-sourcetype.spl) |
| IX-08 | Ingest is lagging or forwarders report blocked output; determine which pipeline queue (parsing, aggregation, typing, index) is blocked on which host, and how long it has been saturated. | [main](IX-08-which-indexing-queue-is-blocked-and-since.spl) |
| IX-09 | Detect an index/sourcetype pair that normally receives data every hour but has gone quiet, before a downstream alert or dashboard owner notices. | [main](IX-09-silent-index-or-sourcetype-data-stopped-arriving.spl) |
| IX-10 | Real-time alerts are firing late or missing events; quantify the gap between event time and index time per host and sourcetype, and separate pipeline delay from timezone and clock problems. | [main](IX-10-index-time-latency-forwarding-delay-vs-clock.spl) |
| IX-11 | SmartStore searches are slow and peers show constant download activity; detect cache eviction thrash and failed uploads or downloads to the remote object store. | [main](IX-11-smartstore-cache-thrash-and-remote-storage-failures.spl) |
| IX-12 | Searches return errors about unreadable buckets or tsidx files, or a thawed bucket failed to rebuild; list every corrupt bucket by peer and index so they can be repaired with fsck. | [main](IX-12a-corrupt-buckets-tsidx-errors-and-failed-rebuilds.spl) · [b](IX-12b-corrupt-buckets-tsidx-errors-and-failed-rebuilds.spl) |
