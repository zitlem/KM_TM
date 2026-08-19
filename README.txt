TOOL MASTER — setup
===================

The whole app is one file: "Tool Master.html". Nothing to install, no accounts,
no internet needed. It keeps its data as ordinary files in a folder you choose.

FIRST MACHINE
-------------
1. Put "Tool Master.html" and "start.command" anywhere on the PC (Desktop is
   fine). They can live on each machine's local disk — only the DATA folder is
   shared.
2. Decide where the data lives. For one person, any local folder. For the shop,
   use a folder everyone can reach:
       - a network share / NAS  (\\SHOPNAS\toolmaster  or  smb://shopnas/toolmaster)
       - or a synced folder     (Dropbox / OneDrive / Google Drive)
3. Double-click start.command. The app opens in Chrome.
4. Click "Connect data folder" and pick the folder from step 2.
   Chrome asks once for permission to edit that folder — say yes.

EVERY OTHER MACHINE
-------------------
Same three steps: copy the two files over, run start.command, and point
"Connect data folder" at the SAME shared folder. That's it — they are now
looking at the same data.

Each machine remembers the folder, so from then on it just opens and loads.
Occasionally Chrome re-asks for permission; the header button then says
"Sync — allow folder access" and one click restores it.

HOW SHARING BEHAVES
-------------------
- Every machine re-checks the folder about every 10 seconds, and immediately
  when you switch back to the tab. Other people's changes appear on their own.
- Each job is its own directory, so two people working on two different jobs
  never touch the same file.
- If two people change the SAME job at the same time, the app stops and asks:
  "Keep mine" or "Take theirs". Nothing is overwritten silently.
- On a synced folder (Dropbox/OneDrive), changes travel as fast as that service
  syncs — usually seconds. A real network share is instant.

WHAT'S IN THE DATA FOLDER
-------------------------
    tools.json          every tool in the mill and lathe registries
    machines.json       the machine list
    settings.json       shop name and the two display options
    tools/
      T101-x3f9a2b.jpg  one photo per tool that has one
    jobs/
      mill/
        WO-1042/
          job.json        the setup: machine, rev, last run, notes, tool list
          setup-sheet.html  the printable sheet, rewritten on every save
      lathe/
        LA-500/
          job.json
          setup-sheet.html
      millturn/
        MT-100/
          ...

A job sits in the folder for its machine's type; change its machine to another
kind and the folder moves with it.

MACHINE TYPES
-------------
Settings > Machine types. Mill and Lathe are there from the start, Mill-turn is
there but hidden. Untick "Show" on any type to keep it out of the menus (its
jobs stay on disk, they just do not clutter the app), and add your own types —
EDM, Grinder, Saw, whatever the shop runs. Each type says which tool registry
its jobs pick from: mill tools, lathe tools, or both. The list is stored in
settings.json, so every machine on the shared folder gets the same types.

The setup sheets are plain HTML — double-click one to view or print it without
opening the app at all. Everything is readable text, so a normal file backup of
this folder is a complete backup of the shop's tooling data.

BROWSERS
--------
Chrome or Edge, opened through start.command. Safari and Firefox can run the
app but cannot write to a folder — they show a banner and keep data in that
browser only. A file:// page (double-clicking the HTML directly) is blocked by
Chrome from touching folders, which is why start.command exists.

The original design-tool version is kept as "Tool Master.dc.html" with
support.js and _ds/. Nothing in the standalone app uses them.
