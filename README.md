Wheel Spin Referral Site — Demo bundle

Overview
This repository is a ready-to-deploy demo of a “spin-to-win” referral site:
- Users spin a wheel and get a prize.
- After spinning they receive a unique share URL.
- When 3 unique recipients confirm the link, the spinner is eligible and is redirected to WhatsApp with a pre-filled message to contact the supplier.
- Admin UI to add/edit prizes, change required shares, change WhatsApp supplier number, and view redemptions.

This demo uses a file-based JSON DB (lowdb) for fast setup. For production, migrate to Postgres (notes below).

Default credentials (DEMO — change immediately)
- Admin email: omodaratanemmanuel5@gmail.com
- Admin password: Omodara12

Placeholder WhatsApp number
- +1234567890 (change from Admin UI or in server .env)

Quick local run (dev)
1. Install Node.js 18+.
2. Start backend:
   - cd server
   - npm install
   - copy .env.example -> .env and edit values if needed
   - npm run dev
   Backend runs on http://localhost:4000 by default.

3. Start frontend:
   - cd frontend
   - npm install
   - npm run dev
   Frontend runs on http://localhost:5173 (Vite default).

Open frontend URL, click “Spin”, and use Admin -> login to edit prizes/settings.

Deploy to Vercel (frontend) + Render (backend)
- Create repo on GitHub and push this code.
- On Vercel: create a new project -> import the frontend folder from the repo -> set build: npm run build, output: dist (Vite default). Set env var: VITE_API_BASE to your backend URL (https://your-backend.onrender.com).
- On Render: create a new Web Service, connect your repo, point the service root to /server, build: npm install && npm run build (no build step required), start: node index.js or use npm start. Set environment variables from .env.example in Render service settings.

Environment variables (.env.example)
- PORT (default 4000)
- JWT_SECRET (choose a strong random string)
- REQUIRED_SHARES (default 3)
- WHATSAPP_SUPPLIER (E.164 formatted phone, e.g. +1234567890)

Switching to Postgres (production)
- Replace lowdb usage with Postgres (node-postgres or an ORM).
- Migrate data schema (users, prizes, spins, share_tokens, referrals).
- Add rate-limits and email/SMS verification for referral confirmations.

Support
If you want, I can provide step-by-step assistance to push this to GitHub and guide deploys on Vercel and Render.
