# License & Forwarder Management (LF)

Queries from the **License & Forwarder Management** section of *Splunk Administrator Field Manual*.

| ID | Use case | Files |
|---|---|---|
| LF-01 | Report daily license consumption against the pool quota and identify which indexes, sourcetypes, and hosts account for it. | [main](LF-01a-daily-license-usage-by-index-sourcetype-and.spl) · [b](LF-01b-daily-license-usage-by-index-sourcetype-and.spl) |
| LF-02 | The license manager is showing warnings, or searches are blocked for a license violation; identify the days and pools that went over quota and how close the stack is to a violation. | [main](LF-02a-license-warnings-and-violations-which-day-which.spl) · [b](LF-02b-license-warnings-and-violations-which-day-which.spl) |
| LF-03 | An indexer or search head shows a license bulletin about being unable to contact the license manager; identify which instances are not checking in and since when. | [main](LF-03-license-peer-cannot-reach-the-license-manager.spl) |
| LF-04 | License usage jumped overnight; identify the hosts and sourcetypes whose volume yesterday was far above their normal daily volume. | [main](LF-04-sudden-ingestion-spike-which-host-or-sourcetype.spl) |
| LF-05 | License usage reports show large volumes with an empty host or source; recover per-host and per-source attribution when license_usage.log has squashed those values. | [main](LF-05a-host-and-source-missing-from-license-usage.spl) · [b](LF-05b-host-and-source-missing-from-license-usage.spl) |
| LF-06 | Data from some systems is missing; list forwarders that were connected to the indexers recently but have not been seen since, with their last contact time. | [main](LF-06-forwarders-that-stopped-sending-data.spl) |
| LF-07 | A heavy forwarder or intermediate forwarder is falling behind; confirm whether its output to the indexers is blocked, to which destinations, and for how long. | [main](LF-07a-heavy-forwarder-backpressure-output-blocked-to-indexers.spl) · [b](LF-07b-heavy-forwarder-backpressure-output-blocked-to-indexers.spl) |
| LF-08 | Build an inventory of every forwarder connected to the indexers with its version, OS, and type, to find forwarders on unsupported or vulnerable versions. | [main](LF-08-forwarder-version-os-and-architecture-inventory.spl) |
| LF-09 | Configuration changes pushed from the deployment server are not reaching some forwarders; find clients that have stopped phoning home and clients that report errors installing deployed apps. | [main](LF-09a-deployment-clients-not-phoning-home-or-failing.spl) · [b](LF-09b-deployment-clients-not-phoning-home-or-failing.spl) |
| LF-10 | Forwarders cannot connect to indexers after a certificate change, or connections drop with TLS errors; classify SSL handshake failures by cause and by the forwarders affected. | [main](LF-10-forwarder-to-indexer-ssl-and-certificate-failures.spl) |
| LF-11 | Some indexers are much busier than others or fill their disks first; measure how evenly forwarder traffic spreads across the indexers and find forwarders that stick to a single indexer. | [main](LF-11a-forwarders-pinned-to-one-indexer-uneven-load.spl) · [b](LF-11b-forwarders-pinned-to-one-indexer-uneven-load.spl) |
| LF-12 | A forwarder is falling behind on its files with no errors; confirm whether it is throttled by maxKBps, and on heavy forwarders, find which parsing processor is consuming the most CPU. | [main](LF-12a-forwarder-throughput-throttling-and-parsing-bottlenecks.spl) · [b](LF-12b-forwarder-throughput-throttling-and-parsing-bottlenecks.spl) |
