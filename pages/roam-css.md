---
title: roam/css
---

## ^^全局^^
### **主题** 
#### 背景颜色
##### ```clojure
body {
background: linear-gradient(to right,#FE7FBFAD, #FFffff, #9580FFAD); / cover fixed;/* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
background: -webkit-linear-gradient(to right,#ffffff);
}
.roam-topbar {
  background: linear-gradient(to right,#FE7FBFAD, #FFffff, #9580FFAD); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
}
```

##### ```clojure
.roam-body .roam-app .roam-sidebar-container {
background: linear-gradient(to right,#FE7FBFAD, #FFffff); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
background: -webkit-linear-gradient(to right,#ffffff);
}
#right-sidebar {
background: linear-gradient(to right, #FFffff, #9580FFAD); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
background: -webkit-linear-gradient(to right,#ffffff);
}```

#### 极简主题
##### ```clojure
 @import url('https://rcvd.github.io/roam_mnml/site.css');```

#### 可滚动的侧边栏
##### 宽度
###### ```common lisp
:root {
  /**--roamer-sb-card-width: 447px;
      --roamer-sb-card-width: 590px;
  **/
    --roamer-sb-card-width: 590px;
}
```

###### ```common lisp
.roam-center {
  flex-basis: 45% !important; /* 主编辑器宽度 */
}```

##### Main Code
###### ```common lisp
/**
 use variables to control colors, size.
 delete the part below comment to remove any behaviour
**/
:root {
    /** update colors for dark themes here 
         #d8e1e8
         #778da9
         #ffffff
         #f2f4f8
  */
    --roamer-sb-bg: #d8e1e8;
    --roamer-sb-card-bg: #d8e1e8;
    /* leave blank for no prefix */
    --roamer-sb-card-page-prefix: " "; 

}

.roam-center {
    /* sidebar-to-content-ratio */
    flex-basis: 50% !important;
}

#right-sidebar > div {
    background-color: var(--roamer-sb-bg);
}
/* sidebar layout */
#right-sidebar #roam-right-sidebar-content {
    overflow: auto !important;
    white-space: normal;
    display: flex;
    align-content: flex-start;
    flex-direction: row;
    height: 100%
}

#right-sidebar #roam-right-sidebar-content > div {
    min-width: var(--roamer-sb-card-width);
    background-color: var(--roamer-sb-card-bg);
    border: 1px solid var(--roamer-sb-card-border) !important;
    /* card layout */
    display: flex;
    flex-direction: column;
    padding: 12px;
    border-radius: 4px;
    align-self: flex-start;
    margin-right: 0px !important;
    height: 100% !important;
}

#right-sidebar #roam-right-sidebar-content > div > div:nth-child(2) {
    /* adds scrollbar to card content */
    overflow: auto;
    padding: 0 8px 8px 8px !important;
}

/* sticky */
#right-sidebar #roam-right-sidebar-content > div {
    position: sticky;
    left: 16px
}

/* page numbers */
#right-sidebar #roam-right-sidebar-content {
    counter-reset: page;
}
#right-sidebar #roam-right-sidebar-content > div > div:nth-child(1):before {
    counter-increment: page;
    content: var(--roamer-sb-card-page-prefix) counter(page);
    padding: 0px 4px;
    display: flex;
    align-items: center;
    z-index: 1;
}

/** brings card to top on focus */
#right-sidebar #roam-right-sidebar-content > div:focus-within {
    z-index: 100;
}```

#### 卡片式主题
##### ```common lisp
@import url('https://cdn.jsdelivr.net/gh/JimmyLv/styled-roam@master/card.min.css');```

#### candy主题
##### ```clojure
@import url('https://cdn.jsdelivr.net/gh/JimmyLv/Roam-Research-Themes@patch-1/Candy.css');```

#### RoamR
##### ```clojure
/*
    Designed to work best with the Operator Mono font
*/



body {
    -webkit-font-smoothing: antialiased;
    font-family: "Operator Mono", Menlo, Monaco, 'Courier New', monospace;
}

body, .roam-topbar {
    background: #00162B
}

*[style*="background-color: rgb(213, 218, 223)"] {
    background-color: rgba(0, 22, 43, 1) !important;
}

/* BODY COLOR */

.rm-pages-title-text,
.roam-body .roam-app h1,
.roam-body .roam-app,
.rm-reference-container > div > div > strong,
.bp3-menu .rm-search-title {
    color: #98daf2;
}

.rm-reference-main strong,
.rm-reference-container > div > div > strong {
    color: #98daf2 !important;
}

/* FONTS */

body, .level2, .level3, .level4, .level5, .level6, div, textarea, .roam-log-page.roam-log-preview h1.level2 {
   font-family: "Operator Mono", Menlo, Monaco, 'Courier New', monospace;
}
.level2, .level3, .level4, .level5, .level6 {
    font-weight: 500;
}

h1,
h2,
h3,
h4,
h5,
h6 {
    font-weight: 500;
}
.roam-body .roam-app h1 textarea {
    font-weight: 500;
}


.roam-body .roam-app h1 {
    font-size: 28px;
}

b,
strong {
    font-weight: 600;
}

div {
    font-size: 14px;
}

div,
textarea {
    font-weight: 400;
}

.roam-body .roam-app h1, .roam-body .roam-app h2, .roam-body .roam-app h3, .roam-body .roam-app h4, .roam-body .roam-app h5, .roam-body .roam-app h6 {
    color: #ffc76a;
}


/* LINKS AND TAGS */

.rm-page-ref-brackets {
    color: #ffc76a;
    opacity: 0.4;
}

.rm-page-ref-link-color {
    font-weight: 500;
}
.rm-page-ref-link-color, a, a:hover, .rm-page-ref {
    color: #ffc76a;
}
a:hover {
    text-decoration-color: #ffc76a;
    text-underline-position: under;
}

.rm-page-ref {
    font-style: italic;
}

.rm-block-ref {
    font-size: 1em;
    color: #8d9fb9;
    font-style: italic;
    border-color: rgba(141, 156, 176, .2);
    transition: border-color 0.26s ease;
}
.rm-block-ref:hover {
    background: none;
    cursor: pointer;
    border-color: rgba(141, 156, 176, .5);
}

.rm-page-ref-tag {
    background: #ffecd9;
    box-shadow: inset 0 0 0 1px rgba(0, 0, 0, 0.06);
    padding: 3px;
    color: #000911;
    font-weight: 500;
    display: inline-block;
    padding: 0 3px;
    border-radius: 2px;
}

.rm-page-ref-tag:hover {
    text-decoration: none;
    color: #ffecd9;
    background: none;
    box-shadow: inset 0 0 0 1px #ffecd9;
}

/* HIHGLIGHTED BLOCK SELECT */
.block-highlight-blue {
    background-color: #000911;
}


/* SIDEBAR */

.roam-body .roam-app .roam-sidebar-container {
    background-color: #000911;
    border-right: 1px rgba(255, 255, 255, .06) solid;
}


.block-border-left {
    border-left: 1px solid rgba(141, 156, 176, .2);
}

.starred-pages-wrapper > div:first-of-type {
    background-color: rgba(255, 255, 255, .06) !important;
}

.starred-pages a div:before {
    content: '★ ';
}
.roam-body .roam-app .roam-sidebar-container .roam-sidebar-content .starred-pages-wrapper .starred-pages .page {
    color: #ffc76a;
    /* opacity: 0.4;*/
    letter-spacing: -0.002em;
    font-weight: 400;
    transition: all 0.16s ease;
}
.roam-body .roam-app .roam-sidebar-container .roam-sidebar-content .starred-pages-wrapper .starred-pages .page:hover {
    background: none;
    opacity: 1;
}
.starred-pages-wrapper .flex-h-box span {
    color: white;
    font-weight: 500;
    font-size: 13px;
    letter-spacing: 0.02em;
    /* opacity: 0.4; */
}


/* RIGHT SIDEBAR */


#right-sidebar > div {
    background-color: #000911;
    border-left: 1px rgba(255, 255, 255, .06) solid;
}



/* REFERENCE BOXES*/

.rm-reference-item {
    margin-top: 8px;
    border-radius: 6px;
    border: 1px solid rgba(255, 255, 255, .06);
    margin-right: 8px;
    flex: 1 1 100%;
    word-break: break-word;
    background-color: #000911;
    padding: 8px;
}

/* DAILY LOG */

.roam-log-page, .roam-log-container .roam-log-preview, .roam-log-container .roam-log-page {
    border-color: rgba(255, 255, 255, .06);
}

/* SEARCH AND TOOLTIPS */

.roam-body .roam-app .roam-sidebar-container .roam-sidebar-content .top-row:hover {
    background: #000408;
}

.bp3-input {
    box-shadow: 0 0 0 0 rgba(19, 124, 189, 0), 0 0 0 0 rgba(19, 124, 189, 0), inset 0 0 0 1px rgba(16, 22, 26, 0.15), inset 0 0px 0px rgba(16, 22, 26, 0.2);
}
.bp3-input:focus,
.bp3-input.bp3-active {
    box-shadow: 0 0 0 1px #137cbd, 0 0 0 3px rgba(19, 124, 189, 0.3), inset 0 1px 0px rgba(16, 22, 26, 0.2);
}

.bp3-popover .bp3-popover-content, .bp3-menu, .bp3-elevation-3 {
    background: #000408 !important;
}

.rm-find-or-create-wrapper .rm-menu-item {
    background: #000408 !important;
}
.rm-find-or-create-wrapper .rm-menu-item:hover, .bp3-elevation-3 .dont-unfocus-block:hover {
    background: #000 !important;
    color: white !important;
}

.bp3-menu .rm-search-title:hover {
    color: white !important;
}

/* SEARCH */

.bp3-input {
    background-color: #000911;
}

.bp3-input:focus {
    box-shadow: 0 0 0 2px #137cbd;
    color: white;
}

/* MORE MENU */

.bp3-popover .bp3-popover-arrow-fill {
    fill: #000408;
}
.bp3-menu {
    color: white;
}

/* ALL PAGES TABLE */

.rm-pages-title-text strong {
    font-weight: 600;
}
.rm-all-pages .table .rm-pages-row.rm-pages-row-header {
    background: #00162B;
    border-radius: 0;
}
.rm-all-pages .table .rm-pages-row .rm-pages-col {
    align-self: center;
}
.bp3-text-small span {
    font-size: 14px;
}
.rm-all-pages .table .rm-pages-row.rm-pages-row-header .rm-pages-title-col span,
.rm-all-pages .table .rm-pages-row.rm-pages-row-header .rm-pages-col span {
    font-size: 12px;
    font-weight: 500;
}
.rm-clickable-pill,
.rm-clickable-pill.level1-pill {
    background-color: #ffc76a;
    opacity: 1;
    color: #00162B;
}
.checkmark {
    background: #fff;
}
.check-container input:checked ~ .checkmark {
    background: #33bdea;
}
.check-container input:checked ~ .checkmark:after {
    border-color: #fff;
}
.rm-all-pages .table .rm-pages-row {
    border-color: rgba(255,255,255,0.16);
}


.rm-level2 {
    font-size: 1.5em;
}
.rm-level3 {
    color: #939aae;
    font-weight: 400;
    font-size: 1.3em;
}


/* USER MENU */


.roam-body .roam-app .roam-sidebar-container .rm-graph-dropdown {
    box-shadow: none;
}
.bp3-menu-item:hover, .roam-body .roam-app .roam-sidebar-container .rm-graph-dropdown .setting, .roam-body .roam-app .roam-sidebar-container .rm-graph-dropdown .setting:hover {
    background: #00162B;
}
.roam-sidebar-container .rm-db-title-container .rm-db-title, .roam-body .roam-app .roam-sidebar-container .rm-graph-dropdown a {
    color: white;
}


/* END */



.rm-query {
    border: 0.5px solid #e4e9ec;
    border-radius: 5px;
}

.title-children-text {
    font-size: 14px;
}

.rm-query .rm-query-title {
    background-color: #f7f8f8;
    padding: 0.8em;
    color: #d1dbe2;
    font-size: 80%;
}


.rm-reference-main.rm-query-content {
    padding: 0.8em;
}

.rm-reference-main .rm-reference-item .rm-block-text {
    font-size: 90%;
}

.roam-log-page.roam-log-preview h1.level2 + div {
    font-size: 13px;
    position: relative;
    top: 4px;
}

.rm-reference-main .rm-reference-item .controls {
    margin-left: -1em;
}

.rm-ref-page-view {
    padding: 0.4em 0.2em;
}

.roam-body .roam-app .roam-sidebar-container .roam-sidebar-content .starred-pages-wrapper .starred-pages .page {
    padding: 4px 6px;
}


div.roam-sidebar-container.noselect > div > div {
    font-size: 14px;
    letter-spacing: 0.03em;
}
.bp3-icon-caret-down::before {
    content: "⌄";
    position: relative;
    top: -4px;
    opacity: 0.6;
}

#block-input {
    background: white;
}

.roam-body #block-input > span > div {
    padding: 6px 24px;
    background: white;
}

span.bp3-icon-small.bp3-icon-star {
    display: none;
    visibility: hidden;
}

.controls .simple-bullet-outer .simple-bullet-inner {
    background-color: #cccfd6;
}
.kanban-board {
    background-color: #fff;
}
.kanban-card {
    background-color: white;
    margin: 8px;
    box-shadow: 0px 1px 2px #9EB3C0;
    padding: 10px;
    border-radius: 2px;
    line-height: 1.3em;
}
.kanban-title {
    text-align: center;
    font-weight: bold;
    padding-top: 6px;
}
.kanban-column {
    background-color: #E4EDF2;
    margin: 0px 4px 0px 4px;
    padding: 4px;
    min-width: 200px;
    border-radius: 3px;
}




.intercom-app,
.intercom-launcher-frame,
#intercom-container {
    display: none;
}



.roam-body .roam-app .roam-sidebar-container .roam-sidebar-content .log-button .icon {
    display: none;
}
.roam-body .roam-app .roam-sidebar-container .roam-sidebar-content .log-button {
    font-weight: 600;
    font-size: 13px;
    color: white;
    opacity: 0.4;
    transition: all 0.16s ease;
    padding: 8px 27px;
}
.roam-body .roam-app .roam-sidebar-container .roam-sidebar-content .log-button div {
    font-size: 13px;
    font-weight: 600;
}
.roam-body .roam-app .roam-sidebar-container .roam-sidebar-content .log-button:hover {
    background: none;
    color: white;
    opacity: 1;
}
.roam-sidebar-container .rm-db-title-container .rm-db-title {
    font-size: 14px;
}

.roam-sidebar-content .top-row {
    margin-bottom: 1.6em;
}

