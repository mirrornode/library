# Osiris platform preservation status

DATE: 2026-05-29
SOURCE: mirrornode/mirrornode-platform app/osiris
TARGET: mirrornode/osiris app/osiris
STATUS: PARTIAL / BLOCKED

WHAT CHANGED:
- app/osiris/main.py was copied into mirrornode/osiris.
- app/osiris/rotan_routes.py was not copied because the connector blocked that write.
- No deletion was performed in mirrornode-platform.
- No PR C was opened.

VERIFIED:
- Source main.py blob: b2f82ab18394e3f17e941ad4b6ea0a7c4412f38f
- Source rotan_routes.py blob: da53a8a48b90580a8caf9599876dcc32f04b14cc
- Osiris preservation commit for main.py: fddc492a47b53de16e1c3033c58d0bf3bc3e2f8e

NEXT ACTION:
- Preserve rotan_routes.py through a manual git workflow.
- Then open PR C removing only app/osiris from mirrornode-platform.

DO NOT TOUCH:
- PR 5
- PR 6
- Stripe
- Health routes
- Env config
- Anything outside app/osiris

BOUNDARY:
app/osiris is an Osiris Python surface and belongs outside the Next.js platform repo. Deletion remains held until full preservation proof exists.
