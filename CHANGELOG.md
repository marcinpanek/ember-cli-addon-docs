# Ember CLI Addon Docs Changelog

## 0.3.0

- [ BREAKING ] If you have any config for `ember-router-scroll` in your dummy app's `config/environment`, you can remove it. (The `<body>` element is the only scrollable element now.)
- [ BREAKING ] Renames `{{docs-navbar}}` to `{{docs-header}}`
- [ BREAKING ]The setup for your dummy app's `/docs/template.hbs` is simpler and should be updated. [Check out the docs for example usage](https://ember-learn.github.io/ember-cli-addon-docs/latest/docs/components/docs-viewer).
- The navigation section of `{{docs-viewer}}` has a new contextual component `{{viewer.section}}` that you should use to group your guides. (The nav layout was designed to expect a section for the first item). [See the docs for example usage](https://ember-learn.github.io/ember-cli-addon-docs/latest/docs/components/docs-viewer).
- [ BREAKING ] Removes yield for alt-logo in docs-hero. The block below the byline is now yielded. (We will introduce a new api for custom project logos later).
- Adds `style` arg to docs-hero which can be "light" or "dark". Defaults to "light".

## 0.2.4

- Fix EMFILE errors for developers on APFS without watchman installed

## 0.2.0

- **Breaking change**: Versioned deployment has been overhauled, impacting the deployed layout of files on `gh-pages` and changing the API available in `config/addon-docs.js`. See [Migrating to 0.2.x](#migrating-to-02x) below for more details.
- **Breaking change**: We no longer attempt to abort from within when running `ember deploy` on a non-`master` branch or a non-default Ember Try scenario. You should instead guard the invocation of `ember deploy` itself in your `.travis.yml` or equivalent.

### Migrating to 0.2.x

Addon Docs 0.2.x uses a different structure for deploys than 0.1.x in order to accomodate versioned documentation. For details on the new structure, read the new [Deploying](https://ember-learn.github.io/ember-cli-addon-docs/docs/deploying) section of the guide. In short, before deploying with 0.2.x, you should consider manually migrating your existing site to a subdirectory on your `gh-pages` branch. If you want, you can add an entry in `versions.json` for this subdirectory after you've done a deploy with 0.2.x.

In particular, if you have an `index.html` and/or `404.html` in the root of your `gh-pages` branch, you should move or delete them to allow Addon Docs to set up its own redirection logic.

## 0.1.4

- **Breaking change**: You now must always pass the file extension into the DocsSnippet component: {{docs-snippet name='foo.js'}}

- Addon docs now works in Fastboot

And more bug fixes.

## 0.1.3

Bug fixes.

## 0.1.2

Style tweaks.

## 0.1.1

More style updates. Updates:

- Use `docs-link` anywhere in your MD files where you were using `link-to`, as we now style by class rather than descendents.

## 0.1.0

First release! We can start tracking "breaking" changes before 1.0.

If you were already using addon docs, this release

- Removes the global app navbar. You can see how we're using it in this dummy app - just move `{{docs-navbar}}` from `application.hbs` to `index.hbs`.

- Updates the design of the docs-viewer, to include the project name & version. This data is inferred from your project's `package.json`.
