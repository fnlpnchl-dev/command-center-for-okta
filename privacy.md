# Privacy Policy

**Command Center for Okta** (the "extension"), by Fenil Panchal.
An independent extension. Not affiliated with, endorsed by, or sponsored by
Okta, Inc. Okta is a trademark of Okta, Inc.

Last updated: October 20, 2026 (version 1.5.0)

## The short version

The extension sends nothing to its developer or to anyone else. It has no
server, no analytics, no telemetry, and no crash reporting. Every request it
makes goes to your own Okta organization, from your own browser, using the Okta
session you are already signed in to.

What you choose to keep, such as notes, snapshots and access reviews, stays in
your browser on this computer. So does what it keeps so screens show at once:
the lists of groups, applications and group rules, where each group is pushed,
the certificate check, and what the home screen last showed. The developer cannot see any of it, because it never leaves
your machine.

## What the extension reads

While you have your Okta admin console open, the extension issues read-only
requests to your organization's Okta API on your behalf. Depending on which
screen you open, that can include:

- user profiles, status, and sign-in history
- the kinds of factor people have enrolled (never a secret or a phone number)
- group definitions, membership, and group rules
- applications, their assignments, and their provisioning settings
- authentication policies and their rules
- administrator role assignments
- system log events

This is your own Okta directory data, read with your own permissions. The
extension cannot see anything your Okta administrator role cannot already see.

When you open a person, a group or an application in the admin console, the
extension reads a short summary of it for the launcher's card, in the
background, at the lowest priority: a few requests, plus what it already keeps.
**Have the card ready before it is opened**, in Settings, turns this off, and the
card is then read only when you open the launcher. What you type in the
launcher's search is sent only to your own Okta org, as a search.

If you turn on **Live activity**, the extension also reads your org's system log
about once a minute while the panel is open, to show admin changes as they
happen. It is off until you turn it on, and it pauses whenever the panel is
hidden, the browser is offline, or your org's rate limit runs low.

## What the extension stores

Everything below is kept in Chrome's storage for this extension, on this
computer, in this browser profile. None of it is sent anywhere.

**Your preferences**, which apply in every org:

| Key | What it is |
| --- | --- |
| `theme` | light or dark |
| `density` | row spacing |
| `zoom` | text size |
| `railPinned` | whether the navigation rail is pinned open |
| `syncFollow` | whether the panel follows the admin console |
| `syncPush` | whether the console follows the panel |
| `consoleActions` | whether the launcher is shown in the admin console |
| `consoleWarm` | whether the launcher's card is read before it is opened |
| `consolePos` | which corner of the admin console the launcher sits in |
| `liveStrip` | whether Live activity is on, how often it checks, and when it pauses |
| `exportColumns`, `exportPreamble` | the columns you chose for exports, and whether files start with a description of themselves |
| `schemaVersion` | the layout of this storage, so an update can carry it forward |

**What you choose to keep, per org.** Each is stored under that org's address,
so one org's data is never shown in another:

| What | What it holds | Kept because |
| --- | --- | --- |
| Notes | the text you write, and which person, group, application or rule it is about | you wrote a note |
| Watchlist | the groups and applications you watch, and their member counts when last checked | you chose to watch one |
| Snapshots | the members of one group or application at the moment you took it: each person's Okta id, name and login | you took a snapshot, to compare with later |
| Stale access checks | for each of the last 24 checks: when, at which threshold, and how many were found; and which people, by the kind of finding and their Okta id only, with when each was first found | you ran a check, so the next one can say what is new, what was resolved, and how long the rest have been open |
| Exceptions | for a direct assignment: the person and the application, by name and Okta id, the reason you wrote, the end date you gave, and who wrote it and when; up to 500 | you recorded why an assignment exists |
| Stale access settings | the profile attribute that holds an end date, and up to 50 pairs of applications or groups you said nobody should hold together, by name and Okta id | you named them |
| Verified removals | for each of up to 50 reviews: the people a Remove decision named, by name and Okta id, whether Okta still assigned them their applications (by id), and when that was checked | you pressed Verify |
| Saved comparisons | up to 30 comparisons: which people, groups, applications, rules, policies or roles were compared, by Okta id and name, and what each held when you saved it, by Okta id only: its groups, applications, members or permissions | you saved a comparison, to see later what has changed |
| Access reviews | the people and access under review, your decisions, and your comments | you started a review |
| Privileged applications | which applications you marked as privileged | you marked them |
| Since you last looked | the counts on the home screen the last time you saw it, so it can show what changed | you opened the home screen |

