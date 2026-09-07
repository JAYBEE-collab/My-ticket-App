# EventPass — Digital Ticketing & Check-In App

A self-contained, single-file event ticketing system: create events, add guests, generate
QR-coded digital tickets, distribute them (email / WhatsApp / native share), and scan
tickets at the door to check guests in.

## Live demo
Deployed via GitHub Pages: `https://<your-username>.github.io/<your-repo-name>/`

## Features
- Create events and manage guest lists
- Auto-generate a unique QR-coded boarding-pass-style ticket per guest
- Export tickets as PNG or PDF
- Share tickets via WhatsApp (text) or native Share (image attached, on supported mobile browsers)
- Email tickets via [EmailJS](https://www.emailjs.com/) (free tier available)
- Camera-based QR scanner to validate/check in guests at the event

## Deployment (GitHub Pages)
1. Create a new **public** GitHub repository.
2. Upload `index.html` to the **root** of the repo (filename must be exactly `index.html`, all lowercase).
3. Go to **Settings → Pages**, set Source to "Deploy from a branch", branch `main`, folder `/ (root)`, Save.
4. Your site goes live at `https://<username>.github.io/<repo-name>/` within about a minute.
5. Any future edits: edit `index.html` in GitHub's web editor and commit — the live site updates automatically.

## Required setup for full functionality

### Email sending
The Email button requires a free [EmailJS](https://www.emailjs.com/) account:
1. Sign up at emailjs.com and connect an email service (e.g. Gmail).
2. Create an email template with variables matching what's sent: `to_email`, `to_name`,
   `event_name`, `event_date`, `event_time`, `event_venue`, `ticket_id`, `ticket_image`, `message`.
3. Copy your **Public Key**, **Service ID**, and **Template ID** into the app's settings/config.

### QR Scanner
- Requires HTTPS (GitHub Pages provides this automatically) and camera permission.
- Test on a phone or a laptop with a working webcam — grant camera access when prompted.

### Native Share (WhatsApp/Email/etc. with image attached)
- Uses the Web Share API — supported on most mobile browsers (Chrome/Safari on phones),
  not supported on most desktop browsers. On desktop it will fall back to downloading the image instead.

## Tech stack
Vanilla HTML/CSS/JS, no build step. External libraries loaded via CDN:
- QRCode.js — QR code generation
- ZXing — QR code scanning
- html2canvas + jsPDF — ticket export as PNG/PDF
- EmailJS — email delivery
- Font Awesome — icons

## Local development
Just open `index.html` directly in a browser, or run a local server for camera-dependent
features to work (browsers restrict camera access on `file://` URLs):

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.
