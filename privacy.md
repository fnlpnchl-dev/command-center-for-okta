# Privacy Policy

**Command Center for Okta** (the "extension"), by Fenil Panchal.
An independent extension. Not affiliated with, endorsed by, or sponsored by
Okta, Inc. Okta is a trademark of Okta, Inc.

Last updated: October 29, 2026 (version 1.18.0)

## The short version

The extension sends nothing to its developer or to anyone else. It has no
server, no analytics, no telemetry, and no crash reporting. Every request it
makes goes to your own Okta organization, from your own browser, using the Okta
session you are already signed in to.

The one exception is the Assistant, which is off until you connect a model of
your own to it. Then what you type there is sent to the endpoint you chose,
with instructions naming what the extension can read and your org's user
profile attribute names. No person, group member or log entry is sent: the
extension reads Okta itself. See [The Assistant](#the-assistant-when-you-connect-a-model).

What you choose to keep, such as notes, snapshots and access reviews, stays in
your browser on this computer. So does what it keeps so screens show at once:
the lists of groups, applications and group rules, where each group is pushed,
the certificate check, and what the home screen last showed. Lists of people
and their access, such as an application's users, a group's members, or one
person's groups and applications, are held only in the browser's memory while
Chrome runs, never on disk. The developer cannot see any of it, because it never leaves
your machine.

## What the extension reads

While you have your Okta Admin Console open, the extension issues read-only
requests to your organization's Okta API on your behalf. Depending on which
screen you open, that can include:

- user profiles, status, and sign-in history
- the kinds of factor people have enrolled (never a secret or a phone number)
- group definitions, membership, and group rules
- applications, their assignments, and their provisioning settings
- policies and their rules, the applications each is assigned to, and the device assurance policies, user types and authenticators their rules name
- network zones: the addresses, countries and networks each holds
- event hooks and inline hooks, and API tokens with the admin roles of the people who own them
- administrator role assignments
- System Log events

This is your own Okta directory data, read with your own permissions. The
extension cannot see anything your Okta administrator role cannot already see.

When you open a person, a group or an application in the Admin Console, the
extension reads a short summary of it for the launcher's card, in the
background, at the lowest priority: a few requests, plus what it already keeps.
**Have the card ready before it is opened**, in Settings, turns this off, and the
card is then read only when you open the launcher. What you type in the
launcher's search is sent only to your own Okta org, as a search.
What you type into Workflows › **Build a flow** is not sent anywhere, not
even to Okta: it is read in the panel and forgotten when you leave the screen.

If you turn on **Live activity**, the extension also reads your org's System Log
about once a minute while the panel is open, to show admin changes as they
happen. It is off until you turn it on, and it pauses whenever the panel is
hidden, the browser is offline, or your org's rate limit runs low.

If you watch a group or an application, the extension reads your org's System
Log every 20 seconds while the panel is on screen, for changes to the members
of what you watch, and the home checks each watched one in full every 5
minutes. Nothing is read for the watchlist while the panel is hidden, or when
nothing is watched.

## What the extension stores

Everything below is kept in Chrome's storage for this extension, on this
computer, in this browser profile. None of it is sent anywhere.

**Your preferences**, which apply in every org:

| Key | What it is |
| --- | --- |
| `theme` | light or dark |
| `density` | row spacing |
| `zoom` | text size |
| `timeFormat` | whether times are written 12-hour or 24-hour |
| `timeZone` | the time zone Okta's times are written in |
| `railPinned` | whether the navigation rail is pinned open |
| `syncFollow` | whether the panel follows the Admin Console |
| `syncPush` | whether the console follows the panel |
| `consoleActions` | whether the launcher is shown in the Admin Console |
| `consoleWarm` | whether the launcher's card is read before it is opened |
| `consolePos` | which corner of the Admin Console the launcher sits in |
| `workflowChecks` | which follow-up checks Workflows › Health runs |
| `liveStrip` | whether Live activity is on, how often it checks, and when it pauses |
| `massThreshold` | how many of one kind of change within an hour the home calls a mass change |
| `exportColumns`, `exportPreamble` | the columns you chose for exports, and whether files start with a description of themselves |
| `assistant` | the Assistant's endpoint, model name, and how its key is sent, when you connect a model |
| `assistantKeyKept` | the Assistant's key, only if you tick **Remember the key on this computer**; otherwise it is held in memory, below |
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
| Saved reports | up to 50 Assistant reports: the words you asked with, and the plan, which is the reads it makes (searches, and groups and applications by the name you used or the Okta id you chose) and the steps that combine them. Never what a report found | you pressed **Save as a report**, so it runs again without the model |

**Screens kept so they show at once, per org.** So that the home screen,
Groups, Applications, Rules, Certificates and where a group is pushed show
straight away after a reload or in a new session, the extension keeps the last
answer it read:

| What | What it holds |
| --- | --- |
| Groups | each group's name, description, type, and member, application and push mapping counts |
| Applications | each application's name, label, status, sign-on mode and provisioning features, the format it makes a person's username in, and the NameID a SAML application of its own sends. Configuration only, nothing about any person |
| Group rules | each rule's name, status, condition and the groups it assigns to, when Okta created and last updated it, and how many people it excludes (never who), with the names of the groups it names |
| Where a group is pushed | for each of the last 200 groups whose push mappings it read: which applications push it, the group each one writes to, by name, each mapping's status, last push and last error, Okta's count of its mappings, and which applications it is assigned to. Kept with them, once per org: the name, status, sign-on mode and features of each application able to push a group |
| Certificates | each signing application's and SAML identity provider's name and status, the id of the certificate it uses, that certificate's expiry date, and when it was read. Never the certificate or any other part of a key |
| The home screen | what each card last showed: its count, title and the up to three people, applications or objects it names, such as who is locked out, who was granted an admin role, who made a mass change, or who is assigned a privileged application directly, by name and username. And the tenant's counts and the week of sign-in failures by day |

Only the home screen names people, and only the few its cards show. No member
list or profile is kept this way. The groups, applications and group rules stay
as they were read until you press **Sync** beside them, unless Okta's rate limit
cut that read short, when they are read again at the next visit. The rest is
read again from Okta in the background once older than fifteen minutes, and
replaced, except a certificate's expiry date, which changes only when somebody
rotates it and is read again after a day. **Sync** beside each list, and
**Refresh** on the home screen, read it from Okta at once. The panel's refresh
button deletes all of these, and a list is kept only while it is smaller than a
fixed size.

**Kept as the group rules are read, per org.** Okta keeps no earlier version of
a group rule, and its System Log records no edit to one. So that a rule's page
can show what it said before it changed, each time the rules are read the
extension compares each one with the copy it last read:

| What | What it holds |
| --- | --- |
| Rule history | for each group rule, the copy last read (its name, status, condition, the groups it assigns to by Okta id, and how many people it excludes, never who), when it was first and last read, and up to 10 earlier versions, with when each change was seen |

The panel's refresh button does not delete the rule history, since an earlier
version cannot be read from Okta again. Removing the extension deletes it.

**Held in memory while Chrome runs, never on disk.** So that the screens that
list people show at once when they are opened again, the extension holds what
it last read there in `chrome.storage.session`. That is the browser's memory:
it is never written to disk, and Chrome clears it when it closes. It holds:

- for an application whose Users tab you opened, each person assigned: their
  name, username and app username, how they are assigned, its status, what the
  assignment sets inside the application, and whether their app username
  matches the application's format. And, when you checked its groups, the
  people in them who are not assigned it, by name and username, with the group;
- for a group whose Members tab you opened, each member's name, username,
  email, department, status and last sign-in;
- for a person you opened, the groups they are in and the applications they
  are assigned, with what each assignment sets.

The Assistant's key is held there too, unless you ask for it to be
remembered on this computer.

**Sync** on each of those reads it from Okta again, and the panel's refresh
button lets all of it go. An application with too many people to hold is not held, and
when room is needed the one opened longest ago goes first.

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
applications you opened is kept for three minutes. For a group a rule feeds,
how each person's membership arrived (by a rule, or by hand) is kept for an
hour, under that org's address, so a large group can be checked a few hundred
people at a time: Okta answers that one membership at a time. This is ordinary memory, never written to disk, and Chrome discards it when
the panel closes or the worker stops.

## The Assistant, when you connect a model

The Assistant is off until you connect a model to it: an endpoint that takes
a Chat Completions request, the name of a model, and a key if the endpoint
needs one. The endpoint is yours to choose: an AI provider's API, your
company's gateway, or a model running on your own computer. The extension has
no server of its own in between.

**What is sent, each time you press Ask**, and only to that endpoint:
- the words you typed;
- instructions that list the read-only questions the extension can run, the
  shapes of answer it accepts, today's date, and your org's user profile
  attribute names (such as `department` or `employeeType`), read from Okta's
  user schema.

**What is never sent:** any person, group member, application assignment, log
entry, or anything else the extension has read from Okta. The model answers
with a plan. The extension checks it, says it back in its own words, and runs
it against Okta itself, read only, through the same path as every other screen.
**What was sent to the model**, under each answer, shows the exact text.

What you type is your own: if you type a person's name, it is sent as you
typed it.

**The key** is held in the browser's memory until Chrome closes, unless you
tick **Remember the key on this computer**, which writes it to the extension's
storage on this computer. It is sent only to the endpoint, in the header you
chose.

**Forget** removes the endpoint, the model, the key, and Chrome's permission to
reach that address. Saved reports stay; they run without the model.

What the endpoint does with a request is set by whoever runs it, under your
agreement with them. The developer of this extension has no access to it.

## Credentials

The extension never asks for, receives, or stores an Okta password, API token,
client secret, or private key.

It works by reusing the session you already have. A small script running on
your Admin Console page reads the anti-forgery token that the console itself
places in the page, and issues same-origin requests with your existing session
cookie. Chrome keeps that cookie. The extension never reads it, and could not
send it anywhere, because the requests go only to your own Okta organization.

Because the reads use your session, they appear in your Okta System Log
attributed to you, exactly as if you had clicked through the Admin Console
yourself. That is deliberate: your organization's audit trail stays accurate.

## Read-only

The extension cannot change anything in Okta. This is enforced in three
independent places:

1. the script on the console page accepts only `GET` and `HEAD` requests
2. it rejects any path that is not a same-origin `/api/v1/` path
3. there is no interface anywhere in the extension that submits a change

The rule builder and policy builder validate and explain what you write and
produce what Okta would need, but they cannot save. You copy the result into
Okta yourself. The Assistant is held to the same: its plans run through the same
read-only path, its rules open in the simulator, and its Workflows build sheets
are for you to build.

## Where the extension runs

Only on your Okta Admin Console, and only on these paths:

```
https://*.okta.com/admin/*         https://*.okta.com/report*
https://*.oktapreview.com/admin/*  https://*.oktapreview.com/report*
https://*.okta-emea.com/admin/*    https://*.okta-emea.com/report*
```

It does not run on Okta sign-in pages, on end-user dashboards, or on any other
website, and it cannot see which other sites you visit.

## Third parties

There are none of the extension's choosing. No data is sold or shared. No
third-party code, library, font, or service is loaded at runtime. All code ships
inside the extension package.

When you connect a model to the Assistant, the endpoint you chose receives what
is described in [The Assistant](#the-assistant-when-you-connect-a-model), at your
direction, and nothing else.

## Permissions, and why each one exists

| Permission | Why |
| --- | --- |
| `storage` | keep your preferences, the notes, watchlist, snapshots and reviews you choose to keep, and the screens kept so they show at once, as listed above |
| `sidePanel` | the interface is a Chrome side panel, so it can sit beside the console |
| `scripting` | put the console-page script back into an admin tab that was already open, for example after the extension updates |
| host access to the Admin Console paths above | follow which console screen you are on, and issue the same-origin read-only requests described above |
| optional host access (`https://*/*`, `http://localhost/*`, `http://127.0.0.1/*`) | asked for only when you connect a model to the Assistant, and only for that endpoint's address; given back when you press Forget. Nothing is asked for at install |

## Children

The extension is a tool for enterprise identity administrators and is not
directed at children.

## Changes

Material changes to this policy will be published with a new "last updated"
date before the version they apply to is released.

## Contact

Questions about this policy: **panchal.fenil09@gmail.com**
