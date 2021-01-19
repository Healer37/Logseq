---
title: roam/js
---

## **Roam42**
### {{[[roam/js]] null}}
#### ```javascript

// DISABLE FEATURES
// Remove two forward slashes from in front of name 
// of feature to DISABLE it
// Everything is enabled by default
window.disabledFeatures = [
  // 'quickReference',
  // 'lookupUI',
  // 'livePreview',
  // 'dailyNote',
  // 'templatePoc',
  // 'jumpToDate',
  // 'jumpNav',
];

// Live Preview - to change the defaults 
// 1) remove // in front of parameter to ACTIVATE the change
// 2) modify the value to change it's behavior
// width  = width of preview window
// height = height of preview window
// delay  = milliseconds of delay for preview to 
// 			fire (defaults to 200) can be set to 0
window.roam42LivePreview = {
  //width:	'400px',
  //height: '600px',
  //delay: 500,
};


// Change the Deep navigation options
// activate-on-no-focus - activate navigation mode when body is focused (default: false)
// REMOVE // in front of setting to change it from default setting
window.roamNavigatorSettings = {
//   'activate-on-no-focus': true, 
};;

var s = document.createElement('script');
	s.type = "text/javascript";
  //  s.src =  "https://roam42.glitch.me/main.js";
   	s.src =  "https://roam42-test.glitch.me/main.js";
	s.async = true;
document.getElementsByTagName('head')[0].appendChild(s);
```

### {{[[roam/js]] null}}
#### ```javascript

// DISABLE FEATURES
// Remove two forward slashes from in front of name 
// of feature to DISABLE it
// Everything is enabled by default
window.disabledFeatures = [
  // 'quickReference',
  // 'turnDown',
  // 'dateProcessing',
  // 'lookupUI',
  // 'livePreview',
  // 'dailyNote',
  // 'jumpToDate',
  // 'jumpNav',
];

// Live Preview - to change the defaults 
// 1) remove // in front of parameter to ACTIVATE the change
// 2) modify the value to change it's behavior
// width  = width of preview window
// height = height of preview window
// delay  = milliseconds of delay for preview to 
// 			fire (defaults to 200) can be set to 0
window.roam42LivePreview = {
  //width:	'400px',
  //height: '600px',
  //delay: 500,
};

// Change the Deep navigation options
// activate-on-no-focus - activate navigation mode when body is focused (default: false)
// REMOVE // in front of setting to change it from default setting
window.roamNavigatorSettings = {
 //  'activate-on-no-focus': true, 
};

var s = document.createElement('script');
	s.type = "text/javascript";
    s.src =  "https://cdn.jsdelivr.net/gh/roamhacker/roam42/main.js";
      // "https://roam42.glitch.me/main.js";
  	s.async = true;
document.getElementsByTagName('head')[0].appendChild(s);
```

## **日期样式**
### {{[[roam/js]] null}}
#### ```javascript
/*
 * Viktor's Roam default date format POC
 * version: 0.2
 * author: @ViktorTabori
 *
 * How to install it:
 *  - go to page [[roam/js]]
 *  - create a node with: { {[[roam/js]]}}
 *  - create a clode block pulled under it, and change its type from clojure to javascript
 *  - allow the running of the javascript on the {{[[roam/js]] null}} node
 *  - reload roam
 */
