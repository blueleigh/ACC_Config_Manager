# ACC Config Manager -- User Guide

## Overview

ACC Config Manager is a desktop application for managing Assetto Corsa Competizione dedicated server configurations. It replaces manual JSON editing and FTP/SFTP file transfers with a visual form editor, a full JSON editor, diff previews, and organized config storage.

Configs are organized by season and week, making it easy to manage race-by-race settings across a full league calendar. You can push and pull configs directly to/from your server, preview changes before transferring, and keep a complete local history of every configuration.

---
## Installing

The .msi installer should work fine in Win 11. If you are running Win 10, you may want to use the .exe installer.

## First Launch: Setting Your Storage Path

On first launch, the app will ask you to select a folder to store your configs locally.

1. Click **Select Storage Folder**.
2. Choose an empty folder (or an existing one to reuse).
3. The app saves this path and loads the main interface.

To change the storage path later, click the **Change** button next to the path shown in the header.

---

## Adding a Server

Before you can push or pull configs, you need to add your ACC server's connection details.

1. Click **Manage Servers** in the header to expand the server section.
2. Click **Add Server**.
3. Fill in the required fields:
   - **Name** -- A friendly label (e.g., "League Server 1").
   - **Host** -- Hostname or IP address.
   - **Protocol** -- FTP or SFTP. The port auto-updates to the default (21 for FTP, 22 for SFTP).
   - **Port** -- Adjust if your server uses a non-standard port.
   - **Username** and **Password** -- Your server credentials.
4. (Optional) Click **Test Connection** to verify your credentials before saving.
5. Click **Save**.

The server now appears in your server list and is available for push/pull operations.

---

## Importing a Config from a Local Folder

If you already have config files on your machine, you can import them into your organized library.

1. Click **Import Config** in the header.
2. A folder picker opens. Select the folder containing your config files (it must contain at least `event.json` or `settings.json`).
3. The editor opens in import mode. Fill in the **Season** and **Week** fields at the top (e.g., Season: "2026Spring", Week: "1").
4. Review or edit the config using the form editor or JSON editor.
5. Click **Save**.

The config is saved to your storage folder under `{Season}/{Season}_Week{Week}/` with metadata extracted automatically from the config files.

---

## Copying an Existing Config

Use **Copy** for a quick clone within the same season. This is the fastest way to set up next week's config from this week's.

1. Right-click on a config in the browser.
2. Click **Copy**.
3. A new config is created in the same season with an incremented week number.

---

## Duplicating a Config to a Different Season/Week

Use **Duplicate** when you want to place the copy in a specific season and week.

1. Right-click on a config in the browser.
2. Click **Duplicate**.
3. In the dialog, enter the target **Season** (autocomplete suggestions appear from existing seasons) and **Week**.
4. Click **Duplicate**.

---

## Editing a Config

1. Click on a config in the browser (or right-click and select **Open**).
2. The editor opens in **Form** view by default, with collapsible sections:
   - **Event Settings** -- Track, weather, session timing, and time multiplier.
   - **Event Rules** -- Pitstop rules and restrictions.
   - **Assist Rules** -- Driver assist limitations.
   - **Settings** -- Server name, passwords, car group.
3. To edit raw JSON, click the **JSON** button in the toolbar. File tabs let you switch between configuration.json, settings.json, event.json, and others.
4. Use **Undo/Redo** buttons (or Ctrl+Z / Ctrl+Y) to step through your edit history.
5. Click **Save** when done.

Note: `entrylist.json` and `bop.json` are only editable through the JSON editor due to their complex nested structure.

---

## Pushing a Config to Your Server

1. Open the config you want to push.
2. Make sure a server is selected from the server list.
3. Click **Push** in the editor toolbar.
4. The push dialog opens showing:
   - **File checkboxes** -- Toggle which files to include. By default only `event.json` is selected.
   - **Diff preview** -- Side-by-side comparison of your local files vs. what's currently on the server, with modification timestamps.
5. Review the changes, adjust file selection as needed.
6. Click **Confirm Push**.
7. A progress bar shows each file uploading. On completion you'll see a success message.

---

## Pulling a Config from Your Server

1. Select a server from the server list.
2. Click **Pull from Server** in the header.
3. The pull dialog opens showing the current server files. Choose a destination:
   - Select an **existing season folder**, or click **Create New Folder** and type a new season name.
   - Enter a **Week** number.
4. Click **Pull**.
5. A diff preview shows the server files. Review and confirm.
6. Files download with a progress bar. On completion, the config appears in your browser.

---

## Browsing Server Files

You can inspect files on your server without pulling them.

1. Select a server and open the server browser.
2. The dialog lists all files in the server's `/cfg` directory with file sizes and modification times.
3. Click any file to view its contents in a read-only editor with syntax highlighting.
4. Use the **Copy** button to copy file contents to your clipboard.

---

## Tips

- **Context menu** -- Right-click any config in the browser for quick actions: Open, Copy, Duplicate, Rename, Delete.
- **Search and filter** -- Use the search bar in the browser to find configs by name.
- **Keyboard navigation** -- Arrow keys work in context menus and browser lists.
- **Encoding** -- The app automatically handles ACC's UTF-16 LE file encoding. No manual conversion needed.

