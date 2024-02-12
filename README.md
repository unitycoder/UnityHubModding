# UnityHubModding
for educational purposes only!

### Uncheck "Connect to Unity Cloud" by default
- open build/renderer/main.js
- find line:<br> ```{testId:"connect-services-checkbox",id:"unified-project-enabled-checkbox",isChecked:Y,onChange```
- replace with:<br> ```{testId:"connect-services-checkbox",id:"unified-project-enabled-checkbox",isChecked:0==1,onChange```


### Enable Create Project Button (without having to select Cloud Organization)
- open build/renderer/main.js
- find line:<br> ```{r({id:"cancel-create-project",label:"Cancel"}),e()},testId:`cancel-project-${i.name}`},n("common:CANCEL")),s.default.createElement(u.Button,{isDisabled:o||S,onClick:function(){r```
- replace with:<br> ```{r({id:"cancel-create-project",label:"Cancel"}),e()},testId:`cancel-project-${i.name}`},n("common:CANCEL")),s.default.createElement(u.Button,{isDisabled:1==0,onClick:function()```
