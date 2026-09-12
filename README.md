# CPUE demo data and triggers

Companion to [cpue-actions-demo](https://github.com/kyuhank/cpue-actions-demo).

Synthetic submissions run through submission → QC → preparation and loading. Failed QC stops before publication. Accepted releases then feed extraction, CPUE analyses and reporting, assessment inputs, models, results summary and the assessment report. Stage-setting changes rerun only the affected analysis path.

Visitor settings use the temporary `demo-runtime` branch. Run records and outputs appear in **Actions** and expire after the demonstration. The SQLite file is the local data fixture.

[Open the demo](https://kyuhank.github.io/cpue-actions-demo/)
