---
title: roam42-template
---

## #42SmartBlock YouTube TimeStamp
### {{AddTimestamp 42SmartBlock}}

### <%IFTRUE:"<%GET:varYTbut%>" == "y"%><%JAVASCRIPT:
```javascript

if (window.YT !== undefined) {
    if (Array.from(document.getElementsByTagName('IFRAME')).filter(iframe => iframe.src.includes('youtube.com'))[0]) {
        var getClosestParent = function (elem, srcStr) {
            for (; elem && elem !== document; elem = elem.parentNode) {
                if (elem.getElementsByTagName('IFRAME').length > 0) {
                    var foundIframe = elem.getElementsByTagName('IFRAME')[0];
                    if (foundIframe.src.includes(srcStr)) { return foundIframe };
                }
            }
            return null;
        };
        var ytIframe = getClosestParent(document.getElementsByTagName('TEXTAREA')[0], 'youtube.com');
        if (ytIframe) {
            var ytIframeId = ytIframe.id;
            var ytPlayer = YT.get(ytIframeId);
            var currentTime = ytPlayer.getCurrentTime() - 5;
            if (currentTime < 1) { currentTime = 1 };
            return (new Date(currentTime * 1000).toISOString().substr(11, 8)) + ' - ';
        }
        else {
            return "No YouTube Player Open!";
        }
    }
    else {
        return "No YouTube Player Open!";
    }
}
```
%><%CURSOR%>

### <%IFTRUE:"<%GET:varYTbut%>" != "y"%> <%CURSOR%>

### <%SET:varYTbut,n%><%NOBLOCKOUTPUT%>

## 

## #42SmartBlock z_Shortcut embed youtube
### <%SET:varCurBlock,<%RESOLVEBLOCKREF:<%CURRENTBLOCKREF%>%>%><%NOBLOCKOUTPUT%>

### <%JAVASCRIPT:
```javascript

document.activeElement.value = '';
var curBlock = roam42.smartBlocks.activeWorkflow.vars["varCurBlock"];
var newVal = curBlock.substring(0,curBlock.indexOf(';;')).trim();
roam42.smartBlocks.activeWorkflow.vars["varCurBlock"] = newVal;
return '';```
%><%NOBLOCKOUTPUT%>

### TODO {{[[YouTubeTimeStamp]] null}}[ ]([[Toread]])
#### <%CONCAT:{,{[,[youtube]]:,<%GET:varCurBlock%>,}}%>
##### <%NOBLOCKOUTPUT%>

##### <%SMARTBLOCK:YouTube TimeStamp%>
