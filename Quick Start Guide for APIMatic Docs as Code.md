# Quick Start Guide for APIMatic Docs as Code
This guide helps you get started quickly with APIMatic’s Docs as Code solution to generate and deploy your API portal.
## Set Up Prerequisites
- Obtain an API Key:
Request an authentication key by following the instructions provided [in this section](https://docs.apimatic.io/account-management/obtaining-auth-keys/) or by emailing support@apimatic.io.
-	Install Required Tools:
	- Git for repository management
  	- A code editor (e.g., VSCode)
	- Optional: A static web server (e.g., http-server via npm) for local portal preview
- Clone the Sample Repository:
Download the sample Docs as Code repository from [GitHub](https://github.com/apimatic/static-portal-workflow).
## Prepare the Build Input
Your build input consists of several components:
-	Spec Directory:
Place your API specification file(s) (e.g., OpenAPI) here. APIMatic will automatically detect and merge multiple specs if needed.
-	Content Directory:
Add your custom Markdown guides, changelogs, or tutorials.
Tip: Include a toc.yml file to define your navigation structure.
-	Static Directory (Optional):
Store images, logos, or PDFs that you want to include in your portal.
-	Build Configuration File:
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
## Generate Your API Portal
Choose one of the two methods based on your API spec size and complexity:

### Option 1: Using the Sync API
- Step 1:
Submit your build input to the APIMatic Portal Generation Sync endpoint. A successful call returns a ZIP file.
- Step 2:
Extract the ZIP file and host the static portal on your preferred web server.
Note: The sync API is ideal for most scenarios but has a 4-minute processing limit.

### Option B: Using the Async API
- Step 1:
Submit your build input to the Async endpoint. You will receive an ID and status endpoint.
- Step 2:
Poll the status endpoint until the portal is ready.
Step 3:
Once complete, download and extract the ZIP file containing your API portal.
Tip: Use this method for large or complex API specifications.

## Automate Deployment (Optional)
Leverage GitHub Actions to automate the entire process:
- Fork the sample repository containing workflow files (e.g., DeployStaticPortal.yml for sync or DeployStaticPortalAsync.yml for async).
- Configure the workflow with your repository secrets.
- Whenever a commit is pushed to the master branch, the workflow is triggered automatically and the deployed server will reflect the updated portal.
