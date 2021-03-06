<properties 
	pageTitle="Explore Java trace logs in Application Insights" 
	description="Search Log4J or Logback traces in Application Insights" 
	services="application-insights" 
    documentationCenter=""
	authors="alancameronwills" 
	manager="kamrani"/>

<tags 
	ms.service="application-insights" 
	ms.workload="tbd" 
	ms.tgt_pltfrm="ibiza" 
	ms.devlang="na" 
	ms.topic="article" 
	ms.date="03/05/2015" 
	ms.author="awills"/>

# Explore Java trace logs in Application Insights

If you’re using Logback or Log4J (v1.2 or v2.0) for tracing, you can have your trace logs sent automatically to Application Insights where you can explore and search on them.

Install [Application Insights SDK for Java][java], if you haven't already done that.


## Add logging libraries to your project

*Choose the appropriate way for your project.*

#### If you're using Maven...

If your project is already set up to use Maven for build, merge one of the following snippets of code into your pom.xml file.

Then refresh the project dependencies, to get the binaries downloaded.

*Logback*

    <dependencies>
       <dependency>
          <groupId>com.microsoft.azure</groupId>
          <artifactId>applicationinsights-logging-logback</artifactId>
          <version>[0.9,)</version>
       </dependency>
    </dependencies>

*Log4J v2.0*

    <dependencies>
       <dependency>
          <groupId>com.microsoft.azure</groupId>
          <artifactId>applicationinsights-logging-log4j2</artifactId>
          <version>[0.9,)</version>
       </dependency>
    </dependencies>

*Log4J v1.2*

    <dependencies>
       <dependency>
          <groupId>com.microsoft.azure</groupId>
          <artifactId>applicationinsights-logging-log4j1_2</artifactId>
          <version>[0.9,)</version>
       </dependency>
    </dependencies>

#### If you're using Gradle...

If your project is already set up to use Gradle for build, add one of the following lines to the `dependencies` group in your build.gradle file:

Then refresh the project dependencies, to get the binaries downloaded.

**Logback**

    compile group: 'com.microsoft.azure', name: 'applicationinsights-logging-logback', version: '0.9.+'

**Log4J v2.0**

    compile group: 'com.microsoft.azure', name: 'applicationinsights-logging-log4j2', version: '0.9.+'

**Log4J v1.2**

    compile group: 'com.microsoft.azure', name: 'applicationinsights-logging-log4j1_2', version: '0.9.+'

#### Otherwise ...

Download and extract the appropriate appender, then add the appropriate library to your project:


Logger | Download | Library
----|----|----
Logback|[SDK with Logback appender](http://dl.msopentech.com/applicationinsights/javabin/logbackAppender.zip)|applicationinsights-logging-logback
Log4J v2.0|[SDK with Log4J v2 appender](http://dl.msopentech.com/applicationinsights/javabin/log4j2Appender.zip)|applicationinsights-logging-log4j2 
Log4j v1.2|[SDK with Log4J v1.2 appender](http://dl.msopentech.com/applicationinsights/javabin/log4j1_2Appender.zip)|applicationinsights-logging-log4j1_2 



## Add the appender to your logging framework

To start getting traces, merge the relevant snippet of code to the Log4J or Logback configuration file: 

*Logback*

    <appender name="aiAppender" 
      class="com.microsoft.applicationinsights.logback.ApplicationInsightsAppender">
    </appender>
    <root level="trace">
      <appender-ref ref="aiAppender" />
    </root>


*Log4J v2.0*

    
    <Appenders>
      <ApplicationInsightsAppender name="aiAppender" />
    </Appenders>
    <Loggers>
      <Root level="trace">
        <AppenderRef ref="aiAppender"/>
      </Root>
    </Loggers>


*Log4J v1.2*

    <appender name="aiAppender" 
         class="com.microsoft.applicationinsights.log4j.v1_2.ApplicationInsightsAppender">
    </appender>
    <root>
      <priority value ="trace" />
      <appender-ref ref="aiAppender" />
    </root>

The Application Insights appenders can be referenced by any configured logger, and not necessarily by the root logger (as shown in the code samples above).

## Explore your traces in the Application Insights portal

Now that you’ve configured your project to send traces to Application Insights, you can view and search these traces in the Application Insights portal, in the [Diagnostic Search][diagnostic] blade.

![In the Application Insights portal, open Diagnostic Search](./media/app-insights-java-get-started/10-diagnostics.png)

## Next steps

[Diagnostic search][diagnostic]

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

