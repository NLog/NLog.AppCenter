# NLog.AppCenter
NLog Target for [Microsoft Visual Studio App Center with Azure](https://azure.microsoft.com/services/app-center/)

[![Version](https://badge.fury.io/nu/NLog.Targets.AppCenter.svg)](https://www.nuget.org/packages/NLog.Targets.AppCenter)
[![AppVeyor](https://img.shields.io/appveyor/ci/nlog/nlog-azureappcenter/master.svg)](https://ci.appveyor.com/project/nlog/nlog-azureappcenter/branch/master)

### How to use

1) Install the package

    `Install-Package NLog.Targets.AppCenter` or in your csproj:

    ```xml
    <PackageReference Include="NLog.Targets.AppCenter" Version="2.*" />
    ```

2) Add to your nlog.config:

    ```xml
    <extensions>
        <add assembly="NLog.Targets.AppCenter"/>
    </extensions>
    ```

3) Use the target "appcenter" in your nlog.config

    ```xml
    <targets>
        <target name="appcenter" xsi:type="appcenter" layout="${message}" reportExceptionAsCrash="true">
		<contextproperty name="logger" layout="${logger}" />
		<contextproperty name="loglevel" layout="${level}" />
		<contextproperty name="threadid" layout="${threadid}" />
        </target>
    </targets>
    <rules>
        <logger minLevel="Info" writeTo="appcenter" />
    </rules>
    ```

### Configuration options for AppCenterTarget

- **AppSecret** - Appsecret for starting AppCenter if needed (optional)
- **UserId** - Application UserId to register in AppCenter (optional)
- **LogUrl** - Base URL (scheme + authority + port only) to the AppCenter-backend (optional)
- **CountryCode** - Two-letter ISO country code to send to the AppCenter-backend (optional)
- **ReportExceptionAsCrash** - Report all exceptions as crashes to AppCenter (default=false)
- **IncludeEventProperties** - Include LogEvent properties in AppCenter properties (default=true)
- **IncludeMdlc** - Include MappedDiagnosticsLogicalContext (MLDC) that can be provided with MEL BeginScope (default=false)

