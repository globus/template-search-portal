# 🧪 EXPERIMENTAL 🧪

**This is a working proof-of-concept of a static Globus-powered research search portal.**

**⚠️ Until this notice is removed, usage of this repository is NOT recommended and is provided as-is.**

**We're looking forward to sharing more details about this repository and more at [GlobusWorld 2024](https://www.globusworld.org/)!**


----

<img src="https://github.com/globus/example-data-portal/assets/694253/29723bc0-d692-47d5-bdc3-2625d3712cf3" height="200px" alt="Globus + static" />

This is a static research search portal powered by Globus.

View the result at: [globus.github.io/example-search-portal](https://globus.github.io/example-search-portal).

While this repository is a working example of a search portal, it is also a template for [creating your own static research search portal](#creating-your-own-static-research-search-portal).

----

### Creating Your Own Static Research Search Portal

1. Create a new repository from the [globus/example-search-portal](https://github.com/globus/example-search-portal) template.
   * <img width="188" alt="Screenshot 2024-03-11 at 12 24 22 PM" src="https://github.com/globus/example-data-portal/assets/694253/abffa5a5-86c8-47d9-be4b-f249d34505ab">
1. [Update your repository to allow publishing with GitHub Actions](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site#publishing-with-a-custom-github-actions-workflow).
1. [Ensure your GitHub Pages are configured to Enforce HTTPS](https://docs.github.com/en/pages/getting-started-with-github-pages/securing-your-github-pages-site-with-https)
1. Update the `static.json` to include:
   * `data.attributes.globus.search.index` – The Globus Search Index UUID that will be used source results from.
   * Optional: Set the `data.attributes.globus.search.facets` to enable facet-based filtering.
   * See the [static.json](#staticjson) type definitions for more configuration options.
1. **That's it!** The changes made (and any future changes) to the `static.json` will trigger a GitHub Action that will automatically build and deploy your research data portal to your GitHub Pages URL.

#### Private Globus Search Indexes (Authentication)

If your Globus Search Index is private, you'll want to include authentication to your portal.

1. Register an application on Globus – https://app.globus.org/settings/developers
   * You'll be creating an OAuth public client.
   * Update the **Redirects** to include your GitHub Pages URL + `/authenticate`, i.e., `https://globus.github.io/example-search-portal/authenticate`.
   * Optional: Specify the **Privacy Policy URL** and **Terms & Conditions URL** to the portal-provided routes, i.e. `https://globus.github.io/example-search-portal/privacy-policy`
1. Update the `static.json` to include:
   * `data.attributes.globus.application.client_id` – The UUID of the client created in **the previous step**.

#### Common Changes after Creating Your Portal
– **Result + Result Listing Rendering** – Update the `data.attributes.components.Result` and `data.attributes.components.ResultListing` to reference specific properties on your indexed data.
- **Edit/Remove the `CITATION` file** – Update the [`CITATION.cff`](CITATION.cff) file to reflect the appropriate citation information for your research data portal – [learn more about `CITATION` files](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-citation-files).
- **Removing this section of the README** – Remove this section from the `README.md` file or update the README to meet your needs.

----

# Features + Functionality

## Search Portal

- **Powered by [Globus](https://www.globus.org/)**
- Search for documents in a Globus Search Index with support for facets.


## GitHub Repository

- 📄 **Hosted via GitHub Pages** – Users can access your data portal at this repository's GitHub Pages URL. Use all the functionality built-in to GitHub pages to suit your needs, including [configuring a custom domain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/about-custom-domains-and-github-pages).

- 🚀 **Automated Deployments via GitHub Actions** – Any file changes will result in the deployment (and rebuild) of your data portal.
   - You can manually trigger a deployment by navigating to the **Actions** tab and selecting the **static** workflow.
   
- 🤖 **Dependabot** – A default [Dependabot](https://docs.github.com/en/code-security/dependabot) configuration ([`.github/dependabot.yml`](.github/dependabot.yml)) to keep your repository up-to-date with latest changes to [globus/static-data-portal](https://github.com/globus/static-data-portal).

### `static.json`

The type used for `data` by the [@globus/static-search-portal generator](https://github.com/globus/static-search-portal).

#### Type declaration


#### Supported Fields

#### Advanced Customization

##### JSONata Support
