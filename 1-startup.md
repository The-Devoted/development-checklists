# Startup / Development Kickoff

These tasks can be done before design begins. That will provide us a ready and blank site for styling and customization as soon as design is approved.

- [ ] Create a repository for the project. See [Using a Startup
  Kit](#using-a-startup-kit) below.
- [ ] Create a GitHub project board for the repo.
- [ ] Create any necessary additional issue labels for the type of work being
  done.
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

## Documentation

- [ ] Ensure the project has a readme file at the root.
- [ ] Add the following details to the readme:
  - [ ] A link to where the project is staged/development server.
  - [ ] A link to the project board.
  - [ ] A Development section with:
    - [ ] A list of high-level relevant technologies.
    - [ ] Instructions for how to contribute.
    - [ ] Visually separate this information to make reviewing the repo easier
      for clients and non-developers.
- [ ] Create a user guide within the site/as a CMS node or page.
- [ ] Port the relevant checklists from this repo into issues.
  - [ ] Create a Project_Name Launch Checklist issue for capturing specific preflight items for this project.
- [ ] If needed, begin a separate wiki or markdown docs for the project.
