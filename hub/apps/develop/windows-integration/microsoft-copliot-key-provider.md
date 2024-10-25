---
title: Microsoft Copilot hardware key providers
description: Learn how to register as an app that can be selected as the launch app for the Microsoft Copilot hardware key. 
ms.topic: article
ms.date: 10/25/2024
ms.localizationpriority: medium
---



# Microsoft Copilot hardware key providers

Starting with [TBD - build number], apps can register to be included in the picker UI that allows users to select the app that is launched when the Microsoft Copilot hardware key is pressed.

## Requirements

For an app to be included in the Microsoft Copilot hardware key picker UI, it must meed the following requirements.

* The app must have packaged identity. See the below for details about packaging requirements.
* The app must be implemented as a single-window app.

## Microsoft Copilot hardware key app extension

An app must be packaged in order to register as a Microsoft Copilot hardware key provider. For information on app packaging, see [An overview of Package Identity in Windows app](/windows/apps/desktop/modernize/package-identity-overview). The app package manifest file, `Package.appxmanifest`, supports many different extensions and features for Windows apps. The app package manifest format is defined by a set of schemas that are documented in the [Package manifest schema reference](/uwp/schemas/appxpackage/uapmanifestschema/schema-root).  Microsoft Copilot hardware key providers declare their registration information within the [uap3:AppExtension](/uwp/schemas/appxpackage/uapmanifestschema/element-uap3-appextension-manual). The **Name** attribute of the extension must be set to "com.microsoft.windows.copilotkeyprovider".


```xml
<Package
...

  xmlns:uap3="http://schemas.microsoft.com/appx/manifest/uap/windows10/3"
...>
    <Applications>
        <Application...>
            ...
            <Extensions>
                <uap3:Extension Category="windows.appExtension">
                    <uap3:AppExtension Name="com.microsoft.windows.copilotkeyprovider" 
                        Id="MyAppId"
                        DisplayName="App display name"
                        Description="App description"
                        PublicFolder="Public" />
                </uap3:Extension>
            </Extensions>
          ...
    </Application>
    </Applications>
    ...
</Package>
```

The following table *uap3:AppExtension* describes the attributes of the **uap3:AppExtension** element.

| Attribute | Description | Required |
|-----------|-------------|----------|
| Id | The app-defined identifier for the app. | Yes |
| DisplayName | The app name displayed in the Windows Copilot hardware button picker UI.  | Yes |
| Description | The app description displayed in the Windows Copilot hardware button picker UI. | Yes |
| PublicFolder| [TBD - Need description] | Yes | 