**Screens kept so they show at once, per org.** So that the home screen,
Groups, Applications, Rules, Certificates and where a group is pushed show
straight away after a reload or in a new session, the extension keeps the last
answer it read:

| What | What it holds |
| --- | --- |
| Groups | each group's name, description, type, and member, application and push mapping counts |
| Applications | each application's name, label, status, sign-on mode and provisioning features |
| Group rules | each rule's name, status, condition and the groups it assigns to |
| Where a group is pushed | for each of the last 200 groups whose push mappings it read: which applications push it, the group each one writes to, by name, each mapping's status, last push and last error, Okta's count of its mappings, and which applications it is assigned to. Kept with them, once per org: the name, status, sign-on mode and features of each application able to push a group |
| Certificates | each signing application's and SAML identity provider's name and status, the id of the certificate it uses, that certificate's expiry date, and when it was read. Never the certificate or any other part of a key |
| The home screen | what each card last showed: its count, title and the up to three people, applications or objects it names, such as who is locked out, who was granted an admin role, or who is assigned a privileged application directly, by name and username. And the tenant's counts and the week of sign-in failures by day |

Only the home screen names people, and only the few its cards show. No member
list or profile is kept this way. Anything older than fifteen minutes is read
again from Okta in the background and replaced, except a certificate's expiry
date, which changes only when somebody rotates it and is read again after a day. **Sync** beside each list, and
**Refresh** on the home screen, read it from Okta at once. The panel's refresh
button deletes all of these, and a list is kept only while it is smaller than a
fixed size.

You can delete any note, snapshot or access review from the panel, and stop
watching anything you watch. Removing the extension from Chrome deletes
everything it stored.

**To a file, only when you ask.** An export is written to your downloads folder
as CSV or JSON. It contains the Okta data on the screen you exported, plus your
Okta org's address, your Okta username, and the time, so the file can be used
as audit evidence. Nothing is written without you clicking Export, and the file
goes only where your browser puts downloads.

**In memory, briefly.** Okta API answers are cached inside the extension's
background worker so the same data is not read twice and your org's Okta rate
limits are respected. Live activity keeps the events it has shown in memory
too, and the launcher's card for each of the last 60 people, groups and
applications you opened is kept for three minutes. This is ordinary memory, never written to disk, and Chrome discards it when
the panel closes or the worker stops.

## Credentials

The extension never asks for, receives, or stores an Okta password, API token,
client secret, or private key.

It works by reusing the session you already have. A small script running on
your admin console page reads the anti-forgery token that the console itself
places in the page, and issues same-origin requests with your existing session
cookie. Chrome keeps that cookie. The extension never reads it, and could not
send it anywhere, because the requests go only to your own Okta organization.

Because the reads use your session, they appear in your Okta System Log
attributed to you, exactly as if you had clicked through the admin console
yourself. That is deliberate: your organization's audit trail stays accurate.

## Read-only

The extension cannot change anything in Okta. This is enforced in three
independent places:

1. the script on the console page accepts only `GET` and `HEAD` requests
2. it rejects any path that is not a same-origin `/api/v1/` path
3. there is no interface anywhere in the extension that submits a change

The rule builder and policy builder validate and explain what you write and
produce what Okta would need, but they cannot save. You copy the result into
Okta yourself.

## Where the extension runs

Only on your Okta admin console, and only on these paths:

```
https://*.okta.com/admin/*         https://*.okta.com/report*
https://*.oktapreview.com/admin/*  https://*.oktapreview.com/report*
https://*.okta-emea.com/admin/*    https://*.okta-emea.com/report*
```

It does not run on Okta sign-in pages, on end-user dashboards, or on any other
website, and it cannot see which other sites you visit.

## Third parties

There are none. No data is sold, shared, or transferred to anyone. No
third-party code, library, font, or service is loaded at runtime. All code ships
inside the extension package.

## Permissions, and why each one exists

| Permission | Why |
| --- | --- |
| `storage` | keep your preferences, the notes, watchlist, snapshots and reviews you choose to keep, and the screens kept so they show at once, as listed above |
| `sidePanel` | the interface is a Chrome side panel, so it can sit beside the console |
| `scripting` | put the console-page script back into an admin tab that was already open, for example after the extension updates |
| host access to the admin console paths above | follow which console screen you are on, and issue the same-origin read-only requests described above |

## Children

The extension is a tool for enterprise identity administrators and is not
directed at children.

## Changes

Material changes to this policy will be published with a new "last updated"
date before the version they apply to is released.

## Contact

Questions about this policy: **panchal.fenil09@gmail.com**
