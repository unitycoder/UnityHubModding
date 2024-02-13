# UnityHubModding
for educational purposes only!

## Contents
- [link Uncheck "Connect to Unity Cloud" by default](#uncheck-connect-to-unity-cloud-by-default)
- [link Enable Create Project Button (without having to select Cloud Organization)](#enable-create-project-button-without-having-to-select-cloud-organization)
- [link Remove Version Control & Cloud Dashboard columns](#remove-version-control--cloud-dashboard-columns)
- [link Add Support for Custom Project Titles from ProjectName.txt or ProjectSettings ProductName field (instead of using folder name)](#add-support-for-custom-project-titles-from-projectnametxt-or-projectsettings-productname-field-instead-of-using-folder-name)
- [link Add IRC Chat to Hub window (using iframe)](#add-irc-chat-to-hub-window-using-iframe))

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

