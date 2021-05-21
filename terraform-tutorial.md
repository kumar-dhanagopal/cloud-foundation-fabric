# Deploy a Terraform configuration

This tutorial walks you through the steps to deploy the Terraform example configurations for Google Cloud available in the GitHub repository, [Terraform Examples and Modules for Google Cloud repository](https://github.com/terraform-google-modules/cloud-foundation-fabric). These examples are provided and maintained by Google.

## Let's get started!

If you haven't already downloaded or cloned the repository, get the code now:
- Using `git`:
  ```
  git clone https://github.com/terraform-google-modules/cloud-foundation-fabric.git
  ```
- Using the GitHub CLI:
  ```
  gh repo clone terraform-google-modules/cloud-foundation-fabric
  ```

## (Optional) Configure the Terraform variables

The Terraform code that you downloaded includes variables that you can use to customize the deployment based on your requirements.
- Some of the variables have a default value, which you can change. 
- For variables that don't have a default value, you can either assign a value beforehand, or enter a value when Terraform prompts you to do so while running any Terraform command.

If you choose to configure the variables ahead of running the Terraform commands, or if you want to change any of the default values, complete the following steps. Otherwise, skip this section.

1.  Go to the directory that contains the example configuration that you want to deploy (for example, `networking/hub-and-spoke-vpn`).

1.  Open the file `variables.tf`.

    The input variables for the Terraform configuration are declared in this file.

1.  Identify the variables for which you need to assign values:

    -   Variables that don't have a default value.
    -   Variables with a default value that you want to change.

    For each variable that you identify, read its `description`, and note its [`type`](https://www.terraform.io/docs/language/values/variables.html#type-constraints).

1.  Create a text file named _`FILE_NAME`_`.tfvars`.

    `FILE_NAME` can be any name, but the extension _must_ be `.tfvars` or `.tfvars.json`. Terraform treats any file with this extension as a [_variable definitions_](https://www.terraform.io/docs/language/values/variables.html#variable-definitions-tfvars-files) file.

    If you don't create a `.tfvars` or `.tfvars.json` file, Terraform uses the default values, where available. For each variable that doesn't have a default value, Terraform prompts you to enter a value every time you run any Terraform command.

1.  In the `.tfvars`, assign appropriate values to the variables that you identified earlier.

    **Important**: The value that you assign to each variable must match the `type` of that variable as declared in `variables.tf`.
    
## Initialize Terraform and validate the configuration

Complete the following steps from the directory that contains the example configuration that you want to deploy (for example, `networking/hub-and-spoke-vpn`).

1.  Initialize Terraform:

    ```
    terraform init
    ```

1.  Verify that the configuration has no errors:

    ```
    terraform validate
    ```

    If the command returns an error, make the required corrections in the configuration, and run `terraform validate` again.

    Repeat this step until the command displays the following message:

    ```none
    Success! The configuration is valid.
    ```

1.  Review the resources defined in the configuration:

    ```
    terraform plan
    ```

    The output lists the resources that Terraform will provision when you apply the configuration.

    If you want to make any changes, edit the configuration, and then run
    `terraform validate` and `terraform plan` again.

## Provision resources

When no further changes are necessary in the configuration, deploy the resources.

Complete the following steps from the directory that contains the example configuration that you want to deploy (for example, `networking/hub-and-spoke-vpn`).

1.  Run the following command:

    ```
    terraform apply
    ```

    Terraform displays a list of the resources that will be created.

2.  At the prompt to perform the actions, enter `yes`.

    If Terraform displays an error message that one or more APIs are not enabled, use each link shown in the message to enable the required APIs.

    Terraform displays messages showing the progress of the deployment. After all the resources are created, Terraform displays the following message:

    ```none {:.devsite-disable-click-to-copy}
    Apply complete!
    ```

## Add, change, or remove resources

-   To add, change, or remove resources, edit the Terraform configuration, and then run the commands `terraform validate`, `terraform plan`, and `terraform apply`.

-   To remove all the resources, run the command `terraform destroy`.
