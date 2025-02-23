# Quick Start Guide for APIMatic Docs as Code
This guide helps you get started quickly with APIMatic’s Docs as Code solution to generate and deploy your API portal.
## Set Up Prerequisites
•	Obtain an API Key:
Request an authentication key by following the instructions provided in this section or by emailing support@apimatic.io.
•	Install Required Tools:
o	Git for repository management
o	A code editor (e.g., VSCode)
o	Optional: A static web server (e.g., http-server via npm) for local portal preview
•	Clone the Sample Repository:
Download the sample Docs as Code repository from GitHub.
## Prepare the Build Input
Your build input consists of several components:
•	Spec Directory:
Place your API specification file(s) (e.g., OpenAPI) here. APIMatic will automatically detect and merge multiple specs if needed.
•	Content Directory:
Add your custom Markdown guides, changelogs, or tutorials.
Tip: Include a toc.yml file to define your navigation structure.
•	Static Directory (Optional):
Store images, logos, or PDFs that you want to include in your portal.
•	Build Configuration File:
Create a JSON build file, with name ending with APIMATIC-BUILD.json) at the repository root. Customize fields such as portal title, logo, theme, and SDK generation options as needed. These will allow you to customize the generated portal.
Example:
```
{
  "$schema": "https://titan.apimatic.io/api/build/schema",
  "buildFileVersion": "1",
  "generatePortal": {
    "apiSpecs": [
      "spec/your-api-spec.yaml"
    ],
    "languageConfig": {
      "http": {}
    }
  }
}
```
