#### Table of contents

* [Unable to list subscriptions](#unable-to-list-subscriptions)
* [Unable to sign in while using a proxy](#unable-to-sign-in-while-using-a-proxy)

## Unable to list subscriptions

This is a [common problem](https://github.com/microsoft/vscode-azure-account/issues/193) for users and it typically can be fixed by following the steps below:

### Setup your Azure account

This should only be done if you have yet to setup your Azure account with at least one subscription.

1. Open VS Code and sign out of the Azure Account Extension using the `Azure: Sign Out` command (accessible via the [command palette](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette)).
2. Navigate to [azure.microsoft.com](https://aka.ms/AAevntl) and follow the steps there to setup your Azure account.
3. Once you get your new subscription up and running, open VS Code and sign into the Azure Account Extension using the `Azure: Sign In` command.
4. If you're still having trouble viewing your subscriptions, move onto the next troubleshooting section.

### Configure your [tenant](https://docs.microsoft.com/microsoft-365/education/deploy/intro-azure-active-directory#what-is-an-azure-ad-tenant) in the Azure Account Extension

These steps need to be taken when the subscription you're looking for is associated with a tenant other the default tenant (which is set for you by the extension).

1. Open VS Code and ensure you are signed into the Azure Account Extension. You may sign in using the `Azure: Sign In` command (accessible via the [command palette](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette)).
2. Run the `Azure: Select Tenant` command.
3. Select a new tenant from the list of displayed tenants.
4. Sign out then sign back in for the new tenant to take effect.

If selecting a tenant from the list fails to solve your problem, try again with a different tenant.
If you're unable to list tenants or if you exhaust the list of tenants, follow these steps to manually find your tenant ID:

1. Ensure subscriptions are listed for your account when you sign into the [Azure portal](https://ms.portal.azure.com/#blade/Microsoft_Azure_Billing/SubscriptionsBlade).
2. Follow [these instructions](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-to-find-tenant) to find your tenant ID.
3. Run the `Azure: Select Tenant` command.
4. Select "Enter custom tenant" and enter the tenant ID from above.
5. Sign out then sign back in for the new tenant to take effect.

If you still aren't able to list subscriptions after following these steps, please consider [filing an issue](https://github.com/microsoft/vscode-azure-account/issues/new?assignees=&labels=&template=cannot-list-subscriptions.md&title=Cannot+list+subscriptions) so we can better understand why this problem is occurring.

## Unable to sign in while using a proxy

### Try an alternative sign in method

If the standard sign in method isn't working, try running the `Azure: Sign In with Device Code` command which is accessible via the [command palette](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).

### Install a private build to help debug the issue

Follow these instructions to install a private build. It includes an unreleased feature that displays a list of URLs that the extension attempts to access so you can properly configure your proxy.

1. Download version `v0.10.2-alpha` of the extension [here](https://dev.azure.com/ms-azuretools/534e1e1c-b364-44d0-b5ee-dce879a5106e/_apis/build/builds/44727/artifacts?artifactName=vsix&api-version=7.0&%24format=zip).
2. Open VS Code and run the `Extensions: Install Specific Version of Extension...` command.
![Screen Shot 2022-02-28 at 10 19 15 AM](https://user-images.githubusercontent.com/22795803/156036649-2f02c066-7e89-470c-8300-1903fe16f563.png)
3. In the file picker: browse to the `.vsix` file you downloaded and select it.
4. After selecting the file, a notification should appear prompting you to reaload the VS Code window. Click "Reload Now".
![Screen Shot 2022-02-28 at 10 21 37 AM](https://user-images.githubusercontent.com/22795803/156037095-0e4830ed-f226-48d6-9bbd-1e2cbde08029.png)
5. Open the marketplace in VS Code. Verify that the Azure Account Extension version reads `v0.10.2-alpha`.
6. Try signing in again.
7. Open the output window and view the URLs that the extension is attempting to access
<img width="1102" alt="Screen Shot 2022-04-01 at 11 37 41 AM" src="https://user-images.githubusercontent.com/22795803/161322573-8a1f6317-b02d-4b18-9c3c-844709cd855d.png">

8. Configure your proxy to whitelist those URLs.
9. Try signing in again.

### File an issue

If the above steps don't work, please [file an issue](https://github.com/microsoft/vscode-azure-account/issues/new?assignees=&labels=&template=bug-report.md&title=Cannot+sign+in+while+using+proxy). In your issue, be sure to include the information in the Azure Account Extension's output channel, the sign in error you're getting, and any other information that you think may be useful.

