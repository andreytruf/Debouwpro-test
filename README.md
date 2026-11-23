# DE BOUW PRO — Test

Staging for the Dutch DE BOUW PRO V2 website. The initial website snapshot comes from [Playground commit 3e17934](https://github.com/andreytruf/Debouwpro-playground/commit/3e179343ab99b9fa2aecb28763c269a562e9b032). See the [source handoff and contact rule](https://github.com/andreytruf/Debouwpro-playground/blob/3e17934/docs/HANDOFF-TEST-MAIN.md) and the [legal reconciliation](https://github.com/andreytruf/Debouwpro-playground/blob/3e17934/docs/privacy-cookies/RECONCILIATION.md).

## Local checks

Use Node.js 22 or newer.

```sh
npm ci
npm run check
npx playwright install chromium
npm test
```

`npm run dev` serves the static build on http://127.0.0.1:8787. The build writes public files to `dist/`. The GitHub Actions workflow runs a dry run and tests.

## Staging deployment

The Wrangler configuration targets the dedicated `debouwpro-test` Worker with static assets. The intended staging address is https://debouwpro-test.andrey-57c.workers.dev/. Use `npm run deploy` from an authenticated Cloudflare session after verifying the intended account and Worker. The staging configuration uses a workers.dev address. Keep `noindex, nofollow` in the HTML and response headers and retain the crawler policy in `robots.txt`.

After staging publication, run `node scripts/audit-privacy.mjs` against the staging address and verify the reported status, indexing headers, cookies, storage and external page requests. Review Cloudflare settings separately from the browser audit.

## Contacts and legal status

Use **hallo@debouwpro.nl**, **info@debouwpro.nl** and **+31 6 12350850**. The main mailbox uses the Dutch spelling with **a**.

The separate legal documents retain **CONCEPT** status. The older combined draft is historical reference. The proposed 24/60-month guarantee in the Particulieren draft requires formal approval before any promotional use. Main and production release require separate explicit approval of the reviewed version.
