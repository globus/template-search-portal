<p align="center">
  <img src="https://github.com/globus/template-data-portal/assets/694253/8c55d1e3-1ecd-47ea-8288-73c79cd2c953" height="100px" alt="Globus" />
   <br/>
  <strong>🧪 BETA 🧪</strong>
  <br/>
  <strong>This is template repository used to generate a static Globus-powered research search portal.</strong>
  <br/>
</p>

----

View the result at: [globus.github.io/template-search-portal](https://globus.github.io/template-search-portal).

While this repository is a working example of a search portal, it is also a template for [creating your own static research search portal](#creating-your-own-static-research-search-portal).

----

# Features + Functionality

## Search Portal

- **Powered by [Globus](https://www.globus.org/)**
- Search for documents in a Globus Search Index with support for facets.
- **Optional Authentication** – Authenticate users to access private Globus Search Indexes.
- **Globus Transfer Integration** – Transfer files directly from the search portal to your Globus-connected storage.

## GitHub Repository

- 📄 **Hosted via GitHub Pages** – Users can access your data portal at this repository's GitHub Pages URL. Use all the functionality built-in to GitHub pages to suit your needs, including [configuring a custom domain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/about-custom-domains-and-github-pages).

- 🚀 **Automated Deployments via GitHub Actions** – Any file changes will result in the deployment (and rebuild) of your data portal.
   - You can manually trigger a deployment by navigating to the **Actions** tab and selecting the **static** workflow.
   
- 🤖 **Dependabot** – A default [Dependabot](https://docs.github.com/en/code-security/dependabot) configuration ([`.github/dependabot.yml`](.github/dependabot.yml)) to keep your repository up-to-date with latest changes to [globus/static-search-portal](https://github.com/globus/static-search-portal).

### Creating Your Own Static Research Search Portal

1. Create a new repository from the [globus/template-search-portal](https://github.com/globus/template-search-portal) template.
   * Using the following URL: https://github.com/new?template_name=template-search-portal&template_owner=globus
   * <img width="188" alt="Screenshot 2024-03-11 at 12 24 22 PM" src="https://github.com/globus/template-data-portal/assets/694253/abffa5a5-86c8-47d9-be4b-f249d34505ab">
1. [Update your repository to allow publishing with GitHub Actions](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site#publishing-with-a-custom-github-actions-workflow).
   - **IMPORTANT** The built-in GitHub Action workflows in your new repository will fail until you've updated this setting.
1. [Ensure your GitHub Pages are configured to Enforce HTTPS](https://docs.github.com/en/pages/getting-started-with-github-pages/securing-your-github-pages-site-with-https)
1. Update the `static.json` to include:
   * `data.attributes.globus.search.index` – The Globus Search Index UUID that will be used source results from.
   * Optional: Set the `data.attributes.globus.search.facets` to enable facet-based filtering.
   * See the [static.json](#staticjson) type definitions for more configuration options.
1. **That's it!** The changes made (and any future changes) to the `static.json` will trigger a GitHub Action that will automatically build and deploy your research data portal to your GitHub Pages URL.

#### Private Globus Search Indexes (Authentication)

If your Globus Search Index is private, you'll want to include authentication to your portal.

1. Register an application on Globus – https://app.globus.org/settings/developers
   * You'll be creating an OAuth public client; This option is presented as _"Register a thick client or script that will be installed and run by users on their devices"_.
   * Update the **Redirects** to include your GitHub Pages URL + `/authenticate`, i.e., `https://{username}.github.io/{repository}/authenticate`
     * If you have [configured your GitHub Pages to use a custom domain](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site), this will be `https://{domain}/authenticate`
     * It is important to note that Globus Auth **requires HTTPS**.
1. Update the `static.json` to include:
   * `data.attributes.globus.application.client_id` – The UUID of the client created in **the previous step**.

#### Common Changes after Creating Your Portal
- **Result + Result Listing Rendering** – Update the `data.attributes.components.Result` and `data.attributes.components.ResultListing` to reference specific properties on your indexed data.
- **Edit/Remove the `CITATION` file** – Update the [`CITATION.cff`](CITATION.cff) file to reflect the appropriate citation information for your research data portal – [learn more about `CITATION` files](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-citation-files).
- **Removing this section of the README** – Remove this section from the `README.md` file or update the README to meet your needs.

----

### `static.json`

The type used for `data` by the [@globus/static-search-portal generator](https://github.com/globus/static-search-portal).

#### Type declaration

See: https://github.com/globus/static-search-portal/blob/main/docs/modules.md#data


#### Field Types

#### Advanced Customization

##### JSONata Support
