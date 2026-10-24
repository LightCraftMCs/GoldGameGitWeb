# GoldGame — GitHub Pages + Supabase Auth

This is a static GitHub Pages website with Supabase-powered email/password sign-up, sign-in, password reset email request, and a basic account page.

## 1. Create a Supabase project
1. Create a project at https://supabase.com/
2. In Project Settings → API (or Connect), copy the **Project URL** and the **publishable/anon public key**.
3. Edit `assets/supabase-config.js`:
   - Replace `PASTE_YOUR_SUPABASE_PROJECT_URL_HERE`
   - Replace `PASTE_YOUR_SUPABASE_ANON_OR_PUBLISHABLE_KEY_HERE`
4. Commit and push the updated file to GitHub.

Only use the public anon/publishable key in browser code. **Never put a `service_role`, secret, database password, or other privileged key in this repository.**

## 2. Configure Supabase Auth URLs
In Supabase → Authentication → URL Configuration:
- Set Site URL to the deployed GitHub Pages site URL, e.g. `https://YOUR-USERNAME.github.io/YOUR-REPOSITORY/`.
- Add that same site URL to the Redirect URLs allow-list. Add the exact auth callback URL if your project configuration requires it.
- Enable email/password sign-in. Configure SMTP/email settings if you need reliable production email delivery; default email sending may be limited.

Use your real GitHub Pages URL, not the example above.

## 3. Publish with GitHub Pages
Upload the contents of this project folder to the repository root. In GitHub → Settings → Pages, choose `Deploy from a branch`, branch `main`, folder `/(root)`.

## Included pages
- `auth.html`: sign up, sign in, password reset email request
- `account.html`: basic signed-in account view and sign out
- `assets/supabase-config.js`: public project configuration placeholders

## Important limitations
- Supabase uses PostgreSQL, not MySQL.
- The auth pages use Supabase Auth. They do not automatically create a custom profile table or a secure admin dashboard.
- A frontend-only static site cannot safely hold privileged secrets. Protect any future profile tables with Row Level Security (RLS) policies and never trust browser-submitted rank/payment/admin status.
- Password reset requires configuring allowed redirect URLs and an email provider.
- This is not a payment gateway and does not automatically deliver ranks to Minecraft.
