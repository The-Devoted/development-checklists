# Preflight and Launch

## Planning

- [ ] Create an issue and/or milestone for the launch prep process.
  - [ ] Port these checklist items there where relevant.
- [ ] Determine launch date and time if not already set.
- [ ] Set a date for content freeze, if needed.
- [ ] Set a date for code freeze, if needed.
- [ ] Develop a caching strategy.
- [ ] Identify and document the production domain.
- [ ] Determine who manages DNS.
- [ ] Verify the deployment process is working.
- [ ] Take before screenshots of site.
- [ ] Add site to [web.archive.org](http://web.archive.org/).
- [ ] Identify the need for any monitoring tools (uptime, performance, etc).

## Communications

- [ ] Contact any relevant hosting partners, third parties, etc and confirm:
  - [ ] They know what needs to occur,
  - [ ] They know what's needed from them,
  - [ ] What they need from us (an when),
  - [ ] They know all relevant times and dates.
- [ ] Ensure content and code freeze dates are communicated to the team.
- [ ] Set expectations with the client about what will happen on launch day.
- [ ] Confirm that we have launch approval from client.
- [ ] Identify anyone who will be involved from the client’s team, for example,
  IT? Security team?
  - [ ] What do they need from us, and when?
  - [ ] What do we need from them, and when?
- [ ] Create a list of renewal dates/reminders for the client, for example:
  - [ ] SSL Certificate(s)
  - [ ] Domain name renewals
  - [ ] Plugin / Third party subscriptions
  - [ ] Monitoring tools
- [ ] Create a launch event on Google Calendar, add relevant team members.

## Content

- [ ] Verify all content migrations are complete.
- [ ] Disable any migration-related plugins, modules, or tools.
- [ ] Run exports of site configs (and content where possible). Verify these
  exports run cleanly and correctly.
- [ ] Verify the 404 page is working correctly, styled as expected, and has
  appropriate language/content for strategic rerouting.
- [ ] Search for and replace any placeholder content, such as lorem ipsum or links to example.com

## Error Logging & Reporting

- [ ] Check site logs for recurring notices, warnings, or errors.
- [ ] Create issues for and correct any recurring errors found in logs.
- [ ] Verify PHP error messages are suppressed on the front end.
- [ ] Disable database logging for production.
- [ ] Check the browser console for recurring errors.
- [ ] Create issues for and correct any errors found in the browser console.
- [ ] Check any CMS reporting tools for issues (for example, Site Health in
  WordPress or Drupal's Status Report).
- [ ] Create issues for and correct any issues identified by CMS tools.

## Analytics & SEO

- [ ] Configure Google Analytics or other analytics tool.
- [ ] Configure Google Tag Manager if applicable.
- [ ] Verify reporting of analytics tools: either only from the production
  environment, or separately if tracking dev environments.
- [ ] Ensure meta tags are filled out.
- [ ] Configure 301 redirects.

## Security

- [ ] Verify no API keys or sensitive credentials are stored in code.
- [ ] Ensure any content meant to be behind paywalls or gated sections is not
  accessible outside of its intended bounds.
- [ ] Verify that development related accounts/passwords have been reset or
  removed.
- [ ] Confirm any development-related plugins or modules are removed or disabled.
- [ ] Confirm that `robots.txt` or the corresponding HTTP header is configured
  to block traffic to any development or staging sites.
- [ ] Ensure correct permissions are set on any site config files such as
  `wp-config.php` for WordPress, or `settings.php` and `services.yml` for
  Drupal.

## Performance

- [ ] Ensure asset compression is enabled.
- [ ] Implement caching strategy.
- [ ] Ensure CDN is setup and verified to be working, if applicable.
- [ ] Ensure load balancer is setup and verified to be working, if applicable.
- [ ] Verify caching tools are working.

## Hosting

- [ ] DNS: confirm who is responsible and that they will be available to update
  the entries for launch.
- [ ] Setup HTTPS and test the SSL certificate.
- [ ] Configure redirects from www to the base URL (or vice-versa).
- [ ] Create and test any redirect rules.
- [ ] Create and test any reverse-proxy rules.
- [ ] Configure 301 redirects.

## Final Steps

- [ ] Alert the client before the launch process begins.
- [ ] Update DNS entries.
- [ ] Update SSL certs as needed.
- [ ] Test the site manually for large obvious issues.
