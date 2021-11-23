## Unable to list subscriptions

This is a [common problem](https://github.com/microsoft/vscode-azure-account/issues/193#issuecomment-643975021) for users and it typically can be fixed by following the steps below:

### Setup your Azure account

This should only be done if you have yet to setup your Azure account with at least one subscription.

1. Navigate to [azure.microsoft.com](https://aka.ms/AAevntl) to setup your Azure account.
2. Once you get your new subscription up and running, sign into the Azure Account Extension again using the `Azure: Sign In` command (accessible via the [command palette](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette)).
3. If you're still having trouble viewing your subscriptions, move onto the next troubleshooting section.

### Configure your [tenant](https://docs.microsoft.com/microsoft-365/education/deploy/intro-azure-active-directory#what-is-an-azure-ad-tenant) in the Azure Account Extension

1. Ensure subscriptions are listed for your account when you sign into the [Azure portal](https://ms.portal.azure.com/#blade/Microsoft_Azure_Billing/SubscriptionsBlade).
2. Follow [these instructions](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-how-to-find-tenant) to find your tenant ID.
3. Open [VS Code's settings](https://code.visualstudio.com/docs/getstarted/settings#_creating-user-and-workspace-settings) and search for the `Azure: Tenant` setting.

    ![image](https://user-images.githubusercontent.com/22795803/142292709-39f828f5-2188-4156-8c96-b71009c160a1.png)

4. Input your tenant ID and sign in again via the `Azure: Sign In` command (accessible via the [command palette](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette)).

If you still aren't able to list subscriptions after following these steps, please consider [filing an issue](https://github.com/microsoft/vscode-azure-account/issues/new?assignees=&labels=&template=cannot-list-subscriptions.md&title=Cannot+list+subscriptions) so we can better understand why this problem is occurring.