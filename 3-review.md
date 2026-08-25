# ✨ QA, Migration, Review, and Training

## Migration

- [ ] Ensure team member who will participate in migration have appropriate
  access to the CMS.
- [ ] Import any "automatic" exported migrated content.
- [ ] Review auto-migrated content for errors.
- [ ] Migrate manual content, leveraging for training where possible.
- [ ] Set a date for content freeze, if needed.
- [ ] After content imports, run a 404 and broken image check.

-------

## QA

### Performance

- [ ] Re-run performance tests and identify any issues that can be resolved or improved.
  - [ ] Create an issue to track these if needed.
- [ ] Ensure fonts are `woff2` format.
- [ ] Ensure images are minified before or during upload.
- [ ] Ensure next-gen efficient images (such as `webp` format) are being served where possible.

### Compliance

- [ ] GDPR / Cookie Statement
  - [ ] Implement banner/notification front-end functionality and dessign
  - [ ] Implement opt-out functionality
- [ ] Privacy Policy
- [ ] Accessibility Statement
- [ ] Copyright information
- [ ] Other legal or compliance needs specific to site?

### Accessibility

- [ ] Run accessibility tests and identify any issues to be resolved.
- [ ] Ensure the site has a skip-nav link (WordPress Block Themes will insert one automatically if a `<main>` tag exists).
- [ ] Ensure the site is navigible by keyboard.
- [ ] Enable `prefers-reduced-motion` and verify all motion effects are disabled.
- [ ] _More_to_add_here_

### SEO

- [ ] Preview how the site looks when linked within social networks. Preview with [metatags.io](https://metatags.io/) or similar tool.
- [ ] _More_to_add_here_

### Internal QA Capture

- [ ] Ensure relevant internal team members have GitHub access and can submit
  issues.
- [ ] Share a list of QA links with team, to ensure QA covers all necessary site
  areas, sections, templates, or obscure hidden corners. Include things such as:
  - [ ] Archive pages
  - [ ] Search results
  - [ ] 404 page
  - [ ] Directions for triggering any hidden content (sliders, drawers, etc).
- [ ] Set an end date for internal QA.

### Full Team / Client QA Capture

- [ ] Ensure all relevant team members on client side have GitHub access and
  understand how to submit issues.
- [ ] Provide QA instructions if needed (provide a video where possible).
- [ ] Set an end date for client QA review.

### Issue Mitigation

- [ ] Triage issues from internal & client QA
- [ ] Identify any issues that are launch blockers.
- [ ] Identify any issues that will be addressed postlaunch.
- [ ] Determine if the launch date is still feasible given the results of QA.
- [ ] Validate that all parties are clear on what will and will not be going
  live at launch.

-------

## Training

- [ ] Setup storage for any training videos, if needed.
- [ ] Schedule training sessions with relevant team members.
- [ ] Ensure User Guide is up to date, complete, and ready to share.
- [ ] Ensure custom fields have useful descriptive/help text.
- [ ] Review the project's docs or wiki for a list of training topics.
- [ ] Review the "special cases" list of any unusual sections, methodologies, or
  processes for the site: things that are unique to this project and can't be
  found in CMS documentation.
  - [ ] Ensure these things are documented clearly (provide videos where
    possible).
- [ ] Ensure training covers accessibility requirements and best practices in _content_, such as:
  - [ ] Alt text for images
  - [ ] Heading hierarchy + single H1s
  - [ ] Writing descriptive link text
  - [ ] Disabling autoplay for videos
- [ ] Ensure training covers web concepts used by editing tools, for example:
  - [ ] REM units for tools that allow dimension changes
  - [ ] _more_to_come_
- [ ] During training, identify any features or editing tools that should be disabled (for example, should we leave color pickers or dimension tools on in the WordPress block styles pane).

### Editor Experience

- [ ] Optimize media/asset tools in the CMS for the project's needs. Extend with organization or taxonomy tools as needed.
- [ ] Ensure the system provides a low-effort way for editors to add alt text to images.
- [ ] Ensure admin area is tidy, easy to navigate, and free of plugin/third party clutter.
- [ ] Identify and disable any tools that will overcomplicate the editing process, or have design-breaking potential for this client team.
