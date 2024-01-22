<!-- BEGIN_TF_DOCS -->
# Terraform Cloud Foundation

Code which manages configuration and life-cycle of all the Terraform Cloud
module in the private registry. It is designed to be used from a dedicated
VCS-Driven Terraform Cloud workspace that would provision and manage the
configuration using Terraform code (IaC).

## Permissions

To manage the module in the private registry from that code, provide a token
from an account with `manage modules` access. Alternatively, you can use a
token from a team with that access instead of a user token.

To manage the GitHub resources, provide a token from an account or a GitHub App with
appropriate permissions. It should have `repository creation` and `manage actions repository secrets`.

## Authentication

### Terraform Cloud

The Terraform Cloud provider requires a Terraform Cloud/Enterprise API token in
order to manage resources.

- Set the `TFE_TOKEN` environment variable: The provider can read the TFE\_TOKEN environment variable and the token stored there
to authenticate. Refer to [Managing Variables](https://developer.hashicorp.com/terraform/cloud-docs/workspaces/variables/managing-variables) documentation for more details.

### GitHub

The GitHub provider requires a GitHub token or GitHub App installation in order to manage resources.

There are several ways to provide the required token:

- Set the `token` argument in the provider configuration. You can set the `token` argument in the provider configuration. Use an
input variable for the token.
- Set the `GITHUB_TOKEN` environment variable. The provider can read the `GITHUB_TOKEN` environment variable and the token stored there
to authenticate.

There are several ways to provide the required GitHub App installation:

- Set the `app_auth` argument in the provider configuration. You can set the app\_auth argument with the id, installation\_id and pem\_file
in the provider configuration. The owner parameter is also required in this situation.
- Set the `GITHUB_APP_ID`, `GITHUB_APP_INSTALLATION_ID` and `GITHUB_APP_PEM_FILE` environment variables. The provider can read the GITHUB\_APP\_ID,
GITHUB\_APP\_INSTALLATION\_ID and GITHUB\_APP\_PEM\_FILE environment variables to authenticate.

> Because strings with new lines is not support:</br>
> use "\\\n" within the `pem_file` argument to replace new line</br>
> use "\n" within the `GITHUB_APP_PEM_FILE` environment variables to replace new line</br>

## Features

- Manages configuration and life-cycle of Terraform Cloud resources:
  - private module registry
- Manages configuration and life-cycle of GitHub resources:
- repository
- branch protection
- actions repository permissions

## Prerequisite

In order to deploy the configuration from this code, you must first create
a VCS-Driven workspace in Terraform Cloud. This workspace mut contain an
environment variable `TFE_TOKEN`.

You can use the code from the [TerraformCloud\_Foundation](https://github.com/benyboy84/TerraformCloud_Foundation) repository.

Variable must be added to the TFC Workspace.
Variable-set must be linked to the workspace for GitHub Authentication.

## Documentation

## Requirements

The following requirements are needed by this module:

- <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) (> 1.6.0)

- <a name="requirement_tfe"></a> [tfe](#requirement\_tfe) (0.48.0)

## Modules

The following Modules are called:

### <a name="module_modules"></a> [modules](#module\_modules)

Source: ./modules/tfe_module

Version:

### <a name="module_repository"></a> [repository](#module\_repository)

Source: ./modules/github_repository

Version:

## Required Inputs

The following input variables are required:

### <a name="input_modules_name"></a> [modules\_name](#input\_modules\_name)

Description: A list of modules name to published.

Type: `list(string)`

### <a name="input_oauth_client_name"></a> [oauth\_client\_name](#input\_oauth\_client\_name)

Description: Name of the OAuth client.

Type: `string`

### <a name="input_organization_name"></a> [organization\_name](#input\_organization\_name)

Description: The name of the organization.

Type: `string`

## Optional Inputs

No optional inputs.

## Resources

The following resources are used by this module:

- [tfe_oauth_client.client](https://registry.terraform.io/providers/hashicorp/tfe/0.48.0/docs/data-sources/oauth_client) (data source)

## Outputs

No outputs.

<!-- markdownlint-enable -->

<!-- END_TF_DOCS -->