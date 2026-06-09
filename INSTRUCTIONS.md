# DocusaurOps Documentation Template — Instructions

This is the DocusaurOps documentation template. Follow these instructions when setting up a new installation or applying an update.

---

## DO NOT MODIFY — Protected Files

The following files must not be modified by consumers. They are managed by the platform and changes will break the site.

- `documentation/src/server/*` — Server configuration that ensures the application is served correctly in the App Service behind the Application Gateway.
- `.github/workflows/deploy-docs.yml` — GitHub Actions workflow that deploys the documentation site to the DocusaurOps platform.
- `documentation/docusaurus.config.ts` — Docusaurus configuration file. The following properties must not be changed:
  - `url` — Used in search results. An incorrect URL will cause broken references.
  - `baseUrl` — Must match the Application Gateway path. An incorrect value will result in a broken site (404 errors).
  - `webpackConfig.plugins.EnvironmentPlugin` — Default environment variables must remain. Additional variables may be added if needed.
  - `presets.docs.routeBasePath`: Use template value for new installation. Don't add/update it otherwise. 
  - **If other properties already exists, leave them untouched (ex: `themeConfig`,`presets`):**
  
---

## MODIFY WITH CARE — Advanced Configuration Files

The following files in the `documentation/` folder may be modified beyond their default values for advanced customization. Default values must always be preserved unless intentionally overridden.

- `tailwind.config.js` — Tailwind CSS global configuration. Requires technical expertise to modify.
- `tsconfig.json` — TypeScript configuration.
- `babel.config.js` — Babel presets for Docusaurus. Requires technical expertise. Should only be modified in very specific cases.
- `package.json` — Project dependencies. New packages may be added if needed.
- `src/css/custom.css` — Company main brand theme. Consumers are encouraged to keep the default theme but may change it if needed.
- `.gitignore` — Files excluded from version control.
- `.env.docusaurops` — File describing the DocusaurOps setup. Needs to be commited along the code. Do not add to .gitignore.

---

## FREE TO REPLACE — Content Files

The following files and folders are intended to be replaced with consumer-specific content:

- `sidebars.ts` — Navigation sidebar configuration.
- `static/*` — Static assets used in the documentation (images, files, etc.).
- `docs/*` — Documentation content. This is where all consumer content should be placed. **Never update this folder is already exists**

---

## Required Constraint — Home Page Meta Tag

The documentation home page **must** include the following meta tag:

- **Tag name:** `docusaurOpsPageType`
- **Value:** `site_home`

This tag can be placed in a regular `.md` file, a React `.tsx` file, or an `.mdx` file. It is used to register the site in the DocusaurOps portal. Without it, the site will not appear in the DocusaurOps portal listing. **If a home page is already defined, update it and add this tag in it**.
