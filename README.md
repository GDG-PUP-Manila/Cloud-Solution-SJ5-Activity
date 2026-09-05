# GDG Founder's Edition Shirt Drop

[![Status: Teaching](https://img.shields.io/badge/Status-Teaching-blue)](docs/state.md)
[![Stack: Google Cloud](https://img.shields.io/badge/Stack-Google%20Cloud-black)](#about)
[![FMD philosophy: 1.31.0](https://img.shields.io/badge/FMD%20philosophy-1.31.0-blue)](AGENTS.md)


Teaching lab for a flash-sale architecture on Google Cloud. Not a product.

Owner: **GDG PUP Technology** (incoming CTO). Handover **2026-09-02**.

The GDG Founder's Edition Shirt Drop is a flash-sale app built to survive a burst of student traffic without overselling inventory.

## Table of Contents

- [About](#about)
- [Start here](#start-here)
- [Mission](#mission)
- [What's Included](#whats-included)
- [Quick start](#quick-start)
- [Operator Notes](#operator-notes)
- [REQUIRED: Shutdown All Services to avoid additional costs](#required-shutdown-all-services-to-avoid-additional-costs)
- [Documentation](#documentation)
- [Contributors](#contributors)

## About

Teaching lab for a flash-sale architecture on Google Cloud. Students and operators practice Cloud Run, Cloud SQL, Cloud Storage, and a global HTTP Load Balancer in a shirt-drop scenario. Not a product launch.

Owner: **GDG PUP Technology** (incoming CTO). Handover **2026-09-02**.

## Start here

- **Humans:** this README, then [docs/state.md](docs/state.md)
- **Agents:** [AGENTS.md](AGENTS.md) (state → index → FLAGS)
- **Contributors:** table below

## Mission

The deployment is built around five goals:

1. Keep inventory in a transactional Cloud SQL PostgreSQL database.
2. Run the API on Cloud Run so it scales with demand.
3. Host the frontend as a static site on Cloud Storage.
4. Route traffic through a global HTTP Load Balancer.
5. Keep the operator workflow simple enough to run from Google Cloud Console Cloud Shell.

## What's Included

- `docs/deploy_instructions.md` - the full Cloud Shell-first deployment guide.
- Backend source for the Cloud Run API.
- Frontend source for the static storefront.
- Infrastructure steps for Cloud SQL, Cloud Storage, and Load Balancing.

## Quick start

1. Open **Google Cloud Console Cloud Shell**.
2. Follow [docs/deploy_instructions.md](docs/deploy_instructions.md) from the repository root.
3. Set the `postgres` password, deploy the API, update `frontend/script.js` with the API URL, then deploy the frontend and load balancer.

This lab is Cloud Shell-first. Local PowerShell is not the intended path. Secrets and ops detail: [FLAGS.md](FLAGS.md) and [docs/state.md](docs/state.md).

## Operator Notes

- The guide assumes Cloud Shell, not local PowerShell.
- Cloud SQL does not ship with a usable default `postgres` password.
- If `gcloud sql connect` prompts for a password and fails, reset the `postgres` password and try again.

## REQUIRED: Shutdown All Services to avoid additional costs

Run these commands in Cloud Shell if you want to remove everything created by the demo.

```bash
# Delete the load balancer pieces
gcloud compute forwarding-rules delete gdg-http-rule --global
gcloud compute target-http-proxies delete gdg-http-proxy
gcloud compute url-maps delete gdg-app-url-map
gcloud compute backend-services delete gdg-api-backend --global
gcloud compute backend-buckets delete gdg-frontend-backend
gcloud compute network-endpoint-groups delete gdg-api-neg --region=us-central1

# Delete the app services
gcloud run services delete gdg-api --region=us-central1
gcloud storage rm -r gs://gdg-shirt-drop-frontend-YOUR_ID
gcloud sql instances delete gdg-inventory-db
```

If you used a custom domain, remove or update the DNS record separately.

## Documentation

| Doc | Purpose |
|-----|---------|
| [State](docs/state.md) | Operate position, ownership, cold start |
| [Index](docs/index.md) | Document manifest |
| [FLAGS](FLAGS.md) | Improvement register |
| [AGENTS](AGENTS.md) | Agent read order |
| [Deploy instructions](docs/deploy_instructions.md) | Cloud Shell-first deployment guide |

## Contributors

This project is made possible by the GDG PUP community.

| Name | Role | GitHub |
| --- | --- | --- |
| [Carlos Jerico Dela Torre](https://www.linkedin.com/in/delatorrecj) | Chief Technology Officer (2025-2026) | [@delatorrecj](https://github.com/delatorrecj) |
| [James Gabriele Torzar](https://www.linkedin.com/in/4regab) | Cloud Solutions / Front End | [@4regab](https://github.com/4regab) |
| [Justin Royse L. Solomon](https://www.linkedin.com/in/justin-royse-solomon) | Cloud Solutions / Front End | [@Justinroyse](https://github.com/Justinroyse) |

