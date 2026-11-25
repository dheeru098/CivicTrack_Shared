# CivicTrack — Shared community reporting

Independent student prototype. No affiliation or direct API integration with ride-hailing companies or government. Reports are voluntary, unverified, and publicly visible to anyone with the website link. No automatic complaint forwarding. Do not report private addresses or personal details; report only public issue locations while safely stationary.

## Run locally
1. Install Node.js 18+ and extract the ZIP.
2. Open the extracted CivicTrack_Shared folder in VS Code.
3. Run `npm start` in the terminal. Open http://localhost:3000/.
4. Sarpanch view: http://localhost:3000/?view=dashboard. This view hides the form and has no editing controls. No status mutation endpoint exists. Anyone can submit via the main page; this is a public read-only dashboard, not identity-based access control.

## Public hosting (required for different phones on different networks)
Upload the folder contents to a GitHub repository. Create a Node web service on a host such as Render. Build command: `npm install`; start command: `npm start`. Set `DATA_FILE` to a path on a persistent writable disk (e.g. `/var/data/reports.json` with a disk mounted at `/var/data`); storage without persistence can be lost on redeploy/restart. The host provides a public HTTPS URL. Share that URL with friends and the same URL plus `/?view=dashboard` with the Sarpanch. The dashboard refreshes automatically every 15 seconds. Do not host just the HTML on GitHub Pages: the shared Node backend is necessary. Hosting may require payment for persistent storage. No hosting account has been connected or deployed by this package.

## Actual Google Maps overview
Enable billing and **Maps JavaScript API** in Google Cloud Console. Create a browser API key restricted to Maps JavaScript API and allowed website referrers (for local testing: `http://localhost:3000/*`; add your production HTTPS domain when hosted). Set `GOOGLE_MAPS_JS_KEY` in the environment. Windows Command Prompt: `set "GOOGLE_MAPS_JS_KEY=YOUR_KEY"` then `npm start`. Do not commit keys. A browser Maps key is visible to visitors; restrictions are essential. Set `GOOGLE_MAP_ID` to your own JavaScript map ID for production; local tests default to Google's DEMO_MAP_ID. Google Maps loads on both reporting and dashboard pages, with category-coloured clickable markers and map click location selection on the reporting page. Without a valid key, the map falls back to OpenStreetMap. Maps links without explicit coordinates still show in the report list; drop a pin or enter coordinates to display them on the overview. This does not import Google Maps reviews or in-app feedback. Existing reports.json is compatible and should be retained when updating. API use may incur costs; configure quotas and billing alerts. Docs: https://developers.google.com/maps/documentation/javascript/get-api-key and https://developers.google.com/maps/documentation/javascript/advanced-markers/start

## Demonstrate
Use two browser windows. Submit a genuine report with permission in the first. Open the dashboard link in the second, refresh or wait 15 seconds, and open the Google Maps link. Sample reports are off by default. Before real public use, add moderation, rate limiting, access controls as appropriate, privacy/retention policies, and obtain organisation approval. Do not claim official affiliation or verified incidents.
