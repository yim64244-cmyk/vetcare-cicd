# VetCare – CI/CD workflow templates (Track C: Legacy System Modernization)

Conceptual GitHub Actions templates for moving the VetCare clinic system from a single
clinic PC to container-based delivery.

| File | What it does |
|---|---|
| `.github/workflows/ci.yml` | Quality gates on every pull request: lint, tests (≥80% coverage), security scan, image build |
| `.github/workflows/deploy.yml` | Merge to `main` → build image once → deploy to **staging**; tag `v*.*.*` → deploy the same image to **production** after approval; automatic rollback if the rollout fails |
| `.github/workflows/rollback.yml` | Manual rollback to an earlier image |
| `Dockerfile` | Container image for the app |

## Settings needed on GitHub
- **Branch protection on `main`**: pull request required, 1 approval, status checks `test`, `security`, `build` must pass, no force push.
- **Environments**: `staging` and `production`; `production` has a required reviewer.
- **Secrets** (per environment): `KUBE_CONFIG` (base64 kubeconfig).

## Team
Ma Yitong · Pan Yaqin · Жанарбек Серлан · Бақытбай Бұлдірген
