# UnityHubModding
For educational purposes only!<br>
Personally i use alternative launchers, so not affected from these Hub Pains(tm)<br>
Alternative Launchers: https://github.com/unitycoder/UnityLauncherPro/wiki/Alternative-Launchers<br>

### Hów to unpack app.asar?
- Unpack app.asar from Hub folder (using 7zip Asar plugin https://www.tc4shell.com/en/7zip/asar/ or python script https://github.com/unitycoder/UnityHubPatcher )
- rename old app.asar as app.asar.bak (then hub will run using the app/ folder instead of app.asar)
- Open app/ folder in VSCode/VSStudio (need to run as an Admin!)

## Contents
- [Uncheck "Connect to Unity Cloud" by default](#uncheck-connect-to-unity-cloud-by-default)
- [Enable Create Project Button (without having to select Cloud Organization)](#enable-create-project-button-without-having-to-select-cloud-organization)
- [Remove Version Control & Cloud Dashboard columns](#remove-version-control--cloud-dashboard-columns)
- [Add Support for Custom Project Titles from ProjectName.txt or ProjectSettings ProductName field (instead of using folder name)](#add-support-for-custom-project-titles-from-projectnametxt-or-projectsettings-productname-field-instead-of-using-folder-name)
- [Add IRC Chat to Hub window (using iframe)](#add-irc-chat-to-hub-window-using-iframe))
- [Custom Styles](#custom-styles)

<br>
<hr>

### Uncheck "Connect to Unity Cloud" by default
- Tested on Hub 3.6.1
- open build/renderer/main.js
- find line:<br> ```{testId:"connect-services-checkbox",id:"unified-project-enabled-checkbox",isChecked:Y,onChange```
- replace with:<br> ```{testId:"connect-services-checkbox",id:"unified-project-enabled-checkbox",isChecked:0==1,onChange```

### Enable Create Project Button (without having to select Cloud Organization)
- Tested on Hub 3.6.1
- open build/renderer/main.js
- find line:<br> ```{r({id:"cancel-create-project",label:"Cancel"}),e()},testId:`cancel-project-${i.name}`},n("common:CANCEL")),s.default.createElement(u.Button,{isDisabled:o||S,onClick:function(){r```
- replace with:<br> ```{r({id:"cancel-create-project",label:"Cancel"}),e()},testId:`cancel-project-${i.name}`},n("common:CANCEL")),s.default.createElement(u.Button,{isDisabled:1==0,onClick:function()```
- ![GGKi2WcXEAAT6EX](https://github.com/unitycoder/UnityHubModding/assets/5438317/699475de-a59b-47f8-a3d0-2a10cb8f3af8)

### Remove Version Control & Cloud Dashboard columns
- Tested on Hub 3.6.1
- https://unitycoder.com/blog/2023/10/29/unityhub-3-6-0-remove-version-control-cloud-dashboard-columns/
- ![image](https://github.com/unitycoder/UnityHubModding/assets/5438317/426aa7bb-9752-47bf-bfb4-d8ab1001a607)
  
### Add Support for Custom Project Titles from ProjectName.txt or ProjectSettings ProductName field (instead of using folder name)
- Tested on Hub 3.6.1
- https://unitycoder.com/blog/2023/12/07/unityhub-add-support-for-custom-project-titles-instead-of-folder-name/
- ![upload_2023-12-7_13-47-12](https://github.com/unitycoder/UnityHubModding/assets/5438317/69337194-6d55-455b-affb-9a8789b952f9)

### Add IRC Chat to Hub window (using iframe)
- Tested on Hub 3.6.1
- Open nuild/renderer/index.html
- Add any IRC embed code before ```</body>```, like: ```<iframe src="https://chat.undernet.org/" style="background: #444; width:99%; height:450px;"></iframe>```
- Video example: https://www.youtube.com/watch?v=3e9FSimbdfk
- ![GF2Au1-XUAEEra3](https://github.com/unitycoder/UnityHubModding/assets/5438317/3bb074e3-4118-4eef-ac6f-d03ff45eefdf)

### Custom Styles
- tested in Hub 3.0.x
- Light color theme example, but you could modify the css to anything else https://unitycoder.com/blog/2022/03/02/customize-unityhub-colors/
- ![image](https://github.com/unitycoder/UnityHubModding/assets/5438317/90c77478-fe4f-43d2-ba7e-3090dedc9d46)
