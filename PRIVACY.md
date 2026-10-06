# Privacy Policy

Initiative Board is a client-side web application that runs entirely in your browser. This document describes how your data is handled.

## Data Storage

All your initiative data is stored locally in your browser's **localStorage**. This data:

- Never leaves your device
- Is not sent to any server
- Is not shared with any third party
- Persists across browser sessions until you clear your browser data

Daily snapshots are stored under date-keyed entries (e.g., `now_2026-05-19`) in localStorage.

If you use the optional "Connect file" feature (Chrome/Edge only), a reference to your selected file is stored in **IndexedDB** so the connection can persist across sessions. The file handle requires re-granting permission when the browser restarts.

## External Resources

When you load the app, your browser contacts the **jsDelivr CDN** to fetch the Tabler Icons web font:

```
https://cdn.jsdelivr.net/npm/@tabler/icons-webfont@2.47.0/tabler-icons.min.css
```

This request is subject to [jsDelivr's privacy policy](https://www.jsdelivr.com/terms/privacy-policy-jsdelivr-net). jsDelivr may receive your IP address and standard HTTP request headers as part of serving this resource.

After the first load, the icon font is typically cached by your browser and no additional requests are made until the cache expires.

## No Analytics or Tracking

This app does not include any analytics, tracking scripts, cookies, or advertising. No data is collected about your usage.

## No Ads

This app contains no advertisements.
