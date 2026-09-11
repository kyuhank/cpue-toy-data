# Synthetic fishery data

New data here trigger extraction → CPUE → toy assessment → report, using the
reusable workflow in [cpue-actions-demo](https://github.com/kyuhank/cpue-actions-demo).
Runs and report artifacts appear in this repository’s **Actions** tab.

```bash
python3 scripts/add_year.py --append
git add data/toy-fishery.sqlite
git commit -m "Add one synthetic year"
git push
```

The Actions **Add synthetic year** workflow also adds data and runs the chain.
It explicitly calls the analysis workflow because `GITHUB_TOKEN` commits do not
start another push workflow. All data and models are for demonstration only.
