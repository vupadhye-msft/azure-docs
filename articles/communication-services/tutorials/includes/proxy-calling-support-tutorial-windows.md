---
title: include file
description: include file
services: azure-communication-services
ms.date: 08/14/2023
ms.topic: include
ms.service: azure-communication-services
---

## Force calling traffic to be proxied across your own server for Windows SDK

In certain situations, it might be useful to have all your client traffic proxied to a server that you can control. When the SDK is initializing, you can provide the details of your servers that you would like the traffic to route to. This tutorial guides on how to have Windows SDK calling traffic be proxied to servers that you control.

>[!IMPORTANT]
> The proxy feature will be available in a future public preview version of the Calling SDK.
>[!IMPORTANT]
> The proxy feature will NOT be available for Teams Identities and ACS Teams interop actions. 
## Proxy signaling traffic

To provide the URL of a proxy server, you need to pass it in as part of `CallClientOptions` through its property `CallNetworkOptions` while initializing the `CallClient`. For more details how to setup a call see [Azure Communication Services Windows SDK](../../quickstarts/voice-video-calling/get-started-with-video-calling.md?pivots=platform-windows)) for the Quickstart on how to setup Voice and Video.

```c#
CallClientOptions callClientOptions = new CallClientOptions();
CallNetworkOptions callNetworkOptions = new CallNetworkOptions();
callNetworkOptions.ProxyAddress = "https://myproxyserver.com";
callClientOptions.NetworkOptions = callNetworkOptions;
this.callClient = new CallClient(callClientOptions);
// ...continue normally with your SDK setup and usage.
```
