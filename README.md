# Grand Cherokee Service Log

A single-page maintenance tracker for a 2024 Jeep Grand Cherokee Summit (3.6L Pentastar V6,
ZF 8HP75, Quadra-Trac). Enter your odometer reading and it tells you what's due, how soon,
and how much it matters.

Everything runs in the browser. No accounts, no server, no data leaves the phone.

## What it does

Four tabs along the bottom:

- **Due** — odometer entry, a plain-language "what needs attention" headline, and the list of
  anything overdue or coming up. Tap the status counts to filter.
- **Schedule** — every service ordered by mileage, with cost estimates, DIY ratings, and details.
- **History** — toggle between completed maintenance and repairs, with a running spend total.
- **Settings** — driving conditions, in-service date, backup/restore, calendar export, and reset.

Other features:

- Every scheduled service ordered by the odometer reading it comes due at
- Importance rating on each item — Critical, High, Medium, Low
- Normal vs. severe duty intervals (severe is Jeep's Schedule B: short trips, heat, towing, dust)
- One-tap check-off — clears a service even if you haven't reached its due mileage
- Or a full entry with cost, shop, parts, and invoice number
- Estimated shop cost on every service, plus a DIY-yourself parts figure
- A DIY rating on each item — do it yourself, do it if you're handy, or leave it to a shop
- Completed maintenance history, newest first
- Wear items — brakes, tires, battery — shown as expected windows rather than hard intervals
- Learns your actual monthly mileage from odometer entries and projects dates from it
- Separate log for repairs and unscheduled work, with a running spend total
- Calendar export (.ics) with a one-week-ahead alert on each upcoming service
- JSON backup and restore
- Works offline once installed

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole app — markup, styles, and logic |
| `sw.js` | Service worker, for offline use |
| `manifest.json` | Makes it installable to a home screen |
| `icon-192.png` / `icon-512.png` | App icons |

## Publishing it to GitHub Pages

1. Create a new repository on GitHub named `jeep-service-log`. Leave it public — Pages
   requires that on free accounts.
2. On the repo page choose **Add file → Upload files**, drag in all five files, and commit.
   Upload the files themselves, not the folder that contains them; `index.html` must sit at
   the top level of the repo.
3. Go to **Settings → Pages**. Under *Build and deployment*, set **Source** to
   *Deploy from a branch*, **Branch** to `main`, folder `/ (root)`. Save.
4. Wait a minute or two, then open `https://YOUR-USERNAME.github.io/jeep-service-log/`.

To install it on your phone: open that link in the browser, then **Share → Add to Home Screen**
on iPhone, or the **Install app** prompt in Chrome on Android. It opens full screen and works
without a signal.

## Updating it later

Edit `index.html`, then **bump the version number in `sw.js`** — change `gc-service-log-v1`
to `v2`, and so on. Without that bump, phones that already cached the app will keep showing
the old version. Commit both files together.

## Where your data lives

Records are stored in the browser's local storage, tied to that browser on that device.
They survive closing the app but not clearing site data, and they do not sync between your
phone and your computer. Use **Download backup** occasionally and keep the file somewhere
safe; **Restore from backup** reads it back, including onto a second device.

## Accuracy

Intervals follow Chrysler's published schedule for the 2024 WL with the 3.6L V6, with
conservative adjustments where real-world wear tends to run ahead of the book — notably
transmission fluid, which Jeep calls fill-for-life. Wear-item windows (brakes, tires) are
typical ranges, not promises; the inspection at every tire rotation is what gives you the
real number. Check the owner's manual for your exact build before any major service.
