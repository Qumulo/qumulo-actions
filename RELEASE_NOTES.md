## Qumulo Actions 1.3

**New: Uninstall Qumulo Actions.** The installer now adds an **Uninstall Qumulo Actions** app to
Applications (optional — leave it out under **Customize**). It finds every copy of Qumulo Actions on
the Mac, including old *QumuloTags* versions and stray copies in Downloads, and removes them along
with their entries in **Login Items & Extensions** — the usual cause of Qumulo Actions being listed
there more than once. You choose which copies to remove and whether to also remove your settings
and saved sign‑ins. It asks for an administrator password at most once, cancelling leaves everything
as it was, and Finder keeps running throughout. See *Uninstall Qumulo Actions* in the guide.

**Clusters on your local network get the menu.** A cluster on the Mac's local network — such as a
test cluster in a virtual machine — could silently lose the **Qumulo Actions…** menu because macOS
blocked the check that recognizes Qumulo shares. Qumulo Actions now explains why it needs local
network access when macOS asks, and keeps retrying for a few minutes, so the menu appears once
access is allowed without relaunching Finder. A cluster that is still starting up is picked up the
same way.

**A clear message for self‑signed certificates.** Connecting to a cluster with a certificate this Mac
doesn't trust used to fail with "transport failure: cancelled". It now says exactly what to do: turn
on **Accept self‑signed certificate** for that cluster in **Settings**. Loading a long‑lived token no
longer blames the token when the certificate is the real problem.

**Readable diagnostics in Console.** Qumulo Actions now records what it does — which shares are
recognized as Qumulo and why not, certificate problems, loads, and each uninstall step — in the
macOS system log. Filter Console on *Subsystem: com.qumulo.actions*; the guide has a short walkthrough.
Passwords and tokens are never logged.

## Qumulo Actions 1.2

**Names ending in a space or a period now work.** An item called `Final Draft ` or `Report.` used
to report that it could not be found, even though it was sitting in the folder — macOS and SMB
store the last character of such a name differently. **Info**, **Tags** and **Permissions** now
open normally for these items, and tagging and permission changes apply to them as expected. This
completes the unusual‑name work started in 1.1.

**Items created outside SMB open too.** A file or folder written by another protocol — NFS, S3 or
the REST API — whose name genuinely ends in a space, or contains a character such as `:` or `?`,
is now found correctly from the Mac. Previously only names created over SMB could be opened.

**Names read the way they look in Finder.** Any name affected by the above used to appear with a
blank box in the window title, in search results, in the permission dialogs and in the list of
skipped items. Names are now shown exactly as Finder shows them, with a trailing space displayed
as a space.

**No “Applies to” column on files.** The **Permissions** tab used to show an *Applies to* column
for files, where it could only ever read “This folder only” — inheritance describes what a folder
passes down to its contents, and a file has no contents. The column is now shown for folders only.
*Inherited From* still appears for files, since a file can inherit permissions from the folder
above it.

Signed, Apple‑notarized installer for macOS 14+ (Intel and Apple Silicon). Double‑click the `.pkg`
to install, then enable the Finder extension in **System Settings → Login Items & Extensions**.

## Qumulo Actions 1.1

**Files with unusual names now work.** Items whose names contain characters macOS permits but SMB
does not — `/`, `:`, `?`, `*`, `"`, `<`, `>`, `|` and `\` — used to report that they could not be
found, even though they were sitting in the folder. So did names with accented or international
characters, such as `café` or `piñata`. **Info**, **Tags** and **Permissions** now open normally
for all of these.

**Errors you can actually read.** When something goes wrong, the app now explains it in a sentence
— for example, "'report.pdf' no longer exists — it may have been deleted, moved or renamed" —
instead of a truncated block of cluster diagnostics.

**Bulk actions finish what they start.** Applying tags to a multi‑item selection, tagging folder
contents, and propagating permissions to children no longer stop at the first problem. If another
user deletes, moves or renames something while the run is in progress, that object is skipped and
every remaining object is still completed. Previously a single object could abandon the rest of
the run partway through, leaving a folder's tags or permissions inconsistent.

**See exactly what was skipped.** A run that could not update everything now lists the objects it
missed and why, rather than reporting only a count.

**No more partly‑tagged files.** One unavailable file in a selection could previously leave other,
perfectly healthy files with only some of their tags written. Each item is now applied
independently.

**Straight answers about missing items.** The **Tags** tab no longer shows an empty tag list for an
item that has been deleted — it tells you the item is gone. Removing a tag from a deleted item no
longer reports success.

Signed, Apple‑notarized installer for macOS 14+ (Intel and Apple Silicon). Double‑click the `.pkg`
to install, then enable the Finder extension in **System Settings → Login Items & Extensions**.

## Qumulo Actions 1.0.6

**One cluster, many addresses.** Clusters are now identified by their unique cluster ID, so different node FQDNs of the same cluster (e.g. `du72` and `du73`) are recognized as a single cluster. They share one sign‑in, reuse the same token, and appear as one row in **Settings** — no more re‑authenticating per node.

**Sibling nodes connect cleanly.** Mounting a second node of an already‑configured cluster no longer fails with a transport error: the new address inherits the cluster's certificate‑trust setting and existing sign‑in automatically.

**See a cluster's ID.** A new **?** button beside the cluster name in **Settings** shows the cluster's unique ID (UUID).

Signed, Apple‑notarized installer for macOS 14+ (Intel and Apple Silicon). Double‑click the `.pkg` to install, then enable the Finder extension in **System Settings → Login Items & Extensions**.

## Qumulo Actions 1.0.5

**Tag search refinements.** Search by tag **name**, **value**, or **both** with a clear selector, plus a **Contains / Exact** match toggle — value searches now work as expected.

**Finder sidebar.** The Qumulo Finder extension now attaches only to Qumulo shares, so its icon no longer appears on unrelated removable drives or other SMB shares.

**Stronger TLS defaults.** Connections validate the server certificate by default; accepting a self‑signed certificate is now an explicit per‑cluster opt‑in in **Settings → Accept self‑signed certificate**. Existing self‑signed clusters will need that option enabled once.

Signed, Apple‑notarized installer for macOS 14+ (Intel and Apple Silicon). Double‑click the `.pkg` to install, then enable the Finder extension in **System Settings → Login Items & Extensions**.
