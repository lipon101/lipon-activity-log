===================================================================
--- /dev/null
+++ lipon-activity-log/README.md
@@ -0,0 +1,148 @@
+# Lipon Activity Log
+
+> See every change made in your WordPress dashboard — who did what, and when.
+
+A lightweight, privacy-first activity log for WordPress. No external requests, no tracking, no fuss. Install, activate, done.
+
+[![License: GPL v2+](https://img.shields.io/badge/License-GPLv2%2B-blue.svg)](https://www.gnu.org/licenses/gpl-2.0.html)
+[![WordPress](https://img.shields.io/badge/WordPress-5.5%2B-21759b.svg)](https://wordpress.org/)
+[![PHP](https://img.shields.io/badge/PHP-7.4%2B-777bb4.svg)](https://www.php.net/)
+
+---
+
+## Why
+
+You inherited a site. Something broke. *Who changed what, and when?*
+
+Lipon Activity Log keeps a running record of everything that happens inside the WordPress admin so you can answer that question in seconds — without sending a single byte of data to a third party.
+
+## Features
+
+- **Comprehensive event tracking** across users, content, plugins, themes, settings, media, comments, taxonomies, and menus
+- **Dashboard widget** with the 10 most recent events at a glance
+- **Full log page** with search, multi-filter (action, type, date range), and pagination
+- **CSV export** for offline auditing or compliance reporting
+- **Configurable retention** from 7 to 365 days, auto-pruned daily
+- **Role-based visibility** — limit access to Admins, Editors+, or Authors+
+- **100% on-server** — no analytics, no telemetry, no external connections
+- **Zero configuration** — works the moment you activate it
+
+## What Gets Tracked
+
+| Area | Events |
+|------|--------|
+| **Auth** | Login, logout, failed login attempts |
+| **Users** | Registration, profile edits, role changes, deletions |
+| **Content** | Create, publish, draft, schedule, trash, delete (all post types) |
+| **Comments** | Approved, unapproved, spam, trashed, deleted |
+| **Plugins** | Activated, deactivated, updated, deleted |
+| **Themes** | Switched, updated, Customizer saves |
+| **Settings** | Site title, tagline, URL, and other option changes |
+| **Core** | WordPress core updates |
+| **Media** | Uploads and deletions |
+| **Taxonomies** | Categories, tags, and custom terms — added, edited, removed |
+| **Menus** | Navigation menus saved |
+
+## Installation
+
+### From the WordPress.org directory *(coming soon)*
+
+1. In your WordPress admin, go to **Plugins -> Add New**
+2. Search for "Lipon Activity Log"
+3. Click **Install**, then **Activate**
+
+### Manual install
+
+1. Download the latest [release](https://github.com/lipon101/lipon-activity-log/releases) or this repository as a ZIP
+2. Upload the `lipon-activity-log` folder to `/wp-content/plugins/`
+3. Activate it from the **Plugins** screen in your WordPress admin
+
+The **Activity Log** menu item will appear in your sidebar and logging starts immediately.
+
+## Usage
+
+- **Dashboard widget** — added to the WP admin home screen on activation
+- **Full log** — *Activity Log* in the admin sidebar
+- **Settings** — *Activity Log -> Settings* to adjust retention and viewer capability
+- **Export** — *Download CSV* button on the log page
+- **Clear** — *Clear All Entries* with a confirmation prompt
+
+## Requirements
+
+- WordPress **5.5** or higher
+- PHP **7.4** or higher
+
+## Privacy
+
+Lipon Activity Log is built with privacy as a first principle:
+
+- Nothing leaves your server, ever
+- No analytics, no tracking pixels, no remote calls
+- IP addresses and user-agents are stored locally for audit purposes only
+- Uninstalling the plugin drops the log table and removes all options
+
+## Performance
+
+One database row per event, written only inside the admin. **No code runs on the front end for visitors.** The log table is indexed on `user_id`, `action`, and `created_at` for fast filtering, and old entries are pruned automatically via WP-Cron.
+
+## Frequently Asked Questions
+
+**Will this slow down my site?**
+No. It only runs in the admin and writes a single indexed row per event.
+
+**Can non-admins see the log?**
+By default, only administrators. You can opt to allow Editors+ or Authors+ in **Settings**.
+
+**What happens when I delete the plugin?**
+The custom DB table is dropped and all plugin options are removed. Nothing is left behind.
+
+**Does it work with custom post types?**
+Yes — anything using the standard WP status transition hooks is logged automatically.
+
+## Development
+
+```bash
+git clone https://github.com/lipon101/lipon-activity-log.git
+```
+
+Drop the cloned folder into `wp-content/plugins/` of a local WordPress install and activate.
+
+### Project structure
+
+```
+lipon-activity-log/
+├── assets/
+│   ├── css/admin.css        # All admin styles
+│   └── js/admin.js          # Confirm prompts, filter UX, notice auto-dismiss
+├── includes/
+│   ├── class-lipoaclo-admin.php   # Menu, widget, asset enqueue, CSV export
+│   ├── class-lipoaclo-db.php      # Schema, queries, retention
+│   └── class-lipoaclo-logger.php  # WP hook bindings and event capture
+├── views/
+│   ├── log-page.php
+│   └── settings-page.php
+├── languages/
+│   └── lipon-activity-log.pot
+├── lipon-activity-log.php   # Plugin bootstrap
+├── uninstall.php            # Cleanup on delete
+└── readme.txt               # WordPress.org readme
+```
+
+## Changelog
+
+### 1.0.0
+
+- Initial release.
+
+## License
+
+Released under the [GPL-2.0-or-later](https://www.gnu.org/licenses/gpl-2.0.html) license.
+
+## Author
+
+**Md. Torikul Islam Lipon**
+GitHub: [@lipon101](https://github.com/lipon101)
+
+---
+
+If Lipon Activity Log saves you time, a star on this repository goes a long way. Thanks!
