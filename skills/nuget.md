---
layout: default
title: NuGet
collection_style: skills
---

# NuGet

Public samples that show how to consume and demonstrate Nabs Launchpad packages.

### [LaunchpadCoreApis.WeatherSample](https://github.com/nabs-darrel-schreyer/LaunchpadCoreApis.WeatherSample)

**NuGet-first APIs with NabsEndpointBase + MapNabsEndpoints**

LaunchpadCoreApis.WeatherSample is a .NET 10 showcase for the [Nabs.Launchpad.Core.Apis](https://www.nuget.org/packages/Nabs.Launchpad.Core.Apis/10.0.273) NuGet package (10.0.273). It defines one endpoint class per route by subclassing NabsEndpointBase, declaring path/method/metadata in NabsEndpointOptions, and implementing HandleAsync. A single MapNabsEndpoints<Program>() call discovers and maps those endpoints - illustrated with GET /weatherforecast - so teams can structure APIs as discoverable classes instead of scattered minimal-route lambdas.

`.NET` | `ASP.NET Core` | `NuGet` | `OpenAPI` | `Nabs.Launchpad.Core.Apis`