#buffer.tall {
    height: calc(100vh - 50px);
}
.check-container {
    padding-right: 4px;
}
.content span.rm-page-ref {
    padding: 4px 1px 1px;
    /* required for fixing azo */
}
.center-proj {
    text-align: center;
}

/* sw修改 */
.bp3-button:not([class*="bp3-intent-"]) {
    color: #57b890;
}```

#### Alzen
##### ```clojure
@import url('https://azlen.github.io/roam-themes/zenith.css');

/* FIXING resizable interface */

/* fix: collapsed sidebar windows by @_robertkirk */
.window-headers:only-child {
  text-orientation: mixed;
  writing-mode: vertical-lr;
}

/* left sidebar fix */
.roam-sidebar-container {
  padding-left: 45px;
}

@media only screen and (max-width: 600px) {
  .roam-sidebar-container {
    padding-left: 0;
  }
}


/* fix resizing */
.roam-body .roam-app .roam-main {
  overflow-x:hidden;
  flex-direction: row !important;
  max-width: var(--page-width) !important;
}

@media only screen and (max-width: 600px) {
  .roam-body .roam-app .roam-main {
    flex: 0 0 auto!important;
  }
  
  .roam-body .roam-app .roam-body-main {
    flex: 0 0 auto!important;
  }
}

/* main panel size fix */
.roam-body .roam-app .roam-body-main {
  flex: 0 0 100%!important;
  padding-left: 55px;
}

.roam-body .roam-app .roam-body-main > [style*="padding-right"] {
  max-width: 100%!important;
  padding-left:unset!important;
  padding-right:unset!important;
}

.rm-block-text {
  max-width: 100%!important;
}

/* make the main panel scroll */
.roam-app > .flex-h-box {
  overflow-x: scroll;
}

.roam-article {
  max-width: 100%;!important;
  overflow-x: hidden;
}

/* right sidebar fix */
#right-sidebar {
  flex: 0 0 auto!important;
}

#right-sidebar .rm-resize-handle {
  left:-4px!important; /* in the original code this has set to -4 which is invalid */
}

#roam-right-sidebar-content {
  flex: 0 0 auto!important;
  overflow: scroll;
}

#roam-right-sidebar-content .sidebar-content > * {
  max-width: 100%;
  overflow-x: hidden;
  padding-top: 45px;
}

/* right sidebar header fixes */
#roam-right-sidebar-content .window-headers {
  margin-left: 5px!important;
  flex-direction: row !important;
  align-items: center!important;
  position: relative!important;
}

#roam-right-sidebar-content .window-headers .bp3-icon-cross {
  order: 1!important;
  margin-right: 10px;
}

#roam-right-sidebar-content .window-headers > :nth-child(1) {
 order: 2;
}

#roam-right-sidebar-content .window-headers > :nth-child(2) {
 order: 3;
}

#roam-right-sidebar-content .window-headers button.bp3-small {
  color: var(--text-color);
  order: 4;
}

#roam-right-sidebar-content .window-headers > [style*="0px"] {
 order: 5;
}

#roam-right-sidebar-content .sidebar-content > * > * {
  padding-right: 10px!important;
}

/* sidebar title editing */
.rm-sidebar-outline .rm-title-editing-display {
	display: inline-block;
}
.rm-sidebar-outline .rm-title-editing-display textarea {
	margin-left: 0!important;
}

/* visualize the right sidebar resize-handle */
.rm-resize-handle:hover, .rm-resize-handle:focus {
    background-color: #66666640;
}
```
###### ```clojure
/* FIXING resizable interface */

/* fix: collapsed sidebar windows by @_robertkirk */
.window-headers:only-child {
  text-orientation: mixed;
  writing-mode: vertical-lr;
}

/* left sidebar fix */
.roam-sidebar-container {
  padding-left: 45px;
}

@media only screen and (max-width: 600px) {
  .roam-sidebar-container {
    padding-left: 0;
  }
}


/* fix resizing */
.roam-body .roam-app .roam-main {
  overflow-x:hidden;
  flex-direction: row !important;
  max-width: var(--page-width) !important;
}

@media only screen and (max-width: 600px) {
  .roam-body .roam-app .roam-main {
    flex: 0 0 auto!important;
  }
  
  .roam-body .roam-app .roam-body-main {
    flex: 0 0 auto!important;
  }
}

/* main panel size fix */
.roam-body .roam-app .roam-body-main {
  flex: 0 0 100%!important;
  padding-left: 55px;
}

.roam-body .roam-app .roam-body-main > [style*="padding-right"] {
  max-width: 100%!important;
  padding-left:unset!important;
  padding-right:unset!important;
}

.rm-block-text {
  max-width: 100%!important;
}

/* make the main panel scroll */
.roam-app > .flex-h-box {
  overflow-x: scroll;
}

.roam-article {
  max-width: 100%;!important;
  overflow-x: hidden;
}

/* right sidebar fix */
#right-sidebar {
  flex: 0 0 auto!important;
}

#right-sidebar .rm-resize-handle {
  left:-4px!important; /* in the original code this has set to -4 which is invalid */
}

#roam-right-sidebar-content {
  flex: 0 0 auto!important;
  overflow: scroll;
}

#roam-right-sidebar-content .sidebar-content > * {
  max-width: 100%;
  overflow-x: hidden;
  padding-top: 45px;
}

/* right sidebar header fixes */
#roam-right-sidebar-content .window-headers {
  margin-left: 5px!important;
  flex-direction: row !important;
  align-items: center!important;
  position: relative!important;
}

#roam-right-sidebar-content .window-headers .bp3-icon-cross {
  order: 1!important;
  margin-right: 10px;
}

#roam-right-sidebar-content .window-headers > :nth-child(1) {
 order: 2;
}

#roam-right-sidebar-content .window-headers > :nth-child(2) {
 order: 3;
}

#roam-right-sidebar-content .window-headers button.bp3-small {
  color: var(--text-color);
  order: 4;
}

#roam-right-sidebar-content .window-headers > [style*="0px"] {
 order: 5;
}

#roam-right-sidebar-content .sidebar-content > * > * {
  padding-right: 10px!important;
}

/* sidebar title editing */
.rm-sidebar-outline .rm-title-editing-display {
	display: inline-block;
}
.rm-sidebar-outline .rm-title-editing-display textarea {
	margin-left: 0!important;
}

/* visualize the right sidebar resize-handle */
.rm-resize-handle:hover, .rm-resize-handle:focus {
    background-color: #66666640;
}```

#### 护眼黄色
##### ```clojure
@import url（' https://calrobertlee.github.io/roam-themes/lux.css '）;```

#### LV
##### ```clojure
@import url('https://cdn.jsdelivr.net/combine/gh/JimmyLv/styled-roam/main.css,gh/JimmyLv/styled-roam/sidebar.css,gh/JimmyLv/styled-roam/tags.css,gh/JimmyLv/styled-roam/refs.css,gh/JimmyLv/styled-roam/misc.css');
:root {
  --article-width: 640px;
}```

##### ```clojure
/* -------------------------- */
/*       RIGHT SIDEBAR        */
/* -------------------------- */

#right-sidebar {
  display: inline-block !important;
  vertical-align: top;
  overflow-y: scroll;
  height: 100%;
  background-color: transparent !important;
  border: none !important;
  /* flex-direction: row !important; */
  padding-right: 20px;
  margin-top: 50px;
  padding-bottom: 50px;
  /* max-height: 100vh; */
  /* overflow-y: scroll; */
}
/* hide icon to close sidebar */
#right-sidebar > .flex-h-box {
  display: none;
}

/* spacing and scrolling */
#roam-right-sidebar-content > * {
  margin: 0px 0px 0 20px !important;
  overflow-y: auto !important;
  max-height: 100vh;
  padding: 0 0px 20px 0px;

  /* pesky bottom border/outline in chrome won't go away! */
  /* this does not fix it */
  border: none !important;
  outline: none !important;
}

#roam-right-sidebar-content {
  /* visibility: visible; */
  display: flex;
  flex-direction: column;
  align-items: flex-start; /* allow pages to have their own height */
  justify-content: flex-end;
}

.roam-center > div:first-child {
  padding: 0 !important;
}
.roam-body-main > * {
  display: inline-block;
}

#roam-right-sidebar-content > * {
  display: block !important;
  max-width: var(--article-width);
  position: relative !important;
}

#roam-right-sidebar-content > * > .flex-h-box {
  display: flex !important;
  padding: 15px 10px !important;
}
#roam-right-sidebar-content > * > div {
  background: var(--page-color);
}
#roam-right-sidebar-content > * > div:first-child {
  border-radius: 10px 10px 0px 0px;
}
#roam-right-sidebar-content > * > div:first-child:last-child {
  border-radius: 10px;
}
#roam-right-sidebar-content > * > div:last-child:not(:first-child) {
  border-radius: 0px 0px 10px 10px;
  padding-bottom: 50px !important;
  width:var(--article-width);
}
#roam-right-sidebar-content > div > div:not(.flex-h-box) {
  padding: 0px 50px 0px 40px;
}
#roam-right-sidebar-content > div > .flex-h-box > .bp3-button, #roam-right-sidebar-content .flex-h-box > .bp3-popover-wrapper {
  margin: auto !important;
  width: 20px !important;
  text-align: center;
}
#roam-right-sidebar-content > div > .flex-h-box > .bp3-button:first-child, #roam-right-sidebar-content .flex-h-box > .bp3-button:last-child {
  display: block;
}

#roam-right-sidebar-content > div .bp3-icon-plus ~ .bp3-button, #roam-right-sidebar-content > div .bp3-icon-plus ~ .bp3-popover-wrapper {
  display: none;
}

/* position minus button */
#roam-right-sidebar-content > div .bp3-icon-minus, #roam-right-sidebar-content > div .bp3-icon-plus {
  position: absolute;
  top: 20px;
  left: 20px;
}
/* position filter button */
#roam-right-sidebar-content > div .bp3-icon-minus ~ .bp3-popover-wrapper {
  position: absolute;
  top: 20px;
  left: 50px;
}
/* position references button */
#roam-right-sidebar-content > div .bp3-icon-minus ~ button.bp3-button {
  position: absolute;
  top: 20px;
  left: 80px;
}
/* position close button */
#roam-right-sidebar-content > div .bp3-icon-minus ~ .bp3-button.bp3-icon-cross {
  position: absolute;
  top: 20px;
  right: 20px;
}

#roam-right-sidebar-content > div .bp3-icon-minus + * {
  margin: 45px 20px 5px 50px !important;
}

#roam-right-sidebar-content > div .bp3-icon-plus ~ h1 {
  margin-left: 50px !important;
}
#roam-right-sidebar-content > div .bp3-icon-plus ~ .bp3-button:last-child {margin-left: 10px !important;}
#roam-right-sidebar-content > div .bp3-icon-plus, #roam-right-sidebar-content > div .bp3-icon-plus ~ * {
  display: block;
  flex: none !important;
}
#roam-right-sidebar-content > div .bp3-icon-plus + * {
  white-space: nowrap;
  writing-mode: horizontal-tb;
  min-width: 0;
}
#roam-right-sidebar-content > div .bp3-icon-plus + div {
  padding: 5px 50px;
}


.roam-topbar .bp3-icon-star::before {
  color: rgb(var(--color-primary)) !important;
  color: rgb(var(--color-secondary)) !important;
}
/* fix positioning problems with menu icon */
.roam-topbar *[class*="icon-menu"]::before {
  position: absolute !important;
  top: 4px !important;
  left: 4px !important;
}
.roam-topbar .bp3-icon-menu-open::before {
  content: ""; /* prevent menu icon from changing on hover */
}```

### **字体大小**
#### ```css
.roam-body {
    font-size: 14.8px;
   
    font-family: PingFangSC-Regular, sans-serif !important;
}


```

### **Tags**  
#### **Tags样式**
##### #[[Literature Notes]][[Test]]    {{模式1 null}}
###### **Literature Notes**
####### ```css
/*Literature Notes*/
span.rm-page-ref[data-tag="Literature Notes"] {
background: #fff;
	background-size: 100%;
    color: #000;
    padding: 2px 5px 2px 5px;
    font-size: 13px;
    line-height: 1em;
    font-weight: 500;
    border-radius: 5px 5px 5px 5px;
   border-style: solid;
  border-color: #215F0040;
  border-width: thin;
    position:relative;
    
  box-shadow: 0px 1px 3px -1px #000000, 
            0px -1px 5px  #DFDFDF;
}
span.rm-page-ref[data-tag="Literature Notes"] + span[data-link-title] {
     background: #B7989128 !important;
     color: #F3F7F2 !important;
     padding: 3px 5px 3px 5px;
     font-size: 13px;
     line-height: 1em;
     font-weight: 400;
     border-radius: 0px 5px 5px 0px;
     margin-left: -5px;
}













































































