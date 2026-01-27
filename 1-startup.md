# Startup / Development Kickoff

These tasks can be done before design begins. That will provide us a ready and blank site for styling and customization as soon as design is approved.

- [ ] Create a repository for the project. See [Using a Startup
  Kit](#using-a-startup-kit) below.
- [ ] Grant repository access to relevant team members.
- [ ] Create an environment for staging the site, if not provided by a hosting
  partner. [Follow the Droplet Setup Guide]() to create a Devoted-hosted
  development server.
- [ ] Setup local development utilities for pulling copies of assets and
  databases.
- [ ] Setup a testing environment, likely with
  [Tugboat](https://www.tugboatqa.com/).
- [ ] Install necessary any plugins, modules, or extensions identified during
  discovery.
- [ ] Add relevant team members as CMS editors.  

## Using a Startup Kit

Currently we have one startup kit, [Devoted WordPress
Start](https://github.com/The-Devoted/devoted-wp-start).

Additional kits may be added as needed for more platforms in the future.

When using a startup kit, **follow the kit's wiki or readme** for specific
startup tasks. Tasks listed above are intentionally broad and not meant to
replace startup kit guides.

## Security

- [ ] Reroute the CMS's default login url, for example, `wp-login` and
  `wp-admin` for Wordpress.
- [ ] Setup login security rules such as limiting repeated login attempts and
  password content constraints.