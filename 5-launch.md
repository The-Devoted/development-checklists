# 🚀 Launch!

## Error Logging & Reporting

- [ ] Check site logs for recurring notices, warnings, or errors.
- [ ] Create issues for and correct any recurring errors found in logs.
- [ ] Verify PHP error messages are suppressed on the front end.
- [ ] Disable database logging for production.
- [ ] Check the browser console for recurring errors.
- [ ] Create issues for and correct any errors found in the browser console.
- [ ] Check any CMS reporting tools for issues (for example, Site Health in WordPress or Drupal's Status Report).
- [ ] Create issues for and correct any issues identified by CMS tools.

## Analytics & SEO

- [ ] Configure Google Analytics or other analytics tool.
- [ ] Configure Google Tag Manager if applicable.
- [ ] Configure Google Search Console if applicable.
  - [ ] Make a todo list item to submit the new site immediately upon launch.
- [ ] Verify reporting of analytics tools: either only from the production environment, or separately if tracking dev environments.
- [ ] Ensure meta tags are filled out.
- [ ] Configure 301 redirects.
  - [ ] Use Regex matching to ensure no partial matches occur.
    - For example, Source: `^/news/?$` → Target `https://www.example.com/news/`.
  - [ ] Ensure target URLs have trailing slashes.
    - For example, use `.../news/` and **not** `.../news`.
  - [ ] After 301s are added, verify none of the redirected URLs 404.
- [ ] Disable any tools/settings that discourage search engine crawls enabled while the site was in development.
  - In WordPress, find this toggle in Settings > Reading > Search Engine Visibility

## Security

- [ ] Verify no API keys or sensitive credentials are stored in code.
- [ ] Ensure any content meant to be behind paywalls or gated sections is not accessible outside of its intended bounds.
- [ ] Verify that development related accounts/passwords have been reset or removed.
- [ ] Confirm any development-related plugins or modules are removed or disabled.
- [ ] Confirm that `robots.txt` or the corresponding HTTP header is configured
  to block traffic to any development or staging sites.
- [ ] Ensure correct permissions are set on any site config files such as `wp-config.php` for WordPress, or `settings.php` and `services.yml` for Drupal.
- [ ] If a generic `admin` account exists, create less obvious alternatives (use people's names).
  - [ ] Set the existing `admin` account's privileges to 0.

## Performance

- [ ] Ensure asset compression is enabled.
- [ ] Implement caching strategy.
- [ ] Ensure CDN is setup and verified to be working, if applicable.
- [ ] Ensure load balancer is setup and verified to be working, if applicable.
- [ ] Verify caching tools are working.
- [ ] Setup Cloudflare, if not included in hosting.

## Hosting

- [ ] DNS: confirm who is responsible and that they will be available to update
  the entries for launch.
- [ ] Setup HTTPS and test the SSL certificate.
- [ ] Configure redirects from www to the base URL (or vice-versa).
- [ ] Create and test any redirect rules.
- [ ] Create and test any reverse-proxy rules.
- [ ] Configure 301 redirects.

## Final Steps

- [ ] Get launch approval from client.
- [ ] Alert the client before the launch process begins.
- [ ] Update DNS entries.
- [ ] Update SSL certs as needed.
- [ ] Test the site manually for large obvious issues.
- [ ] Prepare to complete immediate Postlaunch tasks (add a link here if an issue exists).
