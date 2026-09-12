# Synthetic fishery data

Versioned example records and workflow triggers for the [CPUE demo](https://github.com/kyuhank/cpue-actions-demo).

**Submission → QC → Prepare & load → Database**

QC rejects invalid records before loading. A corrected submission passes through the checks again, then becomes a database release for extraction and analysis.

Fixed snapshots support comparisons between data versions. New submissions add at most one batch; repeated demonstrations do not accumulate data. The SQLite fixture supports local runs.

Visitor selections use the temporary `demo-runtime` branch. Run records and outputs expire ten minutes after completion; the baseline is retained.

[Open the demo](https://kyuhank.github.io/cpue-actions-demo/) · [Browse the database](https://kyuhank.github.io/cpue-actions-demo/data.html)
