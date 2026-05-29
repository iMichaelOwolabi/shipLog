# shipLog
ShipLog is an AI-powered release communications workflow built on n8n

It automatically transforms every GitHub release into two tailored outputs: a technical digest for the dev team and a plain-English announcement for stakeholders; delivered instantly to the right Slack channels and logged to dedicated Notion changelogs. No manual write-up, no copy-pasting, no one forgetting to update the changelog.

## Problem Statement
Every time the team ships a release, someone has to manually write release notes, communicate what changed to two different audiences, post to Slack, and update documentation. This takes 15–30 minutes per release, produces inconsistent output, and often gets skipped under time pressure. As release frequency increases, this becomes a growing bottleneck.

### Solution
ShipLog listens for a GitHub release event and automatically:

Fetches all PRs merged since the previous release
Passes them to a Claude AI Agent which writes two audience-specific outputs in a single call
Posts the dev-facing notes to Slack #releases and logs them to a Notion dev changelog
Posts the stakeholder-facing announcement to the product Slack channel and logs it to a separate Notion stakeholder changelog

The entire process completes in under 30 seconds from release publish to Slack delivery.

 ### Tech Stack

* n8n — workflow orchestration
* GitHub — release trigger and PR data source
* Jira — ticket context for release notes
* Claude AI — dual-audience release note generation
* Slack — delivery to #releases and stakeholder channel
* Notion — persistent changelog for both audiences

### Current Status
ShipLog is fully built and operational. Known items on the backlog:

* Deduplicate GitHub webhook events firing multiple times per release
* Improve Notion notes formatting for richer text rendering
* Add Jira ticket lookup as an AI Agent tool for deeper release context

### Business Value

* Saves 15–30 minutes of manual work per release
* Ensures consistent, professional release communication every time
* Eliminates the risk of stakeholders being uninformed after a deploy
* Creates a searchable, permanent release history in Notion automatically
* Scales with release frequency at zero additional effort
