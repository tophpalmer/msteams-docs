---
title: Prerequisites
author: surbhigupta
description: Every tab in Microsoft Teams must adhere to these requirements.
keywords: teams tabs group channel configurable
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
---

# Prerequisites

Teams tabs must adhere to the following prerequisites:

* You must allow your tab pages to be shown in an iFrame, using X-Frame-Options and Content-Security-Policy HTTP response headers.
  * Set header: `Content-Security-Policy: frame-ancestors teams.microsoft.com *.teams.microsoft.com *.skype.com`
  * For Internet Explorer 11 compatibility, set `X-Content-Security-Policy`.
  * Alternately, set header `X-Frame-Options: ALLOW-FROM https://teams.microsoft.com/`. This header is deprecated but still accepted by most browsers.

* Typically, as a safeguard against clickjacking, login pages do not render in iFrames. Your authentication logic needs to use a method other than redirect. For example, use token-based or cookie-based authentication.

    > [!NOTE]
    > Chrome 80, scheduled for release in early 2020, introduces new cookie values and imposes cookie policies by default. It is recommended that you set the intended use for your cookies rather than rely on default browser behavior. For more information, see [SameSite cookie attribute](../../resources/samesite-cookie-update.md).

* Browsers adhere to a same-origin policy restriction. It prevents webpages from making requests to different domains than the served web page. However, you can redirect the configuration or content page to another domain or subdomain. Your cross-domain navigation logic must allow the Teams client to validate the origin against a static `validDomains` list in the app manifest when loading or communicating with the tab.

* You must style your tabs based on the Teams client's theme, design, and intent. Typically, tabs work best when they are built to address a specific need and focus on a small set of tasks or a subset of data that is relevant to the tab's channel location.

* Within your content page, add a reference to [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client) using script tags. After your page loads, make a call to `microsoftTeams.initialize()`, otherwise your page is not displayed.

* For authentication to work on mobile clients, you must upgrade Teams JavaScript SDK to at least version 1.4.1.

* If you choose to have your channel or group tab appear on Teams mobile clients, the `setSettings()` configuration must have a value for the `websiteUrl` property.

* MS Teams tab does not support the ability to load intranet websites that use self-signed certificates.

## See also

* [Teams tabs](~/tabs/what-are-tabs.md)
* [Create a channel or group tab](~/tabs/how-to/create-channel-group-tab.md)
* [Tabs on mobile](~/tabs/design/tabs-mobile.md)

## Next step

> [!div class="nextstepaction"]
> [Create a personal tab](~/tabs/how-to/create-personal-tab.md)
