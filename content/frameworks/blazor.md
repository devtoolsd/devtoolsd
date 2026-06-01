---
name: Blazor
slug: blazor
language: csharp
description: C# UI framework for the web — run .NET code in the browser via WebAssembly or server-side with SignalR.
website: https://dotnet.microsoft.com/apps/aspnet/web-apps/blazor
github: dotnet/aspnetcore
year: 2018
pricing: free
open_source: true
license: MIT
tool_type: web
tags: [frontend, csharp, dotnet, wasm, webassembly, spa, server-side]
related_frameworks: [aspnet-core]
features:
  - "Write interactive web UIs entirely in C# — no JavaScript required"
  - "Blazor WebAssembly — .NET code runs client-side in the browser sandbox"
  - "Blazor Server — UI logic runs on the server, synced via SignalR"
  - "Blazor Auto — switches between Server and WASM for best of both"
  - "Component model similar to React — parameters, event callbacks, lifecycle"
  - "CSS isolation and scoped styles per component"
  - "Reuse .NET libraries and NuGet packages on the frontend"
  - "JavaScript interop for calling JS when needed"
install:
  dotnet: "dotnet new blazor -n MyBlazorApp && cd MyBlazorApp && dotnet run"
---

Blazor lets C# developers build interactive web UIs without JavaScript. Blazor WebAssembly runs .NET code directly in the browser sandbox; Blazor Server keeps UI logic on the server and sends updates via SignalR. Blazor Auto (introduced in .NET 8) starts with Server rendering for fast initial load, then downloads the WASM runtime and switches to client-side execution. For .NET shops, Blazor eliminates the context switch between C# backend and JavaScript frontend.

## Quick start

```bash
dotnet new blazor -n MyBlazorApp --interactivity WebAssembly
cd MyBlazorApp
dotnet run
```

```razor
@* Components/Counter.razor *@
@rendermode InteractiveWebAssembly

<h1>Counter</h1>
<p>Current count: @currentCount</p>
<button @onclick="IncrementCount">Click me</button>

@code {
    private int currentCount = 0;

    private void IncrementCount()
    {
        currentCount++;
    }
}
```

```razor
@* Pages/FetchData.razor *@
@page "/weather"
@inject HttpClient Http

@if (forecasts == null)
{
    <p>Loading...</p>
}
else
{
    <table>
        @foreach (var f in forecasts)
        {
            <tr><td>@f.Date</td><td>@f.TemperatureC°C</td></tr>
        }
    </table>
}

@code {
    private WeatherForecast[]? forecasts;

    protected override async Task OnInitializedAsync()
    {
        forecasts = await Http.GetFromJsonAsync<WeatherForecast[]>("sample-data/weather.json");
    }
}
```

## When to use

Blazor is ideal for .NET teams that want to build web UIs without switching to JavaScript. It's particularly valuable for internal enterprise tools, line-of-business apps, and teams with deep .NET expertise. Blazor WASM suits offline-capable apps; Blazor Server is better for apps needing real-time data. If your team already uses React or Vue, sticking with the JavaScript ecosystem is usually the right call unless there's strong motivation to unify the stack in C#.
