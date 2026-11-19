# bluegreen-demo

A small project that practises trunk-based development and blue-green deployment.

- `app.py` - one shop environment (`/health`, `/info`, `/checkout`) and the router.
- `demo.py` - commands: `up`, `apply`, `probe`, `traffic`, `smoke <env>`.
- `deploy.json` - the manifest: which environment is live, versions and feature flags.
- `test_app.py` - unit tests and a smoke test of every environment.
- `scripts/secret_scan.py` - simple hard-coded secret scanner.
- `.github/workflows/ci.yml` - the `security-checks` pipeline (tests, secret scan, Bandit, pip-audit).

## Run locally

```
python -m pip install -r requirements.txt bandit pip-audit
python -m pytest -q
python demo.py up            # terminal 1, leave running
python demo.py probe         # terminal 2
python demo.py traffic
python demo.py smoke green
```
