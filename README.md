# TapStar Review Cards — Netlify

This is a standalone Netlify copy of the TapStar Review Cards site. It includes the site's pages, styling, local images, QR generation, activation flow, admin dashboard, dynamic links, and scan tracking.

## Netlify build settings

The included Netlify configuration sets:

- Build command: **npm run build**
- Publish directory: **.next**
- Node.js: **22**

Import this folder as a Netlify project so Netlify can build the Next.js app and deploy its server routes and API handlers. The site uses server-side functions, so it is not a static drag-and-drop site.

## Admin access

Before the first deploy, add these environment variables in the Netlify project settings:

- **TAPSTAR_ADMIN_PASSWORD**: choose a password with at least 12 characters.
- **TAPSTAR_SESSION_SECRET**: generate a private secret with **openssl rand -hex 32**.

Keep both values private and do not add them to the source files. Open **/admin** on the deployed site to sign in. The admin session expires after 12 hours.

The original Sites-only ChatGPT sign-in is replaced in this standalone copy by the password sign-in above. The admin dashboard keeps the same site styling and controls.

## Data storage

The Netlify copy stores its card records and scan counts in a site-wide Netlify Blobs store. Netlify provides the store credentials to its server functions automatically.

The store starts empty. Existing activation codes, destinations, and scan counts from the live Sites database are not included in this source ZIP. The original live website remains separate and unchanged.

## Local development

Install dependencies with **npm install**. For local routes and Blobs storage, run the app through the Netlify CLI after linking a Netlify project:

**npx netlify dev --command "npm run dev"**

For a plain build check, run **npm run build**.
