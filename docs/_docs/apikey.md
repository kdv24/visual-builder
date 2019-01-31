---
title: — API Key Auth
order: 6
layout: post-toc
redirect_from: /docs/
---

## Authentication — API Key Auth

API Key authentication lets apps verify users account with an API key that is passed along with every API call. In a Zapier integration using API Key authentication, Zapier includes the API key—optionally along with any other data your API needs—every time a Zap step runs.

![Zapier API key auth example](https://cdn.zapier.com/storage/photos/19467b7d1852276b766b373373fd069c.png)
_Example API key auth screen for users inside Zapier_

API Key authentication works similarly to Zapier's [Basic Auth](https://zapier.github.io/visual-builder/docs/basic) in that Zapier passes the credentials with every API call. Here, though, you need to build the [input form](https://zapier.github.io/visual-builder/docs/input-designer) where users add their API key and any other optional information your API requires, such as their account name, site URL, and other identifying data. You can additionally include help text under each field to direct users to where they can retrieve their API key.

Use API key authentication if your API primarily uses an API key to identify accounts, especially with apps for weather, maps, content verification, file conversion, and other data tools that require a key for access to the service but do not contain user-specific content. Alternately, since API key authentication allows you to create a custom input form, you can use it to customize username and password-based logins that don't fit Zapier's default Basic auth scheme.

<a id="add"></a>
## How to Add API Key Auth to a Zapier Integration

![Add API Key Auth to Zapier Integration](https://cdn.zapier.com/storage/photos/b364e321d1a02fc607d9d360679d6b64.png)

To add API Key Auth to your Zapier integration, open the _Authentication_ tab in Zapier visual builder and select _API key_.

You then need to:

- Build an input form for users to enter their API key and any other required data
- Add a test API call to verify user credentials when adding new accounts
- Add a connection label to identify each added account
- Test the authentication to ensure it works and to obtain a testing login that can be used in testing subsequent Zap steps as you add them

<a id="form"></a>
### Add an API Key Input Form

![Add fields to API key auth Zapier](https://cdn.zapier.com/storage/photos/0ecfa173843efc628fe1407a9346e0ea.png)

Start by adding a form where users will enter their API key and other authentication details when connecting their app account to Zapier. Check your API documentation for what fields are required, including user or account names, domains, and more. Additionally, note any details users may need on how to find that data, since API keys especially are often hidden under settings menus and you'll need to include those details in your input form's help text.

For each field that you need, click the _Add Fields_ button and fill in the details for your field. Be sure to add the most commonly needed fields first, in the order users expect, as you cannot reorder fields once added.

![Zapier API Key Input Form](https://cdn.zapier.com/storage/photos/efe397d89f0cf26122513b9d3c2ea2f4.png)

Every input field requires a _Key_, the name your API uses to reference this field. Enter the same key name that your API uses.

Then fill in the optional fields, as appropriate, especially the _Label_:

- **Label**: A human friendly name for this field. Enter what this value is called inside your app's UI.
- **Is this field required**: Check this box for your API key field, and for any other fields that your API requires for authentication.
- **Type**: Zapier uses the `string` text field for all input fields by default; select `password` instead if you would like to obscure the data as users enter it.
- **Help Text**: Include details to assist users in authenticating with your app, especially if they may be unsure where to find the data needed. Format text with [Markdown](https://zapier.com/blog/beginner-ultimate-guide-markdown/), and include a link if needed.
- **Default Value**: Include a value for this field to be used a fallback. For optional fields, the default value is set on initial creation and used instead of missing or null values every time the Zap runs. For required fields, this value is used during Zap creation, but not when the Zap runs (Zapier raises an error for missing/null values instead).

![Zapier Computed Fields](https://cdn.zapier.com/storage/photos/b82edea722597f88f5c0d21a46d6c847.png)

Zapier includes one more field option: Computed Fields. These are used to store values obtained from your API test call that would be referenced in your integration's subsequent API calls.

Say your app includes a username that can be fetched with an API call using the API key—and your other API calls require the username be used. You would add a computed field that references that value from your server's response, much like the way you reference fields in connected accounts.

Add your field's key as before, with the same key your API uses to reference that data. Zapier stores all fields returned by the authentication API test call, including the one you reference in the computed field, so you can use them in subsequent API calls. If your API does not return the field referenced in your computed field, Zapier will show an error since computed fields are required by default.

![Edit API key input fields](https://cdn.zapier.com/storage/photos/b3d0bf644fd562435e5099083b8b66a2.png)

Once you've added your input fields, Zapier lists each input field with its label, key, type, and required status on your authentication settings. Click the field to edit it, or click the gear icon and select _Delete_ to remove a field.

When you've added the needed forms, click _Continue_ to add a test API call and continue setting up your app's authentication.

<a id="request"></a>
### Add a Test API Request

![Zapier test request API Key authentication](https://cdn.zapier.com/storage/photos/3130a3ad4c5b211de33886d4eff2abc0.png)

Zapier then 

Also add a Connection Label. 