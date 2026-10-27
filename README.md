# Ikjoo234 Photos

Public photo gallery backed by Cloudflare Worker and R2.

- Worker URL: https://ikjoo234-photos.zjaghkf0000.workers.dev
- R2 bucket: `ikjoo234-photos`
- 2 GiB application-level storage limit; no application-level per-image size limit.
- Multi-photo uploads with upload progress, virtual folders, single and bulk ZIP downloads, 500px JPEG low-quality downloads.
- Bulk original ZIP is limited to 100 MiB per batch to avoid excessive browser memory use.

## Public site warning
This is intentionally public with no login. Anyone who can access the site can upload images, download them, create folders, and delete photos/folders. Do not store private or sensitive images.

## Deploy
`npx wrangler deploy`