```

###### **TR**
####### ```css
/*TR*/
span.rm-page-ref[data-tag="TR"] {
background: #778da9;
	background-size: 100%;
    color: #000;
    padding: 2px 5px 2px 5px;
    font-size: 13px;
    line-height: 1em;
    font-weight: 500;
    border-radius: 5px 5px 5px 5px;
   border-style: solid;
  border-color: #215F0040;
  border-width: thin;
    position:relative;
    
  box-shadow: 0px 1px 3px -1px #000000, 
            0px -1px 5px  #DFDFDF;
}
span.rm-page-ref[data-tag="TR"] + span[data-link-title] {
     background: #B7989128 !important;
     color: #F3F7F2 !important;
     padding: 3px 5px 3px 5px;
  font-size: 13px;
     line-height: 1em;
     font-weight: 400;
     border-radius: 0px 5px 5px 0px;
     margin-left: -5px;
}```

###### **Example&Data**
####### ```css
/*Example&Data*/
span.rm-page-ref[data-tag="Example&Data"] {
background: #fff;
  background-size: 100%;
    color: #000;
    padding: 2px 5px 2px 5px;
    font-size: 13px;
    line-height: 1em;
    font-weight: 500;
    border-radius: 5px 5px 5px 5px;
   border-style: solid;
  border-color: #215F0040;
  border-width: thin;
    position:relative;
    
  box-shadow: 0px 1px 3px -1px #000000, 
            0px -1px 5px  #DFDFDF;
}
span.rm-page-ref[data-tag="Example&Data"] + span[data-link-title] {
     background: #B7989128 !important;
     color: #F3F7F2 !important;
     padding: 3px 5px 3px 5px;
     font-size: 13px;
     line-height: 1em;
     font-weight: 400;
     border-radius: 0px 5px 5px 0px;
     margin-left: -5px;
}```

###### **Question**
####### ```css
/*Question*/
span.rm-page-ref[data-tag="Question"] {
background: #DFDFDF;
	background-size: 100%;
    color: #000;
    padding: 2px 5px 2px 5px;
    font-size: 13px;
    line-height: 1em;
    font-weight: 500;
    border-radius: 5px 5px 5px 5px;
   border-style: solid;
  border-color: #215F0040;
  border-width: thin;
    position:relative;
    
  box-shadow: 0px 1px 3px -1px #000000, 
            0px -1px 5px  #DFDFDF;
}
span.rm-page-ref[data-tag="Question"] + span[data-link-title] {
     background: #B7989128 !important;
     color: #F3F7F2 !important;
     padding: 3px 5px 3px 5px;
     font-size: 13px;
     line-height: 1em;
     font-weight: 400;
     border-radius: 0px 5px 5px 0px;
     margin-left: -5px;
}```

###### **Relevant Notes**
####### ```css
/*Relevant Notes*/
span.rm-page-ref[data-tag="Relevant Notes"] {
background: #fff;
	background-size: 100%;
    color: #000;
    padding: 2px 5px 2px 5px;
    font-size: 13px;
    line-height: 1em;
    font-weight: 500;
    border-radius: 5px 5px 5px 5px;
   border-style: solid;
  border-color: #215F0040;
  border-width: thin;
    position:relative;
    
  box-shadow: 0px 1px 3px -1px #000000, 
            0px -1px 5px  #DFDFDF;
}
span.rm-page-ref[data-tag="Relevant Notes"] + span[data-link-title] {
     background: #B7989128 !important;
     color: #F3F7F2 !important;
     padding: 3px 5px 3px 5px;
     font-size: 13px;
     line-height: 1em;
     font-weight: 400;
     border-radius: 0px 5px 5px 0px;
     margin-left: -5px;
}```

###### **PTM**
####### ```css
/*PTM*/
span.rm-page-ref[data-tag="PTM"] {
background: #fff;
	background-size: 100%;
    color: #000;
    padding: 2px 5px 2px 5px;
    font-size: 13px;
    line-height: 1em;
    font-weight: 500;
    border-radius: 5px 5px 5px 5px;
   border-style: solid;
  border-color: #215F0040;
  border-width: thin;
    position:relative;
    
  box-shadow: 0px 1px 3px -1px #000000, 
            0px -1px 5px  #DFDFDF;
}
```

###### **Fleeting Notes**
####### ```css
/*Fleeting Notes*/
span.rm-page-ref[data-tag="Fleeting Notes"] {
  background: #fff;
	background-size: 100%;
 background-color:#fff !important;
    color: #000;
    padding: 2px 5px 2px 5px;
    font-size: 13px;
    line-height: 1em;
    font-weight: 500;
    border-radius: 5px 5px 5px 5px;
   border-style: solid;
  border-color: #215F0040;
  border-width: thin;
    position:relative;
    
  box-shadow: 0px 1px 3px -1px #000000, 
            0px -1px 5px  #DFDFDF;
}```

###### **Reference Notes**
####### ```css
/*Reference Notes*/
span.rm-page-ref[data-tag="Reference Notes"] {
background: #fff;
	background-size: 100%;
 background-color:#fff !important;
    color: #000;
    padding: 2px 5px 2px 5px;
    font-size: 13px;
    line-height: 1em;
    font-weight: 500;
    border-radius: 5px 5px 5px 5px;
   border-style: solid;
  border-color: #215F0040;
  border-width: thin;
    position:relative;
    
  box-shadow: 0px 1px 3px -1px #000000, 
            0px -1px 5px  #DFDFDF;
}```

###### **Matter**
####### ```css
/*Matter*/
span.rm-page-ref[data-tag="Matter"] {
background: #fff;
	background-size: 100%;
    background-color:#778da9 !important;
    color: #000;
    padding: 2px 5px 2px 5px;
    font-size: 13px;
    line-height: 1em;
    font-weight: 500;
    border-radius: 5px 5px 5px 5px;
   border-style: solid;
  border-color: #215F0040;
  border-width: thin;
    position:relative;
    
  box-shadow: 0px 1px 3px -1px #000000, 
            0px -1px 5px  #DFDFDF;
}```

###### **Thedata**
####### ```css
/*Thedata*/
span.rm-page-ref[data-tag="Thedata"] {
background: #fff;
	background-size: 100%;
 background-color:#ce796b !important;
    color: #000;
    padding: 2px 5px 2px 5px;
    font-size: 13px;
    line-height: 1em;
    font-weight: 500;
    border-radius: 5px 5px 5px 5px;
   border-style: solid;
  border-color: #215F0040;
  border-width: thin;
    position:relative;
    
  box-shadow: 0px 1px 3px -1px #000000, 
            0px -1px 5px  #DFDFDF;
}```

###### **LN**
####### ```css
/*LN*/
span.rm-page-ref[data-tag="LN"] {
background: #fff;
	background-size: 100%;
 background-color:#e09f3e !important;
    color: #000;
    padding: 2px 5px 2px 5px;
    font-size: 8px;
    line-height: 1em;
    font-weight: 500;
    border-radius: 5px 5px 5px 5px;
   border-style: solid;
  border-color: #215F0040;
  border-width: thin;
    position:relative;
    
  box-shadow: 0px 1px 3px -1px #000000, 
            0px -1px 5px  #DFDFDF;
}```

###### **Toread**
####### ```css
/*Toread*/
span.rm-page-ref[data-tag="Toread"] {
background: #fff;
	background-size: 100%;
 background-color:#e09f3e !important;
    color: #000;
    padding: 2px 5px 2px 5px;
    font-size: 13px;
    line-height: 1em;
    font-weight: 500;
    border-radius: 5px 5px 5px 5px;
   border-style: solid;
  border-color: #215F0040;
  border-width: thin;
    position:relative;
    
  box-shadow: 0px 1px 3px -1px #000000, 
            0px -1px 5px  #DFDFDF;
}```

###### **Tolink**
####### ```css
/*Tolink*/
span.rm-page-ref[data-tag="Tolink"] {
background: #fff;
	background-size: 100%;
 background-color:#6b9080 !important;
    color: #000;
    padding: 2px 5px 2px 5px;
    font-size: 13px;
    line-height: 1em;
    font-weight: 500;
    border-radius: 5px 5px 5px 5px;
   border-style: solid;
  border-color: #215F0040;
  border-width: thin;
    position:relative;
    
  box-shadow: 0px 1px 3px -1px #000000, 
            0px -1px 5px  #DFDFDF;
}
```

###### **Theday**
####### ```css
/*Theday*/
span.rm-page-ref[data-tag="Theday"] {
background: #fff;
	background-size: 100%;
 background-color:#81a4cd !important;
    color: #000;
    padding: 2px 5px 2px 5px;
    font-size: 13px;
    line-height: 1em;
    font-weight: 500;
    border-radius: 5px 5px 5px 5px;
   border-style: solid;
  border-color: #215F0040;
  border-width: thin;
    position:relative;
    
  box-shadow: 0px 1px 3px -1px #000000, 
            0px -1px 5px  #DFDFDF;
}```

###### **Quick Capture**
####### ```css
/*Quick Capture*/
span.rm-page-ref[data-tag="Quick Capture"] {
background: #fff;
	background-size: 100%;
 background-color:#fff !important;
    color: #000;
    padding: 2px 5px 2px 5px;
    font-size: 13px;
    line-height: 1em;
    font-weight: 500;
    border-radius: 5px 5px 5px 5px;
   border-style: solid;
  border-color: #215F0040;
  border-width: thin;
    position:relative;
    
  box-shadow: 0px 1px 3px -1px #000000, 
            0px -1px 5px  #DFDFDF;
}
```

##### #[[Intermediary Notes]]    {{模式2 null}} 
###### **Intermediary Notes**
####### ```css
/*Intermediary Notes*/
span.rm-page-ref[data-tag="Intermediary Notes"] {
	color: #1A1718 !important;
    padding: 2px 5px 2px 5px;
    font-size: 13px;
    line-height: 1em;
    font-weight: 500;
    border-radius: 5px 5px 5px 5px;
    position:relative;
background: #215F0068;  /* fallback for old browsers */
background: -webkit-linear-gradient(to right, #E4E4D96B, #215F0040);  /* Chrome 10-25, Safari 5.1-6 */
background: linear-gradient(to right, #E4E4D96B, #215F0040); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

  
}
```

##### #[[Branching Notes]] [[Test]]     {{模式3 null}}  
###### **Branching Notes**
####### ```css
/*Branching Notes*/
span.rm-page-ref[data-tag="Branching Notes"] {
background: #B79891;  /* fallback for old browsers */
background: -webkit-linear-gradient(to right, #94716B, #B79891);  /* Chrome 10-25, Safari 5.1-6 */
background: linear-gradient(to right, #94716B, #B79891); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

	background-size: 100%;
    color: #EEF2EE;
    padding: 2px 5px 2px 5px;
    font-size: 13px;
    line-height: 1em;
    font-weight: 500;
    border-radius: 5px 5px 5px 5px;
    position:relative;
}

 span.rm-page-ref[data-tag="Branching Notes"] + span[data-link-title] {
     background: #B7989128 !important;
     color: #F3F7F2 !important;
     padding: 3px 5px 3px 5px;
     font-size: 13px;
     line-height: 1em;
     font-weight: 400;
     border-radius: 0px 5px 5px 0px;
     margin-left: -5px;
}

}





















```

###### 

##### #[[💡Zettelkasten]]   {{模式4 null}} 
###### **42SmartBlock**
####### ```css
/*42SmartBlock */
span.rm-page-ref[data-tag="42SmartBlock"] {
	color: #1A1718 !important;
    padding: 2px 5px 2px 5px;
    font-size: 13px;
    line-height: 1em;
    font-weight: 500;
    border-radius: 5px 5px 5px 5px;
    position:relative;
background: #215F0068;  /* fallback for old browsers */
background: -webkit-linear-gradient(to right,#DA53EEAD, #FE7FBFAD, #FF9580AD, #FFFF80AD, #8AFF80AD, #92FFFFAD, #9580FFAD);  /* Chrome 10-25, Safari 5.1-6 */
background: linear-gradient(to right,#DA53EEAD, #FE7FBFAD, #FF9580AD, #FFFF80AD, #8AFF80AD, #92FFFFAD, #9580FFAD); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

  
}




```

###### **💡Zettelkasten**
####### ```css
/*💡Zettelkasten*/
span.rm-page-ref[data-tag="💡Zettelkasten"] {
	color: #1A1718 !important;
    padding: 2px 5px 2px 5px;
    font-size: 15px;
    line-height: 1em;
    font-weight: 500;
    border-radius: 5px 5px 5px 5px;
    position:relative;
background: #778da9;  /* fallback for old browsers */
background: -webkit-linear-gradient(to right,#DA53EEAD, #FE7FBFAD, #FF9580AD, #FFFF80AD, #8AFF80AD, #92FFFFAD, #9580FFAD);  /* Chrome 10-25, Safari 5.1-6 */
background: linear-gradient(to right,#DA53EEAD, #FE7FBFAD, #FF9580AD, #FFFF80AD, #8AFF80AD, #92FFFFAD, #9580FFAD); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

  
}```

###### **roam/templates**
####### ```css
/* roam/templates*/
span.rm-page-ref[data-tag="roam/templates"] {
	color: #1A1718 !important;
    padding: 2px 5px 2px 5px;
    font-size: 13px;
    line-height: 1em;
    font-weight: 500;
    border-radius: 5px 5px 5px 5px;
    position:relative;
background: #215F0068;  /* fallback for old browsers */
background: -webkit-linear-gradient(to right,#DA53EEAD, #FE7FBFAD, #FF9580AD, #FFFF80AD, #8AFF80AD, #92FFFFAD, #9580FFAD);  /* Chrome 10-25, Safari 5.1-6 */
background: linear-gradient(to right,#DA53EEAD, #FE7FBFAD, #FF9580AD, #FFFF80AD, #8AFF80AD, #92FFFFAD, #9580FFAD); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

  
}```

##### #Chat [[Your Name]] #@ [[Your Name]]     {{模式5 null}}
###### **Chat**
####### ```css
/*Chat*/
span.rm-page-ref[data-tag="Chat"] {
	background-image: linear-gradient(to right, #4c8dc9,#4c8dc9);
	background-size: 100%;
    color: #EEF2EE;
    padding: 3px 2px 3px 5px;
    font-size: 13px;
    line-height: 1em;
    border-radius: 3px 0 0 3px;
    position:relative;
}

 span.rm-page-ref[data-tag="Chat"] + span[data-link-title] {
     background: #e4ffe3 !important;
     color: #F3F7F2 !important;
     padding: 3px 5px 3px 15px;
     font-size: 13px;
     line-height: 1em;
     font-weight: 400;
     border-radius: 0 3px 3px 0;
     margin-left: -5px;
}


span.rm-page-ref[data-tag="Chat"]:after, 
span.rm-page-ref[data-tag="Chat"]:before {
    left: 100%;
    top: 50%;
    border: solid transparent;
    content: " ";
    height: 0;
  width: 0;
    position: absolute;
  pointer-events: none;
}

span.rm-page-ref[data-tag="Chat"]:after {
    border-color: rgba(255,255,255,0);
    border-left-color: #4c8dc9;
    border-width: 11px;
    margin-top: -11px;
}

span.rm-page-ref[data-tag="Chat"]:before {
  border-color: rgba(255,255,255,0);
    border-left-color: #4c8dc9;
    border-width: 11px;
  margin-top: -11px;
}```

###### **@**
####### ```css
/*@*/
span.rm-page-ref[data-tag="@"] {
	background-image: linear-gradient(to right, #4c8dc9,#4c8dc9);
	background-size: 100%;
    color: #EEF2EE;
    padding: 3px 2px 3px 5px;
    font-size: 13px;
    line-height: 1em;
    border-radius: 3px 0 0 3px;
    position:relative;
}

 span.rm-page-ref[data-tag="@"] + span[data-link-title] {
     background: #e4ffe3 !important;
     padding: 3px 5px 3px 15px;
     font-size: 13px;
     line-height: 1em;
     font-weight: 400;
     border-radius: 0 3px 3px 0;
     margin-left: -5px;
}


span.rm-page-ref[data-tag="@"]:after, span.rm-page-ref[data-tag="@"]:before {
    left: 100%;
    top: 50%;
    border: solid transparent;
    content: " ";
  height: 0;
    width: 0;
    position: absolute;
  pointer-events: none;
}

span.rm-page-ref[data-tag="@"]:after {
    border-color: rgba(255,255,255,0);
    border-left-color: #4c8dc9;
    border-width: 11px;
  margin-top: -11px;
}

span.rm-page-ref[data-tag="@"]:before {
  border-color: rgba(255,255,255,0);
    border-left-color: #4c8dc9;
    border-width: 11px;
  margin-top: -11px;
}```

###### **TODO**
####### ```css
/*TODO*/
span.rm-page-ref[data-tag="TODO"] {
	background-image: linear-gradient(to right, #e56b6f,#e56b6f);
	background-size: 100%;
    color: #EEF2EE;
    padding: 3px 2px 3px 5px;
    font-size: 13px;
    line-height: 1em;
    border-radius: 3px 0 0 3px;
    position:relative;
}


 span.rm-page-ref[data-tag="TODO"] + span[data-link-title] {
     background: #e4ffe3 !important;
     color: #F3F7F2 !important;
     padding: 3px 5px 3px 15px;
     font-size: 13px;
     line-height: 1em;
     font-weight: 400;
     border-radius: 0 3px 3px 0;
     margin-left: -5px;
}
span.rm-page-ref[data-tag="TODO"]:after, 
span.rm-page-ref[data-tag="TODO"]:before {
  left: 100%;
  top: 50%;
    border: solid transparent;
    content: " ";
    height: 0;
  width: 0;
    position: absolute;
  pointer-events: none;
}
span.rm-page-ref[data-tag="TODO"]:after {
    border-color: rgba(255,255,255,0);
    border-left-color: #e56b6f;
  border-width: 11px;
    margin-top: -11px;
}
span.rm-page-ref[data-tag="TODO"]:before {
  border-color: rgba(255,255,255,0);
  border-left-color: #e56b6f;
    border-width: 11px;
  margin-top: -11px;
}
```

###### **Tofollow**
####### ```css
/*Tofollow*/
span.rm-page-ref[data-tag="Tofollow"] {
	background-image: linear-gradient(to right, #e56b6f,#e56b6f);
	background-size: 100%;
    color: #EEF2EE;
    padding: 3px 2px 3px 5px;
    font-size: 13px;
    line-height: 1em;
    border-radius: 3px 0 0 3px;
    position:relative;
}


 span.rm-page-ref[data-tag="Tofollow"] + span[data-link-title] {
     background: #e4ffe3 !important;
     color: #F3F7F2 !important;
     padding: 3px 5px 3px 15px;
     font-size: 13px;
     line-height: 1em;
     font-weight: 400;
     border-radius: 0 3px 3px 0;
     margin-left: -5px;
}




span.rm-page-ref[data-tag="Tofollow"]:after, 
span.rm-page-ref[data-tag="Tofollow"]:before {
    left: 100%;
    top: 50%;
    border: solid transparent;
    content: " ";
    height: 0;
  width: 0;
    position: absolute;
  pointer-events: none;
}


span.rm-page-ref[data-tag="Tofollow"]:after {
    border-color: rgba(255,255,255,0);
    border-left-color: #e56b6f;
    border-width: 11px;
    margin-top: -11px;
}


span.rm-page-ref[data-tag="Tofollow"]:before {
  border-color: rgba(255,255,255,0);
    border-left-color: #e56b6f;
    border-width: 11px;
  margin-top: -11px;
}
```

###### **Tobill**
####### ```css
/*Tobill*/
span.rm-page-ref[data-tag="Tobill"] {
	background-image: linear-gradient(to right, #e09f3e,#e09f3e);
	background-size: 100%;
    color: #EEF2EE;
    padding: 3px 2px 3px 5px;
    font-size: 13px;
    line-height: 1em;
    border-radius: 3px 0 0 3px;
    position:relative;
}


 span.rm-page-ref[data-tag="Tobill"] + span[data-link-title] {
     background: #e4ffe3 !important;
     color: #F3F7F2 !important;
     padding: 3px 5px 3px 15px;
     font-size: 13px;
     line-height: 1em;
     font-weight: 400;
     border-radius: 0 3px 3px 0;
     margin-left: -5px;
}




span.rm-page-ref[data-tag="Tobill"]:after, 
span.rm-page-ref[data-tag="Tobill"]:before {
    left: 100%;
    top: 50%;
    border: solid transparent;
    content: " ";
    height: 0;
  width: 0;
    position: absolute;
  pointer-events: none;
}


span.rm-page-ref[data-tag="Tobill"]:after {
    border-color: rgba(255,255,255,0);
    border-left-color: #e09f3e;
    border-width: 11px;
    margin-top: -11px;
}


span.rm-page-ref[data-tag="Tobill"]:before {
  border-color: rgba(255,255,255,0);
    border-left-color: #e09f3e;
    border-width: 11px;
  margin-top: -11px;
}
```

###### **Todooo**
####### ```css
/*Todooo*/
span.rm-page-ref[data-tag="Todooo"] {
	background-image: linear-gradient(to right, #e56b6f,#e56b6f);
	background-size: 100%;
    color: #EEF2EE;
    padding: 3px 2px 3px 5px;
    font-size: 13px;
    line-height: 1em;
    border-radius: 3px 0 0 3px;
    position:relative;
}




 span.rm-page-ref[data-tag="Todooo"] + span[data-link-title] {
     background: #e4ffe3 !important;
     color: #F3F7F2 !important;
     padding: 3px 5px 3px 15px;
     font-size: 13px;
     line-height: 1em;
     font-weight: 400;
     border-radius: 0 3px 3px 0;
     margin-left: -5px;
}
span.rm-page-ref[data-tag="Todooo"]:after, 
span.rm-page-ref[data-tag="Todooo"]:before {
    left: 100%;
    top: 50%;
    border: solid transparent;
    content: " ";
    height: 0;
  width: 0;
    position: absolute;
  pointer-events: none;
}




span.rm-page-ref[data-tag="Todooo"]:after {
    border-color: rgba(255,255,255,0);
    border-left-color: #e56b6f;
    border-width: 11px;
    margin-top: -11px;
}




span.rm-page-ref[data-tag="Todooo"]:before {
  border-color: rgba(255,255,255,0);
    border-left-color: #e56b6f;
    border-width: 11px;
  margin-top: -11px;
}
```

###### **Error**
####### ```css
/*Error*/
span.rm-page-ref[data-tag="Error"] {
	background-image: linear-gradient(to right, #e72100,#e72100);
	background-size: 100%;
    color: #EEF2EE;
    padding: 3px 2px 3px 5px;
    font-size: 13px;
    line-height: 1em;
    border-radius: 3px 0 0 3px;
    position:relative;
}

 span.rm-page-ref[data-tag="Error"] + span[data-link-title] {
     background: #e4ffe3 !important;
     color: #F3F7F2 !important;
     padding: 3px 5px 3px 15px;
     font-size: 13px;
     line-height: 1em;
     font-weight: 400;
     border-radius: 0 3px 3px 0;
     margin-left: -5px;
}


span.rm-page-ref[data-tag="Error"]:after, 
span.rm-page-ref[data-tag="Error"]:before {
    left: 100%;
    top: 50%;
    border: solid transparent;
    content: " ";
    height: 0;
  width: 0;
    position: absolute;
  pointer-events: none;
}

span.rm-page-ref[data-tag="Error"]:after {
    border-color: rgba(255,255,255,0);
    border-left-color: #e72100;
    border-width: 11px;
    margin-top: -11px;
}

span.rm-page-ref[data-tag="Error"]:before {
  border-color: rgba(255,255,255,0);
    border-left-color: #e72100;
    border-width: 11px;
  margin-top: -11px;
}


```

##### #[[Permanent Notes]] [[Test]]    #Zettels[[Test]]  {{模式6 null}}
###### **Permanent Notes**
####### ```css
/*Permanent Notes*/
span.rm-page-ref[data-tag="Permanent Notes"] {
	background-image: linear-gradient(90deg, #4c8dc9, #4c8dc9, #4c8dc9);
	background-size: 100%;
    color: #EEF2EE;
    padding: 2px 2px 2px 5px;
    font-size: 13px;
    line-height: 1em;
    font-weight: 500;
    border-radius: 3px 0 0 3px;
    position:relative;
}

 span.rm-page-ref[data-tag="Permanent Notes"] + span[data-link-title] {
     background: #DCE5DE8C !important;
     color: #F3F7F2 !important;
     padding: 3px 5px 3px 15px;
     font-size: 13px;
     line-height: 1em;
     font-weight: 400;
     border-radius: 0 3px 3px 0;
     margin-left: -5px;
}


span.rm-page-ref[data-tag="Permanent Notes"]:after, span.rm-page-ref[data-tag="Permanent Notes"]:before {
    left: 100%;
    top: 50%;
    border: solid transparent;
    content: " ";
    height: 0;
    width: 0;
    position: absolute;
    pointer-events: none;
}

span.rm-page-ref[data-tag="Permanent Notes"]:after {
    border-color: rgba(255,255,255,0);
    border-left-color: #4c8dc9;
    border-width: 10px;
    margin-top: -10px;
}

span.rm-page-ref[data-tag="Permanent Notes"]:before {
    border-color: rgba(255,255,255,0);
    border-left-color: #4c8dc9;
    border-width: 10px;
    margin-top: -10px;
}
```

###### **Anki**
####### ```css
/*Anki*/
span.rm-page-ref[data-tag="Anki"] {
	background-image: linear-gradient(90deg, #607D8B, #96B09B, #607D8B);
	background-size: 100%;
    color: #EEF2EE;
    padding: 2px 2px 2px 5px;
    font-size: 13px;
    line-height: 1em;
    font-weight: 500;
    border-radius: 3px 0 0 3px;
    position:relative;
}

 span.rm-page-ref[data-tag="Anki"] + span[data-link-title] {
     background: #DCE5DE8C !important;
     color: #F3F7F2 !important;
     padding: 3px 5px 3px 15px;
     font-size: 13px;
     line-height: 1em;
     font-weight: 400;
     border-radius: 0 3px 3px 0;
     margin-left: -5px;
}


span.rm-page-ref[data-tag="Anki"]:after, span.rm-page-ref[data-tag="Anki"]:before {
    left: 100%;
    top: 50%;
    border: solid transparent;
    content: " ";
    height: 0;
    width: 0;
    position: absolute;
    pointer-events: none;
}

span.rm-page-ref[data-tag="Anki"]:after {
    border-color: rgba(255,255,255,0);
    border-left-color: #607D8B;
    border-width: 10px;
    margin-top: -10px;
}

span.rm-page-ref[data-tag="Anki"]:before {
    border-color: rgba(255,255,255,0);
    border-left-color: #607D8B;
    border-width: 10px;
    margin-top: -10px;
}

```

###### **Roam Flow**
####### ```css
/*Roam Flow*/
span.rm-page-ref[data-tag="Roam Flow"] {
	background-image: linear-gradient(90deg, #778da9, #778da9, #778da9);
	background-size: 100%;
    color: #EEF2EE;
    padding: 2px 2px 2px 5px;
    font-size: 13px;
    line-height: 1em;
    font-weight: 500;
    border-radius: 3px 0 0 3px;
    position:relative;
}

 span.rm-page-ref[data-tag="Roam Flow"] + span[data-link-title] {
     background: #DCE5DE8C !important;
     color: #F3F7F2 !important;
     padding: 3px 5px 3px 15px;
     font-size: 13px;
     line-height: 1em;
     font-weight: 400;
     border-radius: 0 3px 3px 0;
     margin-left: -5px;
}


span.rm-page-ref[data-tag="Roam Flow"]:after, span.rm-page-ref[data-tag="Roam Flow"]:before {
    left: 100%;
    top: 50%;
    border: solid transparent;
    content: " ";
    height: 0;
    width: 0;
    position: absolute;
    pointer-events: none;
}

span.rm-page-ref[data-tag="Roam Flow"]:after {
    border-color: rgba(255,255,255,0);
    border-left-color: #778da9;
    border-width: 10px;
    margin-top: -10px;
}

span.rm-page-ref[data-tag="Roam Flow"]:before {
    border-color: rgba(255,255,255,0);
    border-left-color: #778da9;
    border-width: 10px;
    margin-top: -10px;
}

```

###### **Zettels**
####### ```css
/* Zettels */
span.rm-page-ref[data-tag="Zettels"] {
	background-image: linear-gradient(90deg, #4c8dc9, #4c8dc9, #4c8dc9);
	background-size: 100%;
    color: #EEF2EE;
    padding: 2px 2px 2px 5px;
    font-size: 13px;
    line-height: 1em;
    font-weight: 500;
    border-radius: 3px 0 0 3px;
    position:relative;
}

 span.rm-page-ref[data-tag="Zettels"] + span[data-link-title] {
     background: #DCE5DE8C !important;
     color: #F3F7F2 !important;
     padding: 3px 5px 3px 15px;
     font-size: 13px;
     line-height: 1em;
     font-weight: 400;
     border-radius: 0 3px 3px 0;
     margin-left: -5px;
}


span.rm-page-ref[data-tag="Zettels"]:after, span.rm-page-ref[data-tag="Zettels"]:before {
    left: 100%;
    top: 50%;
    border: solid transparent;
    content: " ";
    height: 0;
    width: 0;
    position: absolute;
    pointer-events: none;
}

span.rm-page-ref[data-tag="Zettels"]:after {
    border-color: rgba(255,255,255,0);
    border-left-color: #4c8dc9;
    border-width: 10px;
    margin-top: -10px;
}

span.rm-page-ref[data-tag="Zettels"]:before {
    border-color: rgba(255,255,255,0);
    border-left-color: #4c8dc9;
    border-width: 10px;
    margin-top: -10px;
}
```

##### #quote     {{模式7 null}}
###### **quote**
####### ```css
/*quote*/
span.rm-page-ref[data-tag="quote"] {
    background: #A7E2EA !important;
    color: rgb(50,68,213) !important;
    padding: 1px 5px;
    line-height: 2em;
  	border-radius: 4px 4px 4px 20px;
}


span.rm-page-ref[data-tag="quote"]:before {
    content: '✦'
}
```

#### **Tags前面添加emoji**
##### ```clojure
span.rm-page-ref[data-tag="TR"]:before {
    content: "🎙"
}

span.rm-page-ref[data-tag="Todooo"]:before {
    content: " 🔔"
}

span.rm-page-ref[data-tag="TODO"]:before {
    content: " 🔔"
}

span.rm-page-ref[data-tag="Tofollow"]:before {
    content: " 🧐"
}

span.rm-page-ref[data-tag="Tobill"]:before {
  content: " 💰"
}

span.rm-page-ref[data-tag="Toread"]:before {
    content: "📒"
}

span.rm-page-ref[data-tag="Tolink"]:before {
    content: "➰"
}

span.rm-page-ref[data-tag="Theday"]:before {
    content: " 🧸"
}

span.rm-page-ref[data-tag="Error"]:before {
    content: " ⚡"
}```

### **颜色与样式**
#### {{颜色 null}}
##### **Block输入底色**
###### ```css
/* 
BODY AND BLOCK COLORS 
         #778da9    
         #95b3d7
         #d8e1e8
         #ebf1f5
         #f5f8fa
         #f2f4f8
         #b76e79   玫瑰金
*/
.rm-block-input {
  background-color: var(--sidebar-background);
  --sidebar-background : #d8e1e8;
  padding-left    : 9px;
  border-radius  : 5.5px;
}}dius  : 5.5px;
}}```

##### **颜色Block**  `chld /blck-chld /blck +colour`
###### ```css
/* this code hides all block tags */
[data-tag^="chld:"] {
    	display:none !important;  
}
[data-tag^="blck-chld:"] {
    	display:none !important;  
}
[data-tag^="blck:"] {
    	display:none !important;  
}
/* -------Roam Colour--------- */
[data-page-links*='\"blck:grey\"'] > .rm-block-main,
[data-page-links*='\"blck-chld:grey\"'],
[data-page-links*='\"chld:grey\"'] > .rm-block-children
{
    /* color: #383d41; */
    background-color: #e2e3e5;
    border: 1px solid #d6d8db; 
    margin-bottom: 5px;
}

[data-page-links*='\"blck:blue\"'] > .rm-block-main,
[data-page-links*='\"blck-chld:blue\"'],
[data-page-links*='\"chld:blue\"'] > .rm-block-children
{
    background-color: #cce5ff;
    border: solid 1px #b8daff;
    margin-bottom: 5px;
}

[data-page-links*='\"blck:green\"'] > .rm-block-main,
[data-page-links*='\"blck-chld:green\"'],
[data-page-links*='\"chld:green\"'] > .rm-block-children
{
    background-color: #d4edda;
    border: 1px solid #c3e6cb; 
    margin-bottom: 5px;
}

[data-page-links*='\"blck:red\"'] > .rm-block-main,
[data-page-links*='\"blck-chld:red\"'],
[data-page-links*='\"chld:red\"'] > .rm-block-children
{
    background-color: #f8d7da;
    border: 1px solid #f5c6cb; 
    margin-bottom: 5px;
}

[data-page-links*='\"blck:yellow\"'] > .rm-block-main,
[data-page-links*='\"blck-chld:yellow\"'],
[data-page-links*='\"chld:yellow\"'] > .rm-block-children
{
    background-color: #fff3cd;   
    border: 1px solid #ffeeba;
    margin-bottom: 5px;
}```

##### **颜色文本**  `#c:colour +高亮/加粗/斜体文本`
###### ```css
/*
Author:: @CatoMinor3
Version:: 3.0
Date:: Sept.rm-italicsber 22nd, 2020
Changes log:
- 3.0 - code adapted for the new classes in Roam
- 2.1 - code adaptated for future support of colour shades (different opacity), 
download the additonal CSS here: https://gist.github.com/ciceronianus/5d7b224658b7a9832a6249a13091aa9d

Support: 
- Paypal: https://www.paypal.me/catominor3
- Patreon: https://www.patreon.com/catominor

How to use this? Simply write c:COLOR (see supported colors below) and follow it with 
the highlighted text, bold text or .rm-italicsphasis. 
*/

/* ---------------- Roam colors -----------------*/

/*Supporter colors:
https://github.com/mrmrs/colors

.navy { color: #001F3F; }
.blue { color: #0074D9; }
.aqua { color: #7FDBFF; }
.teal { color: #39CCCC; }
.olive { color: #3D9970; }
.green { color: #2ECC40; }
.lime { color: #01FF70; }
.yellow { color: #FFDC00; }
.orange { color: #FF851B; }
.red { color: #FF4136; }
.fuchsia { color: #F012BE; }
.purple { color: #B10DC9; }
.maroon { color: #85144B; }
.silver { color: #DDDDDD; }
.gray { color: #AAAAAA; }
.black { color: #111111; }

*/
[data-tag^="c:"] {
    	display:none !important;  
}

[data-tag^="c:"] + .rm-highlight, 
[data-tag^="c:"] + span > .rm-page-ref--link {
    color: #111111 !important;
	border-radius: 1px;
	padding-left: 4px;
	padding-right: 4px;
	font-weight: bold;
}

[data-tag^="c:navy"] + .rm-highlight,
[data-tag^="c:navy"] + span > .rm-page-ref--link {
	background-color: #001F3F !important;
}

[data-tag^="c:navy"] + .rm-italics, 
[data-tag^="c:navy"] + .rm-bold 
{color: #001F3F; }

[data-tag^="c:blue"] + .rm-highlight,
[data-tag^="c:blue"] + span > .rm-page-ref--link {
	background-color: #0074D9 !important;
}


[data-tag^="c:blue"] + .rm-italics, 
[data-tag^="c:blue"] + .rm-bold {
    color: #0074D9;
    
}

[data-tag^="c:aqua"] + .rm-highlight,
[data-tag^="c:aqua"] + span > .rm-page-ref--link {
	background-color: #7FDBFF !important;
}

[data-tag^="c:aqua"] + .rm-italics, 
[data-tag^="c:aqua"] + .rm-bold {
    color: #7FDBFF;
    
}

[data-tag^="c:teal"] + .rm-highlight,
[data-tag^="c:teal"] + span > .rm-page-ref--link {
	background-color: #39CCCC !important;
}


[data-tag^="c:teal"] + .rm-italics,
[data-tag^="c:teal"] + .rm-bold {
    color: #39CCCC;
    
}


[data-tag^="c:olive"] + .rm-highlight,
[data-tag^="c:olive"] + span > .rm-page-ref--link {
	background-color: #3D9970 !important;
}

[data-tag^="c:olive"] + .rm-italics,
[data-tag^="c:olive"] + .rm-bold {
    color: #3D9970;
    
}

[data-tag^="c:green"] + .rm-highlight,
[data-tag^="c:green"] + span > .rm-page-ref--link {
	background-color: #2ECC40 !important;
}

[data-tag^="c:green"] + .rm-italics,
[data-tag^="c:green"] + .rm-bold {
    color: #2ECC40;
    
}


[data-tag^="c:lime"] + .rm-highlight,
[data-tag^="c:lime"] + span > .rm-page-ref--link {

	background-color: #01FF70 !important;

}

[data-tag^="c:lime"] + .rm-italics,
[data-tag^="c:lime"] + .rm-bold {
    color: #01FF70;
    
}

[data-tag^="c:yellow"] + .rm-highlight,
[data-tag^="c:yellow"] + span > .rm-page-ref--link {

	background-color: #FFDC00 !important;

}

[data-tag^="c:yellow"] + .rm-italics,
[data-tag^="c:yellow"] + .rm-bold {
    color: #FFDC00;
    
}

[data-tag^="c:orange"] + .rm-highlight,
[data-tag^="c:orange"] + span > .rm-page-ref--link {

	background-color: #FF851B !important;

}

[data-tag^="c:orange"] + .rm-italics,
[data-tag^="c:orange"] + .rm-bold {
    color: #FF851B;
    
}


[data-tag^="c:red"] + .rm-highlight,
[data-tag^="c:red"] + span > .rm-page-ref--link {

	background-color: #FF4136 !important;

}

[data-tag^="c:red"] + .rm-italics,
[data-tag^="c:red"] + .rm-bold
{
    color: #FF4136;
    
}

 







[data-tag^="c:fuchsia"] + .rm-highlight,
[data-tag^="c:fuchsia"] + span > .rm-page-ref--link {

	background-color: #F012BE !important;

}

[data-tag^="c:fuchsia"] + .rm-italics, 
[data-tag^="c:fuchsia"] + .rm-bold {
    color: #F012BE;
    
}

[data-tag^="c:purple"] + .rm-highlight,
[data-tag^="c:purple"] + span > .rm-page-ref--link {

	background-color: #B10DC9 !important;

}

[data-tag^="c:purple"] + .rm-italics,
[data-tag^="c:purple"] + .rm-bold {
    
    color: #B10DC9;
}

[data-tag^="c:maroon"] + .rm-highlight,
[data-tag^="c:maroon"] + span > .rm-page-ref--link {

	background-color: #85144B !important;

}

[data-tag^="c:maroon"] + .rm-italics,
[data-tag^="c:maroon"] + .rm-bold {
    color: #85144B;
    
}

[data-tag^="c:silver"] + .rm-highlight,
[data-tag^="c:silver"] + span > .rm-page-ref--link {

	background-color: #DDDDDD !important;

}

[data-tag^="c:silver"] + .rm-italics,
[data-tag^="c:silver"] + .rm-bold {
    color: #DDDDDD;
    
}

[data-tag^="c:gray"] + .rm-highlight,
[data-tag^="c:gray"] + span > .rm-page-ref--link {

	background-color: #AAAAAA !important;

}

[data-tag^="c:gray"] + .rm-italics,
[data-tag^="c:gray"] + .rm-bold {
    color: #AAAAAA;
    
}

[data-tag^="c:black"] + .rm-highlight,
[data-tag^="c:black"] + span > .rm-page-ref--link {

	background-color: #111111 !important;

}

[data-tag^="c:black"] + .rm-italics,
[data-tag^="c:black"] + .rm-bold {
    color: #111111;
    
}	
```

###### ```css

[data-tags-up~="sticky"] {
  position: -webkit-sticky; /* Safari */
  position: sticky !important;
  top: 0;
  z-index: 10;
}```

##### 颜色边框
###### ```css

[data-tag^="border:"] {
    	display:none !important;  
}

[data-tags~="border:red"] {
  border: 1px solid red;
}

[data-tags-up~="border:orange"] {
  border: 1px solid orange;
}


[data-tags-up~="border:blue"] > div:nth-child(2) {
border: 1px solid blue;
}

```

#### {{样式 null}}
##### **级标题样式**
###### ```css
/* h3 三级标题
#5c7080
#0549BA
*/
/*
.rm-level3 div, .rm-level3 textarea {
    color: #4E7486F9 !important;
    font-size: 16px !important;
    font-weight:700 !important;
}
h3 {
    font-family:".萍方-简", Times, serif !important;
    border-left: 5px solid #4E7486F9 !important;
    padding-left:5px !important;
    padding-right:7px !important;
    font-style:normal;
    border-top-left-radius:4px;
    border-bottom-left-radius:4px;
}
*/
/* h2 二级标题*/
.rm-level2 div, .rm-level2 textarea {
    color: #0549BA !important;
    font-size: 17px !important;
    font-weight:900 !important;
}
h2 {
    font-family:".萍方-简", Times, serif !important;
    border-left: 5.5px solid #0549BA !important;
    padding-left:6px !important;
    padding-right:7px !important;
    font-style:normal;
    border-top-left-radius:4px;
    border-bottom-left-radius:4px;
}```

##### **CSS code for inline Bold & Italics** 
###### [[****]] 
[[____]] 
[[$$$$]]
####### ```css

[data-page-links*="****"] > .rm-block-main > .roam-block,
[data-page-links*="****"] > .rm-block-main > .rm-autocomplete__wrapper
{
 font-weight: bold;
}

[data-link-title="****"] {
  display:none;
}
[data-page-links*='\"____\"'] > .rm-block-main > .roam-block,
[data-page-links*='\"____\"'] > .rm-block-main > .rm-autocomplete__wrapper
{ font-style: italic; 
}
[data-link-title="____"] 
{ display:none;
}

/* DELETE THESE LINES if you want to activate UNDERLINE
You can UNDERLINE with [[$$$$]] -- may not work with PC
 */

[data-page-links*='\"$$$$\"'] > .rm-block-main > .roam-block,
[data-page-links*='\"$$$$\"'] > .rm-block-main > .rm-autocomplete__wrapper
{ text-decoration: underline;
}
[data-link-title="$$$$"] 
{ display:none;
}
```

##### **高亮、加粗、斜体、删除线样式**
###### ```css
/* 高亮、加粗、斜体、删除线样式*/
b, strong {
    color: #07090A !important;
    font-weight:800 !important;
    text-shadow: 0px 0px 0px #c6c0c0;
    background-color:rgb(0,0,0)00;
	font-size:15.5px;
    
}
em {
	border-bottom:1.3px wavy;
	color: #4E8888;
    font-weight:700 !important;
  font-family:"宋体", Times, serif !important;
}
del {
    background: #9E9E9E !important;
    color: #9E9E9E !important;
    text-decoration: none;
}
del:hover{
    text-decoration: none;
    background-color: #DFF4C63b;
}
/*.roam-highlight {
	border-bottom:1.3px wavy;
	color: #121313;
	font-weight:500 !important;
	background-color:#fef09f;
    font-size:15.5px;
    line-height: 1.5em;
}
*/
/* 
    #0468BD    
    #337ab7
    .萍方-简
    text-shadow: 0px 0px 0px #c6c0c0;
 COLORS - One light
    --page-links              : #2979ff;
    --attributes-color        : #986801;
    --external-links          : #50A14E;
    --links-hover             : #E4564A;
    --hashtags                : #A626A4;
    --body-text               : #292D31;
    --italics-color           : #E4564A;
    --bold-color              : #0184BC;
    --highlight-text-color    : #292D31;
    --highlighter             : #FFFF80;
    --background              : #FAFAFA;
    --sidebar-background      : #EAEAEB;
    --sidebar-text            : #292D31;
    --page-heading            : #2979ff;
    --daily-heading           : #2979ff;
    --headings                : #292D31;
    --bullets                 : #4078F2;
    --closed-bullets          : #4078F277;
    --references              : #4078F2;
    --block-reference-text    : #0184BC;
    --namespaces              : #E4564A;
    --all-pages-mentions      : #0184BC;
    --cursor                  : #292D31;
    --icons                   : #4078F2;
    --icons-hover             : #E4564A;
    --filter-icon             : #50A14E;
*/
```

##### **Highlighting the Scope**
###### Where do we work:
####### Transition in: 
######## ```css


.roam-block-container:focus-within > .rm-block-main > div:nth-child(1) .rm-bullet .rm-bullet__inner {
   background-color: #ce796b;
  width: 7px;
  height: 3px;
  border-radius: 0px;
  transition: width 300ms linear, height 300ms linear, border-radius 300ms linear;
}
```

####### Transition out:
######## ```css

.roam-block-container > .rm-block-main > div:nth-child(1)
 .rm-bullet .rm-bullet__inner  {
  background-color: default;
  width: default;
  height: default;
  border-radius: default;
  transition: width 300ms linear, height 300ms linear, border-radius 300ms linear;
}```

###### Where does the mouse hover
####### Setting default values
######## ```css
.roam-block-container div.roam-block-container {
  border-left-width: 0.1px;
  border-left-color: #c2ced8;
  transition: border-left-color 0.1s;
  
  box-shadow: -0.1px 0px 0px 0px #c2ced8;
  transition: box-shadow 0.1s;
}
```

####### Transition on hover:
######## ```css
div.roam-block-container:hover > 
div:nth-child(2) > .roam-block-container {
 border-left-style: solid;
 border-left-color: #c2ced8;
 transition:  border-left-color 0.1s ease-in-out;
  
 box-shadow: -1.5px 0px 0px 0px #d62828;
 transition: box-shadow 0.01s;
  
}```

##### **彩虹 indentation**
###### ```clojure
/* Rainbow indentation */
/* 
Feel free to adjust the color variables!
This one has 18 colors deep (3 cycles of 3 rainbow flavored palettes).
This loops 3 times so it goes 54 levels deep!
To add more levels just target
.rm-level-n > div for every nth level
*/

@import url('https://abhayprasanna.github.io/rainbow-indent-core.css');

:root {
    --box-shadow-values: 25px 0px 20px -30px; /* Set to "none" to remove shadow */
    --indent1: #5F388BAD;
    --indent2: #4A57BAAD;
    --indent3: #48864DAD;
    --indent4: #A7A15AAD;
    --indent5: #AD7E48AD;
    --indent6: #A5494FAD;
    --indent7: #634071AD;
    --indent8: #303472AD;
    --indent9: #395C45AD;
    --indent10: #7C7948AD;
    --indent11: #7D5039AD;
    --indent12: #A5494FAD;
    --indent13: #706597AD;
    --indent14: #657D91AD;
    --indent15: #6D8D76AD;
    --indent16: #A09A84AD;
    --indent17: #987174AD;
    --indent18: #8B5F78AD;
}

.block-border-left {
    border-left-width: 1px !important; /* Default 1px */
    margin-left: 6px; /* Default 6px */
    border-radius: 0; /* Set to 0 to get smooth, straight indents */
    padding: 0 !important; /* Set to 0 to align all indents */
}

/* 
To add deeper indents:
Add colors for " .rm-level-n > div " incrementally (n = indent level)
*/
/* Level 1 */
.rm-level-1 > div, .rm-level-19 > div, .rm-level-37 > div {
    border-left-color: var(--indent1) !important;
  box-shadow: var(--box-shadow-values) var(--indent1) inset;
}

/* Level 2 */
.rm-level-2 > div, .rm-level-20 > div, .rm-level-38 > div {
    border-left-color: var(--indent2) !important;
    box-shadow: var(--box-shadow-values) var(--indent2) inset;
}

/* Level 3 */
.rm-level-3 > div, .rm-level-21 > div, .rm-level-39 > div {
    border-left-color: var(--indent3) !important;
    box-shadow: var(--box-shadow-values) var(--indent3) inset;
}

/* Level 4 */
.rm-level-4 > div, .rm-level-22 > div, .rm-level-40 > div {
    border-left-color: var(--indent4) !important;
    box-shadow: var(--box-shadow-values) var(--indent4) inset;
}

/* Level 5 */
.rm-level-5 > div, .rm-level-23 > div, .rm-level-41 > div {
    border-left-color: var(--indent5) !important;
    box-shadow: var(--box-shadow-values) var(--indent5) inset;
}

/* Level 6 */
.rm-level-6 > div, .rm-level-24 > div, .rm-level-42 > div {
    border-left-color: var(--indent6) !important;
    box-shadow: var(--box-shadow-values) var(--indent6) inset;
}

/* Level 7 */
.rm-level-7 > div, .rm-level-25 > div, .rm-level-43 > div {
    border-left-color: var(--indent7) !important;
    box-shadow: var(--box-shadow-values) var(--indent7) inset;
}

/* Level 8 */
.rm-level-8 > div, .rm-level-26 > div, .rm-level-44 > div {
  border-left-color: var(--indent8) !important;
    box-shadow: var(--box-shadow-values) var(--indent8) inset;
}

/* Level 9 */
.rm-level-9 > div, .rm-level-27 > div, .rm-level-45 > div {
    border-left-color: var(--indent9) !important;
    box-shadow: var(--box-shadow-values) var(--indent9) inset;
}

/* Level 10 */
.rm-level-10 > div, .rm-level-28 > div, .rm-level-46 > div {
    border-left-color: var(--indent10) !important;
    box-shadow: var(--box-shadow-values) var(--indent10) inset;
}

/* Level 11 */
.rm-level-11 > div, .rm-level-29 > div, .rm-level-47 > div {
    border-left-color: var(--indent11) !important;
    box-shadow: var(--box-shadow-values) var(--indent11) inset;
}

/* Level 12 */
.rm-level-12 > div, .rm-level-30 > div, .rm-level-48 > div {
    border-left-color: var(--indent12) !important;
    box-shadow: var(--box-shadow-values) var(--indent12) inset;
}

/* Level 13 */
.rm-level-13 > div, .rm-level-31 > div, .rm-level-49 > div {
    border-left-color: var(--indent13) !important;
    box-shadow: var(--box-shadow-values) var(--indent13) inset;
}

/* Level 14 */
.rm-level-14 > div, .rm-level-32 > div, .rm-level-50 > div {
    border-left-color: var(--indent14) !important;
    box-shadow: var(--box-shadow-values) var(--indent14) inset;
}

/* Level 15 */
.rm-level-15 > div, .rm-level-33 > div, .rm-level-51 > div {
    border-left-color: var(--indent15) !important;
    box-shadow: var(--box-shadow-values) var(--indent15) inset;
}

/* Level 16 */
.rm-level-16 > div, .rm-level-34 > div, .rm-level-52 > div {
    border-left-color: var(--indent16) !important;
    box-shadow: var(--box-shadow-values) var(--indent16) inset;
}

/* Level 17 */
.rm-level-17 > div, .rm-level-35 > div, .rm-level-53 > div {
    border-left-color: var(--indent17) !important;
    box-shadow: var(--box-shadow-values) var(--indent17) inset;
}

/* Level 18 */
.rm-level-18 > div, .rm-level-36 > div, .rm-level-54 > div {
    border-left-color: var(--indent18) !important;
    box-shadow: var(--box-shadow-values) var(--indent18) inset;
}
```

###### ```clojure
/* Rainbow indentation */
/* 
Feel free to adjust the color variables!
This one loops every 6 colors, and goes 18 levels deep (3 cycles).
The 3 selectors for each level correspond to:
1. Daily notes scrolling view
2. Single page view
3. Right sidebar outline view
*/

@import url('https://abhayprasanna.github.io/rainbow-indent-core.css');

:root {
    --box-shadow-values: 25px 0px 20px -30px; /* Set to "none" to remove shadow */
    --indent1: #5F388BAD;
    --indent2: #4A57BAAD;
    --indent3: #48864DAD;
    --indent4: #A7A15AAD;
    --indent5: #AD7E48AD;
    --indent6: #A5494FAD;
    --indent7: #634071AD;
    --indent8: #303472AD;
    --indent9: #395C45AD;
    --indent10: #7C7948AD;
    --indent11: #7D5039AD;
    --indent12: #A5494FAD;
    --indent13: #706597AD;
    --indent14: #657D91AD;
    --indent15: #6D8D76AD;
    --indent16: #A09A84AD;
    --indent17: #987174AD;
    --indent18: #8B5F78AD;
}

.block-border-left {
    border-left-width: 1px !important; /* Default 1px */
    margin-left: 6px; /* Default 6px */
    border-radius: 0; /* Set to 0 to get smooth, straight indents */
    padding: 0 !important; /* Set to 0 to align all indents */
}```

## ^^偏好设置^^
### **原文显示**
#### ```css

/* Standard part */
[data-page-links*='\">\"'] > .rm-block-main > .roam-block
{
  border: 1px solid lightgrey;
  padding: 20px;
  background-color: hsl(0,0%,98%); 
}

[data-page-links*='\">\"'] > .rm-block-main > .roam-block > blockquote
{
 background-color: inherit;
 border-left: 3px solid orange; 
}

/* Special style for preserving the formatting during editing */ 
[data-page-links*='\">\"'] > .rm-block-main > .rm-autocomplete__wrapper {
  border: 1px solid lightgrey;
  padding: 20px;
  background-color: hsl(0,0%,98%);
  
 /* If you have issues with this style, try to deactivate the following two lines */
  flex: none !important;
  width: 520px;
}

[data-page-links*='\">\"'] > .rm-block-main > .rm-autocomplete__wrapper  > textarea
{
  background-color: inherit;
  border-left: 3px solid orange; 
  
  /* added padding */
  padding-left: 20px;
  padding-top: 10px;
  padding-right: 20px;
  padding-bottom: 10px;
}
```

### **看板**
#### ```clojure
.kanban-board {
    max一width：100% !important； /*看板最大宽度*/
}

.rm- full-width {
    margin-right：0% !important;   /* 看板右侧边缘距离*/
}```

#### ```css
.kanban-board {
  background-color: #f2f5f9;
  max-height: 600px; 
  overflow-x: auto;
  overflow-y: auto;
}

.kanban-column {
  background-color: transparent;
}

.kanban-card {
  box-shadow: 0 1px 4px 0 rgba(21, 27, 38, 0.08);
  border-radius: 4px;
  box-shadow: 0 1px 4px 0 rgba(21, 27, 38, 0.08);
}

.kanban-card:hover {
  box-shadow: 0 3px 5px 0 rgba(0, 0, 0, 0.1);
  transform: translateY(-1px);
}

.kanban-title {
  text-align: left;
  margin: 0px 8px;
  font-weight: 700px;
  border-bottom: none;
}
```

### **去除mermaid的背景色**
#### ```css
.rm-mermaid{
  background: transparent !important;
  min-width: 0px !important;
}

.rm-mermaid .node rect{
  stroke: #2A496F !important;
}

.rm-mermaid div{
  color: #448889 !important;
  margin-right: 15px;
}

.rm-mermaid text{
  fill: #34A5A5 !important;
  font-size: 25px !important;
}

.rm-mermaid rect{
  fill: transparent !important;
  stroke-width: 0px !important;
}

.rm-mermaid tspan{
  fill: #438BE0 !important;
  font-size: 20px !important;
}```

### **块引用**
#### ```css
/* 块引用 */
.rm-block-ref::before {
  content: '↖';
  display: inline-block;
  color: #9E9E9E7A !important;
  margin-right: 5px;
  top: -2px;
  position: relative;
}
.rm-block-ref {
  display: inline-flex;
  border-bottom: none;
  font-size: 1em;
   background-color: #ebf1f5;
  color: #424444 !important;
  background-color:;
}
.rm-block-ref:hover {
  cursor: pointer;
}```

### **Roam-Portal**
#### ```css
/* Roam Portal */
div#ras-results-container-dialog {
  width: 80%;
  height: 80%;
  top: 10%;
  left: 10%;
  transform: unset;
}
div#ras-results-container-dialog[data-v-03d87d80] > div {
  height: 100%;
}
.ras-results-menu-bar[data-v-5709e97f] {
  height: 5%;
}
.ras-results-view-mode[data-v-372f0bd5] {
  height: 74%;
}
.ras-show-pages-on-top-checkbox-container[data-v-54b868be] {
  height: 4%;
}
.ras-results-container[data-v-54b868be] {
  height: 94%;
  padding-bottom: 10px;
}
.ras-result[data-v-54b868be] {
  display: inline-block;
  padding-top: 0px;
  padding-bottom: 0px;
}
.ras-result-title-container[data-v-54b868be] {
  width: 12%;
  min-width: 12%;
  white-space: nowrap;
  overflow: hidden;
  float: left;
}
.ras-result-string[data-v-54b868be] {
  margin-left: 10px;
  white-space: nowrap;
  overflow: hidden;
  float: left;
  width: 78%;
  min-width: 78%;
}
.ras-block-actions-container[data-v-54b868be] {
  white-space: nowrap;
  overflow: hidden;
  width: 9%;
  min-width: 9%;
  display: -webkit-inline-box;
  margin-left: 3px;
}
.ras-tweet-button-container[data-v-54b868be] {
  display: none;
  display: -webkit-inline-box; /* comment this out if you don't want to show tweet icon */
  float: left;
  margin-left: 3px;
}
.ras-copy-button-container[data-v-54b868be] {
  float: left;
  margin-left: 0px;
  width: 15px;
  display: -webkit-inline-box;
}
.ras-time-action-container-block[data-v-54b868be] {
  overflow: hidden;
  white-space: nowrap;
  display: -webkit-inline-box;
  width: 150px;
  margin-left: 2px;
}```

### **简化query样式，隐藏query的Title**
#### ```css
/* RR change: moved this section to top of CSS for user options
*/
.rm-query {
  border: 0.5px solid #bfccd6;
  padding-bottom: var(--s1);
  border-top-left-radius: 7px;
  border-top-right-radius: 7px;
  border-radius: 7px;
}
.rm-query .rm-query-title {
  color: var(--primary-color);
  background-color: var(--background-color);
  padding: var(--s1);
  font-size: .8em;
  border-top-left-radius: 7px;
  border-top-right-radius: 7px;
} 
--no-query-results: "Query returned no results";
  --no-query-results-color: #FC5963;
  --query-results-border: #f2c98f1a;
/* ----------------------------------------- */
/* RR change: QUERIES - Query results options */

/* Show empty query message */
.rm-block-text .rm-reference-main .rm-mentions:empty:after {
  content: var(--no-query-results);
  color: var(--no-query-results-color);
  font-family: var(--main-font);
  padding: var(--s1);
}
.rm-query {
  /* border: 0.5px solid #38332e; */
  padding-bottom: var(--s1);
  /* border-top-left-radius: 7px;
  border-top-right-radius: 7px; */
  border-radius: 7px;
  border: 0.75px solid var(--query-results-border);
}
.rm-query .rm-query-title {
  /* color: #508bb5; */
  /* background-color: #38332e; */
  padding: var(--s1);
  font-size: .8em;
  border-top-left-radius: 7px;
  border-top-right-radius: 7px;
  background-color: var(--reference-item-bg);
  color: var(--breadcrumb-color);
}

/*RR change: HIDE QUERY SCRIPT - Comment/uncomment to hide the original query and revert back to legacy behavior */

/* 
.rm-query .rm-query-title {
  display: none;
}
 */

/* RR change: MINIMIZE QUERIES: add any one of the following tags before the beginning of your query (in the same block):

    #min-title = hides the page reference link / page title
    #min-con = hides the contextual reference information (breadcrumbs)
    #minimal = hides both the title and the context
    #min-q = hides the query string, similar to legacy behavior
    #min-all = hides everything — title, context, and query string

inspired by Matt Goldenberg */

[data-tag="minimal"], 
[data-tag="minimal"] + .rm-query .rm-title-arrow-wrapper,
[data-tag="minimal"] + .rm-query .zoom-mentions-view {
  display:none!important; /* hide page reference (title) and mention context (breadcrumbs) */
}
[data-tag="min-title"], [data-tag="min-title"] + .rm-query .rm-title-arrow-wrapper {
display:none!important; /* hide page reference (title) */
}
[data-tag="min-con"], [data-tag="min-con"] + .rm-query .zoom-mentions-view {
  display:none !important;  /* hide mention context (breadcrumbs) */
}
[data-tag="min-q"], 
[data-tag="min-q"] + .rm-query .rm-query-title {
  display:none !important;  /* hide the query string */
}
[data-tag="min-all"], 
[data-tag="min-all"] + .rm-query .zoom-mentions-view,
[data-tag="min-all"] + .rm-query .rm-title-arrow-wrapper,
[data-tag="min-all"] + .rm-query .rm-query-title {
  display:none !important;  /* hide everything */
}
[data-tag="minimal"] + .rm-query .rm-query-title::after,
[data-tag="min-title"] + .rm-query .rm-query-title::after,
[data-tag="min-con"] + .rm-query .rm-query-title::after{
  content: " #minimal" /* add a tag to the query string to indicate this query has been minimized */
}
.rm-zoom .parent-path-wrapper .rm-query {
  display: none;
}
```

#### ```css
.rm-query-title {
      font-size: 0px !important;
      &:after {
         font-size: 14px;
         content: "Query";
      }
   }```

### **嵌套链接**
#### ```css
:root {
    --custom-background-color: lightsteelblue;
    --custom-background-color-hover: orange;
    }


.rm-page-ref-link-color{
   color:black !important;
    background: linear-gradient(0deg, var(--custom-background-color) 2px, white 1px, transparent 1px);
    background-position: 0 100%;
    line-height: 24px;
    padding-bottom: 4px;
}

.rm-page-ref-link-color:hover{
   color:black !important;
    background: linear-gradient(0deg, var(--custom-background-color-hover) 2px, white 1px, transparent 1px);
    background-position: 0 100%;
    text-decoration: none;
    line-height: 24px;
    padding-bottom: 4px;
}

.rm-page-ref-link-color .rm-page-ref-link-color {
color: black !important;
  background: linear-gradient(0deg, var(--custom-background-color) 2px, white 1px, transparent 1px);
    background-position: 0 100%;
   line-height: 28px;
    padding-bottom: 8px;
}

.rm-page-ref-link-color .rm-page-ref-link-color:hover {
color: black !important;
  background: linear-gradient(0deg, var(--custom-background-color-hover) 2px, white 1px, transparent 1px);
    background-position: 0 100%;
   line-height: 28px;
    padding-bottom: 8px;
}


.rm-page-ref-link-color .rm-page-ref-link-color .rm-page-ref-link-color {
color: black !important;
background: linear-gradient(0deg, var(--custom-background-color) 2px, white 1px, transparent 1px);
    background-position: 0 100%;
   line-height: 32px;
    padding-bottom: 12px;
}


.rm-page-ref-link-color .rm-page-ref-link-color .rm-page-ref-link-color:hover {
color: black !important;
background: linear-gradient(0deg, var(--custom-background-color-hover) 2px, white 1px, transparent 1px);
    background-position: 0 100%;
   line-height: 32px;
    padding-bottom: 12px;
}

```

### **Customizing Nested Tables and embeds(自定义嵌套表和嵌入)**
#### ```css
/* don't limit the block width for tables */
.rm-block-text {
    max-width: none!important;
}

/* clean up tables embedded in tables and blocks within tables */
.roam-table, .roam-table th, .roam-table td, .roam-table tr {
    padding:0!important;
    vertical-align: top;
    min-width:auto!important;
    overflow: hidden;
}

.roam-table .roam-table table {
    width:100%;
}

.roam-table .rm-block-ref {
    padding:0!important;
}

.roam-table .rm-embed-container {
    background-color:transparent!important;
    padding-bottom:20px;
}

.roam-table .rm-embed-edit, .roam-table .bp3-popover-wrapper {
    display:none!important;
}

.roam-table .controls .block-expand .rm-caret {
    transition:none!important;
}

.rm-embed-inner-block-hide:hover {
    margin-left:-42px!important;
}

.roam-table .roam-table th, .roam-table  .roam-table td, .roam-table  .roam-table tr {
    border-bottom:0;
    border-left:0;
    border-top:0;
}```

### **Alias page underlined**
#### ```css
.rm-alias-page{
   color:black !important;
    background: linear-gradient(0deg,  rgb(189,111,48) 2px, white 1px, transparent 1px);
    background-position: 0 100%;
    line-height: 24px;
    padding-bottom: 4px;
}

.rm-alias-page:hover{
   color:black !important;
    background: linear-gradient(0deg, orange 2px, white 1px, transparent 1px);
    background-position: 0 100%;
    text-decoration: none;
    line-height: 24px;
    padding-bottom: 4px;
}```

### **Alias block underlined**
#### ```css
.rm-alias-block{
   color:black !important;
    background: linear-gradient(0deg,  #9C27B0 2px, white 1px, transparent 1px);
    background-position: 0 100%;
    line-height: 24px;
    padding-bottom: 4px;
}

.rm-alias-block:hover{
   color:black !important;
    background: linear-gradient(0deg, orange 2px, white 1px, transparent 1px);
    background-position: 0 100%;
    text-decoration: none;
    line-height: 24px;
    padding-bottom: 4px;
}```

### **双链样式**
#### ```css
/* Page link */
.rm-page-ref-link-color {
    color: #106ba3 !important;
    font-weight: 800;
}```

### **Make wide**
#### ```css
[data-tag="make:wide"] ~ div {
	width: 110% !important;
}

[data-tag="make:wide-x"] ~ div {
	width: 120% !important;	
}

[data-tag="make:wide-xx"] ~ div {
	width: 130% !important;	
}

[data-tag="make:wide-xxl"] ~ div {
	width: 150% !important;
}


[data-tag="make:wide-on-hover"] ~ div:hover {
  transform: scale(1.5); 
}

[data-tag*="make:wide"] ~ div div:nth-child(2){
	width: 100% !important;
}



[data-tag="make:long"] ~ div {
	height: 660px !important;
}

[data-tag="make:long-x"] ~ div {
	height: 760px !important;
}

[data-tag="make:long-xx"] ~ div {
	height: 860px !important;
}

[data-tag="make:long-xxl"] ~ div {
	height: 960px !important;
}


[data-tag*="make:long"] ~ div div:nth-child(2){
	height: 100% !important;
}```

### **YouTube Timestamp-Play-Button**
#### ```css
.timestamp-control{
  background-color: rgba(108,109,36,0.1); 
  color: rgb(251,106,13);
  margin-right: 5px;
  margin-top: 3px;
  margin-bottom: 3px;
  border-radius: '90%';
  border-style: inset;  
  border-color: #FF3200;
  font-size: 0.9em;
}
.timestamp-control:hover {
  background-color: rgba(108,109,36,0.25); 
  border-style: outset;  
  color: #FFFFFF;
}```

### **Checkbox**
#### ```css


[data-tag="table:project"] + div > .roam-table table {
   border-collapse: separate;
  border: 1px solid black;


  
}

[data-tag="table:project"] + div > .roam-table table tr {
 border: 0px solid #4CAF50;
 padding: 0px;
} 

[data-tag="table:project"] + div > .roam-table table td {
 border: 0px solid #4CAF50;

} 


tr[data-checked-tr="false"] {
  background-color: rgb(253,253,253);
  
}

tr[data-checked-tr="true"] {
   background-color: rgb(220,249,213);
}

 
tr[data-display="table-row"] {
  display: table-row;
}

tr[data-display="table-row"] > td:nth-child(1) {
 

}

/*
tr[data-display="table-row"] > td:nth-child(1) > span:before {
  content: " - "

  
}*/

tr[data-display="none"] {
  display: none;
}```

### **Unlink finder**
#### ```css
.exact-word-match.unlink-finder,
.unlink-finder-legend.exact-word-match.unlink-finder {
  background-color: darkgreen;
  border-radius: 2px;
  text-decoration: none !important;
}
.fuzzy-word-match.unlink-finder,
.unlink-finder-legend.fuzzy-word-match.unlink-finder {
  background-color:  darkorange !important;
  text-decoration: none !important;
}
.partial-word-match.unlink-finder,
.unlink-finder-legend.partial-word-match.unlink-finder {
  background-color:  brown !important;
  text-decoration: none !important;
}
.redundant-word-match.unlink-finder,
.unlink-finder-legend.redundant-word-match.unlink-finder {
  background-color: slategrey !important;
  text-decoration: none !important;
}```

### 添加滑动条（失效）
#### ```clojure
/* Scrollbar improvements HT: Palash Karia
Mobile scrollable right sidebar in portrait mode

参考资料:
- https://abhayprasanna.github.io/better-dark-age.css
- https://segmentfault.com/a/1190000003708894
*/

/* 修改滑块颜色 */
@media (prefers-color-scheme: light){
	:root {
    --closed-bullets: #2E2E2E77;
    --icons-hover: #E4564A;
  	}
}
/* ------ */

div::-webkit-scrollbar-track {
  background-color: transparent !important;
}

div::-webkit-scrollbar {
  width        : 5px;
  height       : 5px;
  border-radius: 8px;
}

div::-webkit-scrollbar-track {
  background   : transparent;
  border-radius: 20px;
}

div::-webkit-scrollbar-thumb {
  background-color: var(--closed-bullets)!important;
}

div::-webkit-scrollbar-thumb:hover {
  background-color: rgba(0,0,0,0.4);
  border          : 5px var(--icons-hover) solid;
}

/* Compact borderless references and queries */

.rm-reference-item {
  padding: 0 !important;
  margin : 0 !important;
  border : 0 !important;
}

.rm-ref-page-view {
  padding-bottom: 10px !important;
}

.flex-h-box.rm-title-arrow-wrapper {
  padding-bottom: 3px !important;
}


/* Mobile scrollable right sidebar in portrait mode */

@media only screen and (max-width: 600px) {
  .roam-body {
    overflow-x: scroll !important;
    display   : flex;
  }

  .roam-main {
    min-width: 95vw;
  }

  #right-sidebar[style*="flex: 0 0 40%;"] {
    flex: 0 0 95% !important;
  }
}
/*---------------------------------------------------------------------------*/```

### 其他
#### 图像相关
##### ```clojure
.react-resizable-handle {
	display:none;
	z-index:20;
	
}

.react-resizable-handle:hover {
	display: block !important;
	z-index: 20;
	
}

.rm-resize-img:hover .react-resizable-handle {
	display: block !important;
	
}```

#### 表格
##### ```clojure
.rm-block-text {
    max-width: 900px!important;
         font-size: 15px !important;
}```

#### 字体
##### ```clojure
body {
  font-size: 16px;
}
body, html, a, div, textarea {
  font-family: "Iowan Old Style", serif, "PingFang SC", -apple-system, "SF UI Text", "Lucida Grande", STheiti, "Microsoft YaHei", sans-serif !important;
}```

#### 两端对齐
##### ```clojure
.roam-block {
    text-align: justify;
}```

#### **修复**
##### ```css
/* chrome浏览器 4240.111 版本上 出现了 auto的兼容性问题 */
#all-pages-search {
    max-height: calc(100%);
    overflow-y: auto;
 height:100% !important;
}
.rm-pages-col-word-count > span:first-child, .rm-pages-col-word-count + div > span:first-child {
display: none;
}```

#### 黄底黑字高亮
##### ```clojure
    text-shadow: 0px 1px 2px #c6c0c0;
    background-color:#FFEB3B;
    padding: 3px 7px;
    line-height: 2em;```

#### Sidebar标题颜色
##### ```clojure
a {
/*color: #0D0D0C;*/
/* #4f718f; */
  font-weight:500 !important;
   font-size: 33px;
  padding: 3px 7px;
}
```

#### 全局标签设计
##### ```clojure
/* Hashtags */
.rm-page-ref-tag {
    color: #F8F8F8 !important;
    font-weight: 500;
    background-color: #4CAF5087;
    border-radius: 7px;
    padding: 1px 5px 2px;
}```

##### 

#### 预览
##### ```clojure
/* 主页面padding */
.roam-article > div {
    padding: 20px 10px 30px 30px;
}
.rm-block-text {
  max-width: 680px!important;
}

/* 侧边栏padding */
#roam-right-sidebar-content > div > div:not(.flex-h-box) {
    padding: 0px 20px 0px 20px;
}
#roam-right-sidebar-content > * > div:last-child:not(:first-child) {
    border-radius: 0px 0px 10px 10px;
    padding-bottom: 30px !important;
    width: var(--page-width);
}```

#### 黑暗模式（BetterRoamresearch）
##### ```clojure
:root {
    --font-size: 15.5px;
    --font-color: hsl(205, 23%, 16%);
    --font-color-lighter: hsl(0, 0%, 40%);
    --font-color-placeholder: hsl(0, 0%, 70%);
    --link-color: hsl(203, 82%, 35%);
    --border-color: rgba(0, 0, 0, 0.08);
    --subtle-border-color: rgba(0, 0, 0, 0.05);
    --main-background-color: hsl(210, 9%, 98%);
    --body-background-color: #ffffff;
    --popup-background-color: #ffffff;
    --reference-item-background: hsl(0, 0%, 99%);
    --brackets-color: rgba(0, 0, 0, 0.25);
    --empty-text-color: hsl(203, 12%, 75%);
}

body,
.roam-body,
.roam-app,
.rm-pages-title-text,
.bp3-button {
    color: var(--font-color) !important;
}

h1 {
    color: var(--font-color) !important;
}

.rm-page-ref-link-color {
    color: var(--link-color) !important;
}

.rm-page-ref-brackets {
    color: var(--brackets-color) !important;
}

.bp3-input {
    background: var(--body-background-color) !important;
    &::placeholder {
        color: var(--font-color-placeholder) !important;
    }
}

.bp3-elevation-3,
.confirmation-content-dialog,
.bp3-dialog {
    background: var(--popup-background-color) !important;
}

.rm-title-untitled,
#block-input-ghost > span,
textarea::placeholder {
    color: var(--empty-text-color) !important;
}

.rm-all-pages .table .rm-pages-row.rm-pages-row-header {
    background: var(--main-background-color) !important;
}

body,
div,
textarea,
.level2 {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell,
        'Open Sans', 'Helvetica Neue', sans-serif !important;
}

iframe {
    border: none !important;
}

.loading-astrolabe {
    position: absolute !important;
    width: 80px !important;
    height: 80px !important;
    opacity: 0.3 !important;
    top: calc(50% - 40px) !important;
    left: calc(50% - 40px) !important;
}

#roam-sidebar-logo {
    display: none !important;
}

body,
#app {
    background: var(--main-background-color) !important;
}

.roam-center {
    border-left: 1px solid var(--border-color) !important;
    border-top: 1px solid var(--border-color) !important;
    border-right: 1px solid var(--border-color) !important;
    border-radius: 6px;
    box-shadow: 0px 2px 14px rgba(0, 0, 0, 0.04) !important;
    overflow: visible !important;
    background: var(--body-background-color) !important;
    margin-right: 12px;
    margin-left: 12px;
}

// .roam-article {
//     border-left: 1px solid var(--border-color) !important;
//     border-top: 1px solid var(--border-color) !important;
//     border-right: 1px solid var(--border-color) !important;
//     border-radius: 8px;
//     box-shadow: 0px 2px 8px rgba(0, 0, 0, 0.5) !important;
//     overflow: visible !important;
//     background: var(--body-background-color) !important;
//     margin-right: 10px;
// }

.roam-topbar {
    background: var(--main-background-color) !important;
    border-bottom: none !important;
    input#find-or-create-input {
        box-shadow: none !important;
        border: 1px solid var(--border-color) !important;
    }
}

.roam-body,
.roam-topbar,
#right-sidebar,
.roam-sidebar-container {
    background: var(--main-background-color) !important;
}

#right-sidebar {
    border: none !important;
    transition: none !important;
    overflow: hidden !important;
    h1 {
        font-size: 18px !important;
    }
    #roam-right-sidebar-content {
        > div[style] {
            border-bottom: 1px solid var(--subtle-border-color) !important;
        }
    }
    .hoverparent,
    .react-resizable {
        max-width: 100% !important;
        img {
            max-width: 100% !important;
        }
    }
}

.rm-page-ref-tag {
    color: #9099a1 !important;
}

span.checkmark {
    top: -2px;
}

.rm-level1 {
    div,
    textarea {
        font-size: 22px !important;
        line-height: 1.5 !important;
    }
}

.rm-level2 {
    div,
    textarea {
        font-size: 20px !important;
        line-height: 1.5 !important;
    }
}

.rm-level3 {
    div,
    textarea {
        font-size: 18px !important;
        line-height: 1.5 !important;
    }
}

.level2 {
    font-weight: inherit !important;
}

// .roam-body .roam-app .roam-sidebar-container {
//     background-color: var(--main-background-color) !important;
//     box-shadow: none !important;
// }

.roam-log-container .roam-log-page {
    border-top: 1px solid var(--subtle-border-color) !important;
    &:first-child {
        min-height: 0 !important;
        border-top: none !important;
    }
}

.rm-reference-item {
    background: var(--reference-item-background) !important;
    border: 1px solid var(--subtle-border-color) !important;
    border-radius: 6px !important;
    padding: 8px 10px 8px 2px !important;
    .rm-block-text {
        font-size: var(--font-size) !important;
    }
}

.CodeMirror {
    font-size: 13px !important;
}

.roam-body .roam-app .roam-sidebar-container .roam-sidebar-content .log-button:hover,
.roam-body
    .roam-app
    .roam-sidebar-container
    .roam-sidebar-content
    .starred-pages-wrapper
    .starred-pages
    .page:hover {
    background-color: transparent !important;
    color: var(--font-color) !important;
}

.roam-body .roam-app .roam-sidebar-container .roam-sidebar-content .log-button,
.roam-body .roam-app .roam-sidebar-container .roam-sidebar-content .starred-pages-wrapper,
.roam-body
    .roam-app
    .roam-sidebar-container
    .roam-sidebar-content
    .starred-pages-wrapper
    .starred-pages
    .page,
.bp3-minimal > div {
    color: var(--font-color-lighter) !important;
    font-size: 13px !important;
}

.roam-sidebar-content {
    padding: 0 !important;
    > div:not(.log-button):not(:first-child) {
        padding: 0 !important;
    }
    > div:first-child {
        padding-bottom: 18px !important;
    }
    div {
        line-height: 1.2 !important;
    }
    .rm-db-title {
        margin-top: 0 !important;
        color: var(--font-color-lighter) !important;
    }
}

// Sidebar separator and Shortcuts header
.starred-pages-wrapper {
    > div:first-child {
        display: none;
    }
    .flex-h-box,
    .flex-h-box span {
        font-size: 13px !important;
        opacity: 0.6 !important;
    }
}

.roam-body .roam-app .roam-sidebar-container .roam-sidebar-content .log-button,
.roam-body
    .roam-app
    .roam-sidebar-container
    .roam-sidebar-content
    .starred-pages-wrapper
    .starred-pages
    .page {
    padding: 6px 24px 6px !important;
}
.bp3-icon-small {
    padding-left: 24px !important;
}

.rm-block-text {
    max-width: 640px !important;
    font-size: var(--font-size) !important;
}

.block-bullet-view {
    margin-bottom: 3px !important;
}

.roam-article > div > div h1 {
    font-size: 26px !important;
    font-weight: 700 !important;
    height: auto !important;
    line-height: 1.5 !important;
}

.rm-title-display,
.rm-title-textarea {
    height: auto !important;
    line-height: 1.5 !important;
}

.roam-log-container .roam-log-preview h1 {
    font-size: 22px !important;
    font-weight: 700 !important;
}

strong {
    font-weight: 700 !important;
}

.block-border-left {
    border-left-color: var(--subtle-border-color) !important;
}

.rm-reference-main {
    div > strong {
        color: hsl(0, 0%, 50%) !important;
    }
}

// Dark Mode

@media (prefers-color-scheme: dark) {
    body {
        background: hsl(113, 0%, 9%) !important;
    }
    #app {
        // filter: invert(1) hue-rotate(180deg) !important;
    }
    img,
    div#buffer,
    .bp3-portal,
    .intercom-app,
    .loading-astrolabe,
    .bp3-dialog,
    .twitter-tweet,
    iframe {
        // filter: invert(1) hue-rotate(180deg) !important;
    }
    .roam-highlight {
        background-color: hsl(51, 50%, 18%) !important;
    }
    .bp3-overlay-backdrop {
        background-color: rgba(0, 0, 0, 0.7) !important;
    }
    :root {
        --font-color: hsl(205, 0%, 98%);
        --font-color-lighter: hsl(0, 0%, 50%);
        --font-color-placeholder: hsl(0, 0%, 36%);
        --link-color: hsl(203, 62%, 55%);
        --border-color: rgba(255, 255, 255, 0.07);
        --subtle-border-color: rgba(255, 255, 255, 0.05);
        --main-background-color: hsl(0, 0%, 4%);
        --body-background-color: hsl(0, 0%, 10%);
        --popup-background-color: hsl(0, 0%, 14%);
        --reference-item-background: hsl(0, 0%, 8%);
        --brackets-color: rgba(255, 255, 255, 0.3);
        --empty-text-color: hsl(203, 5%, 70%);
    }
}```

#### 左右等宽
##### ```clojure
"/* Split Screen CSS for Roam */
/* "Assembled" and tweaked by @DavidCrandall */
/* https://davidcrandallwrites.com */


/* change main font */

body,
html,
div,
textarea {
font-family: -apple-system, BlinkMacSystemFont, sans-serif;
}

/* change font for all headings */

h1,
h1 div,
h1 textarea,
.rm-level1 div,
#right-sidebar .rm-level2, /* page headings in right sidebar */
.rm-reference-main .rm-level3 , /* page headings in referenced items */
.rm-level1 textarea,
.roam-log-preview h1,
h1.rm-title-display,
h1.rm-title-display textarea,
.level1,
.level2 {
--font-family: "Fira Code", Menlo, monospace;
font-family: -apple-system, BlinkMacSystemFont, sans-serif;
font-weight: 500 !important;
--letter-spacing: -0.08em;
}

h2,
h2 div,
h2 textarea,
h3,
h3 div,
h3 textarea {
--font-family: "Fira Code", Menlo, monospace;
font-family: -apple-system, BlinkMacSystemFont, sans-serif;
color: #9E9E9E !important;
}

a {
color: #106ba3;
font-weight:500 !important;
/* #4f718f; */
}

/* less space below page heading */

.roam-body .roam-app .roam-main .roam-article .rm-title-display {
margin-bottom: 10px;
}


h1.level2 {
font-size: 36px !important;
}

/* Main block - remove centering */

.roam-center {
--align-item: left;
flex-basis: 40% !important;
}



/* lighter bullets */

#right-sidebar .controls .roam-bullet-closed,
.controls .roam-bullet-closed {
background: none;
border: 1px solid #333;
}

.simple-bullet-inner {
opacity: 0.3;
}

/* lighter vertical guides */

.block-border-left {
border-color: #eee;
}


.roam-block-container h1 {
font-weight: 300;
font-size: 26px;
color: black;
}

.roam-block-container h2 {
font-weight: 600;
font-size: 18px;
color: black;
}

/* align checkboxes better */

label.check-container {
margin-bottom: 11px;
margin-right: 3px;
}

/* align checkboxes in zoomed-in headings */

.rm-level1 label.check-container {
margin-bottom: 17px;
margin-right: -3px;
}

/* don't shrink block references */

.rm-block-ref {
font-size: 1em;
padding: 0;
margin: 0;
}

.rm-block-ref label.check-container {
margin-bottom: 12px;
}



/* don't need "SHORTCUTS" heading */

.starred-pages-wrapper .flex-h-box {
display: none;
}

.starred-pages-wrapper > div:first-child {
margin: 0 -18px;
}

/* more subtle logo */

#roam-sidebar-logo img {
opacity: 0.4;
}
#roam-sidebar-logo span {
display: none;
}

/* fade loading astrolabe */

.loading-astrolabe img {
opacity: 0.2;
}

/* lighter sidebar background */

#right-sidebar {
background-color: rgba(216, 225, 232, 0.2) !important;
/* rgba(216, 225, 232, 0.3) */
border-left: 1px solid #ddd !important;
}

/* sidebar sections */

#roam-right-sidebar-content > div {
border-bottom: 1px solid #ddd !important;
margin: 0 !important;
padding: 10px 4px 10px 50px;
}

/* sidebar section headings */

#roam-right-sidebar-content > div > div:first-child {
margin-left: -10px;
}

/* rule under top section of left sidebar */

.roam-sidebar-content > div:first-child {
padding: 4px 16px !important;
margin-bottom: 8px;
border-bottom: 1px solid rgb(57, 75, 89);
}

/* rule under topbar */

.roam-topbar {
border-bottom: 1px solid #eee;
}

/* crumbs */

.rm-reference-item
> div:first-child
> div:first-child
div
span:not(.bp3-icon-chevron-right),
.roam-article
> div:first-child:not(.roam-log-container)
> div:first-child
div
span:not(.bp3-icon-chevron-right) {
font-size: 12px;
line-height: 1.3;
color: #bbb !important;
/* truncate to smaller width, use css for ellipsis */
--max-width: 1000px;
white-space: nowrap;
overflow: hidden;
text-overflow: ellipsis;
padding: 2px !important;
}

.rm-reference-item
> div:first-child
> div:first-child
div
span:hover:not(.bp3-icon-chevron-right),
.roam-article
> div:first-child:not(.roam-log-container)
> div:first-child
div
span:hover:not(.bp3-icon-chevron-right) {
color: black !important;
}

/* chevrons in crumbs */

.roam-reference-item > div > div:first-child .bp3-icon-chevron-right,
.roam-article
> div
> div:first-child:not(.roam-log-container)
.bp3-icon-chevron-right {
font-size: 1em;
margin: 0 3px;
color: #ddd !important;
}

/* no checkboxes in crumbs */

.roam-reference-item
> div:first-child:not(.roam-log-container)
> div:first-child
label.check-container,
.roam-article
> div:first-child:not(.roam-log-container)
> div:first-child
label.check-container {
display: none;
}

/* link buttons for referenced items */

.rm-reference-main button {
border: 1px solid #eee;
border-radius: 0.3em;
font-size: 0.8em;
}



/* referenced item section headings */

.rm-reference-main {
--border-top: 1px solid #ededed;
}

.flex-h-box {
padding-top: 0px !important;
}

.rm-reference-main .flex-h-box {
min-height: 30px;
}

.rm-reference-main strong {
color: #E91E63;
font-size: 0.8em;
--background-color: rgba(216, 225, 232, 0.3);
}

/* remove background from referenced items */

.rm-reference-item {
padding: 6px 0 0 0;
margin: 6px 0 0 0;
border-top: 1px solid #eee;
background: none;
}

/* slightly bigger page headings under referenced items */
.rm-reference-main .rm-level3 {
font-size: 1.6em;
}

/* search */

.rm-find-or-create-wrapper {
flex: 0 1 100% !important;
}

.rm-find-or-create-wrapper .bp3-input {
border: none !important;
box-shadow: none !important;
}



/* links */

a.rm-alias.rm-alias-external {


.rm-page-ref-link-color {
	```

#### sidebar折叠功能
##### ```clojure

/**
 use variables to control colors, size.
 delete the part below comment to remove any behaviour
**/
:root {
    /** update colors for dark themes here */
    --roamer-sb-bg: #f7f8fa;
    --roamer-sb-card-bg: white;
    --roamer-sb-card-border: #e4e9ec;
    --roamer-sb-card-width: 600px;
    /* leave blank for no prefix */
    --roamer-sb-card-page-prefix: "Page "; 
}

.roam-center {
    /* sidebar-to-content-ratio */
    flex-basis: 50% !important;
}


#right-sidebar > div {
    background-color: var(--roamer-sb-bg);
}
/* sidebar layout */
#right-sidebar #roam-right-sidebar-content {
    overflow: auto !important;
    white-space: normal;
    display: flex;
    align-content: flex-start;
    flex-direction: row;
    height: 100%
}

#right-sidebar #roam-right-sidebar-content > div {
    min-width: var(--roamer-sb-card-width);
    background-color: var(--roamer-sb-card-bg);
    border: 1px solid var(--roamer-sb-card-border) !important;
    /* card layout */
    display: flex;
    flex-direction: column;
    padding: 12px;
    border-radius: 4px;
    align-self: flex-start;
    margin-right: 0px !important;
    height: 100% !important;
}

#right-sidebar #roam-right-sidebar-content > div > div:nth-child(2) {
    /* adds scrollbar to card content */
    overflow: auto;
    padding: 0 8px 8px 8px !important;
}

/* sticky */
#right-sidebar #roam-right-sidebar-content > div {
    position: sticky;
    left: 16px
}

/* page numbers */
#right-sidebar #roam-right-sidebar-content {
    counter-reset: page;
}
#right-sidebar #roam-right-sidebar-content > div > div:nth-child(1):before {
    counter-increment: page;
    content: var(--roamer-sb-card-page-prefix) counter(page);
    padding: 0px 4px;
    display: flex;
    align-items: center;
    z-index: 1;
}

/** brings card to top on focus */
#right-sidebar #roam-right-sidebar-content > div:focus-within {
    z-index: 100;
}```

#### RoamZenithJs
##### ```php
 /* don't limit the block width */
 .rm-block-text {
     max-width: none!important;
 }
 .ghost{
     opacity: .5;
     background: #C8EBFB;
 }
 .highlight{
     background-color: #f9c7c8 !important;
 }
  .selected {
  background-color: #FFEB3B !important;
  z-index: 1 !important;
 }```
