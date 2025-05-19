# UnityHubModding
For educational purposes only!<br>
Personally i use alternative launchers, so not affected from these Hub Pains(tm)<br>
Alternative Launchers: https://github.com/unitycoder/UnityLauncherPro/wiki/Alternative-Launchers<br>

### Hów to unpack app.asar?
- Inside C:\Program Files\Unity Hub\resources\ Unpack app.asar into app/ folder (using 7zip Asar plugin https://www.tc4shell.com/en/7zip/asar/ or python script https://github.com/unitycoder/UnityHubPatcher )
- Rename old app.asar as app.asar.bak (then hub will run using the app/ folder instead of app.asar)
- Open app/ folder in VSCode/VSStudio (need to run as an Admin!)

## Contents
- [Uncheck "Connect to Unity Cloud" by default](#uncheck-connect-to-unity-cloud-by-default)
- [Enable Create Project Button (without having to select Cloud Organization)](#enable-create-project-button-without-having-to-select-cloud-organization)
- [Remove Version Control & Cloud Dashboard columns](#remove-version-control--cloud-dashboard-columns)
- [Add Support for Custom Project Titles from ProjectName.txt or ProjectSettings ProductName field (instead of using folder name)](#add-support-for-custom-project-titles-from-projectnametxt-or-projectsettings-productname-field-instead-of-using-folder-name)
- [Add IRC Chat to Hub window (using iframe)](#add-irc-chat-to-hub-window-using-iframe))
- [Custom Styles](#custom-styles)
- [Custom Previews or any html for project template description](#custom-previews-or-any-html-for-project-templates-description)
- [Enable Built-in Login Dialog (no more browser login/logout issues with multiple accounts](#enable-built-in-login-dialog-no-more-browser-loginlogout-issues-with-multiple-accounts)
- [Completely quit Hub when you press X (window close button)](#completely-quit-unity-hub-when-you-press-x-window-close-button)
- [Make Hub background translucent](#make-hub-background-translucent)
- [Custom username initials in Editor](#custom-username-initials-in-editor)
<br>
<hr>

### Uncheck "Connect to Unity Cloud" by default
- Tested on Hub 3.6.1
- open build/renderer/main.js
- find line:<br> ```{testId:"connect-services-checkbox",id:"unified-project-enabled-checkbox",isChecked:Y,onChange```
- replace with:<br> ```{testId:"connect-services-checkbox",id:"unified-project-enabled-checkbox",isChecked:0==1,onChange```
<hr>

### Enable Create Project Button (without having to select Cloud Organization)
- Tested on Hub 3.6.1
- open build/renderer/main.js
- find line:<br> ```{r({id:"cancel-create-project",label:"Cancel"}),e()},testId:`cancel-project-${i.name}`},n("common:CANCEL")),s.default.createElement(u.Button,{isDisabled:o||S,onClick:function(){r```
- replace with:<br> ```{r({id:"cancel-create-project",label:"Cancel"}),e()},testId:`cancel-project-${i.name}`},n("common:CANCEL")),s.default.createElement(u.Button,{isDisabled:1==0,onClick:function()```
- ![GGKi2WcXEAAT6EX](https://github.com/unitycoder/UnityHubModding/assets/5438317/699475de-a59b-47f8-a3d0-2a10cb8f3af8)
<hr>

### Remove Version Control & Cloud Dashboard columns
- Tested on Hub 3.6.1
- https://unitycoder.com/blog/2023/10/29/unityhub-3-6-0-remove-version-control-cloud-dashboard-columns/
- ![image](https://github.com/unitycoder/UnityHubModding/assets/5438317/426aa7bb-9752-47bf-bfb4-d8ab1001a607)
  <hr>

### Add Support for Custom Project Titles from ProjectName.txt or ProjectSettings ProductName field (instead of using folder name)
- Tested on Hub 3.6.1
- https://unitycoder.com/blog/2023/12/07/unityhub-add-support-for-custom-project-titles-instead-of-folder-name/
- ![upload_2023-12-7_13-47-12](https://github.com/unitycoder/UnityHubModding/assets/5438317/69337194-6d55-455b-affb-9a8789b952f9)
<hr>

### Add IRC Chat to Hub window (using iframe)
- Tested on Hub 3.6.1
- Open _build/renderer/index.html_
- Add any IRC embed code before ```</body>```, like: ```<iframe src="https://chat.undernet.org/" style="background: #444; width:99%; height:450px;"></iframe>```
- Video example: https://www.youtube.com/watch?v=3e9FSimbdfk
- ![GF2Au1-XUAEEra3](https://github.com/unitycoder/UnityHubModding/assets/5438317/3bb074e3-4118-4eef-ac6f-d03ff45eefdf)
<hr>

### Custom Styles
- tested in Hub 3.0.x
- Light color theme example, but you could modify the css to anything else https://unitycoder.com/blog/2022/03/02/customize-unityhub-colors/
- ![image](https://github.com/unitycoder/UnityHubModding/assets/5438317/90c77478-fe4f-43d2-ba7e-3090dedc9d46)
<hr>

### Custom Previews (or any html) for Project Templates description
- This doesn't require modifying Hub sources! it just works.
- Modify package.json to add HTML+CSS
- https://unitycoder.com/blog/2024/03/06/custom-unity-hub-project-template-preview-image-video-using-htmlcss-in-package-description/
- ![ssprojecttemplate2024-03-06 11-39-57](https://github.com/unitycoder/UnityHubModding/assets/5438317/c054a96c-5e58-4842-8fb4-ac0b5fee16c9)
<hr>

### Enable Built-in Login Dialog (no more browser login/logout issues with multiple accounts!)
- Open Unity _Hub\resources\app\build\main\services\authService\AuthService.js_
- Find line: <br> ```if ((0, appDefaultProtocolClientHelpers_1.isUnityHubProtocolHandled)()) {```
- Replace with<br> ```if (1==0 && (0, appDefaultProtocolClientHelpers_1.isUnityHubProtocolHandled)())```
- (to make this “if” be false, so that createLoginWindow gets called instead)
- Alternative to modifying source: Could try disabling "UnityHub" protocol from Registry, since the code tries to check for it "isUnityHubProtocolHandled"
- info https://unitycoder.com/blog/2024/04/26/unityhub-enable-builtin-login-dialog-no-more-browser-login-logout-issues/
- ![image](https://github.com/unitycoder/UnityHubModding/assets/5438317/43afdd85-d3f4-491c-9bba-8e1af4b9c9e0)
<hr>

### Completely quit Unity Hub when you press X (window close button)
- Open baseWindow.js
- add ```const electron_1 = require("electron");``` at the top (next to other require lines)
- Find line ```logger.debug('close event is prevented, browser window will be hidden');```
- add this line after it ```electron_1.app.quit();```
<hr>

### Make Hub background translucent
- Steps: https://unitycoder.com/blog/2024/07/05/unityhub-make-hub-application-background-translucent/
- ![image](https://github.com/unitycoder/UnityHubModding/assets/5438317/55892c15-2819-4f46-b76a-41ad019e5571)

### Custom username initials in Editor
- If you dont want to doxx your initials on Editor screen
- You change them in Unity Profile at unity id site, or modify hub sources
- Open AuthServices.js
- Find ```displayName: this.userInfo.name,``` (its inside getFormattedUserInfo() method)
- replace with any short string for your initials
- ![Image](https://github.com/user-attachments/assets/6c7e5c0c-a6fb-447f-b6ab-44f5eb3e7938)
- Hub 3.12.x has everything changed:
- Open IdentityProvider.js
- Find ```const { userInfo: e } = AuthService_1.default;```
- override your initials there
- ```e.name = "🥔 🥔";```
- ![image](https://github.com/user-attachments/assets/88eca0aa-9b07-4688-8e96-b8b18863ab0c)


<br><br><br><br><br><br><br><br><br><br><br><br>
