# UnityHubModding
for educational purposes only!

## Contents
- 


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

### Remove Version Control & Cloud Dashboard columns
- Tested on Hub 3.6.1
- https://unitycoder.com/blog/2023/10/29/unityhub-3-6-0-remove-version-control-cloud-dashboard-columns/

### Add Support for Custom Project Titles from ProjectName.txt or ProjectSettings ProductName field (instead of using folder name)
- Tested on Hub 3.6.1
- https://unitycoder.com/blog/2023/12/07/unityhub-add-support-for-custom-project-titles-instead-of-folder-name/

### Add IRC Chat to Hub window (using iframe)
- Tested on Hub 3.6.1
- Open nuild/renderer/index.html
- Add any IRC embed code before ```</body>```, like: ```<iframe src="https://chat.undernet.org/" style="background: #444; width:99%; height:450px;"></iframe>```
- Video example: https://www.youtube.com/watch?v=3e9FSimbdfk
