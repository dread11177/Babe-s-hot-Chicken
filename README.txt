BABE'S HOT CHICKEN - WEBSITE PACKAGE
====================================

FILES
  index.html                                  The full website (one self-contained file).
  extras/standalone-orders-dashboard.html     Older separate dashboard page. Only works inside
                                              claude.ai (needs its sign-in). Not needed.

WHAT index.html CONTAINS
  Customer site     Hero, menu highlights, reviews, address/contact, Track your order.
  Ordering          Add items, checkout, order goes to the restaurant on WhatsApp.
                    There is no number at checkout; the restaurant gives the
                    number when confirming (see Dashboard).
  Staff login       "Staff" in the top bar / "Staff login" in the footer.
  Registration      New staff register; the admin approves with one tap.
  Dashboard         Order board (New / Preparing / Ready / Done), daily stat boxes,
                    "Notify customer" WhatsApp button, + Add order (paste WhatsApp message;
                    orders without a number get BHC-0001, BHC-0002, ...
                    automatically, and a number already on the board is rejected
                    as a duplicate).
  Admin only        Month-end sales export, staff and attendance export, Staff accounts
                    (approve, reject, remove, reset password).

HOW TO USE / HOST
  Open index.html in a browser, or upload it to any static host (Netlify, GitHub Pages,
  Cloudflare Pages, your own web server). No build step. It must be served over https
  (or opened as a file) because the staff login uses the browser's crypto features.
  Excel export loads the SheetJS library from cdnjs.cloudflare.com; if offline it
  saves a CSV instead, which Excel opens.

THINGS TO EDIT (search for these words in index.html)
  var WA='923441111804'     WhatsApp number that receives orders (customer checkout).
  var PRICES={}             Menu prices, e.g. "Chicken Tenders":850. Totals and revenue
                            appear once prices are filled in.
  var STAFF=[...]           Built-in logins (username, salted hash, role). Passwords are
                            not stored in readable form; ask whoever set them up to change.

HOW LOGINS AND STORAGE WORK (IMPORTANT)
  - There is no server. Orders and staff accounts are saved in the browser of the device
    in use. A different phone or computer has its own separate list.
  - Staff registered on one device can only be approved on that same device, unless both
    devices use shared storage (inside claude.ai, signed in with an invited account).
  - The staff login is a lock on the page, not strong security. Use long passwords.
  - Customer orders arrive by WhatsApp; staff paste them into "+ Add order".
  - For orders and staff accounts shared across devices on a normal website, you need a
    small backend (for example Firebase or Supabase).
