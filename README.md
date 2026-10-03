# GeM Comply AI

A browser-based prototype for exploring government e-procurement document review, risk scoring, and audit workflows.

- **Live demo:** [gem-comply.vercel.app](https://gem-comply.vercel.app/)
- **Repository:** [Ansh-vibe/gem-comply](https://github.com/Ansh-vibe/gem-comply)

> **Prototype notice:** This is a demonstration project, not an official Government of India, Ministry of Petroleum & Natural Gas, GeM, or NIC service. It is not affiliated with or endorsed by those organizations. Do not use it to make procurement, eligibility, fraud, or compliance decisions, and do not enter real credentials or sensitive documents.

## What it demonstrates

- A portal-style interface with a landing page, sample dashboard, document verification view, rules page, audit ledger, and printable report.
- PDF selection, in-browser PDF preview, basic PDF file checks, and SHA-256 file hashing.
- A sample risk review with PAN/GSTIN fields, configurable demo rules, weighted scores, and a result breakdown.
- A locally simulated hash-linked audit ledger with an integrity check.
- Browser speech synthesis for the on-screen guide and report controls.

The verification view currently displays **hard-coded sample extraction text** after the simulated progress indicator. It does not run OCR on the uploaded PDF. PAN/GSTIN and risk results are demo checks, not live verification against government or registry systems.

## Technology

- Next.js 16 with the App Router
- React 19 and TypeScript
- Tailwind CSS 4
- PDF.js for rendering PDF files in the browser
- Browser `localStorage` and IndexedDB for demo state and selected file data
- Vercel Analytics in production

The Next.js home page embeds the main interface from `public/gem-comply.html` in a full-screen iframe.

## Run locally

### Requirements

- Node.js 20.9 or newer
- pnpm 12.3.4 (declared in `package.json`)

### Start the development server

```bash
git clone https://github.com/Ansh-vibe/gem-comply.git
cd gem-comply
corepack enable
pnpm install
pnpm dev
```

Open [http://localhost:3000](http://localhost:3000).

### Build and run for production

```bash
pnpm build
pnpm start
```

No application environment variables or external API credentials are required for the current demo.

## Data and security notes

- The selected PDF is previewed and hashed in the browser. The prototype stores its file data in the browser's IndexedDB and stores interface state, rules, and ledger entries in `localStorage`.
- The sign-in screen is a UI simulation; it does not authenticate users or connect to NIC/eOffice SSO.
- The ledger is a browser-local demo hash chain, not a distributed blockchain or tamper-proof production audit system.
- The interface includes sample metrics and placeholder records. Registry checks, document OCR, digital-signature validation, and real fraud detection are not implemented.
- Browser storage is not a secure records system. Clear this site's browser data to remove locally stored demo data.

## Deploy

The project can be deployed to Vercel by importing the GitHub repository and using the standard Next.js build settings. No environment variables are needed for the current prototype.

## Project structure

```text
app/
  layout.tsx        Root layout, metadata, and production analytics
  page.tsx          Full-screen wrapper for the demo interface
  globals.css       Global styles
components/         Shared UI components
lib/                UI helpers
public/
  gem-comply.html   Main prototype interface and browser-side logic
package.json        Scripts and dependencies
```

## License

No license file is currently included. All rights reserved unless the repository owner specifies a license.
