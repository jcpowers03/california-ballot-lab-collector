# California Ballot Lab count collector

Checks the official California Proposition 40, 41 and 42 results for the [public tracker](https://california-ballot-lab.jcpowers03.chatgpt.site/returns).

The workflow targets every five minutes. GitHub can delay or drop scheduled jobs; an enabled schedule is not proof that automatic collection is running. The tracker shows the last successful check and warns when it is more than 15 minutes old. Use **Actions → Collect official California returns → Run workflow** for an immediate hosted check, or the tracker's signed-in source-check button.

Each run obtains a short-lived GitHub identity token. The site verifies its signature, audience, expiry, repository and owner IDs, main branch and exact workflow before fetching fixed official sources. There is no long-lived collector secret. Pull requests and forks cannot invoke the writer.

The site validates all 58 counties against statewide totals, preserves the previous snapshot on failure, and stores every changed snapshot plus the original feeds. Runs read back the saved result before reporting success. The workflow never changes forecast assumptions or publishes site code.

Collection ends December 11, 2026 at 6 p.m. Pacific (December 12 at 02:00 UTC). A final scheduled job disables the workflow. Frozen forecasts and the count archive remain available.

This repository contains the scheduler only. The site source and persistent archive are maintained in Sites.
