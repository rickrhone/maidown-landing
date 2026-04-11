# MaidOwn Landing Page

Marketing landing page for [MaidOwn](https://maidown.com) — scheduling and invoicing software for cleaning businesses. One-time purchase, no subscriptions.

## Deployment

This site deploys automatically via **Cloudflare Pages** on every push to `main`.

- No build step required — pure HTML/CSS
- Cloudflare Pages build settings: framework = None, build command = empty, output directory = `/`

## Mailchimp Form

The waitlist email capture form embed code goes in `index.html` at the `<!-- MAILCHIMP_FORM_PLACEHOLDER -->` comment (appears in Section 7 — CTA). CSS overrides in the `<style>` block will style it automatically to match the page.
