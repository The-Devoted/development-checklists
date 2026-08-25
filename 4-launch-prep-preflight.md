# 🎯 Preflight and Launch Prep

## Decisions and Identifications

- [ ] Create an issue and/or milestone for the launch prep process.
  - [ ] Port these checklist items there where relevant.
- [ ] Determine launch date and time if not already set.
- [ ] Set a date for content freeze, if needed.
- [ ] Set a date for code freeze, if needed.
- [ ] Identify and document the production domain.
- [ ] Determine where DNS is managed.
  - [ ] Determine who will make DNS updates on launch day.
  - [ ] If The Devoted is handling DNS updates, verify we have access to DNS settings beforehand.
- [ ] Develop a deployment plan, if needed.
  - For example, sites that will be _physically relocating_ from staging to a new host will need a deployment plan.
- [ ] Develop a caching strategy.
- [ ] Identify the need for any monitoring tools (uptime, performance, etc).

## Preflight Tasks

- [ ] Create a Site Launch Plan document (use template in Google Drive).
  - [ ] Document high level items and decisions made within this checklist in the Site Launch Plan.
  - [ ] Share the Site Launch Plan with the team.
- [ ] Take before screenshots of site, if not already created (typically done during discovery).
  - [ ] Any important screens to capture that may have been created since the initial capture?
- [ ] Verify the any services/workflows needed by the deployment plan are working.

## Communications

- [ ] Contact any relevant hosting partners, third parties, etc and confirm:
  - [ ] They know what needs to occur,
  - [ ] They know what's needed from them,
  - [ ] What they need from us (an when),
  - [ ] They know all relevant times and dates.
- [ ] Ensure content and code freeze dates are communicated to the team.
- [ ] Set expectations with the client about what will happen on launch day.
- [ ] Confirm that we have launch approval from client.
- [ ] Identify anyone who will be involved from the client’s team, for example, IT? Security team?
  - [ ] What do they need from us, and when?
  - [ ] What do we need from them, and when?
- [ ] Create a list of renewal dates/reminders for the client, for example:
  - [ ] SSL Certificate(s)
  - [ ] Domain name renewals
  - [ ] Plugin / Third party subscriptions
  - [ ] Monitoring tools
- [ ] Create a launch event on Google Calendar, add relevant team members.

## Content

- [ ] Ensure the site has a favicon configured.
- [ ] Verify all content migrations are complete.
- [ ] Disable any migration-related plugins, modules, or tools.
- [ ] Run exports of site configs (and content where possible). Verify these exports run cleanly and correctly.
- [ ] Verify the 404 page is working correctly, styled as expected, and has appropriate language/content for strategic rerouting.
- [ ] Search for and replace any placeholder content, such as:
  - [ ] Lorem ipsum
  - [ ] Moby Dick database starter entries
  - [ ] TKTKTK
  - [ ] "Optional Superhead"
  - [ ] Links to # or example.com
- [ ] Run a 404 and broken image check.
  - [ ] Note we'll likely need to run another after the production domain is actively pointing to the new site. Ensure this is captured in a todo.
- [ ] Preview how the site looks when linked within social networks. Preview with metatags.io or similar tool.
