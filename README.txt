FAH CRUNCHIES NUTRITION WEBSITE + ADMIN

The public index.html retains the uploaded page's original branding and content:
- Logo file name: logo.png
- CRUNCHIES heading and “Know what you're eating.” tagline
- Original cream/green design and fonts
- Original Instagram and support email links
- Existing Lime nutrition values

Added:
- Search bar for product/flavour names
- Ingredients panel displayed ABOVE nutritional values
- Admin login with email and password
- Admin page to add/edit/delete products and nutrient rows
- Draft/published status; only published products show publicly
- Supabase database and row-level security policies

FILES
index.html        Public searchable product page
admin-login.html  Email + password login
admin.html        Product management interface
config.js         Supabase URL and publishable/anon key
setup.sql         Database schema, RLS policies, allowlist and original Lime seed
README.txt        Setup guide

SETUP
1. In setup.sql, replace replace-with-your-admin-email@example.com with your actual email.
2. Run setup.sql in Supabase Dashboard > SQL Editor.
   If you already ran an earlier version of the SQL, inspect the optional Lime seed section to avoid duplicate Lime products.
3. In config.js, set your Supabase project URL and publishable/anon key. Never use a service_role/secret key in browser code.
4. In Supabase Dashboard > Authentication > Users, create/invite your admin user using the email listed in the allowlist. Set a strong password for that account (or use the password reset flow from Supabase if already created). Password sign-in must be enabled in Authentication > Sign In / Providers.
6. Public page remains https://fahcrunchies.github.io/snack-nutrition/
7. Admin login: https://fahcrunchies.github.io/snack-nutrition/admin-login.html

HOW TO USE
- Sign in with the allowlisted email and its Supabase Auth password.
- Add or edit the product name, flavour/search terms, serving size, ingredients and nutrition rows.
- Select Draft or Published, then Save.
- Published products become searchable on the public page after it reloads.

NOTES
- This ZIP does not contain your actual logo.png because it was not part of the HTML upload; keep and upload your existing logo.png unchanged.
- Current Lime nutrition numbers are copied from the uploaded HTML. Verify them against the product's approved nutrition data.
- The uploaded HTML did not contain Lime ingredients. Enter the verified ingredient list in the admin page.
- Supabase must be configured before the admin/data sync is functional. This package is code, not an already deployed/connected service.

PASSWORD LOGIN UPDATE
- Admin login now uses Supabase email/password authentication, not email OTP, so it avoids OTP email rate limits.
- This is not a password hardcoded into HTML. Supabase verifies the password and database RLS policies restrict data access.
- Existing OTP-only users may need to set a password for their Supabase Auth user before they can sign in.
- Use a unique, strong password and do not put it into config.js or any website file.