if (window.ViktorMutation) window.ViktorMutation.stop();
window.ViktorMutation = (function(){
  var dateformat = 'YYYY-MM-DD EE';  // EEE stands for `Tuesday` for example
	// formats dates, roam default is `Month Dth, YYYY`
	/*
	 * dY - delta years between date and today
	 * dM - delta month between date and today
	 * dW - delta week between date and today
	 * dD - delta day between date and today
	 * YYYY - year, 2020
	 * YY - year, 20
	 * Month - month, January
	 * Mon - month, Jan
	 * MM - month, 01
	 * M - month 1
	 * DD - day, 07
	 * D - day, 7
	 * th - after any number: 5th
	 * (s) - plural form decoder: 5 day(s) -> 5 days
	 * WW - week of year, 09
	 * W - week of year, 9
	 * EEE - day of week, Tuesday
	 * EE - day of week, Tue
	 * E - day of week 1-7
	*/
  var observer,
		started = false,
		lookfor = [
			'title',
			'.level2',
			'.rm-title-display',
			'.rm-ref-page-view-title span', 
			'.rm-page-ref',
			'.rm-search-title',
			'.bp3-text-overflow-ellipsis > div', 
			'.rm-autocomplete-result', 
			'.rm-zoom span',
			'.bp3-popover button.bp3-button' // filters
		].join(', '),
		months = ['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December'],
		monthsShort = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'],
		days = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday', 'Sunday'],
		daysShort = ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'];

	// start date change
	setTimeout(start, 1000);

	return {
		start: start,
		stop: stop,
		started: started,
		observer: observer,
		callback: callback,
		dateformat: dateformat,
		changeDate: changeDate,
	}

	function start() {
		if (started) return;
		started = true;

		// change current dates
		changeDate(document); 

		// subscribe to changes
		observer = new MutationObserver(callback);
		observer.observe(document, { childList: true, subtree: true });

		// log
		console.log('looking for mutations for date change');

		return true;
	}

	function stop() {
		if (!started) return;
		started = false;

		observer.disconnect();

		// log
		console.log('stopped looking for date replaces');

		return true;
	}

	function callback(mutationsList, observer) {
		for(var mutation of mutationsList) {
	    	if (mutation.addedNodes && mutation.addedNodes.length) {
				processMutation(mutation);
	    	}
	    }
	}

	function processMutation(mutation) {
		for (var i=0; i<mutation.addedNodes.length; i++) {
			changeDate(mutation.addedNodes[i]);
		}
	}

	function changeDate(dom) {
		if (!dom) return;
		var mutations = [];

		// filter changed elements
		if (dom.querySelectorAll)
			mutations = Array.from(dom.querySelectorAll(lookfor));
		else
		// ignore textareas
		if (dom.parentNode && dom.parentNode.closest && dom.parentNode.closest('textarea'))
			return;
		else
		// add text nodes
		if (dom.textContent)
			mutations.push(dom);

		mutations = mutations.filter(function(_e){ 
			if (!_e.textContent || !_e.parentNode) return; // return if no text content

			// get date match
			var date = (_e.textContent.match(/#?(January|February|March|April|May|June|July|August|September|October|November|December) \d{1,2}(st|nd|rd|th), \d{4}/i)||[''])[0];
			if (!date) return;

			// get exact matching text nodes
			var result = document.evaluate(".//text()[.='"+ date.replace(/'/g,"\\'") +"']", _e, null, XPathResult.ORDERED_NODE_SNAPSHOT_TYPE);
			var nodes = Array.from({ length: result.snapshotLength }, (_, index) => result.snapshotItem(index));
			if (!nodes.length) return;
			_e = nodes[0];

			// replace dates
			var changed = _e.textContent.replace(date, function(_v){
				return (_v && _v[0]=='#' ? '#' : '') + dateFormat(_v.replace(/^#/,'').replace(/(\d)(st|nd|rd|th)/g,'$1'), dateformat);
			});

			// only change textContent when the content should be changed, otherwise assigning value to textContent can mess up the DOM
			if (changed != _e.textContent) {
				// save original content
				if (_e.parentNode && _e.parentNode.dataset) _e.parentNode.dataset.originalText = _e.textContent;

				// change format
				_e.textContent = changed;
				return true;
			}

			return;
		});	

		if (mutations.length) {
			//console.log('date replaced:',mutations);
			window._tmp = mutations;
		}
	}

	// formats dates
	/*
	 * dY - delta years between date and today
	 * dM - delta month between date and today
	 * dW - delta week between date and today
	 * dD - delta day between date and today
	 * YYYY - year, 2020
	 * YY - year, 20
	 * Month - month, January
	 * Mon - month, Jan
	 * MM - month, 01
	 * M - month 1
	 * DD - day, 07
	 * D - day, 7
	 * th - after any number: 5th
	 * (s) - plural form decoder: day(s)
	 * WW - week of year, 09
	 * W - week of year, 9
	 * EEE - day of week, Tuesday
	 * EE - day of week, Tue
	 * E - day of week 1-7
	*/
	function dateFormat(date, format){
		var text = format || '[[Month Dth, YYYY]]'; // default format
		var date = new Date(date);
			date.setHours(12,0,0,0);
		var today = new Date();
			today.setHours(12,0,0,0);

		// dD
		text = text.replace(/dD/g, function(){
			return Math.floor(Math.abs(date.getTime()-today.getTime())/1000/60/60/24);
		});

		// dW
		text = text.replace(/dW/g, function(){
			return Math.floor(Math.abs(date.getTime()-today.getTime())/1000/60/60/24/7);
		});

		// dM
		text = text.replace(/dM/g, function(){
			var d1 = new Date(compareDates(date, today) > 0 ? date : today);
			var d2 = new Date(compareDates(date, today) > 0 ? today : date);
			return (d1.getFullYear()-d2.getFullYear())*12+d1.getMonth()-d2.getMonth()+(d1.getDate()>=d2.getDate()?1:0)-1;
		});

		// dY
		text = text.replace(/dY/g, function(){
			var d1 = new Date(compareDates(date, today) > 0 ? date : today);
			var d2 = new Date(compareDates(date, today) > 0 ? today : date);
			var ret = (d1.getFullYear()-d2.getFullYear())-1;
			d2.setFullYear(d1.getFullYear());
			return ret + (compareDates(d1,d2) >= 0 ? 1 : 0);
			//return Math.floor(Math.abs(date.getTime()-today.getTime())/1000/60/60/24/365);
		});

		// YYYY
		text = text.replace(/YYYY/g, function(){
			return date.getFullYear();
		});

		// YY
		text = text.replace(/YY/g, function(){
			return date.getFullYear().toString().substr(-2);
		});

		// Month
		text = text.replace(/Month/g, function(){
			return months[ date.getMonth() ];
		});

		// Mon
		text = text.replace(/Mon/g, function(){
			return monthsShort[ date.getMonth() ];
		});

		// MM
		text = text.replace(/MM/g, function(){
			var month = date.getMonth() + 1;
			return month < 10 ? '0'+month : month;
		});

		// M
		text = text.replace(/M(?![ao])/g, function(){
			return date.getMonth() + 1;
		});

		// DD
		text = text.replace(/DD/g, function(){
			var day = date.getDate();
			return day < 10 ? '0'+day : day;
		});

		// D
		text = text.replace(/D(?!e)/g, function(){
			return date.getDate();
		});

		// WW
		text = text.replace(/WW/g, function(){
			var week = getWeekOfYear(date);
			return week < 10 ? '0'+week : week;
		});

		// W
		text = text.replace(/W(?!e)/g, function(){
			return getWeekOfYear(date);
		});

		// EEE
		text = text.replace(/EEE/g, function(){
			return days[getDayOfWeek(date)];
		});

		// EE
		text = text.replace(/EE/g, function(){
			return daysShort[getDayOfWeek(date)];
		});

		// E
		text = text.replace(/E/g, function(){
			return getDayOfWeek(date)+1;
		});

		// th
		text = text.replace(/(\d+)\s*(th|st|nd|rd)/g, function(_,number){
			var str = number.substr(-2);
			var suffix;
			switch (str.substr(-1)) {
				case '1':
					suffix = 'st';
					break;
				case '2':
					suffix = 'nd';
					break;
				case '3':
					suffix = 'rd';
					break;
				default:
					suffix = 'th';
			}
			// th for all `1X` numbers
			if (str.length > 1 && str[0] == 1) {
				suffix = 'th';
			}
			return number+suffix;
		});

		// (s)
		text = text.replace(/([\s\d\.\,]+)([\w\s]+\(s\))/g, function(_, _n, _w){
			_w = parseFloat(_n.replace(/[\s,]/g,'')) > 1 ? _w.replace('(s)','s') : _w.replace('(s)','');
			return _n+_w;
		});

		return text;
	}

	// add `days` days to date
	function addDay(days, date) {
		date = new Date(date);

		date.setDate(date.getDate()+days);
		return date;
	}

	// return Ceil + 1 for integers, otherwise the Ceil
	function upperCeil(num) {
		return Math.ceil(num%1 === 0 ? num+1 : num);
	}

	// get day of week: 0 - Monday, 6 - Sunday
	function getDayOfWeek(date) {
		date = new Date(date);
		return (date.getDay()+6)%7;	// week begins with monday
	}

	// week number of the year
	function getWeekOfYear(date) {
		date = new Date(date);
		// get first Monday of the year
		var week1 = new Date(date.getFullYear(), 0, 1);
		week1 = addDay(-getDayOfWeek(week1), week1);
		// calculate the difference in weeks
		var diff = (date.getTime()-week1.getTime())/(60*60*24*7*1000);
		return upperCeil(diff);
	}

	// compares two dates
	function compareDates(date1,date2) {
		date1 = (new Date(date1)).toISOString().substr(0,10);
		date2 = (new Date(date2)).toISOString().substr(0,10);

		if (date1 < date2) return -1;
		if (date1 > date2) return 1;
		return 0;
	}

})();
```

## **Unlink Finder**
### {{[[roam/js]] null}}
#### ```javascript
var s = document.createElement('script');
	s.type = "text/javascript";
  	s.src =  "https://tylerwince.github.io/roam-plugins/unlink-finder/unlink-finder.js";
  	s.async = true;
document.body.appendChild(s);```

## **卡片式主题**
### {{[[roam/js]] null}}
#### ```javascript
 const CARD_MODE_VERSION = 'f61eecf'

 
window.URLScriptServer = `https://cdn.jsdelivr.net/gh/JimmyLv/styled-roam@${CARD_MODE_VERSION}/`
var s = document.createElement('script')
 s.type = "text/javascript"
    s.src =  window.URLScriptServer + "js/index.js"
 s.async = true
document.getElementsByTagName('head')[0].appendChild(s)```

### CARD_MODE_VERSION 版本号
#### 442b3cb5
##### 小图标

#### 2357517

#### 854539d6

#### 1d14b520

#### d4507a7c 

## **Roambookclub Styles**
### RBC/Block remixer
#### {{[[roam/js]] null}}
##### ```javascript
const COMMAND = "remix!";
const TEXT_AREA_REGEX = new RegExp(`.*${COMMAND}.*`);
const SAMPLE_SIZE = 2;

function getRandomInts(n, min, max, results = []) {
  if (results.length === n) return results;

  if (Math.abs(max - min) + 1 < n)
    throw new Error(`Can't find enough unique values`);

  const i = Math.floor(Math.random() * (max - min + 1)) + min;

  if (!results.includes(i)) {
    return getRandomInts(n, min, max, [...results, i]);
  }

  return getRandomInts(n, min, max, [...results]);
}

function sample(n, array) {
  const indexes = getRandomInts(n, 0, array.length - 1);
  return array.filter((_e, i) => indexes.includes(i));
}

function findBlockInputs(node, blockInputs = []) {
  node.childNodes.forEach((n) => {
    if (n.id && n.id.match(/block-input/)) {
      blockInputs.push(n);
    } else {
      findBlockInputs(n, blockInputs);
    }

    return blockInputs;
  });

  return [...blockInputs];
}

const extractBlockId = (blockNode) => {
  return blockNode.id.match(/.{9}$/)[0];
};

const extractBlockReferences = (blockNodes) => {
  const blockReferences = [];

  blockNodes.forEach((blockNode) => {
    blockReferences.push(`((${extractBlockId(blockNode)}))`);
  });

  return blockReferences;
};

const applyRemixedBlocks = (str) => {
  const queryResultsNode = document.querySelector(".rm-query-content");
  
  if (!queryResultsNode) return alert(`Can't remix! Do you have query results showing?`)
  
  const blockReferences = extractBlockReferences(
    findBlockInputs(queryResultsNode)
  );
  const sampling = sample(SAMPLE_SIZE, blockReferences);

  if (!blockReferences.length) return;

  return str.replace(new RegExp(COMMAND), sampling.join("\n"));
};

const handleEnterPress = (evt) => {
  if (evt.key === "Enter") {
    const value = applyRemixedBlocks(evt.target.value);

    if (!value)
      return alert("No blocks found to remix! Are there query results?");

    evt.target.value = value;
  }
};

const applyListener = () =>
  document.querySelectorAll("textarea").forEach((el) => {
    if (el.value.match(COMMAND)) {
      el.onkeydown = handleEnterPress;
    }
  });

const observer = new MutationObserver(applyListener);

observer.observe(document.body, { subtree: true, childList: true });
```

### The below is David Vargas' JS that allows for the filtering and sorting of linked references. It is here primarily to allow shared users to view and filter group # chat  but also will help, e.g., viewing our directory
#### {{[[roam/js]] null}}
##### ```javascript
var old = document.getElementById("sort-references");
if (old) {
  old.remove();
}

var s = document.createElement("script");
s.src = "https://roamjs.com/sort-references.js";
s.id = "sort-references";
s.async = false;
s.type = "text/javascript";
document.getElementsByTagName("head")[0].appendChild(s);```

### roamext
#### {{[[roam/js]] null}}
##### ```javascript
		

;(()=>{
  
  if( typeof window.catominor_tags != 'undefined') return;

  window.catominor_tags = {};

  const scanTags = () => {
    document.querySelectorAll('[data-tag]').forEach( (element)=>{
      console.log("start");
      let divBlockTagAttributeArray;
      let divBlock = element.parentElement.parentElement;
      const tagAttribute = " " + element.getAttribute('data-tag') + " ";
      
      
      

      
      let divBlockTagAttribute = divBlock.getAttribute("data-tags");
      
      if (divBlockTagAttribute ==  null){
        divBlockTagAttributeArray = [];
      } else {
        
        divBlockTagAttributeArray = divBlockTagAttribute.split(","); 
      }
    
      let index;
	 
      if(element) {
        console.log(tagAttribute);
        let index = divBlockTagAttributeArray.indexOf(tagAttribute);
        if (index == -1) {
       			divBlockTagAttributeArray.push(tagAttribute);
   		 }
     
      } else {
         let index = divBlockTagAttributeArray.indexOf(tagAttribute);
		 if (index > -1) {
       			divBlockTagAttributeArray.splice(index, 1);
   		 }
         
        
        
      }
      console.log(divBlockTagAttributeArray);
      divBlock.dataset.tags = divBlockTagAttributeArray.join();
      divBlock.parentNode.parentNode.parentNode.dataset.tagsUp = " " + divBlockTagAttributeArray.join() + " ";
     // divBlock.parentNode.parentNode.parentNode.childNodes[0].dataset.tagsDown = divBlockTagAttributeArray.join();


      console.log(divBlock.dataset.tags);
  
    })
  }

  scanTags()
  var observerTags = new MutationObserver(scanTags);
  observerTags.observe(document.querySelector('#app'), {
    childList: true,
    subtree: true
  })

})();```

### **ROAMEXT (beta)**
#### {{[[roam/js]] null}}
##### ```javascript

/* 
v.03 beta
*/

;(()=>{
  
  if( typeof window.catominor_tags != 'undefined') return;

  window.catominor_tags = {};

  const scanTags = () => {
    document.querySelectorAll('[data-tag]').forEach( (element)=>{
      console.log("start");
      let divBlockTagAttributeArray;
      let divBlock = element.closest("div");
      const tagAttribute = " " + element.getAttribute('data-tag') + " ";
      
  
      

      
      let divBlockTagAttribute = divBlock.getAttribute("data-tags");
      
      if (divBlockTagAttribute ==  null){
        divBlockTagAttributeArray = [];
      } else {
        
        divBlockTagAttributeArray = divBlockTagAttribute.split(","); 
      }
    
      let index;
	 
      if(element) {
        console.log(tagAttribute);
        let index = divBlockTagAttributeArray.indexOf(tagAttribute);
        if (index == -1) {
       			divBlockTagAttributeArray.push(tagAttribute);
   		 }
     
      } else {
         let index = divBlockTagAttributeArray.indexOf(tagAttribute);
		 if (index > -1) {
       			divBlockTagAttributeArray.splice(index, 1);
   		 }
         
        
        
      }
      console.log(divBlockTagAttributeArray);
      divBlock.dataset.tags = divBlockTagAttributeArray.join();
      divBlock.parentNode.parentNode.parentNode.dataset.tagsUp = " " + divBlockTagAttributeArray.join() + " ";
     // divBlock.parentNode.parentNode.parentNode.childNodes[0].dataset.tagsDown = divBlockTagAttributeArray.join();


      console.log(divBlock.dataset.tags);
  
    })
  }

  scanTags()
  var observerTags = new MutationObserver(scanTags);
  observerTags.observe(document.querySelector('#app'), {
    childList: true,
    subtree: true
  })

})();```

## ** YouTube Timestamp**
### {{[[roam/js]] null}}
#### ```javascript
// ==UserScript==
// @name         Responsive YouTube with Timestamp Control for Roamresearch
// @author       Connected Cognition Crumbs <c3founder@gmail.com>
// @version      0.2
// @description  Add timestamp controls to YouTube videos embedded in Roam and makes the player responsive. 
// @match        https://*.roamresearch.com

(function() {
    let ytApiReady = false;
    const players = new Map();  	
    const activateYtVideos = () => {	
        if (!ytApiReady) {
            if (window.YT !== undefined) loadYtApi(); // wait until Roam loads its YT, then insert script on top
            return null;
        }
        Array.from(document.getElementsByTagName('IFRAME'))
            .filter(iframe => iframe.src.includes('youtube.com'))            
            .forEach(ytEl => {          		
          		const block = ytEl.closest('.roam-block-container');          		
          		if(ytEl.src.indexOf("enablejsapi") === -1){
                  var ytId = extractVideoID(ytEl.src); 
                  var frameId = genUniquePlayerId(ytEl,ytId);			
                  ytEl.parentElement.id = frameId; 
                  ytEl.remove();
                  players[frameId] = new window.YT.Player(frameId, {
                    height: '300',
                    width: '450', 
                    videoId: ytId
                  });                        
                  wrapIframe(frameId);
                } else {				                                      
                  var frameId = ytEl.id				  
                }         
          		addTimestampControls(block, players[frameId]);   
          		var sideBarOpen = document.getElementById("right-sidebar").childElementCount - 1;
          		//Make iframes flexible
          		adjustIframe(frameId, sideBarOpen);  
        	});
    };

	const genUniquePlayerId = (ytEl, ytId) => {
      var d = new Date();
      var n = d.getTime();
      const rsideBar = ytEl.closest('#right-sidebar');
      return (rsideBar ? (ytId + '-rSide') : ytId) + n;
    };  	
  
    const addTimestampControls = (block, player) => {
      if (block.children.length < 2) return null;
      const childBlocks = Array.from(block.children[1].querySelectorAll('.roam-block-container'));
      childBlocks.forEach(child => {
        const timestamp = getTimestamp(child);
        const buttonIfPresent = child.querySelectorAll('.timestamp-control')[0]
        if (buttonIfPresent) {
          	buttonIfPresent.remove();
        }
        if (timestamp) { 
          addControlButton(child, () => player.seekTo(timestamp, true));
        }
      });
	};
  
	const adjustIframe = (frameId, sideBarOpen) => {
      var child = document.getElementById(frameId); //Iframe
      var par = child.parentElement;
      if(sideBarOpen){
        child.style.position = 'absolute';
        child.style.margin = '0px';
        child.style.border = '0px';
        child.style.width = '100%';
        child.style.height = '100%';
        child.style.borderStyle = 'inset';
        child.style.borderRadius = '25px';
        par.style.position = 'relative';
        par.style.paddingBottom = '56.25%';     
        par.style.height = '0px';
      } else {
      	child.style.position = null;
        child.style.margin = '0px';
        child.style.border = '0px';        
        child.style.width = '600px';
        child.style.height = '400px';
        child.style.borderStyle = 'inset';
        child.style.borderRadius = '25px';
        par.style.position = null;
        par.style.paddingBottom = '0px';   
		par.style.height = '420px';
      }
    }
    
    //const wrapIframe = (frameId, divId) => {
    const wrapIframe = (frameId) => {
      var child = document.getElementById(frameId); //Iframe
      var par = document.createElement('div');
      child.parentNode.insertBefore(par, child);
      par.appendChild(child);
      child.style.position = 'absolute';
      child.style.margin = '0px';
      child.style.border = '0px';
      child.style.width = '100%';
      child.style.height = '100%';
      par.style.position = 'relative';
      par.style.paddingBottom = '56.25%';     
      par.style.height = '0px';
      //par.id = divId;
    };
    const getControlButton = (block) => block.querySelectorAll('.timestamp-control')[0];

    const addControlButton = (block, fn) => {
        const button = document.createElement('button');
        button.innerText = '►';
        button.classList.add('timestamp-control');
      	button.style.borderRadius = '50%';
        button.addEventListener('click', fn);
        const parentEl = block.children[0].children[0];
        parentEl.insertBefore(button, parentEl.querySelectorAll('.roam-block')[0]);
    };

    const getTimestamp = (block) => {
        const innerBlockSelector = block.querySelectorAll('.roam-block');
        const blockText = innerBlockSelector.length ? innerBlockSelector[0].textContent : '';
        const matches = blockText.match(/^((?:\d+:)?\d+:\d\d)\D/); // start w/ m:ss or h:mm:ss
      	//console.log(matches)
        if (!matches || matches.length < 2) return null;
        const timeParts = matches[1].split(':').map(part => parseInt(part));
        if (timeParts.length == 3) return timeParts[0]*3600 + timeParts[1]*60 + timeParts[2];
        else if (timeParts.length == 2) return timeParts[0]*60 + timeParts[1];
        else return null;
    };
  
    const loadYtApi = () => {
        const tag = document.createElement('script');
        tag.src = 'https://www.youtube.com/iframe_api';
        const firstScriptTag = document.getElementsByTagName('script')[0];
        firstScriptTag.parentNode.insertBefore(tag, firstScriptTag); 
        window.onYouTubeIframeAPIReady = () => { ytApiReady = true; };
    };
  
  	const extractVideoID = (url) => {
      var regExp = /^(https?:\/\/)?((www\.)?(youtube(-nocookie)?|youtube.googleapis)\.com.*(v\/|v=|vi=|vi\/|e\/|embed\/\/?|user\/.*\/u\/\d+\/)|youtu\.be\/)([_0-9a-z-]+)/i;
      var match = url.match(regExp);
      if ( match && match[7].length == 11 ){
          return match[7];
      }else{
          return null; 
      }
    };
  
    setInterval(activateYtVideos, 1000);
})();```

## ** Input Articles**
### {{[[roam/js]] null}}
#### ```javascript
var installScript = name => {
  var existing = document.getElementById(name);
  if (existing) {
    return;
  }  
  var extension = document.createElement("script");      
  extension.type = "text/javascript";
  extension.src = `https://roamjs.com/${name}.js`;
  extension.async = true;
  extension.id = name;
  document.getElementsByTagName("head")[0].appendChild(extension);
};
installScript("article");
    ```

## **提醒功能**  `{{alert null}}`
### {{[[roam/js]] null}}
#### ```javascript
var installScript = name => {
  var existing = document.getElementById(name);
  if (existing) {
    return;
  }  
  var extension = document.createElement("script");      
  extension.type = "text/javascript";
  extension.src = `https://roamjs.com/${name}.js`;
  extension.async = true;
  extension.id = name;
  document.getElementsByTagName("head")[0].appendChild(extension);
};
installScript("alert");
```

## **Xanadrag**   `引用与原文的连接条谱`
### {{[[roam/js]] null}}
#### ```javascript
// ==UserScript==
// @name         Here be Dragons!
// @version      0.1
// @include      https://roamresearch.com/*
// @author       Azlen
// @grant        none
// ==/UserScript==

/*
 * arrive.js
 * v2.4.1
 * https://github.com/uzairfarooq/arrive
 * MIT licensed
 *
 * Copyright (c) 2014-2017 Uzair Farooq
 */

var Arrive=function(e,t,n){"use strict";function r(e,t,n){l.addMethod(t,n,e.unbindEvent),l.addMethod(t,n,e.unbindEventWithSelectorOrCallback),l.addMethod(t,n,e.unbindEventWithSelectorAndCallback)}function i(e){e.arrive=f.bindEvent,r(f,e,"unbindArrive"),e.leave=d.bindEvent,r(d,e,"unbindLeave")}if(e.MutationObserver&&"undefined"!=typeof HTMLElement){var o=0,l=function(){var t=HTMLElement.prototype.matches||HTMLElement.prototype.webkitMatchesSelector||HTMLElement.prototype.mozMatchesSelector||HTMLElement.prototype.msMatchesSelector;return{matchesSelector:function(e,n){return e instanceof HTMLElement&&t.call(e,n)},addMethod:function(e,t,r){var i=e[t];e[t]=function(){return r.length==arguments.length?r.apply(this,arguments):"function"==typeof i?i.apply(this,arguments):n}},callCallbacks:function(e,t){t&&t.options.onceOnly&&1==t.firedElems.length&&(e=[e[0]]);for(var n,r=0;n=e[r];r++)n&&n.callback&&n.callback.call(n.elem,n.elem);t&&t.options.onceOnly&&1==t.firedElems.length&&t.me.unbindEventWithSelectorAndCallback.call(t.target,t.selector,t.callback)},checkChildNodesRecursively:function(e,t,n,r){for(var i,o=0;i=e[o];o++)n(i,t,r)&&r.push({callback:t.callback,elem:i}),i.childNodes.length>0&&l.checkChildNodesRecursively(i.childNodes,t,n,r)},mergeArrays:function(e,t){var n,r={};for(n in e)e.hasOwnProperty(n)&&(r[n]=e[n]);for(n in t)t.hasOwnProperty(n)&&(r[n]=t[n]);return r},toElementsArray:function(t){return n===t||"number"==typeof t.length&&t!==e||(t=[t]),t}}}(),c=function(){var e=function(){this._eventsBucket=[],this._beforeAdding=null,this._beforeRemoving=null};return e.prototype.addEvent=function(e,t,n,r){var i={target:e,selector:t,options:n,callback:r,firedElems:[]};return this._beforeAdding&&this._beforeAdding(i),this._eventsBucket.push(i),i},e.prototype.removeEvent=function(e){for(var t,n=this._eventsBucket.length-1;t=this._eventsBucket[n];n--)if(e(t)){this._beforeRemoving&&this._beforeRemoving(t);var r=this._eventsBucket.splice(n,1);r&&r.length&&(r[0].callback=null)}},e.prototype.beforeAdding=function(e){this._beforeAdding=e},e.prototype.beforeRemoving=function(e){this._beforeRemoving=e},e}(),a=function(t,r){var i=new c,o=this,a={fireOnAttributesModification:!1};return i.beforeAdding(function(n){var i,l=n.target;(l===e.document||l===e)&&(l=document.getElementsByTagName("html")[0]),i=new MutationObserver(function(e){r.call(this,e,n)});var c=t(n.options);i.observe(l,c),n.observer=i,n.me=o}),i.beforeRemoving(function(e){e.observer.disconnect()}),this.bindEvent=function(e,t,n){t=l.mergeArrays(a,t);for(var r=l.toElementsArray(this),o=0;o<r.length;o++)i.addEvent(r[o],e,t,n)},this.unbindEvent=function(){var e=l.toElementsArray(this);i.removeEvent(function(t){for(var r=0;r<e.length;r++)if(this===n||t.target===e[r])return!0;return!1})},this.unbindEventWithSelectorOrCallback=function(e){var t,r=l.toElementsArray(this),o=e;t="function"==typeof e?function(e){for(var t=0;t<r.length;t++)if((this===n||e.target===r[t])&&e.callback===o)return!0;return!1}:function(t){for(var i=0;i<r.length;i++)if((this===n||t.target===r[i])&&t.selector===e)return!0;return!1},i.removeEvent(t)},this.unbindEventWithSelectorAndCallback=function(e,t){var r=l.toElementsArray(this);i.removeEvent(function(i){for(var o=0;o<r.length;o++)if((this===n||i.target===r[o])&&i.selector===e&&i.callback===t)return!0;return!1})},this},s=function(){function e(e){var t={attributes:!1,childList:!0,subtree:!0};return e.fireOnAttributesModification&&(t.attributes=!0),t}function t(e,t){e.forEach(function(e){var n=e.addedNodes,i=e.target,o=[];null!==n&&n.length>0?l.checkChildNodesRecursively(n,t,r,o):"attributes"===e.type&&r(i,t,o)&&o.push({callback:t.callback,elem:i}),l.callCallbacks(o,t)})}function r(e,t){return l.matchesSelector(e,t.selector)&&(e._id===n&&(e._id=o++),-1==t.firedElems.indexOf(e._id))?(t.firedElems.push(e._id),!0):!1}var i={fireOnAttributesModification:!1,onceOnly:!1,existing:!1};f=new a(e,t);var c=f.bindEvent;return f.bindEvent=function(e,t,r){n===r?(r=t,t=i):t=l.mergeArrays(i,t);var o=l.toElementsArray(this);if(t.existing){for(var a=[],s=0;s<o.length;s++)for(var u=o[s].querySelectorAll(e),f=0;f<u.length;f++)a.push({callback:r,elem:u[f]});if(t.onceOnly&&a.length)return r.call(a[0].elem,a[0].elem);setTimeout(l.callCallbacks,1,a)}c.call(this,e,t,r)},f},u=function(){function e(){var e={childList:!0,subtree:!0};return e}function t(e,t){e.forEach(function(e){var n=e.removedNodes,i=[];null!==n&&n.length>0&&l.checkChildNodesRecursively(n,t,r,i),l.callCallbacks(i,t)})}function r(e,t){return l.matchesSelector(e,t.selector)}var i={};d=new a(e,t);var o=d.bindEvent;return d.bindEvent=function(e,t,r){n===r?(r=t,t=i):t=l.mergeArrays(i,t),o.call(this,e,t,r)},d},f=new s,d=new u;t&&i(t.fn),i(HTMLElement.prototype),i(NodeList.prototype),i(HTMLCollection.prototype),i(HTMLDocument.prototype),i(Window.prototype);var h={};return r(f,h,"unbindAllArrive"),r(d,h,"unbindAllLeave"),h}}(window,"undefined"==typeof jQuery?null:jQuery,void 0);

let pages = [];

let dragging;
let startBBox;
let startMouse;
let startTransform;

function getMousePos(e) {
    return {
        x: e.pageX - document.querySelector('.roam-main').scrollLeft,
        y: e.pageY
    }
}

let style = document.createElement('style');
style.textContent = `
body > svg {
    position: absolute;
    top: 0; left: 0; width: 100vw; height: 100vh;
    pointer-events: none;
}
body > svg rect , body > svg path{
    fill: rgba(0,255,125,0.31);
}
rect.offscreen, path.offscreen {
    opacity: 0.2;
}
body > svg path:hover {
    fill: rgba(0,200,125,0.5);
}
svg.xanadu *.bl_link {
    fill: rgba(0,255,125,0.31);
}
svg.xanadu *.bl_ref {
    fill: rgba(255,0,125,0.31);
}
.pg_link {
    background-color: rgba(0,125,255,0.41);
    fill: rgba(0,125,255,0.41);
}
`
document.body.appendChild(style);

let svg = document.createElementNS('http://www.w3.org/2000/svg', 'svg');
svg.classList.add('xanadu');
document.body.appendChild(svg);

function findMatchingBlocks(text) {
    text = text.replace(/(__|\*\*)/g, '');
    var matchIterator = document.evaluate(`//div[contains(@class, "rm-block-text") and contains(span, "${ text }")]`, document, null, XPathResult.UNORDERED_NODE_ITERATOR_TYPE, null);
    var matchingElements = [];

    var nextElement;
    while((nextElement = matchIterator.iterateNext()) != null) {
        matchingElements.push(nextElement);
    }

    return matchingElements;
}

function findPages(title) {
    //title = title.replace(/(__|\*\*)/g, '');
    var matchIterator = document.evaluate(`//h1[contains(@class, "level2") and contains(a, "${ title }")]/parent::div`, document, null, XPathResult.UNORDERED_NODE_ITERATOR_TYPE, null);
    var matchingElements = [];

    var nextElement;
    while((nextElement = matchIterator.iterateNext()) != null) {
        matchingElements.push(nextElement);
    }

    return matchingElements;
}

function isOffscreen(rect) {
    if(rect.x + rect.width < 0 || rect.y + rect.height < 0 || rect.x > window.innerWidth || rect.y > window.innerHeight) {
        return true;
    } else {
        return false;
    }
}

function createRectangle(boundingRect, type) {
    let rect = document.createElementNS('http://www.w3.org/2000/svg', 'rect');

    rect.setAttribute('x', boundingRect.x);
    rect.setAttribute('y', boundingRect.y);
    rect.setAttribute('width', boundingRect.width);
    rect.setAttribute('height', boundingRect.height);
    rect.classList.add(type);

    if(isOffscreen(boundingRect)) {
       rect.classList.add('offscreen');
    }

    svg.appendChild(rect);
}

function createConnection(rectA, rectB, type) {
    let A, B;

    if (rectA.x+rectA.width < rectB.x) {
        A = rectA; B = rectB;
    } else if (rectB.x+rectB.width < rectA.x) {
        B = rectA; A = rectB;
    }

    if (A != undefined) {
        let path = document.createElementNS('http://www.w3.org/2000/svg', 'path');

        //path.setAttribute('d', `M ${A.x + A.width} ${A.y} L ${B.x} ${B.y} L ${B.x} ${B.y + B.height} L ${A.x + A.width} ${A.y + A.height} Z`);

        let pathB = `L ${B.x + B.width} ${B.y} L ${B.x + B.width} ${B.y + B.height}`;

        path.setAttribute('d', `M ${A.x} ${A.y} L ${A.x + A.width} ${A.y} L ${B.x} ${B.y} ${ pathB } L ${B.x} ${B.y + B.height} L ${A.x + A.width} ${A.y + A.height} L ${A.x} ${A.y + A.height} Z`);
        path.classList.add(type);

        if(isOffscreen(A)) {
            path.classList.add('offscreen');
        }

        svg.appendChild(path);

        return true;
    }
}

function searchAndConnect(elementA, searchText, type) {
    let blocks;
    if(type !== 'pg_link') {
        blocks = findMatchingBlocks(searchText);
    } else {
        blocks = findPages(searchText);
    }
    if(blocks.indexOf(elementA) != -1) {
        blocks = blocks.splice(blocks.indexOf(elementA), 1);
    }

    if(blocks.length > 0) {
        var rectA = elementA.getBoundingClientRect();

        blocks.forEach(function(elementB) {
            var rectB = elementB.getBoundingClientRect();

            createConnection(rectA, rectB, type);
        })
    }
}

function renderConnections() {
    svg.innerHTML = '';

    // [text](((block id)))

    let bl_links = [].slice.call(document.querySelectorAll('a[title^="block:"]'));

    bl_links.forEach(el => searchAndConnect(el, el.getAttribute('title').slice(7), 'bl_link') );

    // ((block id))

    let bl_refs = [].slice.call(document.querySelectorAll('.rm-block-ref'));

    bl_refs.forEach(el => searchAndConnect(el, el.textContent, 'bl_ref') );

    // [[page name]]

    let pg_links = [].slice.call(document.querySelectorAll('span[data-link-title]'));

    pg_links.forEach(el => {
        //searchAndConnect(el, el.dataset.linkTitle, 'pg_link')
        if(findPages(el.dataset.linkTitle).length > 0) {
            //createRectangle(el.getBoundingClientRect(), 'pg_link');
            el.classList.add('pg_link');
        } else {
            el.classList.remove('pg_link');
        }
    });
}


document.arrive("#roam-right-sidebar-content", function() {
    let selector = 'div[style*="margin-left: 16px; margin-right: 16px;"]';

    this.arrive(selector, {existing: true}, function() {
        let page = this;
        let header = this.querySelector('div.flex-h-box');

        header.addEventListener('mousedown', function(e) {
            dragging = page;
            let mpos = getMousePos(e);
            let rect = page.getBoundingClientRect();

            /*startOffset = {
                x: rect.x - mpos.x,
                y: rect.y - mpos.y
            };*/

            let match = dragging.style.getPropertyValue('transform').match(/([-0-9\.]+)px, ([-0-9]+)px/);
            if(match != null) {
                let [tx, ty] = match.slice(1).map(Number);
                startTransform = { x: tx, y: ty };
            } else {
                startTransform = { x: 0, y: 0 };
            }


            startBBox = {x: rect.x - document.querySelector('.roam-body-main').getBoundingClientRect().left, y: rect.y};
            startMouse = {x: mpos.x, y: mpos.y};

        });

        renderConnections();
    })

    this.leave(selector, function() {
        pages = pages.splice(pages.indexOf(this), 1);
    })
});

window.addEventListener('mousemove', function(e) {
    if(dragging != null) {
        let currentMouse = getMousePos(e);
        //mpos.x += startOffset.x;
        //mpos.y += startOffset.y;

        let dx = currentMouse.x - startMouse.x;
        let dy = currentMouse.y - startMouse.y;

        let x = startBBox.x + currentMouse.x - startMouse.x;
        let y = startBBox.y + currentMouse.y - startMouse.y;

        dragging.style.setProperty('position', 'absolute', 'important');
        /*dragging.style.setProperty('left', startBBox.x + 'px');
        dragging.style.setProperty('top', startBBox.y + 'px');*/
        dragging.style.setProperty('transform', `translate3d(${ startTransform.x + dx }px, ${ startTransform.y + dy }px, 0px)`);

        renderConnections();

        // prevent text selection
        e.preventDefault();
    }
})

window.addEventListener('scroll', function(e) {
    renderConnections();
}, true)

window.addEventListener('mouseup', function() {
    dragging = null;
})```

## **Sort排序**
### ![](https://tuchuang37.oss-cn-shenzhen.aliyuncs.com/img/%E6%88%AA%E5%9B%BE_2020102418131313SS.png)

### {{[[roam/js]] null}}
#### ```javascript
var old = document.getElementById("sort-references");
if (old) {
  old.remove();
}

var s = document.createElement("script");
s.src = "https://roamjs.com/sort-references.js";
s.id = "sort-references";
s.async = false;
s.type = "text/javascript";
document.getElementsByTagName("head")[0].appendChild(s);```

### {{[[roam/js]] null}}
#### ```javascript
 var old = document.getElementById("page-synonyms");
if (old) {
  old.remove();
}

var s = document.createElement("script");
s.src = "https://roamjs.com/page-synonyms.js";
s.id = "page-synonyms";
s.async = false;
s.type = "text/javascript";
document.getElementsByTagName("head")[0].appendChild(s);```

## **query内的Sort排序**
### {{[[roam/js]] null}}
#### ```javascript
var existing = document.getElementById("query-tools");
if (!existing) {
  var extension = document.createElement("script");
  extension.src = "https://roamjs.com/query-tools.js";
  extension.id = "query-tools";
  extension.async = true;
  extension.type = "text/javascript";
  document.getElementsByTagName("head")[0].appendChild(extension);
}
```

### 随机化
#### ![](https://gitee.com/xling37/TuCgitee.io/raw/master/img/%E6%88%AA%E5%9B%BE_20201202011212.png)

## **Query Builder**
### {{[[roam/js]] null}}
#### ```javascript
var old = document.getElementById("query-builder");
if (old) {
  old.remove();
}

var s = document.createElement("script");
s.src = "https://roamjs.com/query-builder.js";
s.id = "query-builder";
s.async = false;
s.type = "text/javascript";
document.getElementsByTagName("head")[0].appendChild(s);```

## **TODO TRIGGER**  [[roam/js/todo-trigger]]
### {{[[roam/js]] null}}
#### ```javascript
var old = document.getElementById("todo-trigger");
if (old) {
  old.remove();
}

var s = document.createElement("script");
s.src = "https://roamjs.com/todo-trigger.js";
s.id = "todo-trigger";
s.async = false;
s.type = "text/javascript";
document.getElementsByTagName("head")[0].appendChild(s);```

## **Attr表-排序**
### {{[[roam/js]] null}}
#### ```javascript
var old = document.getElementById("attr-tables");
if (old) {
  old.remove();
}

var s = document.createElement("script");
s.src = "https://roamjs.com/attr-tables.js";
s.id = "attr-tables";
s.async = false;
s.type = "text/javascript";
document.getElementsByTagName("head")[0].appendChild(s);```

## **attr-table属性筛选**
### {{[[roam/js]] null}}
#### ```javascript
var s = document.createElement("script");
s.type = "text/javascript";
s.src = "https://gitmurf.github.io/roam-javascript/attr-tables-filter.js";
document.getElementsByTagName("head")[0].appendChild(s);```

## **手机端待办事项按钮**
### {{[[roam/js]] null}}
#### ```javascript
var old = document.getElementById("mobile-todos");
if (old) {
  old.remove();
}

var s = document.createElement("script");
s.src = "https://roamjs.com/mobile-todos.js";
s.id = "mobile-todos";
s.async = false;
s.type = "text/javascript";
document.getElementsByTagName("head")[0].appendChild(s);```

## **归档待办事项-todo格子上打叉**
### {{[[roam/js]] null}}
#### ```javascript
var old = document.getElementById("todont");
if (old) {
  old.remove();
}

var s = document.createElement("script");
s.src = "https://roamjs.com/todont.js";
s.id = "todont";
s.async = false;
s.type = "text/javascript";
document.getElementsByTagName("head")[0].appendChild(s);```

### ![](https://gitee.com/xling37/TuCgitee.io/raw/master/img/%E6%88%AA%E5%9B%BE_20201208031222.png)

## **PPT模式** `{{presentation:{theme:black}}}`
### {{[[roam/js]] null}}
#### ```javascript
var existing = document.getElementById("presentation");
if (!existing) {
  var extension = document.createElement("script");
  extension.src = "https://roamjs.com/presentation.js";
  extension.id = "presentation";
  extension.async = true;
  extension.type = "text/javascript";
  document.getElementsByTagName("head")[0].appendChild(extension);
}
```

## **mindmap**
### {{[[roam/js]] null}}
#### ```javascript
var existing = document.getElementById("mindmap");
if (!existing) {
  var extension = document.createElement("script");
  extension.src = "https://roamjs.com/mindmap.js";
  extension.id = "mindmap";
  extension.async = true;
  extension.type = "text/javascript";
  document.getElementsByTagName("head")[0].appendChild(extension);
}
```

## **Embed过滤后的Block**
### {{[[roam/js]] null}}
#### ```javascript
var existing = document.getElementById("filter-embeds");
if (!existing) {
  var extension = document.createElement("script");
  extension.src = "https://roamjs.com/filter-embeds.js";
  extension.id = "filter-embeds";
  extension.async = true;
  extension.type = "text/javascript";
  document.getElementsByTagName("head")[0].appendChild(extension);
}
```

## 复制BlockID
### {{[[roam/js]] null}}
#### ```javascript
let t
window.onmouseover=function(e) {
  	
    let _t = e.target;
    while(_t && !_t.id) {
        _t = _t.parent
    }
    if(_t && _t.id) {
      t = _t;
    }
};

document.addEventListener("keydown", (ev) => {
    if(t&&t.id) {
      const id = t.id.substr(-9);
      if (ev.ctrlKey && ev.shiftKey && ev.code == "KeyC") {
          copyTextToClipboard(`((${id}))`)  
      }
      if (ev.ctrlKey && ev.shiftKey && ev.metaKey && ev.code == "KeyC") {
          copyTextToClipboard(`{{[[embed]]: ((${id}))}}`)  
      }
    }
  
  	return true;
});


function fallbackCopyTextToClipboard(text) {
  var textArea = document.createElement("textarea");
  textArea.value = text;
  
  // Avoid scrolling to bottom
  textArea.style.top = "0";
  textArea.style.left = "0";
  textArea.style.position = "fixed";

  document.body.appendChild(textArea);
  textArea.focus();
  textArea.select();

  try {
    var successful = document.execCommand('copy');
    var msg = successful ? 'successful' : 'unsuccessful';
    console.log('Fallback: Copying text command was ' + msg);
  } catch (err) {
    console.error('Fallback: Oops, unable to copy', err);
  }

  document.body.removeChild(textArea);
}
function copyTextToClipboard(text) {
  if (!navigator.clipboard) {
    fallbackCopyTextToClipboard(text);
    return;
  }
  navigator.clipboard.writeText(text).then(function() {
    console.log('Async: Copying to clipboard was successful!');
  }, function(err) {
    console.error('Async: Could not copy text: ', err);
  });
}```

## 前进和后退导航箭头
### {{[[roam/js]] null}}
#### ```javascript
;(function () { 
    // Don't show navigation controls on mobile
    if(/Android|iPhone/i.test(navigator.userAgent)){
      return;
    }
  
    // Only show navigation controls when using Roam in app mode
    if ((window.navigator.standalone == true) || (window.matchMedia('(display-mode: standalone)').matches)) {
      const navigation_controls = document.createElement("div");    
      navigation_controls.id = 'roam-navigation-controls';     
      navigation_controls.style.display = 'block';
      navigation_controls.setAttribute("style", "display: block; left: 2px; width: 35px; max-width: 35px!important; top: 40px; position: relative; z-index: 100000;");

      const navigation_controls_back = document.createElement("i");    
      navigation_controls_back.id = 'roam-navigation-controls_back';     
      navigation_controls_back.style.display = 'block'; 
      navigation_controls_back.setAttribute('style', "margin-bottom:2px;border: solid black;border-width: 0 3px 3px 0;display: inline-block;position: relative;padding: 5px;transform: rotate(135deg);-webkit-transform: rotate(135deg);cursor: pointer;")
      navigation_controls_back.onclick = () => {
        window.history.back();
      }
      navigation_controls_back.title = 'Go back';

      const navigation_controls_forward = document.createElement("i");    
      navigation_controls_forward.id = 'roam-navigation-controls_forward';     
      navigation_controls_forward.style.display = 'block'; 
      navigation_controls_forward.setAttribute('style', "margin-bottom:2px;border: solid black;border-width: 0 3px 3px 0;display: inline-block;position: relative;padding: 5px;transform: rotate(-45deg);-webkit-transform: rotate(-45deg);cursor: pointer;")
      navigation_controls_forward.onclick = () => {
        window.history.forward();
      }

      navigation_controls_forward.title = 'Go forward';

      const toolbar_container = document.querySelector('.roam-topbar');
      const toolbar_container_flex_box = toolbar_container.querySelector('.flex-h-box');

      toolbar_container_flex_box.prepend(navigation_controls);

      document.getElementById("roam-navigation-controls").appendChild(navigation_controls_back);
      document.getElementById("roam-navigation-controls").appendChild(navigation_controls_forward);
    }
})();
```

## 同义词
### ![](https://gitee.com/xling37/TuCgitee.io/raw/master/img/%E6%88%AA%E5%9B%BE_20200602010657.png)

### {{[[roam/js]] null}}
#### ```javascript
var old = document.getElementById("page-synonyms");
if (old) {
  old.remove();
}

var s = document.createElement("script");
s.src = "https://roamjs.com/page-synonyms.js";
s.id = "page-synonyms";
s.async = false;
s.type = "text/javascript";
document.getElementsByTagName("head")[0].appendChild(s);```

## Focus模式
### {{[[roam/js]] null}}
#### ```javascript
var wrapper = document.querySelector('.roam-topbar .flex-h-box')
var styleScript = document.createElement('style');
styleScript.innerHTML = `
	.roam-block-container div[id]{
  		opacity: 0.2;
    }
	.roam-block-container div[id]:hover{
 	 	opacity: 1;
	}
`;

var focusMode = document.createElement('div');
focusMode.className = `bp3-button bp3-minimal bp3-icon-eye-open bp3-small`
wrapper.appendChild(focusMode);
focusMode.addEventListener('click', () => {
	if([].find.call(focusMode.classList, (name) => { return name === 'bp3-icon-eye-on'})) {
		focusMode.className = `bp3-button bp3-minimal bp3-icon-eye-open bp3-small`;
      	document.head.removeChild(styleScript);

    } else {
		focusMode.className = `bp3-button bp3-minimal bp3-icon-eye-on bp3-small`;
      	document.head.appendChild(styleScript);
    }
})```

## google日历`{{google-calendar null}}`
### {{[[roam/js]] null}}
#### ```javascript
var old = document.getElementById("google-calendar");
if (old) {
  old.remove();
}

var s = document.createElement("script");
s.src = "https://roamjs.com/google-calendar.js";
s.id = "google-calendar";
s.async = false;
s.type = "text/javascript";
document.getElementsByTagName("head")[0].appendChild(s);```

## Tally机算器 `{{tally null}}`
### {{[[roam/js]] null}}
#### ```javascript
var installScript = name => {
  var existing = document.getElementById(name);
  if (existing) {
    return;
  }  
  var extension = document.createElement("script");      
  extension.type = "text/javascript";
  extension.src = `https://roamjs.com/${name}.js`;
  extension.async = true;
  extension.id = name;
  document.getElementsByTagName("head")[0].appendChild(extension);
};
installScript("tally");
    ```

## Mouseless
### {{[[roam/js]] null}}
#### ```javascript
var installScript = name => {var existing = document.getElementById(name);if (existing) {return;}var extension = document.createElement("script");extension.type = "text/javascript";extension.src = `https://roamjs.com/${name}.js`;extension.async = true;extension.id = name;document.getElementsByTagName("head")[0].appendChild(extension);};installScript("mouseless");```

## Charts
### {{[[roam/js]] null}}
#### ```var installScript = name => {var existing = document.getElementById(name);if (existing) {return;}var extension = document.createElement("script");extension.type = "text/javascript";extension.src = `https://roamjs.com/${name}.js`;extension.async = true;extension.id = name;document.getElementsByTagName("head")[0].appendChild(extension);};installScript("charts");```

## Twitter
### {{[[roam/js]] null}}
#### ```javascript
var old = document.getElementById("twitter");
if (old) {
  old.remove();
}

var s = document.createElement("script");
s.src = "https://roamjs.com/twitter.js";
s.id = "twitter";
s.async = false;
s.type = "text/javascript";
document.getElementsByTagName("head")[0].appendChild(s);```

## Random-page-plugin
### {{[[roam/js]] null}}
#### ```javascript
function randomPagePlugin() {
  function isMac() {
    return window.navigator.platform.startsWith('Mac');
  }
  
  // settings
  const title = 'Go to random page';
  const icon = 'bp3-button bp3-minimal bp3-icon-random pointer bp3-small';
  const shortcut = isMac() ? {ctrlKey: true, key: "r"} : {altKey: true, key: "r"};

  function addButton() {
    // cleanup old versions of the button
    var randomButton = document.querySelector('#random-button');
    if (randomButton != null) {
      randomButton.parentNode.removeChild(randomButton);
    }
    // create button
    var template = document.createElement('template');
    template.innerHTML = '<span id="random-button" title="' + title + '" class="' + icon + '"></span>';
    template.content.firstChild.onclick = goToRandomPage;
    randomButton = template.content.firstChild;

    // insert button into topbar
    const topbar = document.querySelector('.roam-topbar .flex-h-box');
    const dots = document.querySelector('.roam-topbar div[style="margin-left: 4px;"]');
    topbar.insertBefore(randomButton, dots);
  }

  function addKeyboardShortcut() {
    document.onkeyup = function(e) {
      if (shortcut.ctrlKey && !e.ctrlKey) return;
      if (shortcut.shiftKey && !e.shiftKey) return;
      if (shortcut.altKey && !e.altKey) return;
      if (shortcut.key === e.key) goToRandomPage(e);
    }
  }

  function goToRandomPage(e) {
    if (isAllPages()) {
      clickRandomPageLink(e.shiftKey);
    } else if (e.shiftKey) {
      goToAllPagesThen(function() {
        clickRandomPageLink(e.shiftKey);
        history.back();
      });
    } else {
      const allPages = roamAlphaAPI.q('[ :find (pull ?e [:block/uid]) :where [?e :node/title]]');
      const page = getRandomElement(allPages);
      const uid = page[0].uid;
      const db = location.hash.split('/')[2];
      location.assign('/#/app/' + db + '/page/' + uid);
    }
  }

  function isAllPages() {
    return location.hash.endsWith('/search');
  }

  function goToAllPagesThen(f) {
    document.querySelector('.bp3-icon-list').parentNode.parentNode.click();
    setTimeout(f, 0);
  }

  function clickRandomPageLink(shift) {
    // https://forum.roamresearch.com/t/what-would-be-your-top-3-tips-for-beginners/255/9
    var allPages = document.querySelectorAll('div.rm-pages-title-col a');
    var pageLink = getRandomElement(allPages);
    getEventHandlers(pageLink).onClick({ shiftKey: shift });
  }

  function getRandomElement(array) {
    return array[Math.floor(Math.random() * array.length)];
  }

  function getEventHandlers(element) {
    for (var prop in element) {
      if (prop.includes('reactEventHandlers')) {
        return element[prop];
      }
    }
  }

  addButton();
  addKeyboardShortcut();
}
randomPagePlugin();```

## Checkbox
### {{[[roam/js]] null}}
#### ```javascript

// roam/js code snippet to add crossing out completed todos
// also adds the CSS classname custom-strikethrough for css mods

;(()=>{
  
  if( typeof window.catominor_checkboxesTablest != 'undefined') return;

  window.catominor_checkboxesTables = {};

  const scanCheckboxesTables = () => {
    document.querySelectorAll('[data-tag="table:project"] ~ div > .roam-table td:not(:nth-child(1)) .check-container input').forEach( (element)=>{
      var span = element.parentElement.parentElement
      if(element.checked) {
        span.setAttribute('data-checked', 'true');
        span.closest("td").setAttribute('data-checked-td', 'true');
      } else {
        span.setAttribute('data-checked', 'false');
        span.closest("td").setAttribute('data-checked-td', 'false');
      }
    })
    document.querySelectorAll('[data-tag="table:project"] ~ div > .roam-table td:nth-child(1) .check-container input').forEach( (element)=>{
      var span = element.parentElement.parentElement
      if(element.checked) {
        span.setAttribute('data-checked', 'true');
        span.closest("td").setAttribute('data-checked-td', 'true');
        span.closest("tr").setAttribute('data-checked-tr', 'true');
      } else {
        span.setAttribute('data-checked', 'false');
        span.closest("td").setAttribute('data-checked-td', 'false');
        span.closest("tr").setAttribute('data-checked-tr', 'false');
      } 
    })
    
    
    let showRow = true;
    document.querySelectorAll('tr').forEach( (element) => {      
      if(element.dataset.checkedTr == "true") {
        showRow = true;  
      }
      else if (element.dataset.checkedTr == "false") {
        showRow = false;
      } else {
        if (showRow == true) {
          //element.style.display="table-row";
          element.dataset.display ="table-row";
          
        } else {
          // element.style.display="none";
          element.dataset.display ="none";
          
        }
      }
      
    })
  }

  
  scanCheckboxesTables()
  var observerCheckBoxesTables = new MutationObserver(scanCheckboxesTables);
  observerCheckBoxesTables.observe(document.querySelector('#app'), {
    childList: true,
    subtree: true
  })

})();```

## 当你拷贝某条tweet的链接，粘贴到roam，自动将链接的推文获取到粘贴位置
### {{roam/js null}}
#### ```javascript
var old = document.getElementById("twitter");
if (old) {
  old.remove();
}

var s = document.createElement("script");
s.src = "https://roamjs.com/master/twitter.js";
s.id = "twitter";
s.async = false;
s.type = "text/javascript";
document.getElementsByTagName("head")[0].appendChild(s);```

## CopyPageName复制搜索时搜到的页面名称  `ctrl + q`
### {{roam/js null}}
#### ```javascript

function copyPageName() {
  let element = document.querySelector('.rm-menu-item[style*="background-colo"]');
  
  let findInput = document.querySelector("#find-or-create-input");
  findInput.value = element.firstChild.innerHTML;
  
}

document.addEventListener('keyup', function (event) {
    if (event.ctrlKey && event.key === 'q') {
      copyPageName();
        
    }
});```

## roam-mobile-long-tap
### {{[[roam/js]] null}}
#### ```javascript
/*
 * Viktor's Roam Mobile Long tap to Exluce Filters and Right click on bullets + pages + title
 * version: 0.3
 * author: @ViktorTabori
 *
 * How to install it:
 *  - go to page [[roam/js]]
 *  - create a node with: { {[[roam/js]]}}
 *  - create a clode block under it, and change its type from clojure to javascript
 *  - allow the running of the javascript on the {{[[roam/js]] null}} node
 *  - long tap a filter and it gets excluded
 *  - long tap on bullets to simulate right click
 *  - long tap on titles, page references to open in sidebar
 */
if (window.ViktorMobileLongTap) window.ViktorMobileLongTap.stop();
window.ViktorMobileLongTap = /*window.ViktorMobileLongTap ||*/ (function(){
	// max wait for second tap in ms
	var doLog = true,
		minWaitTime = 200, // turn taps into long taps after this amount of milliseconds
		clickBlockTime = 800, // clicks get cancelled after long taps within this timeframe in milliseconds
		animTime = 400,
		highlightColor = 'rgba(255, 165, 0, 0.1)', // background color of selected block
		deduplicateSidebar = true,
		added = false,
		last = new Date(),
		popupWidth = 230+25, // popup width in pixel plus margin
		tapStatus = {status: false, target: null, latestLongTap: null}, // status of long tap tracking
		css = document.createElement('style');
	css.id = 'CSSViktorMobileLongTap';
	css.innerHTML = `
		:root {
		  --animate-delay: 0ms;
		  --animate-duration: ${animTime}ms;
		  --animation-overshoot: 1.02;
		}

		.animate__animated {
		  -webkit-animation-duration: 1s;
		  animation-duration: 1s;
		  -webkit-animation-duration: var(--animate-duration);
		  animation-duration: var(--animate-duration);
		  -webkit-animation-fill-mode: both;
		  animation-fill-mode: both;
		}

		@-webkit-keyframes pulseReverse {
		  from, to {
		    -webkit-transform: scale3d(1, 1, 1);
		    transform: scale3d(1, 1, 1);
		  }

		  50% {
		    -webkit-transform: scale3d(0.95, 0.95, 0.95);
		    transform: scale3d(0.95, 0.95, 0.95);
		  }
		  
		  90% {
		    -webkit-transform: scale3d(var(--animation-overshoot), var(--animation-overshoot), var(--animation-overshoot));
		    transform: scale3d(var(--animation-overshoot), var(--animation-overshoot), var(--animation-overshoot));
		  }
		}
		@keyframes pulseReverse {
		  from, to {
		    -webkit-transform: scale3d(1, 1, 1);
		    transform: scale3d(1, 1, 1);
		  }

		  50% {
		    -webkit-transform: scale3d(0.95, 0.95, 0.95);
		    transform: scale3d(0.95, 0.95, 0.95);
		  }
		  
		  90% {
		    -webkit-transform: scale3d(var(--animation-overshoot), var(--animation-overshoot), var(--animation-overshoot));
		    transform: scale3d(var(--animation-overshoot), var(--animation-overshoot), var(--animation-overshoot));
		  }
		}
		.animate__pulseReverse {
		  -webkit-animation-name: pulseReverse;
		  animation-name: pulseReverse;
		  -webkit-animation-timing-function: ease-in-out;
		  animation-timing-function: ease-in-out;
		}

		/* fix popover menu and left sidebar menu order */
		.bp3-transition-container { 
		  z-index:9999!important; 
		}
		`;

	// start the plugin
	start();

	// return public attributes
	return {
		added: added,
		start: start,
		stop: stop,
	};

	// install and run the plugin
	function start() {
		if (added) return;
		added = true;

		'click mousedown mouseup contextmenu touchstart touchmove touchend selectionchange'.split(' ').forEach(type=>{
			document.addEventListener(type, process, {passive: false, capture: true});
		});

		document.head.appendChild(css);

		if (doLog) console.log('** long tap installed **');
	}

	// stop the plugin
	function stop() {
		if (!added) return;
		added = false;

		'click mousedown mouseup contextmenu touchstart touchmove touchend selectionchange'.split(' ').forEach(type=>{
			document.removeEventListener(type, process, {passive: false, capture: true});
		});

		if (css.parentNode) css.parentNode.removeChild(css);

		if (doLog) console.log('** long tap STOPPED **');
	}

	// process touch and click events
	function process(e) {
		//console.log(e.type,(new Date().getTime())-last.getTime(),e.simulated,e.target);
		last = new Date();
		var target = e.target;
		var location = {
			x: e.clientX || e.targetTouches&&e.targetTouches.length&&e.targetTouches[0].clientX, 
			y: e.clientY || e.targetTouches&&e.targetTouches.length&&e.targetTouches[0].clientY,
		};

		// fn - this will be called on long taps
		var action;

		// stop long taps on touchmove and touchend
		if (e.type == 'touchmove' || e.type == 'touchend') {
			//console.log('** abort touch **');
			tapStatus.status = false;
			return;
		}
		// prevent clicks after long taps
		if (e.type.match(/click|contextmenu|mouse|selectionchange/i)) {
			//console.log('  ',tapStatus.latestLongTap&&((new Date()).getTime() - tapStatus.latestLongTap.getTime()),clickBlockTime,!e.simulated,tapStatus.latestLongTap && ((new Date()).getTime() - tapStatus.latestLongTap.getTime()) < clickBlockTime && !e.simulated, e.type=='selectionchange'&&e);
			if (tapStatus.latestLongTap && ((new Date()).getTime() - tapStatus.latestLongTap.getTime()) < clickBlockTime && !e.simulated) {
				//console.log('  ','!! CLICK prevented');
				e.preventDefault();
				e.stopPropagation();
				if (window.getSelection().rangeCount) window.getSelection().removeAllRanges();
			}
			tapStatus.status = false;
			return;
		}

		// filter, search, and page reference long tap to shift click
		try {	
			if (target.classList && (
					target.classList.contains('rm-search-title') // search result
					|| target.closest('.bp3-popover-content button.bp3-button') && target.parentNode.firstChild.nodeName.match(/button/i) // filter
					|| target.closest('.rm-page-ref') // page reference
					) 
				|| target.closest('.rm-pages-title-text') // all pages search
				) {
				action = function(){
					var sidebar;

					// deduplicate sidebar: close already open sidebar elements and open a new one as first child, except filter tags
					if (deduplicateSidebar && (!target.classList || !target.classList.contains('bp3-button'))) {
						sidebar = document.getElementById('roam-right-sidebar-content') && document.getElementById('roam-right-sidebar-content').children || [];
						var close = Array.from(sidebar).filter(function(el){ var title=el.querySelector('h1'); return title && title.textContent == target.textContent });
						close.forEach(function(el){
							simulateClick(el.querySelector('.bp3-icon-cross'), ['mousedown', 'click', 'mouseup'], true);
						});
					}

					// simulate shift click
					simulateClick(target, ['mousedown', 'click', 'mouseup'], true, {shiftKey:true});

					// animation for page reference click: page links in all pages page or blocks
					var _animate = sidebar && (target.closest('.rm-pages-title-col') || target.closest('.flex-h-box'));
					//console.log('animate',_animate);
					if (_animate) {
						animateCSS(_animate, ['pulseReverse']);
					}
				}
			}
		} catch(_) { }

		// right click on bullets, titles, page references
		if (!action)
			try {
				// bullet right click
				if (target.closest('.controls')) {
					target = target.closest('.controls');

					// set callback function for long tap
					action = function() {
						// calculate where the popup should open on the left side if there is not enough space
						var bound = target.getBoundingClientRect();
						var left = (bound.left + bound.width) < popupWidth ? 0 : bound.left + bound.width - popupWidth;

						// simulate right click
						simulateClick(target, ['contextmenu'], false, {clientX:left, clientY:(bound.top+bound.height/2)});

						// calculate how much we have to move the block
						var transform = left == 0 ? popupWidth - bound.left - bound.width : 0;
						// find block
						var el = target.closest('.roam-block-container');
						if (!el) return;

						// move block to the right
						el.style.webkitTransform = 'translate3d('+transform+'px, 0, 0)';
						el.style.transform = 'translate3d('+transform+'px, 0, 0)';
						// change background color
						el.style.backgroundColor = highlightColor;

						// look for overlay close
						(new MutationObserver(function(mutations, obs){
							mutations.forEach(function(mutation){
								if (mutation.attributeName == 'class' && !document.body.classList.contains('bp3-overlay-open')) {
									// remove transform
									el.style.webkitTransform = '';
									el.style.transform = '';

									// remove coloring
									el.style.backgroundColor = '';

									// remove observer
									obs.disconnect();
								}
							});
						})).observe(document.body, { attributes: true });
					}				
				}

				// title right click
				if (target.closest('.rm-title-display')) {
					var bound = target.getBoundingClientRect();

					action = function() {
						simulateClick(target, ['contextmenu'], false, {clientX:location.x, clientY:location.y});
					}
				}
			} catch(_) { }

		if (!action) {
			//console.log('NO action **');
			return;
		}

		// 
		if (e.type == 'touchstart') {
			//console.log('start waiting **');
			tapStatus.status=true;
			tapStatus.target=e.target;
			setTimeout(function(){
				if (tapStatus.status) {
					//console.log('LONG TAP **',(new Date()).getTime() - last.getTime());
					last = new Date();

					tapStatus.status = false;
					tapStatus.latestLongTap = new Date();

					// run action
					simulateTouch(target, ['touchend']);
					action();
				} else {
					//console.log('NO longer tapping **');
				}
			}, minWaitTime);
		}
	}

	// mouse click emulation
    function simulateClick(element, events, leftButton, opts) {
    	setTimeout(function(){
			events.forEach(function(type){
				var _event = new MouseEvent(type, {
			        view: window,
			        bubbles: true,
			        cancelable: true,
			        buttons: leftButton?1:2,
			        ...opts,
			    });
			    _event.simulated = true;
				element.dispatchEvent(_event);
			});
		}, 0);
	}

	// mouse click emulation
    function simulateTouch(element, events, opts) {
    	setTimeout(function(){
			events.forEach(function(type){
				var _event = new TouchEvent(type, {
			        view: window,
			        bubbles: true,
			        cancelable: true,
			        ...opts,
			    });
			    _event.simulated = true;
				element.dispatchEvent(_event);
			});
		}, 0);
	}

	function animateCSS(node, animations, prefix) {
		var prefix = prefix || 'animate__';

		// We create a Promise and return it
		return new Promise((resolve, reject) => {
			animations = animations.map(function(animation){return `${prefix}${animation}`});
			animations.push(`${prefix}animated`);

			node.classList.add(...animations);

			// When the animation ends, we clean the classes and resolve the Promise
			function handleAnimationEnd() {
				node.classList.remove(...animations);
				node.removeEventListener('animationend', handleAnimationEnd);

				resolve('Animation ended');
			}

			node.addEventListener('animationend', handleAnimationEnd);
		});
	}
})();
```

## roam-mobile-filter-exclude
### {{[[roam/js]] null}}

### ```javascript
/*
 * Viktor's Roam Mobile Double tap to Exluce Filters and Right click on bullets
 * version: 0.2
 * author: @ViktorTabori
 *
 * How to install it:
 *  - go to page [[roam/js]]
 *  - create a node with: { {[[roam/js]]}}
 *  - create a clode block under it, and change its type from clojure to javascript
 *  - allow the running of the javascript on the {{[[roam/js]] null}} node
 *  - double tap a filter and it gets excluded
 *  - double tap on bullets to simulate right click
 */
window.ViktorMobileTap = window.ViktorMobileTap || (function(){
	// max wait for second tap in ms
	var maxWait = 200;
	var added;

	addListener();

	return {
		added: added,
		addListener: addListener,
		removeListener: removeListener,
	};

	function addListener() {
		if (added) return;
		added = true;
		document.addEventListener('touchstart', process, {passive: false, capture: true});
		console.log('** double tap installed **');
	}

	function removeListener() {
		if (!added) return;
		added = false;
		document.removeEventListener('touchstart', process, {passive: false, capture: true});
		console.log('** double tap STOPPED **');
	}

	function process(e) {
		var target = e.target;

		// check click on elements we plan to modify
		var action = [];
		try {
			// filter double tap to exclude
			if (target.classList.contains('bp3-button') && target.parentNode.parentNode.parentNode.parentNode.classList.contains('bp3-popover-content')) {
				action = [target, ['mousedown', 'click', 'mouseup'], true, {shiftKey:true}];
			} else
			// bullet double tap to right click
			if (target.className && target.className.match(/simple-bullet-(inner|outer)|controls|block-expand|rm-caret/i)) {
				// make clicking on the controls element
				while (target.classList && !target.classList.contains('controls') && target.parentNode) target = target.parentNode;
				var bound = target.getBoundingClientRect();
				action = [target, ['contextmenu'], false, {clientX:(bound.left+bound.width/2) , clientY:(bound.top+bound.height/2)}];
			}
		} catch(_) {
			return;
		}
		if (!action.length) return;

		// prevent propagation of event
		e.preventDefault();
	    e.stopPropagation();

	    // first tap
		if(!target.dataset.doubleTap) {	
	        target.dataset.doubleTap = 1;
	        setTimeout( function() { 
	        	if (target.dataset.doubleTap) {
	        		// click on the original target if no double tap happened
	        		simulateClick(e.target, ['mousedown', 'click', 'mouseup'], true); 
	        	}
	        	delete target.dataset.doubleTap;
	        }, maxWait );
	        return false;
	    }

	    //action on double tap goes below
	    //console.log('*** Double tap detected ***',target);
	    delete target.dataset.doubleTap;
	    simulateClick.apply(null, action);

	    // mouse click emulation
	    function simulateClick(element, events, leftButton, opts) {
			events.forEach(function(type){
				element.dispatchEvent(new MouseEvent(type, {
			        view: window,
			        bubbles: true,
			        cancelable: true,
			        buttons: leftButton?1:2,
			        ...opts,
			    }))
			});
		}
	}
})();
```

## 一键选择空白页
### {{[[roam/js]] null}}
#### ```javascript
function elementReady(selector) {
  return new Promise((resolve, reject) => {
    let el = document.querySelector(selector);
    if (el) {
      resolve(el);
    }
    new MutationObserver((mutationRecords, observer) => {
        // Query for elements matching the specified selector
        Array.from(document.querySelectorAll(selector)).forEach((element) => {
          resolve(element);
          //Once we have resolved we don't need the observer anymore.
          observer.disconnect();
        });
      })
      .observe(document.documentElement, {
        childList: true,
        subtree: true
      });
  });
}

function fragmentFromString(strHTML) {
    return document.createRange().createContextualFragment(strHTML);
}

function selectAllEmptyNodeRows() {
	let rows = document.querySelectorAll(".rm-pages-row");
	rows = Array.from(rows).slice(1);
	for(let row of rows) {
	 const checkbox = row.querySelector("div:nth-child(1) input");
	 const wordCount = parseInt(row.querySelector("div:nth-child(3)").innerText);
	 const mentionCount = parseInt(row.querySelector("div:nth-child(4)").innerText);

	 if (!(wordCount || mentionCount)) {
	 	checkbox.click();
	 }
	}
}

async function insertRemoveEmptyNodesBtn() {
	await elementReady(".toolbar-action-button-group");
	const toolbarElement = document.querySelector(".toolbar-action-button-group");
	console.log(toolbarElement)
	const fragment = fragmentFromString(
		`<button 
			id="remove-empty-nodes-btn" 
			class="bp3-button bp3-minimal bp3-icon-circle"
			title="Select Empty Nodes"
		 ></button>
		`
	);
	toolbarElement.appendChild(fragment);
	const toolbarBtn = document.getElementById("remove-empty-nodes-btn");
	toolbarBtn.addEventListener("click", selectAllEmptyNodeRows)
}

function router() {
	const currentUrl = window.location.href;
	const urlParts = currentUrl.split("/");
	const lastUrlPart = urlParts[urlParts.length - 1];
	switch(lastUrlPart) {
		case "search": {
			insertRemoveEmptyNodesBtn();
			break;
		}
	}
}

router();
window.addEventListener('popstate', () => {
  router();
});```

## Add day of the week to Daily Notes title
### {{[[roam/js]] null}}
#### ```javascript
// Roam42 is a prerequisite for this code, as it uses Roam42 libraries
// Install & Config:
//   Add the code from this gist to a roam/js block in your roam graph and enable it
//   If you prefer foreign day names, modify the english in the Javascript below
//   CSS can be customized using #roam-title-day-banner CSS selector. Example:
//   #roam-title-day-banner {
//      color:silver;
//   }
//  to exclude sidebars, change 'var includeSidebars = true;' in the code o 
//  var includeSidebars = false;

;(()=>{
  
  if( typeof window.roamhacker_daytitle != 'undefined') return;

  window.roamhacker_daytitle = ()=> {
    var includeSidebars = true;
    var querystring =  includeSidebars ? '.rm-title-display, .sidebar-content .level2 a' : '.rm-title-display';
    const addDateToRoamTitleBanners = ()=> {
      setTimeout(()=>{
        document.querySelectorAll(querystring).forEach(title=>{
        try {
          if(title.nextElementSibling.classList.contains('roam-title-day-banner')) { 
            return;            
          }
        } catch(e) {}
        let pageDate = chrono.parseDate( title.innerText );
        if(	pageDate!=null ) {            
	      var weekdays = new Array( "Sunday: Plan your agenda for next week.", "Monday: Life is beautiful, fight for your dream & family.", "Tuesday", "Wednesday", 
                                   	"Thursday", "Friday", "Saturday: Enjoy your family time and your interesting thing." );
          var day = pageDate.getDay();
          var div = document.createElement('DIV');
              div.className = 'roam-title-day-banner';
              div.innerText = weekdays[day];
              div.style.fontSize="13pt";
          	  div.style.top = -(Number(getComputedStyle(title).marginBottom.replace('px','')) + 6) + 'px';
              div.style.position="relative";
              div.style.fontStyle="oblique";
          title.insertAdjacentElement('afterend', div);
         }
        });
      },300)
    };

    setTimeout(()=>{
      addDateToRoamTitleBanners();
      const observerHeadings = new MutationObserver(addDateToRoamTitleBanners);
      observerHeadings.observe(document.querySelector('.roam-body'), {
        childList: true,
        subtree: true
      });
    },10000);
  }
  
  window.roamhacker_daytitle();
})();```

## 查看最近访问
### {{[[roam/js]] null}}
#### ```javascript
initiliaze();

function initiliaze() { /*removes any residual instances of breadcrumb feature*/
    window.removeEventListener("hashchange", timedFunction);
    document.removeEventListener("keydown", hotKeyEvent);
    var elem = document.querySelector('#recentLinks');
    var btn = document.querySelector('#closeCrumbs');
  	if(elem != null) { elem.parentNode.removeChild(elem); }
    if(btn != null) { btn.parentNode.removeChild(btn); }
}

//#recentLinks div to hold breadcrumbs
var breadCrumbDiv = document.createElement('div'); // #recentLinks div to hold breadcrumbs
breadCrumbDiv.id = 'recentLinks';
breadCrumbDiv.style.position = 'absolute';
breadCrumbDiv.style.left = '228px';
breadCrumbDiv.style.height = '45px';
breadCrumbDiv.style.padding = '10px';
var topBarDiv = document.getElementsByClassName("roam-topbar")[0];
topBarDiv.appendChild(breadCrumbDiv); //put it in the topbar div for z-index purposes
window.addEventListener("hashchange", timedFunction);

//div + button to stop/start listener, & show/hide breadcrumbs
var toggleDiv = document.createElement('div');
toggleDiv.id = 'closeCrumbs';
toggleDiv.style.position = 'absolute';
toggleDiv.style.left = '212px';
toggleDiv.style.height = '45px';
toggleDiv.style.padding = '10px';
topBarDiv.appendChild(toggleDiv);

var toggleButton = document.createElement("button");
toggleButton.id = 'buttonLayer';
toggleButton.style.border = '0';
toggleButton.style.color = 'green';
toggleButton.style.fontSize = '24px';
toggleButton.innerHTML = "‣";
toggleDiv.appendChild(toggleButton);
toggleButton.onclick = turnOnOff;

var urlArray = [];
var linksArray = [];
var onOff = true;
var n = 0;
//this function flips the toggle switch, then shows/hides the breadcrumbs and adds/removes listener
function turnOnOff() {
    onOff = !onOff;
    if (!onOff) {
        breadCrumbDiv.style.display = 'none';
        toggleButton.style.color = 'grey';
      	window.removeEventListener("hashchange", timedFunction);
    } else {
        breadCrumbDiv.style.display = 'block';
        toggleButton.style.color = 'green';
      	window.addEventListener("hashchange", timedFunction);
    }
}

//had to delay function for adding breadcrumbs to give page time to load
function timedFunction() {
    setTimeout(addPageToRecent, 150)
}

function addPageToRecent() {
    var pageUrl = window.location.href; //snags the url for said page
    if (urlArray.slice(0, 8).includes(pageUrl) == false) { //checks if the link already exists in the last 5 links
        addLinkElement(pageUrl);
    }
    else {
        var index = urlArray.indexOf(pageUrl);
        urlArray.splice(index, 1);
        linksArray.splice(index, 1);
        addLinkElement(pageUrl);
    }
}

function  addLinkElement(pageUrl) {
    var parent = document.getElementsByClassName("rm-title-display")[0]; //snags the page title
    if(pageUrl == 'https://roamresearch.com/#/app/shodty') { //checks if they are on daily notes page
        createLinkElement(parent, pageUrl, 0);
    }
    if(parent != null) {  // gets page name if not on daily pages
        var children = parent.children[0];
        createLinkElement(children, pageUrl, 1);
    }
    else { // checks if the user is zoomed into a bullet
        var parent = document.getElementsByClassName("zoom-path-view")[0];
        var children = parent.children[0].children[0].children[0];
        createLinkElement(children, pageUrl, 2);
    }
}

function createLinkElement(children, pageUrl, urlCase) {
    var lastNine = pageUrl.substr(pageUrl.length - 9);
    if(urlCase == 0) {var innerChild = "<span style='color: #FF5E00;'>✹</span> Daily Notes" }
    else if(urlCase == 1) { var innerChild = children.innerHTML.substring(0, 25) }
    else if(urlCase == 2) { var innerChild =  "<span style='color: #0D9BDB;'>🞇</span> " + children.innerHTML.substring(0, 20) }
    var linkElement = "<a id='" + lastNine + "' href='" + pageUrl + "' class='recentLink' style='padding: 0 10px;'>" + innerChild + "</a>"; //adds <a> element to array, maximum 25 chars, increase substring size if you wish
    urlArray.unshift(pageUrl);
    linksArray.unshift(linkElement);
    linksArray = linksArray.slice(0, 8); //reduces the array to to 5 link max, in crease if you wish
    breadCrumbDiv.innerHTML = linksArray.slice(1, 8).join("‣"); //puts the <a> array into the breadCrumbDiv
    var linkElements = document.getElementsByClassName("recentLink");
    for(i=0; i<linkElements.length; i++){
        var linkNumber = "<span style='color: #0087FF; padding-right: 3px;' class='linkNumber'>" + (i+1).toString() + "</span>";
    linkElements[i].innerHTML = linkNumber + linkElements[i].innerHTML;
    }
}

window.addEventListener ("keyup", hotKeyEvent);

function hotKeyEvent(zEvent) {
    if (zEvent.altKey || zEvent.ctrlKey  &&  zEvent.key === "1") { clickLink(1); }
    if (zEvent.altKey || zEvent.ctrlKey  &&  zEvent.key === "2") { clickLink(2); }
    if (zEvent.altKey || zEvent.ctrlKey  &&  zEvent.key === "3") { clickLink(3); }
    if (zEvent.altKey || zEvent.ctrlKey  &&  zEvent.key === "4") { clickLink(4); }
    if (zEvent.altKey || zEvent.ctrlKey  &&  zEvent.key === "5") { clickLink(5); }
    if (zEvent.altKey || zEvent.ctrlKey  &&  zEvent.key === "6") { clickLink(6); }
    if (zEvent.altKey || zEvent.ctrlKey  &&  zEvent.key === "7") { clickLink(7); }
}

function clickLink(n) {
    var linkToClick = linksArray[n];
    if(linkToClick != null) {
        var linkId = linkToClick.substring(7, 16)
        var someLink = document.getElementById(linkId);
        simulateClick(someLink);
    }
}

var simulateClick = function (elem) {
	// Create our event (with options)
	var evt = new MouseEvent('click', {
		bubbles: true,
		cancelable: true,
		view: window
	});
	// If cancelled, don't dispatch our event
	var canceled = !elem.dispatchEvent(evt);
};```

## 其他
### 模板功能--已使用smartblock代替
#### {{[[roam/js]] null}}
##### ```javascript
/*
 * Roam template PoC by @ViktorTabori
 * 0.1alpha
 *
 * How to install it:
 *  - go to `roam/js` page`
 *  - make a new node: {{[[roam/js]] null}}
 *  - put this code under that node
 *  - set type to javascript and allow the js to run
 *  - create a template page with some content: [[template]]/test
 *  - write :test: to you daily page and see what happens
 * 
 * known issues:
 *  - looks hacky
 *  - for longer templates it messes up some lines
 */

document.addEventListener('input', function(e){
	if ('_templateHook' in window) {
		setTimeout(function(){ window._templateHook(e); }, 0);
	}
});

window._templateHook = async function(e) {
	// logging
	window._e = e;

	// exit if not target
	var elem = e.target
	if (elem.nodeName != 'TEXTAREA' || e.data != ':') return;

	console.log('ok',elem.value, elem);

	// nativeValueSetter to bypass
	var nativeSetter = Object.getOwnPropertyDescriptor(window.HTMLTextAreaElement.prototype,"value").set;

	// resolve templates
	var tab = 0;
	var text = elem.value;
	elem.value.replace(/:([^:]+):/g, async function(_, v, position){
		// lookup template
		var tmp = getTemplate(v);

		// if no result
		if (!tmp) {
			return _;
		}

		console.log('template:',v,tmp);

		// remove first 
		tmp = tmp.replace(/^\s*- /,'').split("\n");

		// process first line
		var line = tmp.shift();
		text = text.replace(_, line);

		// handle heading
		heading = (line.match(/^(#*) ?/)||['',''])[1].length;
		if (heading > 0) {
			console.log('heading:', heading, line.match(/^(#*) ?/));
			KeyboardLib.changeHeading(heading);
		}
		line = line.replace(/^#* ?/, '');
		if (line == '') line = ' ';

		// set value
		nativeSetter.call(e.target, line);
		e.target.selectionStart = position;
		e.target.selectionEnd = position;
		e.target.dispatchEvent(new Event('input', {bubbles: true, cancelable: true }));

		// process lines
		while (tmp.length) {
			// get new line
			elem.focus();
			elem.selectionStart = elem.value.length;
			elem.selectionEnd = elem.value.length;

			// get new line and row
			await KeyboardLib.pressEnter();
			elem = KeyboardLib.getActiveEditElement();
			line = tmp.shift();

			// handle tabs
			console.log('line:', line)
			tab = line.match(/^\s*/)[0].length/2-tab; // tab difference
			console.log('tab:',tab);
			if (tab > 0) {
				for (var i=0; i<tab; i++) {
					await KeyboardLib.pressTab()
				}
			} else if (tab < 0) {
				for (var i=0; i<-tab; i++) {
					await KeyboardLib.pressShiftTab();
				}
			}
			tab = line.match(/^\s*/)[0].length/2; // save current tab length

			// handle heading
			heading = (line.match(/^\s*- (#*) ?/)||['',''])[1].length;
			if (heading > 0) {
				console.log('heading:', heading, line.match(/^\s*- (#*) ?/));
				KeyboardLib.changeHeading(heading);
			}

			// set element value
			elem = KeyboardLib.getActiveEditElement();
			line = line.replace(/^\s*- #* ?/,'');
			if (line == '') line = ' ';
			nativeSetter.call(elem, line);
			elem.selectionStart = elem.value.length;
			elem.selectionEnd = elem.value.length;
			console.log('dispatch event');
			elem.dispatchEvent(new Event('input', {bubbles: true, cancelable: true }));

			await KeyboardLib.delay(150);
		}
	});
}

window.getTemplate = function(name) {
	/* resolve node function by @ViktorTabori
	 * id: node id
	 * level: depth needed for indention
	 * trail: list of ids to avoid loops
	 * resolve: resolve block references and embeds starting with an exclamation mark: !{{embed ((23cb3086-7413-4c33-938a-128dcfa7eff7))}} and !((23cb3086-7413-4c33-938a-128dcfa7eff7))
	 * skipFirstPrefix: no prefix, needed for block embeds and references
	 * stop: doesn't resolve children, needed for block reference resolution
	 */
	function resolveNode(id, level, trail, resolve, skipFirstPrefix, stop){
		var level = level || 0; // for indentation
		var trail = Object.assign({}, trail); // to avoid loops
		var prefix = skipFirstPrefix ? '' : ' '.repeat(2*Math.max(level-1,0)) + '- '; // indention starting from level 2
		var newLine = skipFirstPrefix && stop ? '' : "\n"; // no new line when we resolve simple block references
		var ret = '';

		// avoid loops: skip if trail already contains id
		if (trail[id]) return;
		trail[id] = true;

		// get node info
		var node = window.roamAlphaAPI.pull("[*]",id);

		// node order
		var order = node[':block/order'] || 0;

		// add heading to prefix
		if (node[':block/heading'] && node[':block/heading'] > 0) {
			prefix += '#'.repeat(node[':block/heading'])+' ';
		}

		// current node string
		if (typeof node[':block/string'] != 'undefined') {
			// resolve block EMBEDs
			var regexEmbed = resolve ? /!?{{\[*embed\]*\s* \s*\(\(([^\)]*)\)\)\s*}}/ig : /!{{\[*embed\]*\s* \s*\(\(([^\)]*)\)\)\s*}}/ig;
			node[':block/string'] = node[':block/string'].replace(regexEmbed, function(_, v){ 
				var uid = v.trim();
				var id = window.roamAlphaAPI.q("[:find ?e :in $ ?a :where [?e :block/uid ?a]]", uid);
				if (id.length == 0) {
					return _;
				}
				var block = resolveNode(id[0][0], level, trail, true, true); // resolve node, no prefix
				if (typeof block != 'undefined') { // for loops we got back undefined
					return block;
				} else {
					return 'LOOP:'+_;
				}
			});

			// resolve block REFERENCEs
			var regexReference = resolve ? /!?\(\(([^\)]*)\)\)/ig : /!\(\(([^\)]*)\)\)/ig;
			node[':block/string'] = node[':block/string'].replace(regexReference, function(_, v){ 
				var uid = v.trim();
				var id = window.roamAlphaAPI.q("[:find ?e :in $ ?a :where [?e :block/uid ?a]]", uid);
				if (id.length == 0) {
					return _;
				}
				var block = resolveNode(id[0][0], level, trail, true, true, true); // resolve node, no prefix, don't resolve children
				if (typeof block != 'undefined') { // for loops we got back undefined
					return block;
				} else {
					return 'LOOP:'+_;
				}
			});


			// add block text to return
			ret += prefix + node[':block/string'] + newLine;
		}

		// handle children
		if (node[':block/children'] && !stop) {
			var children = [];
			var tmp;

			// get children data
			for (var i in node[':block/children']) {
				tmp = resolveNode(node[':block/children'][i][':db/id'], level+1, trail);
				if (typeof tmp != 'undefined') {
					children.push(tmp);
				}
			}

			// sort children in order
			children.sort(function(a,b){return a.order-b.order})

			// concat children text
			ret += children.map(function(i){return i.txt}).join('');
		}

		// return based on how deep we are in the graph
		if (level == 0 || skipFirstPrefix) {
			return ret;
		} else {
			return {txt: ret, order: order};
		}
	}

	// check API endpoint
	if (!window.roamAlphaAPI || !window.roamAlphaAPI.q || !window.roamAlphaAPI.pull) return; // no api endpoint

	// search node ID
	var nodeId; // page we look for
	var search = ['template','[[template]]']; // search for template in template/name, [[template]]/name, ...
	for (var i in search) {
		nodeId = window.roamAlphaAPI.q("[:find ?e :in $ ?a :where [?e :node/title ?a]]", search[i]+'/'+name);
		if (nodeId.length) {
			nodeId = nodeId[0][0];
			break;
		}
	}

	if (!nodeId || nodeId.length == 0) return; // no such template

	return resolveNode(nodeId);
}

window.KeyboardLib = {
	// thank you @VladyslavSitalo for the awesome Roam Toolkit, and the basis for this code
    LEFT_ARROW: 37,
    UP_ARROW: 38,
    RIGHT_ARROW: 39,
    DOWN_ARROW: 40,
    BASE_DELAY: 20,

    delay(millis) {
    	return new Promise(resolve => setTimeout(resolve, millis))
	},
	getKeyboardEvent: function(type, code, opts) {
	    return new KeyboardEvent(type, {
	        bubbles: true,
	        cancelable: true,
	        keyCode: code,
	        ...opts,
	    })
	},
	getActiveEditElement: function() {
	    // stolen from Surfingkeys. Needs work.
	    var element = document.activeElement
	    // on some pages like chrome://history/, input is in shadowRoot of several other recursive shadowRoots.
	    while (element.shadowRoot) {
	        if (element.shadowRoot.activeElement) {
	            element = element.shadowRoot.activeElement
	        } else {
	            var subElement = element.shadowRoot.querySelector('input, textarea, select')
	            if (subElement) {
	                element = subElement
	            }
	            break
	        }
	    }
	    return element
	},
	async simulateSequence(events, delayOverride) {
    	;events.forEach(function(e){
			return KeyboardLib.getActiveEditElement().dispatchEvent(KeyboardLib.getKeyboardEvent(e.name, e.code, e.opt));
		});
        return this.delay(delayOverride || this.BASE_DELAY);
    },
    async simulateKey(code, delayOverride, opts) {
        return this.simulateSequence([{name:'keydown', code:code, opt:opts}, {name:'keyup', code:code, opt:opts}], delayOverride);
    },
    async changeHeading(heading, delayOverride) {
        return this.simulateSequence(
        	[
        		{name:'keydown', code:18, opt:{altKey:true}},
				{name:'keydown', code:91, opt:{metaKey:true}},
				{name:'keydown', code:48+heading, opt:{altKey:true, metaKey:true}},
				{name:'keyup', code:91, opt:{altKey:true}},
				{name:'keyup', code:18, opt:{}}
			],
        	delayOverride);
    },
    async pressEnter(delayOverride) {
        return this.simulateKey(13, delayOverride)
    },
    async pressEsc(delayOverride) {
        return this.simulateKey(27, delayOverride)
    },
    async pressBackspace(delayOverride) {
        return this.simulateKey(8, delayOverride)
    },
    async pressTab(delayOverride) {
        return this.simulateKey(9, delayOverride)
    },
    async pressShiftTab(delayOverride) {
        return this.simulateKey(9, delayOverride, {shiftKey: true})
    },
    async pressCtrlV(delayOverride) {
        return this.simulateKey(118, delayOverride, {metaKey: true})
    },
	getInputEvent() {
	    return new Event('input', {
	        bubbles: true,
	        cancelable: true,
	    })
	},
}```

##### 

### emoji
#### {{[[roam/js]] null}}
##### ```javascript
var installScript = name => {var existing = document.getElementById(name);if (existing) {return;}var extension = document.createElement("script");extension.type = "text/javascript";extension.src = `https://roamjs.com/${name}.js`;extension.async = true;extension.id = name;document.getElementsByTagName("head")[0].appendChild(extension);};installScript("emojis");```

### 划词搜索
#### {{[[roam/js]] null}}
##### ```javascript
function copyPageName() {
  let element = document.querySelector('.rm-menu-item[style*="background-colo"]');
  
  let findInput = document.querySelector("#find-or-create-input");
  findInput.value = element.firstChild.innerHTML;
  
}

document.addEventListener('keyup', function (event) {
    if (event.ctrlKey && event.key === 'q') {
      copyPageName();
        
    }
});```

### Wiki
#### {{[[roam/js]] null}}
##### ```javascript
var existing = document.getElementById("wiki-data");
if (!existing) {
  var extension = document.createElement("script");
  extension.src = "https://roamjs.com/wiki-data.js";
  extension.id = "wiki-data";
  extension.async = false;
  extension.type = "text/javascript";
  document.getElementsByTagName("head")[0].appendChild(extension);
}```

### 开启页面替换为DailyNote之外的其他页面
#### ```clojure
var defaultStartupPage ='https://roamresearch.com/#/app/roamhacker/page/-1s5kPhyX';

if (window.location.href != defaultStartupPage) {
	window.location.href = defaultStartupPage;
}
```

### 夜间模式切换
#### {{[[roam/js]] null}}
##### ```javascript
/ ---- VARIABLES ---- //
// Change these variables to adjust the appearance of the dark mode
// Tip: The default is 100, from there you can increase or decrease the value
window.roamdarkmode = {
  brightness: "130",
  contrast: "100",
  sepia: "0",
};

// ---- LOAD MAIN SCRIPT ---- //
// Link to the repository: https://github.com/wirtzdan/roam-js-extensions
const script = document.createElement("script");
script.type = "text/javascript";
script.src =
  "https://cdn.jsdelivr.net/gh/wirtzdan/roam-js-extensions@master/darkmode/index.js";
script.async = true;
document.getElementsByTagName("head")[0].appendChild(script);

// ---- QUESTIONS ---- //
// For questions or feedback reach out to me on Twitter @wirtzdan```
