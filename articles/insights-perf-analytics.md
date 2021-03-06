<properties 
	pageTitle="Performance analytics for Azure Web Apps" 
	description="Chart load and response time, dependency information and set alerts on performance." 
	services="application-insights"
    documentationCenter=""
	authors="alancameronwills" 
	manager="keboyd"/>

<tags 
	ms.service="application-insights" 
	ms.workload="tbd" 
	ms.tgt_pltfrm="ibiza" 
	ms.devlang="na" 
	ms.topic="article" 
	ms.date="03/31/2015" 
	ms.author="awills"/>

# Performance analytics for Azure Web Apps and VMs

After enabling the Azure web app extension (detailed steps below) you’ll be able to see statistics and details on the application dependencies of your [Azure App Service Web App](websites-learning-map.md) or web apps in your [Azure VM](http://azure.microsoft.com/documentation/services/virtual-machines/).  These application dependencies are automatically discovered. 

Here's an example that shows the amount of time spent in a SQL dependency including the number of SQL calls and related statistics such as the average duration and standard deviation. 

![](./media/insights-perf-analytics/01-example.png) 



## Create a new Azure Web App with Performance Analytics

#### 1. Add Visual Studio Application Insights to your Visual Studio project

If you're creating a new Web Application project make sure to check the Application Insights option:

![In the New Project dialog, check Add Application Insights](./media/insights-perf-analytics/04-new.png)

Or if you have an existing project:

![In the New Project dialog, check Add Application Insights](./media/insights-perf-analytics/03-add.png)

When you're asked to login, use the credentials for your Azure account.

#### 2. Enable the Application Insights extension

In [the Azure portal](http://portal.azure.com), open the control blade of your web app (not the Application Insights blade), and enable the Application Insights Extension:

![](./media/insights-perf-analytics/05-extend.png)

Or if you're using an Azure VM:

![](./media/insights-perf-analytics/10-vm1.png)



## Explore the data

Use your website for a while to generate some telemetry.

Then, from your web app overview blade, open Application Monitoring. (Or from the [Azure portal home](http://portal.azure.com), Browse to Application Insights.)  

![Click Refresh](./media/insights-perf-analytics/06-overview.png)

Scroll down and open Performance:

![On the Application Insights overview blade, click the Performance tile](./media/insights-perf-analytics/07-dependency.png)

Drill through to see individual requests:

![In the grid, click a dependency to see related requests.](./media/insights-perf-analytics/08-requests.png)

## Q & A


*Can I automate adding the Application Insights extension?*

Yes, there's a REST API for Azure web apps. In PowerShell:

    $extension = "https://<sitename>.scm.azurewebsites.net/api/siteextensions/Microsoft.ApplicationInsights.AzureWebSites"
    Invoke-RestMethod -Uri $extension -Headers @{Authorization=("Basic {0}" -f $base64AuthInfo)} -Method PUT -Verbose

## Next steps

* [Monitor usage][azure-usage] to find out how many users you have, how often they visit, and how the pages perform on their browsers.
* [Create web tests][azure-availability] to make sure your site is available and responsive
* [Capture and search diagnostic logging](app-insights-diagnostic-search.md)
* [Use the API](app-insights-web-track-usage-custom-events-metrics.md) for usage tracking and diagnostic logging
* [Set performance alerts](app-insights-metrics-explorer.md)



<!--Link references-->

[alerts]: app-insightss-alerts.md
[android]: https://github.com/Microsoft/AppInsights-Android
[api]: app-insights-custom-events-metrics-api.md
[apiproperties]: app-insights-custom-events-metrics-api.md#properties
[apiref]: http://msdn.microsoft.com/library/azure/dn887942.aspx
[availability]: app-insights-monitor-web-app-availability.md
[azure]: insights-perf-analytics.md
[azure-availability]: insights-create-web-tests.md
[azure-usage]: insights-usage-analytics.md
[azurediagnostic]: insights-how-to-use-diagnostics.md
[client]: app-insights-web-track-usage.md
[config]: app-insights-configuration-with-applicationinsights-config.md
[data]: app-insights-data-retention-privacy.md
[desktop]: app-insights-windows-desktop.md
[detect]: app-insights-detect-triage-diagnose.md
[diagnostic]: app-insights-diagnostic-search.md
[eclipse]: app-insights-java-eclipse.md
[exceptions]: app-insights-web-failures-exceptions.md
[export]: app-insights-export-telemetry.md
[exportcode]: app-insights-code-sample-export-telemetry-sql-database.md
[greenbrown]: app-insights-start-monitoring-app-health-usage.md
[java]: app-insights-java-get-started.md
[javalogs]: app-insights-java-trace-logs.md
[javareqs]: app-insights-java-track-http-requests.md
[knowUsers]: app-insights-overview-usage.md
[metrics]: app-insights-metrics-explorer.md
[netlogs]: app-insights-asp-net-trace-logs.md
[new]: app-insights-create-new-resource.md
[older]: http://www.visualstudio.com/get-started/get-usage-data-vs
[perf]: app-insights-web-monitor-performance.md
[platforms]: app-insights-platforms.md
[portal]: http://portal.azure.com/
[qna]: app-insights-troubleshoot-faq.md
[redfield]: app-insights-monitor-performance-live-website-now.md
[roles]: app-insights-role-based-access-control.md
[start]: app-insights-get-started.md
[trace]: app-insights-search-diagnostic-logs.md
[track]: app-insights-custom-events-metrics-api.md
[usage]: app-insights-web-track-usage.md
[windows]: app-insights-windows-get-started.md
[windowsCrash]: app-insights-windows-crashes.md
[windowsUsage]: app-insights-windows-usage.md

