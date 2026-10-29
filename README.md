# FLIX NET
Vercel-hosted paid Wi-Fi portal starter using Supabase Auth/Postgres and Paystack.

## Deploy
1. Create a Supabase project and run `supabase/schema.sql` in SQL Editor.
2. Import this repository into Vercel (Other framework, no build command/output directory).
3. Add the variables listed in `.env.example` in Vercel Project Settings and redeploy.
4. Register your own account, then promote it in Supabase SQL Editor:
`update public.profiles set role='admin' where id=(select id from auth.users where email='YOUR_EMAIL');`
5. Start with Paystack test keys. Set webhook URL to `https://YOUR_DOMAIN/api/paystack/webhook`.

## Important
This project is not live until you add real environment variables and configure a compatible hotspot controller. Payment initialization intentionally refuses checkout unless the hotspot adapter is configured, to avoid taking money without access delivery. RouterOS must be reachable securely over HTTPS/VPN; never expose router management publicly. The included RouterOS adapter requires MikroTik RouterOS v7 REST API and a configured HotSpot server/profile.

Never commit real keys. Keep `SUPABASE_SERVICE_ROLE_KEY` and `PAYSTACK_SECRET_KEY` server-side only.