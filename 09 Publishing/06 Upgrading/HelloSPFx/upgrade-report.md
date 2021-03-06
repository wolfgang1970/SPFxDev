# Upgrade project G:\Classes\SPFxDevelopment\04 Publishing\06 Upgrading\HelloSPFx to v1.7.0

Date: 2019-3-16

## Findings

Following is the list of steps required to upgrade your project to SharePoint Framework version 1.7.0. [Summary](#Summary) of the modifications is included at the end of the report.

### FN001001 @microsoft/sp-core-library | Required

Upgrade SharePoint Framework dependency package @microsoft/sp-core-library

Execute the following command:

```sh
npm i @microsoft/sp-core-library@1.7.0 -SE
```

File: [./package.json](./package.json)

### FN001002 @microsoft/sp-lodash-subset | Required

Upgrade SharePoint Framework dependency package @microsoft/sp-lodash-subset

Execute the following command:

```sh
npm i @microsoft/sp-lodash-subset@1.7.0 -SE
```

File: [./package.json](./package.json)

### FN001003 @microsoft/sp-office-ui-fabric-core | Required

Upgrade SharePoint Framework dependency package @microsoft/sp-office-ui-fabric-core

Execute the following command:

```sh
npm i @microsoft/sp-office-ui-fabric-core@1.7.0 -SE
```

File: [./package.json](./package.json)

### FN001004 @microsoft/sp-webpart-base | Required

Upgrade SharePoint Framework dependency package @microsoft/sp-webpart-base

Execute the following command:

```sh
npm i @microsoft/sp-webpart-base@1.7.0 -SE
```

File: [./package.json](./package.json)

### FN002001 @microsoft/sp-build-web | Required

Upgrade SharePoint Framework dev dependency package @microsoft/sp-build-web

Execute the following command:

```sh
npm i @microsoft/sp-build-web@1.7.0 -DE
```

File: [./package.json](./package.json)

### FN002002 @microsoft/sp-module-interfaces | Required

Upgrade SharePoint Framework dev dependency package @microsoft/sp-module-interfaces

Execute the following command:

```sh
npm i @microsoft/sp-module-interfaces@1.7.0 -DE
```

File: [./package.json](./package.json)

### FN002003 @microsoft/sp-webpart-workbench | Required

Upgrade SharePoint Framework dev dependency package @microsoft/sp-webpart-workbench

Execute the following command:

```sh
npm i @microsoft/sp-webpart-workbench@1.7.0 -DE
```

File: [./package.json](./package.json)

### FN002008 tslint-microsoft-contrib | Required

Remove SharePoint Framework dev dependency package tslint-microsoft-contrib

Execute the following command:

```sh
npm un tslint-microsoft-contrib -D
```

File: [./package.json](./package.json)

### FN006003 package-solution.json isDomainIsolated | Required

Update package-solution.json isDomainIsolated

In file [./config/package-solution.json](./config/package-solution.json) update the code as follows:

```json
{
  "solution": {
    "isDomainIsolated": false
  }
}
```

File: [./config/package-solution.json](./config/package-solution.json)

### FN010001 .yo-rc.json version | Recommended

Update version in .yo-rc.json

In file [./.yo-rc.json](./.yo-rc.json) update the code as follows:

```json
{
  "@microsoft/generator-sharepoint": {
    "version": "1.7.0"
  }
}
```

File: [./.yo-rc.json](./.yo-rc.json)

### FN010007 .yo-rc.json isDomainIsolated | Recommended

Update isDomainIsolated in .yo-rc.json

In file [./.yo-rc.json](./.yo-rc.json) update the code as follows:

```json
{
  "@microsoft/generator-sharepoint": {
    "isDomainIsolated": false
  }
}
```

File: [./.yo-rc.json](./.yo-rc.json)

### FN018001 Web part Microsoft Teams tab resources folder | Optional

Create folder for Microsoft Teams tab resources

Execute the following command:

```sh
mkdir G:\Classes\SPFxDevelopment\04 Publishing\06 Upgrading\HelloSPFx\teams_helloSpFxWp
```

File: [teams_helloSpFxWp](teams_helloSpFxWp)

### FN018002 Web part Microsoft Teams tab manifest | Optional

Create Microsoft Teams tab manifest for the web part

Execute the following command:

```sh
cat > G:\Classes\SPFxDevelopment\04 Publishing\06 Upgrading\HelloSPFx\teams_helloSpFxWp\manifest.json << EOF
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.2/MicrosoftTeams.schema.json",
  "manifestVersion": "1.2",
  "packageName": "HelloSPFxWP",
  "id": "9a90a2cc-d2bf-4603-b847-907dfb3942df",
  "version": "0.1",
  "developer": {
    "name": "SPFx + Teams Dev",
    "websiteUrl": "https://products.office.com/en-us/sharepoint/collaboration",
    "privacyUrl": "https://privacy.microsoft.com/en-us/privacystatement",
    "termsOfUseUrl": "https://www.microsoft.com/en-us/servicesagreement"
  },
  "name": {
    "short": "HelloSPFxWP"
  },
  "description": {
    "short": "HelloSPFxWP description",
    "full": "HelloSPFxWP description"
  },
  "icons": {
    "outline": "tab20x20.png",
    "color": "tab96x96.png"
  },
  "accentColor": "#004578",
  "configurableTabs": [
    {
      "configurationUrl": "https://{teamSiteDomain}{teamSitePath}/_layouts/15/TeamsLogon.aspx?SPFX=true&dest={teamSitePath}/_layouts/15/teamshostedapp.aspx%3FopenPropertyPane=true%26teams%26componentId=9a90a2cc-d2bf-4603-b847-907dfb3942df",
      "canUpdateConfiguration": true,
      "scopes": [
        "team"
      ]
    }
  ],
  "validDomains": [
    "*.login.microsoftonline.com",
    "*.sharepoint.com",
    "*.sharepoint-df.com",
    "spoppe-a.akamaihd.net",
    "spoprod-a.akamaihd.net",
    "resourceseng.blob.core.windows.net",
    "msft.spoppe.com"
  ],
  "webApplicationInfo": {
    "resource": "https://{teamSiteDomain}",
    "id": "00000003-0000-0ff1-ce00-000000000000"
  }
}
EOF
```

File: [teams_helloSpFxWp\manifest.json](teams_helloSpFxWp\manifest.json)

### FN018003 Web part Microsoft Teams tab small icon | Optional

Create Microsoft Teams tab small icon for the web part

Execute the following command:

```sh
cp C:\Users\Alexander\AppData\Roaming\nvm\v8.11.3\node_modules\@pnp\office365-cli\dist\o365\spfx\commands\project\project-upgrade\assets\tab20x20.png G:\Classes\SPFxDevelopment\04 Publishing\06 Upgrading\HelloSPFx\teams_helloSpFxWp\tab20x20.png
```

File: [teams_helloSpFxWp\tab20x20.png](teams_helloSpFxWp\tab20x20.png)

### FN018004 Web part Microsoft Teams tab large icon | Optional

Create Microsoft Teams tab large icon for the web part

Execute the following command:

```sh
cp C:\Users\Alexander\AppData\Roaming\nvm\v8.11.3\node_modules\@pnp\office365-cli\dist\o365\spfx\commands\project\project-upgrade\assets\tab96x96.png G:\Classes\SPFxDevelopment\04 Publishing\06 Upgrading\HelloSPFx\teams_helloSpFxWp\tab96x96.png
```

File: [teams_helloSpFxWp\tab96x96.png](teams_helloSpFxWp\tab96x96.png)

### FN019001 tslint.json rulesDirectory | Required

Remove rulesDirectory from tslint.json

In file [./tslint.json](./tslint.json) update the code as follows:

```json
{
  "rulesDirectory": []
}
```

File: [./tslint.json](./tslint.json)

### FN019002 tslint.json extends | Required

Update tslint.json extends property

In file [./tslint.json](./tslint.json) update the code as follows:

```json
{
  "extends": "@microsoft/sp-tslint-rules/base-tslint.json"
}
```

File: [./tslint.json](./tslint.json)

### FN017001 Run npm dedupe | Optional

If, after upgrading npm packages, when building the project you have errors similar to: "error TS2345: Argument of type 'SPHttpClientConfiguration' is not assignable to parameter of type 'SPHttpClientConfiguration'", try running 'npm dedupe' to cleanup npm packages.

Execute the following command:

```sh
npm dedupe
```

File: [./package.json](./package.json)

## Summary

### Execute script

```sh
npm i @microsoft/sp-core-library@1.7.0 @microsoft/sp-lodash-subset@1.7.0 @microsoft/sp-office-ui-fabric-core@1.7.0 @microsoft/sp-webpart-base@1.7.0 -SE
npm i @microsoft/sp-build-web@1.7.0 @microsoft/sp-module-interfaces@1.7.0 @microsoft/sp-webpart-workbench@1.7.0 -DE
npm un tslint-microsoft-contrib -D
mkdir G:\Classes\SPFxDevelopment\04 Publishing\06 Upgrading\HelloSPFx\teams_helloSpFxWp
cat > G:\Classes\SPFxDevelopment\04 Publishing\06 Upgrading\HelloSPFx\teams_helloSpFxWp\manifest.json << EOF
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.2/MicrosoftTeams.schema.json",
  "manifestVersion": "1.2",
  "packageName": "HelloSPFxWP",
  "id": "9a90a2cc-d2bf-4603-b847-907dfb3942df",
  "version": "0.1",
  "developer": {
    "name": "SPFx + Teams Dev",
    "websiteUrl": "https://products.office.com/en-us/sharepoint/collaboration",
    "privacyUrl": "https://privacy.microsoft.com/en-us/privacystatement",
    "termsOfUseUrl": "https://www.microsoft.com/en-us/servicesagreement"
  },
  "name": {
    "short": "HelloSPFxWP"
  },
  "description": {
    "short": "HelloSPFxWP description",
    "full": "HelloSPFxWP description"
  },
  "icons": {
    "outline": "tab20x20.png",
    "color": "tab96x96.png"
  },
  "accentColor": "#004578",
  "configurableTabs": [
    {
      "configurationUrl": "https://{teamSiteDomain}{teamSitePath}/_layouts/15/TeamsLogon.aspx?SPFX=true&dest={teamSitePath}/_layouts/15/teamshostedapp.aspx%3FopenPropertyPane=true%26teams%26componentId=9a90a2cc-d2bf-4603-b847-907dfb3942df",
      "canUpdateConfiguration": true,
      "scopes": [
        "team"
      ]
    }
  ],
  "validDomains": [
    "*.login.microsoftonline.com",
    "*.sharepoint.com",
    "*.sharepoint-df.com",
    "spoppe-a.akamaihd.net",
    "spoprod-a.akamaihd.net",
    "resourceseng.blob.core.windows.net",
    "msft.spoppe.com"
  ],
  "webApplicationInfo": {
    "resource": "https://{teamSiteDomain}",
    "id": "00000003-0000-0ff1-ce00-000000000000"
  }
}
EOF
cp C:\Users\Alexander\AppData\Roaming\nvm\v8.11.3\node_modules\@pnp\office365-cli\dist\o365\spfx\commands\project\project-upgrade\assets\tab20x20.png G:\Classes\SPFxDevelopment\04 Publishing\06 Upgrading\HelloSPFx\teams_helloSpFxWp\tab20x20.png
cp C:\Users\Alexander\AppData\Roaming\nvm\v8.11.3\node_modules\@pnp\office365-cli\dist\o365\spfx\commands\project\project-upgrade\assets\tab96x96.png G:\Classes\SPFxDevelopment\04 Publishing\06 Upgrading\HelloSPFx\teams_helloSpFxWp\tab96x96.png
npm dedupe
```

### Modify files

#### [./config/package-solution.json](./config/package-solution.json)

Update package-solution.json isDomainIsolated:

```json
{
  "solution": {
    "isDomainIsolated": false
  }
}
```

#### [./.yo-rc.json](./.yo-rc.json)

Update version in .yo-rc.json:

```json
{
  "@microsoft/generator-sharepoint": {
    "version": "1.7.0"
  }
}
```

Update isDomainIsolated in .yo-rc.json:

```json
{
  "@microsoft/generator-sharepoint": {
    "isDomainIsolated": false
  }
}
```

#### [./tslint.json](./tslint.json)

Remove rulesDirectory from tslint.json:

```json
{
  "rulesDirectory": []
}
```

Update tslint.json extends property:

```json
{
  "extends": "@microsoft/sp-tslint-rules/base-tslint.json"
}
```
