# Qumulo Actions for Mac

View and edit **tags**, **permissions** and **file info** for items on mounted Qumulo SMB shares,
directly from Finder's right‑click menu.

![The Qumulo Actions window showing a folder's owner, group and permission entries on the Permissions tab](screenshots/actions-ui-screenshot.png)

## Download

Download the installer for the version you want from the files in this repository:
**`QumuloActions-<version>.pkg`** — the highest version number is the latest. Open the file, then
click **Download raw file**. Every installer is signed with a Developer ID and notarized by Apple.

**Requirements:** macOS 14 (Sonoma) or later, Intel or Apple Silicon, and a Qumulo SMB share
mounted in Finder.

## Install in three steps

1. Double‑click the `.pkg` and follow the prompts (administrator password required).
2. In **System Settings → General → Login Items & Extensions**, click the **ⓘ** next to
   **QumuloActions** and turn on **File Provider**.
3. Right‑click a file on a Qumulo share → **Qumulo Actions…**, then sign in on the **Settings** tab.

## Documentation

- [**Install & User Guide**](GUIDE.md): setup, each tab, troubleshooting, uninstalling, and reading
  the logs in Console.
- [**Release Notes**](RELEASE_NOTES.md): what changed in each version.

To remove Qumulo Actions, run **Applications → Uninstall Qumulo Actions** (see the guide).
