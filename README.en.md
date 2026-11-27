# AgilFrame Deploy

[Русский](README.md) · **English**

Docker Compose configuration for self-hosting AgilFrame Core. Compose builds the image from the Core commit pinned in `AGILFRAME_REF` and stores data in the named `core-data` volume.

[AgilFrame project](https://github.com/GillHD/agilframe) · [Core](https://github.com/GillHD/agilframe-core)

## Run Core

Install Docker Engine and Docker Compose. From the repository root, copy the environment template to `.env`.

```bash
cp .env.example .env
```

Replace the `AGIL_TOKEN_SECRET` and `AGIL_API_KEYS` placeholders with your own random secrets. Keep the API key in `key:tenant` format. For external access, set `AGIL_PUBLIC_ORIGIN` to the public HTTPS URL.

```bash
docker compose config --quiet
docker compose up -d --build
curl --fail http://localhost:8787/v1/health
```

By default, Core is available on `127.0.0.1:8787`. For external access, put a TLS-terminating reverse proxy in front of it. Enable `AGIL_TRUST_PROXY` after restricting direct access to Core.

## Update and validate the configuration

Back up the `core-data` volume before updating. Set `AGILFRAME_REF` to a verified Core commit, then repeat the configuration check and rebuild the image.

Use the environment template to validate the Compose configuration without starting Core.

```bash
docker compose --env-file .env.example config --quiet
```

[Deployment guide](https://github.com/GillHD/agilframe-core/blob/main/agil/core/docs/deployment.md) · [Backups and operations](https://github.com/GillHD/agilframe-core/blob/main/agil/core/docs/operations.md) · [Media nodes](https://github.com/GillHD/agilframe-nodes)

[License](LICENSE) · [Notices](NOTICE) · [Contributing](CONTRIBUTING.en.md) · [Security](SECURITY.en.md)
