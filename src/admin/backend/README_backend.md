Backend for TTS generation

Run locally

1. Copy `.env.example` to `.env` and fill in your Supabase credentials.
2. From project root, run:

```bash
npm install
npm run start-backend
```

This starts the server at `http://localhost:5000` by default.

Deploy with Docker (Render):

1. Build image from project root:

```bash
docker build -t eturismo-backend .
```

2. Run container:

```bash
docker run -p 5000:5000 --env-file src/admin/backend/.env eturismo-backend
```

Deploy notes:

- The code expects a Supabase storage bucket named `artifacts-audio` and a table `artifacts` with columns for `audio_en`, `audio_fil`, `audio_ja`, `audio_es`, `audio_ko`.
- For Vercel you should convert the Express server to serverless functions or host this service separately (Render, Fly, Railway, Docker on VPS).
- Keep `SUPABASE_SERVICE_ROLE_KEY` secret; do not commit it.
