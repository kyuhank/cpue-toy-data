# Synthetic data that trigger another repository's analysis

This public repository holds a small **entirely synthetic** SQLite fishery database.
It contains no real vessel, location, member, or confidential fishery records.

A change to `data/` starts this repository's GitHub Actions workflow. That workflow
calls the version-pinned reusable workflow in
[cpue-actions-demo](https://github.com/kyuhank/cpue-actions-demo):

```mermaid
flowchart LR
  D[New data commit here] --> W[Call analysis workflow in cpue-actions-demo]
  W --> E[Extract]
  E --> C[CPUE]
  C --> A[Toy assessment]
  A --> R[Quarto report]
```

Runs and artifacts appear in **this data repository's Actions tab** because it is
the caller. Within the called workflow, four dependent jobs run sequentially.
This is a cross-repository reusable workflow, not a chain of four separate
repository-dispatch events. It uses the standard read-only `GITHUB_TOKEN`; no
cross-repository personal-access-token secret is needed for the public workflow.

## Add a synthetic year

**Try it entirely in your browser:**

1. Use [this template](https://github.com/kyuhank/cpue-toy-data/generate) to create
   your own **public** repository with the default `main` branch.
2. Open **Actions** and enable workflows if GitHub asks.
3. Select **Try it - add one synthetic year**, then **Run workflow** on `main`.
4. Watch Add synthetic data → Extract → CPUE → Assessment → Report.
5. Download the final `report-1` artifact (the number is the run attempt), unzip
   it, and open `report.html`. Repeat to add another synthetic year.

No R, Python, Docker, Quarto, or Kflow2 installation is required for this route.
The standard GitHub-hosted runners execute the models. The data repository is
public; use only the supplied synthetic data. The demo ends in 2035, after which
you can create another template copy for a fresh rehearsal.

The browser workflow commits as the GitHub user who clicks Run workflow. Because
commits made with `GITHUB_TOKEN` do not trigger another push workflow, it
explicitly calls the separate analysis repository's reusable workflow after the
data update. A normal user push uses the automatic push-triggered route below.

**From a local checkout:**

```bash
python3 scripts/add_year.py --append
git add data/toy-fishery.sqlite
git commit -m "Add one synthetic year"
git push
```

The new commit is the event: no manual Actions click is required. Use **Re-run all
jobs** when repeating a workflow attempt so all four artifacts share its attempt
number. Workflow dispatch can repeat the current data version.

The models compare two CPUE specifications and then fit a tiny biomass model.
They are teaching examples, not a tuna stock assessment or management advice.

Kflow2 and the private presentation viewer are not included in either public
repository. All calculations and the report can be inspected directly in GitHub.
