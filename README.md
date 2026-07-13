# 12-12-nft-serv-z14

Starter repository for an NFT service deployment flow targeting **Google Cloud Run** with CI/CD templates for:
- GitHub (repository host)
- GitLab CI
- Bitbucket Pipelines

## Deploy to Cloud Run

Build and deploy from source:

```bash
gcloud run deploy 12-12-nft-serv-z14 \
  --source . \
  --region us-central1 \
  --allow-unauthenticated
```

Or build/push container manually:

```bash
gcloud builds submit --tag gcr.io/$GOOGLE_CLOUD_PROJECT/12-12-nft-serv-z14
gcloud run deploy 12-12-nft-serv-z14 \
  --image gcr.io/$GOOGLE_CLOUD_PROJECT/12-12-nft-serv-z14 \
  --region us-central1 \
  --allow-unauthenticated
```

## CI/CD Templates

- `.gitlab-ci.yml` for GitLab deploys to Cloud Run
- `bitbucket-pipelines.yml` for Bitbucket Cloud deploys to Cloud Run

Set these variables/secrets in your CI platform:
- `GCP_PROJECT_ID`
- `GCP_REGION` (example: `us-central1`)
- `GCP_SA_KEY` (service account JSON)
