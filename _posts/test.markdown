---
layout: post
title: Trend trading commodities in python
excerpt: "..."
modified: 
categories: 
excerpt:
tags: [science]
image:
  feature:
date: 2017-01-17T20:18:11-07:00
---
date: 2017-01-17

<!DOCTYPE html>
<html>
<head><meta charset="utf-8" />
<title>2017-01-16-Trend-trading-commodities-in-python</title><script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.0.3/jquery.min.js"></script>

<style type="text/css">
    /*!
*
* Twitter Bootstrap
*
*/
/*!
 * Bootstrap v3.3.6 (http://getbootstrap.com)
 * Copyright 2011-2015 Twitter, Inc.
 * Licensed under MIT (https://github.com/twbs/bootstrap/blob/master/LICENSE)
 */
/*! normalize.css v3.0.3 | MIT License | github.com/necolas/normalize.css */
html {
  font-family: sans-serif;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
}
body {
  margin: 0;
}
article,
aside,
details,
figcaption,
figure,
footer,
header,
hgroup,
main,
menu,
nav,
section,
summary {
  display: block;
}
audio,
canvas,
progress,
video {
  display: inline-block;
  vertical-align: baseline;
}
audio:not([controls]) {
  display: none;
  height: 0;
}
[hidden],
template {
  display: none;
}
a {
  background-color: transparent;
}
a:active,
a:hover {
  outline: 0;
}
abbr[title] {
  border-bottom: 1px dotted;
}
b,
strong {
  font-weight: bold;
}
dfn {
  font-style: italic;
}
h1 {
  font-size: 2em;
  margin: 0.67em 0;
}
mark {
  background: #ff0;
  color: #000;
}
small {
  font-size: 80%;
}
sub,
sup {
  font-size: 75%;
  line-height: 0;
  position: relative;
  vertical-align: baseline;
}
sup {
  top: -0.5em;
}
sub {
  bottom: -0.25em;
}
img {
  border: 0;
}
svg:not(:root) {
  overflow: hidden;
}
figure {
  margin: 1em 40px;
}
hr {
  box-sizing: content-box;
  height: 0;
}
pre {
  overflow: auto;
}
code,
kbd,
pre,
samp {
  font-family: monospace, monospace;
  font-size: 1em;
}
button,
input,
optgroup,
select,
textarea {
  color: inherit;
  font: inherit;
  margin: 0;
}
button {
  overflow: visible;
}
button,
select {
  text-transform: none;
}
button,
html input[type="button"],
input[type="reset"],
input[type="submit"] {
  -webkit-appearance: button;
  cursor: pointer;
}
button[disabled],
html input[disabled] {
  cursor: default;
}
button::-moz-focus-inner,
input::-moz-focus-inner {
  border: 0;
  padding: 0;
}
input {
  line-height: normal;
}
input[type="checkbox"],
input[type="radio"] {
  box-sizing: border-box;
  padding: 0;
}
input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button {
  height: auto;
}
input[type="search"] {
  -webkit-appearance: textfield;
  box-sizing: content-box;
}
input[type="search"]::-webkit-search-cancel-button,
input[type="search"]::-webkit-search-decoration {
  -webkit-appearance: none;
}
fieldset {
  border: 1px solid #c0c0c0;
  margin: 0 2px;
  padding: 0.35em 0.625em 0.75em;
}
legend {
  border: 0;
  padding: 0;
}
textarea {
  overflow: auto;
}
optgroup {
  font-weight: bold;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
}
td,
th {
  padding: 0;
}
/*! Source: https://github.com/h5bp/html5-boilerplate/blob/master/src/css/main.css */
@media print {
  *,
  *:before,
  *:after {
    background: transparent !important;
    color: #000 !important;
    box-shadow: none !important;
    text-shadow: none !important;
  }
  a,
  a:visited {
    text-decoration: underline;
  }
  a[href]:after {
    content: " (" attr(href) ")";
  }
  abbr[title]:after {
    content: " (" attr(title) ")";
  }
  a[href^="#"]:after,
  a[href^="javascript:"]:after {
    content: "";
  }
  pre,
  blockquote {
    border: 1px solid #999;
    page-break-inside: avoid;
  }
  thead {
    display: table-header-group;
  }
  tr,
  img {
    page-break-inside: avoid;
  }
  img {
    max-width: 100% !important;
  }
  p,
  h2,
  h3 {
    orphans: 3;
    widows: 3;
  }
  h2,
  h3 {
    page-break-after: avoid;
  }
  .navbar {
    display: none;
  }
  .btn > .caret,
  .dropup > .btn > .caret {
    border-top-color: #000 !important;
  }
  .label {
    border: 1px solid #000;
  }
  .table {
    border-collapse: collapse !important;
  }
  .table td,
  .table th {
    background-color: #fff !important;
  }
  .table-bordered th,
  .table-bordered td {
    border: 1px solid #ddd !important;
  }
}
@font-face {
  font-family: 'Glyphicons Halflings';
  src: url('../components/bootstrap/fonts/glyphicons-halflings-regular.eot');
  src: url('../components/bootstrap/fonts/glyphicons-halflings-regular.eot?#iefix') format('embedded-opentype'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.woff2') format('woff2'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.woff') format('woff'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.ttf') format('truetype'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.svg#glyphicons_halflingsregular') format('svg');
}
.glyphicon {
  position: relative;
  top: 1px;
  display: inline-block;
  font-family: 'Glyphicons Halflings';
  font-style: normal;
  font-weight: normal;
  line-height: 1;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.glyphicon-asterisk:before {
  content: "\002a";
}
.glyphicon-plus:before {
  content: "\002b";
}
.glyphicon-euro:before,
.glyphicon-eur:before {
  content: "\20ac";
}
.glyphicon-minus:before {
  content: "\2212";
}
.glyphicon-cloud:before {
  content: "\2601";
}
.glyphicon-envelope:before {
  content: "\2709";
}
.glyphicon-pencil:before {
  content: "\270f";
}
.glyphicon-glass:before {
  content: "\e001";
}
.glyphicon-music:before {
  content: "\e002";
}
.glyphicon-search:before {
  content: "\e003";
}
.glyphicon-heart:before {
  content: "\e005";
}
.glyphicon-star:before {
  content: "\e006";
}
.glyphicon-star-empty:before {
  content: "\e007";
}
.glyphicon-user:before {
  content: "\e008";
}
.glyphicon-film:before {
  content: "\e009";
}
.glyphicon-th-large:before {
  content: "\e010";
}
.glyphicon-th:before {
  content: "\e011";
}
.glyphicon-th-list:before {
  content: "\e012";
}
.glyphicon-ok:before {
  content: "\e013";
}
.glyphicon-remove:before {
  content: "\e014";
}
.glyphicon-zoom-in:before {
  content: "\e015";
}
.glyphicon-zoom-out:before {
  content: "\e016";
}
.glyphicon-off:before {
  content: "\e017";
}
.glyphicon-signal:before {
  content: "\e018";
}
.glyphicon-cog:before {
  content: "\e019";
}
.glyphicon-trash:before {
  content: "\e020";
}
.glyphicon-home:before {
  content: "\e021";
}
.glyphicon-file:before {
  content: "\e022";
}
.glyphicon-time:before {
  content: "\e023";
}
.glyphicon-road:before {
  content: "\e024";
}
.glyphicon-download-alt:before {
  content: "\e025";
}
.glyphicon-download:before {
  content: "\e026";
}
.glyphicon-upload:before {
  content: "\e027";
}
.glyphicon-inbox:before {
  content: "\e028";
}
.glyphicon-play-circle:before {
  content: "\e029";
}
.glyphicon-repeat:before {
  content: "\e030";
}
.glyphicon-refresh:before {
  content: "\e031";
}
.glyphicon-list-alt:before {
  content: "\e032";
}
.glyphicon-lock:before {
  content: "\e033";
}
.glyphicon-flag:before {
  content: "\e034";
}
.glyphicon-headphones:before {
  content: "\e035";
}
.glyphicon-volume-off:before {
  content: "\e036";
}
.glyphicon-volume-down:before {
  content: "\e037";
}
.glyphicon-volume-up:before {
  content: "\e038";
}
.glyphicon-qrcode:before {
  content: "\e039";
}
.glyphicon-barcode:before {
  content: "\e040";
}
.glyphicon-tag:before {
  content: "\e041";
}
.glyphicon-tags:before {
  content: "\e042";
}
.glyphicon-book:before {
  content: "\e043";
}
.glyphicon-bookmark:before {
  content: "\e044";
}
.glyphicon-print:before {
  content: "\e045";
}
.glyphicon-camera:before {
  content: "\e046";
}
.glyphicon-font:before {
  content: "\e047";
}
.glyphicon-bold:before {
  content: "\e048";
}
.glyphicon-italic:before {
  content: "\e049";
}
.glyphicon-text-height:before {
  content: "\e050";
}
.glyphicon-text-width:before {
  content: "\e051";
}
.glyphicon-align-left:before {
  content: "\e052";
}
.glyphicon-align-center:before {
  content: "\e053";
}
.glyphicon-align-right:before {
  content: "\e054";
}
.glyphicon-align-justify:before {
  content: "\e055";
}
.glyphicon-list:before {
  content: "\e056";
}
.glyphicon-indent-left:before {
  content: "\e057";
}
.glyphicon-indent-right:before {
  content: "\e058";
}
.glyphicon-facetime-video:before {
  content: "\e059";
}
.glyphicon-picture:before {
  content: "\e060";
}
.glyphicon-map-marker:before {
  content: "\e062";
}
.glyphicon-adjust:before {
  content: "\e063";
}
.glyphicon-tint:before {
  content: "\e064";
}
.glyphicon-edit:before {
  content: "\e065";
}
.glyphicon-share:before {
  content: "\e066";
}
.glyphicon-check:before {
  content: "\e067";
}
.glyphicon-move:before {
  content: "\e068";
}
.glyphicon-step-backward:before {
  content: "\e069";
}
.glyphicon-fast-backward:before {
  content: "\e070";
}
.glyphicon-backward:before {
  content: "\e071";
}
.glyphicon-play:before {
  content: "\e072";
}
.glyphicon-pause:before {
  content: "\e073";
}
.glyphicon-stop:before {
  content: "\e074";
}
.glyphicon-forward:before {
  content: "\e075";
}
.glyphicon-fast-forward:before {
  content: "\e076";
}
.glyphicon-step-forward:before {
  content: "\e077";
}
.glyphicon-eject:before {
  content: "\e078";
}
.glyphicon-chevron-left:before {
  content: "\e079";
}
.glyphicon-chevron-right:before {
  content: "\e080";
}
.glyphicon-plus-sign:before {
  content: "\e081";
}
.glyphicon-minus-sign:before {
  content: "\e082";
}
.glyphicon-remove-sign:before {
  content: "\e083";
}
.glyphicon-ok-sign:before {
  content: "\e084";
}
.glyphicon-question-sign:before {
  content: "\e085";
}
.glyphicon-info-sign:before {
  content: "\e086";
}
.glyphicon-screenshot:before {
  content: "\e087";
}
.glyphicon-remove-circle:before {
  content: "\e088";
}
.glyphicon-ok-circle:before {
  content: "\e089";
}
.glyphicon-ban-circle:before {
  content: "\e090";
}
.glyphicon-arrow-left:before {
  content: "\e091";
}
.glyphicon-arrow-right:before {
  content: "\e092";
}
.glyphicon-arrow-up:before {
  content: "\e093";
}
.glyphicon-arrow-down:before {
  content: "\e094";
}
.glyphicon-share-alt:before {
  content: "\e095";
}
.glyphicon-resize-full:before {
  content: "\e096";
}
.glyphicon-resize-small:before {
  content: "\e097";
}
.glyphicon-exclamation-sign:before {
  content: "\e101";
}
.glyphicon-gift:before {
  content: "\e102";
}
.glyphicon-leaf:before {
  content: "\e103";
}
.glyphicon-fire:before {
  content: "\e104";
}
.glyphicon-eye-open:before {
  content: "\e105";
}
.glyphicon-eye-close:before {
  content: "\e106";
}
.glyphicon-warning-sign:before {
  content: "\e107";
}
.glyphicon-plane:before {
  content: "\e108";
}
.glyphicon-calendar:before {
  content: "\e109";
}
.glyphicon-random:before {
  content: "\e110";
}
.glyphicon-comment:before {
  content: "\e111";
}
.glyphicon-magnet:before {
  content: "\e112";
}
.glyphicon-chevron-up:before {
  content: "\e113";
}
.glyphicon-chevron-down:before {
  content: "\e114";
}
.glyphicon-retweet:before {
  content: "\e115";
}
.glyphicon-shopping-cart:before {
  content: "\e116";
}
.glyphicon-folder-close:before {
  content: "\e117";
}
.glyphicon-folder-open:before {
  content: "\e118";
}
.glyphicon-resize-vertical:before {
  content: "\e119";
}
.glyphicon-resize-horizontal:before {
  content: "\e120";
}
.glyphicon-hdd:before {
  content: "\e121";
}
.glyphicon-bullhorn:before {
  content: "\e122";
}
.glyphicon-bell:before {
  content: "\e123";
}
.glyphicon-certificate:before {
  content: "\e124";
}
.glyphicon-thumbs-up:before {
  content: "\e125";
}
.glyphicon-thumbs-down:before {
  content: "\e126";
}
.glyphicon-hand-right:before {
  content: "\e127";
}
.glyphicon-hand-left:before {
  content: "\e128";
}
.glyphicon-hand-up:before {
  content: "\e129";
}
.glyphicon-hand-down:before {
  content: "\e130";
}
.glyphicon-circle-arrow-right:before {
  content: "\e131";
}
.glyphicon-circle-arrow-left:before {
  content: "\e132";
}
.glyphicon-circle-arrow-up:before {
  content: "\e133";
}
.glyphicon-circle-arrow-down:before {
  content: "\e134";
}
.glyphicon-globe:before {
  content: "\e135";
}
.glyphicon-wrench:before {
  content: "\e136";
}
.glyphicon-tasks:before {
  content: "\e137";
}
.glyphicon-filter:before {
  content: "\e138";
}
.glyphicon-briefcase:before {
  content: "\e139";
}
.glyphicon-fullscreen:before {
  content: "\e140";
}
.glyphicon-dashboard:before {
  content: "\e141";
}
.glyphicon-paperclip:before {
  content: "\e142";
}
.glyphicon-heart-empty:before {
  content: "\e143";
}
.glyphicon-link:before {
  content: "\e144";
}
.glyphicon-phone:before {
  content: "\e145";
}
.glyphicon-pushpin:before {
  content: "\e146";
}
.glyphicon-usd:before {
  content: "\e148";
}
.glyphicon-gbp:before {
  content: "\e149";
}
.glyphicon-sort:before {
  content: "\e150";
}
.glyphicon-sort-by-alphabet:before {
  content: "\e151";
}
.glyphicon-sort-by-alphabet-alt:before {
  content: "\e152";
}
.glyphicon-sort-by-order:before {
  content: "\e153";
}
.glyphicon-sort-by-order-alt:before {
  content: "\e154";
}
.glyphicon-sort-by-attributes:before {
  content: "\e155";
}
.glyphicon-sort-by-attributes-alt:before {
  content: "\e156";
}
.glyphicon-unchecked:before {
  content: "\e157";
}
.glyphicon-expand:before {
  content: "\e158";
}
.glyphicon-collapse-down:before {
  content: "\e159";
}
.glyphicon-collapse-up:before {
  content: "\e160";
}
.glyphicon-log-in:before {
  content: "\e161";
}
.glyphicon-flash:before {
  content: "\e162";
}
.glyphicon-log-out:before {
  content: "\e163";
}
.glyphicon-new-window:before {
  content: "\e164";
}
.glyphicon-record:before {
  content: "\e165";
}
.glyphicon-save:before {
  content: "\e166";
}
.glyphicon-open:before {
  content: "\e167";
}
.glyphicon-saved:before {
  content: "\e168";
}
.glyphicon-import:before {
  content: "\e169";
}
.glyphicon-export:before {
  content: "\e170";
}
.glyphicon-send:before {
  content: "\e171";
}
.glyphicon-floppy-disk:before {
  content: "\e172";
}
.glyphicon-floppy-saved:before {
  content: "\e173";
}
.glyphicon-floppy-remove:before {
  content: "\e174";
}
.glyphicon-floppy-save:before {
  content: "\e175";
}
.glyphicon-floppy-open:before {
  content: "\e176";
}
.glyphicon-credit-card:before {
  content: "\e177";
}
.glyphicon-transfer:before {
  content: "\e178";
}
.glyphicon-cutlery:before {
  content: "\e179";
}
.glyphicon-header:before {
  content: "\e180";
}
.glyphicon-compressed:before {
  content: "\e181";
}
.glyphicon-earphone:before {
  content: "\e182";
}
.glyphicon-phone-alt:before {
  content: "\e183";
}
.glyphicon-tower:before {
  content: "\e184";
}
.glyphicon-stats:before {
  content: "\e185";
}
.glyphicon-sd-video:before {
  content: "\e186";
}
.glyphicon-hd-video:before {
  content: "\e187";
}
.glyphicon-subtitles:before {
  content: "\e188";
}
.glyphicon-sound-stereo:before {
  content: "\e189";
}
.glyphicon-sound-dolby:before {
  content: "\e190";
}
.glyphicon-sound-5-1:before {
  content: "\e191";
}
.glyphicon-sound-6-1:before {
  content: "\e192";
}
.glyphicon-sound-7-1:before {
  content: "\e193";
}
.glyphicon-copyright-mark:before {
  content: "\e194";
}
.glyphicon-registration-mark:before {
  content: "\e195";
}
.glyphicon-cloud-download:before {
  content: "\e197";
}
.glyphicon-cloud-upload:before {
  content: "\e198";
}
.glyphicon-tree-conifer:before {
  content: "\e199";
}
.glyphicon-tree-deciduous:before {
  content: "\e200";
}
.glyphicon-cd:before {
  content: "\e201";
}
.glyphicon-save-file:before {
  content: "\e202";
}
.glyphicon-open-file:before {
  content: "\e203";
}
.glyphicon-level-up:before {
  content: "\e204";
}
.glyphicon-copy:before {
  content: "\e205";
}
.glyphicon-paste:before {
  content: "\e206";
}
.glyphicon-alert:before {
  content: "\e209";
}
.glyphicon-equalizer:before {
  content: "\e210";
}
.glyphicon-king:before {
  content: "\e211";
}
.glyphicon-queen:before {
  content: "\e212";
}
.glyphicon-pawn:before {
  content: "\e213";
}
.glyphicon-bishop:before {
  content: "\e214";
}
.glyphicon-knight:before {
  content: "\e215";
}
.glyphicon-baby-formula:before {
  content: "\e216";
}
.glyphicon-tent:before {
  content: "\26fa";
}
.glyphicon-blackboard:before {
  content: "\e218";
}
.glyphicon-bed:before {
  content: "\e219";
}
.glyphicon-apple:before {
  content: "\f8ff";
}
.glyphicon-erase:before {
  content: "\e221";
}
.glyphicon-hourglass:before {
  content: "\231b";
}
.glyphicon-lamp:before {
  content: "\e223";
}
.glyphicon-duplicate:before {
  content: "\e224";
}
.glyphicon-piggy-bank:before {
  content: "\e225";
}
.glyphicon-scissors:before {
  content: "\e226";
}
.glyphicon-bitcoin:before {
  content: "\e227";
}
.glyphicon-btc:before {
  content: "\e227";
}
.glyphicon-xbt:before {
  content: "\e227";
}
.glyphicon-yen:before {
  content: "\00a5";
}
.glyphicon-jpy:before {
  content: "\00a5";
}
.glyphicon-ruble:before {
  content: "\20bd";
}
.glyphicon-rub:before {
  content: "\20bd";
}
.glyphicon-scale:before {
  content: "\e230";
}
.glyphicon-ice-lolly:before {
  content: "\e231";
}
.glyphicon-ice-lolly-tasted:before {
  content: "\e232";
}
.glyphicon-education:before {
  content: "\e233";
}
.glyphicon-option-horizontal:before {
  content: "\e234";
}
.glyphicon-option-vertical:before {
  content: "\e235";
}
.glyphicon-menu-hamburger:before {
  content: "\e236";
}
.glyphicon-modal-window:before {
  content: "\e237";
}
.glyphicon-oil:before {
  content: "\e238";
}
.glyphicon-grain:before {
  content: "\e239";
}
.glyphicon-sunglasses:before {
  content: "\e240";
}
.glyphicon-text-size:before {
  content: "\e241";
}
.glyphicon-text-color:before {
  content: "\e242";
}
.glyphicon-text-background:before {
  content: "\e243";
}
.glyphicon-object-align-top:before {
  content: "\e244";
}
.glyphicon-object-align-bottom:before {
  content: "\e245";
}
.glyphicon-object-align-horizontal:before {
  content: "\e246";
}
.glyphicon-object-align-left:before {
  content: "\e247";
}
.glyphicon-object-align-vertical:before {
  content: "\e248";
}
.glyphicon-object-align-right:before {
  content: "\e249";
}
.glyphicon-triangle-right:before {
  content: "\e250";
}
.glyphicon-triangle-left:before {
  content: "\e251";
}
.glyphicon-triangle-bottom:before {
  content: "\e252";
}
.glyphicon-triangle-top:before {
  content: "\e253";
}
.glyphicon-console:before {
  content: "\e254";
}
.glyphicon-superscript:before {
  content: "\e255";
}
.glyphicon-subscript:before {
  content: "\e256";
}
.glyphicon-menu-left:before {
  content: "\e257";
}
.glyphicon-menu-right:before {
  content: "\e258";
}
.glyphicon-menu-down:before {
  content: "\e259";
}
.glyphicon-menu-up:before {
  content: "\e260";
}
* {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
*:before,
*:after {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
html {
  font-size: 10px;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
}
body {
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-size: 13px;
  line-height: 1.42857143;
  color: #000;
  background-color: #fff;
}
input,
button,
select,
textarea {
  font-family: inherit;
  font-size: inherit;
  line-height: inherit;
}
a {
  color: #337ab7;
  text-decoration: none;
}
a:hover,
a:focus {
  color: #23527c;
  text-decoration: underline;
}
a:focus {
  outline: thin dotted;
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
figure {
  margin: 0;
}
img {
  vertical-align: middle;
}
.img-responsive,
.thumbnail > img,
.thumbnail a > img,
.carousel-inner > .item > img,
.carousel-inner > .item > a > img {
  display: block;
  max-width: 100%;
  height: auto;
}
.img-rounded {
  border-radius: 3px;
}
.img-thumbnail {
  padding: 4px;
  line-height: 1.42857143;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 2px;
  -webkit-transition: all 0.2s ease-in-out;
  -o-transition: all 0.2s ease-in-out;
  transition: all 0.2s ease-in-out;
  display: inline-block;
  max-width: 100%;
  height: auto;
}
.img-circle {
  border-radius: 50%;
}
hr {
  margin-top: 18px;
  margin-bottom: 18px;
  border: 0;
  border-top: 1px solid #eeeeee;
}
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  margin: -1px;
  padding: 0;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  border: 0;
}
.sr-only-focusable:active,
.sr-only-focusable:focus {
  position: static;
  width: auto;
  height: auto;
  margin: 0;
  overflow: visible;
  clip: auto;
}
[role="button"] {
  cursor: pointer;
}
h1,
h2,
h3,
h4,
h5,
h6,
.h1,
.h2,
.h3,
.h4,
.h5,
.h6 {
  font-family: inherit;
  font-weight: 500;
  line-height: 1.1;
  color: inherit;
}
h1 small,
h2 small,
h3 small,
h4 small,
h5 small,
h6 small,
.h1 small,
.h2 small,
.h3 small,
.h4 small,
.h5 small,
.h6 small,
h1 .small,
h2 .small,
h3 .small,
h4 .small,
h5 .small,
h6 .small,
.h1 .small,
.h2 .small,
.h3 .small,
.h4 .small,
.h5 .small,
.h6 .small {
  font-weight: normal;
  line-height: 1;
  color: #777777;
}
h1,
.h1,
h2,
.h2,
h3,
.h3 {
  margin-top: 18px;
  margin-bottom: 9px;
}
h1 small,
.h1 small,
h2 small,
.h2 small,
h3 small,
.h3 small,
h1 .small,
.h1 .small,
h2 .small,
.h2 .small,
h3 .small,
.h3 .small {
  font-size: 65%;
}
h4,
.h4,
h5,
.h5,
h6,
.h6 {
  margin-top: 9px;
  margin-bottom: 9px;
}
h4 small,
.h4 small,
h5 small,
.h5 small,
h6 small,
.h6 small,
h4 .small,
.h4 .small,
h5 .small,
.h5 .small,
h6 .small,
.h6 .small {
  font-size: 75%;
}
h1,
.h1 {
  font-size: 33px;
}
h2,
.h2 {
  font-size: 27px;
}
h3,
.h3 {
  font-size: 23px;
}
h4,
.h4 {
  font-size: 17px;
}
h5,
.h5 {
  font-size: 13px;
}
h6,
.h6 {
  font-size: 12px;
}
p {
  margin: 0 0 9px;
}
.lead {
  margin-bottom: 18px;
  font-size: 14px;
  font-weight: 300;
  line-height: 1.4;
}
@media (min-width: 768px) {
  .lead {
    font-size: 19.5px;
  }
}
small,
.small {
  font-size: 92%;
}
mark,
.mark {
  background-color: #fcf8e3;
  padding: .2em;
}
.text-left {
  text-align: left;
}
.text-right {
  text-align: right;
}
.text-center {
  text-align: center;
}
.text-justify {
  text-align: justify;
}
.text-nowrap {
  white-space: nowrap;
}
.text-lowercase {
  text-transform: lowercase;
}
.text-uppercase {
  text-transform: uppercase;
}
.text-capitalize {
  text-transform: capitalize;
}
.text-muted {
  color: #777777;
}
.text-primary {
  color: #337ab7;
}
a.text-primary:hover,
a.text-primary:focus {
  color: #286090;
}
.text-success {
  color: #3c763d;
}
a.text-success:hover,
a.text-success:focus {
  color: #2b542c;
}
.text-info {
  color: #31708f;
}
a.text-info:hover,
a.text-info:focus {
  color: #245269;
}
.text-warning {
  color: #8a6d3b;
}
a.text-warning:hover,
a.text-warning:focus {
  color: #66512c;
}
.text-danger {
  color: #a94442;
}
a.text-danger:hover,
a.text-danger:focus {
  color: #843534;
}
.bg-primary {
  color: #fff;
  background-color: #337ab7;
}
a.bg-primary:hover,
a.bg-primary:focus {
  background-color: #286090;
}
.bg-success {
  background-color: #dff0d8;
}
a.bg-success:hover,
a.bg-success:focus {
  background-color: #c1e2b3;
}
.bg-info {
  background-color: #d9edf7;
}
a.bg-info:hover,
a.bg-info:focus {
  background-color: #afd9ee;
}
.bg-warning {
  background-color: #fcf8e3;
}
a.bg-warning:hover,
a.bg-warning:focus {
  background-color: #f7ecb5;
}
.bg-danger {
  background-color: #f2dede;
}
a.bg-danger:hover,
a.bg-danger:focus {
  background-color: #e4b9b9;
}
.page-header {
  padding-bottom: 8px;
  margin: 36px 0 18px;
  border-bottom: 1px solid #eeeeee;
}
ul,
ol {
  margin-top: 0;
  margin-bottom: 9px;
}
ul ul,
ol ul,
ul ol,
ol ol {
  margin-bottom: 0;
}
.list-unstyled {
  padding-left: 0;
  list-style: none;
}
.list-inline {
  padding-left: 0;
  list-style: none;
  margin-left: -5px;
}
.list-inline > li {
  display: inline-block;
  padding-left: 5px;
  padding-right: 5px;
}
dl {
  margin-top: 0;
  margin-bottom: 18px;
}
dt,
dd {
  line-height: 1.42857143;
}
dt {
  font-weight: bold;
}
dd {
  margin-left: 0;
}
@media (min-width: 541px) {
  .dl-horizontal dt {
    float: left;
    width: 160px;
    clear: left;
    text-align: right;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }
  .dl-horizontal dd {
    margin-left: 180px;
  }
}
abbr[title],
abbr[data-original-title] {
  cursor: help;
  border-bottom: 1px dotted #777777;
}
.initialism {
  font-size: 90%;
  text-transform: uppercase;
}
blockquote {
  padding: 9px 18px;
  margin: 0 0 18px;
  font-size: inherit;
  border-left: 5px solid #eeeeee;
}
blockquote p:last-child,
blockquote ul:last-child,
blockquote ol:last-child {
  margin-bottom: 0;
}
blockquote footer,
blockquote small,
blockquote .small {
  display: block;
  font-size: 80%;
  line-height: 1.42857143;
  color: #777777;
}
blockquote footer:before,
blockquote small:before,
blockquote .small:before {
  content: '\2014 \00A0';
}
.blockquote-reverse,
blockquote.pull-right {
  padding-right: 15px;
  padding-left: 0;
  border-right: 5px solid #eeeeee;
  border-left: 0;
  text-align: right;
}
.blockquote-reverse footer:before,
blockquote.pull-right footer:before,
.blockquote-reverse small:before,
blockquote.pull-right small:before,
.blockquote-reverse .small:before,
blockquote.pull-right .small:before {
  content: '';
}
.blockquote-reverse footer:after,
blockquote.pull-right footer:after,
.blockquote-reverse small:after,
blockquote.pull-right small:after,
.blockquote-reverse .small:after,
blockquote.pull-right .small:after {
  content: '\00A0 \2014';
}
address {
  margin-bottom: 18px;
  font-style: normal;
  line-height: 1.42857143;
}
code,
kbd,
pre,
samp {
  font-family: monospace;
}
code {
  padding: 2px 4px;
  font-size: 90%;
  color: #c7254e;
  background-color: #f9f2f4;
  border-radius: 2px;
}
kbd {
  padding: 2px 4px;
  font-size: 90%;
  color: #888;
  background-color: transparent;
  border-radius: 1px;
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.25);
}
kbd kbd {
  padding: 0;
  font-size: 100%;
  font-weight: bold;
  box-shadow: none;
}
pre {
  display: block;
  padding: 8.5px;
  margin: 0 0 9px;
  font-size: 12px;
  line-height: 1.42857143;
  word-break: break-all;
  word-wrap: break-word;
  color: #333333;
  background-color: #f5f5f5;
  border: 1px solid #ccc;
  border-radius: 2px;
}
pre code {
  padding: 0;
  font-size: inherit;
  color: inherit;
  white-space: pre-wrap;
  background-color: transparent;
  border-radius: 0;
}
.pre-scrollable {
  max-height: 340px;
  overflow-y: scroll;
}
.container {
  margin-right: auto;
  margin-left: auto;
  padding-left: 0px;
  padding-right: 0px;
}
@media (min-width: 768px) {
  .container {
    width: 768px;
  }
}
@media (min-width: 992px) {
  .container {
    width: 940px;
  }
}
@media (min-width: 1200px) {
  .container {
    width: 1140px;
  }
}
.container-fluid {
  margin-right: auto;
  margin-left: auto;
  padding-left: 0px;
  padding-right: 0px;
}
.row {
  margin-left: 0px;
  margin-right: 0px;
}
.col-xs-1, .col-sm-1, .col-md-1, .col-lg-1, .col-xs-2, .col-sm-2, .col-md-2, .col-lg-2, .col-xs-3, .col-sm-3, .col-md-3, .col-lg-3, .col-xs-4, .col-sm-4, .col-md-4, .col-lg-4, .col-xs-5, .col-sm-5, .col-md-5, .col-lg-5, .col-xs-6, .col-sm-6, .col-md-6, .col-lg-6, .col-xs-7, .col-sm-7, .col-md-7, .col-lg-7, .col-xs-8, .col-sm-8, .col-md-8, .col-lg-8, .col-xs-9, .col-sm-9, .col-md-9, .col-lg-9, .col-xs-10, .col-sm-10, .col-md-10, .col-lg-10, .col-xs-11, .col-sm-11, .col-md-11, .col-lg-11, .col-xs-12, .col-sm-12, .col-md-12, .col-lg-12 {
  position: relative;
  min-height: 1px;
  padding-left: 0px;
  padding-right: 0px;
}
.col-xs-1, .col-xs-2, .col-xs-3, .col-xs-4, .col-xs-5, .col-xs-6, .col-xs-7, .col-xs-8, .col-xs-9, .col-xs-10, .col-xs-11, .col-xs-12 {
  float: left;
}
.col-xs-12 {
  width: 100%;
}
.col-xs-11 {
  width: 91.66666667%;
}
.col-xs-10 {
  width: 83.33333333%;
}
.col-xs-9 {
  width: 75%;
}
.col-xs-8 {
  width: 66.66666667%;
}
.col-xs-7 {
  width: 58.33333333%;
}
.col-xs-6 {
  width: 50%;
}
.col-xs-5 {
  width: 41.66666667%;
}
.col-xs-4 {
  width: 33.33333333%;
}
.col-xs-3 {
  width: 25%;
}
.col-xs-2 {
  width: 16.66666667%;
}
.col-xs-1 {
  width: 8.33333333%;
}
.col-xs-pull-12 {
  right: 100%;
}
.col-xs-pull-11 {
  right: 91.66666667%;
}
.col-xs-pull-10 {
  right: 83.33333333%;
}
.col-xs-pull-9 {
  right: 75%;
}
.col-xs-pull-8 {
  right: 66.66666667%;
}
.col-xs-pull-7 {
  right: 58.33333333%;
}
.col-xs-pull-6 {
  right: 50%;
}
.col-xs-pull-5 {
  right: 41.66666667%;
}
.col-xs-pull-4 {
  right: 33.33333333%;
}
.col-xs-pull-3 {
  right: 25%;
}
.col-xs-pull-2 {
  right: 16.66666667%;
}
.col-xs-pull-1 {
  right: 8.33333333%;
}
.col-xs-pull-0 {
  right: auto;
}
.col-xs-push-12 {
  left: 100%;
}
.col-xs-push-11 {
  left: 91.66666667%;
}
.col-xs-push-10 {
  left: 83.33333333%;
}
.col-xs-push-9 {
  left: 75%;
}
.col-xs-push-8 {
  left: 66.66666667%;
}
.col-xs-push-7 {
  left: 58.33333333%;
}
.col-xs-push-6 {
  left: 50%;
}
.col-xs-push-5 {
  left: 41.66666667%;
}
.col-xs-push-4 {
  left: 33.33333333%;
}
.col-xs-push-3 {
  left: 25%;
}
.col-xs-push-2 {
  left: 16.66666667%;
}
.col-xs-push-1 {
  left: 8.33333333%;
}
.col-xs-push-0 {
  left: auto;
}
.col-xs-offset-12 {
  margin-left: 100%;
}
.col-xs-offset-11 {
  margin-left: 91.66666667%;
}
.col-xs-offset-10 {
  margin-left: 83.33333333%;
}
.col-xs-offset-9 {
  margin-left: 75%;
}
.col-xs-offset-8 {
  margin-left: 66.66666667%;
}
.col-xs-offset-7 {
  margin-left: 58.33333333%;
}
.col-xs-offset-6 {
  margin-left: 50%;
}
.col-xs-offset-5 {
  margin-left: 41.66666667%;
}
.col-xs-offset-4 {
  margin-left: 33.33333333%;
}
.col-xs-offset-3 {
  margin-left: 25%;
}
.col-xs-offset-2 {
  margin-left: 16.66666667%;
}
.col-xs-offset-1 {
  margin-left: 8.33333333%;
}
.col-xs-offset-0 {
  margin-left: 0%;
}
@media (min-width: 768px) {
  .col-sm-1, .col-sm-2, .col-sm-3, .col-sm-4, .col-sm-5, .col-sm-6, .col-sm-7, .col-sm-8, .col-sm-9, .col-sm-10, .col-sm-11, .col-sm-12 {
    float: left;
  }
  .col-sm-12 {
    width: 100%;
  }
  .col-sm-11 {
    width: 91.66666667%;
  }
  .col-sm-10 {
    width: 83.33333333%;
  }
  .col-sm-9 {
    width: 75%;
  }
  .col-sm-8 {
    width: 66.66666667%;
  }
  .col-sm-7 {
    width: 58.33333333%;
  }
  .col-sm-6 {
    width: 50%;
  }
  .col-sm-5 {
    width: 41.66666667%;
  }
  .col-sm-4 {
    width: 33.33333333%;
  }
  .col-sm-3 {
    width: 25%;
  }
  .col-sm-2 {
    width: 16.66666667%;
  }
  .col-sm-1 {
    width: 8.33333333%;
  }
  .col-sm-pull-12 {
    right: 100%;
  }
  .col-sm-pull-11 {
    right: 91.66666667%;
  }
  .col-sm-pull-10 {
    right: 83.33333333%;
  }
  .col-sm-pull-9 {
    right: 75%;
  }
  .col-sm-pull-8 {
    right: 66.66666667%;
  }
  .col-sm-pull-7 {
    right: 58.33333333%;
  }
  .col-sm-pull-6 {
    right: 50%;
  }
  .col-sm-pull-5 {
    right: 41.66666667%;
  }
  .col-sm-pull-4 {
    right: 33.33333333%;
  }
  .col-sm-pull-3 {
    right: 25%;
  }
  .col-sm-pull-2 {
    right: 16.66666667%;
  }
  .col-sm-pull-1 {
    right: 8.33333333%;
  }
  .col-sm-pull-0 {
    right: auto;
  }
  .col-sm-push-12 {
    left: 100%;
  }
  .col-sm-push-11 {
    left: 91.66666667%;
  }
  .col-sm-push-10 {
    left: 83.33333333%;
  }
  .col-sm-push-9 {
    left: 75%;
  }
  .col-sm-push-8 {
    left: 66.66666667%;
  }
  .col-sm-push-7 {
    left: 58.33333333%;
  }
  .col-sm-push-6 {
    left: 50%;
  }
  .col-sm-push-5 {
    left: 41.66666667%;
  }
  .col-sm-push-4 {
    left: 33.33333333%;
  }
  .col-sm-push-3 {
    left: 25%;
  }
  .col-sm-push-2 {
    left: 16.66666667%;
  }
  .col-sm-push-1 {
    left: 8.33333333%;
  }
  .col-sm-push-0 {
    left: auto;
  }
  .col-sm-offset-12 {
    margin-left: 100%;
  }
  .col-sm-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-sm-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-sm-offset-9 {
    margin-left: 75%;
  }
  .col-sm-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-sm-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-sm-offset-6 {
    margin-left: 50%;
  }
  .col-sm-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-sm-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-sm-offset-3 {
    margin-left: 25%;
  }
  .col-sm-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-sm-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-sm-offset-0 {
    margin-left: 0%;
  }
}
@media (min-width: 992px) {
  .col-md-1, .col-md-2, .col-md-3, .col-md-4, .col-md-5, .col-md-6, .col-md-7, .col-md-8, .col-md-9, .col-md-10, .col-md-11, .col-md-12 {
    float: left;
  }
  .col-md-12 {
    width: 100%;
  }
  .col-md-11 {
    width: 91.66666667%;
  }
  .col-md-10 {
    width: 83.33333333%;
  }
  .col-md-9 {
    width: 75%;
  }
  .col-md-8 {
    width: 66.66666667%;
  }
  .col-md-7 {
    width: 58.33333333%;
  }
  .col-md-6 {
    width: 50%;
  }
  .col-md-5 {
    width: 41.66666667%;
  }
  .col-md-4 {
    width: 33.33333333%;
  }
  .col-md-3 {
    width: 25%;
  }
  .col-md-2 {
    width: 16.66666667%;
  }
  .col-md-1 {
    width: 8.33333333%;
  }
  .col-md-pull-12 {
    right: 100%;
  }
  .col-md-pull-11 {
    right: 91.66666667%;
  }
  .col-md-pull-10 {
    right: 83.33333333%;
  }
  .col-md-pull-9 {
    right: 75%;
  }
  .col-md-pull-8 {
    right: 66.66666667%;
  }
  .col-md-pull-7 {
    right: 58.33333333%;
  }
  .col-md-pull-6 {
    right: 50%;
  }
  .col-md-pull-5 {
    right: 41.66666667%;
  }
  .col-md-pull-4 {
    right: 33.33333333%;
  }
  .col-md-pull-3 {
    right: 25%;
  }
  .col-md-pull-2 {
    right: 16.66666667%;
  }
  .col-md-pull-1 {
    right: 8.33333333%;
  }
  .col-md-pull-0 {
    right: auto;
  }
  .col-md-push-12 {
    left: 100%;
  }
  .col-md-push-11 {
    left: 91.66666667%;
  }
  .col-md-push-10 {
    left: 83.33333333%;
  }
  .col-md-push-9 {
    left: 75%;
  }
  .col-md-push-8 {
    left: 66.66666667%;
  }
  .col-md-push-7 {
    left: 58.33333333%;
  }
  .col-md-push-6 {
    left: 50%;
  }
  .col-md-push-5 {
    left: 41.66666667%;
  }
  .col-md-push-4 {
    left: 33.33333333%;
  }
  .col-md-push-3 {
    left: 25%;
  }
  .col-md-push-2 {
    left: 16.66666667%;
  }
  .col-md-push-1 {
    left: 8.33333333%;
  }
  .col-md-push-0 {
    left: auto;
  }
  .col-md-offset-12 {
    margin-left: 100%;
  }
  .col-md-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-md-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-md-offset-9 {
    margin-left: 75%;
  }
  .col-md-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-md-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-md-offset-6 {
    margin-left: 50%;
  }
  .col-md-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-md-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-md-offset-3 {
    margin-left: 25%;
  }
  .col-md-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-md-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-md-offset-0 {
    margin-left: 0%;
  }
}
@media (min-width: 1200px) {
  .col-lg-1, .col-lg-2, .col-lg-3, .col-lg-4, .col-lg-5, .col-lg-6, .col-lg-7, .col-lg-8, .col-lg-9, .col-lg-10, .col-lg-11, .col-lg-12 {
    float: left;
  }
  .col-lg-12 {
    width: 100%;
  }
  .col-lg-11 {
    width: 91.66666667%;
  }
  .col-lg-10 {
    width: 83.33333333%;
  }
  .col-lg-9 {
    width: 75%;
  }
  .col-lg-8 {
    width: 66.66666667%;
  }
  .col-lg-7 {
    width: 58.33333333%;
  }
  .col-lg-6 {
    width: 50%;
  }
  .col-lg-5 {
    width: 41.66666667%;
  }
  .col-lg-4 {
    width: 33.33333333%;
  }
  .col-lg-3 {
    width: 25%;
  }
  .col-lg-2 {
    width: 16.66666667%;
  }
  .col-lg-1 {
    width: 8.33333333%;
  }
  .col-lg-pull-12 {
    right: 100%;
  }
  .col-lg-pull-11 {
    right: 91.66666667%;
  }
  .col-lg-pull-10 {
    right: 83.33333333%;
  }
  .col-lg-pull-9 {
    right: 75%;
  }
  .col-lg-pull-8 {
    right: 66.66666667%;
  }
  .col-lg-pull-7 {
    right: 58.33333333%;
  }
  .col-lg-pull-6 {
    right: 50%;
  }
  .col-lg-pull-5 {
    right: 41.66666667%;
  }
  .col-lg-pull-4 {
    right: 33.33333333%;
  }
  .col-lg-pull-3 {
    right: 25%;
  }
  .col-lg-pull-2 {
    right: 16.66666667%;
  }
  .col-lg-pull-1 {
    right: 8.33333333%;
  }
  .col-lg-pull-0 {
    right: auto;
  }
  .col-lg-push-12 {
    left: 100%;
  }
  .col-lg-push-11 {
    left: 91.66666667%;
  }
  .col-lg-push-10 {
    left: 83.33333333%;
  }
  .col-lg-push-9 {
    left: 75%;
  }
  .col-lg-push-8 {
    left: 66.66666667%;
  }
  .col-lg-push-7 {
    left: 58.33333333%;
  }
  .col-lg-push-6 {
    left: 50%;
  }
  .col-lg-push-5 {
    left: 41.66666667%;
  }
  .col-lg-push-4 {
    left: 33.33333333%;
  }
  .col-lg-push-3 {
    left: 25%;
  }
  .col-lg-push-2 {
    left: 16.66666667%;
  }
  .col-lg-push-1 {
    left: 8.33333333%;
  }
  .col-lg-push-0 {
    left: auto;
  }
  .col-lg-offset-12 {
    margin-left: 100%;
  }
  .col-lg-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-lg-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-lg-offset-9 {
    margin-left: 75%;
  }
  .col-lg-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-lg-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-lg-offset-6 {
    margin-left: 50%;
  }
  .col-lg-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-lg-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-lg-offset-3 {
    margin-left: 25%;
  }
  .col-lg-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-lg-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-lg-offset-0 {
    margin-left: 0%;
  }
}
table {
  background-color: transparent;
}
caption {
  padding-top: 8px;
  padding-bottom: 8px;
  color: #777777;
  text-align: left;
}
th {
  text-align: left;
}
.table {
  width: 100%;
  max-width: 100%;
  margin-bottom: 18px;
}
.table > thead > tr > th,
.table > tbody > tr > th,
.table > tfoot > tr > th,
.table > thead > tr > td,
.table > tbody > tr > td,
.table > tfoot > tr > td {
  padding: 8px;
  line-height: 1.42857143;
  vertical-align: top;
  border-top: 1px solid #ddd;
}
.table > thead > tr > th {
  vertical-align: bottom;
  border-bottom: 2px solid #ddd;
}
.table > caption + thead > tr:first-child > th,
.table > colgroup + thead > tr:first-child > th,
.table > thead:first-child > tr:first-child > th,
.table > caption + thead > tr:first-child > td,
.table > colgroup + thead > tr:first-child > td,
.table > thead:first-child > tr:first-child > td {
  border-top: 0;
}
.table > tbody + tbody {
  border-top: 2px solid #ddd;
}
.table .table {
  background-color: #fff;
}
.table-condensed > thead > tr > th,
.table-condensed > tbody > tr > th,
.table-condensed > tfoot > tr > th,
.table-condensed > thead > tr > td,
.table-condensed > tbody > tr > td,
.table-condensed > tfoot > tr > td {
  padding: 5px;
}
.table-bordered {
  border: 1px solid #ddd;
}
.table-bordered > thead > tr > th,
.table-bordered > tbody > tr > th,
.table-bordered > tfoot > tr > th,
.table-bordered > thead > tr > td,
.table-bordered > tbody > tr > td,
.table-bordered > tfoot > tr > td {
  border: 1px solid #ddd;
}
.table-bordered > thead > tr > th,
.table-bordered > thead > tr > td {
  border-bottom-width: 2px;
}
.table-striped > tbody > tr:nth-of-type(odd) {
  background-color: #f9f9f9;
}
.table-hover > tbody > tr:hover {
  background-color: #f5f5f5;
}
table col[class*="col-"] {
  position: static;
  float: none;
  display: table-column;
}
table td[class*="col-"],
table th[class*="col-"] {
  position: static;
  float: none;
  display: table-cell;
}
.table > thead > tr > td.active,
.table > tbody > tr > td.active,
.table > tfoot > tr > td.active,
.table > thead > tr > th.active,
.table > tbody > tr > th.active,
.table > tfoot > tr > th.active,
.table > thead > tr.active > td,
.table > tbody > tr.active > td,
.table > tfoot > tr.active > td,
.table > thead > tr.active > th,
.table > tbody > tr.active > th,
.table > tfoot > tr.active > th {
  background-color: #f5f5f5;
}
.table-hover > tbody > tr > td.active:hover,
.table-hover > tbody > tr > th.active:hover,
.table-hover > tbody > tr.active:hover > td,
.table-hover > tbody > tr:hover > .active,
.table-hover > tbody > tr.active:hover > th {
  background-color: #e8e8e8;
}
.table > thead > tr > td.success,
.table > tbody > tr > td.success,
.table > tfoot > tr > td.success,
.table > thead > tr > th.success,
.table > tbody > tr > th.success,
.table > tfoot > tr > th.success,
.table > thead > tr.success > td,
.table > tbody > tr.success > td,
.table > tfoot > tr.success > td,
.table > thead > tr.success > th,
.table > tbody > tr.success > th,
.table > tfoot > tr.success > th {
  background-color: #dff0d8;
}
.table-hover > tbody > tr > td.success:hover,
.table-hover > tbody > tr > th.success:hover,
.table-hover > tbody > tr.success:hover > td,
.table-hover > tbody > tr:hover > .success,
.table-hover > tbody > tr.success:hover > th {
  background-color: #d0e9c6;
}
.table > thead > tr > td.info,
.table > tbody > tr > td.info,
.table > tfoot > tr > td.info,
.table > thead > tr > th.info,
.table > tbody > tr > th.info,
.table > tfoot > tr > th.info,
.table > thead > tr.info > td,
.table > tbody > tr.info > td,
.table > tfoot > tr.info > td,
.table > thead > tr.info > th,
.table > tbody > tr.info > th,
.table > tfoot > tr.info > th {
  background-color: #d9edf7;
}
.table-hover > tbody > tr > td.info:hover,
.table-hover > tbody > tr > th.info:hover,
.table-hover > tbody > tr.info:hover > td,
.table-hover > tbody > tr:hover > .info,
.table-hover > tbody > tr.info:hover > th {
  background-color: #c4e3f3;
}
.table > thead > tr > td.warning,
.table > tbody > tr > td.warning,
.table > tfoot > tr > td.warning,
.table > thead > tr > th.warning,
.table > tbody > tr > th.warning,
.table > tfoot > tr > th.warning,
.table > thead > tr.warning > td,
.table > tbody > tr.warning > td,
.table > tfoot > tr.warning > td,
.table > thead > tr.warning > th,
.table > tbody > tr.warning > th,
.table > tfoot > tr.warning > th {
  background-color: #fcf8e3;
}
.table-hover > tbody > tr > td.warning:hover,
.table-hover > tbody > tr > th.warning:hover,
.table-hover > tbody > tr.warning:hover > td,
.table-hover > tbody > tr:hover > .warning,
.table-hover > tbody > tr.warning:hover > th {
  background-color: #faf2cc;
}
.table > thead > tr > td.danger,
.table > tbody > tr > td.danger,
.table > tfoot > tr > td.danger,
.table > thead > tr > th.danger,
.table > tbody > tr > th.danger,
.table > tfoot > tr > th.danger,
.table > thead > tr.danger > td,
.table > tbody > tr.danger > td,
.table > tfoot > tr.danger > td,
.table > thead > tr.danger > th,
.table > tbody > tr.danger > th,
.table > tfoot > tr.danger > th {
  background-color: #f2dede;
}
.table-hover > tbody > tr > td.danger:hover,
.table-hover > tbody > tr > th.danger:hover,
.table-hover > tbody > tr.danger:hover > td,
.table-hover > tbody > tr:hover > .danger,
.table-hover > tbody > tr.danger:hover > th {
  background-color: #ebcccc;
}
.table-responsive {
  overflow-x: auto;
  min-height: 0.01%;
}
@media screen and (max-width: 767px) {
  .table-responsive {
    width: 100%;
    margin-bottom: 13.5px;
    overflow-y: hidden;
    -ms-overflow-style: -ms-autohiding-scrollbar;
    border: 1px solid #ddd;
  }
  .table-responsive > .table {
    margin-bottom: 0;
  }
  .table-responsive > .table > thead > tr > th,
  .table-responsive > .table > tbody > tr > th,
  .table-responsive > .table > tfoot > tr > th,
  .table-responsive > .table > thead > tr > td,
  .table-responsive > .table > tbody > tr > td,
  .table-responsive > .table > tfoot > tr > td {
    white-space: nowrap;
  }
  .table-responsive > .table-bordered {
    border: 0;
  }
  .table-responsive > .table-bordered > thead > tr > th:first-child,
  .table-responsive > .table-bordered > tbody > tr > th:first-child,
  .table-responsive > .table-bordered > tfoot > tr > th:first-child,
  .table-responsive > .table-bordered > thead > tr > td:first-child,
  .table-responsive > .table-bordered > tbody > tr > td:first-child,
  .table-responsive > .table-bordered > tfoot > tr > td:first-child {
    border-left: 0;
  }
  .table-responsive > .table-bordered > thead > tr > th:last-child,
  .table-responsive > .table-bordered > tbody > tr > th:last-child,
  .table-responsive > .table-bordered > tfoot > tr > th:last-child,
  .table-responsive > .table-bordered > thead > tr > td:last-child,
  .table-responsive > .table-bordered > tbody > tr > td:last-child,
  .table-responsive > .table-bordered > tfoot > tr > td:last-child {
    border-right: 0;
  }
  .table-responsive > .table-bordered > tbody > tr:last-child > th,
  .table-responsive > .table-bordered > tfoot > tr:last-child > th,
  .table-responsive > .table-bordered > tbody > tr:last-child > td,
  .table-responsive > .table-bordered > tfoot > tr:last-child > td {
    border-bottom: 0;
  }
}
fieldset {
  padding: 0;
  margin: 0;
  border: 0;
  min-width: 0;
}
legend {
  display: block;
  width: 100%;
  padding: 0;
  margin-bottom: 18px;
  font-size: 19.5px;
  line-height: inherit;
  color: #333333;
  border: 0;
  border-bottom: 1px solid #e5e5e5;
}
label {
  display: inline-block;
  max-width: 100%;
  margin-bottom: 5px;
  font-weight: bold;
}
input[type="search"] {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
input[type="radio"],
input[type="checkbox"] {
  margin: 4px 0 0;
  margin-top: 1px \9;
  line-height: normal;
}
input[type="file"] {
  display: block;
}
input[type="range"] {
  display: block;
  width: 100%;
}
select[multiple],
select[size] {
  height: auto;
}
input[type="file"]:focus,
input[type="radio"]:focus,
input[type="checkbox"]:focus {
  outline: thin dotted;
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
output {
  display: block;
  padding-top: 7px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
}
.form-control {
  display: block;
  width: 100%;
  height: 32px;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  -o-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
}
.form-control:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.form-control::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.form-control:-ms-input-placeholder {
  color: #999;
}
.form-control::-webkit-input-placeholder {
  color: #999;
}
.form-control::-ms-expand {
  border: 0;
  background-color: transparent;
}
.form-control[disabled],
.form-control[readonly],
fieldset[disabled] .form-control {
  background-color: #eeeeee;
  opacity: 1;
}
.form-control[disabled],
fieldset[disabled] .form-control {
  cursor: not-allowed;
}
textarea.form-control {
  height: auto;
}
input[type="search"] {
  -webkit-appearance: none;
}
@media screen and (-webkit-min-device-pixel-ratio: 0) {
  input[type="date"].form-control,
  input[type="time"].form-control,
  input[type="datetime-local"].form-control,
  input[type="month"].form-control {
    line-height: 32px;
  }
  input[type="date"].input-sm,
  input[type="time"].input-sm,
  input[type="datetime-local"].input-sm,
  input[type="month"].input-sm,
  .input-group-sm input[type="date"],
  .input-group-sm input[type="time"],
  .input-group-sm input[type="datetime-local"],
  .input-group-sm input[type="month"] {
    line-height: 30px;
  }
  input[type="date"].input-lg,
  input[type="time"].input-lg,
  input[type="datetime-local"].input-lg,
  input[type="month"].input-lg,
  .input-group-lg input[type="date"],
  .input-group-lg input[type="time"],
  .input-group-lg input[type="datetime-local"],
  .input-group-lg input[type="month"] {
    line-height: 45px;
  }
}
.form-group {
  margin-bottom: 15px;
}
.radio,
.checkbox {
  position: relative;
  display: block;
  margin-top: 10px;
  margin-bottom: 10px;
}
.radio label,
.checkbox label {
  min-height: 18px;
  padding-left: 20px;
  margin-bottom: 0;
  font-weight: normal;
  cursor: pointer;
}
.radio input[type="radio"],
.radio-inline input[type="radio"],
.checkbox input[type="checkbox"],
.checkbox-inline input[type="checkbox"] {
  position: absolute;
  margin-left: -20px;
  margin-top: 4px \9;
}
.radio + .radio,
.checkbox + .checkbox {
  margin-top: -5px;
}
.radio-inline,
.checkbox-inline {
  position: relative;
  display: inline-block;
  padding-left: 20px;
  margin-bottom: 0;
  vertical-align: middle;
  font-weight: normal;
  cursor: pointer;
}
.radio-inline + .radio-inline,
.checkbox-inline + .checkbox-inline {
  margin-top: 0;
  margin-left: 10px;
}
input[type="radio"][disabled],
input[type="checkbox"][disabled],
input[type="radio"].disabled,
input[type="checkbox"].disabled,
fieldset[disabled] input[type="radio"],
fieldset[disabled] input[type="checkbox"] {
  cursor: not-allowed;
}
.radio-inline.disabled,
.checkbox-inline.disabled,
fieldset[disabled] .radio-inline,
fieldset[disabled] .checkbox-inline {
  cursor: not-allowed;
}
.radio.disabled label,
.checkbox.disabled label,
fieldset[disabled] .radio label,
fieldset[disabled] .checkbox label {
  cursor: not-allowed;
}
.form-control-static {
  padding-top: 7px;
  padding-bottom: 7px;
  margin-bottom: 0;
  min-height: 31px;
}
.form-control-static.input-lg,
.form-control-static.input-sm {
  padding-left: 0;
  padding-right: 0;
}
.input-sm {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
select.input-sm {
  height: 30px;
  line-height: 30px;
}
textarea.input-sm,
select[multiple].input-sm {
  height: auto;
}
.form-group-sm .form-control {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.form-group-sm select.form-control {
  height: 30px;
  line-height: 30px;
}
.form-group-sm textarea.form-control,
.form-group-sm select[multiple].form-control {
  height: auto;
}
.form-group-sm .form-control-static {
  height: 30px;
  min-height: 30px;
  padding: 6px 10px;
  font-size: 12px;
  line-height: 1.5;
}
.input-lg {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
select.input-lg {
  height: 45px;
  line-height: 45px;
}
textarea.input-lg,
select[multiple].input-lg {
  height: auto;
}
.form-group-lg .form-control {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
.form-group-lg select.form-control {
  height: 45px;
  line-height: 45px;
}
.form-group-lg textarea.form-control,
.form-group-lg select[multiple].form-control {
  height: auto;
}
.form-group-lg .form-control-static {
  height: 45px;
  min-height: 35px;
  padding: 11px 16px;
  font-size: 17px;
  line-height: 1.3333333;
}
.has-feedback {
  position: relative;
}
.has-feedback .form-control {
  padding-right: 40px;
}
.form-control-feedback {
  position: absolute;
  top: 0;
  right: 0;
  z-index: 2;
  display: block;
  width: 32px;
  height: 32px;
  line-height: 32px;
  text-align: center;
  pointer-events: none;
}
.input-lg + .form-control-feedback,
.input-group-lg + .form-control-feedback,
.form-group-lg .form-control + .form-control-feedback {
  width: 45px;
  height: 45px;
  line-height: 45px;
}
.input-sm + .form-control-feedback,
.input-group-sm + .form-control-feedback,
.form-group-sm .form-control + .form-control-feedback {
  width: 30px;
  height: 30px;
  line-height: 30px;
}
.has-success .help-block,
.has-success .control-label,
.has-success .radio,
.has-success .checkbox,
.has-success .radio-inline,
.has-success .checkbox-inline,
.has-success.radio label,
.has-success.checkbox label,
.has-success.radio-inline label,
.has-success.checkbox-inline label {
  color: #3c763d;
}
.has-success .form-control {
  border-color: #3c763d;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-success .form-control:focus {
  border-color: #2b542c;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #67b168;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #67b168;
}
.has-success .input-group-addon {
  color: #3c763d;
  border-color: #3c763d;
  background-color: #dff0d8;
}
.has-success .form-control-feedback {
  color: #3c763d;
}
.has-warning .help-block,
.has-warning .control-label,
.has-warning .radio,
.has-warning .checkbox,
.has-warning .radio-inline,
.has-warning .checkbox-inline,
.has-warning.radio label,
.has-warning.checkbox label,
.has-warning.radio-inline label,
.has-warning.checkbox-inline label {
  color: #8a6d3b;
}
.has-warning .form-control {
  border-color: #8a6d3b;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-warning .form-control:focus {
  border-color: #66512c;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #c0a16b;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #c0a16b;
}
.has-warning .input-group-addon {
  color: #8a6d3b;
  border-color: #8a6d3b;
  background-color: #fcf8e3;
}
.has-warning .form-control-feedback {
  color: #8a6d3b;
}
.has-error .help-block,
.has-error .control-label,
.has-error .radio,
.has-error .checkbox,
.has-error .radio-inline,
.has-error .checkbox-inline,
.has-error.radio label,
.has-error.checkbox label,
.has-error.radio-inline label,
.has-error.checkbox-inline label {
  color: #a94442;
}
.has-error .form-control {
  border-color: #a94442;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-error .form-control:focus {
  border-color: #843534;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #ce8483;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #ce8483;
}
.has-error .input-group-addon {
  color: #a94442;
  border-color: #a94442;
  background-color: #f2dede;
}
.has-error .form-control-feedback {
  color: #a94442;
}
.has-feedback label ~ .form-control-feedback {
  top: 23px;
}
.has-feedback label.sr-only ~ .form-control-feedback {
  top: 0;
}
.help-block {
  display: block;
  margin-top: 5px;
  margin-bottom: 10px;
  color: #404040;
}
@media (min-width: 768px) {
  .form-inline .form-group {
    display: inline-block;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .form-control {
    display: inline-block;
    width: auto;
    vertical-align: middle;
  }
  .form-inline .form-control-static {
    display: inline-block;
  }
  .form-inline .input-group {
    display: inline-table;
    vertical-align: middle;
  }
  .form-inline .input-group .input-group-addon,
  .form-inline .input-group .input-group-btn,
  .form-inline .input-group .form-control {
    width: auto;
  }
  .form-inline .input-group > .form-control {
    width: 100%;
  }
  .form-inline .control-label {
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .radio,
  .form-inline .checkbox {
    display: inline-block;
    margin-top: 0;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .radio label,
  .form-inline .checkbox label {
    padding-left: 0;
  }
  .form-inline .radio input[type="radio"],
  .form-inline .checkbox input[type="checkbox"] {
    position: relative;
    margin-left: 0;
  }
  .form-inline .has-feedback .form-control-feedback {
    top: 0;
  }
}
.form-horizontal .radio,
.form-horizontal .checkbox,
.form-horizontal .radio-inline,
.form-horizontal .checkbox-inline {
  margin-top: 0;
  margin-bottom: 0;
  padding-top: 7px;
}
.form-horizontal .radio,
.form-horizontal .checkbox {
  min-height: 25px;
}
.form-horizontal .form-group {
  margin-left: 0px;
  margin-right: 0px;
}
@media (min-width: 768px) {
  .form-horizontal .control-label {
    text-align: right;
    margin-bottom: 0;
    padding-top: 7px;
  }
}
.form-horizontal .has-feedback .form-control-feedback {
  right: 0px;
}
@media (min-width: 768px) {
  .form-horizontal .form-group-lg .control-label {
    padding-top: 11px;
    font-size: 17px;
  }
}
@media (min-width: 768px) {
  .form-horizontal .form-group-sm .control-label {
    padding-top: 6px;
    font-size: 12px;
  }
}
.btn {
  display: inline-block;
  margin-bottom: 0;
  font-weight: normal;
  text-align: center;
  vertical-align: middle;
  touch-action: manipulation;
  cursor: pointer;
  background-image: none;
  border: 1px solid transparent;
  white-space: nowrap;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  border-radius: 2px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
.btn:focus,
.btn:active:focus,
.btn.active:focus,
.btn.focus,
.btn:active.focus,
.btn.active.focus {
  outline: thin dotted;
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
.btn:hover,
.btn:focus,
.btn.focus {
  color: #333;
  text-decoration: none;
}
.btn:active,
.btn.active {
  outline: 0;
  background-image: none;
  -webkit-box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
  box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
}
.btn.disabled,
.btn[disabled],
fieldset[disabled] .btn {
  cursor: not-allowed;
  opacity: 0.65;
  filter: alpha(opacity=65);
  -webkit-box-shadow: none;
  box-shadow: none;
}
a.btn.disabled,
fieldset[disabled] a.btn {
  pointer-events: none;
}
.btn-default {
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
.btn-default:focus,
.btn-default.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
.btn-default:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.btn-default:active,
.btn-default.active,
.open > .dropdown-toggle.btn-default {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.btn-default:active:hover,
.btn-default.active:hover,
.open > .dropdown-toggle.btn-default:hover,
.btn-default:active:focus,
.btn-default.active:focus,
.open > .dropdown-toggle.btn-default:focus,
.btn-default:active.focus,
.btn-default.active.focus,
.open > .dropdown-toggle.btn-default.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
.btn-default:active,
.btn-default.active,
.open > .dropdown-toggle.btn-default {
  background-image: none;
}
.btn-default.disabled:hover,
.btn-default[disabled]:hover,
fieldset[disabled] .btn-default:hover,
.btn-default.disabled:focus,
.btn-default[disabled]:focus,
fieldset[disabled] .btn-default:focus,
.btn-default.disabled.focus,
.btn-default[disabled].focus,
fieldset[disabled] .btn-default.focus {
  background-color: #fff;
  border-color: #ccc;
}
.btn-default .badge {
  color: #fff;
  background-color: #333;
}
.btn-primary {
  color: #fff;
  background-color: #337ab7;
  border-color: #2e6da4;
}
.btn-primary:focus,
.btn-primary.focus {
  color: #fff;
  background-color: #286090;
  border-color: #122b40;
}
.btn-primary:hover {
  color: #fff;
  background-color: #286090;
  border-color: #204d74;
}
.btn-primary:active,
.btn-primary.active,
.open > .dropdown-toggle.btn-primary {
  color: #fff;
  background-color: #286090;
  border-color: #204d74;
}
.btn-primary:active:hover,
.btn-primary.active:hover,
.open > .dropdown-toggle.btn-primary:hover,
.btn-primary:active:focus,
.btn-primary.active:focus,
.open > .dropdown-toggle.btn-primary:focus,
.btn-primary:active.focus,
.btn-primary.active.focus,
.open > .dropdown-toggle.btn-primary.focus {
  color: #fff;
  background-color: #204d74;
  border-color: #122b40;
}
.btn-primary:active,
.btn-primary.active,
.open > .dropdown-toggle.btn-primary {
  background-image: none;
}
.btn-primary.disabled:hover,
.btn-primary[disabled]:hover,
fieldset[disabled] .btn-primary:hover,
.btn-primary.disabled:focus,
.btn-primary[disabled]:focus,
fieldset[disabled] .btn-primary:focus,
.btn-primary.disabled.focus,
.btn-primary[disabled].focus,
fieldset[disabled] .btn-primary.focus {
  background-color: #337ab7;
  border-color: #2e6da4;
}
.btn-primary .badge {
  color: #337ab7;
  background-color: #fff;
}
.btn-success {
  color: #fff;
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.btn-success:focus,
.btn-success.focus {
  color: #fff;
  background-color: #449d44;
  border-color: #255625;
}
.btn-success:hover {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.btn-success:active,
.btn-success.active,
.open > .dropdown-toggle.btn-success {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.btn-success:active:hover,
.btn-success.active:hover,
.open > .dropdown-toggle.btn-success:hover,
.btn-success:active:focus,
.btn-success.active:focus,
.open > .dropdown-toggle.btn-success:focus,
.btn-success:active.focus,
.btn-success.active.focus,
.open > .dropdown-toggle.btn-success.focus {
  color: #fff;
  background-color: #398439;
  border-color: #255625;
}
.btn-success:active,
.btn-success.active,
.open > .dropdown-toggle.btn-success {
  background-image: none;
}
.btn-success.disabled:hover,
.btn-success[disabled]:hover,
fieldset[disabled] .btn-success:hover,
.btn-success.disabled:focus,
.btn-success[disabled]:focus,
fieldset[disabled] .btn-success:focus,
.btn-success.disabled.focus,
.btn-success[disabled].focus,
fieldset[disabled] .btn-success.focus {
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.btn-success .badge {
  color: #5cb85c;
  background-color: #fff;
}
.btn-info {
  color: #fff;
  background-color: #5bc0de;
  border-color: #46b8da;
}
.btn-info:focus,
.btn-info.focus {
  color: #fff;
  background-color: #31b0d5;
  border-color: #1b6d85;
}
.btn-info:hover {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.btn-info:active,
.btn-info.active,
.open > .dropdown-toggle.btn-info {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.btn-info:active:hover,
.btn-info.active:hover,
.open > .dropdown-toggle.btn-info:hover,
.btn-info:active:focus,
.btn-info.active:focus,
.open > .dropdown-toggle.btn-info:focus,
.btn-info:active.focus,
.btn-info.active.focus,
.open > .dropdown-toggle.btn-info.focus {
  color: #fff;
  background-color: #269abc;
  border-color: #1b6d85;
}
.btn-info:active,
.btn-info.active,
.open > .dropdown-toggle.btn-info {
  background-image: none;
}
.btn-info.disabled:hover,
.btn-info[disabled]:hover,
fieldset[disabled] .btn-info:hover,
.btn-info.disabled:focus,
.btn-info[disabled]:focus,
fieldset[disabled] .btn-info:focus,
.btn-info.disabled.focus,
.btn-info[disabled].focus,
fieldset[disabled] .btn-info.focus {
  background-color: #5bc0de;
  border-color: #46b8da;
}
.btn-info .badge {
  color: #5bc0de;
  background-color: #fff;
}
.btn-warning {
  color: #fff;
  background-color: #f0ad4e;
  border-color: #eea236;
}
.btn-warning:focus,
.btn-warning.focus {
  color: #fff;
  background-color: #ec971f;
  border-color: #985f0d;
}
.btn-warning:hover {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.btn-warning:active,
.btn-warning.active,
.open > .dropdown-toggle.btn-warning {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.btn-warning:active:hover,
.btn-warning.active:hover,
.open > .dropdown-toggle.btn-warning:hover,
.btn-warning:active:focus,
.btn-warning.active:focus,
.open > .dropdown-toggle.btn-warning:focus,
.btn-warning:active.focus,
.btn-warning.active.focus,
.open > .dropdown-toggle.btn-warning.focus {
  color: #fff;
  background-color: #d58512;
  border-color: #985f0d;
}
.btn-warning:active,
.btn-warning.active,
.open > .dropdown-toggle.btn-warning {
  background-image: none;
}
.btn-warning.disabled:hover,
.btn-warning[disabled]:hover,
fieldset[disabled] .btn-warning:hover,
.btn-warning.disabled:focus,
.btn-warning[disabled]:focus,
fieldset[disabled] .btn-warning:focus,
.btn-warning.disabled.focus,
.btn-warning[disabled].focus,
fieldset[disabled] .btn-warning.focus {
  background-color: #f0ad4e;
  border-color: #eea236;
}
.btn-warning .badge {
  color: #f0ad4e;
  background-color: #fff;
}
.btn-danger {
  color: #fff;
  background-color: #d9534f;
  border-color: #d43f3a;
}
.btn-danger:focus,
.btn-danger.focus {
  color: #fff;
  background-color: #c9302c;
  border-color: #761c19;
}
.btn-danger:hover {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.btn-danger:active,
.btn-danger.active,
.open > .dropdown-toggle.btn-danger {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.btn-danger:active:hover,
.btn-danger.active:hover,
.open > .dropdown-toggle.btn-danger:hover,
.btn-danger:active:focus,
.btn-danger.active:focus,
.open > .dropdown-toggle.btn-danger:focus,
.btn-danger:active.focus,
.btn-danger.active.focus,
.open > .dropdown-toggle.btn-danger.focus {
  color: #fff;
  background-color: #ac2925;
  border-color: #761c19;
}
.btn-danger:active,
.btn-danger.active,
.open > .dropdown-toggle.btn-danger {
  background-image: none;
}
.btn-danger.disabled:hover,
.btn-danger[disabled]:hover,
fieldset[disabled] .btn-danger:hover,
.btn-danger.disabled:focus,
.btn-danger[disabled]:focus,
fieldset[disabled] .btn-danger:focus,
.btn-danger.disabled.focus,
.btn-danger[disabled].focus,
fieldset[disabled] .btn-danger.focus {
  background-color: #d9534f;
  border-color: #d43f3a;
}
.btn-danger .badge {
  color: #d9534f;
  background-color: #fff;
}
.btn-link {
  color: #337ab7;
  font-weight: normal;
  border-radius: 0;
}
.btn-link,
.btn-link:active,
.btn-link.active,
.btn-link[disabled],
fieldset[disabled] .btn-link {
  background-color: transparent;
  -webkit-box-shadow: none;
  box-shadow: none;
}
.btn-link,
.btn-link:hover,
.btn-link:focus,
.btn-link:active {
  border-color: transparent;
}
.btn-link:hover,
.btn-link:focus {
  color: #23527c;
  text-decoration: underline;
  background-color: transparent;
}
.btn-link[disabled]:hover,
fieldset[disabled] .btn-link:hover,
.btn-link[disabled]:focus,
fieldset[disabled] .btn-link:focus {
  color: #777777;
  text-decoration: none;
}
.btn-lg,
.btn-group-lg > .btn {
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
.btn-sm,
.btn-group-sm > .btn {
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.btn-xs,
.btn-group-xs > .btn {
  padding: 1px 5px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.btn-block {
  display: block;
  width: 100%;
}
.btn-block + .btn-block {
  margin-top: 5px;
}
input[type="submit"].btn-block,
input[type="reset"].btn-block,
input[type="button"].btn-block {
  width: 100%;
}
.fade {
  opacity: 0;
  -webkit-transition: opacity 0.15s linear;
  -o-transition: opacity 0.15s linear;
  transition: opacity 0.15s linear;
}
.fade.in {
  opacity: 1;
}
.collapse {
  display: none;
}
.collapse.in {
  display: block;
}
tr.collapse.in {
  display: table-row;
}
tbody.collapse.in {
  display: table-row-group;
}
.collapsing {
  position: relative;
  height: 0;
  overflow: hidden;
  -webkit-transition-property: height, visibility;
  transition-property: height, visibility;
  -webkit-transition-duration: 0.35s;
  transition-duration: 0.35s;
  -webkit-transition-timing-function: ease;
  transition-timing-function: ease;
}
.caret {
  display: inline-block;
  width: 0;
  height: 0;
  margin-left: 2px;
  vertical-align: middle;
  border-top: 4px dashed;
  border-top: 4px solid \9;
  border-right: 4px solid transparent;
  border-left: 4px solid transparent;
}
.dropup,
.dropdown {
  position: relative;
}
.dropdown-toggle:focus {
  outline: 0;
}
.dropdown-menu {
  position: absolute;
  top: 100%;
  left: 0;
  z-index: 1000;
  display: none;
  float: left;
  min-width: 160px;
  padding: 5px 0;
  margin: 2px 0 0;
  list-style: none;
  font-size: 13px;
  text-align: left;
  background-color: #fff;
  border: 1px solid #ccc;
  border: 1px solid rgba(0, 0, 0, 0.15);
  border-radius: 2px;
  -webkit-box-shadow: 0 6px 12px rgba(0, 0, 0, 0.175);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.175);
  background-clip: padding-box;
}
.dropdown-menu.pull-right {
  right: 0;
  left: auto;
}
.dropdown-menu .divider {
  height: 1px;
  margin: 8px 0;
  overflow: hidden;
  background-color: #e5e5e5;
}
.dropdown-menu > li > a {
  display: block;
  padding: 3px 20px;
  clear: both;
  font-weight: normal;
  line-height: 1.42857143;
  color: #333333;
  white-space: nowrap;
}
.dropdown-menu > li > a:hover,
.dropdown-menu > li > a:focus {
  text-decoration: none;
  color: #262626;
  background-color: #f5f5f5;
}
.dropdown-menu > .active > a,
.dropdown-menu > .active > a:hover,
.dropdown-menu > .active > a:focus {
  color: #fff;
  text-decoration: none;
  outline: 0;
  background-color: #337ab7;
}
.dropdown-menu > .disabled > a,
.dropdown-menu > .disabled > a:hover,
.dropdown-menu > .disabled > a:focus {
  color: #777777;
}
.dropdown-menu > .disabled > a:hover,
.dropdown-menu > .disabled > a:focus {
  text-decoration: none;
  background-color: transparent;
  background-image: none;
  filter: progid:DXImageTransform.Microsoft.gradient(enabled = false);
  cursor: not-allowed;
}
.open > .dropdown-menu {
  display: block;
}
.open > a {
  outline: 0;
}
.dropdown-menu-right {
  left: auto;
  right: 0;
}
.dropdown-menu-left {
  left: 0;
  right: auto;
}
.dropdown-header {
  display: block;
  padding: 3px 20px;
  font-size: 12px;
  line-height: 1.42857143;
  color: #777777;
  white-space: nowrap;
}
.dropdown-backdrop {
  position: fixed;
  left: 0;
  right: 0;
  bottom: 0;
  top: 0;
  z-index: 990;
}
.pull-right > .dropdown-menu {
  right: 0;
  left: auto;
}
.dropup .caret,
.navbar-fixed-bottom .dropdown .caret {
  border-top: 0;
  border-bottom: 4px dashed;
  border-bottom: 4px solid \9;
  content: "";
}
.dropup .dropdown-menu,
.navbar-fixed-bottom .dropdown .dropdown-menu {
  top: auto;
  bottom: 100%;
  margin-bottom: 2px;
}
@media (min-width: 541px) {
  .navbar-right .dropdown-menu {
    left: auto;
    right: 0;
  }
  .navbar-right .dropdown-menu-left {
    left: 0;
    right: auto;
  }
}
.btn-group,
.btn-group-vertical {
  position: relative;
  display: inline-block;
  vertical-align: middle;
}
.btn-group > .btn,
.btn-group-vertical > .btn {
  position: relative;
  float: left;
}
.btn-group > .btn:hover,
.btn-group-vertical > .btn:hover,
.btn-group > .btn:focus,
.btn-group-vertical > .btn:focus,
.btn-group > .btn:active,
.btn-group-vertical > .btn:active,
.btn-group > .btn.active,
.btn-group-vertical > .btn.active {
  z-index: 2;
}
.btn-group .btn + .btn,
.btn-group .btn + .btn-group,
.btn-group .btn-group + .btn,
.btn-group .btn-group + .btn-group {
  margin-left: -1px;
}
.btn-toolbar {
  margin-left: -5px;
}
.btn-toolbar .btn,
.btn-toolbar .btn-group,
.btn-toolbar .input-group {
  float: left;
}
.btn-toolbar > .btn,
.btn-toolbar > .btn-group,
.btn-toolbar > .input-group {
  margin-left: 5px;
}
.btn-group > .btn:not(:first-child):not(:last-child):not(.dropdown-toggle) {
  border-radius: 0;
}
.btn-group > .btn:first-child {
  margin-left: 0;
}
.btn-group > .btn:first-child:not(:last-child):not(.dropdown-toggle) {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.btn-group > .btn:last-child:not(:first-child),
.btn-group > .dropdown-toggle:not(:first-child) {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.btn-group > .btn-group {
  float: left;
}
.btn-group > .btn-group:not(:first-child):not(:last-child) > .btn {
  border-radius: 0;
}
.btn-group > .btn-group:first-child:not(:last-child) > .btn:last-child,
.btn-group > .btn-group:first-child:not(:last-child) > .dropdown-toggle {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.btn-group > .btn-group:last-child:not(:first-child) > .btn:first-child {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.btn-group .dropdown-toggle:active,
.btn-group.open .dropdown-toggle {
  outline: 0;
}
.btn-group > .btn + .dropdown-toggle {
  padding-left: 8px;
  padding-right: 8px;
}
.btn-group > .btn-lg + .dropdown-toggle {
  padding-left: 12px;
  padding-right: 12px;
}
.btn-group.open .dropdown-toggle {
  -webkit-box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
  box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
}
.btn-group.open .dropdown-toggle.btn-link {
  -webkit-box-shadow: none;
  box-shadow: none;
}
.btn .caret {
  margin-left: 0;
}
.btn-lg .caret {
  border-width: 5px 5px 0;
  border-bottom-width: 0;
}
.dropup .btn-lg .caret {
  border-width: 0 5px 5px;
}
.btn-group-vertical > .btn,
.btn-group-vertical > .btn-group,
.btn-group-vertical > .btn-group > .btn {
  display: block;
  float: none;
  width: 100%;
  max-width: 100%;
}
.btn-group-vertical > .btn-group > .btn {
  float: none;
}
.btn-group-vertical > .btn + .btn,
.btn-group-vertical > .btn + .btn-group,
.btn-group-vertical > .btn-group + .btn,
.btn-group-vertical > .btn-group + .btn-group {
  margin-top: -1px;
  margin-left: 0;
}
.btn-group-vertical > .btn:not(:first-child):not(:last-child) {
  border-radius: 0;
}
.btn-group-vertical > .btn:first-child:not(:last-child) {
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.btn-group-vertical > .btn:last-child:not(:first-child) {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
  border-bottom-right-radius: 2px;
  border-bottom-left-radius: 2px;
}
.btn-group-vertical > .btn-group:not(:first-child):not(:last-child) > .btn {
  border-radius: 0;
}
.btn-group-vertical > .btn-group:first-child:not(:last-child) > .btn:last-child,
.btn-group-vertical > .btn-group:first-child:not(:last-child) > .dropdown-toggle {
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.btn-group-vertical > .btn-group:last-child:not(:first-child) > .btn:first-child {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.btn-group-justified {
  display: table;
  width: 100%;
  table-layout: fixed;
  border-collapse: separate;
}
.btn-group-justified > .btn,
.btn-group-justified > .btn-group {
  float: none;
  display: table-cell;
  width: 1%;
}
.btn-group-justified > .btn-group .btn {
  width: 100%;
}
.btn-group-justified > .btn-group .dropdown-menu {
  left: auto;
}
[data-toggle="buttons"] > .btn input[type="radio"],
[data-toggle="buttons"] > .btn-group > .btn input[type="radio"],
[data-toggle="buttons"] > .btn input[type="checkbox"],
[data-toggle="buttons"] > .btn-group > .btn input[type="checkbox"] {
  position: absolute;
  clip: rect(0, 0, 0, 0);
  pointer-events: none;
}
.input-group {
  position: relative;
  display: table;
  border-collapse: separate;
}
.input-group[class*="col-"] {
  float: none;
  padding-left: 0;
  padding-right: 0;
}
.input-group .form-control {
  position: relative;
  z-index: 2;
  float: left;
  width: 100%;
  margin-bottom: 0;
}
.input-group .form-control:focus {
  z-index: 3;
}
.input-group-lg > .form-control,
.input-group-lg > .input-group-addon,
.input-group-lg > .input-group-btn > .btn {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
select.input-group-lg > .form-control,
select.input-group-lg > .input-group-addon,
select.input-group-lg > .input-group-btn > .btn {
  height: 45px;
  line-height: 45px;
}
textarea.input-group-lg > .form-control,
textarea.input-group-lg > .input-group-addon,
textarea.input-group-lg > .input-group-btn > .btn,
select[multiple].input-group-lg > .form-control,
select[multiple].input-group-lg > .input-group-addon,
select[multiple].input-group-lg > .input-group-btn > .btn {
  height: auto;
}
.input-group-sm > .form-control,
.input-group-sm > .input-group-addon,
.input-group-sm > .input-group-btn > .btn {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
select.input-group-sm > .form-control,
select.input-group-sm > .input-group-addon,
select.input-group-sm > .input-group-btn > .btn {
  height: 30px;
  line-height: 30px;
}
textarea.input-group-sm > .form-control,
textarea.input-group-sm > .input-group-addon,
textarea.input-group-sm > .input-group-btn > .btn,
select[multiple].input-group-sm > .form-control,
select[multiple].input-group-sm > .input-group-addon,
select[multiple].input-group-sm > .input-group-btn > .btn {
  height: auto;
}
.input-group-addon,
.input-group-btn,
.input-group .form-control {
  display: table-cell;
}
.input-group-addon:not(:first-child):not(:last-child),
.input-group-btn:not(:first-child):not(:last-child),
.input-group .form-control:not(:first-child):not(:last-child) {
  border-radius: 0;
}
.input-group-addon,
.input-group-btn {
  width: 1%;
  white-space: nowrap;
  vertical-align: middle;
}
.input-group-addon {
  padding: 6px 12px;
  font-size: 13px;
  font-weight: normal;
  line-height: 1;
  color: #555555;
  text-align: center;
  background-color: #eeeeee;
  border: 1px solid #ccc;
  border-radius: 2px;
}
.input-group-addon.input-sm {
  padding: 5px 10px;
  font-size: 12px;
  border-radius: 1px;
}
.input-group-addon.input-lg {
  padding: 10px 16px;
  font-size: 17px;
  border-radius: 3px;
}
.input-group-addon input[type="radio"],
.input-group-addon input[type="checkbox"] {
  margin-top: 0;
}
.input-group .form-control:first-child,
.input-group-addon:first-child,
.input-group-btn:first-child > .btn,
.input-group-btn:first-child > .btn-group > .btn,
.input-group-btn:first-child > .dropdown-toggle,
.input-group-btn:last-child > .btn:not(:last-child):not(.dropdown-toggle),
.input-group-btn:last-child > .btn-group:not(:last-child) > .btn {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.input-group-addon:first-child {
  border-right: 0;
}
.input-group .form-control:last-child,
.input-group-addon:last-child,
.input-group-btn:last-child > .btn,
.input-group-btn:last-child > .btn-group > .btn,
.input-group-btn:last-child > .dropdown-toggle,
.input-group-btn:first-child > .btn:not(:first-child),
.input-group-btn:first-child > .btn-group:not(:first-child) > .btn {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.input-group-addon:last-child {
  border-left: 0;
}
.input-group-btn {
  position: relative;
  font-size: 0;
  white-space: nowrap;
}
.input-group-btn > .btn {
  position: relative;
}
.input-group-btn > .btn + .btn {
  margin-left: -1px;
}
.input-group-btn > .btn:hover,
.input-group-btn > .btn:focus,
.input-group-btn > .btn:active {
  z-index: 2;
}
.input-group-btn:first-child > .btn,
.input-group-btn:first-child > .btn-group {
  margin-right: -1px;
}
.input-group-btn:last-child > .btn,
.input-group-btn:last-child > .btn-group {
  z-index: 2;
  margin-left: -1px;
}
.nav {
  margin-bottom: 0;
  padding-left: 0;
  list-style: none;
}
.nav > li {
  position: relative;
  display: block;
}
.nav > li > a {
  position: relative;
  display: block;
  padding: 10px 15px;
}
.nav > li > a:hover,
.nav > li > a:focus {
  text-decoration: none;
  background-color: #eeeeee;
}
.nav > li.disabled > a {
  color: #777777;
}
.nav > li.disabled > a:hover,
.nav > li.disabled > a:focus {
  color: #777777;
  text-decoration: none;
  background-color: transparent;
  cursor: not-allowed;
}
.nav .open > a,
.nav .open > a:hover,
.nav .open > a:focus {
  background-color: #eeeeee;
  border-color: #337ab7;
}
.nav .nav-divider {
  height: 1px;
  margin: 8px 0;
  overflow: hidden;
  background-color: #e5e5e5;
}
.nav > li > a > img {
  max-width: none;
}
.nav-tabs {
  border-bottom: 1px solid #ddd;
}
.nav-tabs > li {
  float: left;
  margin-bottom: -1px;
}
.nav-tabs > li > a {
  margin-right: 2px;
  line-height: 1.42857143;
  border: 1px solid transparent;
  border-radius: 2px 2px 0 0;
}
.nav-tabs > li > a:hover {
  border-color: #eeeeee #eeeeee #ddd;
}
.nav-tabs > li.active > a,
.nav-tabs > li.active > a:hover,
.nav-tabs > li.active > a:focus {
  color: #555555;
  background-color: #fff;
  border: 1px solid #ddd;
  border-bottom-color: transparent;
  cursor: default;
}
.nav-tabs.nav-justified {
  width: 100%;
  border-bottom: 0;
}
.nav-tabs.nav-justified > li {
  float: none;
}
.nav-tabs.nav-justified > li > a {
  text-align: center;
  margin-bottom: 5px;
}
.nav-tabs.nav-justified > .dropdown .dropdown-menu {
  top: auto;
  left: auto;
}
@media (min-width: 768px) {
  .nav-tabs.nav-justified > li {
    display: table-cell;
    width: 1%;
  }
  .nav-tabs.nav-justified > li > a {
    margin-bottom: 0;
  }
}
.nav-tabs.nav-justified > li > a {
  margin-right: 0;
  border-radius: 2px;
}
.nav-tabs.nav-justified > .active > a,
.nav-tabs.nav-justified > .active > a:hover,
.nav-tabs.nav-justified > .active > a:focus {
  border: 1px solid #ddd;
}
@media (min-width: 768px) {
  .nav-tabs.nav-justified > li > a {
    border-bottom: 1px solid #ddd;
    border-radius: 2px 2px 0 0;
  }
  .nav-tabs.nav-justified > .active > a,
  .nav-tabs.nav-justified > .active > a:hover,
  .nav-tabs.nav-justified > .active > a:focus {
    border-bottom-color: #fff;
  }
}
.nav-pills > li {
  float: left;
}
.nav-pills > li > a {
  border-radius: 2px;
}
.nav-pills > li + li {
  margin-left: 2px;
}
.nav-pills > li.active > a,
.nav-pills > li.active > a:hover,
.nav-pills > li.active > a:focus {
  color: #fff;
  background-color: #337ab7;
}
.nav-stacked > li {
  float: none;
}
.nav-stacked > li + li {
  margin-top: 2px;
  margin-left: 0;
}
.nav-justified {
  width: 100%;
}
.nav-justified > li {
  float: none;
}
.nav-justified > li > a {
  text-align: center;
  margin-bottom: 5px;
}
.nav-justified > .dropdown .dropdown-menu {
  top: auto;
  left: auto;
}
@media (min-width: 768px) {
  .nav-justified > li {
    display: table-cell;
    width: 1%;
  }
  .nav-justified > li > a {
    margin-bottom: 0;
  }
}
.nav-tabs-justified {
  border-bottom: 0;
}
.nav-tabs-justified > li > a {
  margin-right: 0;
  border-radius: 2px;
}
.nav-tabs-justified > .active > a,
.nav-tabs-justified > .active > a:hover,
.nav-tabs-justified > .active > a:focus {
  border: 1px solid #ddd;
}
@media (min-width: 768px) {
  .nav-tabs-justified > li > a {
    border-bottom: 1px solid #ddd;
    border-radius: 2px 2px 0 0;
  }
  .nav-tabs-justified > .active > a,
  .nav-tabs-justified > .active > a:hover,
  .nav-tabs-justified > .active > a:focus {
    border-bottom-color: #fff;
  }
}
.tab-content > .tab-pane {
  display: none;
}
.tab-content > .active {
  display: block;
}
.nav-tabs .dropdown-menu {
  margin-top: -1px;
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.navbar {
  position: relative;
  min-height: 30px;
  margin-bottom: 18px;
  border: 1px solid transparent;
}
@media (min-width: 541px) {
  .navbar {
    border-radius: 2px;
  }
}
@media (min-width: 541px) {
  .navbar-header {
    float: left;
  }
}
.navbar-collapse {
  overflow-x: visible;
  padding-right: 0px;
  padding-left: 0px;
  border-top: 1px solid transparent;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1);
  -webkit-overflow-scrolling: touch;
}
.navbar-collapse.in {
  overflow-y: auto;
}
@media (min-width: 541px) {
  .navbar-collapse {
    width: auto;
    border-top: 0;
    box-shadow: none;
  }
  .navbar-collapse.collapse {
    display: block !important;
    height: auto !important;
    padding-bottom: 0;
    overflow: visible !important;
  }
  .navbar-collapse.in {
    overflow-y: visible;
  }
  .navbar-fixed-top .navbar-collapse,
  .navbar-static-top .navbar-collapse,
  .navbar-fixed-bottom .navbar-collapse {
    padding-left: 0;
    padding-right: 0;
  }
}
.navbar-fixed-top .navbar-collapse,
.navbar-fixed-bottom .navbar-collapse {
  max-height: 340px;
}
@media (max-device-width: 540px) and (orientation: landscape) {
  .navbar-fixed-top .navbar-collapse,
  .navbar-fixed-bottom .navbar-collapse {
    max-height: 200px;
  }
}
.container > .navbar-header,
.container-fluid > .navbar-header,
.container > .navbar-collapse,
.container-fluid > .navbar-collapse {
  margin-right: 0px;
  margin-left: 0px;
}
@media (min-width: 541px) {
  .container > .navbar-header,
  .container-fluid > .navbar-header,
  .container > .navbar-collapse,
  .container-fluid > .navbar-collapse {
    margin-right: 0;
    margin-left: 0;
  }
}
.navbar-static-top {
  z-index: 1000;
  border-width: 0 0 1px;
}
@media (min-width: 541px) {
  .navbar-static-top {
    border-radius: 0;
  }
}
.navbar-fixed-top,
.navbar-fixed-bottom {
  position: fixed;
  right: 0;
  left: 0;
  z-index: 1030;
}
@media (min-width: 541px) {
  .navbar-fixed-top,
  .navbar-fixed-bottom {
    border-radius: 0;
  }
}
.navbar-fixed-top {
  top: 0;
  border-width: 0 0 1px;
}
.navbar-fixed-bottom {
  bottom: 0;
  margin-bottom: 0;
  border-width: 1px 0 0;
}
.navbar-brand {
  float: left;
  padding: 6px 0px;
  font-size: 17px;
  line-height: 18px;
  height: 30px;
}
.navbar-brand:hover,
.navbar-brand:focus {
  text-decoration: none;
}
.navbar-brand > img {
  display: block;
}
@media (min-width: 541px) {
  .navbar > .container .navbar-brand,
  .navbar > .container-fluid .navbar-brand {
    margin-left: 0px;
  }
}
.navbar-toggle {
  position: relative;
  float: right;
  margin-right: 0px;
  padding: 9px 10px;
  margin-top: -2px;
  margin-bottom: -2px;
  background-color: transparent;
  background-image: none;
  border: 1px solid transparent;
  border-radius: 2px;
}
.navbar-toggle:focus {
  outline: 0;
}
.navbar-toggle .icon-bar {
  display: block;
  width: 22px;
  height: 2px;
  border-radius: 1px;
}
.navbar-toggle .icon-bar + .icon-bar {
  margin-top: 4px;
}
@media (min-width: 541px) {
  .navbar-toggle {
    display: none;
  }
}
.navbar-nav {
  margin: 3px 0px;
}
.navbar-nav > li > a {
  padding-top: 10px;
  padding-bottom: 10px;
  line-height: 18px;
}
@media (max-width: 540px) {
  .navbar-nav .open .dropdown-menu {
    position: static;
    float: none;
    width: auto;
    margin-top: 0;
    background-color: transparent;
    border: 0;
    box-shadow: none;
  }
  .navbar-nav .open .dropdown-menu > li > a,
  .navbar-nav .open .dropdown-menu .dropdown-header {
    padding: 5px 15px 5px 25px;
  }
  .navbar-nav .open .dropdown-menu > li > a {
    line-height: 18px;
  }
  .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-nav .open .dropdown-menu > li > a:focus {
    background-image: none;
  }
}
@media (min-width: 541px) {
  .navbar-nav {
    float: left;
    margin: 0;
  }
  .navbar-nav > li {
    float: left;
  }
  .navbar-nav > li > a {
    padding-top: 6px;
    padding-bottom: 6px;
  }
}
.navbar-form {
  margin-left: 0px;
  margin-right: 0px;
  padding: 10px 0px;
  border-top: 1px solid transparent;
  border-bottom: 1px solid transparent;
  -webkit-box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1), 0 1px 0 rgba(255, 255, 255, 0.1);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1), 0 1px 0 rgba(255, 255, 255, 0.1);
  margin-top: -1px;
  margin-bottom: -1px;
}
@media (min-width: 768px) {
  .navbar-form .form-group {
    display: inline-block;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .form-control {
    display: inline-block;
    width: auto;
    vertical-align: middle;
  }
  .navbar-form .form-control-static {
    display: inline-block;
  }
  .navbar-form .input-group {
    display: inline-table;
    vertical-align: middle;
  }
  .navbar-form .input-group .input-group-addon,
  .navbar-form .input-group .input-group-btn,
  .navbar-form .input-group .form-control {
    width: auto;
  }
  .navbar-form .input-group > .form-control {
    width: 100%;
  }
  .navbar-form .control-label {
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .radio,
  .navbar-form .checkbox {
    display: inline-block;
    margin-top: 0;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .radio label,
  .navbar-form .checkbox label {
    padding-left: 0;
  }
  .navbar-form .radio input[type="radio"],
  .navbar-form .checkbox input[type="checkbox"] {
    position: relative;
    margin-left: 0;
  }
  .navbar-form .has-feedback .form-control-feedback {
    top: 0;
  }
}
@media (max-width: 540px) {
  .navbar-form .form-group {
    margin-bottom: 5px;
  }
  .navbar-form .form-group:last-child {
    margin-bottom: 0;
  }
}
@media (min-width: 541px) {
  .navbar-form {
    width: auto;
    border: 0;
    margin-left: 0;
    margin-right: 0;
    padding-top: 0;
    padding-bottom: 0;
    -webkit-box-shadow: none;
    box-shadow: none;
  }
}
.navbar-nav > li > .dropdown-menu {
  margin-top: 0;
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.navbar-fixed-bottom .navbar-nav > li > .dropdown-menu {
  margin-bottom: 0;
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.navbar-btn {
  margin-top: -1px;
  margin-bottom: -1px;
}
.navbar-btn.btn-sm {
  margin-top: 0px;
  margin-bottom: 0px;
}
.navbar-btn.btn-xs {
  margin-top: 4px;
  margin-bottom: 4px;
}
.navbar-text {
  margin-top: 6px;
  margin-bottom: 6px;
}
@media (min-width: 541px) {
  .navbar-text {
    float: left;
    margin-left: 0px;
    margin-right: 0px;
  }
}
@media (min-width: 541px) {
  .navbar-left {
    float: left !important;
    float: left;
  }
  .navbar-right {
    float: right !important;
    float: right;
    margin-right: 0px;
  }
  .navbar-right ~ .navbar-right {
    margin-right: 0;
  }
}
.navbar-default {
  background-color: #f8f8f8;
  border-color: #e7e7e7;
}
.navbar-default .navbar-brand {
  color: #777;
}
.navbar-default .navbar-brand:hover,
.navbar-default .navbar-brand:focus {
  color: #5e5e5e;
  background-color: transparent;
}
.navbar-default .navbar-text {
  color: #777;
}
.navbar-default .navbar-nav > li > a {
  color: #777;
}
.navbar-default .navbar-nav > li > a:hover,
.navbar-default .navbar-nav > li > a:focus {
  color: #333;
  background-color: transparent;
}
.navbar-default .navbar-nav > .active > a,
.navbar-default .navbar-nav > .active > a:hover,
.navbar-default .navbar-nav > .active > a:focus {
  color: #555;
  background-color: #e7e7e7;
}
.navbar-default .navbar-nav > .disabled > a,
.navbar-default .navbar-nav > .disabled > a:hover,
.navbar-default .navbar-nav > .disabled > a:focus {
  color: #ccc;
  background-color: transparent;
}
.navbar-default .navbar-toggle {
  border-color: #ddd;
}
.navbar-default .navbar-toggle:hover,
.navbar-default .navbar-toggle:focus {
  background-color: #ddd;
}
.navbar-default .navbar-toggle .icon-bar {
  background-color: #888;
}
.navbar-default .navbar-collapse,
.navbar-default .navbar-form {
  border-color: #e7e7e7;
}
.navbar-default .navbar-nav > .open > a,
.navbar-default .navbar-nav > .open > a:hover,
.navbar-default .navbar-nav > .open > a:focus {
  background-color: #e7e7e7;
  color: #555;
}
@media (max-width: 540px) {
  .navbar-default .navbar-nav .open .dropdown-menu > li > a {
    color: #777;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > li > a:focus {
    color: #333;
    background-color: transparent;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a,
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a:focus {
    color: #555;
    background-color: #e7e7e7;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a,
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a:focus {
    color: #ccc;
    background-color: transparent;
  }
}
.navbar-default .navbar-link {
  color: #777;
}
.navbar-default .navbar-link:hover {
  color: #333;
}
.navbar-default .btn-link {
  color: #777;
}
.navbar-default .btn-link:hover,
.navbar-default .btn-link:focus {
  color: #333;
}
.navbar-default .btn-link[disabled]:hover,
fieldset[disabled] .navbar-default .btn-link:hover,
.navbar-default .btn-link[disabled]:focus,
fieldset[disabled] .navbar-default .btn-link:focus {
  color: #ccc;
}
.navbar-inverse {
  background-color: #222;
  border-color: #080808;
}
.navbar-inverse .navbar-brand {
  color: #9d9d9d;
}
.navbar-inverse .navbar-brand:hover,
.navbar-inverse .navbar-brand:focus {
  color: #fff;
  background-color: transparent;
}
.navbar-inverse .navbar-text {
  color: #9d9d9d;
}
.navbar-inverse .navbar-nav > li > a {
  color: #9d9d9d;
}
.navbar-inverse .navbar-nav > li > a:hover,
.navbar-inverse .navbar-nav > li > a:focus {
  color: #fff;
  background-color: transparent;
}
.navbar-inverse .navbar-nav > .active > a,
.navbar-inverse .navbar-nav > .active > a:hover,
.navbar-inverse .navbar-nav > .active > a:focus {
  color: #fff;
  background-color: #080808;
}
.navbar-inverse .navbar-nav > .disabled > a,
.navbar-inverse .navbar-nav > .disabled > a:hover,
.navbar-inverse .navbar-nav > .disabled > a:focus {
  color: #444;
  background-color: transparent;
}
.navbar-inverse .navbar-toggle {
  border-color: #333;
}
.navbar-inverse .navbar-toggle:hover,
.navbar-inverse .navbar-toggle:focus {
  background-color: #333;
}
.navbar-inverse .navbar-toggle .icon-bar {
  background-color: #fff;
}
.navbar-inverse .navbar-collapse,
.navbar-inverse .navbar-form {
  border-color: #101010;
}
.navbar-inverse .navbar-nav > .open > a,
.navbar-inverse .navbar-nav > .open > a:hover,
.navbar-inverse .navbar-nav > .open > a:focus {
  background-color: #080808;
  color: #fff;
}
@media (max-width: 540px) {
  .navbar-inverse .navbar-nav .open .dropdown-menu > .dropdown-header {
    border-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu .divider {
    background-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a {
    color: #9d9d9d;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a:focus {
    color: #fff;
    background-color: transparent;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a:focus {
    color: #fff;
    background-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a:focus {
    color: #444;
    background-color: transparent;
  }
}
.navbar-inverse .navbar-link {
  color: #9d9d9d;
}
.navbar-inverse .navbar-link:hover {
  color: #fff;
}
.navbar-inverse .btn-link {
  color: #9d9d9d;
}
.navbar-inverse .btn-link:hover,
.navbar-inverse .btn-link:focus {
  color: #fff;
}
.navbar-inverse .btn-link[disabled]:hover,
fieldset[disabled] .navbar-inverse .btn-link:hover,
.navbar-inverse .btn-link[disabled]:focus,
fieldset[disabled] .navbar-inverse .btn-link:focus {
  color: #444;
}
.breadcrumb {
  padding: 8px 15px;
  margin-bottom: 18px;
  list-style: none;
  background-color: #f5f5f5;
  border-radius: 2px;
}
.breadcrumb > li {
  display: inline-block;
}
.breadcrumb > li + li:before {
  content: "/\00a0";
  padding: 0 5px;
  color: #5e5e5e;
}
.breadcrumb > .active {
  color: #777777;
}
.pagination {
  display: inline-block;
  padding-left: 0;
  margin: 18px 0;
  border-radius: 2px;
}
.pagination > li {
  display: inline;
}
.pagination > li > a,
.pagination > li > span {
  position: relative;
  float: left;
  padding: 6px 12px;
  line-height: 1.42857143;
  text-decoration: none;
  color: #337ab7;
  background-color: #fff;
  border: 1px solid #ddd;
  margin-left: -1px;
}
.pagination > li:first-child > a,
.pagination > li:first-child > span {
  margin-left: 0;
  border-bottom-left-radius: 2px;
  border-top-left-radius: 2px;
}
.pagination > li:last-child > a,
.pagination > li:last-child > span {
  border-bottom-right-radius: 2px;
  border-top-right-radius: 2px;
}
.pagination > li > a:hover,
.pagination > li > span:hover,
.pagination > li > a:focus,
.pagination > li > span:focus {
  z-index: 2;
  color: #23527c;
  background-color: #eeeeee;
  border-color: #ddd;
}
.pagination > .active > a,
.pagination > .active > span,
.pagination > .active > a:hover,
.pagination > .active > span:hover,
.pagination > .active > a:focus,
.pagination > .active > span:focus {
  z-index: 3;
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
  cursor: default;
}
.pagination > .disabled > span,
.pagination > .disabled > span:hover,
.pagination > .disabled > span:focus,
.pagination > .disabled > a,
.pagination > .disabled > a:hover,
.pagination > .disabled > a:focus {
  color: #777777;
  background-color: #fff;
  border-color: #ddd;
  cursor: not-allowed;
}
.pagination-lg > li > a,
.pagination-lg > li > span {
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
}
.pagination-lg > li:first-child > a,
.pagination-lg > li:first-child > span {
  border-bottom-left-radius: 3px;
  border-top-left-radius: 3px;
}
.pagination-lg > li:last-child > a,
.pagination-lg > li:last-child > span {
  border-bottom-right-radius: 3px;
  border-top-right-radius: 3px;
}
.pagination-sm > li > a,
.pagination-sm > li > span {
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
}
.pagination-sm > li:first-child > a,
.pagination-sm > li:first-child > span {
  border-bottom-left-radius: 1px;
  border-top-left-radius: 1px;
}
.pagination-sm > li:last-child > a,
.pagination-sm > li:last-child > span {
  border-bottom-right-radius: 1px;
  border-top-right-radius: 1px;
}
.pager {
  padding-left: 0;
  margin: 18px 0;
  list-style: none;
  text-align: center;
}
.pager li {
  display: inline;
}
.pager li > a,
.pager li > span {
  display: inline-block;
  padding: 5px 14px;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 15px;
}
.pager li > a:hover,
.pager li > a:focus {
  text-decoration: none;
  background-color: #eeeeee;
}
.pager .next > a,
.pager .next > span {
  float: right;
}
.pager .previous > a,
.pager .previous > span {
  float: left;
}
.pager .disabled > a,
.pager .disabled > a:hover,
.pager .disabled > a:focus,
.pager .disabled > span {
  color: #777777;
  background-color: #fff;
  cursor: not-allowed;
}
.label {
  display: inline;
  padding: .2em .6em .3em;
  font-size: 75%;
  font-weight: bold;
  line-height: 1;
  color: #fff;
  text-align: center;
  white-space: nowrap;
  vertical-align: baseline;
  border-radius: .25em;
}
a.label:hover,
a.label:focus {
  color: #fff;
  text-decoration: none;
  cursor: pointer;
}
.label:empty {
  display: none;
}
.btn .label {
  position: relative;
  top: -1px;
}
.label-default {
  background-color: #777777;
}
.label-default[href]:hover,
.label-default[href]:focus {
  background-color: #5e5e5e;
}
.label-primary {
  background-color: #337ab7;
}
.label-primary[href]:hover,
.label-primary[href]:focus {
  background-color: #286090;
}
.label-success {
  background-color: #5cb85c;
}
.label-success[href]:hover,
.label-success[href]:focus {
  background-color: #449d44;
}
.label-info {
  background-color: #5bc0de;
}
.label-info[href]:hover,
.label-info[href]:focus {
  background-color: #31b0d5;
}
.label-warning {
  background-color: #f0ad4e;
}
.label-warning[href]:hover,
.label-warning[href]:focus {
  background-color: #ec971f;
}
.label-danger {
  background-color: #d9534f;
}
.label-danger[href]:hover,
.label-danger[href]:focus {
  background-color: #c9302c;
}
.badge {
  display: inline-block;
  min-width: 10px;
  padding: 3px 7px;
  font-size: 12px;
  font-weight: bold;
  color: #fff;
  line-height: 1;
  vertical-align: middle;
  white-space: nowrap;
  text-align: center;
  background-color: #777777;
  border-radius: 10px;
}
.badge:empty {
  display: none;
}
.btn .badge {
  position: relative;
  top: -1px;
}
.btn-xs .badge,
.btn-group-xs > .btn .badge {
  top: 0;
  padding: 1px 5px;
}
a.badge:hover,
a.badge:focus {
  color: #fff;
  text-decoration: none;
  cursor: pointer;
}
.list-group-item.active > .badge,
.nav-pills > .active > a > .badge {
  color: #337ab7;
  background-color: #fff;
}
.list-group-item > .badge {
  float: right;
}
.list-group-item > .badge + .badge {
  margin-right: 5px;
}
.nav-pills > li > a > .badge {
  margin-left: 3px;
}
.jumbotron {
  padding-top: 30px;
  padding-bottom: 30px;
  margin-bottom: 30px;
  color: inherit;
  background-color: #eeeeee;
}
.jumbotron h1,
.jumbotron .h1 {
  color: inherit;
}
.jumbotron p {
  margin-bottom: 15px;
  font-size: 20px;
  font-weight: 200;
}
.jumbotron > hr {
  border-top-color: #d5d5d5;
}
.container .jumbotron,
.container-fluid .jumbotron {
  border-radius: 3px;
  padding-left: 0px;
  padding-right: 0px;
}
.jumbotron .container {
  max-width: 100%;
}
@media screen and (min-width: 768px) {
  .jumbotron {
    padding-top: 48px;
    padding-bottom: 48px;
  }
  .container .jumbotron,
  .container-fluid .jumbotron {
    padding-left: 60px;
    padding-right: 60px;
  }
  .jumbotron h1,
  .jumbotron .h1 {
    font-size: 59px;
  }
}
.thumbnail {
  display: block;
  padding: 4px;
  margin-bottom: 18px;
  line-height: 1.42857143;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 2px;
  -webkit-transition: border 0.2s ease-in-out;
  -o-transition: border 0.2s ease-in-out;
  transition: border 0.2s ease-in-out;
}
.thumbnail > img,
.thumbnail a > img {
  margin-left: auto;
  margin-right: auto;
}
a.thumbnail:hover,
a.thumbnail:focus,
a.thumbnail.active {
  border-color: #337ab7;
}
.thumbnail .caption {
  padding: 9px;
  color: #000;
}
.alert {
  padding: 15px;
  margin-bottom: 18px;
  border: 1px solid transparent;
  border-radius: 2px;
}
.alert h4 {
  margin-top: 0;
  color: inherit;
}
.alert .alert-link {
  font-weight: bold;
}
.alert > p,
.alert > ul {
  margin-bottom: 0;
}
.alert > p + p {
  margin-top: 5px;
}
.alert-dismissable,
.alert-dismissible {
  padding-right: 35px;
}
.alert-dismissable .close,
.alert-dismissible .close {
  position: relative;
  top: -2px;
  right: -21px;
  color: inherit;
}
.alert-success {
  background-color: #dff0d8;
  border-color: #d6e9c6;
  color: #3c763d;
}
.alert-success hr {
  border-top-color: #c9e2b3;
}
.alert-success .alert-link {
  color: #2b542c;
}
.alert-info {
  background-color: #d9edf7;
  border-color: #bce8f1;
  color: #31708f;
}
.alert-info hr {
  border-top-color: #a6e1ec;
}
.alert-info .alert-link {
  color: #245269;
}
.alert-warning {
  background-color: #fcf8e3;
  border-color: #faebcc;
  color: #8a6d3b;
}
.alert-warning hr {
  border-top-color: #f7e1b5;
}
.alert-warning .alert-link {
  color: #66512c;
}
.alert-danger {
  background-color: #f2dede;
  border-color: #ebccd1;
  color: #a94442;
}
.alert-danger hr {
  border-top-color: #e4b9c0;
}
.alert-danger .alert-link {
  color: #843534;
}
@-webkit-keyframes progress-bar-stripes {
  from {
    background-position: 40px 0;
  }
  to {
    background-position: 0 0;
  }
}
@keyframes progress-bar-stripes {
  from {
    background-position: 40px 0;
  }
  to {
    background-position: 0 0;
  }
}
.progress {
  overflow: hidden;
  height: 18px;
  margin-bottom: 18px;
  background-color: #f5f5f5;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.1);
  box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.1);
}
.progress-bar {
  float: left;
  width: 0%;
  height: 100%;
  font-size: 12px;
  line-height: 18px;
  color: #fff;
  text-align: center;
  background-color: #337ab7;
  -webkit-box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.15);
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.15);
  -webkit-transition: width 0.6s ease;
  -o-transition: width 0.6s ease;
  transition: width 0.6s ease;
}
.progress-striped .progress-bar,
.progress-bar-striped {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-size: 40px 40px;
}
.progress.active .progress-bar,
.progress-bar.active {
  -webkit-animation: progress-bar-stripes 2s linear infinite;
  -o-animation: progress-bar-stripes 2s linear infinite;
  animation: progress-bar-stripes 2s linear infinite;
}
.progress-bar-success {
  background-color: #5cb85c;
}
.progress-striped .progress-bar-success {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-info {
  background-color: #5bc0de;
}
.progress-striped .progress-bar-info {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-warning {
  background-color: #f0ad4e;
}
.progress-striped .progress-bar-warning {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-danger {
  background-color: #d9534f;
}
.progress-striped .progress-bar-danger {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.media {
  margin-top: 15px;
}
.media:first-child {
  margin-top: 0;
}
.media,
.media-body {
  zoom: 1;
  overflow: hidden;
}
.media-body {
  width: 10000px;
}
.media-object {
  display: block;
}
.media-object.img-thumbnail {
  max-width: none;
}
.media-right,
.media > .pull-right {
  padding-left: 10px;
}
.media-left,
.media > .pull-left {
  padding-right: 10px;
}
.media-left,
.media-right,
.media-body {
  display: table-cell;
  vertical-align: top;
}
.media-middle {
  vertical-align: middle;
}
.media-bottom {
  vertical-align: bottom;
}
.media-heading {
  margin-top: 0;
  margin-bottom: 5px;
}
.media-list {
  padding-left: 0;
  list-style: none;
}
.list-group {
  margin-bottom: 20px;
  padding-left: 0;
}
.list-group-item {
  position: relative;
  display: block;
  padding: 10px 15px;
  margin-bottom: -1px;
  background-color: #fff;
  border: 1px solid #ddd;
}
.list-group-item:first-child {
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
}
.list-group-item:last-child {
  margin-bottom: 0;
  border-bottom-right-radius: 2px;
  border-bottom-left-radius: 2px;
}
a.list-group-item,
button.list-group-item {
  color: #555;
}
a.list-group-item .list-group-item-heading,
button.list-group-item .list-group-item-heading {
  color: #333;
}
a.list-group-item:hover,
button.list-group-item:hover,
a.list-group-item:focus,
button.list-group-item:focus {
  text-decoration: none;
  color: #555;
  background-color: #f5f5f5;
}
button.list-group-item {
  width: 100%;
  text-align: left;
}
.list-group-item.disabled,
.list-group-item.disabled:hover,
.list-group-item.disabled:focus {
  background-color: #eeeeee;
  color: #777777;
  cursor: not-allowed;
}
.list-group-item.disabled .list-group-item-heading,
.list-group-item.disabled:hover .list-group-item-heading,
.list-group-item.disabled:focus .list-group-item-heading {
  color: inherit;
}
.list-group-item.disabled .list-group-item-text,
.list-group-item.disabled:hover .list-group-item-text,
.list-group-item.disabled:focus .list-group-item-text {
  color: #777777;
}
.list-group-item.active,
.list-group-item.active:hover,
.list-group-item.active:focus {
  z-index: 2;
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
}
.list-group-item.active .list-group-item-heading,
.list-group-item.active:hover .list-group-item-heading,
.list-group-item.active:focus .list-group-item-heading,
.list-group-item.active .list-group-item-heading > small,
.list-group-item.active:hover .list-group-item-heading > small,
.list-group-item.active:focus .list-group-item-heading > small,
.list-group-item.active .list-group-item-heading > .small,
.list-group-item.active:hover .list-group-item-heading > .small,
.list-group-item.active:focus .list-group-item-heading > .small {
  color: inherit;
}
.list-group-item.active .list-group-item-text,
.list-group-item.active:hover .list-group-item-text,
.list-group-item.active:focus .list-group-item-text {
  color: #c7ddef;
}
.list-group-item-success {
  color: #3c763d;
  background-color: #dff0d8;
}
a.list-group-item-success,
button.list-group-item-success {
  color: #3c763d;
}
a.list-group-item-success .list-group-item-heading,
button.list-group-item-success .list-group-item-heading {
  color: inherit;
}
a.list-group-item-success:hover,
button.list-group-item-success:hover,
a.list-group-item-success:focus,
button.list-group-item-success:focus {
  color: #3c763d;
  background-color: #d0e9c6;
}
a.list-group-item-success.active,
button.list-group-item-success.active,
a.list-group-item-success.active:hover,
button.list-group-item-success.active:hover,
a.list-group-item-success.active:focus,
button.list-group-item-success.active:focus {
  color: #fff;
  background-color: #3c763d;
  border-color: #3c763d;
}
.list-group-item-info {
  color: #31708f;
  background-color: #d9edf7;
}
a.list-group-item-info,
button.list-group-item-info {
  color: #31708f;
}
a.list-group-item-info .list-group-item-heading,
button.list-group-item-info .list-group-item-heading {
  color: inherit;
}
a.list-group-item-info:hover,
button.list-group-item-info:hover,
a.list-group-item-info:focus,
button.list-group-item-info:focus {
  color: #31708f;
  background-color: #c4e3f3;
}
a.list-group-item-info.active,
button.list-group-item-info.active,
a.list-group-item-info.active:hover,
button.list-group-item-info.active:hover,
a.list-group-item-info.active:focus,
button.list-group-item-info.active:focus {
  color: #fff;
  background-color: #31708f;
  border-color: #31708f;
}
.list-group-item-warning {
  color: #8a6d3b;
  background-color: #fcf8e3;
}
a.list-group-item-warning,
button.list-group-item-warning {
  color: #8a6d3b;
}
a.list-group-item-warning .list-group-item-heading,
button.list-group-item-warning .list-group-item-heading {
  color: inherit;
}
a.list-group-item-warning:hover,
button.list-group-item-warning:hover,
a.list-group-item-warning:focus,
button.list-group-item-warning:focus {
  color: #8a6d3b;
  background-color: #faf2cc;
}
a.list-group-item-warning.active,
button.list-group-item-warning.active,
a.list-group-item-warning.active:hover,
button.list-group-item-warning.active:hover,
a.list-group-item-warning.active:focus,
button.list-group-item-warning.active:focus {
  color: #fff;
  background-color: #8a6d3b;
  border-color: #8a6d3b;
}
.list-group-item-danger {
  color: #a94442;
  background-color: #f2dede;
}
a.list-group-item-danger,
button.list-group-item-danger {
  color: #a94442;
}
a.list-group-item-danger .list-group-item-heading,
button.list-group-item-danger .list-group-item-heading {
  color: inherit;
}
a.list-group-item-danger:hover,
button.list-group-item-danger:hover,
a.list-group-item-danger:focus,
button.list-group-item-danger:focus {
  color: #a94442;
  background-color: #ebcccc;
}
a.list-group-item-danger.active,
button.list-group-item-danger.active,
a.list-group-item-danger.active:hover,
button.list-group-item-danger.active:hover,
a.list-group-item-danger.active:focus,
button.list-group-item-danger.active:focus {
  color: #fff;
  background-color: #a94442;
  border-color: #a94442;
}
.list-group-item-heading {
  margin-top: 0;
  margin-bottom: 5px;
}
.list-group-item-text {
  margin-bottom: 0;
  line-height: 1.3;
}
.panel {
  margin-bottom: 18px;
  background-color: #fff;
  border: 1px solid transparent;
  border-radius: 2px;
  -webkit-box-shadow: 0 1px 1px rgba(0, 0, 0, 0.05);
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.05);
}
.panel-body {
  padding: 15px;
}
.panel-heading {
  padding: 10px 15px;
  border-bottom: 1px solid transparent;
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel-heading > .dropdown .dropdown-toggle {
  color: inherit;
}
.panel-title {
  margin-top: 0;
  margin-bottom: 0;
  font-size: 15px;
  color: inherit;
}
.panel-title > a,
.panel-title > small,
.panel-title > .small,
.panel-title > small > a,
.panel-title > .small > a {
  color: inherit;
}
.panel-footer {
  padding: 10px 15px;
  background-color: #f5f5f5;
  border-top: 1px solid #ddd;
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .list-group,
.panel > .panel-collapse > .list-group {
  margin-bottom: 0;
}
.panel > .list-group .list-group-item,
.panel > .panel-collapse > .list-group .list-group-item {
  border-width: 1px 0;
  border-radius: 0;
}
.panel > .list-group:first-child .list-group-item:first-child,
.panel > .panel-collapse > .list-group:first-child .list-group-item:first-child {
  border-top: 0;
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel > .list-group:last-child .list-group-item:last-child,
.panel > .panel-collapse > .list-group:last-child .list-group-item:last-child {
  border-bottom: 0;
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .panel-heading + .panel-collapse > .list-group .list-group-item:first-child {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.panel-heading + .list-group .list-group-item:first-child {
  border-top-width: 0;
}
.list-group + .panel-footer {
  border-top-width: 0;
}
.panel > .table,
.panel > .table-responsive > .table,
.panel > .panel-collapse > .table {
  margin-bottom: 0;
}
.panel > .table caption,
.panel > .table-responsive > .table caption,
.panel > .panel-collapse > .table caption {
  padding-left: 15px;
  padding-right: 15px;
}
.panel > .table:first-child,
.panel > .table-responsive:first-child > .table:first-child {
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child {
  border-top-left-radius: 1px;
  border-top-right-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child td:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child td:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child td:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child td:first-child,
.panel > .table:first-child > thead:first-child > tr:first-child th:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child th:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child th:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child th:first-child {
  border-top-left-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child td:last-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child td:last-child,
.panel > .table:first-child > tbody:first-child > tr:first-child td:last-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child td:last-child,
.panel > .table:first-child > thead:first-child > tr:first-child th:last-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child th:last-child,
.panel > .table:first-child > tbody:first-child > tr:first-child th:last-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child th:last-child {
  border-top-right-radius: 1px;
}
.panel > .table:last-child,
.panel > .table-responsive:last-child > .table:last-child {
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child {
  border-bottom-left-radius: 1px;
  border-bottom-right-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child td:first-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child td:first-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child td:first-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child td:first-child,
.panel > .table:last-child > tbody:last-child > tr:last-child th:first-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child th:first-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child th:first-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child th:first-child {
  border-bottom-left-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child td:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child td:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child td:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child td:last-child,
.panel > .table:last-child > tbody:last-child > tr:last-child th:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child th:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child th:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child th:last-child {
  border-bottom-right-radius: 1px;
}
.panel > .panel-body + .table,
.panel > .panel-body + .table-responsive,
.panel > .table + .panel-body,
.panel > .table-responsive + .panel-body {
  border-top: 1px solid #ddd;
}
.panel > .table > tbody:first-child > tr:first-child th,
.panel > .table > tbody:first-child > tr:first-child td {
  border-top: 0;
}
.panel > .table-bordered,
.panel > .table-responsive > .table-bordered {
  border: 0;
}
.panel > .table-bordered > thead > tr > th:first-child,
.panel > .table-responsive > .table-bordered > thead > tr > th:first-child,
.panel > .table-bordered > tbody > tr > th:first-child,
.panel > .table-responsive > .table-bordered > tbody > tr > th:first-child,
.panel > .table-bordered > tfoot > tr > th:first-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > th:first-child,
.panel > .table-bordered > thead > tr > td:first-child,
.panel > .table-responsive > .table-bordered > thead > tr > td:first-child,
.panel > .table-bordered > tbody > tr > td:first-child,
.panel > .table-responsive > .table-bordered > tbody > tr > td:first-child,
.panel > .table-bordered > tfoot > tr > td:first-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > td:first-child {
  border-left: 0;
}
.panel > .table-bordered > thead > tr > th:last-child,
.panel > .table-responsive > .table-bordered > thead > tr > th:last-child,
.panel > .table-bordered > tbody > tr > th:last-child,
.panel > .table-responsive > .table-bordered > tbody > tr > th:last-child,
.panel > .table-bordered > tfoot > tr > th:last-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > th:last-child,
.panel > .table-bordered > thead > tr > td:last-child,
.panel > .table-responsive > .table-bordered > thead > tr > td:last-child,
.panel > .table-bordered > tbody > tr > td:last-child,
.panel > .table-responsive > .table-bordered > tbody > tr > td:last-child,
.panel > .table-bordered > tfoot > tr > td:last-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > td:last-child {
  border-right: 0;
}
.panel > .table-bordered > thead > tr:first-child > td,
.panel > .table-responsive > .table-bordered > thead > tr:first-child > td,
.panel > .table-bordered > tbody > tr:first-child > td,
.panel > .table-responsive > .table-bordered > tbody > tr:first-child > td,
.panel > .table-bordered > thead > tr:first-child > th,
.panel > .table-responsive > .table-bordered > thead > tr:first-child > th,
.panel > .table-bordered > tbody > tr:first-child > th,
.panel > .table-responsive > .table-bordered > tbody > tr:first-child > th {
  border-bottom: 0;
}
.panel > .table-bordered > tbody > tr:last-child > td,
.panel > .table-responsive > .table-bordered > tbody > tr:last-child > td,
.panel > .table-bordered > tfoot > tr:last-child > td,
.panel > .table-responsive > .table-bordered > tfoot > tr:last-child > td,
.panel > .table-bordered > tbody > tr:last-child > th,
.panel > .table-responsive > .table-bordered > tbody > tr:last-child > th,
.panel > .table-bordered > tfoot > tr:last-child > th,
.panel > .table-responsive > .table-bordered > tfoot > tr:last-child > th {
  border-bottom: 0;
}
.panel > .table-responsive {
  border: 0;
  margin-bottom: 0;
}
.panel-group {
  margin-bottom: 18px;
}
.panel-group .panel {
  margin-bottom: 0;
  border-radius: 2px;
}
.panel-group .panel + .panel {
  margin-top: 5px;
}
.panel-group .panel-heading {
  border-bottom: 0;
}
.panel-group .panel-heading + .panel-collapse > .panel-body,
.panel-group .panel-heading + .panel-collapse > .list-group {
  border-top: 1px solid #ddd;
}
.panel-group .panel-footer {
  border-top: 0;
}
.panel-group .panel-footer + .panel-collapse .panel-body {
  border-bottom: 1px solid #ddd;
}
.panel-default {
  border-color: #ddd;
}
.panel-default > .panel-heading {
  color: #333333;
  background-color: #f5f5f5;
  border-color: #ddd;
}
.panel-default > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #ddd;
}
.panel-default > .panel-heading .badge {
  color: #f5f5f5;
  background-color: #333333;
}
.panel-default > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #ddd;
}
.panel-primary {
  border-color: #337ab7;
}
.panel-primary > .panel-heading {
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
}
.panel-primary > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #337ab7;
}
.panel-primary > .panel-heading .badge {
  color: #337ab7;
  background-color: #fff;
}
.panel-primary > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #337ab7;
}
.panel-success {
  border-color: #d6e9c6;
}
.panel-success > .panel-heading {
  color: #3c763d;
  background-color: #dff0d8;
  border-color: #d6e9c6;
}
.panel-success > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #d6e9c6;
}
.panel-success > .panel-heading .badge {
  color: #dff0d8;
  background-color: #3c763d;
}
.panel-success > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #d6e9c6;
}
.panel-info {
  border-color: #bce8f1;
}
.panel-info > .panel-heading {
  color: #31708f;
  background-color: #d9edf7;
  border-color: #bce8f1;
}
.panel-info > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #bce8f1;
}
.panel-info > .panel-heading .badge {
  color: #d9edf7;
  background-color: #31708f;
}
.panel-info > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #bce8f1;
}
.panel-warning {
  border-color: #faebcc;
}
.panel-warning > .panel-heading {
  color: #8a6d3b;
  background-color: #fcf8e3;
  border-color: #faebcc;
}
.panel-warning > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #faebcc;
}
.panel-warning > .panel-heading .badge {
  color: #fcf8e3;
  background-color: #8a6d3b;
}
.panel-warning > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #faebcc;
}
.panel-danger {
  border-color: #ebccd1;
}
.panel-danger > .panel-heading {
  color: #a94442;
  background-color: #f2dede;
  border-color: #ebccd1;
}
.panel-danger > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #ebccd1;
}
.panel-danger > .panel-heading .badge {
  color: #f2dede;
  background-color: #a94442;
}
.panel-danger > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #ebccd1;
}
.embed-responsive {
  position: relative;
  display: block;
  height: 0;
  padding: 0;
  overflow: hidden;
}
.embed-responsive .embed-responsive-item,
.embed-responsive iframe,
.embed-responsive embed,
.embed-responsive object,
.embed-responsive video {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  height: 100%;
  width: 100%;
  border: 0;
}
.embed-responsive-16by9 {
  padding-bottom: 56.25%;
}
.embed-responsive-4by3 {
  padding-bottom: 75%;
}
.well {
  min-height: 20px;
  padding: 19px;
  margin-bottom: 20px;
  background-color: #f5f5f5;
  border: 1px solid #e3e3e3;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.05);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.05);
}
.well blockquote {
  border-color: #ddd;
  border-color: rgba(0, 0, 0, 0.15);
}
.well-lg {
  padding: 24px;
  border-radius: 3px;
}
.well-sm {
  padding: 9px;
  border-radius: 1px;
}
.close {
  float: right;
  font-size: 19.5px;
  font-weight: bold;
  line-height: 1;
  color: #000;
  text-shadow: 0 1px 0 #fff;
  opacity: 0.2;
  filter: alpha(opacity=20);
}
.close:hover,
.close:focus {
  color: #000;
  text-decoration: none;
  cursor: pointer;
  opacity: 0.5;
  filter: alpha(opacity=50);
}
button.close {
  padding: 0;
  cursor: pointer;
  background: transparent;
  border: 0;
  -webkit-appearance: none;
}
.modal-open {
  overflow: hidden;
}
.modal {
  display: none;
  overflow: hidden;
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 1050;
  -webkit-overflow-scrolling: touch;
  outline: 0;
}
.modal.fade .modal-dialog {
  -webkit-transform: translate(0, -25%);
  -ms-transform: translate(0, -25%);
  -o-transform: translate(0, -25%);
  transform: translate(0, -25%);
  -webkit-transition: -webkit-transform 0.3s ease-out;
  -moz-transition: -moz-transform 0.3s ease-out;
  -o-transition: -o-transform 0.3s ease-out;
  transition: transform 0.3s ease-out;
}
.modal.in .modal-dialog {
  -webkit-transform: translate(0, 0);
  -ms-transform: translate(0, 0);
  -o-transform: translate(0, 0);
  transform: translate(0, 0);
}
.modal-open .modal {
  overflow-x: hidden;
  overflow-y: auto;
}
.modal-dialog {
  position: relative;
  width: auto;
  margin: 10px;
}
.modal-content {
  position: relative;
  background-color: #fff;
  border: 1px solid #999;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 3px;
  -webkit-box-shadow: 0 3px 9px rgba(0, 0, 0, 0.5);
  box-shadow: 0 3px 9px rgba(0, 0, 0, 0.5);
  background-clip: padding-box;
  outline: 0;
}
.modal-backdrop {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 1040;
  background-color: #000;
}
.modal-backdrop.fade {
  opacity: 0;
  filter: alpha(opacity=0);
}
.modal-backdrop.in {
  opacity: 0.5;
  filter: alpha(opacity=50);
}
.modal-header {
  padding: 15px;
  border-bottom: 1px solid #e5e5e5;
}
.modal-header .close {
  margin-top: -2px;
}
.modal-title {
  margin: 0;
  line-height: 1.42857143;
}
.modal-body {
  position: relative;
  padding: 15px;
}
.modal-footer {
  padding: 15px;
  text-align: right;
  border-top: 1px solid #e5e5e5;
}
.modal-footer .btn + .btn {
  margin-left: 5px;
  margin-bottom: 0;
}
.modal-footer .btn-group .btn + .btn {
  margin-left: -1px;
}
.modal-footer .btn-block + .btn-block {
  margin-left: 0;
}
.modal-scrollbar-measure {
  position: absolute;
  top: -9999px;
  width: 50px;
  height: 50px;
  overflow: scroll;
}
@media (min-width: 768px) {
  .modal-dialog {
    width: 600px;
    margin: 30px auto;
  }
  .modal-content {
    -webkit-box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
  }
  .modal-sm {
    width: 300px;
  }
}
@media (min-width: 992px) {
  .modal-lg {
    width: 900px;
  }
}
.tooltip {
  position: absolute;
  z-index: 1070;
  display: block;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-style: normal;
  font-weight: normal;
  letter-spacing: normal;
  line-break: auto;
  line-height: 1.42857143;
  text-align: left;
  text-align: start;
  text-decoration: none;
  text-shadow: none;
  text-transform: none;
  white-space: normal;
  word-break: normal;
  word-spacing: normal;
  word-wrap: normal;
  font-size: 12px;
  opacity: 0;
  filter: alpha(opacity=0);
}
.tooltip.in {
  opacity: 0.9;
  filter: alpha(opacity=90);
}
.tooltip.top {
  margin-top: -3px;
  padding: 5px 0;
}
.tooltip.right {
  margin-left: 3px;
  padding: 0 5px;
}
.tooltip.bottom {
  margin-top: 3px;
  padding: 5px 0;
}
.tooltip.left {
  margin-left: -3px;
  padding: 0 5px;
}
.tooltip-inner {
  max-width: 200px;
  padding: 3px 8px;
  color: #fff;
  text-align: center;
  background-color: #000;
  border-radius: 2px;
}
.tooltip-arrow {
  position: absolute;
  width: 0;
  height: 0;
  border-color: transparent;
  border-style: solid;
}
.tooltip.top .tooltip-arrow {
  bottom: 0;
  left: 50%;
  margin-left: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.top-left .tooltip-arrow {
  bottom: 0;
  right: 5px;
  margin-bottom: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.top-right .tooltip-arrow {
  bottom: 0;
  left: 5px;
  margin-bottom: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.right .tooltip-arrow {
  top: 50%;
  left: 0;
  margin-top: -5px;
  border-width: 5px 5px 5px 0;
  border-right-color: #000;
}
.tooltip.left .tooltip-arrow {
  top: 50%;
  right: 0;
  margin-top: -5px;
  border-width: 5px 0 5px 5px;
  border-left-color: #000;
}
.tooltip.bottom .tooltip-arrow {
  top: 0;
  left: 50%;
  margin-left: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.tooltip.bottom-left .tooltip-arrow {
  top: 0;
  right: 5px;
  margin-top: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.tooltip.bottom-right .tooltip-arrow {
  top: 0;
  left: 5px;
  margin-top: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.popover {
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1060;
  display: none;
  max-width: 276px;
  padding: 1px;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-style: normal;
  font-weight: normal;
  letter-spacing: normal;
  line-break: auto;
  line-height: 1.42857143;
  text-align: left;
  text-align: start;
  text-decoration: none;
  text-shadow: none;
  text-transform: none;
  white-space: normal;
  word-break: normal;
  word-spacing: normal;
  word-wrap: normal;
  font-size: 13px;
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid #ccc;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 3px;
  -webkit-box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
}
.popover.top {
  margin-top: -10px;
}
.popover.right {
  margin-left: 10px;
}
.popover.bottom {
  margin-top: 10px;
}
.popover.left {
  margin-left: -10px;
}
.popover-title {
  margin: 0;
  padding: 8px 14px;
  font-size: 13px;
  background-color: #f7f7f7;
  border-bottom: 1px solid #ebebeb;
  border-radius: 2px 2px 0 0;
}
.popover-content {
  padding: 9px 14px;
}
.popover > .arrow,
.popover > .arrow:after {
  position: absolute;
  display: block;
  width: 0;
  height: 0;
  border-color: transparent;
  border-style: solid;
}
.popover > .arrow {
  border-width: 11px;
}
.popover > .arrow:after {
  border-width: 10px;
  content: "";
}
.popover.top > .arrow {
  left: 50%;
  margin-left: -11px;
  border-bottom-width: 0;
  border-top-color: #999999;
  border-top-color: rgba(0, 0, 0, 0.25);
  bottom: -11px;
}
.popover.top > .arrow:after {
  content: " ";
  bottom: 1px;
  margin-left: -10px;
  border-bottom-width: 0;
  border-top-color: #fff;
}
.popover.right > .arrow {
  top: 50%;
  left: -11px;
  margin-top: -11px;
  border-left-width: 0;
  border-right-color: #999999;
  border-right-color: rgba(0, 0, 0, 0.25);
}
.popover.right > .arrow:after {
  content: " ";
  left: 1px;
  bottom: -10px;
  border-left-width: 0;
  border-right-color: #fff;
}
.popover.bottom > .arrow {
  left: 50%;
  margin-left: -11px;
  border-top-width: 0;
  border-bottom-color: #999999;
  border-bottom-color: rgba(0, 0, 0, 0.25);
  top: -11px;
}
.popover.bottom > .arrow:after {
  content: " ";
  top: 1px;
  margin-left: -10px;
  border-top-width: 0;
  border-bottom-color: #fff;
}
.popover.left > .arrow {
  top: 50%;
  right: -11px;
  margin-top: -11px;
  border-right-width: 0;
  border-left-color: #999999;
  border-left-color: rgba(0, 0, 0, 0.25);
}
.popover.left > .arrow:after {
  content: " ";
  right: 1px;
  border-right-width: 0;
  border-left-color: #fff;
  bottom: -10px;
}
.carousel {
  position: relative;
}
.carousel-inner {
  position: relative;
  overflow: hidden;
  width: 100%;
}
.carousel-inner > .item {
  display: none;
  position: relative;
  -webkit-transition: 0.6s ease-in-out left;
  -o-transition: 0.6s ease-in-out left;
  transition: 0.6s ease-in-out left;
}
.carousel-inner > .item > img,
.carousel-inner > .item > a > img {
  line-height: 1;
}
@media all and (transform-3d), (-webkit-transform-3d) {
  .carousel-inner > .item {
    -webkit-transition: -webkit-transform 0.6s ease-in-out;
    -moz-transition: -moz-transform 0.6s ease-in-out;
    -o-transition: -o-transform 0.6s ease-in-out;
    transition: transform 0.6s ease-in-out;
    -webkit-backface-visibility: hidden;
    -moz-backface-visibility: hidden;
    backface-visibility: hidden;
    -webkit-perspective: 1000px;
    -moz-perspective: 1000px;
    perspective: 1000px;
  }
  .carousel-inner > .item.next,
  .carousel-inner > .item.active.right {
    -webkit-transform: translate3d(100%, 0, 0);
    transform: translate3d(100%, 0, 0);
    left: 0;
  }
  .carousel-inner > .item.prev,
  .carousel-inner > .item.active.left {
    -webkit-transform: translate3d(-100%, 0, 0);
    transform: translate3d(-100%, 0, 0);
    left: 0;
  }
  .carousel-inner > .item.next.left,
  .carousel-inner > .item.prev.right,
  .carousel-inner > .item.active {
    -webkit-transform: translate3d(0, 0, 0);
    transform: translate3d(0, 0, 0);
    left: 0;
  }
}
.carousel-inner > .active,
.carousel-inner > .next,
.carousel-inner > .prev {
  display: block;
}
.carousel-inner > .active {
  left: 0;
}
.carousel-inner > .next,
.carousel-inner > .prev {
  position: absolute;
  top: 0;
  width: 100%;
}
.carousel-inner > .next {
  left: 100%;
}
.carousel-inner > .prev {
  left: -100%;
}
.carousel-inner > .next.left,
.carousel-inner > .prev.right {
  left: 0;
}
.carousel-inner > .active.left {
  left: -100%;
}
.carousel-inner > .active.right {
  left: 100%;
}
.carousel-control {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  width: 15%;
  opacity: 0.5;
  filter: alpha(opacity=50);
  font-size: 20px;
  color: #fff;
  text-align: center;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.6);
  background-color: rgba(0, 0, 0, 0);
}
.carousel-control.left {
  background-image: -webkit-linear-gradient(left, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-image: -o-linear-gradient(left, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-image: linear-gradient(to right, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-repeat: repeat-x;
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#80000000', endColorstr='#00000000', GradientType=1);
}
.carousel-control.right {
  left: auto;
  right: 0;
  background-image: -webkit-linear-gradient(left, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-image: -o-linear-gradient(left, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-image: linear-gradient(to right, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-repeat: repeat-x;
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#00000000', endColorstr='#80000000', GradientType=1);
}
.carousel-control:hover,
.carousel-control:focus {
  outline: 0;
  color: #fff;
  text-decoration: none;
  opacity: 0.9;
  filter: alpha(opacity=90);
}
.carousel-control .icon-prev,
.carousel-control .icon-next,
.carousel-control .glyphicon-chevron-left,
.carousel-control .glyphicon-chevron-right {
  position: absolute;
  top: 50%;
  margin-top: -10px;
  z-index: 5;
  display: inline-block;
}
.carousel-control .icon-prev,
.carousel-control .glyphicon-chevron-left {
  left: 50%;
  margin-left: -10px;
}
.carousel-control .icon-next,
.carousel-control .glyphicon-chevron-right {
  right: 50%;
  margin-right: -10px;
}
.carousel-control .icon-prev,
.carousel-control .icon-next {
  width: 20px;
  height: 20px;
  line-height: 1;
  font-family: serif;
}
.carousel-control .icon-prev:before {
  content: '\2039';
}
.carousel-control .icon-next:before {
  content: '\203a';
}
.carousel-indicators {
  position: absolute;
  bottom: 10px;
  left: 50%;
  z-index: 15;
  width: 60%;
  margin-left: -30%;
  padding-left: 0;
  list-style: none;
  text-align: center;
}
.carousel-indicators li {
  display: inline-block;
  width: 10px;
  height: 10px;
  margin: 1px;
  text-indent: -999px;
  border: 1px solid #fff;
  border-radius: 10px;
  cursor: pointer;
  background-color: #000 \9;
  background-color: rgba(0, 0, 0, 0);
}
.carousel-indicators .active {
  margin: 0;
  width: 12px;
  height: 12px;
  background-color: #fff;
}
.carousel-caption {
  position: absolute;
  left: 15%;
  right: 15%;
  bottom: 20px;
  z-index: 10;
  padding-top: 20px;
  padding-bottom: 20px;
  color: #fff;
  text-align: center;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.6);
}
.carousel-caption .btn {
  text-shadow: none;
}
@media screen and (min-width: 768px) {
  .carousel-control .glyphicon-chevron-left,
  .carousel-control .glyphicon-chevron-right,
  .carousel-control .icon-prev,
  .carousel-control .icon-next {
    width: 30px;
    height: 30px;
    margin-top: -10px;
    font-size: 30px;
  }
  .carousel-control .glyphicon-chevron-left,
  .carousel-control .icon-prev {
    margin-left: -10px;
  }
  .carousel-control .glyphicon-chevron-right,
  .carousel-control .icon-next {
    margin-right: -10px;
  }
  .carousel-caption {
    left: 20%;
    right: 20%;
    padding-bottom: 30px;
  }
  .carousel-indicators {
    bottom: 20px;
  }
}
.clearfix:before,
.clearfix:after,
.dl-horizontal dd:before,
.dl-horizontal dd:after,
.container:before,
.container:after,
.container-fluid:before,
.container-fluid:after,
.row:before,
.row:after,
.form-horizontal .form-group:before,
.form-horizontal .form-group:after,
.btn-toolbar:before,
.btn-toolbar:after,
.btn-group-vertical > .btn-group:before,
.btn-group-vertical > .btn-group:after,
.nav:before,
.nav:after,
.navbar:before,
.navbar:after,
.navbar-header:before,
.navbar-header:after,
.navbar-collapse:before,
.navbar-collapse:after,
.pager:before,
.pager:after,
.panel-body:before,
.panel-body:after,
.modal-header:before,
.modal-header:after,
.modal-footer:before,
.modal-footer:after,
.item_buttons:before,
.item_buttons:after {
  content: " ";
  display: table;
}
.clearfix:after,
.dl-horizontal dd:after,
.container:after,
.container-fluid:after,
.row:after,
.form-horizontal .form-group:after,
.btn-toolbar:after,
.btn-group-vertical > .btn-group:after,
.nav:after,
.navbar:after,
.navbar-header:after,
.navbar-collapse:after,
.pager:after,
.panel-body:after,
.modal-header:after,
.modal-footer:after,
.item_buttons:after {
  clear: both;
}
.center-block {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
.pull-right {
  float: right !important;
}
.pull-left {
  float: left !important;
}
.hide {
  display: none !important;
}
.show {
  display: block !important;
}
.invisible {
  visibility: hidden;
}
.text-hide {
  font: 0/0 a;
  color: transparent;
  text-shadow: none;
  background-color: transparent;
  border: 0;
}
.hidden {
  display: none !important;
}
.affix {
  position: fixed;
}
@-ms-viewport {
  width: device-width;
}
.visible-xs,
.visible-sm,
.visible-md,
.visible-lg {
  display: none !important;
}
.visible-xs-block,
.visible-xs-inline,
.visible-xs-inline-block,
.visible-sm-block,
.visible-sm-inline,
.visible-sm-inline-block,
.visible-md-block,
.visible-md-inline,
.visible-md-inline-block,
.visible-lg-block,
.visible-lg-inline,
.visible-lg-inline-block {
  display: none !important;
}
@media (max-width: 767px) {
  .visible-xs {
    display: block !important;
  }
  table.visible-xs {
    display: table !important;
  }
  tr.visible-xs {
    display: table-row !important;
  }
  th.visible-xs,
  td.visible-xs {
    display: table-cell !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-block {
    display: block !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-inline {
    display: inline !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm {
    display: block !important;
  }
  table.visible-sm {
    display: table !important;
  }
  tr.visible-sm {
    display: table-row !important;
  }
  th.visible-sm,
  td.visible-sm {
    display: table-cell !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-block {
    display: block !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-inline {
    display: inline !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md {
    display: block !important;
  }
  table.visible-md {
    display: table !important;
  }
  tr.visible-md {
    display: table-row !important;
  }
  th.visible-md,
  td.visible-md {
    display: table-cell !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-block {
    display: block !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-inline {
    display: inline !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg {
    display: block !important;
  }
  table.visible-lg {
    display: table !important;
  }
  tr.visible-lg {
    display: table-row !important;
  }
  th.visible-lg,
  td.visible-lg {
    display: table-cell !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-block {
    display: block !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-inline {
    display: inline !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-inline-block {
    display: inline-block !important;
  }
}
@media (max-width: 767px) {
  .hidden-xs {
    display: none !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .hidden-sm {
    display: none !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .hidden-md {
    display: none !important;
  }
}
@media (min-width: 1200px) {
  .hidden-lg {
    display: none !important;
  }
}
.visible-print {
  display: none !important;
}
@media print {
  .visible-print {
    display: block !important;
  }
  table.visible-print {
    display: table !important;
  }
  tr.visible-print {
    display: table-row !important;
  }
  th.visible-print,
  td.visible-print {
    display: table-cell !important;
  }
}
.visible-print-block {
  display: none !important;
}
@media print {
  .visible-print-block {
    display: block !important;
  }
}
.visible-print-inline {
  display: none !important;
}
@media print {
  .visible-print-inline {
    display: inline !important;
  }
}
.visible-print-inline-block {
  display: none !important;
}
@media print {
  .visible-print-inline-block {
    display: inline-block !important;
  }
}
@media print {
  .hidden-print {
    display: none !important;
  }
}
/*!
*
* Font Awesome
*
*/
/*!
 *  Font Awesome 4.2.0 by @davegandy - http://fontawesome.io - @fontawesome
 *  License - http://fontawesome.io/license (Font: SIL OFL 1.1, CSS: MIT License)
 */
/* FONT PATH
 * -------------------------- */
@font-face {
  font-family: 'FontAwesome';
  src: url('../components/font-awesome/fonts/fontawesome-webfont.eot?v=4.2.0');
  src: url('../components/font-awesome/fonts/fontawesome-webfont.eot?#iefix&v=4.2.0') format('embedded-opentype'), url('../components/font-awesome/fonts/fontawesome-webfont.woff?v=4.2.0') format('woff'), url('../components/font-awesome/fonts/fontawesome-webfont.ttf?v=4.2.0') format('truetype'), url('../components/font-awesome/fonts/fontawesome-webfont.svg?v=4.2.0#fontawesomeregular') format('svg');
  font-weight: normal;
  font-style: normal;
}
.fa {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
/* makes the font 33% larger relative to the icon container */
.fa-lg {
  font-size: 1.33333333em;
  line-height: 0.75em;
  vertical-align: -15%;
}
.fa-2x {
  font-size: 2em;
}
.fa-3x {
  font-size: 3em;
}
.fa-4x {
  font-size: 4em;
}
.fa-5x {
  font-size: 5em;
}
.fa-fw {
  width: 1.28571429em;
  text-align: center;
}
.fa-ul {
  padding-left: 0;
  margin-left: 2.14285714em;
  list-style-type: none;
}
.fa-ul > li {
  position: relative;
}
.fa-li {
  position: absolute;
  left: -2.14285714em;
  width: 2.14285714em;
  top: 0.14285714em;
  text-align: center;
}
.fa-li.fa-lg {
  left: -1.85714286em;
}
.fa-border {
  padding: .2em .25em .15em;
  border: solid 0.08em #eee;
  border-radius: .1em;
}
.pull-right {
  float: right;
}
.pull-left {
  float: left;
}
.fa.pull-left {
  margin-right: .3em;
}
.fa.pull-right {
  margin-left: .3em;
}
.fa-spin {
  -webkit-animation: fa-spin 2s infinite linear;
  animation: fa-spin 2s infinite linear;
}
@-webkit-keyframes fa-spin {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(359deg);
    transform: rotate(359deg);
  }
}
@keyframes fa-spin {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(359deg);
    transform: rotate(359deg);
  }
}
.fa-rotate-90 {
  filter: progid:DXImageTransform.Microsoft.BasicImage(rotation=1);
  -webkit-transform: rotate(90deg);
  -ms-transform: rotate(90deg);
  transform: rotate(90deg);
}
.fa-rotate-180 {
  filter: progid:DXImageTransform.Microsoft.BasicImage(rotation=2);
  -webkit-transform: rotate(180deg);
  -ms-transform: rotate(180deg);
  transform: rotate(180deg);
}
.fa-rotate-270 {
  filter: progid:DXImageTransform.Microsoft.BasicImage(rotation=3);
  -webkit-transform: rotate(270deg);
  -ms-transform: rotate(270deg);
  transform: rotate(270deg);
}
.fa-flip-horizontal {
  filter: progid:DXImageTransform.Microsoft.BasicImage(rotation=0, mirror=1);
  -webkit-transform: scale(-1, 1);
  -ms-transform: scale(-1, 1);
  transform: scale(-1, 1);
}
.fa-flip-vertical {
  filter: progid:DXImageTransform.Microsoft.BasicImage(rotation=2, mirror=1);
  -webkit-transform: scale(1, -1);
  -ms-transform: scale(1, -1);
  transform: scale(1, -1);
}
:root .fa-rotate-90,
:root .fa-rotate-180,
:root .fa-rotate-270,
:root .fa-flip-horizontal,
:root .fa-flip-vertical {
  filter: none;
}
.fa-stack {
  position: relative;
  display: inline-block;
  width: 2em;
  height: 2em;
  line-height: 2em;
  vertical-align: middle;
}
.fa-stack-1x,
.fa-stack-2x {
  position: absolute;
  left: 0;
  width: 100%;
  text-align: center;
}
.fa-stack-1x {
  line-height: inherit;
}
.fa-stack-2x {
  font-size: 2em;
}
.fa-inverse {
  color: #fff;
}
/* Font Awesome uses the Unicode Private Use Area (PUA) to ensure screen
   readers do not read off random characters that represent icons */
.fa-glass:before {
  content: "\f000";
}
.fa-music:before {
  content: "\f001";
}
.fa-search:before {
  content: "\f002";
}
.fa-envelope-o:before {
  content: "\f003";
}
.fa-heart:before {
  content: "\f004";
}
.fa-star:before {
  content: "\f005";
}
.fa-star-o:before {
  content: "\f006";
}
.fa-user:before {
  content: "\f007";
}
.fa-film:before {
  content: "\f008";
}
.fa-th-large:before {
  content: "\f009";
}
.fa-th:before {
  content: "\f00a";
}
.fa-th-list:before {
  content: "\f00b";
}
.fa-check:before {
  content: "\f00c";
}
.fa-remove:before,
.fa-close:before,
.fa-times:before {
  content: "\f00d";
}
.fa-search-plus:before {
  content: "\f00e";
}
.fa-search-minus:before {
  content: "\f010";
}
.fa-power-off:before {
  content: "\f011";
}
.fa-signal:before {
  content: "\f012";
}
.fa-gear:before,
.fa-cog:before {
  content: "\f013";
}
.fa-trash-o:before {
  content: "\f014";
}
.fa-home:before {
  content: "\f015";
}
.fa-file-o:before {
  content: "\f016";
}
.fa-clock-o:before {
  content: "\f017";
}
.fa-road:before {
  content: "\f018";
}
.fa-download:before {
  content: "\f019";
}
.fa-arrow-circle-o-down:before {
  content: "\f01a";
}
.fa-arrow-circle-o-up:before {
  content: "\f01b";
}
.fa-inbox:before {
  content: "\f01c";
}
.fa-play-circle-o:before {
  content: "\f01d";
}
.fa-rotate-right:before,
.fa-repeat:before {
  content: "\f01e";
}
.fa-refresh:before {
  content: "\f021";
}
.fa-list-alt:before {
  content: "\f022";
}
.fa-lock:before {
  content: "\f023";
}
.fa-flag:before {
  content: "\f024";
}
.fa-headphones:before {
  content: "\f025";
}
.fa-volume-off:before {
  content: "\f026";
}
.fa-volume-down:before {
  content: "\f027";
}
.fa-volume-up:before {
  content: "\f028";
}
.fa-qrcode:before {
  content: "\f029";
}
.fa-barcode:before {
  content: "\f02a";
}
.fa-tag:before {
  content: "\f02b";
}
.fa-tags:before {
  content: "\f02c";
}
.fa-book:before {
  content: "\f02d";
}
.fa-bookmark:before {
  content: "\f02e";
}
.fa-print:before {
  content: "\f02f";
}
.fa-camera:before {
  content: "\f030";
}
.fa-font:before {
  content: "\f031";
}
.fa-bold:before {
  content: "\f032";
}
.fa-italic:before {
  content: "\f033";
}
.fa-text-height:before {
  content: "\f034";
}
.fa-text-width:before {
  content: "\f035";
}
.fa-align-left:before {
  content: "\f036";
}
.fa-align-center:before {
  content: "\f037";
}
.fa-align-right:before {
  content: "\f038";
}
.fa-align-justify:before {
  content: "\f039";
}
.fa-list:before {
  content: "\f03a";
}
.fa-dedent:before,
.fa-outdent:before {
  content: "\f03b";
}
.fa-indent:before {
  content: "\f03c";
}
.fa-video-camera:before {
  content: "\f03d";
}
.fa-photo:before,
.fa-image:before,
.fa-picture-o:before {
  content: "\f03e";
}
.fa-pencil:before {
  content: "\f040";
}
.fa-map-marker:before {
  content: "\f041";
}
.fa-adjust:before {
  content: "\f042";
}
.fa-tint:before {
  content: "\f043";
}
.fa-edit:before,
.fa-pencil-square-o:before {
  content: "\f044";
}
.fa-share-square-o:before {
  content: "\f045";
}
.fa-check-square-o:before {
  content: "\f046";
}
.fa-arrows:before {
  content: "\f047";
}
.fa-step-backward:before {
  content: "\f048";
}
.fa-fast-backward:before {
  content: "\f049";
}
.fa-backward:before {
  content: "\f04a";
}
.fa-play:before {
  content: "\f04b";
}
.fa-pause:before {
  content: "\f04c";
}
.fa-stop:before {
  content: "\f04d";
}
.fa-forward:before {
  content: "\f04e";
}
.fa-fast-forward:before {
  content: "\f050";
}
.fa-step-forward:before {
  content: "\f051";
}
.fa-eject:before {
  content: "\f052";
}
.fa-chevron-left:before {
  content: "\f053";
}
.fa-chevron-right:before {
  content: "\f054";
}
.fa-plus-circle:before {
  content: "\f055";
}
.fa-minus-circle:before {
  content: "\f056";
}
.fa-times-circle:before {
  content: "\f057";
}
.fa-check-circle:before {
  content: "\f058";
}
.fa-question-circle:before {
  content: "\f059";
}
.fa-info-circle:before {
  content: "\f05a";
}
.fa-crosshairs:before {
  content: "\f05b";
}
.fa-times-circle-o:before {
  content: "\f05c";
}
.fa-check-circle-o:before {
  content: "\f05d";
}
.fa-ban:before {
  content: "\f05e";
}
.fa-arrow-left:before {
  content: "\f060";
}
.fa-arrow-right:before {
  content: "\f061";
}
.fa-arrow-up:before {
  content: "\f062";
}
.fa-arrow-down:before {
  content: "\f063";
}
.fa-mail-forward:before,
.fa-share:before {
  content: "\f064";
}
.fa-expand:before {
  content: "\f065";
}
.fa-compress:before {
  content: "\f066";
}
.fa-plus:before {
  content: "\f067";
}
.fa-minus:before {
  content: "\f068";
}
.fa-asterisk:before {
  content: "\f069";
}
.fa-exclamation-circle:before {
  content: "\f06a";
}
.fa-gift:before {
  content: "\f06b";
}
.fa-leaf:before {
  content: "\f06c";
}
.fa-fire:before {
  content: "\f06d";
}
.fa-eye:before {
  content: "\f06e";
}
.fa-eye-slash:before {
  content: "\f070";
}
.fa-warning:before,
.fa-exclamation-triangle:before {
  content: "\f071";
}
.fa-plane:before {
  content: "\f072";
}
.fa-calendar:before {
  content: "\f073";
}
.fa-random:before {
  content: "\f074";
}
.fa-comment:before {
  content: "\f075";
}
.fa-magnet:before {
  content: "\f076";
}
.fa-chevron-up:before {
  content: "\f077";
}
.fa-chevron-down:before {
  content: "\f078";
}
.fa-retweet:before {
  content: "\f079";
}
.fa-shopping-cart:before {
  content: "\f07a";
}
.fa-folder:before {
  content: "\f07b";
}
.fa-folder-open:before {
  content: "\f07c";
}
.fa-arrows-v:before {
  content: "\f07d";
}
.fa-arrows-h:before {
  content: "\f07e";
}
.fa-bar-chart-o:before,
.fa-bar-chart:before {
  content: "\f080";
}
.fa-twitter-square:before {
  content: "\f081";
}
.fa-facebook-square:before {
  content: "\f082";
}
.fa-camera-retro:before {
  content: "\f083";
}
.fa-key:before {
  content: "\f084";
}
.fa-gears:before,
.fa-cogs:before {
  content: "\f085";
}
.fa-comments:before {
  content: "\f086";
}
.fa-thumbs-o-up:before {
  content: "\f087";
}
.fa-thumbs-o-down:before {
  content: "\f088";
}
.fa-star-half:before {
  content: "\f089";
}
.fa-heart-o:before {
  content: "\f08a";
}
.fa-sign-out:before {
  content: "\f08b";
}
.fa-linkedin-square:before {
  content: "\f08c";
}
.fa-thumb-tack:before {
  content: "\f08d";
}
.fa-external-link:before {
  content: "\f08e";
}
.fa-sign-in:before {
  content: "\f090";
}
.fa-trophy:before {
  content: "\f091";
}
.fa-github-square:before {
  content: "\f092";
}
.fa-upload:before {
  content: "\f093";
}
.fa-lemon-o:before {
  content: "\f094";
}
.fa-phone:before {
  content: "\f095";
}
.fa-square-o:before {
  content: "\f096";
}
.fa-bookmark-o:before {
  content: "\f097";
}
.fa-phone-square:before {
  content: "\f098";
}
.fa-twitter:before {
  content: "\f099";
}
.fa-facebook:before {
  content: "\f09a";
}
.fa-github:before {
  content: "\f09b";
}
.fa-unlock:before {
  content: "\f09c";
}
.fa-credit-card:before {
  content: "\f09d";
}
.fa-rss:before {
  content: "\f09e";
}
.fa-hdd-o:before {
  content: "\f0a0";
}
.fa-bullhorn:before {
  content: "\f0a1";
}
.fa-bell:before {
  content: "\f0f3";
}
.fa-certificate:before {
  content: "\f0a3";
}
.fa-hand-o-right:before {
  content: "\f0a4";
}
.fa-hand-o-left:before {
  content: "\f0a5";
}
.fa-hand-o-up:before {
  content: "\f0a6";
}
.fa-hand-o-down:before {
  content: "\f0a7";
}
.fa-arrow-circle-left:before {
  content: "\f0a8";
}
.fa-arrow-circle-right:before {
  content: "\f0a9";
}
.fa-arrow-circle-up:before {
  content: "\f0aa";
}
.fa-arrow-circle-down:before {
  content: "\f0ab";
}
.fa-globe:before {
  content: "\f0ac";
}
.fa-wrench:before {
  content: "\f0ad";
}
.fa-tasks:before {
  content: "\f0ae";
}
.fa-filter:before {
  content: "\f0b0";
}
.fa-briefcase:before {
  content: "\f0b1";
}
.fa-arrows-alt:before {
  content: "\f0b2";
}
.fa-group:before,
.fa-users:before {
  content: "\f0c0";
}
.fa-chain:before,
.fa-link:before {
  content: "\f0c1";
}
.fa-cloud:before {
  content: "\f0c2";
}
.fa-flask:before {
  content: "\f0c3";
}
.fa-cut:before,
.fa-scissors:before {
  content: "\f0c4";
}
.fa-copy:before,
.fa-files-o:before {
  content: "\f0c5";
}
.fa-paperclip:before {
  content: "\f0c6";
}
.fa-save:before,
.fa-floppy-o:before {
  content: "\f0c7";
}
.fa-square:before {
  content: "\f0c8";
}
.fa-navicon:before,
.fa-reorder:before,
.fa-bars:before {
  content: "\f0c9";
}
.fa-list-ul:before {
  content: "\f0ca";
}
.fa-list-ol:before {
  content: "\f0cb";
}
.fa-strikethrough:before {
  content: "\f0cc";
}
.fa-underline:before {
  content: "\f0cd";
}
.fa-table:before {
  content: "\f0ce";
}
.fa-magic:before {
  content: "\f0d0";
}
.fa-truck:before {
  content: "\f0d1";
}
.fa-pinterest:before {
  content: "\f0d2";
}
.fa-pinterest-square:before {
  content: "\f0d3";
}
.fa-google-plus-square:before {
  content: "\f0d4";
}
.fa-google-plus:before {
  content: "\f0d5";
}
.fa-money:before {
  content: "\f0d6";
}
.fa-caret-down:before {
  content: "\f0d7";
}
.fa-caret-up:before {
  content: "\f0d8";
}
.fa-caret-left:before {
  content: "\f0d9";
}
.fa-caret-right:before {
  content: "\f0da";
}
.fa-columns:before {
  content: "\f0db";
}
.fa-unsorted:before,
.fa-sort:before {
  content: "\f0dc";
}
.fa-sort-down:before,
.fa-sort-desc:before {
  content: "\f0dd";
}
.fa-sort-up:before,
.fa-sort-asc:before {
  content: "\f0de";
}
.fa-envelope:before {
  content: "\f0e0";
}
.fa-linkedin:before {
  content: "\f0e1";
}
.fa-rotate-left:before,
.fa-undo:before {
  content: "\f0e2";
}
.fa-legal:before,
.fa-gavel:before {
  content: "\f0e3";
}
.fa-dashboard:before,
.fa-tachometer:before {
  content: "\f0e4";
}
.fa-comment-o:before {
  content: "\f0e5";
}
.fa-comments-o:before {
  content: "\f0e6";
}
.fa-flash:before,
.fa-bolt:before {
  content: "\f0e7";
}
.fa-sitemap:before {
  content: "\f0e8";
}
.fa-umbrella:before {
  content: "\f0e9";
}
.fa-paste:before,
.fa-clipboard:before {
  content: "\f0ea";
}
.fa-lightbulb-o:before {
  content: "\f0eb";
}
.fa-exchange:before {
  content: "\f0ec";
}
.fa-cloud-download:before {
  content: "\f0ed";
}
.fa-cloud-upload:before {
  content: "\f0ee";
}
.fa-user-md:before {
  content: "\f0f0";
}
.fa-stethoscope:before {
  content: "\f0f1";
}
.fa-suitcase:before {
  content: "\f0f2";
}
.fa-bell-o:before {
  content: "\f0a2";
}
.fa-coffee:before {
  content: "\f0f4";
}
.fa-cutlery:before {
  content: "\f0f5";
}
.fa-file-text-o:before {
  content: "\f0f6";
}
.fa-building-o:before {
  content: "\f0f7";
}
.fa-hospital-o:before {
  content: "\f0f8";
}
.fa-ambulance:before {
  content: "\f0f9";
}
.fa-medkit:before {
  content: "\f0fa";
}
.fa-fighter-jet:before {
  content: "\f0fb";
}
.fa-beer:before {
  content: "\f0fc";
}
.fa-h-square:before {
  content: "\f0fd";
}
.fa-plus-square:before {
  content: "\f0fe";
}
.fa-angle-double-left:before {
  content: "\f100";
}
.fa-angle-double-right:before {
  content: "\f101";
}
.fa-angle-double-up:before {
  content: "\f102";
}
.fa-angle-double-down:before {
  content: "\f103";
}
.fa-angle-left:before {
  content: "\f104";
}
.fa-angle-right:before {
  content: "\f105";
}
.fa-angle-up:before {
  content: "\f106";
}
.fa-angle-down:before {
  content: "\f107";
}
.fa-desktop:before {
  content: "\f108";
}
.fa-laptop:before {
  content: "\f109";
}
.fa-tablet:before {
  content: "\f10a";
}
.fa-mobile-phone:before,
.fa-mobile:before {
  content: "\f10b";
}
.fa-circle-o:before {
  content: "\f10c";
}
.fa-quote-left:before {
  content: "\f10d";
}
.fa-quote-right:before {
  content: "\f10e";
}
.fa-spinner:before {
  content: "\f110";
}
.fa-circle:before {
  content: "\f111";
}
.fa-mail-reply:before,
.fa-reply:before {
  content: "\f112";
}
.fa-github-alt:before {
  content: "\f113";
}
.fa-folder-o:before {
  content: "\f114";
}
.fa-folder-open-o:before {
  content: "\f115";
}
.fa-smile-o:before {
  content: "\f118";
}
.fa-frown-o:before {
  content: "\f119";
}
.fa-meh-o:before {
  content: "\f11a";
}
.fa-gamepad:before {
  content: "\f11b";
}
.fa-keyboard-o:before {
  content: "\f11c";
}
.fa-flag-o:before {
  content: "\f11d";
}
.fa-flag-checkered:before {
  content: "\f11e";
}
.fa-terminal:before {
  content: "\f120";
}
.fa-code:before {
  content: "\f121";
}
.fa-mail-reply-all:before,
.fa-reply-all:before {
  content: "\f122";
}
.fa-star-half-empty:before,
.fa-star-half-full:before,
.fa-star-half-o:before {
  content: "\f123";
}
.fa-location-arrow:before {
  content: "\f124";
}
.fa-crop:before {
  content: "\f125";
}
.fa-code-fork:before {
  content: "\f126";
}
.fa-unlink:before,
.fa-chain-broken:before {
  content: "\f127";
}
.fa-question:before {
  content: "\f128";
}
.fa-info:before {
  content: "\f129";
}
.fa-exclamation:before {
  content: "\f12a";
}
.fa-superscript:before {
  content: "\f12b";
}
.fa-subscript:before {
  content: "\f12c";
}
.fa-eraser:before {
  content: "\f12d";
}
.fa-puzzle-piece:before {
  content: "\f12e";
}
.fa-microphone:before {
  content: "\f130";
}
.fa-microphone-slash:before {
  content: "\f131";
}
.fa-shield:before {
  content: "\f132";
}
.fa-calendar-o:before {
  content: "\f133";
}
.fa-fire-extinguisher:before {
  content: "\f134";
}
.fa-rocket:before {
  content: "\f135";
}
.fa-maxcdn:before {
  content: "\f136";
}
.fa-chevron-circle-left:before {
  content: "\f137";
}
.fa-chevron-circle-right:before {
  content: "\f138";
}
.fa-chevron-circle-up:before {
  content: "\f139";
}
.fa-chevron-circle-down:before {
  content: "\f13a";
}
.fa-html5:before {
  content: "\f13b";
}
.fa-css3:before {
  content: "\f13c";
}
.fa-anchor:before {
  content: "\f13d";
}
.fa-unlock-alt:before {
  content: "\f13e";
}
.fa-bullseye:before {
  content: "\f140";
}
.fa-ellipsis-h:before {
  content: "\f141";
}
.fa-ellipsis-v:before {
  content: "\f142";
}
.fa-rss-square:before {
  content: "\f143";
}
.fa-play-circle:before {
  content: "\f144";
}
.fa-ticket:before {
  content: "\f145";
}
.fa-minus-square:before {
  content: "\f146";
}
.fa-minus-square-o:before {
  content: "\f147";
}
.fa-level-up:before {
  content: "\f148";
}
.fa-level-down:before {
  content: "\f149";
}
.fa-check-square:before {
  content: "\f14a";
}
.fa-pencil-square:before {
  content: "\f14b";
}
.fa-external-link-square:before {
  content: "\f14c";
}
.fa-share-square:before {
  content: "\f14d";
}
.fa-compass:before {
  content: "\f14e";
}
.fa-toggle-down:before,
.fa-caret-square-o-down:before {
  content: "\f150";
}
.fa-toggle-up:before,
.fa-caret-square-o-up:before {
  content: "\f151";
}
.fa-toggle-right:before,
.fa-caret-square-o-right:before {
  content: "\f152";
}
.fa-euro:before,
.fa-eur:before {
  content: "\f153";
}
.fa-gbp:before {
  content: "\f154";
}
.fa-dollar:before,
.fa-usd:before {
  content: "\f155";
}
.fa-rupee:before,
.fa-inr:before {
  content: "\f156";
}
.fa-cny:before,
.fa-rmb:before,
.fa-yen:before,
.fa-jpy:before {
  content: "\f157";
}
.fa-ruble:before,
.fa-rouble:before,
.fa-rub:before {
  content: "\f158";
}
.fa-won:before,
.fa-krw:before {
  content: "\f159";
}
.fa-bitcoin:before,
.fa-btc:before {
  content: "\f15a";
}
.fa-file:before {
  content: "\f15b";
}
.fa-file-text:before {
  content: "\f15c";
}
.fa-sort-alpha-asc:before {
  content: "\f15d";
}
.fa-sort-alpha-desc:before {
  content: "\f15e";
}
.fa-sort-amount-asc:before {
  content: "\f160";
}
.fa-sort-amount-desc:before {
  content: "\f161";
}
.fa-sort-numeric-asc:before {
  content: "\f162";
}
.fa-sort-numeric-desc:before {
  content: "\f163";
}
.fa-thumbs-up:before {
  content: "\f164";
}
.fa-thumbs-down:before {
  content: "\f165";
}
.fa-youtube-square:before {
  content: "\f166";
}
.fa-youtube:before {
  content: "\f167";
}
.fa-xing:before {
  content: "\f168";
}
.fa-xing-square:before {
  content: "\f169";
}
.fa-youtube-play:before {
  content: "\f16a";
}
.fa-dropbox:before {
  content: "\f16b";
}
.fa-stack-overflow:before {
  content: "\f16c";
}
.fa-instagram:before {
  content: "\f16d";
}
.fa-flickr:before {
  content: "\f16e";
}
.fa-adn:before {
  content: "\f170";
}
.fa-bitbucket:before {
  content: "\f171";
}
.fa-bitbucket-square:before {
  content: "\f172";
}
.fa-tumblr:before {
  content: "\f173";
}
.fa-tumblr-square:before {
  content: "\f174";
}
.fa-long-arrow-down:before {
  content: "\f175";
}
.fa-long-arrow-up:before {
  content: "\f176";
}
.fa-long-arrow-left:before {
  content: "\f177";
}
.fa-long-arrow-right:before {
  content: "\f178";
}
.fa-apple:before {
  content: "\f179";
}
.fa-windows:before {
  content: "\f17a";
}
.fa-android:before {
  content: "\f17b";
}
.fa-linux:before {
  content: "\f17c";
}
.fa-dribbble:before {
  content: "\f17d";
}
.fa-skype:before {
  content: "\f17e";
}
.fa-foursquare:before {
  content: "\f180";
}
.fa-trello:before {
  content: "\f181";
}
.fa-female:before {
  content: "\f182";
}
.fa-male:before {
  content: "\f183";
}
.fa-gittip:before {
  content: "\f184";
}
.fa-sun-o:before {
  content: "\f185";
}
.fa-moon-o:before {
  content: "\f186";
}
.fa-archive:before {
  content: "\f187";
}
.fa-bug:before {
  content: "\f188";
}
.fa-vk:before {
  content: "\f189";
}
.fa-weibo:before {
  content: "\f18a";
}
.fa-renren:before {
  content: "\f18b";
}
.fa-pagelines:before {
  content: "\f18c";
}
.fa-stack-exchange:before {
  content: "\f18d";
}
.fa-arrow-circle-o-right:before {
  content: "\f18e";
}
.fa-arrow-circle-o-left:before {
  content: "\f190";
}
.fa-toggle-left:before,
.fa-caret-square-o-left:before {
  content: "\f191";
}
.fa-dot-circle-o:before {
  content: "\f192";
}
.fa-wheelchair:before {
  content: "\f193";
}
.fa-vimeo-square:before {
  content: "\f194";
}
.fa-turkish-lira:before,
.fa-try:before {
  content: "\f195";
}
.fa-plus-square-o:before {
  content: "\f196";
}
.fa-space-shuttle:before {
  content: "\f197";
}
.fa-slack:before {
  content: "\f198";
}
.fa-envelope-square:before {
  content: "\f199";
}
.fa-wordpress:before {
  content: "\f19a";
}
.fa-openid:before {
  content: "\f19b";
}
.fa-institution:before,
.fa-bank:before,
.fa-university:before {
  content: "\f19c";
}
.fa-mortar-board:before,
.fa-graduation-cap:before {
  content: "\f19d";
}
.fa-yahoo:before {
  content: "\f19e";
}
.fa-google:before {
  content: "\f1a0";
}
.fa-reddit:before {
  content: "\f1a1";
}
.fa-reddit-square:before {
  content: "\f1a2";
}
.fa-stumbleupon-circle:before {
  content: "\f1a3";
}
.fa-stumbleupon:before {
  content: "\f1a4";
}
.fa-delicious:before {
  content: "\f1a5";
}
.fa-digg:before {
  content: "\f1a6";
}
.fa-pied-piper:before {
  content: "\f1a7";
}
.fa-pied-piper-alt:before {
  content: "\f1a8";
}
.fa-drupal:before {
  content: "\f1a9";
}
.fa-joomla:before {
  content: "\f1aa";
}
.fa-language:before {
  content: "\f1ab";
}
.fa-fax:before {
  content: "\f1ac";
}
.fa-building:before {
  content: "\f1ad";
}
.fa-child:before {
  content: "\f1ae";
}
.fa-paw:before {
  content: "\f1b0";
}
.fa-spoon:before {
  content: "\f1b1";
}
.fa-cube:before {
  content: "\f1b2";
}
.fa-cubes:before {
  content: "\f1b3";
}
.fa-behance:before {
  content: "\f1b4";
}
.fa-behance-square:before {
  content: "\f1b5";
}
.fa-steam:before {
  content: "\f1b6";
}
.fa-steam-square:before {
  content: "\f1b7";
}
.fa-recycle:before {
  content: "\f1b8";
}
.fa-automobile:before,
.fa-car:before {
  content: "\f1b9";
}
.fa-cab:before,
.fa-taxi:before {
  content: "\f1ba";
}
.fa-tree:before {
  content: "\f1bb";
}
.fa-spotify:before {
  content: "\f1bc";
}
.fa-deviantart:before {
  content: "\f1bd";
}
.fa-soundcloud:before {
  content: "\f1be";
}
.fa-database:before {
  content: "\f1c0";
}
.fa-file-pdf-o:before {
  content: "\f1c1";
}
.fa-file-word-o:before {
  content: "\f1c2";
}
.fa-file-excel-o:before {
  content: "\f1c3";
}
.fa-file-powerpoint-o:before {
  content: "\f1c4";
}
.fa-file-photo-o:before,
.fa-file-picture-o:before,
.fa-file-image-o:before {
  content: "\f1c5";
}
.fa-file-zip-o:before,
.fa-file-archive-o:before {
  content: "\f1c6";
}
.fa-file-sound-o:before,
.fa-file-audio-o:before {
  content: "\f1c7";
}
.fa-file-movie-o:before,
.fa-file-video-o:before {
  content: "\f1c8";
}
.fa-file-code-o:before {
  content: "\f1c9";
}
.fa-vine:before {
  content: "\f1ca";
}
.fa-codepen:before {
  content: "\f1cb";
}
.fa-jsfiddle:before {
  content: "\f1cc";
}
.fa-life-bouy:before,
.fa-life-buoy:before,
.fa-life-saver:before,
.fa-support:before,
.fa-life-ring:before {
  content: "\f1cd";
}
.fa-circle-o-notch:before {
  content: "\f1ce";
}
.fa-ra:before,
.fa-rebel:before {
  content: "\f1d0";
}
.fa-ge:before,
.fa-empire:before {
  content: "\f1d1";
}
.fa-git-square:before {
  content: "\f1d2";
}
.fa-git:before {
  content: "\f1d3";
}
.fa-hacker-news:before {
  content: "\f1d4";
}
.fa-tencent-weibo:before {
  content: "\f1d5";
}
.fa-qq:before {
  content: "\f1d6";
}
.fa-wechat:before,
.fa-weixin:before {
  content: "\f1d7";
}
.fa-send:before,
.fa-paper-plane:before {
  content: "\f1d8";
}
.fa-send-o:before,
.fa-paper-plane-o:before {
  content: "\f1d9";
}
.fa-history:before {
  content: "\f1da";
}
.fa-circle-thin:before {
  content: "\f1db";
}
.fa-header:before {
  content: "\f1dc";
}
.fa-paragraph:before {
  content: "\f1dd";
}
.fa-sliders:before {
  content: "\f1de";
}
.fa-share-alt:before {
  content: "\f1e0";
}
.fa-share-alt-square:before {
  content: "\f1e1";
}
.fa-bomb:before {
  content: "\f1e2";
}
.fa-soccer-ball-o:before,
.fa-futbol-o:before {
  content: "\f1e3";
}
.fa-tty:before {
  content: "\f1e4";
}
.fa-binoculars:before {
  content: "\f1e5";
}
.fa-plug:before {
  content: "\f1e6";
}
.fa-slideshare:before {
  content: "\f1e7";
}
.fa-twitch:before {
  content: "\f1e8";
}
.fa-yelp:before {
  content: "\f1e9";
}
.fa-newspaper-o:before {
  content: "\f1ea";
}
.fa-wifi:before {
  content: "\f1eb";
}
.fa-calculator:before {
  content: "\f1ec";
}
.fa-paypal:before {
  content: "\f1ed";
}
.fa-google-wallet:before {
  content: "\f1ee";
}
.fa-cc-visa:before {
  content: "\f1f0";
}
.fa-cc-mastercard:before {
  content: "\f1f1";
}
.fa-cc-discover:before {
  content: "\f1f2";
}
.fa-cc-amex:before {
  content: "\f1f3";
}
.fa-cc-paypal:before {
  content: "\f1f4";
}
.fa-cc-stripe:before {
  content: "\f1f5";
}
.fa-bell-slash:before {
  content: "\f1f6";
}
.fa-bell-slash-o:before {
  content: "\f1f7";
}
.fa-trash:before {
  content: "\f1f8";
}
.fa-copyright:before {
  content: "\f1f9";
}
.fa-at:before {
  content: "\f1fa";
}
.fa-eyedropper:before {
  content: "\f1fb";
}
.fa-paint-brush:before {
  content: "\f1fc";
}
.fa-birthday-cake:before {
  content: "\f1fd";
}
.fa-area-chart:before {
  content: "\f1fe";
}
.fa-pie-chart:before {
  content: "\f200";
}
.fa-line-chart:before {
  content: "\f201";
}
.fa-lastfm:before {
  content: "\f202";
}
.fa-lastfm-square:before {
  content: "\f203";
}
.fa-toggle-off:before {
  content: "\f204";
}
.fa-toggle-on:before {
  content: "\f205";
}
.fa-bicycle:before {
  content: "\f206";
}
.fa-bus:before {
  content: "\f207";
}
.fa-ioxhost:before {
  content: "\f208";
}
.fa-angellist:before {
  content: "\f209";
}
.fa-cc:before {
  content: "\f20a";
}
.fa-shekel:before,
.fa-sheqel:before,
.fa-ils:before {
  content: "\f20b";
}
.fa-meanpath:before {
  content: "\f20c";
}
/*!
*
* IPython base
*
*/
.modal.fade .modal-dialog {
  -webkit-transform: translate(0, 0);
  -ms-transform: translate(0, 0);
  -o-transform: translate(0, 0);
  transform: translate(0, 0);
}
code {
  color: #000;
}
pre {
  font-size: inherit;
  line-height: inherit;
}
label {
  font-weight: normal;
}
/* Make the page background atleast 100% the height of the view port */
/* Make the page itself atleast 70% the height of the view port */
.border-box-sizing {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
.corner-all {
  border-radius: 2px;
}
.no-padding {
  padding: 0px;
}
/* Flexible box model classes */
/* Taken from Alex Russell http://infrequently.org/2009/08/css-3-progress/ */
/* This file is a compatability layer.  It allows the usage of flexible box
model layouts accross multiple browsers, including older browsers.  The newest,
universal implementation of the flexible box model is used when available (see
`Modern browsers` comments below).  Browsers that are known to implement this
new spec completely include:

    Firefox 28.0+
    Chrome 29.0+
    Internet Explorer 11+
    Opera 17.0+

Browsers not listed, including Safari, are supported via the styling under the
`Old browsers` comments below.
*/
.hbox {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
.hbox > * {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
}
.vbox {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
.vbox > * {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
}
.hbox.reverse,
.vbox.reverse,
.reverse {
  /* Old browsers */
  -webkit-box-direction: reverse;
  -moz-box-direction: reverse;
  box-direction: reverse;
  /* Modern browsers */
  flex-direction: row-reverse;
}
.hbox.box-flex0,
.vbox.box-flex0,
.box-flex0 {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
  width: auto;
}
.hbox.box-flex1,
.vbox.box-flex1,
.box-flex1 {
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
.hbox.box-flex,
.vbox.box-flex,
.box-flex {
  /* Old browsers */
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
.hbox.box-flex2,
.vbox.box-flex2,
.box-flex2 {
  /* Old browsers */
  -webkit-box-flex: 2;
  -moz-box-flex: 2;
  box-flex: 2;
  /* Modern browsers */
  flex: 2;
}
.box-group1 {
  /*  Deprecated */
  -webkit-box-flex-group: 1;
  -moz-box-flex-group: 1;
  box-flex-group: 1;
}
.box-group2 {
  /* Deprecated */
  -webkit-box-flex-group: 2;
  -moz-box-flex-group: 2;
  box-flex-group: 2;
}
.hbox.start,
.vbox.start,
.start {
  /* Old browsers */
  -webkit-box-pack: start;
  -moz-box-pack: start;
  box-pack: start;
  /* Modern browsers */
  justify-content: flex-start;
}
.hbox.end,
.vbox.end,
.end {
  /* Old browsers */
  -webkit-box-pack: end;
  -moz-box-pack: end;
  box-pack: end;
  /* Modern browsers */
  justify-content: flex-end;
}
.hbox.center,
.vbox.center,
.center {
  /* Old browsers */
  -webkit-box-pack: center;
  -moz-box-pack: center;
  box-pack: center;
  /* Modern browsers */
  justify-content: center;
}
.hbox.baseline,
.vbox.baseline,
.baseline {
  /* Old browsers */
  -webkit-box-pack: baseline;
  -moz-box-pack: baseline;
  box-pack: baseline;
  /* Modern browsers */
  justify-content: baseline;
}
.hbox.stretch,
.vbox.stretch,
.stretch {
  /* Old browsers */
  -webkit-box-pack: stretch;
  -moz-box-pack: stretch;
  box-pack: stretch;
  /* Modern browsers */
  justify-content: stretch;
}
.hbox.align-start,
.vbox.align-start,
.align-start {
  /* Old browsers */
  -webkit-box-align: start;
  -moz-box-align: start;
  box-align: start;
  /* Modern browsers */
  align-items: flex-start;
}
.hbox.align-end,
.vbox.align-end,
.align-end {
  /* Old browsers */
  -webkit-box-align: end;
  -moz-box-align: end;
  box-align: end;
  /* Modern browsers */
  align-items: flex-end;
}
.hbox.align-center,
.vbox.align-center,
.align-center {
  /* Old browsers */
  -webkit-box-align: center;
  -moz-box-align: center;
  box-align: center;
  /* Modern browsers */
  align-items: center;
}
.hbox.align-baseline,
.vbox.align-baseline,
.align-baseline {
  /* Old browsers */
  -webkit-box-align: baseline;
  -moz-box-align: baseline;
  box-align: baseline;
  /* Modern browsers */
  align-items: baseline;
}
.hbox.align-stretch,
.vbox.align-stretch,
.align-stretch {
  /* Old browsers */
  -webkit-box-align: stretch;
  -moz-box-align: stretch;
  box-align: stretch;
  /* Modern browsers */
  align-items: stretch;
}
div.error {
  margin: 2em;
  text-align: center;
}
div.error > h1 {
  font-size: 500%;
  line-height: normal;
}
div.error > p {
  font-size: 200%;
  line-height: normal;
}
div.traceback-wrapper {
  text-align: left;
  max-width: 800px;
  margin: auto;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
body {
  background-color: #fff;
  /* This makes sure that the body covers the entire window and needs to
       be in a different element than the display: box in wrapper below */
  position: absolute;
  left: 0px;
  right: 0px;
  top: 0px;
  bottom: 0px;
  overflow: visible;
}
body > #header {
  /* Initially hidden to prevent FLOUC */
  display: none;
  background-color: #fff;
  /* Display over codemirror */
  position: relative;
  z-index: 100;
}
body > #header #header-container {
  padding-bottom: 5px;
  padding-top: 5px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
body > #header .header-bar {
  width: 100%;
  height: 1px;
  background: #e7e7e7;
  margin-bottom: -1px;
}
@media print {
  body > #header {
    display: none !important;
  }
}
#header-spacer {
  width: 100%;
  visibility: hidden;
}
@media print {
  #header-spacer {
    display: none;
  }
}
#ipython_notebook {
  padding-left: 0px;
  padding-top: 1px;
  padding-bottom: 1px;
}
@media (max-width: 991px) {
  #ipython_notebook {
    margin-left: 10px;
  }
}
#noscript {
  width: auto;
  padding-top: 16px;
  padding-bottom: 16px;
  text-align: center;
  font-size: 22px;
  color: red;
  font-weight: bold;
}
#ipython_notebook img {
  height: 28px;
}
#site {
  width: 100%;
  display: none;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  overflow: auto;
}
@media print {
  #site {
    height: auto !important;
  }
}
/* Smaller buttons */
.ui-button .ui-button-text {
  padding: 0.2em 0.8em;
  font-size: 77%;
}
input.ui-button {
  padding: 0.3em 0.9em;
}
span#login_widget {
  float: right;
}
span#login_widget > .button,
#logout {
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
span#login_widget > .button:focus,
#logout:focus,
span#login_widget > .button.focus,
#logout.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
span#login_widget > .button:hover,
#logout:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
span#login_widget > .button:active,
#logout:active,
span#login_widget > .button.active,
#logout.active,
.open > .dropdown-togglespan#login_widget > .button,
.open > .dropdown-toggle#logout {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
span#login_widget > .button:active:hover,
#logout:active:hover,
span#login_widget > .button.active:hover,
#logout.active:hover,
.open > .dropdown-togglespan#login_widget > .button:hover,
.open > .dropdown-toggle#logout:hover,
span#login_widget > .button:active:focus,
#logout:active:focus,
span#login_widget > .button.active:focus,
#logout.active:focus,
.open > .dropdown-togglespan#login_widget > .button:focus,
.open > .dropdown-toggle#logout:focus,
span#login_widget > .button:active.focus,
#logout:active.focus,
span#login_widget > .button.active.focus,
#logout.active.focus,
.open > .dropdown-togglespan#login_widget > .button.focus,
.open > .dropdown-toggle#logout.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
span#login_widget > .button:active,
#logout:active,
span#login_widget > .button.active,
#logout.active,
.open > .dropdown-togglespan#login_widget > .button,
.open > .dropdown-toggle#logout {
  background-image: none;
}
span#login_widget > .button.disabled:hover,
#logout.disabled:hover,
span#login_widget > .button[disabled]:hover,
#logout[disabled]:hover,
fieldset[disabled] span#login_widget > .button:hover,
fieldset[disabled] #logout:hover,
span#login_widget > .button.disabled:focus,
#logout.disabled:focus,
span#login_widget > .button[disabled]:focus,
#logout[disabled]:focus,
fieldset[disabled] span#login_widget > .button:focus,
fieldset[disabled] #logout:focus,
span#login_widget > .button.disabled.focus,
#logout.disabled.focus,
span#login_widget > .button[disabled].focus,
#logout[disabled].focus,
fieldset[disabled] span#login_widget > .button.focus,
fieldset[disabled] #logout.focus {
  background-color: #fff;
  border-color: #ccc;
}
span#login_widget > .button .badge,
#logout .badge {
  color: #fff;
  background-color: #333;
}
.nav-header {
  text-transform: none;
}
#header > span {
  margin-top: 10px;
}
.modal_stretch .modal-dialog {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  min-height: 80vh;
}
.modal_stretch .modal-dialog .modal-body {
  max-height: calc(100vh - 200px);
  overflow: auto;
  flex: 1;
}
@media (min-width: 768px) {
  .modal .modal-dialog {
    width: 700px;
  }
}
@media (min-width: 768px) {
  select.form-control {
    margin-left: 12px;
    margin-right: 12px;
  }
}
/*!
*
* IPython auth
*
*/
.center-nav {
  display: inline-block;
  margin-bottom: -4px;
}
/*!
*
* IPython tree view
*
*/
/* We need an invisible input field on top of the sentense*/
/* "Drag file onto the list ..." */
.alternate_upload {
  background-color: none;
  display: inline;
}
.alternate_upload.form {
  padding: 0;
  margin: 0;
}
.alternate_upload input.fileinput {
  text-align: center;
  vertical-align: middle;
  display: inline;
  opacity: 0;
  z-index: 2;
  width: 12ex;
  margin-right: -12ex;
}
.alternate_upload .btn-upload {
  height: 22px;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
ul#tabs {
  margin-bottom: 4px;
}
ul#tabs a {
  padding-top: 6px;
  padding-bottom: 4px;
}
ul.breadcrumb a:focus,
ul.breadcrumb a:hover {
  text-decoration: none;
}
ul.breadcrumb i.icon-home {
  font-size: 16px;
  margin-right: 4px;
}
ul.breadcrumb span {
  color: #5e5e5e;
}
.list_toolbar {
  padding: 4px 0 4px 0;
  vertical-align: middle;
}
.list_toolbar .tree-buttons {
  padding-top: 1px;
}
.dynamic-buttons {
  padding-top: 3px;
  display: inline-block;
}
.list_toolbar [class*="span"] {
  min-height: 24px;
}
.list_header {
  font-weight: bold;
  background-color: #EEE;
}
.list_placeholder {
  font-weight: bold;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
}
.list_container {
  margin-top: 4px;
  margin-bottom: 20px;
  border: 1px solid #ddd;
  border-radius: 2px;
}
.list_container > div {
  border-bottom: 1px solid #ddd;
}
.list_container > div:hover .list-item {
  background-color: red;
}
.list_container > div:last-child {
  border: none;
}
.list_item:hover .list_item {
  background-color: #ddd;
}
.list_item a {
  text-decoration: none;
}
.list_item:hover {
  background-color: #fafafa;
}
.list_header > div,
.list_item > div {
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
  line-height: 22px;
}
.list_header > div input,
.list_item > div input {
  margin-right: 7px;
  margin-left: 14px;
  vertical-align: baseline;
  line-height: 22px;
  position: relative;
  top: -1px;
}
.list_header > div .item_link,
.list_item > div .item_link {
  margin-left: -1px;
  vertical-align: baseline;
  line-height: 22px;
}
.new-file input[type=checkbox] {
  visibility: hidden;
}
.item_name {
  line-height: 22px;
  height: 24px;
}
.item_icon {
  font-size: 14px;
  color: #5e5e5e;
  margin-right: 7px;
  margin-left: 7px;
  line-height: 22px;
  vertical-align: baseline;
}
.item_buttons {
  line-height: 1em;
  margin-left: -5px;
}
.item_buttons .btn,
.item_buttons .btn-group,
.item_buttons .input-group {
  float: left;
}
.item_buttons > .btn,
.item_buttons > .btn-group,
.item_buttons > .input-group {
  margin-left: 5px;
}
.item_buttons .btn {
  min-width: 13ex;
}
.item_buttons .running-indicator {
  padding-top: 4px;
  color: #5cb85c;
}
.item_buttons .kernel-name {
  padding-top: 4px;
  color: #5bc0de;
  margin-right: 7px;
  float: left;
}
.toolbar_info {
  height: 24px;
  line-height: 24px;
}
.list_item input:not([type=checkbox]) {
  padding-top: 3px;
  padding-bottom: 3px;
  height: 22px;
  line-height: 14px;
  margin: 0px;
}
.highlight_text {
  color: blue;
}
#project_name {
  display: inline-block;
  padding-left: 7px;
  margin-left: -2px;
}
#project_name > .breadcrumb {
  padding: 0px;
  margin-bottom: 0px;
  background-color: transparent;
  font-weight: bold;
}
#tree-selector {
  padding-right: 0px;
}
#button-select-all {
  min-width: 50px;
}
#select-all {
  margin-left: 7px;
  margin-right: 2px;
}
.menu_icon {
  margin-right: 2px;
}
.tab-content .row {
  margin-left: 0px;
  margin-right: 0px;
}
.folder_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f114";
}
.folder_icon:before.pull-left {
  margin-right: .3em;
}
.folder_icon:before.pull-right {
  margin-left: .3em;
}
.notebook_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f02d";
  position: relative;
  top: -1px;
}
.notebook_icon:before.pull-left {
  margin-right: .3em;
}
.notebook_icon:before.pull-right {
  margin-left: .3em;
}
.running_notebook_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f02d";
  position: relative;
  top: -1px;
  color: #5cb85c;
}
.running_notebook_icon:before.pull-left {
  margin-right: .3em;
}
.running_notebook_icon:before.pull-right {
  margin-left: .3em;
}
.file_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f016";
  position: relative;
  top: -2px;
}
.file_icon:before.pull-left {
  margin-right: .3em;
}
.file_icon:before.pull-right {
  margin-left: .3em;
}
#notebook_toolbar .pull-right {
  padding-top: 0px;
  margin-right: -1px;
}
ul#new-menu {
  left: auto;
  right: 0;
}
.kernel-menu-icon {
  padding-right: 12px;
  width: 24px;
  content: "\f096";
}
.kernel-menu-icon:before {
  content: "\f096";
}
.kernel-menu-icon-current:before {
  content: "\f00c";
}
#tab_content {
  padding-top: 20px;
}
#running .panel-group .panel {
  margin-top: 3px;
  margin-bottom: 1em;
}
#running .panel-group .panel .panel-heading {
  background-color: #EEE;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
  line-height: 22px;
}
#running .panel-group .panel .panel-heading a:focus,
#running .panel-group .panel .panel-heading a:hover {
  text-decoration: none;
}
#running .panel-group .panel .panel-body {
  padding: 0px;
}
#running .panel-group .panel .panel-body .list_container {
  margin-top: 0px;
  margin-bottom: 0px;
  border: 0px;
  border-radius: 0px;
}
#running .panel-group .panel .panel-body .list_container .list_item {
  border-bottom: 1px solid #ddd;
}
#running .panel-group .panel .panel-body .list_container .list_item:last-child {
  border-bottom: 0px;
}
.delete-button {
  display: none;
}
.duplicate-button {
  display: none;
}
.rename-button {
  display: none;
}
.shutdown-button {
  display: none;
}
.dynamic-instructions {
  display: inline-block;
  padding-top: 4px;
}
/*!
*
* IPython text editor webapp
*
*/
.selected-keymap i.fa {
  padding: 0px 5px;
}
.selected-keymap i.fa:before {
  content: "\f00c";
}
#mode-menu {
  overflow: auto;
  max-height: 20em;
}
.edit_app #header {
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
.edit_app #menubar .navbar {
  /* Use a negative 1 bottom margin, so the border overlaps the border of the
    header */
  margin-bottom: -1px;
}
.dirty-indicator {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator.pull-left {
  margin-right: .3em;
}
.dirty-indicator.pull-right {
  margin-left: .3em;
}
.dirty-indicator-dirty {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator-dirty.pull-left {
  margin-right: .3em;
}
.dirty-indicator-dirty.pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator-clean.pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean.pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f00c";
}
.dirty-indicator-clean:before.pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean:before.pull-right {
  margin-left: .3em;
}
#filename {
  font-size: 16pt;
  display: table;
  padding: 0px 5px;
}
#current-mode {
  padding-left: 5px;
  padding-right: 5px;
}
#texteditor-backdrop {
  padding-top: 20px;
  padding-bottom: 20px;
}
@media not print {
  #texteditor-backdrop {
    background-color: #EEE;
  }
}
@media print {
  #texteditor-backdrop #texteditor-container .CodeMirror-gutter,
  #texteditor-backdrop #texteditor-container .CodeMirror-gutters {
    background-color: #fff;
  }
}
@media not print {
  #texteditor-backdrop #texteditor-container .CodeMirror-gutter,
  #texteditor-backdrop #texteditor-container .CodeMirror-gutters {
    background-color: #fff;
  }
}
@media not print {
  #texteditor-backdrop #texteditor-container {
    padding: 0px;
    background-color: #fff;
    -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
    box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  }
}
/*!
*
* IPython notebook
*
*/
/* CSS font colors for translated ANSI colors. */
.ansibold {
  font-weight: bold;
}
/* use dark versions for foreground, to improve visibility */
.ansiblack {
  color: black;
}
.ansired {
  color: darkred;
}
.ansigreen {
  color: darkgreen;
}
.ansiyellow {
  color: #c4a000;
}
.ansiblue {
  color: darkblue;
}
.ansipurple {
  color: darkviolet;
}
.ansicyan {
  color: steelblue;
}
.ansigray {
  color: gray;
}
/* and light for background, for the same reason */
.ansibgblack {
  background-color: black;
}
.ansibgred {
  background-color: red;
}
.ansibggreen {
  background-color: green;
}
.ansibgyellow {
  background-color: yellow;
}
.ansibgblue {
  background-color: blue;
}
.ansibgpurple {
  background-color: magenta;
}
.ansibgcyan {
  background-color: cyan;
}
.ansibggray {
  background-color: gray;
}
div.cell {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  border-radius: 2px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  border-width: 1px;
  border-style: solid;
  border-color: transparent;
  width: 100%;
  padding: 5px;
  /* This acts as a spacer between cells, that is outside the border */
  margin: 0px;
  outline: none;
  border-left-width: 1px;
  padding-left: 5px;
  background: linear-gradient(to right, transparent -40px, transparent 1px, transparent 1px, transparent 100%);
}
div.cell.jupyter-soft-selected {
  border-left-color: #90CAF9;
  border-left-color: #E3F2FD;
  border-left-width: 1px;
  padding-left: 5px;
  border-right-color: #E3F2FD;
  border-right-width: 1px;
  background: #E3F2FD;
}
@media print {
  div.cell.jupyter-soft-selected {
    border-color: transparent;
  }
}
div.cell.selected {
  border-color: #ababab;
  border-left-width: 0px;
  padding-left: 6px;
  background: linear-gradient(to right, #42A5F5 -40px, #42A5F5 5px, transparent 5px, transparent 100%);
}
@media print {
  div.cell.selected {
    border-color: transparent;
  }
}
div.cell.selected.jupyter-soft-selected {
  border-left-width: 0;
  padding-left: 6px;
  background: linear-gradient(to right, #42A5F5 -40px, #42A5F5 7px, #E3F2FD 7px, #E3F2FD 100%);
}
.edit_mode div.cell.selected {
  border-color: #66BB6A;
  border-left-width: 0px;
  padding-left: 6px;
  background: linear-gradient(to right, #66BB6A -40px, #66BB6A 5px, transparent 5px, transparent 100%);
}
@media print {
  .edit_mode div.cell.selected {
    border-color: transparent;
  }
}
.prompt {
  /* This needs to be wide enough for 3 digit prompt numbers: In[100]: */
  min-width: 14ex;
  /* This padding is tuned to match the padding on the CodeMirror editor. */
  padding: 0.4em;
  margin: 0px;
  font-family: monospace;
  text-align: right;
  /* This has to match that of the the CodeMirror class line-height below */
  line-height: 1.21429em;
  /* Don't highlight prompt number selection */
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  /* Use default cursor */
  cursor: default;
}
@media (max-width: 540px) {
  .prompt {
    text-align: left;
  }
}
div.inner_cell {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
@-moz-document url-prefix() {
  div.inner_cell {
    overflow-x: hidden;
  }
}
/* input_area and input_prompt must match in top border and margin for alignment */
div.input_area {
  border: 1px solid #cfcfcf;
  border-radius: 2px;
  background: #f7f7f7;
  line-height: 1.21429em;
}
/* This is needed so that empty prompt areas can collapse to zero height when there
   is no content in the output_subarea and the prompt. The main purpose of this is
   to make sure that empty JavaScript output_subareas have no height. */
div.prompt:empty {
  padding-top: 0;
  padding-bottom: 0;
}
div.unrecognized_cell {
  padding: 5px 5px 5px 0px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
div.unrecognized_cell .inner_cell {
  border-radius: 2px;
  padding: 5px;
  font-weight: bold;
  color: red;
  border: 1px solid #cfcfcf;
  background: #eaeaea;
}
div.unrecognized_cell .inner_cell a {
  color: inherit;
  text-decoration: none;
}
div.unrecognized_cell .inner_cell a:hover {
  color: inherit;
  text-decoration: none;
}
@media (max-width: 540px) {
  div.unrecognized_cell > div.prompt {
    display: none;
  }
}
div.code_cell {
  /* avoid page breaking on code cells when printing */
}
@media print {
  div.code_cell {
    page-break-inside: avoid;
  }
}
/* any special styling for code cells that are currently running goes here */
div.input {
  page-break-inside: avoid;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.input {
    /* Old browsers */
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-box-align: stretch;
    display: -moz-box;
    -moz-box-orient: vertical;
    -moz-box-align: stretch;
    display: box;
    box-orient: vertical;
    box-align: stretch;
    /* Modern browsers */
    display: flex;
    flex-direction: column;
    align-items: stretch;
  }
}
/* input_area and input_prompt must match in top border and margin for alignment */
div.input_prompt {
  color: #303F9F;
  border-top: 1px solid transparent;
}
div.input_area > div.highlight {
  margin: 0.4em;
  border: none;
  padding: 0px;
  background-color: transparent;
}
div.input_area > div.highlight > pre {
  margin: 0px;
  border: none;
  padding: 0px;
  background-color: transparent;
}
/* The following gets added to the <head> if it is detected that the user has a
 * monospace font with inconsistent normal/bold/italic height.  See
 * notebookmain.js.  Such fonts will have keywords vertically offset with
 * respect to the rest of the text.  The user should select a better font.
 * See: https://github.com/ipython/ipython/issues/1503
 *
 * .CodeMirror span {
 *      vertical-align: bottom;
 * }
 */
.CodeMirror {
  line-height: 1.21429em;
  /* Changed from 1em to our global default */
  font-size: 14px;
  height: auto;
  /* Changed to auto to autogrow */
  background: none;
  /* Changed from white to allow our bg to show through */
}
.CodeMirror-scroll {
  /*  The CodeMirror docs are a bit fuzzy on if overflow-y should be hidden or visible.*/
  /*  We have found that if it is visible, vertical scrollbars appear with font size changes.*/
  overflow-y: hidden;
  overflow-x: auto;
}
.CodeMirror-lines {
  /* In CM2, this used to be 0.4em, but in CM3 it went to 4px. We need the em value because */
  /* we have set a different line-height and want this to scale with that. */
  padding: 0.4em;
}
.CodeMirror-linenumber {
  padding: 0 8px 0 4px;
}
.CodeMirror-gutters {
  border-bottom-left-radius: 2px;
  border-top-left-radius: 2px;
}
.CodeMirror pre {
  /* In CM3 this went to 4px from 0 in CM2. We need the 0 value because of how we size */
  /* .CodeMirror-lines */
  padding: 0;
  border: 0;
  border-radius: 0;
}
/*

Original style from softwaremaniacs.org (c) Ivan Sagalaev <Maniac@SoftwareManiacs.Org>
Adapted from GitHub theme

*/
.highlight-base {
  color: #000;
}
.highlight-variable {
  color: #000;
}
.highlight-variable-2 {
  color: #1a1a1a;
}
.highlight-variable-3 {
  color: #333333;
}
.highlight-string {
  color: #BA2121;
}
.highlight-comment {
  color: #408080;
  font-style: italic;
}
.highlight-number {
  color: #080;
}
.highlight-atom {
  color: #88F;
}
.highlight-keyword {
  color: #008000;
  font-weight: bold;
}
.highlight-builtin {
  color: #008000;
}
.highlight-error {
  color: #f00;
}
.highlight-operator {
  color: #AA22FF;
  font-weight: bold;
}
.highlight-meta {
  color: #AA22FF;
}
/* previously not defined, copying from default codemirror */
.highlight-def {
  color: #00f;
}
.highlight-string-2 {
  color: #f50;
}
.highlight-qualifier {
  color: #555;
}
.highlight-bracket {
  color: #997;
}
.highlight-tag {
  color: #170;
}
.highlight-attribute {
  color: #00c;
}
.highlight-header {
  color: blue;
}
.highlight-quote {
  color: #090;
}
.highlight-link {
  color: #00c;
}
/* apply the same style to codemirror */
.cm-s-ipython span.cm-keyword {
  color: #008000;
  font-weight: bold;
}
.cm-s-ipython span.cm-atom {
  color: #88F;
}
.cm-s-ipython span.cm-number {
  color: #080;
}
.cm-s-ipython span.cm-def {
  color: #00f;
}
.cm-s-ipython span.cm-variable {
  color: #000;
}
.cm-s-ipython span.cm-operator {
  color: #AA22FF;
  font-weight: bold;
}
.cm-s-ipython span.cm-variable-2 {
  color: #1a1a1a;
}
.cm-s-ipython span.cm-variable-3 {
  color: #333333;
}
.cm-s-ipython span.cm-comment {
  color: #408080;
  font-style: italic;
}
.cm-s-ipython span.cm-string {
  color: #BA2121;
}
.cm-s-ipython span.cm-string-2 {
  color: #f50;
}
.cm-s-ipython span.cm-meta {
  color: #AA22FF;
}
.cm-s-ipython span.cm-qualifier {
  color: #555;
}
.cm-s-ipython span.cm-builtin {
  color: #008000;
}
.cm-s-ipython span.cm-bracket {
  color: #997;
}
.cm-s-ipython span.cm-tag {
  color: #170;
}
.cm-s-ipython span.cm-attribute {
  color: #00c;
}
.cm-s-ipython span.cm-header {
  color: blue;
}
.cm-s-ipython span.cm-quote {
  color: #090;
}
.cm-s-ipython span.cm-link {
  color: #00c;
}
.cm-s-ipython span.cm-error {
  color: #f00;
}
.cm-s-ipython span.cm-tab {
  background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAMCAYAAAAkuj5RAAAAAXNSR0IArs4c6QAAAGFJREFUSMft1LsRQFAQheHPowAKoACx3IgEKtaEHujDjORSgWTH/ZOdnZOcM/sgk/kFFWY0qV8foQwS4MKBCS3qR6ixBJvElOobYAtivseIE120FaowJPN75GMu8j/LfMwNjh4HUpwg4LUAAAAASUVORK5CYII=);
  background-position: right;
  background-repeat: no-repeat;
}
div.output_wrapper {
  /* this position must be relative to enable descendents to be absolute within it */
  position: relative;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  z-index: 1;
}
/* class for the output area when it should be height-limited */
div.output_scroll {
  /* ideally, this would be max-height, but FF barfs all over that */
  height: 24em;
  /* FF needs this *and the wrapper* to specify full width, or it will shrinkwrap */
  width: 100%;
  overflow: auto;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 2px 8px rgba(0, 0, 0, 0.8);
  box-shadow: inset 0 2px 8px rgba(0, 0, 0, 0.8);
  display: block;
}
/* output div while it is collapsed */
div.output_collapsed {
  margin: 0px;
  padding: 0px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
div.out_prompt_overlay {
  height: 100%;
  padding: 0px 0.4em;
  position: absolute;
  border-radius: 2px;
}
div.out_prompt_overlay:hover {
  /* use inner shadow to get border that is computed the same on WebKit/FF */
  -webkit-box-shadow: inset 0 0 1px #000;
  box-shadow: inset 0 0 1px #000;
  background: rgba(240, 240, 240, 0.5);
}
div.output_prompt {
  color: #D84315;
}
/* This class is the outer container of all output sections. */
div.output_area {
  padding: 0px;
  page-break-inside: avoid;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
div.output_area .MathJax_Display {
  text-align: left !important;
}
div.output_area .rendered_html table {
  margin-left: 0;
  margin-right: 0;
}
div.output_area .rendered_html img {
  margin-left: 0;
  margin-right: 0;
}
div.output_area img,
div.output_area svg {
  max-width: 100%;
  height: auto;
}
div.output_area img.unconfined,
div.output_area svg.unconfined {
  max-width: none;
}
/* This is needed to protect the pre formating from global settings such
   as that of bootstrap */
.output {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.output_area {
    /* Old browsers */
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-box-align: stretch;
    display: -moz-box;
    -moz-box-orient: vertical;
    -moz-box-align: stretch;
    display: box;
    box-orient: vertical;
    box-align: stretch;
    /* Modern browsers */
    display: flex;
    flex-direction: column;
    align-items: stretch;
  }
}
div.output_area pre {
  margin: 0;
  padding: 0;
  border: 0;
  vertical-align: baseline;
  color: black;
  background-color: transparent;
  border-radius: 0;
}
/* This class is for the output subarea inside the output_area and after
   the prompt div. */
div.output_subarea {
  overflow-x: auto;
  padding: 0.4em;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
  max-width: calc(100% - 14ex);
}
div.output_scroll div.output_subarea {
  overflow-x: visible;
}
/* The rest of the output_* classes are for special styling of the different
   output types */
/* all text output has this class: */
div.output_text {
  text-align: left;
  color: #000;
  /* This has to match that of the the CodeMirror class line-height below */
  line-height: 1.21429em;
}
/* stdout/stderr are 'text' as well as 'stream', but execute_result/error are *not* streams */
div.output_stderr {
  background: #fdd;
  /* very light red background for stderr */
}
div.output_latex {
  text-align: left;
}
/* Empty output_javascript divs should have no height */
div.output_javascript:empty {
  padding: 0;
}
.js-error {
  color: darkred;
}
/* raw_input styles */
div.raw_input_container {
  line-height: 1.21429em;
  padding-top: 5px;
}
pre.raw_input_prompt {
  /* nothing needed here. */
}
input.raw_input {
  font-family: monospace;
  font-size: inherit;
  color: inherit;
  width: auto;
  /* make sure input baseline aligns with prompt */
  vertical-align: baseline;
  /* padding + margin = 0.5em between prompt and cursor */
  padding: 0em 0.25em;
  margin: 0em 0.25em;
}
input.raw_input:focus {
  box-shadow: none;
}
p.p-space {
  margin-bottom: 10px;
}
div.output_unrecognized {
  padding: 5px;
  font-weight: bold;
  color: red;
}
div.output_unrecognized a {
  color: inherit;
  text-decoration: none;
}
div.output_unrecognized a:hover {
  color: inherit;
  text-decoration: none;
}
.rendered_html {
  color: #000;
  /* any extras will just be numbers: */
}
.rendered_html em {
  font-style: italic;
}
.rendered_html strong {
  font-weight: bold;
}
.rendered_html u {
  text-decoration: underline;
}
.rendered_html :link {
  text-decoration: underline;
}
.rendered_html :visited {
  text-decoration: underline;
}
.rendered_html h1 {
  font-size: 185.7%;
  margin: 1.08em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h2 {
  font-size: 157.1%;
  margin: 1.27em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h3 {
  font-size: 128.6%;
  margin: 1.55em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h4 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h5 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
  font-style: italic;
}
.rendered_html h6 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
  font-style: italic;
}
.rendered_html h1:first-child {
  margin-top: 0.538em;
}
.rendered_html h2:first-child {
  margin-top: 0.636em;
}
.rendered_html h3:first-child {
  margin-top: 0.777em;
}
.rendered_html h4:first-child {
  margin-top: 1em;
}
.rendered_html h5:first-child {
  margin-top: 1em;
}
.rendered_html h6:first-child {
  margin-top: 1em;
}
.rendered_html ul {
  list-style: disc;
  margin: 0em 2em;
  padding-left: 0px;
}
.rendered_html ul ul {
  list-style: square;
  margin: 0em 2em;
}
.rendered_html ul ul ul {
  list-style: circle;
  margin: 0em 2em;
}
.rendered_html ol {
  list-style: decimal;
  margin: 0em 2em;
  padding-left: 0px;
}
.rendered_html ol ol {
  list-style: upper-alpha;
  margin: 0em 2em;
}
.rendered_html ol ol ol {
  list-style: lower-alpha;
  margin: 0em 2em;
}
.rendered_html ol ol ol ol {
  list-style: lower-roman;
  margin: 0em 2em;
}
.rendered_html ol ol ol ol ol {
  list-style: decimal;
  margin: 0em 2em;
}
.rendered_html * + ul {
  margin-top: 1em;
}
.rendered_html * + ol {
  margin-top: 1em;
}
.rendered_html hr {
  color: black;
  background-color: black;
}
.rendered_html pre {
  margin: 1em 2em;
}
.rendered_html pre,
.rendered_html code {
  border: 0;
  background-color: #fff;
  color: #000;
  font-size: 100%;
  padding: 0px;
}
.rendered_html blockquote {
  margin: 1em 2em;
}
.rendered_html table {
  margin-left: auto;
  margin-right: auto;
  border: 1px solid black;
  border-collapse: collapse;
}
.rendered_html tr,
.rendered_html th,
.rendered_html td {
  border: 1px solid black;
  border-collapse: collapse;
  margin: 1em 2em;
}
.rendered_html td,
.rendered_html th {
  text-align: left;
  vertical-align: middle;
  padding: 4px;
}
.rendered_html th {
  font-weight: bold;
}
.rendered_html * + table {
  margin-top: 1em;
}
.rendered_html p {
  text-align: left;
}
.rendered_html * + p {
  margin-top: 1em;
}
.rendered_html img {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
.rendered_html * + img {
  margin-top: 1em;
}
.rendered_html img,
.rendered_html svg {
  max-width: 100%;
  height: auto;
}
.rendered_html img.unconfined,
.rendered_html svg.unconfined {
  max-width: none;
}
div.text_cell {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.text_cell > div.prompt {
    display: none;
  }
}
div.text_cell_render {
  /*font-family: "Helvetica Neue", Arial, Helvetica, Geneva, sans-serif;*/
  outline: none;
  resize: none;
  width: inherit;
  border-style: none;
  padding: 0.5em 0.5em 0.5em 0.4em;
  color: #000;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
a.anchor-link:link {
  text-decoration: none;
  padding: 0px 20px;
  visibility: hidden;
}
h1:hover .anchor-link,
h2:hover .anchor-link,
h3:hover .anchor-link,
h4:hover .anchor-link,
h5:hover .anchor-link,
h6:hover .anchor-link {
  visibility: visible;
}
.text_cell.rendered .input_area {
  display: none;
}
.text_cell.rendered .rendered_html {
  overflow-x: auto;
  overflow-y: hidden;
}
.text_cell.unrendered .text_cell_render {
  display: none;
}
.cm-header-1,
.cm-header-2,
.cm-header-3,
.cm-header-4,
.cm-header-5,
.cm-header-6 {
  font-weight: bold;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
}
.cm-header-1 {
  font-size: 185.7%;
}
.cm-header-2 {
  font-size: 157.1%;
}
.cm-header-3 {
  font-size: 128.6%;
}
.cm-header-4 {
  font-size: 110%;
}
.cm-header-5 {
  font-size: 100%;
  font-style: italic;
}
.cm-header-6 {
  font-size: 100%;
  font-style: italic;
}
/*!
*
* IPython notebook webapp
*
*/
@media (max-width: 767px) {
  .notebook_app {
    padding-left: 0px;
    padding-right: 0px;
  }
}
#ipython-main-app {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  height: 100%;
}
div#notebook_panel {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  height: 100%;
}
div#notebook {
  font-size: 14px;
  line-height: 20px;
  overflow-y: hidden;
  overflow-x: auto;
  width: 100%;
  /* This spaces the page away from the edge of the notebook area */
  padding-top: 20px;
  margin: 0px;
  outline: none;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  min-height: 100%;
}
@media not print {
  #notebook-container {
    padding: 15px;
    background-color: #fff;
    min-height: 0;
    -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
    box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  }
}
@media print {
  #notebook-container {
    width: 100%;
  }
}
div.ui-widget-content {
  border: 1px solid #ababab;
  outline: none;
}
pre.dialog {
  background-color: #f7f7f7;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0.4em;
  padding-left: 2em;
}
p.dialog {
  padding: 0.2em;
}
/* Word-wrap output correctly.  This is the CSS3 spelling, though Firefox seems
   to not honor it correctly.  Webkit browsers (Chrome, rekonq, Safari) do.
 */
pre,
code,
kbd,
samp {
  white-space: pre-wrap;
}
#fonttest {
  font-family: monospace;
}
p {
  margin-bottom: 0;
}
.end_space {
  min-height: 100px;
  transition: height .2s ease;
}
.notebook_app > #header {
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
@media not print {
  .notebook_app {
    background-color: #EEE;
  }
}
kbd {
  border-style: solid;
  border-width: 1px;
  box-shadow: none;
  margin: 2px;
  padding-left: 2px;
  padding-right: 2px;
  padding-top: 1px;
  padding-bottom: 1px;
}
/* CSS for the cell toolbar */
.celltoolbar {
  border: thin solid #CFCFCF;
  border-bottom: none;
  background: #EEE;
  border-radius: 2px 2px 0px 0px;
  width: 100%;
  height: 29px;
  padding-right: 4px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
  /* Old browsers */
  -webkit-box-pack: end;
  -moz-box-pack: end;
  box-pack: end;
  /* Modern browsers */
  justify-content: flex-end;
  display: -webkit-flex;
}
@media print {
  .celltoolbar {
    display: none;
  }
}
.ctb_hideshow {
  display: none;
  vertical-align: bottom;
}
/* ctb_show is added to the ctb_hideshow div to show the cell toolbar.
   Cell toolbars are only shown when the ctb_global_show class is also set.
*/
.ctb_global_show .ctb_show.ctb_hideshow {
  display: block;
}
.ctb_global_show .ctb_show + .input_area,
.ctb_global_show .ctb_show + div.text_cell_input,
.ctb_global_show .ctb_show ~ div.text_cell_render {
  border-top-right-radius: 0px;
  border-top-left-radius: 0px;
}
.ctb_global_show .ctb_show ~ div.text_cell_render {
  border: 1px solid #cfcfcf;
}
.celltoolbar {
  font-size: 87%;
  padding-top: 3px;
}
.celltoolbar select {
  display: block;
  width: 100%;
  height: 32px;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  -o-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
  width: inherit;
  font-size: inherit;
  height: 22px;
  padding: 0px;
  display: inline-block;
}
.celltoolbar select:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.celltoolbar select::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.celltoolbar select:-ms-input-placeholder {
  color: #999;
}
.celltoolbar select::-webkit-input-placeholder {
  color: #999;
}
.celltoolbar select::-ms-expand {
  border: 0;
  background-color: transparent;
}
.celltoolbar select[disabled],
.celltoolbar select[readonly],
fieldset[disabled] .celltoolbar select {
  background-color: #eeeeee;
  opacity: 1;
}
.celltoolbar select[disabled],
fieldset[disabled] .celltoolbar select {
  cursor: not-allowed;
}
textarea.celltoolbar select {
  height: auto;
}
select.celltoolbar select {
  height: 30px;
  line-height: 30px;
}
textarea.celltoolbar select,
select[multiple].celltoolbar select {
  height: auto;
}
.celltoolbar label {
  margin-left: 5px;
  margin-right: 5px;
}
.completions {
  position: absolute;
  z-index: 110;
  overflow: hidden;
  border: 1px solid #ababab;
  border-radius: 2px;
  -webkit-box-shadow: 0px 6px 10px -1px #adadad;
  box-shadow: 0px 6px 10px -1px #adadad;
  line-height: 1;
}
.completions select {
  background: white;
  outline: none;
  border: none;
  padding: 0px;
  margin: 0px;
  overflow: auto;
  font-family: monospace;
  font-size: 110%;
  color: #000;
  width: auto;
}
.completions select option.context {
  color: #286090;
}
#kernel_logo_widget {
  float: right !important;
  float: right;
}
#kernel_logo_widget .current_kernel_logo {
  display: none;
  margin-top: -1px;
  margin-bottom: -1px;
  width: 32px;
  height: 32px;
}
#menubar {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  margin-top: 1px;
}
#menubar .navbar {
  border-top: 1px;
  border-radius: 0px 0px 2px 2px;
  margin-bottom: 0px;
}
#menubar .navbar-toggle {
  float: left;
  padding-top: 7px;
  padding-bottom: 7px;
  border: none;
}
#menubar .navbar-collapse {
  clear: left;
}
.nav-wrapper {
  border-bottom: 1px solid #e7e7e7;
}
i.menu-icon {
  padding-top: 4px;
}
ul#help_menu li a {
  overflow: hidden;
  padding-right: 2.2em;
}
ul#help_menu li a i {
  margin-right: -1.2em;
}
.dropdown-submenu {
  position: relative;
}
.dropdown-submenu > .dropdown-menu {
  top: 0;
  left: 100%;
  margin-top: -6px;
  margin-left: -1px;
}
.dropdown-submenu:hover > .dropdown-menu {
  display: block;
}
.dropdown-submenu > a:after {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: block;
  content: "\f0da";
  float: right;
  color: #333333;
  margin-top: 2px;
  margin-right: -10px;
}
.dropdown-submenu > a:after.pull-left {
  margin-right: .3em;
}
.dropdown-submenu > a:after.pull-right {
  margin-left: .3em;
}
.dropdown-submenu:hover > a:after {
  color: #262626;
}
.dropdown-submenu.pull-left {
  float: none;
}
.dropdown-submenu.pull-left > .dropdown-menu {
  left: -100%;
  margin-left: 10px;
}
#notification_area {
  float: right !important;
  float: right;
  z-index: 10;
}
.indicator_area {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
}
#kernel_indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
  border-left: 1px solid;
}
#kernel_indicator .kernel_indicator_name {
  padding-left: 5px;
  padding-right: 5px;
}
#modal_indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
}
#readonly-indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
  margin-top: 2px;
  margin-bottom: 0px;
  margin-left: 0px;
  margin-right: 0px;
  display: none;
}
.modal_indicator:before {
  width: 1.28571429em;
  text-align: center;
}
.edit_mode .modal_indicator:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f040";
}
.edit_mode .modal_indicator:before.pull-left {
  margin-right: .3em;
}
.edit_mode .modal_indicator:before.pull-right {
  margin-left: .3em;
}
.command_mode .modal_indicator:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: ' ';
}
.command_mode .modal_indicator:before.pull-left {
  margin-right: .3em;
}
.command_mode .modal_indicator:before.pull-right {
  margin-left: .3em;
}
.kernel_idle_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f10c";
}
.kernel_idle_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_idle_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_busy_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f111";
}
.kernel_busy_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_busy_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_dead_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f1e2";
}
.kernel_dead_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_dead_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_disconnected_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f127";
}
.kernel_disconnected_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_disconnected_icon:before.pull-right {
  margin-left: .3em;
}
.notification_widget {
  color: #777;
  z-index: 10;
  background: rgba(240, 240, 240, 0.5);
  margin-right: 4px;
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
.notification_widget:focus,
.notification_widget.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
.notification_widget:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.notification_widget:active,
.notification_widget.active,
.open > .dropdown-toggle.notification_widget {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.notification_widget:active:hover,
.notification_widget.active:hover,
.open > .dropdown-toggle.notification_widget:hover,
.notification_widget:active:focus,
.notification_widget.active:focus,
.open > .dropdown-toggle.notification_widget:focus,
.notification_widget:active.focus,
.notification_widget.active.focus,
.open > .dropdown-toggle.notification_widget.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
.notification_widget:active,
.notification_widget.active,
.open > .dropdown-toggle.notification_widget {
  background-image: none;
}
.notification_widget.disabled:hover,
.notification_widget[disabled]:hover,
fieldset[disabled] .notification_widget:hover,
.notification_widget.disabled:focus,
.notification_widget[disabled]:focus,
fieldset[disabled] .notification_widget:focus,
.notification_widget.disabled.focus,
.notification_widget[disabled].focus,
fieldset[disabled] .notification_widget.focus {
  background-color: #fff;
  border-color: #ccc;
}
.notification_widget .badge {
  color: #fff;
  background-color: #333;
}
.notification_widget.warning {
  color: #fff;
  background-color: #f0ad4e;
  border-color: #eea236;
}
.notification_widget.warning:focus,
.notification_widget.warning.focus {
  color: #fff;
  background-color: #ec971f;
  border-color: #985f0d;
}
.notification_widget.warning:hover {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.notification_widget.warning:active,
.notification_widget.warning.active,
.open > .dropdown-toggle.notification_widget.warning {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.notification_widget.warning:active:hover,
.notification_widget.warning.active:hover,
.open > .dropdown-toggle.notification_widget.warning:hover,
.notification_widget.warning:active:focus,
.notification_widget.warning.active:focus,
.open > .dropdown-toggle.notification_widget.warning:focus,
.notification_widget.warning:active.focus,
.notification_widget.warning.active.focus,
.open > .dropdown-toggle.notification_widget.warning.focus {
  color: #fff;
  background-color: #d58512;
  border-color: #985f0d;
}
.notification_widget.warning:active,
.notification_widget.warning.active,
.open > .dropdown-toggle.notification_widget.warning {
  background-image: none;
}
.notification_widget.warning.disabled:hover,
.notification_widget.warning[disabled]:hover,
fieldset[disabled] .notification_widget.warning:hover,
.notification_widget.warning.disabled:focus,
.notification_widget.warning[disabled]:focus,
fieldset[disabled] .notification_widget.warning:focus,
.notification_widget.warning.disabled.focus,
.notification_widget.warning[disabled].focus,
fieldset[disabled] .notification_widget.warning.focus {
  background-color: #f0ad4e;
  border-color: #eea236;
}
.notification_widget.warning .badge {
  color: #f0ad4e;
  background-color: #fff;
}
.notification_widget.success {
  color: #fff;
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.notification_widget.success:focus,
.notification_widget.success.focus {
  color: #fff;
  background-color: #449d44;
  border-color: #255625;
}
.notification_widget.success:hover {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.notification_widget.success:active,
.notification_widget.success.active,
.open > .dropdown-toggle.notification_widget.success {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.notification_widget.success:active:hover,
.notification_widget.success.active:hover,
.open > .dropdown-toggle.notification_widget.success:hover,
.notification_widget.success:active:focus,
.notification_widget.success.active:focus,
.open > .dropdown-toggle.notification_widget.success:focus,
.notification_widget.success:active.focus,
.notification_widget.success.active.focus,
.open > .dropdown-toggle.notification_widget.success.focus {
  color: #fff;
  background-color: #398439;
  border-color: #255625;
}
.notification_widget.success:active,
.notification_widget.success.active,
.open > .dropdown-toggle.notification_widget.success {
  background-image: none;
}
.notification_widget.success.disabled:hover,
.notification_widget.success[disabled]:hover,
fieldset[disabled] .notification_widget.success:hover,
.notification_widget.success.disabled:focus,
.notification_widget.success[disabled]:focus,
fieldset[disabled] .notification_widget.success:focus,
.notification_widget.success.disabled.focus,
.notification_widget.success[disabled].focus,
fieldset[disabled] .notification_widget.success.focus {
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.notification_widget.success .badge {
  color: #5cb85c;
  background-color: #fff;
}
.notification_widget.info {
  color: #fff;
  background-color: #5bc0de;
  border-color: #46b8da;
}
.notification_widget.info:focus,
.notification_widget.info.focus {
  color: #fff;
  background-color: #31b0d5;
  border-color: #1b6d85;
}
.notification_widget.info:hover {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.notification_widget.info:active,
.notification_widget.info.active,
.open > .dropdown-toggle.notification_widget.info {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.notification_widget.info:active:hover,
.notification_widget.info.active:hover,
.open > .dropdown-toggle.notification_widget.info:hover,
.notification_widget.info:active:focus,
.notification_widget.info.active:focus,
.open > .dropdown-toggle.notification_widget.info:focus,
.notification_widget.info:active.focus,
.notification_widget.info.active.focus,
.open > .dropdown-toggle.notification_widget.info.focus {
  color: #fff;
  background-color: #269abc;
  border-color: #1b6d85;
}
.notification_widget.info:active,
.notification_widget.info.active,
.open > .dropdown-toggle.notification_widget.info {
  background-image: none;
}
.notification_widget.info.disabled:hover,
.notification_widget.info[disabled]:hover,
fieldset[disabled] .notification_widget.info:hover,
.notification_widget.info.disabled:focus,
.notification_widget.info[disabled]:focus,
fieldset[disabled] .notification_widget.info:focus,
.notification_widget.info.disabled.focus,
.notification_widget.info[disabled].focus,
fieldset[disabled] .notification_widget.info.focus {
  background-color: #5bc0de;
  border-color: #46b8da;
}
.notification_widget.info .badge {
  color: #5bc0de;
  background-color: #fff;
}
.notification_widget.danger {
  color: #fff;
  background-color: #d9534f;
  border-color: #d43f3a;
}
.notification_widget.danger:focus,
.notification_widget.danger.focus {
  color: #fff;
  background-color: #c9302c;
  border-color: #761c19;
}
.notification_widget.danger:hover {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.notification_widget.danger:active,
.notification_widget.danger.active,
.open > .dropdown-toggle.notification_widget.danger {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.notification_widget.danger:active:hover,
.notification_widget.danger.active:hover,
.open > .dropdown-toggle.notification_widget.danger:hover,
.notification_widget.danger:active:focus,
.notification_widget.danger.active:focus,
.open > .dropdown-toggle.notification_widget.danger:focus,
.notification_widget.danger:active.focus,
.notification_widget.danger.active.focus,
.open > .dropdown-toggle.notification_widget.danger.focus {
  color: #fff;
  background-color: #ac2925;
  border-color: #761c19;
}
.notification_widget.danger:active,
.notification_widget.danger.active,
.open > .dropdown-toggle.notification_widget.danger {
  background-image: none;
}
.notification_widget.danger.disabled:hover,
.notification_widget.danger[disabled]:hover,
fieldset[disabled] .notification_widget.danger:hover,
.notification_widget.danger.disabled:focus,
.notification_widget.danger[disabled]:focus,
fieldset[disabled] .notification_widget.danger:focus,
.notification_widget.danger.disabled.focus,
.notification_widget.danger[disabled].focus,
fieldset[disabled] .notification_widget.danger.focus {
  background-color: #d9534f;
  border-color: #d43f3a;
}
.notification_widget.danger .badge {
  color: #d9534f;
  background-color: #fff;
}
div#pager {
  background-color: #fff;
  font-size: 14px;
  line-height: 20px;
  overflow: hidden;
  display: none;
  position: fixed;
  bottom: 0px;
  width: 100%;
  max-height: 50%;
  padding-top: 8px;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  /* Display over codemirror */
  z-index: 100;
  /* Hack which prevents jquery ui resizable from changing top. */
  top: auto !important;
}
div#pager pre {
  line-height: 1.21429em;
  color: #000;
  background-color: #f7f7f7;
  padding: 0.4em;
}
div#pager #pager-button-area {
  position: absolute;
  top: 8px;
  right: 20px;
}
div#pager #pager-contents {
  position: relative;
  overflow: auto;
  width: 100%;
  height: 100%;
}
div#pager #pager-contents #pager-container {
  position: relative;
  padding: 15px 0px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
div#pager .ui-resizable-handle {
  top: 0px;
  height: 8px;
  background: #f7f7f7;
  border-top: 1px solid #cfcfcf;
  border-bottom: 1px solid #cfcfcf;
  /* This injects handle bars (a short, wide = symbol) for
        the resize handle. */
}
div#pager .ui-resizable-handle::after {
  content: '';
  top: 2px;
  left: 50%;
  height: 3px;
  width: 30px;
  margin-left: -15px;
  position: absolute;
  border-top: 1px solid #cfcfcf;
}
.quickhelp {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
  line-height: 1.8em;
}
.shortcut_key {
  display: inline-block;
  width: 20ex;
  text-align: right;
  font-family: monospace;
}
.shortcut_descr {
  display: inline-block;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
span.save_widget {
  margin-top: 6px;
}
span.save_widget span.filename {
  height: 1em;
  line-height: 1em;
  padding: 3px;
  margin-left: 16px;
  border: none;
  font-size: 146.5%;
  border-radius: 2px;
}
span.save_widget span.filename:hover {
  background-color: #e6e6e6;
}
span.checkpoint_status,
span.autosave_status {
  font-size: small;
}
@media (max-width: 767px) {
  span.save_widget {
    font-size: small;
  }
  span.checkpoint_status,
  span.autosave_status {
    display: none;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  span.checkpoint_status {
    display: none;
  }
  span.autosave_status {
    font-size: x-small;
  }
}
.toolbar {
  padding: 0px;
  margin-left: -5px;
  margin-top: 2px;
  margin-bottom: 5px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
.toolbar select,
.toolbar label {
  width: auto;
  vertical-align: middle;
  margin-right: 2px;
  margin-bottom: 0px;
  display: inline;
  font-size: 92%;
  margin-left: 0.3em;
  margin-right: 0.3em;
  padding: 0px;
  padding-top: 3px;
}
.toolbar .btn {
  padding: 2px 8px;
}
.toolbar .btn-group {
  margin-top: 0px;
  margin-left: 5px;
}
#maintoolbar {
  margin-bottom: -3px;
  margin-top: -8px;
  border: 0px;
  min-height: 27px;
  margin-left: 0px;
  padding-top: 11px;
  padding-bottom: 3px;
}
#maintoolbar .navbar-text {
  float: none;
  vertical-align: middle;
  text-align: right;
  margin-left: 5px;
  margin-right: 0px;
  margin-top: 0px;
}
.select-xs {
  height: 24px;
}
.pulse,
.dropdown-menu > li > a.pulse,
li.pulse > a.dropdown-toggle,
li.pulse.open > a.dropdown-toggle {
  background-color: #F37626;
  color: white;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
/** WARNING IF YOU ARE EDITTING THIS FILE, if this is a .css file, It has a lot
 * of chance of beeing generated from the ../less/[samename].less file, you can
 * try to get back the less file by reverting somme commit in history
 **/
/*
 * We'll try to get something pretty, so we
 * have some strange css to have the scroll bar on
 * the left with fix button on the top right of the tooltip
 */
@-moz-keyframes fadeOut {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
@-webkit-keyframes fadeOut {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
@-moz-keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
@-webkit-keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
/*properties of tooltip after "expand"*/
.bigtooltip {
  overflow: auto;
  height: 200px;
  -webkit-transition-property: height;
  -webkit-transition-duration: 500ms;
  -moz-transition-property: height;
  -moz-transition-duration: 500ms;
  transition-property: height;
  transition-duration: 500ms;
}
/*properties of tooltip before "expand"*/
.smalltooltip {
  -webkit-transition-property: height;
  -webkit-transition-duration: 500ms;
  -moz-transition-property: height;
  -moz-transition-duration: 500ms;
  transition-property: height;
  transition-duration: 500ms;
  text-overflow: ellipsis;
  overflow: hidden;
  height: 80px;
}
.tooltipbuttons {
  position: absolute;
  padding-right: 15px;
  top: 0px;
  right: 0px;
}
.tooltiptext {
  /*avoid the button to overlap on some docstring*/
  padding-right: 30px;
}
.ipython_tooltip {
  max-width: 700px;
  /*fade-in animation when inserted*/
  -webkit-animation: fadeOut 400ms;
  -moz-animation: fadeOut 400ms;
  animation: fadeOut 400ms;
  -webkit-animation: fadeIn 400ms;
  -moz-animation: fadeIn 400ms;
  animation: fadeIn 400ms;
  vertical-align: middle;
  background-color: #f7f7f7;
  overflow: visible;
  border: #ababab 1px solid;
  outline: none;
  padding: 3px;
  margin: 0px;
  padding-left: 7px;
  font-family: monospace;
  min-height: 50px;
  -moz-box-shadow: 0px 6px 10px -1px #adadad;
  -webkit-box-shadow: 0px 6px 10px -1px #adadad;
  box-shadow: 0px 6px 10px -1px #adadad;
  border-radius: 2px;
  position: absolute;
  z-index: 1000;
}
.ipython_tooltip a {
  float: right;
}
.ipython_tooltip .tooltiptext pre {
  border: 0;
  border-radius: 0;
  font-size: 100%;
  background-color: #f7f7f7;
}
.pretooltiparrow {
  left: 0px;
  margin: 0px;
  top: -16px;
  width: 40px;
  height: 16px;
  overflow: hidden;
  position: absolute;
}
.pretooltiparrow:before {
  background-color: #f7f7f7;
  border: 1px #ababab solid;
  z-index: 11;
  content: "";
  position: absolute;
  left: 15px;
  top: 10px;
  width: 25px;
  height: 25px;
  -webkit-transform: rotate(45deg);
  -moz-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  -o-transform: rotate(45deg);
}
ul.typeahead-list i {
  margin-left: -10px;
  width: 18px;
}
ul.typeahead-list {
  max-height: 80vh;
  overflow: auto;
}
ul.typeahead-list > li > a {
  /** Firefox bug **/
  /* see https://github.com/jupyter/notebook/issues/559 */
  white-space: normal;
}
.cmd-palette .modal-body {
  padding: 7px;
}
.cmd-palette form {
  background: white;
}
.cmd-palette input {
  outline: none;
}
.no-shortcut {
  display: none;
}
.command-shortcut:before {
  content: "(command)";
  padding-right: 3px;
  color: #777777;
}
.edit-shortcut:before {
  content: "(edit)";
  padding-right: 3px;
  color: #777777;
}
#find-and-replace #replace-preview .match,
#find-and-replace #replace-preview .insert {
  background-color: #BBDEFB;
  border-color: #90CAF9;
  border-style: solid;
  border-width: 1px;
  border-radius: 0px;
}
#find-and-replace #replace-preview .replace .match {
  background-color: #FFCDD2;
  border-color: #EF9A9A;
  border-radius: 0px;
}
#find-and-replace #replace-preview .replace .insert {
  background-color: #C8E6C9;
  border-color: #A5D6A7;
  border-radius: 0px;
}
#find-and-replace #replace-preview {
  max-height: 60vh;
  overflow: auto;
}
#find-and-replace #replace-preview pre {
  padding: 5px 10px;
}
.terminal-app {
  background: #EEE;
}
.terminal-app #header {
  background: #fff;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
.terminal-app .terminal {
  float: left;
  font-family: monospace;
  color: white;
  background: black;
  padding: 0.4em;
  border-radius: 2px;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.4);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.4);
}
.terminal-app .terminal,
.terminal-app .terminal dummy-screen {
  line-height: 1em;
  font-size: 14px;
}
.terminal-app .terminal-cursor {
  color: black;
  background: white;
}
.terminal-app #terminado-container {
  margin-top: 20px;
}
/*# sourceMappingURL=style.min.css.map */
    </style>
<style type="text/css">
    .highlight .hll { background-color: #ffffcc }
.highlight  { background: #f8f8f8; }
.highlight .c { color: #408080; font-style: italic } /* Comment */
.highlight .err { border: 1px solid #FF0000 } /* Error */
.highlight .k { color: #008000; font-weight: bold } /* Keyword */
.highlight .o { color: #666666 } /* Operator */
.highlight .ch { color: #408080; font-style: italic } /* Comment.Hashbang */
.highlight .cm { color: #408080; font-style: italic } /* Comment.Multiline */
.highlight .cp { color: #BC7A00 } /* Comment.Preproc */
.highlight .cpf { color: #408080; font-style: italic } /* Comment.PreprocFile */
.highlight .c1 { color: #408080; font-style: italic } /* Comment.Single */
.highlight .cs { color: #408080; font-style: italic } /* Comment.Special */
.highlight .gd { color: #A00000 } /* Generic.Deleted */
.highlight .ge { font-style: italic } /* Generic.Emph */
.highlight .gr { color: #FF0000 } /* Generic.Error */
.highlight .gh { color: #000080; font-weight: bold } /* Generic.Heading */
.highlight .gi { color: #00A000 } /* Generic.Inserted */
.highlight .go { color: #888888 } /* Generic.Output */
.highlight .gp { color: #000080; font-weight: bold } /* Generic.Prompt */
.highlight .gs { font-weight: bold } /* Generic.Strong */
.highlight .gu { color: #800080; font-weight: bold } /* Generic.Subheading */
.highlight .gt { color: #0044DD } /* Generic.Traceback */
.highlight .kc { color: #008000; font-weight: bold } /* Keyword.Constant */
.highlight .kd { color: #008000; font-weight: bold } /* Keyword.Declaration */
.highlight .kn { color: #008000; font-weight: bold } /* Keyword.Namespace */
.highlight .kp { color: #008000 } /* Keyword.Pseudo */
.highlight .kr { color: #008000; font-weight: bold } /* Keyword.Reserved */
.highlight .kt { color: #B00040 } /* Keyword.Type */
.highlight .m { color: #666666 } /* Literal.Number */
.highlight .s { color: #BA2121 } /* Literal.String */
.highlight .na { color: #7D9029 } /* Name.Attribute */
.highlight .nb { color: #008000 } /* Name.Builtin */
.highlight .nc { color: #0000FF; font-weight: bold } /* Name.Class */
.highlight .no { color: #880000 } /* Name.Constant */
.highlight .nd { color: #AA22FF } /* Name.Decorator */
.highlight .ni { color: #999999; font-weight: bold } /* Name.Entity */
.highlight .ne { color: #D2413A; font-weight: bold } /* Name.Exception */
.highlight .nf { color: #0000FF } /* Name.Function */
.highlight .nl { color: #A0A000 } /* Name.Label */
.highlight .nn { color: #0000FF; font-weight: bold } /* Name.Namespace */
.highlight .nt { color: #008000; font-weight: bold } /* Name.Tag */
.highlight .nv { color: #19177C } /* Name.Variable */
.highlight .ow { color: #AA22FF; font-weight: bold } /* Operator.Word */
.highlight .w { color: #bbbbbb } /* Text.Whitespace */
.highlight .mb { color: #666666 } /* Literal.Number.Bin */
.highlight .mf { color: #666666 } /* Literal.Number.Float */
.highlight .mh { color: #666666 } /* Literal.Number.Hex */
.highlight .mi { color: #666666 } /* Literal.Number.Integer */
.highlight .mo { color: #666666 } /* Literal.Number.Oct */
.highlight .sb { color: #BA2121 } /* Literal.String.Backtick */
.highlight .sc { color: #BA2121 } /* Literal.String.Char */
.highlight .sd { color: #BA2121; font-style: italic } /* Literal.String.Doc */
.highlight .s2 { color: #BA2121 } /* Literal.String.Double */
.highlight .se { color: #BB6622; font-weight: bold } /* Literal.String.Escape */
.highlight .sh { color: #BA2121 } /* Literal.String.Heredoc */
.highlight .si { color: #BB6688; font-weight: bold } /* Literal.String.Interpol */
.highlight .sx { color: #008000 } /* Literal.String.Other */
.highlight .sr { color: #BB6688 } /* Literal.String.Regex */
.highlight .s1 { color: #BA2121 } /* Literal.String.Single */
.highlight .ss { color: #19177C } /* Literal.String.Symbol */
.highlight .bp { color: #008000 } /* Name.Builtin.Pseudo */
.highlight .vc { color: #19177C } /* Name.Variable.Class */
.highlight .vg { color: #19177C } /* Name.Variable.Global */
.highlight .vi { color: #19177C } /* Name.Variable.Instance */
.highlight .il { color: #666666 } /* Literal.Number.Integer.Long */
    </style>
<style type="text/css">

/* Temporary definitions which will become obsolete with Notebook release 5.0 */
.ansi-black-fg { color: #3E424D; }
.ansi-black-bg { background-color: #3E424D; }
.ansi-black-intense-fg { color: #282C36; }
.ansi-black-intense-bg { background-color: #282C36; }
.ansi-red-fg { color: #E75C58; }
.ansi-red-bg { background-color: #E75C58; }
.ansi-red-intense-fg { color: #B22B31; }
.ansi-red-intense-bg { background-color: #B22B31; }
.ansi-green-fg { color: #00A250; }
.ansi-green-bg { background-color: #00A250; }
.ansi-green-intense-fg { color: #007427; }
.ansi-green-intense-bg { background-color: #007427; }
.ansi-yellow-fg { color: #DDB62B; }
.ansi-yellow-bg { background-color: #DDB62B; }
.ansi-yellow-intense-fg { color: #B27D12; }
.ansi-yellow-intense-bg { background-color: #B27D12; }
.ansi-blue-fg { color: #208FFB; }
.ansi-blue-bg { background-color: #208FFB; }
.ansi-blue-intense-fg { color: #0065CA; }
.ansi-blue-intense-bg { background-color: #0065CA; }
.ansi-magenta-fg { color: #D160C4; }
.ansi-magenta-bg { background-color: #D160C4; }
.ansi-magenta-intense-fg { color: #A03196; }
.ansi-magenta-intense-bg { background-color: #A03196; }
.ansi-cyan-fg { color: #60C6C8; }
.ansi-cyan-bg { background-color: #60C6C8; }
.ansi-cyan-intense-fg { color: #258F8F; }
.ansi-cyan-intense-bg { background-color: #258F8F; }
.ansi-white-fg { color: #C5C1B4; }
.ansi-white-bg { background-color: #C5C1B4; }
.ansi-white-intense-fg { color: #A1A6B2; }
.ansi-white-intense-bg { background-color: #A1A6B2; }

.ansi-bold { font-weight: bold; }

    </style>


<style type="text/css">
/* Overrides of notebook CSS for static HTML export */
body {
  overflow: visible;
  padding: 8px;
}

div#notebook {
  overflow: visible;
  border-top: none;
}

@media print {
  div.cell {
    display: block;
    page-break-inside: avoid;
  }
  div.output_wrapper {
    display: block;
    page-break-inside: avoid;
  }
  div.output {
    display: block;
    page-break-inside: avoid;
  }
}
</style>

<!-- Custom stylesheet, it must be in the same directory as the html file -->
<link rel="stylesheet" href="custom.css">

<!-- Loading mathjax macro -->
<!-- Load mathjax -->
    <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS_HTML"></script>
    <!-- MathJax configuration -->
    <script type="text/x-mathjax-config">
    MathJax.Hub.Config({
        tex2jax: {
            inlineMath: [ ['$','$'], ["\\(","\\)"] ],
            displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
            processEscapes: true,
            processEnvironments: true
        },
        // Center justify equations in code and markdown cells. Elsewhere
        // we use CSS to left justify single line equations in code cells.
        displayAlign: 'center',
        "HTML-CSS": {
            styles: {'.MathJax_Display': {"margin": 0}},
            linebreaks: { automatic: true }
        }
    });
    </script>
    <!-- End of mathjax configuration --></head>
<body>
  <div tabindex="-1" id="notebook" class="border-box-sizing">
    <div class="container" id="notebook-container">
---
layout: post
title: Machine learning, not what I thought
---
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><em>This post is my first exploration into using python to analyse stock data.  Over the coming months I plan to gain an understanding of the basics in commodity trading and how to automate simple trend trading strategies in python.</em></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="References:">References:<a class="anchor-link" href="#References:">&#182;</a></h4><p><a href="https://ntguardian.wordpress.com/2016/09/19/introduction-stock-market-data-python-1/?utm_campaign=Revue%20newsletter&amp;utm_medium=Newsletter&amp;utm_source=revue">An Introduction to Stock Market Data Analysis with Python (Part 1)</a></p>
<p><a href="https://en.wikipedia.org/wiki/Average_directional_movement_index">Average Directional Index</a></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><strong>NOTE: The information provided in this article should not be considered financial advice!</strong></p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>My girlfriend recently mentioned she had been succesfully trading commodities for the last few years.  Naturally I got her to talk me through her process and what struck me was the simplicity behind her method.  It seems anyone can follow a set of basic technical indicators to guide decision making, however, the real success of a trader appears to be related to emotional detachment and a constistent mindset.</p>
<p>Nevertheless I decided to try to deconstruct her trading strategy, with a long term goal to fully automate it (and never have to get out of bed).</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The first technical indicator I learned about was the average directional index (ADX).  Developed in 1978 by J. Welles Wilder, the ADX is an indicator of the strength of a trend in stock price.</p>
<p>Although many packages exist to calculate this index for you, I decided to keep it simple to start with and manually code this indicator in python:</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Below I read in data from the Yahoo Finance API for Apple stock since the start of 2016.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[1]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">warnings</span>
<span class="n">warnings</span><span class="o">.</span><span class="n">filterwarnings</span><span class="p">(</span><span class="s1">&#39;ignore&#39;</span><span class="p">)</span>

<span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
<span class="kn">import</span> <span class="nn">pandas.io.data</span> <span class="k">as</span> <span class="nn">web</span>
<span class="kn">import</span> <span class="nn">datetime</span>

<span class="c1"># We will look at stock prices over the past year, starting at January 1, 2016</span>
<span class="n">start</span> <span class="o">=</span> <span class="n">datetime</span><span class="o">.</span><span class="n">datetime</span><span class="p">(</span><span class="mi">2016</span><span class="p">,</span><span class="mi">1</span><span class="p">,</span><span class="mi">1</span><span class="p">)</span>
<span class="n">end</span> <span class="o">=</span> <span class="n">datetime</span><span class="o">.</span><span class="n">date</span><span class="o">.</span><span class="n">today</span><span class="p">()</span>

<span class="c1"># Let&#39;s get Apple stock data, from yahoo finance within the dates specified</span>
<span class="n">apple</span> <span class="o">=</span> <span class="n">web</span><span class="o">.</span><span class="n">DataReader</span><span class="p">(</span><span class="s2">&quot;AAPL&quot;</span><span class="p">,</span> <span class="s2">&quot;yahoo&quot;</span><span class="p">,</span> <span class="n">start</span><span class="p">,</span> <span class="n">end</span><span class="p">)</span>

<span class="n">apple</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="n">n</span><span class="o">=</span><span class="mi">5</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt output_prompt">Out[1]:</div>

<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Volume</th>
      <th>Adj Close</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-01-04</th>
      <td>102.610001</td>
      <td>105.370003</td>
      <td>102.000000</td>
      <td>105.349998</td>
      <td>67649400</td>
      <td>103.057063</td>
    </tr>
    <tr>
      <th>2016-01-05</th>
      <td>105.750000</td>
      <td>105.849998</td>
      <td>102.410004</td>
      <td>102.709999</td>
      <td>55791000</td>
      <td>100.474523</td>
    </tr>
    <tr>
      <th>2016-01-06</th>
      <td>100.559998</td>
      <td>102.370003</td>
      <td>99.870003</td>
      <td>100.699997</td>
      <td>68457400</td>
      <td>98.508268</td>
    </tr>
    <tr>
      <th>2016-01-07</th>
      <td>98.680000</td>
      <td>100.129997</td>
      <td>96.430000</td>
      <td>96.449997</td>
      <td>81094400</td>
      <td>94.350769</td>
    </tr>
    <tr>
      <th>2016-01-08</th>
      <td>98.550003</td>
      <td>99.110001</td>
      <td>96.760002</td>
      <td>96.959999</td>
      <td>70798000</td>
      <td>94.849671</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The first step is to calculate the directional movement (+DM and −DM) according to the following equations:</p>
<p>UpMove = today's high − yesterday's high</p>
<p>DownMove = yesterday's low − today's low</p>
<p>if UpMove &gt; DownMove and UpMove &gt; 0, then +DM = UpMove, else +DM = 0</p>
<p>if DownMove &gt; UpMove and DownMove &gt; 0, then −DM = DownMove, else −DM = 0</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[2]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#calculate downmove and upmove</span>
<span class="n">UpMove</span><span class="o">=</span> <span class="p">(</span><span class="n">apple</span><span class="o">.</span><span class="n">High</span> <span class="o">-</span> <span class="n">apple</span><span class="o">.</span><span class="n">High</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="mi">1</span><span class="p">))</span>
<span class="n">DownMove</span> <span class="o">=</span> <span class="p">(</span><span class="n">apple</span><span class="o">.</span><span class="n">Low</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="mi">1</span><span class="p">)</span> <span class="o">-</span> <span class="n">apple</span><span class="o">.</span><span class="n">Low</span><span class="p">)</span>

<span class="c1">#calculating the directional movement</span>
<span class="n">apple</span><span class="p">[</span><span class="s1">&#39;DM+&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">where</span><span class="p">(</span><span class="n">UpMove</span> <span class="o">&lt;=</span> <span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">,</span> <span class="n">np</span><span class="o">.</span><span class="n">where</span><span class="p">(</span><span class="n">UpMove</span> <span class="o">&gt;</span> <span class="n">DownMove</span><span class="p">,</span> <span class="n">UpMove</span><span class="p">,</span> <span class="mi">0</span><span class="p">))</span>
<span class="n">apple</span><span class="p">[</span><span class="s1">&#39;DM-&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">where</span><span class="p">(</span><span class="n">DownMove</span> <span class="o">&lt;=</span> <span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">,</span> <span class="n">np</span><span class="o">.</span><span class="n">where</span><span class="p">(</span><span class="n">DownMove</span> <span class="o">&gt;</span> <span class="n">UpMove</span><span class="p">,</span> <span class="n">DownMove</span><span class="p">,</span> <span class="mi">0</span><span class="p">))</span>

<span class="n">apple</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="n">n</span><span class="o">=</span><span class="mi">5</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt output_prompt">Out[2]:</div>

<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Volume</th>
      <th>Adj Close</th>
      <th>DM+</th>
      <th>DM-</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-01-04</th>
      <td>102.610001</td>
      <td>105.370003</td>
      <td>102.000000</td>
      <td>105.349998</td>
      <td>67649400</td>
      <td>103.057063</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>2016-01-05</th>
      <td>105.750000</td>
      <td>105.849998</td>
      <td>102.410004</td>
      <td>102.709999</td>
      <td>55791000</td>
      <td>100.474523</td>
      <td>0.479995</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>2016-01-06</th>
      <td>100.559998</td>
      <td>102.370003</td>
      <td>99.870003</td>
      <td>100.699997</td>
      <td>68457400</td>
      <td>98.508268</td>
      <td>0.000000</td>
      <td>2.540001</td>
    </tr>
    <tr>
      <th>2016-01-07</th>
      <td>98.680000</td>
      <td>100.129997</td>
      <td>96.430000</td>
      <td>96.449997</td>
      <td>81094400</td>
      <td>94.350769</td>
      <td>0.000000</td>
      <td>3.440003</td>
    </tr>
    <tr>
      <th>2016-01-08</th>
      <td>98.550003</td>
      <td>99.110001</td>
      <td>96.760002</td>
      <td>96.959999</td>
      <td>70798000</td>
      <td>94.849671</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Then the true range must be calculated:</p>
$$TR = max((high-low),abs(high-close_{prev}, abs(low-close_{prev}))$$
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[3]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#values req for true range calc</span>
<span class="n">a</span> <span class="o">=</span> <span class="p">(</span><span class="n">apple</span><span class="o">.</span><span class="n">High</span> <span class="o">-</span> <span class="n">apple</span><span class="o">.</span><span class="n">Low</span><span class="p">)</span>
<span class="n">b</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">absolute</span><span class="p">(</span><span class="n">apple</span><span class="o">.</span><span class="n">High</span> <span class="o">-</span> <span class="n">apple</span><span class="o">.</span><span class="n">Close</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="mi">1</span><span class="p">))</span>
<span class="n">c</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">absolute</span><span class="p">(</span><span class="n">apple</span><span class="o">.</span><span class="n">Low</span> <span class="o">-</span> <span class="n">apple</span><span class="o">.</span><span class="n">Close</span><span class="o">.</span><span class="n">shift</span><span class="p">(</span><span class="mi">1</span><span class="p">))</span>

<span class="c1">#calculating the true range</span>
<span class="n">apple</span><span class="p">[</span><span class="s1">&#39;TR&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">column_stack</span><span class="p">((</span><span class="n">a</span><span class="p">,</span><span class="n">b</span><span class="p">,</span><span class="n">c</span><span class="p">))</span><span class="o">.</span><span class="n">max</span><span class="p">(</span><span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">)</span>

<span class="n">apple</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="n">n</span><span class="o">=</span><span class="mi">5</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt output_prompt">Out[3]:</div>

<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Volume</th>
      <th>Adj Close</th>
      <th>DM+</th>
      <th>DM-</th>
      <th>TR</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-01-04</th>
      <td>102.610001</td>
      <td>105.370003</td>
      <td>102.000000</td>
      <td>105.349998</td>
      <td>67649400</td>
      <td>103.057063</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-05</th>
      <td>105.750000</td>
      <td>105.849998</td>
      <td>102.410004</td>
      <td>102.709999</td>
      <td>55791000</td>
      <td>100.474523</td>
      <td>0.479995</td>
      <td>0.000000</td>
      <td>3.439994</td>
    </tr>
    <tr>
      <th>2016-01-06</th>
      <td>100.559998</td>
      <td>102.370003</td>
      <td>99.870003</td>
      <td>100.699997</td>
      <td>68457400</td>
      <td>98.508268</td>
      <td>0.000000</td>
      <td>2.540001</td>
      <td>2.839996</td>
    </tr>
    <tr>
      <th>2016-01-07</th>
      <td>98.680000</td>
      <td>100.129997</td>
      <td>96.430000</td>
      <td>96.449997</td>
      <td>81094400</td>
      <td>94.350769</td>
      <td>0.000000</td>
      <td>3.440003</td>
      <td>4.269997</td>
    </tr>
    <tr>
      <th>2016-01-08</th>
      <td>98.550003</td>
      <td>99.110001</td>
      <td>96.760002</td>
      <td>96.959999</td>
      <td>70798000</td>
      <td>94.849671</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>2.660004</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Wilder defined his own smoothed moving average according to the following formula:</p>
$$WSMA(i) = \frac{WSMA_{i-1} \times (N-1) + CLOSE_{i}}{N}$$<p>Where:</p>
<p>$WSMA_1 =$ Wilder’s Smoothing for the first period.  This is just the first numerical term in a standard moving average.</p>
<p>$WSMA(i)$ = Wilder’s Smoothing of the current period (excluding the first WSMA).</p>
<p>$CLOSE_{i}$ = The current closing price.</p>
<p>N = The smoothing period, traditionally 14 days.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[4]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="k">def</span> <span class="nf">wsma</span><span class="p">(</span><span class="n">array</span><span class="p">,</span> <span class="n">period</span><span class="p">):</span>

    <span class="c1">#calculate the first WSMA value and find its index</span>
    <span class="nb">list</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">rolling_mean</span><span class="p">(</span><span class="n">array</span><span class="p">,</span> <span class="n">window</span> <span class="o">=</span> <span class="n">period</span><span class="p">)</span>
    <span class="n">list_NA</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">isnan</span><span class="p">(</span><span class="nb">list</span><span class="p">)</span>
    <span class="n">start</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">where</span><span class="p">(</span><span class="n">list_NA</span> <span class="o">==</span> <span class="kc">False</span><span class="p">)[</span><span class="mi">0</span><span class="p">][</span><span class="mi">0</span><span class="p">]</span>


    <span class="c1">#then the following wilder smoothed averages are calculated</span>
    <span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="nb">len</span><span class="p">(</span><span class="n">array</span><span class="p">)</span><span class="o">-</span><span class="mi">1</span><span class="p">):</span>

        <span class="k">if</span> <span class="n">i</span> <span class="o">&gt;=</span> <span class="n">start</span><span class="p">:</span>

            <span class="nb">list</span><span class="p">[</span><span class="n">i</span><span class="o">+</span><span class="mi">1</span><span class="p">]</span> <span class="o">=</span> <span class="p">(</span><span class="nb">list</span><span class="p">[</span><span class="n">i</span><span class="p">]</span> <span class="o">*</span> <span class="p">(</span><span class="n">period</span> <span class="o">-</span> <span class="mi">1</span><span class="p">)</span> <span class="o">+</span> <span class="n">array</span><span class="p">[</span><span class="n">i</span><span class="o">+</span><span class="mi">1</span><span class="p">])</span> <span class="o">/</span> <span class="n">period</span>


    <span class="k">return</span><span class="p">(</span><span class="nb">list</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>For example in the code below we see that the first value returned is a moving average of the first 5 values.  Subsequent values are calculated according to $WSMA(i) = \frac{WSMA_{i-1} \times (N-1) + CLOSE_{i}}{N}$.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[5]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">([</span><span class="mi">2</span><span class="p">,</span><span class="mi">3</span><span class="p">,</span><span class="mi">1</span><span class="p">,</span><span class="mi">0</span><span class="p">,</span><span class="mi">3</span><span class="p">,</span><span class="mi">2</span><span class="p">,</span><span class="mi">1</span><span class="p">,</span><span class="mi">4</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>
<span class="n">wsma</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="mi">5</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt"></div>
<div class="output_subarea output_stream output_stdout output_text">
<pre>[2 3 1 0 3 2 1 4]
</pre>
</div>
</div>

<div class="output_area"><div class="prompt output_prompt">Out[5]:</div>


<div class="output_text output_subarea output_execute_result">
<pre>array([    nan,     nan,     nan,     nan,  1.8   ,  1.84  ,  1.672 ,
        2.1376])</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>This function is applied below to find the smoothed moving average of the true range and both directional movements.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[6]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">apple</span><span class="p">[</span><span class="s1">&#39;ATR&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">wsma</span><span class="p">(</span><span class="n">apple</span><span class="p">[</span><span class="s1">&#39;TR&#39;</span><span class="p">],</span> <span class="mi">14</span><span class="p">)</span>
<span class="n">apple</span><span class="p">[</span><span class="s1">&#39;ADI+&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">wsma</span><span class="p">(</span><span class="n">apple</span><span class="p">[</span><span class="s1">&#39;DM+&#39;</span><span class="p">],</span> <span class="mi">14</span><span class="p">)</span>
<span class="n">apple</span><span class="p">[</span><span class="s1">&#39;ADI-&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">wsma</span><span class="p">(</span><span class="n">apple</span><span class="p">[</span><span class="s1">&#39;DM-&#39;</span><span class="p">],</span> <span class="mi">14</span><span class="p">)</span>

<span class="n">apple</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="n">n</span><span class="o">=</span><span class="mi">20</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt output_prompt">Out[6]:</div>

<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Volume</th>
      <th>Adj Close</th>
      <th>DM+</th>
      <th>DM-</th>
      <th>TR</th>
      <th>ATR</th>
      <th>ADI+</th>
      <th>ADI-</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-01-04</th>
      <td>102.610001</td>
      <td>105.370003</td>
      <td>102.000000</td>
      <td>105.349998</td>
      <td>67649400</td>
      <td>103.057063</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-05</th>
      <td>105.750000</td>
      <td>105.849998</td>
      <td>102.410004</td>
      <td>102.709999</td>
      <td>55791000</td>
      <td>100.474523</td>
      <td>0.479995</td>
      <td>0.000000</td>
      <td>3.439994</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-06</th>
      <td>100.559998</td>
      <td>102.370003</td>
      <td>99.870003</td>
      <td>100.699997</td>
      <td>68457400</td>
      <td>98.508268</td>
      <td>0.000000</td>
      <td>2.540001</td>
      <td>2.839996</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-07</th>
      <td>98.680000</td>
      <td>100.129997</td>
      <td>96.430000</td>
      <td>96.449997</td>
      <td>81094400</td>
      <td>94.350769</td>
      <td>0.000000</td>
      <td>3.440003</td>
      <td>4.269997</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-08</th>
      <td>98.550003</td>
      <td>99.110001</td>
      <td>96.760002</td>
      <td>96.959999</td>
      <td>70798000</td>
      <td>94.849671</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>2.660004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-11</th>
      <td>98.970001</td>
      <td>99.059998</td>
      <td>97.339996</td>
      <td>98.529999</td>
      <td>49739400</td>
      <td>96.385500</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>2.099999</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-12</th>
      <td>100.550003</td>
      <td>100.690002</td>
      <td>98.839996</td>
      <td>99.959999</td>
      <td>49154200</td>
      <td>97.784376</td>
      <td>1.630004</td>
      <td>0.000000</td>
      <td>2.160003</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-13</th>
      <td>100.320000</td>
      <td>101.190002</td>
      <td>97.300003</td>
      <td>97.389999</td>
      <td>62439600</td>
      <td>95.270312</td>
      <td>0.000000</td>
      <td>1.539993</td>
      <td>3.889999</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-14</th>
      <td>97.959999</td>
      <td>100.480003</td>
      <td>95.739998</td>
      <td>99.519997</td>
      <td>63170100</td>
      <td>97.353950</td>
      <td>0.000000</td>
      <td>1.560005</td>
      <td>4.740005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-15</th>
      <td>96.199997</td>
      <td>97.709999</td>
      <td>95.360001</td>
      <td>97.129997</td>
      <td>79010000</td>
      <td>95.015969</td>
      <td>0.000000</td>
      <td>0.379997</td>
      <td>4.159996</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-19</th>
      <td>98.410004</td>
      <td>98.650002</td>
      <td>95.500000</td>
      <td>96.660004</td>
      <td>53087700</td>
      <td>94.556205</td>
      <td>0.940003</td>
      <td>0.000000</td>
      <td>3.150002</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-20</th>
      <td>95.099998</td>
      <td>98.190002</td>
      <td>93.419998</td>
      <td>96.790001</td>
      <td>72334400</td>
      <td>94.683373</td>
      <td>0.000000</td>
      <td>2.080002</td>
      <td>4.770004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-21</th>
      <td>97.059998</td>
      <td>97.879997</td>
      <td>94.940002</td>
      <td>96.300003</td>
      <td>52161500</td>
      <td>94.204040</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>2.939995</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-22</th>
      <td>98.629997</td>
      <td>101.459999</td>
      <td>98.370003</td>
      <td>101.419998</td>
      <td>65800500</td>
      <td>99.212599</td>
      <td>3.580002</td>
      <td>0.000000</td>
      <td>5.159996</td>
      <td>NaN</td>
      <td>0.473572</td>
      <td>0.824286</td>
    </tr>
    <tr>
      <th>2016-01-25</th>
      <td>101.519997</td>
      <td>101.529999</td>
      <td>99.209999</td>
      <td>99.440002</td>
      <td>51794500</td>
      <td>97.275697</td>
      <td>0.070000</td>
      <td>0.000000</td>
      <td>2.320000</td>
      <td>3.471428</td>
      <td>0.444745</td>
      <td>0.765408</td>
    </tr>
    <tr>
      <th>2016-01-26</th>
      <td>99.930000</td>
      <td>100.879997</td>
      <td>98.070000</td>
      <td>99.989998</td>
      <td>75077000</td>
      <td>97.813722</td>
      <td>0.000000</td>
      <td>1.139999</td>
      <td>2.809997</td>
      <td>3.424183</td>
      <td>0.412978</td>
      <td>0.792165</td>
    </tr>
    <tr>
      <th>2016-01-27</th>
      <td>96.040001</td>
      <td>96.629997</td>
      <td>93.339996</td>
      <td>93.419998</td>
      <td>133369700</td>
      <td>91.386718</td>
      <td>0.000000</td>
      <td>4.730004</td>
      <td>6.650002</td>
      <td>3.654598</td>
      <td>0.383479</td>
      <td>1.073439</td>
    </tr>
    <tr>
      <th>2016-01-28</th>
      <td>93.790001</td>
      <td>94.519997</td>
      <td>92.389999</td>
      <td>94.089996</td>
      <td>55678800</td>
      <td>92.042134</td>
      <td>0.000000</td>
      <td>0.949997</td>
      <td>2.129998</td>
      <td>3.545698</td>
      <td>0.356088</td>
      <td>1.064622</td>
    </tr>
    <tr>
      <th>2016-01-29</th>
      <td>94.790001</td>
      <td>97.339996</td>
      <td>94.349998</td>
      <td>97.339996</td>
      <td>64416500</td>
      <td>95.221398</td>
      <td>2.819999</td>
      <td>0.000000</td>
      <td>3.250000</td>
      <td>3.524577</td>
      <td>0.532082</td>
      <td>0.988577</td>
    </tr>
    <tr>
      <th>2016-02-01</th>
      <td>96.470001</td>
      <td>96.709999</td>
      <td>95.400002</td>
      <td>96.430000</td>
      <td>40943500</td>
      <td>94.331208</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>1.939994</td>
      <td>3.411393</td>
      <td>0.494076</td>
      <td>0.917965</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>We can now calculate the positive directional index, negetive directional index and average directional index:</p>
$$+DI = 100 \times \frac{ADI+}{ATR}$$$$-DI = 100 \times \frac{ADI-}{ATR}$$<p>Then:</p>
$$DX = 100 \times abs\frac{+DI − −DI}{+DI + −DI}$$$$ADX = WSMA(DX)$$
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[7]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#now calculate the +DI and -DI</span>
<span class="n">apple</span><span class="p">[</span><span class="s1">&#39;+DMI&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="mi">100</span> <span class="o">*</span> <span class="n">apple</span><span class="p">[</span><span class="s1">&#39;ADI+&#39;</span><span class="p">]</span> <span class="o">/</span> <span class="n">apple</span><span class="p">[</span><span class="s1">&#39;ATR&#39;</span><span class="p">]</span>
<span class="n">apple</span><span class="p">[</span><span class="s1">&#39;-DMI&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="mi">100</span> <span class="o">*</span> <span class="n">apple</span><span class="p">[</span><span class="s1">&#39;ADI-&#39;</span><span class="p">]</span> <span class="o">/</span> <span class="n">apple</span><span class="p">[</span><span class="s1">&#39;ATR&#39;</span><span class="p">]</span>

<span class="c1">#calculate DX</span>
<span class="n">DX</span> <span class="o">=</span> <span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">absolute</span><span class="p">(</span><span class="n">apple</span><span class="p">[</span><span class="s1">&#39;+DMI&#39;</span><span class="p">]</span> <span class="o">-</span> <span class="n">apple</span><span class="p">[</span><span class="s1">&#39;-DMI&#39;</span><span class="p">])</span> <span class="o">/</span> <span class="p">(</span><span class="n">apple</span><span class="p">[</span><span class="s1">&#39;+DMI&#39;</span><span class="p">]</span> <span class="o">+</span> <span class="n">apple</span><span class="p">[</span><span class="s1">&#39;-DMI&#39;</span><span class="p">]))</span><span class="o">*</span><span class="mi">100</span>

<span class="c1">#finally one more smoothed average of DX to obtain ADX</span>
<span class="n">apple</span><span class="p">[</span><span class="s1">&#39;ADX&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">wsma</span><span class="p">(</span><span class="n">DX</span><span class="p">,</span> <span class="n">period</span> <span class="o">=</span> <span class="mi">14</span><span class="p">)</span>

<span class="n">apple</span><span class="o">.</span><span class="n">head</span><span class="p">(</span><span class="n">n</span> <span class="o">=</span> <span class="mi">30</span><span class="p">)</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt output_prompt">Out[7]:</div>

<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Volume</th>
      <th>Adj Close</th>
      <th>DM+</th>
      <th>DM-</th>
      <th>TR</th>
      <th>ATR</th>
      <th>ADI+</th>
      <th>ADI-</th>
      <th>+DMI</th>
      <th>-DMI</th>
      <th>ADX</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2016-01-04</th>
      <td>102.610001</td>
      <td>105.370003</td>
      <td>102.000000</td>
      <td>105.349998</td>
      <td>67649400</td>
      <td>103.057063</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-05</th>
      <td>105.750000</td>
      <td>105.849998</td>
      <td>102.410004</td>
      <td>102.709999</td>
      <td>55791000</td>
      <td>100.474523</td>
      <td>0.479995</td>
      <td>0.000000</td>
      <td>3.439994</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-06</th>
      <td>100.559998</td>
      <td>102.370003</td>
      <td>99.870003</td>
      <td>100.699997</td>
      <td>68457400</td>
      <td>98.508268</td>
      <td>0.000000</td>
      <td>2.540001</td>
      <td>2.839996</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-07</th>
      <td>98.680000</td>
      <td>100.129997</td>
      <td>96.430000</td>
      <td>96.449997</td>
      <td>81094400</td>
      <td>94.350769</td>
      <td>0.000000</td>
      <td>3.440003</td>
      <td>4.269997</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-08</th>
      <td>98.550003</td>
      <td>99.110001</td>
      <td>96.760002</td>
      <td>96.959999</td>
      <td>70798000</td>
      <td>94.849671</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>2.660004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-11</th>
      <td>98.970001</td>
      <td>99.059998</td>
      <td>97.339996</td>
      <td>98.529999</td>
      <td>49739400</td>
      <td>96.385500</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>2.099999</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-12</th>
      <td>100.550003</td>
      <td>100.690002</td>
      <td>98.839996</td>
      <td>99.959999</td>
      <td>49154200</td>
      <td>97.784376</td>
      <td>1.630004</td>
      <td>0.000000</td>
      <td>2.160003</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-13</th>
      <td>100.320000</td>
      <td>101.190002</td>
      <td>97.300003</td>
      <td>97.389999</td>
      <td>62439600</td>
      <td>95.270312</td>
      <td>0.000000</td>
      <td>1.539993</td>
      <td>3.889999</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-14</th>
      <td>97.959999</td>
      <td>100.480003</td>
      <td>95.739998</td>
      <td>99.519997</td>
      <td>63170100</td>
      <td>97.353950</td>
      <td>0.000000</td>
      <td>1.560005</td>
      <td>4.740005</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-15</th>
      <td>96.199997</td>
      <td>97.709999</td>
      <td>95.360001</td>
      <td>97.129997</td>
      <td>79010000</td>
      <td>95.015969</td>
      <td>0.000000</td>
      <td>0.379997</td>
      <td>4.159996</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-19</th>
      <td>98.410004</td>
      <td>98.650002</td>
      <td>95.500000</td>
      <td>96.660004</td>
      <td>53087700</td>
      <td>94.556205</td>
      <td>0.940003</td>
      <td>0.000000</td>
      <td>3.150002</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-20</th>
      <td>95.099998</td>
      <td>98.190002</td>
      <td>93.419998</td>
      <td>96.790001</td>
      <td>72334400</td>
      <td>94.683373</td>
      <td>0.000000</td>
      <td>2.080002</td>
      <td>4.770004</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-21</th>
      <td>97.059998</td>
      <td>97.879997</td>
      <td>94.940002</td>
      <td>96.300003</td>
      <td>52161500</td>
      <td>94.204040</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>2.939995</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-22</th>
      <td>98.629997</td>
      <td>101.459999</td>
      <td>98.370003</td>
      <td>101.419998</td>
      <td>65800500</td>
      <td>99.212599</td>
      <td>3.580002</td>
      <td>0.000000</td>
      <td>5.159996</td>
      <td>NaN</td>
      <td>0.473572</td>
      <td>0.824286</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-25</th>
      <td>101.519997</td>
      <td>101.529999</td>
      <td>99.209999</td>
      <td>99.440002</td>
      <td>51794500</td>
      <td>97.275697</td>
      <td>0.070000</td>
      <td>0.000000</td>
      <td>2.320000</td>
      <td>3.471428</td>
      <td>0.444745</td>
      <td>0.765408</td>
      <td>12.811592</td>
      <td>22.048801</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-26</th>
      <td>99.930000</td>
      <td>100.879997</td>
      <td>98.070000</td>
      <td>99.989998</td>
      <td>75077000</td>
      <td>97.813722</td>
      <td>0.000000</td>
      <td>1.139999</td>
      <td>2.809997</td>
      <td>3.424183</td>
      <td>0.412978</td>
      <td>0.792165</td>
      <td>12.060619</td>
      <td>23.134417</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-27</th>
      <td>96.040001</td>
      <td>96.629997</td>
      <td>93.339996</td>
      <td>93.419998</td>
      <td>133369700</td>
      <td>91.386718</td>
      <td>0.000000</td>
      <td>4.730004</td>
      <td>6.650002</td>
      <td>3.654598</td>
      <td>0.383479</td>
      <td>1.073439</td>
      <td>10.493061</td>
      <td>29.372282</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-28</th>
      <td>93.790001</td>
      <td>94.519997</td>
      <td>92.389999</td>
      <td>94.089996</td>
      <td>55678800</td>
      <td>92.042134</td>
      <td>0.000000</td>
      <td>0.949997</td>
      <td>2.129998</td>
      <td>3.545698</td>
      <td>0.356088</td>
      <td>1.064622</td>
      <td>10.042813</td>
      <td>30.025725</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-01-29</th>
      <td>94.790001</td>
      <td>97.339996</td>
      <td>94.349998</td>
      <td>97.339996</td>
      <td>64416500</td>
      <td>95.221398</td>
      <td>2.819999</td>
      <td>0.000000</td>
      <td>3.250000</td>
      <td>3.524577</td>
      <td>0.532082</td>
      <td>0.988577</td>
      <td>15.096322</td>
      <td>28.048110</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-02-01</th>
      <td>96.470001</td>
      <td>96.709999</td>
      <td>95.400002</td>
      <td>96.430000</td>
      <td>40943500</td>
      <td>94.331208</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>1.939994</td>
      <td>3.411393</td>
      <td>0.494076</td>
      <td>0.917965</td>
      <td>14.483109</td>
      <td>26.908794</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-02-02</th>
      <td>95.419998</td>
      <td>96.040001</td>
      <td>94.279999</td>
      <td>94.480003</td>
      <td>37357200</td>
      <td>92.423652</td>
      <td>0.000000</td>
      <td>1.120003</td>
      <td>2.150001</td>
      <td>3.321293</td>
      <td>0.458785</td>
      <td>0.932396</td>
      <td>13.813432</td>
      <td>28.073279</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-02-03</th>
      <td>95.000000</td>
      <td>96.839996</td>
      <td>94.080002</td>
      <td>96.349998</td>
      <td>45964300</td>
      <td>94.252947</td>
      <td>0.799995</td>
      <td>0.000000</td>
      <td>2.759994</td>
      <td>3.281200</td>
      <td>0.483157</td>
      <td>0.865796</td>
      <td>14.725000</td>
      <td>26.386569</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-02-04</th>
      <td>95.860001</td>
      <td>97.330002</td>
      <td>95.190002</td>
      <td>96.599998</td>
      <td>46471700</td>
      <td>95.010279</td>
      <td>0.490006</td>
      <td>0.000000</td>
      <td>2.140000</td>
      <td>3.199686</td>
      <td>0.483646</td>
      <td>0.803954</td>
      <td>15.115420</td>
      <td>25.126015</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-02-05</th>
      <td>96.519997</td>
      <td>96.919998</td>
      <td>93.690002</td>
      <td>94.019997</td>
      <td>46418100</td>
      <td>92.472736</td>
      <td>0.000000</td>
      <td>1.500000</td>
      <td>3.229996</td>
      <td>3.201851</td>
      <td>0.449100</td>
      <td>0.853671</td>
      <td>14.026256</td>
      <td>26.661803</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-02-08</th>
      <td>93.129997</td>
      <td>95.699997</td>
      <td>93.040001</td>
      <td>95.010002</td>
      <td>54021400</td>
      <td>93.446449</td>
      <td>0.000000</td>
      <td>0.650001</td>
      <td>2.659996</td>
      <td>3.163147</td>
      <td>0.417021</td>
      <td>0.839123</td>
      <td>13.183746</td>
      <td>26.528116</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-02-09</th>
      <td>94.290001</td>
      <td>95.940002</td>
      <td>93.930000</td>
      <td>94.989998</td>
      <td>44331200</td>
      <td>93.426774</td>
      <td>0.240005</td>
      <td>0.000000</td>
      <td>2.010002</td>
      <td>3.080780</td>
      <td>0.404377</td>
      <td>0.779186</td>
      <td>13.125809</td>
      <td>25.291844</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-02-10</th>
      <td>95.919998</td>
      <td>96.349998</td>
      <td>94.099998</td>
      <td>94.269997</td>
      <td>42343600</td>
      <td>92.718621</td>
      <td>0.409996</td>
      <td>0.000000</td>
      <td>2.250000</td>
      <td>3.021438</td>
      <td>0.404779</td>
      <td>0.723530</td>
      <td>13.396885</td>
      <td>23.946537</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2016-02-11</th>
      <td>93.790001</td>
      <td>94.720001</td>
      <td>92.589996</td>
      <td>93.699997</td>
      <td>50074700</td>
      <td>92.158002</td>
      <td>0.000000</td>
      <td>1.510002</td>
      <td>2.130005</td>
      <td>2.957764</td>
      <td>0.375866</td>
      <td>0.779706</td>
      <td>12.707768</td>
      <td>26.361342</td>
      <td>33.002804</td>
    </tr>
    <tr>
      <th>2016-02-12</th>
      <td>94.190002</td>
      <td>94.500000</td>
      <td>93.010002</td>
      <td>93.989998</td>
      <td>40351400</td>
      <td>92.443230</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>1.489998</td>
      <td>2.852924</td>
      <td>0.349018</td>
      <td>0.724013</td>
      <td>12.233704</td>
      <td>25.377932</td>
      <td>33.141692</td>
    </tr>
    <tr>
      <th>2016-02-16</th>
      <td>95.019997</td>
      <td>96.849998</td>
      <td>94.610001</td>
      <td>96.639999</td>
      <td>49057900</td>
      <td>95.049622</td>
      <td>2.349998</td>
      <td>0.000000</td>
      <td>2.860000</td>
      <td>2.853429</td>
      <td>0.491945</td>
      <td>0.672298</td>
      <td>17.240497</td>
      <td>23.561048</td>
      <td>31.880925</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Finally we can now plot the ADX, +DMI, -DMI and the stock price!</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[8]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>   <span class="c1"># Import matplotlib</span>
<span class="c1"># This line is necessary for the plot to appear in a Jupyter notebook</span>
<span class="o">%</span><span class="k">matplotlib</span> inline
<span class="c1"># Control the default size of figures in this Jupyter notebook</span>
<span class="o">%</span><span class="k">pylab</span> inline
<span class="n">pylab</span><span class="o">.</span><span class="n">rcParams</span><span class="p">[</span><span class="s1">&#39;figure.figsize&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="p">(</span><span class="mi">15</span><span class="p">,</span> <span class="mi">9</span><span class="p">)</span>   <span class="c1"># Change the size of plots</span>


<span class="n">apple</span><span class="p">[</span><span class="s2">&quot;Adj Close&quot;</span><span class="p">]</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">grid</span> <span class="o">=</span> <span class="kc">True</span><span class="p">)</span>
<span class="n">apple</span><span class="p">[[</span><span class="s2">&quot;ADX&quot;</span><span class="p">,</span><span class="s2">&quot;+DMI&quot;</span><span class="p">,</span> <span class="s2">&quot;-DMI&quot;</span><span class="p">]]</span><span class="o">.</span><span class="n">plot</span><span class="p">(</span><span class="n">grid</span> <span class="o">=</span> <span class="kc">True</span><span class="p">)</span> <span class="c1"># Plot the adjusted closing price of AAPL</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

</div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area"><div class="prompt"></div>
<div class="output_subarea output_stream output_stdout output_text">
<pre>Populating the interactive namespace from numpy and matplotlib
</pre>
</div>
</div>

<div class="output_area"><div class="prompt"></div>


<div class="output_png output_subarea ">
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAABL4AAALZCAYAAAC5w+jUAAAABHNCSVQICAgIfAhkiAAAAAlwSFlz
AAAPYQAAD2EBqD+naQAAIABJREFUeJzs3Xl8VPX1//H3xbAqIDu4IKBsKgIJq/sGWpW4b1VbQWtd
0NYFq61Wbb9Vcam2bnXBXUHFCoiICFgRWgUSEYEAKoKiJhJZE2QJub8/PswvCcwks9w7d+Z+Xs/H
g8c1M3funJHDhZycz/k4rusKAAAAAAAACJt6QQcAAAAAAAAA+IHCFwAAAAAAAEKJwhcAAAAAAABC
icIXAAAAAAAAQonCFwAAAAAAAEKJwhcAAAAAAABCicIXAAAAAAAAQonCFwAAAAAAAEKJwhcAAAAA
AABCicIXAAAAAAAAQinhwpfjOEc5jjPJcZzvHMepdBwnv9pzOY7jjHYcZ6HjOGU7z3nBcZwOu1yj
oeM4jzmOU+o4zibHccY7jtPWiw8EAAAAAAAASMl1fO0paYGkqyW5uzzXRFIfSXdJ6ivpTEndJU3c
5byHJZ0q6WxJR0vaR9KbScQCAAAAAAAAROW47q61qwRe7DiVks5wXXdSLef0k/SJpANc113tOE4z
SWskXeC67ls7z+kuqUjSINd15yYdEAAAAAAAALBTOmZ87S3TGbZ+59d5knIkzYic4LruMknfSBqc
hngAAAAAAABgAV8LX47jNJR0r6RXXdct2/lwe0nbXNfduMvpJTufAwAAAAAAAFKW49eFHcfJkfSG
TLfX1Sleq5WkkyStlLQl5eAAAAAAAACQzRpJ6iTpPdd1f4p1ki+Fr2pFr/0lHV+t20uSiiU1cByn
2S5dX+12PhfNSZJe8SNWAAAAAAAAZK2LJL0a60nPC1/Vil5dJB3nuu66XU4pkFQh6QRJ1Yfbd5T0
vxiXXSlJL7/8snr27Ol1yNY755xzNH78+KDDAHxFnsM25DxsQ87DNuQ8bEPOY1dFRUW6+OKLpZ01
o1gSLnw5jrOnpIMkOTsf6uI4Tm9JayX9IOlNSX0knSapvuM47Xaet9Z13e2u6250HGeMpL87jrNO
0iZJ/5Q0p5YdHbdIUs+ePZWbm5toyKhD/fr1+f+K0CPPYRtyHrYh52Ebch62IedRi1pHYiXT8dVP
0gcys7tcSQ/ufPwFSXdJGrbz8QU7H3d2fn2cpFk7H7te0g5J4yU1lDRV0jVJxAIPdO/ePegQAN+R
57ANOQ/bkPOwDTkP25DzdnJdaf58qX//5K+RcOHLdd0PVftukHXuFOm67lZJ1+78BQAAAAAAANQw
Y4Y0ZIg0c6Z03HHJXaPOIhUAAAAAAACQblOnmuPYsclfg8IXdNpppwUdAuA78hy2IedhG3IetiHn
YRty3k7vvy/l5Ehvvilt25bcNSh8QZMnTw46BMB35DlsQ87DNuQ8bEPOwzbkvH1KSqSFC6Xrr5fW
rpWmT0/uOhS+oDvvvDPoEADfkeewDTkP25DzsA05D9uQ8/aZMcMcb7hB6tlTGjcuuetQ+AJbwsIK
5DlsQ87DNuQ8bEPOwzbkvH3ef1/q1Utq31664AJpwgTp558Tvw6FLwAAAAAAAGQM1zWFryFDzNcX
XCBt2iS9+27i16LwBQAAAAAAgIyxdKn03XdVha9u3aTc3OR2d6TwBY0ZMyboEADfkeewDTkP25Dz
sA05D9uQ83Z5/32pQQPp6KOrHrvgAmnyZNP5lQgKX1BhYWHQIQC+I89hG3IetiHnYRtyHrYh5+0y
fbp0xBFSkyZVj11wgVRRId1yS2LXclzX9TY6HziOkyupoKCggIF2AAAAAAAAIbV9u9SqlXTrreZX
dU89Jf32t9K//iX171+ovLw8ScpzXTdmZTTH33ABAAAAAACA+Dz3nFnOeOKJuz93xRXSwoXSyJHS
E0/Edz0KXwAAAAAAAAjUunWmoPXqq9JFF0mmmWt3Dz0kLVkijRoV33WZ8QUAAAAAAIDALF4sHXaY
9M470iuvSC+9JNWLUbGqX1964w1p773juzaFLyg/Pz/oEADfkeewDTkP25DzsA05D9uQ8+F2881S
o0ZmGeMvfyk5Tu3nt2olvfZafNdmqSM0cuTIoEMAfEeewzbkPGxDzsM25DxsQ86H14IF0pQppsur
Y8f4X5cTZ0WLXR0BAAAAAAAQiPPPl+bNk5Yvj7+YJUmFhezqCAAAAAAAgAy1bJmZ1/XEE4kVvRLB
jC8AAAAAAACk3ejRUvv20qWX+vceFL6gCRMmBB0C4DvyHLYh52Ebch62IedhG3I+fFatMnO9brpJ
atjQv/eh8AWNHTs26BAA35HnsA05D9uQ87ANOQ/bkPPh88ADUvPm0hVX+Ps+DLcHAAAAAABA2pSU
SJ06SX/8o3T77cldI97h9nR8AQAAAAAAIG0eekiqX18aOdL/96LwBQAAAAAAgLRYt056/HHp6qul
Fi38fz8KXwAAAAAAAEiLRx+Vtm+Xrr8+Pe9H4QsaPnx40CEAviPPYRtyHrYh52Ebch62IefDoaxM
evhh6fLLpXbt0vOeFL6goUOHBh0C4DvyHLYh52Ebch62IedhG3I+HJ56Stq4URo1Kn3vya6OAAAA
AAAA8NXWrVLnztLJJ0vPPpv69djVEQAAAAAAABnh+eel4mLpD39I7/tS+AIAAAAAAIBvKiqk0aOl
c8+VundP73tT+IJmz54ddAiA78hz2Iach23IediGnIdtyPnsNm6c9PXX0q23pv+9KXxB9913X9Ah
AL4jz2Ebch62IedhG3IetiHns1dlpXTPPdIpp0h9+qT//RluD23evFlNmjQJOgzAV+Q5bEPOwzbk
PGxDzsM25Hz2eust6ayzpDlzpMMP9+66DLdH3Lh5wAbkOWxDzsM25DxsQ87DNuR89nrmGemII7wt
eiWCwhcAAAAAAAB8sXy5NGhQcO9P4QsAAAAAAACe27FDWrVK6tIluBgofEGjRo0KOgTAd+Q5bEPO
wzbkPGxDzsM25Hx2+u47aft2Cl8IWMeOHYMOAfAdeQ7bkPOwDTkP25Dz8ZkyRdq4Mego4AVyPjut
WGGOnTsHFwO7OgIAAAAAQmfVKqlTJzNY+7LLgo4GsNOzz0qXXy5t3iw1auTttdnVEQAAAABgrXff
Nce1a4ONA7DZihXSvvt6X/RKBIUvAAAAAEDoTJlijuvWBRsHYLMVK4Kd7yVR+IKkpUuXBh0C4Dvy
HLYh52Ebch62Iedrt2WLNGOG+W8KX+FAzmcnCl/ICDfffHPQIQC+I89hG3IetiHnYRtyvnazZpmZ
Qu3aSevXBx0NvEDOZ6dMKHzlBPv2yASPPvpo0CEAviPPYRtyHrYh52Ebcr52U6ZI++0n9e9Px1dY
kPPZZ9Mmac2a4AtfdHyBbWFhBfIctiHnYRtyHrYh52v37rvSKadILVpQ+AoLcj41c+ZIn36a3vf8
+mtzpPAFAAAAAIBHvvxSWr68qvDFUkfYbupU6bjjpEsvTe/7rlhhjhS+AAAAAADwyLvvSvXrSyec
QMcXMGeOdNZZUqdO0sKF0pIl6XvvFSukJk2ktm3T957RUPiCRo8eHXQIgO/Ic9iGnIdtyHnYhpyP
bcoU6ZhjpL32kvbe2xS+XDfoqJAqcj5xn30mnXqqNGCANHeu1Ly5NG5c+t4/MtjecdL3ntFQ+II2
b94cdAiA78hz2Iach23Iedgm03N+5kzpk0/Sv8ywrEz64AOzzFEyHV8VFWaHR2S3TM95r23fLt17
ryniJvPRv/hCOukk6aCDpEmTTBH4rLNM4StdheBM2NFRkhw3C0rfjuPkSiooKChQbm5u0OEAAAAA
AGL4/HPpsMOqvm7XTurRQ+revebxgAOkPfbw9r0ffFC65RYz5+uAA6qG3H/7rdnlEcgG8+ZJv/mN
6diSTDH32GPjf/1330lHHCE1bizNmiW1aWMenzbNFMMKCqR0lFZ69JBOPll6+GF/rl9YWKi8vDxJ
ynNdtzDWeXR8AQAAAAA88/77UqNGpuPr1Vel3/5Wat/eLLX605/M0qsDD5T23FPKz5dmz/amA2Xz
Zun++6Vf/9oUvSTT5SIx5wvZY/x4adAgqV4982emaVPpf/+L//WlpdKQIebP1LRpVUUvSTr+eKl1
a2nsWO/j3lVlpbRyZWZ0fOUEHQAAAAAAIDymT5eOPtrMFRowoOZzlZXS6tXSsmXSokXSM89IRx0l
DR4s/f3v5hv+ZD31lPmm/49/rHqsRQtzZGdHZIPNm6Xrr5dOO016800pJ0caODD+wtemTabD8aef
pI8+kvbfv+bzOTnSuedKr70mjR5timt++eEHaevWzCh80fEFlZaWBh0C4DvyHLYh52Ebch62ydSc
37ZN+vBD6cQToz9fr57UsaPpSLn+erMscvJkqbxcuuAC8/pk/Pyz+Ub+kktqfqMdKXzR8ZX9MjXn
vfTww1JJiVmym7OzTWnwYFP4qqsrcssW6fTTTVH5vfekbt2in3fhhWbpbyJdZMlYscIcKXwhI4wY
MSLoEADfkeewDTkP25DzsE0m5LzrShs21Hzsf/8zXSuxCl+7qlfPLH185RVp1SrppZeSi+WZZ6Q1
a8xSyupY6hgemZDzfiopke65R7rmGjOQPuLww00n45dfxn5tRYUpHH/8sfTOO1KfPrHPPeIIad99
zeD86dPN+/ox+j1S+OrUyftrJ4rCF3TnnXcGHQLgO/IctiHnYRtyHrbJhJx//30zuP6LL6oemz5d
atVK6t07sWsdeqh0zjnS3/5mdrNLxJYt5pv4iy6qWTCQpIYNzYBvljpmv0zIeT/ddZfp8rrttpqP
DxxojrE6tCorpcsvNwWv8eOlI4+s/X3q1TPLgadPN52X7dubo9dWrJA6dJCaNPH+2omi8AV2yoQV
yHPYhpyHbch52CYTcn7uXDPD5957qx6bPl064YTkZgfdfrv09dfSyy8n9rpnn5WKi3fv9opo0YKO
rzDIhJz3S1GRmVF3222mcFxdixZSz57RC1+uK91wg/Tii6Zb8pRT4nu/q6+Wysqk5culUaOkmTPN
cmMvrViRGcscJQpfAAAAAIAkLF4sOY75pvubb8yyx7lz41/muKvDDpPOPNN0fVVUxPearVvN8rAL
L4w902jvvSl8IXNt3Vq1E+nIkdHPOfxw6b//3f3xv/5V+sc/pMcfN0sdE7HHHlLXruZ1ristXJh4
7LX56iupc2dvr5ksCl8AAAAAgIQtXiz98pdSs2bS/fdL//mPWXaVbOFLkv78Z/MNc7yzvp57Tvru
u9jdXpLpmGGpIzLVDTdIn31mdlps2DD6OYMHm11QN22qeuyRR6Q77pDuvlu68srk3/+QQ8wSywUL
kr/GrjZtkubP331X16BQ+ILGjBkTdAiA78hz2Iach23Iedgm6JyvqDC7xw0cKP3ud2a4/CuvSAce
mFqXR58+0llnSSNGSEcdZTpZfvop+rnbtplur/PPN0vBYmGpYzgEnfN+eOUVk+P//KfUr1/s8wYP
NkXluXPN1+++K113nXTTTdItt6QWQ8OG0sEHS59+mtp1qps+3czqO/VU766ZCgpfUGFhYdAhAL4j
z2Ebch62Iedhm6Bz/quvTOHp4IOla6+V6teX3ngjtW6viJdekl54QWra1HxzP3CgtGPH7ue98IL0
7be7DwPfFUsdwyHonPfaokXSFVdIl1xijrXp0cPk8f/+J61ebV5z6qnS6NFmuXGq+vTxtuNryhSp
e/fMmfHluH7sW+kxx3FyJRUUFBSEeqAdAAAAAGSDt94ynVk//GB2hbvlFvNN+BtvmN0ZvfLf/0pH
HCFNnSqddFLV49u3m5le/ftLr79e+zWuu0764APp88+9iwtIxcaNJncbNpQ+/ji+nQ9/8QvT9VVe
Lq1aZQpVuw7CT9bDD0u33mqWKObkpHYt15X228/MDnvwQW/ii6WwsFB5eXmSlOe6bszKaIofCQAA
AABgm8WLpZYtpXbtzNejRpld4k4+2dv3GTzYLGN8/vmaha+XXpJWrpQmTar7GnR8IZO4rnTZZaZo
PH9+fEUvyfxZuOMOM5R+1izvil6S6fjassUsXz7kkNSutWCB9P33mbPMUWKpIwAAAAAgQYsXm2WO
kWVWrVpJjz4q7bWXt+/jONLw4abDLDKgfvt2s/PjWWdJvXrVfQ1mfCGT/OMf0vjxppgbayfSaI48
0hzvvtvs8uil3r3N0Yvlju+8Y5YpR+LNBBS+AAAAAAAJWbIk9c6QeF18sSl2jRtnvn71VWnFCrMD
ZDxatJA2bzYzyYAgzZljuiNvvNEUbhNx3HFm59SbbvI+rhYtpE6dvBlwP2WKNGSI1KBB6tfyCoUv
KD8/P+gQAN+R57ANOQ/bkPOwTZA5X1EhLV2avsJXhw5mCeXzz5v3/r//k844o6pLpS57722OkY4x
ZKdsv8+XlEjnnScNGmR2I02U40jHHCPV86mKk8yA+9JS6amnTCE68vXHH2fWMkeJGV+QNHLkyKBD
AHxHnsM25DxsQ87DNkHm/IoVVTs6psvw4dK555oZR19+Kb32WvyvbdHCHNetk9q29Sc++C+b7/MV
FdKFF5rdSV97zeyCmmn69jXLMF237p0iv/9eeuAB6cknTTdls2bSs89KP/9sXn/KKemJOV50fEFD
hw4NOgTAd+Q5bEPOwzbkPGwTZM4vXmyO6er4kqRhw0wB6+67zX/n5sb/2kjhi46v7JbN9/k//1n6
8EOzXHeffYKOJro+faS1a6XVq2Ofs2KFdOWVUufO0nPPmSWbX30lDR1qdnMdNUrKyzM7vWYSCl8A
AAAAgLjtuqNjOjRsKP3yl+a/453tFRFZ6siAewTh7bfN0sZ77pGOPTboaGLr29cco835WrxYuuQS
M4z/3/+W7rpLWrVK+stfpC5dpNdflx55xBTOzjwzvXHHg6WOAAAAAIC4LVlSc0fHdLn9dumoo6R+
/RJ7XfWljkA6vfWWKdiecYbphspk++1nCtoLFkiRcWrz55suy7fekvbfX3roIemyy6QmTWq+1nGk
kSOl88+v+vOWSej4giZMmBB0CIDvyHPYhpyHbch52CbInF+8OL3LHCPatTPfWCdqr72kPfZgqWO2
y7b7/MMPS2efbYpIY8emv1CcKMcxXV+ffirNmiWddJLUv7+0aJE0ZoyZrXfttbsXvapr00bKycD2
Kgpf0NixY4MOAfAdeQ7bkPOwDTkP2wSV8xUV0rJlwRS+kuU4ZrkjHV/ZLZvu87feKl1/venyGjtW
atQo6Iji06ePNHGi2T3yhx9M7EVF0ogRUoMGQUeXPMd13aBjqJPjOLmSCgoKCpSbyBRDAAAAAIBn
li+XuneXpk+XTjgh6Gji17WrmT10331BR4KwW79eatVKuu02Mwsrm8ydK/31r9IVV0innZb5XWqF
hYXKy8uTpDzXdQtjnZeBTWgAAAAAgEwUxI6OXmjRgo4vpMfMmVJlpTR8eNCRJG7AADOMP2xY6ggA
AAAAqFNFhXTvvVKPHund0dELLHVEukybZnY/7NQp6EgQQccXAAAAAKBO99xjdnmbMyfzl0DtqkUL
6aefgo4CYee60nvvmWWCyBx0fEHDs7EHE0gQeQ7bkPOwDTkP26Q75+fPl/7yF+mPf5QGDUrrW3uC
pY7ZLxvu8199Ja1cKQ0dGnQkqI7CFzSUP5WwAHkO25DzsA05D9ukM+d//lm65BKpd2/pz39O29t6
iqWO2S8b7vPTpkk5OdKxxwYdCapjV0cAAAAAQEz33GN2p/v0U6lnz6CjSc7o0ebX2rVBR4IwO+MM
U2D98MOgI7FDvLs60vEFAAAAAIjpnXekU0/N3qKXZDq+1q83u+0Bfti+3ezomAWNadah8AUAAAAA
iKqsTPrkE+mEE4KOJDUtWpjB4xs3Bh0JwmruXGnTJgpfmSjhwpfjOEc5jjPJcZzvHMepdBwnf5fn
z3Qc5z3HcUp3Pn9YlGv8Z+dzkV87HMd5PJUPguTNnj076BAA35HnsA05D9uQ87BNunL+o4+kiopw
FL4k0/WF7JTp9/lp06SWLSWmM2WeZDq+9pS0QNLVkqINCNtT0keSbo7xvHY+/pSkdpLaS+qw83wE
4L777gs6BMB35DlsQ87DNuQ8bJOunJ8xQ9p3X6lbt7S8nW/23tscGXCfvTLxPr9okSkOf/SRNGmS
dOKJ0h57BB0VdpWT6Atc150qaaokOY7jRHn+5Z3PHSBpt+er2ey67ppE3x/eGzduXNAhAL4jz2Eb
ch62Iedhm3Tl/IwZpttr9+/8skuk44vCV/bKtPv8Dz9IvXrVfOyGG4KJBbULcsbXRY7jrHEc53PH
ce52HKdxgLFYrUmTJkGHAPiOPIdtyHnYhpyHbdKR86Wl0oIF0vHH+/5WvmOpY/bLtPv8N9+Y46RJ
0rJl0ldfSRdfHGxMiC7hji+PvCJplaTvJR0m6T5J3SSdE1A8AAAAAIBqPvjAHLN9vpckNW9ujnR8
wSslJeY4YIDUrl2wsaB2gRS+XNd9ptqXix3H+UHSDMdxOruu+3UQMQEAAAAIv8mTpWOOkZo2DTqS
zDdzppnttd9+QUeSupwc83u+dm3QkSAsSkqkevWk1q2DjgR1CXKpY3VzZeaBHVTbSaeccory8/Nr
/Bo8eLAmTJhQ47xp06YpPz9/t9dfc801GjNmTI3HCgsLlZ+fr9LS0hqP33HHHRo9enSNx7755hvl
5+dr6dKlNR5/5JFHNGrUqBqPbd68Wfn5+bvtPDF27FgNHz58t9jOP//8wD5HJPZs/xwRfA4+R7TP
cdBBB4Xic4Tl94PP4f/nOOig3f9KzcbPEZbfDz6H/5/j0EMPDcXnCMvvR6Z+joceekTDho3SY49l
9+d45JFH1L9//xqP+fE5IvO9wpJXOTnX6N13s/9zhOX3I9HPcfTRR2fU5yguNkWv666z8/cj3Z/j
xhtv3K0WNGTIkN3OjcZx3VgbL8bxYseplHSG67qTojx3gKQVkvq6rruwjuscIWmWpN6u6y6K8nyu
pIKCggLlsjeo5x555BFde+21QYcB+Io8h23IediGnEc8fvrJfKN6wgnS9OlBR5Mav3P+22+ljh2l
8eOls8/27W3S6pxzzIyvbP+9t1Wm3edHjjS7OX72WdCR2KuwsFB5eXmSlOe6bmGs8xIufDmOs6dM
Z5YjqVDSDZI+kLTWdd1vHcdpIamjpH0lTZZ0gaRlkopd1y1xHKeLpF9KmiLpJ0m9Jf1d0jeu60Yd
m0jhCwAAAECqvvlGOuAAqWFDM+upMdtrxfT889KIEdKaNVKrVkFH443bbjOfa/XqoCNBGJx7rrRh
gzRtWtCR2CvewlcySx37SfpUUoEkV9KDMgWwu3Y+n7/z+bd3Pj925/O/3fn8NkknSnpPUpGk+yW9
sfN1AAAAAOCLsjJz3LpVmjMn2Fgy3cyZUp8+4Sl6SVKPHtJ330mbNgUdCcKguJih9tki4eH2rut+
qFoKZq7rviDphVqeXy3p2ETfFwAAAABSESl8OY5Z7nbiicHGk6lc18z3+uUvg47EWz16mOOyZVK/
fsHGguxXUiINGhR0FIhHpgy3R4B2HT4HhBF5DtuQ87ANOY94lJeb46BB2T/nyc+cX7ZM+v57Mwst
TLp3N0duF9kp0+7zJSV0fGULCl/QzTffHHQIgO/Ic9iGnIdtyHnEI9LxdfrpUmGhGXafrfzM+Rkz
pPr1paOO8u0tAtG0qbTPPhS+slUm3ed//lnauJHCV7ag8AU9+uijQYcA+I48h23IediGnEc8Ih1f
p59ulvPNnBlsPKnwM+dnzDBdcXvu6dtbBKZHD9PRhuyTSff5khJzbN8+2DgQHwpfUMeOHYMOAfAd
eQ7bkPOwDTmPeJSVmfle3bqZZW/ZvNzRr5zfsUP6z3+k44/35fKB69GDjq9slUn3+Ujhi46v7EDh
CwAAAIAVysqkJk2kevWkIUOyu/DllwULpHXrwjffK6JHD2n5clPgA5JVXGyOFL6yA4UvAAAAAFYo
L5f22sv894knSitWmF+oMmOGKQ4OHBh0JP7o0UPatk1auTLoSJDNSkpMAb1166AjQTwofEGjR48O
OgTAd+Q5bEPOwzbkPOJRVlY1t+rYY803ru+/H2hISfMr52fMkI4+WmrQwJfLB65HD3NkuWP2yaT7
fHGx1KaNtMceQUeCeFD4gjZv3hx0CIDvyHPYhpyHbch5xKOsrKrjq3lzs5zv5ZeDjSlZfuT81q3S
Rx+Fd5mjJO27ryl+UvjKPpl0ny8pYZljNnFc1w06hjo5jpMrqaCgoEC5ublBhwMAAAAgC40YYXb0
mzPHfP3aa9IFF0hFRVWdQDabNUs65hipsFDq2zfoaPyTlyfl5kpPPx10JMhW55wjbdokvfde0JHY
rbCwUHl5eZKU57puYazz6PgCAAAAYIXqSx0l6YwzpJYtpWefDS6mTDJjhvn/0bt30JH4i50dkari
Yjq+sgmFLwAAAABWqL7UUZIaNpQuvlh64QVp+/bg4soUM2ZIxx1nZp+FGYUvpIqljtkl5Lc0xKO0
tDToEADfkeewDTkP25DziEf1XR0jLrtM+vFH6Z13kr/u1q3S5MmpxZYor3O+rEz65JNwz/eK6NFD
Ki01v5A9Muk+X1IitW8fdBSIF4UvaMSIEUGHAPiOPIdtyHnYhpxHPHZd6ihJhx0m9e8vPfNM8td9
4w1p2DDzzXC6eJ3zs2ZJFRX2FL4kM+8N2SNT7vObN5v5XnR8ZQ8KX9Cdd94ZdAiA78hz2Iach23I
ecQjWseXZLq+3n1X+u675K67eLE5/vBD8rElyuucnzlT2m8/qWtXTy+bkbp2lRyHwle28fs+P3as
NHSoKWzVJlLgpvCVPSh8gZ0yYQXyHLYh52Ebch7xiNbxJZmdHRs2NLO+klFUZI7p7PjyOudnzJCO
P94UhMKuUSOpc2dpyZKgI0Ei/L7Pz5olvf++dMUVkuvGPi/y55yljtmDwhcAAAAAK+w63D6ieXPp
3HPN7o6VlYlfN1JAKS5OLb6glJZKCxbYscwxIi9Pmjs36CiQSYqLpdatpVdekf7xj9rPk+j4yiYU
vgAAAAANv3JgAAAgAElEQVSEnuvGXuooSZdfLn31len6SMTWreZ1Uno7vrz0wQfmaFPh6/DDpXnz
pG3bgo4EmaK4WDrtNOmmm8yv//wn+nklJWbn01at0hoeUkDhCxozZkzQIQC+I89hG3IetiHnUZdt
28zw9mhLHSXpyCOlbt0SH3K/fHlVl1g6C19e5vyMGVL37tK++3p2yYx3+OHSli3Sp58GHQni5fd9
vrjYLF+85x7p2GOl886Tvv129/NKSqS2baU99vA1HHiIwhdUWFgYdAiA78hz2Iach23IedSlrMwc
Y3V8OY40YoT05pvS+vXxXzcy3+uQQ9Jb+PIy52fOtKvbS5L69pUaN5b++9+gI0G8/LzPu25V4Ssn
Rxo3TmrSRDrrLFMgra64mGWO2YbCF/TYY48FHQLgO/IctiHnYRtyHnUpLzfHWIUvSfr1r6Xt26VX
X43/ukuWmO6Pgw9O74wvr3L+22+lL76wr/BVv77Uv780Z07QkSBeft7nN240Ba7IwPrWraV//1ta
tEi6+uqaw+5LSih8ZRsKXwAAAABCL9LxFWupo2S+6T31VCmRFVVFRVLPnua12Tjja8YM0+127LFB
R5J+hx9uCl+17eAHO0SK1h06VD2Wmys99ZT03HPSv/5V9XhJCTs6ZhsKXwAAAABCL56OL8kMuS8s
jH/205IlpvDVrl32Fr769pVatgw6kvQ74ghT8Fi1KuhIELRI4WvXgtYll0jXXitdd11VdyBLHbMP
hS8AAAAAoRdPx5ck/eIXpusjnq6vigoz3P7gg803wqWl5rFs8eqr5teZZwYdSTAGDTJH5nwhVuFL
kh58UBo8WDrnHOn771nqmI0ofEH5+flBhwD4jjyHbch52IacR13qGm4fkZNjZn298or088+1n/v1
12a3yEjHl+ua4lcqFi2Sli6t+7xUc/7FF003y69+Jd16a0qXylqtW5vdLJnzlR38vM8XF5vNDpo2
3f25+vWlN94wuziefrq5l7DUMbtQ+IJGjhwZdAiA78hz2Iach23IedQl3qWOktndcf166a23aj9v
yRJzjHR8SakPuL/iCunmm+s+L5Wcf/556dJLzeccM8Z8Q2+rI46g4ytb+Hmfj+zo6DjRn2/Xzgy7
X7iw6mtkDwpf0NChQ4MOAfAdeQ7bkPOwDTmPukQ6vho3rvvcrl2lY46pe7ljUZHUrJlZGhnpAEll
ztf27Wa22Hff1X1usjm/Y4eZWXTxxdKTT0r1LP+O8PDDTTFj06agI0Fd/LzP//BD3V1cAwZIjz9u
imNduvgWCnxg+W0OAAAAgA3Kysx8r3gLPZddJs2cKX31Vexzliwx3V6OI7Vtax5LpfC1ZIm0ZYv5
JtwvRUXm/8Vll1H0kkzhq7JS+uSToCNBkCIdX3W57DJpzRoKX9mGWx0AAACA0Csvj2+ZY8TZZ5tu
rueei31OUZGZ7yVJjRpJzZunVvgqKDDHkhLTmeWHefNMoS4315/rZ5vu3aUWLczulq4bdDQISryF
L0lq1crfWOA9Cl/QhAkTgg4B8B15DtuQ87ANOY+6RDq+4tWkifTLX5p5WNGKUJWVpvB18MFVj7Vr
l9qMr/nzq669Zk3t5yab8/PmST16RB/ibaN69aRhw6R77zW/l3/5i9mpE5nHz/t8IoUvZB8KX9DY
sWODDgHwHXkO25DzsA05j7ok2vElmWVN330nvffe7s+tXm2uGen4kkzhK9WOr8j16lrumGzOz58v
9e+f1EtD65lnpClTzP+X++83XWB5edIDD0jffht0dIjw6z6/Y4cpNFP4Ci/HzYJ+TsdxciUVFBQU
KJeeXAAAAAAJGjFCWro0sR38XFfq21f68UdTkGre3Cxz2n9/Mwz9gQekFSukzp3N+eedJ61bJ73/
fuLxbd9uurCuu84UX955RzrllMSvU5tt28x7PPigxEao0f38symCjR0rTZ4sbd0qHXmkdOGF0rnn
Sm3aBB0hvFZcbDaomDTJdP8hexQWFiovL0+S8lzXLYx1Hh1fAAAAAEKvrCzxji/HkR55xHwz3KaN
KYosWGB2dnvgAfPYAQdUnZ9Kx9fixabIcuqp5n39GHC/cKEpfvXr5/21w6JxYzPfbfx4U/B84YWq
guQhhzAHLIwiy5Pp+AqvnKADAAAAAAC/JbPUUZKOOsr82tWWLWYWV/WdEVMpfM2fb67Vr5/UurU/
ha9586ScHKlPH++vHUbNmkm/+pX59fLL0iWXmE6/Zs2CjgxeovAVfnR8AQAAAAi9RIfb16VRIzMA
v7p27cysoIqKxK8Xme+1555m2ZUfha/586VevUzsSMw++5hjXZsOIPtECl9t2wYbB/xD4QsaPnx4
0CEAviPPYRtyHrYh51GXZJY6JqpdO7MUrrQ08dfOn1+1BDGewlcyOT9vHoPtkxWZ7fXjj8HGYTO/
7vPFxVLLllLDhr5cHhmAwhc0dOjQoEMAfEeewzbkPGxDzqMuyS51TERkqVSiyx23bTPzt8yM5vgK
X4nmfHm5mSNG4Ss5kW4gOr6C49d9vriYZY5hR+ELuvDCC4MOAfAdeQ7bkPOwDTmPuni91DGadu3M
MdHC16JFNYfOx1P4SjTnP/3UzCRjsH1yWrUyRzq+guPXff6HHyh8hR2FLwAAAAChl66ljlLVzKB4
FRSYwfa9e5uvI4UvL3cQnD/fzPY65BDvrmmTnBxT/KLwFT50fIUfhS8AAAAAoea6Zqmf3x1fjRqZ
Hf8S7fiaP98UpCLD8jt0MB1ga9d6F9u8eVLfvlL9+t5d0zZt27LUMYwofIUfhS9o9uzZQYcA+I48
h23IediGnEdttm0zOy363fElma6vRApfGzZI771Xcwlihw7mWH25Y1mZtHx51deJ5Hx5ufTxx8z3
SlWbNnR8Bcmv+zyFr/Cj8AXdd999QYcA+I48h23IediGnEdtysvNMdMKXzt2SBdeaIpft9xS9Xi0
wtdf/2q6wiZNMl/XlfOuKz3zjDR0qNmxbsUK6Re/SOCDYDd0fAXLj/v85s3Sxo1Vf+YQThS+oHHj
xgUdAuA78hy2IedhG3IetSkrM0e/lzpKpnMk3sLXH/5gur1ee03q1q3q8WiFr48/lhxHOuccacqU
unN+1izpN78xxbX77jPdYiefnOCHQQ1t29LxFSQ/7vORP6t0fIVbTtABIHhNIsMEgBAjz2Ebch62
IedRm0jhK10dX8uW1X5OZaX09NPSgw9KDz9surKqa9xYat68qvBVWWl2Zfzzn82srrPOkiZNarLb
66p7+WWpUydp+nRTMEPqWOoYLD/u85GNKCh8hRsdXwAAAABCLROWOu7YIX34oXTttdL++0tXXmk6
sq67Lvp1Ijs7StIXX0ibNkmDBkmvvy6dcIJ0+unSzJnRX7tli/TGG9LFF1P08lJkqaOXu20iWBS+
7EDhCwAAAECopXOpY7t2UmmpKXRVVEgzZkhXXSXts4907LHShAnSueeapYhPPhm7MLXPPlWFr4IC
c8zNlRo2lN58Uzr6aGnYMHOdXU2ebOaGXXyxLx/RWm3amN/T9euDjgReKS6WcnLMHDyEF4UvaNSo
UUGHAPiOPIdtyHnYhpxHbdK91LGyUrrkEtNFcuKJ0tSp0q9+ZeZ0rVplljcedVTt3VjVO74KCqTO
nau+OW/USDr44FEaPFg65RRpzpyar335ZbODY/fu/nxGW7Vta44sdwyGH/f54mLzZ7YelZFQ47cX
6tixY9AhAL4jz2Ebch62IedRm8hSx3R0fEWG1M+bJ11xhTR/vtlR8f77pYED4/8Ge9fCV15ezee7
dOmoSZOkfv3Mbo0ff2we/+knM/yebi/vRQpf7OwYDD/u899/zzJHGzDcHrr22muDDgHwHXkO25Dz
sA05j9pEOr7SsQdCz56m+NSiRWrztSKFr8pKqbBQ+uMfaz4fyfnJk03h66STzLLK+fPNay64IIUP
gajatDFHOr6C4cd9/osvpIMO8vyyyDAUvgAAAACEWnm56fZK13ImL+YFdehg4l6wwAy237XjK2Kv
vUyH19Ch0pAhZtnWSSdVdSfBOy1bmhyi4ys8iorM7D2EG0sdAQAAAIRaWVl6ljl6qUMHc5w82Rxz
c2Of27SpmSN20EHSsmUsc/RLvXpS69Z0fIXF2rXm97Jnz6Ajgd8ofEFLly4NOgTAd+Q5bEPOwzbk
PGpTVpaewfZeql74OuAAqVWrms/vmvPNm0vTpkmPPCKdfXaagrRQ27YUvoLi9X0+cjkKX+FH4Qu6
+eabgw4B8B15DtuQ87ANOY/alJdnb+Fr3rzoyxyj5XyLFtLIkVKDBj4HZ7G2bVnqKEk7dkhff133
ea7r3Xt6fZ8vKjJz+Lp29fSyyEAUvqBHH3006BAA35HnsA05D9uQ86hNNi51bNq0ahh/tMIXOR+M
Nm3s7vgqKZHuuccsq+3Sxew4GsumTea8fv2kF16QtmxJ7b29zvmlS6XOnaXGjT29LDIQhS+w/Tes
QJ7DNuQ8bEPOozbZuNTRcaq6vqIVvsj5YNjc8TV3rtSxo/SXv5iB8C1aSG+9Ffv8P/9ZKi42c9Eu
vdS89k9/klavTu79vc75oiKpRw9PL4kMReELAAAAQKhFdnXMNrUVvhAMm2d8Pf+8ycnvv5eee046
9VTp7bejn/vpp9I//yndcYfZeGHZMunCC80Muk6dpHPPlT76yNulkIkqKmK+ly0ofAEAAAAItWzs
+JJMkaFjR9Mxg8zQpo1UWipVVgYdSXq5rjRpknTmmabTS5KGDZMWLpRWrap5bmWldNVVpqh0/fXm
sW7dpH/8Q/ruO3NctEg6+mipb1/pmWekzZvT+3m2bDEzyih82YHCFzR69OigQwB8R57DNuQ8bEPO
ozbZWvi65hopVmqT88Fo29YUdtauDTqS9CooMEWr00+veuykk6ScnN27vp5+WvrkE+lf/5Lq16/5
XNOmJq+XLDG7kHbsKF1xhSmMTZpUewxe5vzy5aaYx1JHO1D4gjanu7wOBIA8h23IediGnEdtsnWp
4zHHSBdcEP05cj4YbdqYo23LHSdOlFq2lI48suqx5s3NrK/qha+SEumWW6QRI2qeuyvHkYYMMcWu
5culww4zRbXzzjNzwaLxMueLisyRji87OG6Qi2rj5DhOrqSCgoIC5ebmBh0OAAAAgCyy337S5ZdL
d94ZdCTIdsuXS927Sx98YIo+tujVyyxLfPHFmo//85/STTeZ5Z/Nmkm/+pX0zjtmplciS3RdVxo3
Tvrd78wS388+8zb+Xd11l/T446ZQh+xVWFioPDMEMc913cJY59HxBQAAACDUysuzc6kjMk/btuZo
086OK1aYmVxnnLH7c8OGSdu3m2WLH3wgvfSSdP/9ic+lcxwz/P7BB83csI0bvYk9FnZ0tAuFLwAA
AACh5bpmxlc2LnVE5mne3Mytsmmp48SJUsOG0tChuz/XubN06KHSm2+agfZHHCFdemny79W7tzku
XJj8NeLBjo52ofAFlZaWBh0C4DvyHLYh52Ebch6xbNsmVVSEr+OLnA+G45g5XzZ1fE2cKJ14Yuw/
Q8OGmWWKX30lPfGEVC+FKkOPHqawGG2po1c5v2OHWbJK4cseFL6gESNGBB0C4DvyHLYh52Ebch6x
lJebY9g6vsj54LRta0/H108/SR99VHM3x13l55vj9debWWCpaNDAFKSiFb68yvlVq6QtW1jqaJOc
oANA8O5kyicsQJ7DNuQ8bEPOI5ayMnMMW8cXOR+cNm3sKXxNnmyWCw8bFvucgQOlf/9b+sUvvHnP
3r2jF768ynl2dLQPHV9gp0xYgTyHbch52IacRyxhLXyR88Fp29aepY4TJ0qDBknt28c+x3GkM8+U
GjXy5j1795Y+/9wsSazOq5xfutR0gO63nyeXQxag8AUAAAAgtMK61BHBqd7x5bqSV+PWHn9cuugi
swwvE/z8s/Tee7Uvc/RD797mvb/80p/rFxVJ3bunNosM2YXfagAAAAChFdaOLwQnMuNryRLp5JOl
du2kL75I/bpPPCG9+qp03nnS9u2pXy9VM2ZImzcHU/iSoi939MLSpSxztA2FL2jMmDFBhwD4jjyH
bch52IacRyyRjq+wFb7I+eC0bSutXSsddpjZHbCyUlq4MLVrFhdLixZJl10mTZ0qXXzx7kv90m3i
RKlbt/QPgW/TRurQYffClxc577qm44vB9nah8AUVFhYGHQLgO/IctiHnYRtyHrFEOr7CttSRnA9O
377SvvtK99xjuoeaN0+942vGDHO8+27ptdekN9+Urrsu9ViTtWOHNGlS+ru9IqINuPci59esMUVL
Or7s4riuG3QMdXIcJ1dSQUFBAUMcAQAAAMTtmWek3/zGfCPPTB/4oX9/0/2VSkPS8OFSYWFVsWfU
KOnll6UffvAmxkT997/SEUdIc+ZIhx+e/ve/5Raz7PObb7y97qxZ0jHHSIsXSwcf7O21kX6FhYXK
y8uTpDzXdWNWRrn1AwAAAAit8nKpSROKXvBP166pdXy5rjR9unTiiVWP7buvtHFj6rEla+JEs6Rz
4MBg3r93b+nbb013lpeKiqQ99pAOOsjb6yKzcfsHAAAAEFplZeGb74XMkmrha/lyafXqmoWvZs3M
YPmKitTjS8bEidKwYaZIFITIgPtUZ6ftqqhIOvBAqUEDb6+LzEbhCwAAAEBoUfiC37p2NcPpN21K
7vUzZkj160tHHVX1WPPm5hhE19fSpdKyZcHN95LMUP2GDb3f2ZEdHe1E4QvKz88POgTAd+Q5bEPO
wzbkPGIpLw/fYHuJnM8kXbua45dfJvf66dOlQYNqFmibNTPHIApfEyea5cHVO9DSLSdHOvTQmoUv
L3KeHR3tROELGjlyZNAhAL4jz2Ebch62IecRS1g7vsj5zBEpfCWz3HHHDmnmzN2LTEEXvk46SWrc
OP3vXd2uOzummvNlZWZYPh1f9qHwBQ0dOjToEADfkeewDTkP25DziCWshS9yPnO0bCm1apVc4aug
QNqwIXMKXyUl0scfB7vMMaJ3b7P7YmTOWao5v3y5OVL4sg+FLwAAAAChFdaljsgsyQ64nz5datpU
6t+/5uORGV8bNqQeWyLefltyHOnUU9P7vtEccoi0dau0YoU31ysqMsfu3b25HrIHhS8AAAAAoRXW
ji9klmQLX1OnSscea4bbVxdUx9eECdKRR0qtW6f3faM55BBzXLzYm+stXSrts09VURH2oPAFTZgw
IegQAN+R57ANOQ/bkPOIJawdX+R8Zkmm8FVcLM2eLZ155u7P7bmn6bxKZ+GrrMx0oGXCMkdJatfO
LCONFL5SzXkG29sr4cKX4zhHOY4zyXGc7xzHqXQcJ3+X5890HOc9x3FKdz5/WJRrNHQc57Gd52xy
HGe84zhtU/kgSN7YsWODDgHwXabmuetKCxZI//lP0JEgbDI15wG/kPOIJawdX+R8ZunaVVqzRlq/
Pv7XvPWWtMce0QtNjmO6vtK51HHaNLO0MFMKX44jHXywtGSJ+TrVnC8qYr6XrZLp+NpT0gJJV0ty
Yzz/kaSbYzwvSQ9LOlXS2ZKOlrSPpDeTiAUeeO2114IOAfBdpuX5mjXSnXeav3z79pWGDpUqK4OO
CmGSaTkP+I2cRyxhLXyR85klmZ0dx4+Xjj/edDVF07x5eju+Jk6UDj1UOvDA9L1nXQ45pKrjK5Wc
r6gwvzcUvuyUcOHLdd2pruv+2XXdiZKcKM+/7Lru/0maEe15x3GaSRoh6XrXdT90XfdTScMlHeE4
zoCEPwEAZKG//126915p0CDpxhul7dsT+wkhAACIT1iXOiKzJFr4+vFH0/F/zjmxz2nWLH2Fr4oK
afLkzOn2ijjkEDObK7KzY7JWrDD/3mapo52CmPGVJylHpjAmSXJdd5mkbyQNDiAeAEi7VaukgQOl
55+Xhg0zj5WWBhoSAACh47rh7fhCZmnWTGrbNv7C14QJZilftPle1a+ZrsLX7NnS2rWZWfjatk36
6qvUrhPZ0ZGOLzsFUfhqL2mb67q7/hEu2fkcAITe6tXSfvuZ/47smkPhCwAAb23bZjpFKHwhHRIZ
cD9+vNnNsbbdE5s3T8+Mr+Ji6f/+z+x4mJfn//slwqudHZcuNYXEDh1SjwnZh10doeHDhwcdAuC7
TMvz1aul/fc3/03hC37ItJwH/EbOI5rycnMM41JHcj7zxFv4+uknaebM2pc5Sv50fL34onTbbdK7
70rr1kljxpguqM8+k558UqqXYRWCtm3NDLQlS1LL+ciOjs5uw5hggyDSulhSg52zvqprt/O5mE45
5RTl5+fX+DV48ODdtjWdNm2a8vPzd3v9NddcozFjxtR4rLCwUPn5+Srd5TvOO+64Q6NHj67x2Dff
fKP8/HwtXbq0xuOPPPKIRo0aVeOxzZs3Kz8/X7Nnz67x+NixY6P+gT3//PMD+xxDhw4NxeeI4HPw
OaJ9joULF2bM56islL77znR8TZs2TZddZj5H9fDC/vvB5/D/cyxcuDAUnyMsvx98Dv8/x4oVK0Lx
OcLy+5Epn2PBAvM5Ih1f2fo5ov1+rFmzJhSfIyy/H6NGjapR+Krtc+TnD5fr1lzmGO1zbNw4TQUF
3n6Ou++W7r77G51ySr5atlyqyy+X8vNNYejrrzPv98NxTNfXuHF3aMuWLf//PNdNLK8WLdqs77/P
zryqLujfjyA/x4033rhbLWjIkCG7nRuN47qxNl6M48WOUynpDNd1J0V57gBJKyT1dV13YbXHm0la
I+kC13Xf2vlYd0lFkga5rjs3yrVyJRUUFBQoNzc36XgBIBP8+KPUrp3ZwvqMM8xje+8t/fGP0s03
BxsbAABhUlQkHXywmV90xBFBR4Owe+MN6bzzzA8zW7WKfd4vfiFt2SJ98EHt17vpJuntt6Vly7yL
sX176ZprpAsukP77X6lzZ+noo727vh+uukqaM0eK/Exv4UIzi+z116X+/et+/fbtpnvunnuk3//e
31iRXoWFhcoz63PzXNctjHVeTqIXdhxnT0kHqWrHxi6O4/SWtNZ13W8dx2khqaOkfXee08NxHEdS
seu6Ja7rbnQcZ4ykvzuOs07SJkn/lDQnWtELAMJm9WpzjMz4ksxyR5Y6AgDgrbIyc2TGF9Kh+s6O
sQpf69ZJ06dLDz9c9/X8mPG1YYO5bteuVfFmukMOkZ591szry8mRHnpIWrlSGj5cKiiQGjas/fWL
F5tCY79+aQkXGSiZpY79JH0qqUCSK+lBSYWS7tr5fP7O59/e+fzYnc//tto1rpc0WdJ4Sf+R9L2k
s5OIBQCyTqzC108/BRMPAABhReEL6dStm1mat2RJ7HMmTZJ27Kh9N8cIr2d8bdtmCkB77+3dNdPh
4IOrdnYsLZXGjpUuucR0wt19d92vnz/fzC7r29f/WJGZEi58ua77oeu69VzX3WOXXyN2Pv9CjOf/
Uu0aW13XvdZ13dau6zZ1Xfdc13V/9PKDIX67rqsFwiiT8nz1avPTqrZtqx6j4wtey6ScB9KBnEc0
YR5uT85nniZNpAMPlBYtin3OG2+YZbf77FP39Zo1k37+2SzV80Kke6x5c2+uly6RnR3Hj5+tyAiq
v/9duvVWU/iKMta0hnnzTPEsjPcBxCfD9mxAEO67776gQwB8l0l5vnq1tO++NXfNofAFr2VSzgPp
QM4jmjB3fJHzmalXL+nzz6M/t2GDNG2adO658V2r2c7t4DZt8ia29evNMdsKX23bmqWjL754n554
wswna91a+tOfpO7dpREjzDLIWObPj28WGMKLwhc0bty4oEMAfJdJeb56dc1ljhKFL3gvk3IeSAdy
HtFECl9NmgQbhx/I+cx06KGxO77eftt0b511VnzXihSovJrzFblOti11jOzsuH79OK1aJY0caR5v
2NDM/vr0U+nBB6O/dssW0xHGfC+7UfiCmoTxXwLALjIpzyl8IR0yKeeBdCDnEU15uSl61Qvhdz3k
fGbq1UsqLo7+77rx46XBg3f/d2AskY4vr+Z8ZetSR8kUvn78sYkGDKhZxBowQLrhBumOO6Lvfrlw
oekGo+PLbiH8KwAAMluswte6dbW3aQMAgMSUlYVzmSMy16GHmuOuyx03bpSmTpXOOSf+a3ld+MrW
pY6SmdElVXV7VXfXXdL++0uXXSZVVtZ8bt48qX596bDD/I8RmYvCFwCkkevGLny5ril+AQAAb5SX
M9Aa6dW1q9Sgwe7LHd95R9q6NbnCl9dLHSPXzSannSZdemn0+WhNmkhjxkhz5kiPPVbzufnzTRde
w4ZpCRMZisIXNGrUqKBDAHyXKXm+bp3ZnSda4UtiuSO8kyk5D6QLOY9owtzxRc5nppwcqWfP3Tu+
xo83y/I6doz/WpHOLC+XOu61l4kx23TqJLVuPUqNGkV//uijpauvNjs9fv111ePz5rHMERS+IKlj
IndfIEvFk+e7tkb7YfVqc6TwBb9xb4dtyHlEE+bCFzmfuXr1qtnxVVYmTZmSWLeXVDWfzsuljtm4
zDGirpy/916z++MVV5iVFGVlUlERg+1B4QuSrr322qBDAHxXV56PGSN17mz+kvQThS+kC/d22Iac
RzRhXupIzmeuyM6OkX9XTplidhdMtPDlOGZZopcdX9lc+Kor55s2lZ56Spo+3ez2uGCB+cE2HV+g
8AXAetu3S3/9q/TNN1JJib/vtXq1+cld+/Y1H2/RwvzjhsIXAADeCXPHFzJXr17Spk3SqlXm6/Hj
pbw880PWRDVv7u2Mr7339uZameqkk8wssBtvlCZOlBo1qhqMD3tR+AJgvddfr/qHyVdf7f78t996
916rV0sdOuw+W2GPPaSWLSl8AQDgJQpfCEJkZ8dFi6TNm81g+0S7vSK87PjK9qWO8fr736XGjaUH
HpD69jW7OsJuFL6gpUuXBh0C4LtYee660n33ScccY75esaLm84WF0gEHRC+IJSPajo4RrVpR+IJ3
uEFjyPoAACAASURBVLfDNuQ8ognzUkdyPnPtv78pWH3+uTR1qil+ZULhK9uXOsab8y1aSE88Yf6b
+V6QKHxB0s033xx0CIDvYuX51KnSwoXSXXdJ7drtXvhasMAUx7zq+qqt8NW6NYUveId7O2xDziOa
MHd8kfOZy3Gq5nyNHy/16SMddFBy1/K68JXNSx0TyfkzzpAef1y66iofA0LWoPAFPfroo0GHAPgu
Vp6PHi0NHGi2QO7SZffC17Jl5rh2rTdx1FX4+uknb94H4N4O25DziKasLLwdX+R8ZuvVS5o/X3r7
7eS7vSTvZ3xlc8dXojl/1VVSz54+BYOsQuELbIUMK0TL808+kT78UPrDH8xP5rp02X1JY6Tw5VVB
io4vpAv3dtgmW3LedaX33jOzduC/8vLwdnxlS87b6tBDpeXLTfE1lcIXM76qkPNIFoUvANYaPVrq
3l06/XTz9YEHxu748qLwtXGj2eGHwhcA2GvWLOnkk6Vu3aSnn5Z27Ag6onAL81JHZLZevczx0EPN
vzeT5VXhy3Wzv+MLSBaFLwBWWrZMmjBBGjVKqrfzTtili/TDD2YAqSRVVFR1gHmx1HH1anOk8AUA
9nrySTPr5+STpSuuMIOXFy+u/TUbNpgfnCAx27aZv8vDutQRmS1S+Eql20vyrvD188/mz0M2z/gC
kkXhCxo9enTQIQC+2zXP779f6tBBuvjiqse6dDHHlSvN8euvpe3bzTJILzq+4il8bdhg3hNIFfd2
2CYbcr60VHrzTenKK6UXX5T+9z/zjehRR0kffxz9NVu3SoMGmVmUFRXpjTfblZWZY1g7vrIh523W
sqWZ73X99aldx6sZX5Hl1dnc8UXOI1kUvqDNkfYWIMSq5/n330svvST9/vdSw4ZV50QKX5Eur8gy
x169vO342mef6M+3bm2ODLiHF7i3wzbZkPMvvmiOv/61OQ4aJH30kXTIIdIJJ0jTpu3+mvvuk778
UvrsM+mxx9IXaxiEvfCVDTlvu9NOMx1bqWjWTNqyxXQwpiJSPMvmwhc5j2RR+ILuuuuuoEMAfFc9
zx9+WGrcWPrtb2ue06GD1KhR1ZyvZcukJk1M4curjq927aQGDaI/Hyl8sdwRXuDeDttkes67rvTU
U9JZZ1Xd7yWz7Oi996RjjzXfJL/8ctVzX34p/e1v0k03mS6x2283P7xBfMrLzTGsSx0zPefhjUjh
LNXlzpHCVzYvdSTnkSwKXwCssn699K9/me2Nd/0JXL16UufONQtf3bpJrVp51/EVa5mjROELAMJs
1izz98oVV+z+XJMmZu7kRRdJl1xi5k9WVEjXXGN+KHP77aYA1rixdMMN6Y89W4W94wt2iHRopbrc
MQxLHYFkUfgCYJV//cu0iv/ud9Gf79KlZuGre3dT+PKi42vVKumAA2I/T+ELAMLrqaekrl1NZ1c0
9etLzz5rupIfekjq08csfXz0UVMYa9FCeuAB6bXXpPffT2voWStS+AprxxfsEPlBbaoD7sOw1BFI
FoUvqJTvsmGB0tJSbdlivqH49a+l9u2jnxet8NWypen4ct3UYli5UurUKfbzzZtLe+xB4Qve4N4O
22Ryzv/0kzR+vOn2cpzY5zmO+cHMe++ZXYbPPVc69dSq5y++WDrmGOnqq83MH9QustQxrB1fmZzz
8I6Xha969bL7zwM5j2RR+IJGjBgRdAiA70aMGKEXX5R+/NHMSoklUvhat04qKanq+Nq2reof0Mmo
rKy746tePfNe/J0OL3Bvh20yOedfeMEcI0Pt63LCCdI330ivvlrzcceRHn/c/CDl/vs9DTGUwr7U
MZNzHt7ZtfC1fr3pBE30B7IbNphr1cviCgA5j2RlcdrDK3feeWfQIQC+u/32O3X//dLZZ5ulJrEc
eKD5KfqHH5qvIx1fUmpzvn780WxJX1vHl2SWO1L4ghe4t8M2mZrz1Yfat2kT/+v23FPKydn98YMP
lm680cz8iuxCjOgiP7Bq0iTYOPySqTkPb+064+v556Vrr63afTxe69dn/zJHch7JovAF5ebmBh0C
4LuVK3P15ZfSH/5Q+3ldupjju++aY2S4vZTanK+VK82xto4vicIXvMO9HbbJ1Jz/6KPYQ+2Tdfvt
ZpfgkSNjd32wFNJ0fDVpkt0dLrXJ1JyHtxo3NqMwIh1fkRl/CxYkdp0NG7J7R0eJnEfyQvrXAABU
cV1p9Gjp+OOlfv1qP7dzZ3N8911pn32kpk296fhatcoc6yp8sdQRADLTsmXJdVg9+aR00EGxh9on
Y889pX/+U5o6Vfr3v3d//vXXzQ9SvNiROJuVlYV3mSPs4ThmieLGjWb0RmRVwqefJnadDRuyv+ML
SBaFLwChN3OmVFBQd7eXZH4y3L699O23Zpmj5F3HV/Pmdf+kjY4vAMg8riudfrp05ZWJvS7eofbJ
OP10adgwMwx/06aqxysqpD/9ySzzmzvX2/fMNuXl7OiIcIgUvv73P5PXnTolXvgKw1JHIFkUvqAx
Y8YEHQLgq8cfl/bbb4yGDInv/AMPNMdI4atZM9Ninmrhq675XpIpfKXyPkAE93bYxs+cnz3bdHzN
nWs2K4nXiy+aotmll/oT1z/+Ybq67rqr6rGXX5a+/FJq1IjCV9g7vrjP26N5c9Ox9f775t+Kl1xi
ljomMuA+DB1f5DySReELKiwsDDoEwFfz50tt2hTG/dP2yJyvSOHLccxyx1SXOsZb+KLjC17g3g7b
+JnzTz8tNWhgOi7iHSjtumaZY6JD7RPRubN0223Sww9Ln38ubd8u/eUvZiOXY46h8FVWFu6OL+7z
9oh0fL3/vtn1NS9PWrNG+v77+K8Rhhlf5DySReELeuyxx4IOAfDNhg1mS/gbbog/z3ctfEmm8JVq
x1dd870kU/gqK2MoMVLHvR228Svn162T3njD7KToONInn8T3Oj+G2kdz001mt+KrrpKefdb8fXPn
ndKAAabwlUhHSNiUl4e744v7vD2aNTM/RJ0/XxoyROrb1zyeyHLHMCx1JOeRLApfAEJt0SJz7NUr
/tfsutRRMnO+ku34ct34O74ixbHly5N7LwCAt155xczNuu46qUeP+AtfTz1lhtofd5y/8TVoID32
mDRnjvT730vnnScdeqgpfK1ZU7W5io3CvtQR9mje3Cy5rqw0ha/995datEhsZ8cwLHUEkkXhC0Co
ff65mc/Vo0f8rznzTOm556p2eJRS6/gqLZU2b46v46tfPxPvxx8n914AAO+4rlnmOGyY2fhk4MD4
lg/6OdQ+muOPly66SNq6VbrjDvPYgAHmaPNyx7AvdYQ9mjUzRa9u3aSOHc19pW/f+Du+KivNUsls
X+oIJIvCF4BQW7TIdG41bBj/a/baywwirv7NSiodX5GftsfT8bXnntJhh5ldewAAwZo/X1q4UPrN
b8zXAwaYr3/+ufbXvfii+Ubz17/2P8aIp54y8fbsab5u29b8vWNz4SvsSx1hj2bNzLH6Rk19+sRf
+Nq0yRTy6fiCrSh8Qfn5+UGHAPjm88/Nko9U8zyVjq+VK80xno4vSRo8mMIXUse9HbbxI+efftos
KRo61Hw9cKBZ9ljbfGXXNUWoM880xad0adJEys2t+Vhkzlc2+fJL7zZ5CftSR+7z9ohW+OrbV/r6
azO7qy4bNphjthe+yHkki8IXNHLkyKBDADwxc6b0449VX7uuKXz16pV6nqfS8bVypfmHd8uW8Z0/
aJAZiJzKLpIA93bYxuuc/+IL6YUXpCuvNEvQJfP3SaNGtReTZs+Wli6VfvtbT8NJyoABUkGBKdZl
A9c1Rca//c2b65WXh3upI/d5e7RpI9WvLx17bNVjkQH3n31W9+sjha9sX+pIziNZFL6goZEfYwJZ
7uyzpbvuqvr6++/Nblz/j707D4+qPN8Hfh8ICXsggQSQTau4K2sg7gtERYxarYpWK9SlFehm4Vfb
WgFt+3WrVkFbK1ptFXAFpWURVCCsSrCCgkshCSFkgUAghCSEnN8fD6eZ7DPvnDNnee/PdXEdkkxm
3sjjycw9z/ucs8+Ovs6t4Evl6ljWYPtw57ykp8sx3AHKRE3huZ10Y3fN/+IXMtfrZz+r+1y7dsCw
YS2fn//6VxlqH/oC1S1paTJj8ssv3V5JeP77X+lgCX0TKxpB7/jieV4f3/++BO6hHVunnipBfDgD
7oPS8cWaJ1UMvogoECoqpNX7vffqwqktW+QYyRUdm5OUBBw7JoNBI5WTE/42R0CuKtmjB7c7EhG5
ZckSYNEi4IknZAthqLS05oMva6j93XcDbTzwLHvoUFmHX7Y7rlghx3C2boWDw+0pKDp1kpleoeLi
5DluOHO+rP+n/B58EanywK9kIqLoFRXJMT+/bvbKli3yRCGcofKtSU6Wo8qcL6vjK1yGwTlfRERu
qa6WLq9LLgFuvLHx10eOlDc0mupK+tOfZKj9nXc6vMgwdeokcy79EnwtXy5HqzslGtXVssUzyB1f
ROFe2TEoHV9Eqhh8ERYsWOD2EoiiVlhY9/f33pPj1q3AmWfKu93R1rk1nyvS4Ms0I+/4AmTO14YN
0mVGpILndtKNXTX/7LMy3+vPf256i/rIkXJsGCatXw/83/8BDz4Y26H2rfHLgPvaWuCjj+R3th0d
X+Xlcgxy8MXzPA0eLFuZq6pavl1ZmWzV7tAhNutyCmueVDH4IsydO9ftJRBFzQq+MjKAhQvl79Zg
eyD6Orc6viIdOL9/v1xCOtKus/R0+b5t2yL7PiILz+2kGztqvqgImDkT+PGPgXPOafo2AwZIsBW6
3fHwYeD224ERI4AHHoh6GbZKS5M3gg4fdnslLfvPf+TNpQsvtDf4CvJWR57nacgQ6Wz84ouWb3fg
gHR7hTtv1qtY86SKwRdh/vz5bi+BKGpFRXLVrQkT5Mnzf/8r74BZwVe0da7a8ZWbK8dIg68RI+Rd
b253JFU8t5Nu7Kj5X/9a5ubMnNn8bQxDur5efVWu+njkCPDLX8oFVV59Vb7fSy64QLqHP/jA7ZW0
bMUK6Ua58kp7tjpaQV+QO754nqezz5ZzUmvbHcvKgrHNkTVPqhh8EVEgFBYCqanA2LHSyv2nP0nb
tx2D7QF5xzg+PvKOr5wcOUa61bFzZ+k2YPBFRBQbn3wCvPQS8PDDdW92NOf3vwdOO01mefXuDfzl
LzIIf9CgmCw1IqefLkPuX3nF7ZW0bMUKCelSU6Vbq6YmuvvToeOLqFMnubpja1d2LCsDunWLzZqI
vIjBFxEFQmGhXHa+a1fg0kuBOXPk82edZc/9G4a8EFLp+OrQAejZM/LHHDVKZsYQEZGzamuBn/xE
3nC4557Wb3/22cDSpcC33wI/+pEMw//Rj5xfp6oJE+QqlSUlbq+kadXVwKpVwOWX13WlqFxFOdT+
/XLs3j26+yHyunAG3FtbHYl0xeCLiALBCr4A4NprpdsrJcXeAcPJyWodXwMGqM1USE+XGV/Wk3ci
InLGa6/JGw3PPBPZVsXvfEcG2j/1lLdn54wfL+t77TW3V9K0DRuAigoJvqyulGjnfDH4Il0MHixj
Pmprm79NULY6Eqli8EWYMGGC20sgipq11REArrlGjqHbHO2o80g7vvbsAT78MPL5Xpb0dDmGDlAm
ChfP7aQb1Zo/dAiYNg246Sbg4ottXpRHJCcDmZnA3/8em8errIzsqsQrVkjgNWRI3YvzaOd8lZbK
7M8uXaK7Hy/jeZ4A+f+mvFzm2zYnKFsdWfOkymPjN8kNGRkZbi+BKGqFhcBll8nf+/UDxoyRLY8W
O+o8ko6vN96Qq4K1awfMnq32eCefLI+5bp0M+yWKBM/tpBvVmv/97+VF4eOP27wgj7nzTnljaPNm
eaHslFWrgEsuAUwTSEiQmZWdOjX9x/ra4sXyO7xtW3s7vpKSvN2JFy2e5wmQji9A/t8+5ZSmbxOU
ji/WPKli8EUYP36820sgioppylUdra2OALBsWf3b2FHnSUlySfiWlJYCkyYB8+YBN94IPP880KOH
2uMZBud8kTqe20k3KjX/zTeyTfHXvwb693dgUR5y5ZXSGf33vzsbfGVlSZfVU0/JlRUb/ikvl+P+
/UB+vvy9TRvgjjvk++0KvkpLg7/Nked5AmSO7AknyID7m25q+jZBmfHFmidVDL6IyPcOHpRtFaHB
lxNa6/havBj44Q/l0vavvVY3UyUa6enShVBbKy8MiIjIPr/4hVyVcdo0t1fivLg44PbbgZdflt8r
8fHOPM7WrXKRgIkT1b6/a1c52rHVsbWrcxIFRUsD7mtqGr9BTKQbvowiIt8rLJSj07/Qm5vxVV4u
V/MaO1ae7G/dCtx6qz3bK9LT5cn/tm3R3xcREdVZvFiudPjEE3L1XR384Afye6xhV7SdtmyJ7orK
7drJ9ke7tjoS6WDw4OaDr4ICmbmnOnOWKAgYfBGysrLcXgJRVMIJvuyo8+RkeSIeOrA3Kws491zg
H/+QbY2LF0u7uV1GjJBOL253pEjx3E66iaTma2qAn/9cZkHecIODi/KYM8+UF79Llzpz/9XVwPbt
9S8uoyIx0Z6Or6BvdeR5nixDhkhXl/WcOFROjhwHDIjpkhzBmidVDL4Ijz32mNtLIIpKOMGXHXWe
lCTzxA4ckK2V06YBF10k22Q+/1y6vuweotuli7xzvm6dvfdLwcdzO+kmkpr/5hvgq69ktleQh583
ZBhARoZzHV/ffCOhYjQdX4DM+bJjxlfQO754nieLNbevqa6v3Fw5BiH4Ys2TKgZfhHnz5rm9BKKo
FBYC7du3fMlyO+o8OVmOy5cDw4cDf/4z8H//B6xcCXznO1HffbPS0xl8UeR4bifdRFLz+flydPLc
7VVXXAF8/XVdF4idrAvAnHlmdPdjR/Clw1ZHnufJMnCgdEo2FXzl5MgA/I4dY70q+7HmSRWDL0LH
IJwFSWuFhdLt1dK79nbUufUE+pZbZEjwp59K11fbtlHfdYvS04Evv4z+RQDphed20k0kNb97txz7
9HFoMR522WXye8uJrq8tW6QL2nqjSBW3OoaH53myGIbM+frss8Zfy80Nznwv1jypYvBFRL4XqyvV
DBgg3QG/+Q2wcWP0M0zCNWqUHDdujM3jEREFXX6+dEAkJLi9ktjr1g0YOdKZ4GvrVnt+N0bb8VVZ
KVdYDnrHF1Go5q7smJMTjG2ORNFg8EVEvmd1fDktMRH49lvgkUecuwx8UwYNkifv3O5IRGSP3buB
vn3dXoV7MjJk235Njb33u3Vr9PO9gOg7vvbvlyODL9LJ4MHyPPXgwfqfD1LHF5EqBl+EqVOnur0E
oqiEE3z5uc4NQ7q+GHxRJPxc80QqIqn5/Hx7r8DrNxkZEix98ol993n4MLBjhz3BV7QdX6Wlcgz6
Vkee5ymUNeD+88/rPldbC+TlBafjizVPqhh8Efr37+/2EoiiEk7w5fc6T08H1q+XJzBE4fB7zRNF
KpKa173ja8QICZfs3O745Zdy5WMvbHW0gq+gd3zxPE+hTj9ddiSEbncsLASqq4PT8cWaJ1UMvghT
pkxxewlEyo4dA4qLWw++/F7no0bJu/NffeX2Ssgv/F7zRJGKpOZ17/iKiwMuvxxYutS++9y6VTqU
Tz89+vuytjqaptr367LVked5CtWunXRchg64t67eGpSOL9Y8qWLwRUS+tm+fhF+xmPHlprQ0eUHB
7Y5ERNGpqgJKSvTu+AKAK64ANmyw74rBW7YAJ50EdOoU/X116ya/2w8fVvt+XbY6EjXUcMB9bq4c
gxJ8Eali8EVEvlZUJMfUVHfX4bSuXeVdPAZfRETRKSiQo84dX4DM+aqtBa66Cvjd76T7K5qB8nZd
0RGQji9AfT2lpUDnztIBQ6STwYPl/8Xqavk4J0cC4K5dXV0WkesYfBG2b9/u9hKIlBUWyrG1jq8g
1PmoUTLniygcQah5okiEW/O7d8tR946vAQOAV18FUlKA554DrrxSXiAPHgxMmgS8/rp0i4S73dCu
KzoC0vEFqHej7d8f/G2OAM/z1NiQIcDRo8C2bfJx0K7oyJonVQy+CNOmTXN7CUTKrOCrtY6vINR5
ejrwxRfRvSNP+ghCzRNFItyaz8+Xo+4dXwBw++3AwoWy9XP7duDFF4GhQ4Hly4HbbpMXzP36AS+8
0PL97NsH7NnjneCrtFSPbY48z1ND55wjozGs7Y45OcHa5siaJ1UMvgizZs1yewlEygoLZUtEhw4t
3y4IdZ6eLu+8b9zo9krID4JQ80SRCLfm8/OBLl249SeUYQCnngpMnAi89JJcSKW4GFiwQF40P/98
y9+/dascvbTVUYeOL57nqaEuXYCTT64LvoLW8cWaJ1UMvoiXhSVfKywMb7B9EOp80CB5B5tzvigc
Qah5okiEW/O7d7PbKxw9ewLXXgv84AcyuL6iovnbbt4MxMcDp5xiz2Nzq2N4eJ6npgwZIld2NE0J
voLU8cWaJ1UMvojI18INvoKgTRtg5EjO+SIiikZ+Pud7RSItTa6wGHqluIaWLwcuuMC+YfIdOgBx
cdF1fOmw1ZGoKYMHS/BVVAQcORKs4ItIFYMvIvI1nYIvQLY7rl8vV+IiIqLIseMrMmeeKUFUc9vs
q6qAjz6Sq0TaxTCk6yuaGV86dHwRNWXIEODgQeDjj+XjIG11JFLF4Ivw6KOPur0EImVFReEFX0Gp
8/R02cLx9ddur4S8Lig1TxSucGueHV+RaddOBt43F3ytXSvbIK+4wt7HjSb40mWrI8/z1JQhQ+S4
YIEcg9TxxZonVQy+CBUtDW0g8rjCwtav6AgEp87T0uSdcM75otYEpeaJwhVOzR87JlcfZMdXZNLS
mg++li0DUlLkanJ2SkxU2+pYWyvBlw5bHXmep6akpsqbwv/+twy7D9L/C6x5UsXgizBjxgy3l0Ck
5OhRuYR6OMFXUOo8MRE44wzO+aLWBaXmicIVTs0XFwM1Nez4ilRaGrBjB7B3b+OvLV0KjBkjcyjt
pNrxVVYmQ7116PjieZ6aM2QIcOiQdHsZhtursQ9rnlQx+CIi39q/X449eri7jlhLT2fHFxGRit27
5ciOr8ikpcnxk0/qf764WIbe273NEVDv+LKeG+gQfBE1x9ruyPleRILBFxH5VmmpHHV7cpueDmzd
KoNLiYgofPn5cmTHV2ROPBFITm683XH5cjmOHm3/Y6p2fFnPDYK0vYsoUoMHyzFI872IosHgi7C3
qb51Ih+IJPgKUp2np8s2jubmrRABwap5onCEU/O7d8uwdt06haNlGE3P+Vq6VGZ79e5t/2NGG3zp
8KYYz/PUnKB2fLHmSRWDL8LEiRPdXgKRkkie3Aapzk89VQYJf/CB2yshLwtSzROFI5yaz8+XbY52
z6PSgRV8maZ8bJoy2N6JbY4AtzqGg+d5as5JJwF33glceaXbK7EXa55U8dc+Yfr06W4vgUhJJNsZ
glTnbdoA11wDLFzo9krIy4JU80ThCKfmd+/mfC9VaWky3D4nRz7eulWurJyR4czjRdPx1bYt0Lmz
/WvyGp7nqTlt2gAvvwycdZbbK7EXa55UMfgiDB061O0lECkpLQU6dQISElq/bdDqPDMT+Oor+UPU
lKDVPFFrwqn5/HzO91I1YoQcN26UKyrPnAm0bw9ccIEzj5eYCBw5AlRXR/Z9paXS7RWkK9k1h+d5
0g1rnlQx+CIi37Ke3Opo9GigQwfgvffcXgkRkX+w40tdz54y5P7JJ4FTTpFtjrNnS/jlhG7d5Bjp
dsf9+/V9bkBERE1j8EVEvqVz8NWxo2wv4XZHIqLwmCY7vqJ13nnAp58CN94IfPMN4OS4HdXgq7SU
V3QkIqL6GHwR5syZ4/YSiJREEnwFsc4zM4G1a4Hi4rrPrV1bN3+F9BbEmidqSWs1X1YGVFSw4ysa
Tz8tW+xfeEEusuKkxEQ5RjrnS6c3xXieJ92w5kkVgy9Cdna220sgUhLJk9sg1vm4cXJctEiO69YB
l1wCPPywa0siDwlizRO1pLWaz8+XIzu+1PXoIdscY8Hq+Io0+NJpqyPP86Qb1jypijj4MgzjQsMw
3jMMY7dhGLWGYWQ2cZuZhmEUGIZRYRjGB4ZhnNzg6x8f/17rzzHDMJ6L5gchdbNnz3Z7CURKIgm+
gljnKSmy7eS994A9e4AbbgCOHuXAexJBrHmilrRW8xs2yJXOTj89RguiqFgdX9zq2Dye50k3rHlS
pdLx1QnAZwDuA2A2/KJhGP8PwGQA9wBIA3AYwFLDMOJDbmYCeAFAKoBeAHoDmKawFiLSmE7bGZqT
mSkDhm+8UT6+7z4GX0RETVm+HBg+XJ9QxO+6dpUjtzoSEVG0Ig6+TNNcYprm70zTXAigqQsF/xTA
w6ZpLjJNcyuAOwD0AXBdg9tVmKZZYppm8fE/5RGvnoi0xie3wLXXyuXeP/kEePtt4OKLgb175b8N
ERGJ2lpgxQq5Ii75Q9u2En7xqo5ERBQtW2d8GYZxIqSDa4X1OdM0DwLYACC9wc1vMwyjxDCMLYZh
/MEwjA52roWIgu3YMXkXWPcnt6eeCtx5J/Dyy0B6unwMAF9/7eqyiIg8ZcsWoKSEwZffJCZG1vF1
5Ij8YVcfERGFsnu4fS/INsaiBp8vOv41y2sAvg/gEgB/AHA7gH/YvBYKU2ZmozFtRJ5XViaXpg83
+Apynb/8MnDbbfL3k49PVOR2RwpyzRM1paWaX74c6NBB5iKSf3TrFlnwtX+/HHV5U4znedINa55U
xbnxoKZpvhjy4ReGYewBsMIwjBNN09zpxpp0NnnyZLeXQBqoqAAMQ1542MHayhfuk1td6rxTJ6Bf
PwZfpE/NE1laqvkPPgAuughISIjhgihqiYmRbXW0gi9dOr54nifdsOZJld0dX4WQuV+pDT6fevxr
zdl4/PtObuE2GDt2LDIzM+v9SU9Px4IFC+rdbtmyZU2mwZMmTcKcOXPqfS47OxuZmZnYu3dvgBUZ
+wAAIABJREFUvc8/9NBDePTRR+t9Li8vD5mZmdi+fXu9zz/77LOYOnVqvc9VVFQgMzMTWVlZ9T4/
d+5cTJgwodHabr75Ztd+joyMjED8HBb+HN78OW69FfjBD+z7Of7972UAMhsFX839HLNmzdLm32PQ
IOCzz/z/cwDB+Pdw6+eYNWtWIH6OoPx78Odw9ud48MG5+NWv5jb5c7z55gKsWlW3zdHLP0dQ/j3s
+jkOHZrzvzArnJ8j9E0xL/0cTv17fPDBB4H4OYLy78Gfw/mfY/PmzYH4OYLy7xHrn+P+++9vlAWN
GTOm0W2bYphmowszhs0wjFoA15mm+V7I5woAPG6a5lPHP+4K2ep4h2mabzZzP+cDWAXg3OMD8Rt+
fSiATZs2bcLQoUOV10tE7qitlXdfa2pk8LodXV9LlgBXXQXs2gX07Rv9/QXJpEnAqlUy04aISAfX
XAOsXt30triPPwYuvRTYvBkYPDjmS6Mo3Hkn8O23QIPXRc16+225ynFxMdCzp6NLIyIiD8jOzsaw
YcMAYJhpmtnN3S7iji/DMDoZhnGuYRjWU4eTjn/c7/jHTwP4rWEY1xiGcTaAVwHkA1h4/PtPMgzj
t4ZhDDUMY4BhGJkAXgGwsqnQi4j876uvgIMHZbvjxx/bc5+RbnXUyamnAt98IxcAICIKuspK4MMP
ZUvcoUONv758uYQg55wT+7VRdJKTgX37wr/9pk1A795Ajx7OrYmIiPxHZavjcACbAWyCDLJ/EkA2
gBkAYJrmYwCeBfBXyNUcOwC4yjTN6uPfXw1gNIClALYBeBzAmwA4qc4lDVsfiey2YYPM9+rTB1i0
yJ77LC2VWS3hdo/pVOeDBgFVVdINR/rSqeZJb1lZ8sYKsAD5+Y2/vnw5cPnlQBu7B3yQ45KSIgu+
1q6VKxwbhnNr8hKe50k3rHlSFfFTANM0V5qm2cY0zbYN/kwMuc100zT7mKbZ0TTNK0zT/Dbka/mm
aV5immbP418/1TTNB0zTLLfrh6LIzJ3beCYGkZ3WrwdOP122HyxaJFdjjFZpqTwhDvfJrU51fuqp
cuSAe73pVPOkt8WLgfbtAWBuo+Br/37gk0/q5nuRvyQny+/7cJ43HD0q/9Y6XbmT53nSDWueVPG9
L8L8+fPdXgIF3IYNwKhRwLhxQF4esNWGTc1W8BUuneq8f3/phmPwpTedap70tmSJvLECzG/U6bpm
jcyZvOwyN1ZG0UpKkm37Bw+2ftvPP5fOv/R059flFTzPk25Y86SKwRcROaqiQoasjxwpl5Lv3Nme
7Y6RBl86adsWOPlkBl9EFHx5ecCXXwKZmUBqKhp1fH3zDdCxIzBwoCvLoyglJ8vRmuvZkrVrgfh4
gNfBIiKihhh8EZGjNm2Sd2tHjpQupIwMBl+xcOqpwNdfu70KIiJnLV4sYf+YMUC/fo1nG+7YAZx0
kj4zn4LG+j0fzpyvdesk9JJtr0RERHUYfBGRo9avBzp1As48Uz4eN06enO7dG939Mvhq2aBB7Pgi
ouBbskS2tnXrBvTt27jjywq+yJ8i7fjSab4XERGFj8EXYcKECW4vgQJswwZg+HAgLk4+HjtWhtQu
Xhzd/UYafOlW56eeKp0Phw+7vRJyi241T/qprpYrNl55pXy8ffsEBl8BE27HV0EBkJur13wvgOd5
0g9rnlQx+CJkZGS4vQQKsA0bZJujJTUVSEsD3nsvuvuNNPjSrc6tKzt++23Lt6Pg0q3mST9r1gDl
5cBVV8nHQ4Zk1NvqWFsL7NzJ4MvPOnWSuV2tdXytWydH3Tq+eJ4n3bDmSRWDL8L48ePdXgIF1O7d
su1k1Kj6n//ud2XO14EDavdrmpEHX7rV+aBBcuR2R33pVvOknyVL5M2UwYPl43HjxqOsDDh0SD7e
sweoqmLw5WeGIb/rW+v4WrdOrmjcp09s1uUVPM+TbljzpIrBFxE5ZsMGOYZ2fAHA7bfLFhXVKxIf
OiQD8znjq3nJyfKHwRcRBdXixcAVVwBtjj+b7dtXjrt3y3HHDjky+PK35OTWO74434uIiFrC4IuI
mvXVV8All8il4hsyzda/f8MGeSHS8B3YPn1ka8pLL6mty3oCzOCrZYMGAdnZbq+CiMh++fnAli11
2xwBuaojUHdlRyv4Gjgwpksjm7XW8VVVJVeQZvBFRETNYfBFyMrKcnsJ5FEffgisXCnh1+efy+dM
E3juOSAxUS4hn5AAdO4MdO8OpKQAJ5wgLzJOOQV4/vnG2xwtEyYAGzcCX3wR+bpUgi8d6/z224EF
C+TKmqQfHWue9LF0qXR6jRlT97mdO6XmrQH3O3bIGy0dOriwQLJNcnLLwVd2tnSR6zbYHuB5nvTD
midVcW4vgNz32GOP4YILLnB7GeRBOTlA797y59JLgb//HXj2WeCDD4C77pKrNR492vhPTU3d32+7
ren7vuYaoEcP4OWXgSeeiGxdKsGXjnV+zz3Aiy8C990HfPKJBJWkDx1rnvSxeLFcKCU5ue5zTz/9
GFJTL6jX8cVtjv6XlNTym2Rr10q4ee65sVuTV/A8T7phzZMqBl+EefPmub0E8qicHOD004G335bL
xWdmyrvnS5bIXJVoxMdLKPaPfwB//CPQrl3436sSfOlY523bSnfeqFHAX/4CTJrk9ooolnSsedLD
0aPyBsz999f//Lx583DRRfU7vk4+OfbrI3u11vG1bh0wYkRkzyOCgud50g1rnlRxqyOhY8eObi+B
PGrnTtm22K0bsGyZdHtt3Rp96GWZMAEoLgb+/e/Ivq+0VEKdLl3C/x5d63zkSOnO+81vgKIit1dD
saRrzVPwrV8PHDxYf74XIDXft2/94IsdX/7X0nB709R7sD3P86Qb1jypYvBFRM3KyakbCty1KzB5
sszyssu55wJDhwKzZsl8jnCVlkq3l2HYt5Yg++MfJSj86U/DuygBEZGXLV4sW+WHDWv8tX79ZLh9
RQVQWMjgKwiSkoD9++Vqzg3l5QF79ug534uIiMLH4IuImnT4MFBSApx4orOP8+tfAx9/LNvxwh10
bwVfFJ4ePYDZs4H584GHH3Z7NURE0bG227dp4lms1fG1c6d8zODL/5KT5U2bsrLGX1u7Vo4MvoiI
qCUMvghTp051ewnkQbm5cnT6MvA33CDbVior5d37J55o+l3dUCrBl+51fsstwCOPAA89BLzyitur
oVjQveYpmAoLgc2bG29zBKTm+/YFDhyouxIxgy//s37fNzXna906mePWs2ds1+QVPM+TbljzpIrB
F6F///5uL4E8yHq33OngC5DAa9MmGb4+bZpcQXLHjuZvrxJ8sc6lu+7uu2Xm1wcfuL0achprnoJo
yRLZ5p6R0fhr/fv3R79+8vdVq4D27YFevWK7PrKfdeXOpuZ86TzfC+B5nvTDmidVDL4IU6ZMcXsJ
5EE5OXKFpN69Y/N4HToATz4JfPSRzGc55xzghReankmlEnyxzuXF4nPPAaNHS6ed1RFBwcSapyBa
sgQYPrzpDp8pU6agb1/5+6pV0u3FWZD+11zH1+HDwGef6R188TxPumHNkyoGX0TUpJwcoH9/GYoe
SxdfLIHM+PHAvfcCV18NFBTUvw1nfKmLiwPeeEO2howdW3f1MyIir6upkSsMN7XN0XLCCXL88ktu
cwyK5oKvTz+V0Qic70VERK1h8EVETcrJcX6wfXO6dAH+9jdg0SKZ5XLWWTKY3cLgKzpdush/27Zt
JfxqamAwEZHXbNwoV/e78srmb5OQAKSkyN8ZfAVDhw7yp+FWx7Vr5ffZmWe6sy4iIvIPBl+E7du3
u70E8qCdO2Mz36slV18NbN0qW/NuuUX+7NunFnyxzuvr0wf497/lUvA33ggcPer2ishurHkKmiVL
5Nyfltb0162at7Y7MvgKjuTkxh1f69YBI0fGvjPdS3ieJ92w5kkVgy/CtGnT3F4CeVBOjvvBFyBP
dufPB15/Xba4nHkmUFUVefDFOm/szDOBd98FVq4E7rmn6Xlq5F+seQqaxYtlqH1zQYdV8wy+gicp
qX7Hl2lK8KXzfC+A53nSD2ueVDH4IsyaNcvtJZDHHDok76x6IfgCZDjx+PHAli3A4MHyuT59IrsP
1nnTLr0U+Pvf5c/MmW6vhuzEmqcgKS6WmU4tbXO0at66siODr+Bo2PH17bfA3r2c78XzPOmGNU+q
4txeALmPl4WlhnJz5ejWjK/mnHCCvOP/2Wd1AVi4WOfNu/VW+Tf/9a+BAQOAO+90e0VkB9Y8Bcmy
ZXJsKfiyat7q+PLa7zBS17Dja+1aOY4a5c56vILnedINa55UMfgiokZ27pSjVzq+QhkGMGSI26sI
nl/9Sv7d77kHGDcO6NHD7RUREdVZvBgYOhRITW39trfcAnTsKH8oGJKTZQSDZd064IwzgG7dXFsS
ERH5CLc6ElEjOTlAfDzQq5fbK6FYMQzgwQdlyP3q1W6vhoh0l5cHHD4sfz92DFi6tOVur1ADBwI/
+YljSyMXNNXxpft8LyIiCh+DL8Kjjz7q9hLIY3JyZMtbmwCdIVjnrevXT14wrlrl9krIDqx58rNR
o4BzzwU2bZI/+/YBV13V8vew5oMrdMbXwYNyxWcGX6x50g9rnlRxqyOhoqLC7SWQx3jlio52Yp2H
58IL2fEVFKx58qsDB4A9e4Du3SXcGDFCtrS1Ns+JNR9cSUkSeB09CmzYIFd11H2wPcCaJ/2w5kmV
Yfrg+vWGYQwFsGnTpk0YOnSo28shCryhQ+WFxl//6vZKKNZefBG4915g/36ga1e3V0NEOvrPf+QC
JitXAm+9BTz7LPC97wFvvOH2ysgtCxcC110HFBUBzz8PPPMMUFISrM50IiKKXHZ2NoYNGwYAw0zT
zG7udvx1QUSNBLHji8Jz4YVAba0MDiYicoM1xPzUUyXgWL0aePJJV5dELktOluO+ffL7adQohl5E
RBQ+/sogonrKyqTbh8GXngYNAlJSuN2RiNyTkwO0by/nIgC44AKZQUj6SkqS4969wPr1nO9FRESR
8VXw5YNdmb60d+9et5dAHpKbK8egBV+s8/AYhnR9ccC9/7Hmya+srmPDiOz7WPPBZXV8ZWXJG3Sc
7yVY86Qb1jyp8lXwZV3Wmuw1ceJEt5dAHrJzpxxPPNHdddiNdR6+Cy8ENm4EKivdXglFgzVPfqW6
3Z41H1zdu8tx0SLZ4piW5u56vII1T7phzZMqXwVfhw65vYJgmj59uttLIA/JywPi4+u2mAQF6zx8
F10EVFUBn3zi9kooGqx58ivV4Is1H1zx8UCXLrLN8ZxzgM6d3V6RN7DmSTeseVLlq+Dr4EG3VxBM
vFImhSoultAraENjWefhO+ccuaIj53z5G2ue/Eo1+GLNB1tSklx8hfO96rDmSTeseVLlq5e2DL6I
nGcFX6Svtm2B88/nnC8iir0DB+RP0OZMUvSsOV8MvoiIKFK+Cr641ZHIeSUlDL5I5nytXQvU1Li9
EiLSSVAvsELRs67syMH2REQUKV8FX+z4csacOXPcXgJ5SFA7vljnkUlPlzcbvvnG7ZWQKtY8+VFO
jhxVgi/WfLAlJwOpqcG7+E40WPOkG9Y8qWLwRcjOznZ7CeQhQQ2+WOeRSUyUI6+m61+sefKjnByg
fXu130Os+WC74w5g5kzAMNxeiXew5kk3rHlSFef2AiLBrY7OmD17tttLIA8pLgZ69nR7FfZjnUcm
IUGOVVXuroPUsebJj6zB9irhBms+2MaOdXsF3sOaJ92w5kkVO76I6H+qq4GysmB2fFFkGHwRkRtU
r+hIRERE1BwGX0T0PyUlcmTwRQy+iMgNDL6IiIjIbr4KvrjVkchZxcVyZPBFVvBVXe3uOohILwy+
iIiIyG6+Cr7KytxeQTBlZma6vQTyCCv4CuKML9Z5ZNjx5X+sefKbAwfkj2rwxZon3bDmSTeseVLl
q+CLWx2dMXnyZLeXQB5hbXUMYvDFOo8Mgy//Y82T3+TmylE1+GLNk25Y86Qb1jyp8lXwxa2OzsjI
yHB7CeQRxcVA585Ax45ur8R+rPPItGsnRwZf/sWaJ7/JyZGjavDFmifdsOZJN6x5UuW74Ms03V4F
UXAVF3O+F4k2bST8YvBFRLGycyfQvj1/DxEREZG9fBV81day64vISQy+KFRCAoMvIooda7C9Ybi9
EiIiIgoSXwVfALB/v9srCJ4FCxa4vQTyiJKSYM73AljnKhh8+Rtrnvwm2is6suZJN6x50g1rnlQx
+CLMnTvX7SWQRwS544t1HrmEBKC62u1VkCrWPPlNtMEXa550w5on3bDmSRWDL8L8+fPdXgJ5RJCD
L9Z55Njx5W+sefKbaIMv1jzphjVPumHNkyoGX0T0P0EOvihyDL6IKFaqq4GyMqBXL7dXQkREREHD
4IuIAACHDwMVFcGd8UWRi49n8EVEsWGda9q3d3cdREREFDy+Cr46dWLwReSUkhI5suOLLOz4IqJY
qayUY0KCu+sgIiKi4PFV8NWlC4MvJ0yYMMHtJZAHFBfLMajBF+s8cgy+/I01T35inWuiCb5Y86Qb
1jzphjVPqnwVfHXtyuDLCRkZGW4vgTwg6MEX6zxyDL78jTVPfmJH8MWaJ92w5kk3rHlSxeCLMH78
eLeXQB5gbXXs0cPddTiFdR65hAQZOE3+xJonP7Ej+GLNk25Y86Qb1jyp8lXwxa2ORM4pLga6dwfa
tXN7JeQV7PgioljhcHsiIiJyiq+Cr65dgdJSt1dBFEzFxcHd5khqGHwRUazY0fFFRERE1BRfBV+J
iez4ckJWVpbbSyAPCHrwxTqPHIMvf2PNk5/YEXyx5kk3rHnSDWueVPkq+OJWR2c89thjbi+BAOTm
AkuWuPf4JSXBDr5Y55GLj2fw5WesefITO4Iv1jzphjVPumHNkypfBV9duwIHDgCm6fZKgmXevHlu
L4EAPPMMkJkJ7N7tzuMHveOLdR45dnz5G2ue/MSO4Is1T7phzZNuWPOkynfB17FjwKFDbq8kWDp2
7Oj2EghAXh5w9Cjw5z+78/jFxUDPnu48diywziPH4MvfWPPkJ3YEX6x50g1rnnTDmidVvgq+unSR
I7c7UhDl5QFt2wJ/+QtQVhbbxzbN4Hd8UeQYfBFRrFRWypHD7YmIiMhuvgq+unaVI4MvCqK8POCH
P5Sg4a9/je1jHzwo3WYMvihUQgJQXe32KohIB7yqIxERETmFwRdh6tSpbi9Be1VVQGEhMHIkcPvt
wNNPx7bTprhYjkEOvljnkWPHl7+x5slPqqqAuDigTRTPTFnzpBvWPOmGNU+qfBV8caujM/r37+/2
ErRnDbTv3x/45S+BPXuA116L3eNbwVeQZ3yxziPH4MvfWPPkJ1VV0Xd7seZJN6x50g1rnlQx+CJM
mTLF7SVoLy9Pjv37A6edBlx7LfD440BtbWweX4eOL9Z55OLjGXz5GWue/KSqCmjfPrr7YM2Tbljz
pBvWPKnyVfDVtq1sd2TwRUFjBV/9+slx2jRg+3Zg0aLYPH5JiWwvSUqKzeORPyQkADU1sQtgiUhf
dnR8ERERETXFV8EXAHTvzuCLgmfXLqBHD6BDB/n4vPOA888HHnvM+cfeswd4/315/Ghmq1DwWC9C
2fVFRE5j8EVERERO8d3LXAZf9tu+fbvbS9BeXp5scww1bRqwZg2wdq0zj7l7N/CTnwAnngisXg08
8ogzj+MVrPPIMfjyN9Y8+YkdwRdrnnTDmifdsOZJle+Cr6QkBl92mzZtmttL0F5Twde4cTLv6/HH
7X2sXbuAyZOBk04C/vlP4De/AXJygLvvtvdxvIZ1HjnrRWh1tbvrIDWsefITO4Iv1jzphjVPumHN
kyrfBV/s+LLfrFmz3F6C9nbtqpvvZWnTBpg6FVi4UOZ9RSsvD/jxj4GTTwbmzgUeekgCrwcfBLp1
i/7+vY51Hjl2fPkba578xI7gizVPumHNk25Y86TKl8FXaanbqwgWXhbWXaYJ5OY27vgCgNtuA3r1
Ap58Uv3+d+0C7r1XAq833wRmzJDA69e/lotF6IJ1HjkGX/7Gmic/sSP4Ys2TbljzpBvWPKnyZfDF
ji8KkrIyoLy86eArIQH42c+AV1+VIfQqbrwReOcd4Pe/l8DrV78CunSJasmkifh4OTL4IiKnVVZy
uD0RERE5g8EXkcvy8uTYcKuj5d575cXAM89Eft81NcDmzcD06bJtsnNn5WWShtjxRUSxwqs6EhER
kVN8F3xZw+1ra91eSXA8+uijbi9Ba7t2ybG5zt3EROBHPwKefx44eDCy+96xAzh6FDj99OjWGASs
88gx+PI31jz5SVUV0L59dPfBmifdsOZJN6x5UuW74CslRUIvzvmyT0VFhdtL0FpeHhAXJ7O8mvPT
nwIVFcDf/hbZfW/bJkcGX6xzFQy+/I01T35iR8cXa550w5on3bDmSZXvgq/UVDkWF7u7jiCZMWOG
20vQWl4e0Lcv0LZt87c54QTg+98HnnoKqK4O/763bZOOsZZCNV2wziNnvQiNpObIO1jz5Cd2BF+s
edINa550w5onVREHX4ZhXGgYxnuGYew2DKPWMIzMJm4z0zCMAsMwKgzD+MAwjJMbfD3BMIzZhmHs
NQzjkGEYbxmGkRLO46ccv1VRUaQrJ/KmXbuan+8V6pe/BHbvBubODf++v/xSur0MQ319pC92fBFR
rHDGFxERETlFpeOrE4DPANwHwGz4RcMw/h+AyQDuAZAG4DCApYZhxIfc7GkAVwO4AcBFAPoAeDuc
B7eCL3Z8UVDk5TU/3yvUGWcA11wDPP54+DPutm3jNkdSx+CLiGKFwRcRERE5JeLgyzTNJaZp/s40
zYUAmuoj+SmAh03TXGSa5lYAd0CCresAwDCMrgAmAvi5aZorTdPcDGACgPMNw0hr7fG7dJHhp+z4
ss/evXvdXoLWwg2+AOBnPwO++AL49NPWb2uawPbtDL4srPPIMfjyN9Y8+YkdwRdrnnTDmifdsOZJ
la0zvgzDOBFALwArrM+ZpnkQwAYA6cc/NRxAXIPbfAUgL+Q2LTyGdH2x48s+EydOdHsJ2jp2TLYv
hrPVEQDOPx9o1w7YuLH12+bnA+Xl0ilGrHMV8cf7dBl8+RNrnvzEjuCLNU+6Yc2TbljzpMru4fa9
INsfG/ZjFR3/GgCkAqg+Hog1d5sWpaay48tO06dPd3sJ2iosBGpqwu/4SkgAzj0X+OST1m/LKzrW
xzqPXNu28ofBlz+x5slP7Ai+WPOkG9Y86YY1T6p8d1VHgB1fdhs6dKjbS9BWXp4cww2+ACAtLfzg
q317YMAAtbUFDetcTUICgy+/Ys2Tn1RWRh98seZJN6x50g1rnlTZHXwVQuZ+pTb4fOrxr1m3iT8+
66u52zRp7NixyMzMxOefZ2L16kxkZmYiPT0dCxYsqHe7ZcuWITOz0cUmMWnSJMyZM6fe57Kzs5GZ
mdlov/BDDz2ERx99tN7n8vLykJmZie3bt9f7/LPPPoupU6fW+1xFRQUyMzORlZVV7/Nz587FhAkT
Gq3t5ptv5s+h4c8hwVcepk0L/+dYuzYT27Zl4WBIz2RTP8eXXwIJCTfj/ff578GfQ/3nqKmZgOpq
//8cQfn34M/BnyOoP0d5eSYOHPD/zxGUfw/+HPw5+HPw5+DPwZ/Daz/H/fffj8zMzP/9SU9Px5gx
YxrdtimGaTa6MGPYDMOoBXCdaZrvhXyuAMDjpmk+dfzjrpBtjHeYpvnm8Y9LANximua7x29zKoBt
AEaZptloepFhGEMBbNq0aROGDh2KBx4A5s8HduxQXjqRJzzxBDBzJlBWJvPrwvHFF8BZZwEffghc
emnzt7voIuCEE4C5c+1ZK+mpd2/gvvuABx90eyVEFFSmCbRpA7zwAnD33W6vhoiIiPwiOzsbw4YN
A4BhpmlmN3e7iDu+DMPoZBjGuYZhDD7+qZOOf2yN534awG8Nw7jGMIyzAbwKIB/AQuB/w+7nAPiT
YRiXGIYxDMBLANY0FXo1hVsd7dUw1aXYyc2VbY7hhl4AcNppQOfOrW933LaN871Csc7VcKujf7Hm
yS+OHpVjtFsdWfOkG9Y86YY1T6pUtjoOB7AZwCbIIPsnAWQDmAEApmk+BuBZAH+FXM2xA4CrTNMM
3SzzcwCLALwF4GMABQBuCHcBqanA4cPyh6KXnd1sMEoO27w58qsutm0LDBvW8pUd9+6VPwy+6rDO
1TD48i/WPPmFdY6JNvhizZNuWPOkG9Y8qYo4+DJNc6Vpmm1M02zb4M/EkNtMN02zj2maHU3TvMI0
zW8b3EeVaZpTTNPsYZpmF9M0v2eaZtg9XCkpcmTXlz1mz57t9hK0VFkpXVsXXBD5944Y0XLHF6/o
2BjrXE18PIMvv2LNk1/YFXyx5kk3rHnSDWueVPnyqo6px0fnFxW5uw6iaHz6KVBdrRZ8paXJYPzm
/h/Ytk3mpZxySnRrJGLHFxE5za7gi4iIiKgpvgy+2PFFQbBmjczqOuecyL93xAg5Ntf1tW0bcPLJ
fBFB0WPwRUROY/BFRERETvJl8JWcLMPAGXyRn2VlAaNGAXFxkX/vgAFAz57NB19ffsltjmSPhATp
TCQicgqDLyIiInKSL4OvuDigRw9udbRLZmam20vQTm2tdHypbHMEJPgdMaL+gPuKCuBf/wImT5ZQ
jcFXfaxzNez48i/WPPmFXcEXa550w5on3bDmSZUvgy9Atjuy48sekydPdnsJ2tm2Ddi/Xz34AuoG
3O/fDzz4INCrFzBuHLBoEXDHHcCPf2zfeoOAda6GwZd/sebJLyor5Rht8MWaJ92w5kk3rHlSpbDJ
yhtSU9nxZZeMjAy3l6CdNWuAtm2BkSPV7yMtDdi3T7Y91tQA990H/PCHwGmnSUcY1cc6V5OQABw+
7PYq9GCawObNwBlnAO3bR39/rHnyC7s6vljzpBvWPOmGNU+qfBt8paQw+CL/ysoChgzrbvfnAAAg
AElEQVSR4faq0tPlBfLllwMPPAD07m3f+ogs8fHs+IqVNWuACy8EunYFrr8eGD8eyMhgkE3BZ51j
7Ah8iYiIiBry9VZHBl/kV1lZwPnnR3cf3bsDX3wBPPMMQy9yDrc6xs7q1UCXLsDPfw6sWwdceSUw
dixQWOj2yoicxeH2RERE5CTfBl+pqcGZ8fXeezKU3C0LFixw78E1VFAA7NwZ3XwvihzrXA2Dr9hZ
t062ME+fDmzfLvP6Nm8Gzj4bUClf1jz5hV3BF2uedMOaJ92w5kmVb4OvlBSZb1RT4/ZKovfMM7JV
zS1z585178E1tGaNHKPt+KLIsM7VJCQA1dVuryL4TBNYv162MAOyvfHqq4EtW+Rccf31wN13A+Xl
4d8na578wq7gizVPumHNk25Y86TKt8FXaqq8UNi71+2VRO/IEXlx49Z2lvnz57vzwJpavRr4zne4
PTHWWOdq2PEVGzt3AiUlwKhR9T/fsyfw7rvAiy8Cc+fKbMANG8K7T9Y8+YVdwRdrnnTDmifdsOZJ
lW+Dr5QUOQZhu+ORI3L88EN310HO+/xzYM4cYNw4t1dCFB4GX7Gxbp0cGwZfgHR//fCHwGefAcnJ
0gE2c2YwOp6JADnHxMUBbXz7rJSIiIi8zLdPMazgKwgD7isr5bh8ubvrIGeVlsp2pVNOAf7wB7dX
QxQeBl+xsX69nBuSk5u/zcknS8fob38LzJghV4D8739jt0Yip1RVcbA9EREROcf3wVdQOr4MA/jg
A9m+ScFz7Bhw223AgQOybaljR7dXRBQeBl+xETrfqyXt2snw+6ws+f137rnASy/xdwfFVkGBzFm1
C4MvIiIicpJvg69OneRPEDq+jhyR7S35+cDXX8f+8SdMmBD7B9XMww8Dy5YB8+YBJ57o9mr0xDpX
Ex/P4MtpR47INsamtjk2Jz1dvueWW2Qb5I03Np55yZonu+3eDdx3HzBwIHDrrfbdr13BF2uedMOa
J92w5kmVb4MvQAbcB6Xj64or5J18N7Y7ZmRkxP5BNfPmm8CECcCYMW6vRF+sczXWVR3ZUeScTZtk
Xlc4HV+hunSRoffvvAOsXAmcfTawdm3d11nzFC3TBHbsAP7xD+Cuu2S77fz58pxlxQq5IIMdKivt
Cb5Y86Qb1jzphjVPqnwdfKWkBCf4Sk4GzjvPneBr/PjxsX9QzZSXA336uL0KvbHO1VgvRqur3V1H
kK1fL9ufzzpL7fuvv16uDNyjB/DII3WfZ81TNGpq5HnJd74D3HGHhKoPPCBXIH3xRQnFFi6057Gq
qoD27aO/H9Y86YY1T7phzZMqXwdfqan+3+p47Bhw9CjQoQMwerRc2ZFX6gqe8nLZmkvkNwy+nLdu
HTBihFzVTlXv3sDllwM5ObYtizT32msSyv7znzLP68svgd/9DujaVZ5/XXQR8NZb9jwWZ3wRERGR
k3wdfAWh48u6oqMVfB08CHz6qbtrIvuVlwOdO7u9CqLIWS9GOefLGaYpwVek2xybMnCgBF/clkrR
qqmR7sFrr5ULsyQlNb7NjTfKdsfS0ugfj8EXEREROcn3wZffO76OHJFjhw7A8OFAYmLstztmZWXF
9gE1c/SodMsw+HIX61wNgy9n7doF7NkT2WD75gwcKL9TrLlLTtf8E08A//qXow9BLnn9deDbb4GH
Hmr+NtdfL13r770X/ePZFXzxPE+6Yc2TbljzpMrXwZc13N7P726HBl9xccCllwIffBDbNTz22GOx
fUDNHD4sR251dBfrXA2DL2dlZ8sxLS36+xowQI7Wdkcna/7oUWD6dOD55x17CHKJ1e2VmQkMGdL8
7fr0Ac4/357tjnYFXzzPk25Y86Qb1jyp8nXwlZIiT5YOHnR7Jeqs4Msa6jp6tGx7KS+P3RrmzZsX
uwfTkPVvyY4vd7HO1cTHy5HBlzPy8+W/ca9e0d/XwIFytIIvJ2s+O1tC/Q0b/P3mEzU2bx7wzTcy
z6s1N94ILFsGlJVF95h2BV88z5NuWPOkG9Y8qfJ18NW1qxxjGRLZLXTGFyDB19GjwOrVsVtDx44d
Y/dgGrI6vhh8uYt1roYdX84qKJDOGcOI/r66dZPfi1bw5WTNr1wpx717OVA/SI4dAx5+GLjmGmDY
sNZvf8MN8pzl/feje1y7gi+e50k3rHnSDWueVPk6+LK2jlnBgh+FbnUEgEGDgH79Yj/ni5xjBbPc
6kh+xODLWXv2SPBlB8OQrq/cXHvuryUrV9Ztg9u40fnHo9iYNw/4+uuWZ3uF6ttXLswQ7XZHDrcn
IiIiJ/k6+LIC3yAFX4YhXV+xnvNFzuFWR/Iz68VodbW76wiqggKgd2/77s+6sqOTjh0DsrKk2+fE
E2W7I/mf1e01blx43V6WK68EVq0CamvVH5vBFxERETnJ18GX1UFTUeHuOqLRMPgCJPjasgUoLIzN
GqZOnRqbB9IUtzp6A+tcDTu+nGVtdbRLaPDlVM3/5z8yW/Pii4GRI9nxFRTz5wNffRV+t5flvPOA
/fvle1VVVtoTfPE8T7phzZNuWPOkytfBV5A6vqzh9gBw+eVy/PDD2Kyhf//+sXkgTXGrozewztUw
+HKW3cHXgAESfJmmczW/cqX8zhoxQq5GuWmTzHki/7K6vcaOBYYPj+x709KANm2AtWvVH7+qqv7z
IFU8z5NuWPOkG9Y8qfJ18BWEjq+Gw+0BIDUVOOec2G13nDJlSmweSFMMvryBda6GwZdzKiuB0lL7
O74qKmTovFM1v3IlMGqU1EZamvwcW7c68lAUI2++CWzfHnm3FyAXVDj7bLkitSq7tjryPE+6Yc2T
bljzpMrXwVeQOr5Cgy9AtjsuX87LxAfB4cPy79u2rdsrIYpcfLwcGXzZb88eOdodfAHOzfmqrZWr
Dl98sXw8ZIic27jd0b+OHQNmzgSuukqCTBXnnRd9xxdnfBEREZFTfB18deggw+D9HnzFx8s2gVCj
RwP5+XJ1JfK38nJ2e5F/sePLOQUFcnQi+HLqyo5ffCFdalbw1bGjdChzwL1/vfUWsG2bWreXJT1d
7qO0VO37GXwRERGRk3wdfBmGPOn281bHI0cad3sBwEUXAe3aSdeX07Zv3+78g2isvJyD7b2Ada4m
Lk7OtQy+7OdE8NW9O9Cli3R82VHztbXAL34B/OMf0hm0cqW8WTNqVN1t0tLY8eVXtbXS7XXllXKh
AlXnnSfH9evVvt+u4IvnedINa550w5onVb4OvgAJvvze8dVU8NWpkzyRjMWcr2nTpjn/IBo7fJjB
lxewztUYhrwgra52eyXBU1Ag5//ERPvu0zDqruxoR83/61/AU08Bd9whc5xeekmCrtDfW2lpwJdf
ypUeyV/eekv+7aLp9gKAk04CUlLUtzvaFXzxPE+6Yc2TbljzpMr3wVenTv4Oviorm7+S0ejRwEcf
ATU1zq5h1qxZzj6A5rjV0RtY5+oSEtjx5YSCAqB3bwmr7GRd2dGOmv/zn6UTaONGoH9/YPNm4LLL
6t9m5EiZR7lpU9QPRzFkdXtlZNTv4FNhGOpzvkzTvuCL53nSDWuedMOaJ1W+D76CutURkODr4EHg
00/rf76iQt6ltQsvC+ssbnX0Bta5OgZfzigosHebo8Xq+Iq25rduBVasAH76U2DECGDJEpnx9f/+
X/3bnXaanOO43dFf3nlH/j2j7faynHeezHqL9M26mhoJv+wIvnieJ92w5kk3rHlS5fvgy66Or9/8
BvjDH6K/n0i1FHwNHy5bYBrO+XrhBeB73wP27XN+fRQ9bnUkv2Pw5Qyng69orwr85z/L+m68se5z
Z5xRd0VlS9u2EoytWhXd45GzKiqAOXNkXtt77wEzZgBjxtTN54rWeefJY3z+eWTfZ51bONyeiIiI
nBKI4MuOjq9//Qv4+OPo7ydSLQVfcXHApZc2nvP1zjt130vex62O5Hfx8Qy+nOBk8HX4cHRvjuzd
C/zzn8CkSXKhldZcdx2wbBnfkPGyf/0LuOsumdd27bXS7TV9un33P2yY1Eqk2x0ZfBEREZHTfB98
2TXcPjcX2L8/+vuJVEvBFyDbHdetk/AEAIqKgKws+btdL0QfffRRe+6ImsStjt7AOlfHji9n7Nnj
XPAFADNmqNf83/4mx3vuCe/2N90kM6Peflv5IclhBQUyU7SiQp5L7N5tX7cXIPc9bJg8Z4lEZWXd
90eL53nSDWuedMOaJ1W+D77s2OpYVgYcOACUltqzpki0NNwekODr6FFg9Wr5eOHCuu0rdl1lrcLP
Q9J8gFsdvYF1ro7Bl/0OH5bfPU4GX0VFajVfVQXMng3cdhvQo0d439OrF3D55cDcuUoPSTFQVASk
psqbbSkpcmEFu51/vlyU59ix8L/Hzo4vnudJN6x50g1rnlT5PviyY7h9bq4cvdjxNWgQ0K9f3XbH
d94BkpLk73a9EJ0xY4Y9d0RN4lZHb2Cdq0tIsC9oJ7FnjxydCL6SkuScM3KkWs3/6ldASQlw//2R
fd/48cDKlUB+vtLDksOs4MtJN98stb10afjfY2fwxfM86YY1T7phzZMq3wdfdnR85eTI8cAB2aoR
S60FX4YhXV/Ll8v6VqyoGzTMDgx/4FZH8jt2fNmvoECOTgRfhlE34D5S778PPP008MQTwOmnR/a9
3/2uzIObPz/yxyXnxSL4Gj4cOPfcuq2y4eCMLyIiInJaIIKvaDu+rBcHpilbT2KpteALkOBryxbg
xRflst+33CKf5wtRf+BWR/I7Bl/2czL4AtSCr/x84M47gcxMYPLkyB8zMRG4+mpud/SqwkLngy/D
kLlw779f19XYGgZfRERE5DTfB192DLe3tjoCjed8HT3qbBhWWdl68HX55XKcORMYORI46ST52K4X
onv37rXnjqiR6mr5w62O7mOdq2PwZb+CAjkvdOnizP2fdhqweXP4NV9TA9x6q/xOfeklCTBUjB8P
bNoEfPWV2veTc4qKZBab0267TTr/Xn45vNvbGXzxPE+6Yc2TbljzpMr3wZddWx179pS/N5zz9dRT
wIUXRnf/LTlypPUrGaWmAuecAxw6JFtJrCeHdr0QnThxoj13RI1YtcmOL/exztUx+LJfQYFz3V6A
DBnfvXsidu0K7/YPPwysWQO8/jqQnKz+uFdfLWEeu768xTSB4mLnO74A6fy76SbpUg9nfISdwRfP
86Qb1jzphjVPqnwffNk13H7IEPl7w46vb78FduyI7v5bEs5WR0C2OwLA9dfLO6mAfS9Ep0+fbs8d
USMMvryDda4uPp7Bl91iEXwB07FmTeu3/egjCb5mzIj+jZ4OHeQNmtdfr7sCMbnvwAHpPo5F8AUA
d98N7NwJfPhh67e1M/jieZ50w5on3bDmSZXvg69OnWQ74tGj6veRk1MXfDXs+CopkfDCqRd94QZf
kyZJ99kpp9Q9ObTrKmtDhw61546okfJyOXKro/tY5+rY8WU/p4OvlBRg0KChWL265duVlADf/z5w
ySXAAw/Y89i33gp88w2QnW3P/VH0iorkGKvg67zzgDPOCG/IvZ3BF8/zpBvWPOmGNU+qAhF8Aepd
X+XlwL59wFlnAXFxjTu+Skrk2PDzdgk3+DrpJOBnP5O/273VkZxjBV/s+CI/S0iwL2gn4XTwBUj3
VlZW81+vrZVh9tXVwD//CbRta8/jXnaZBG+vv27P/VH0Yh18GYZ0fb37bt3zqOZwuD0RERE5zffB
V8eOclSd82UNth84EOjevXHAVVwsx3371O6/JbW18oIjnOArVFwc0KYNgy8/4FZHCgJ2fNnLNGMT
fF1wgVwR+MCBpr/+9NPAv/8NvPKKvWuJi5MZT/PmAceO2Xe/pK6wUI6xGG5vuf12CcBeeaXl21VW
ypHBFxERETnF98GX1fEVbfA1YACQlNT0VkfAmeDLerLX2nD7ptj5QnTOnDn23BE1wq2O3sE6V8fg
y16HDsnvLKeDrz175sA0gXXrGn/tk0+AX/0KuP9+YOxY+x/71lsl3Fu1yv77psgVFcn/x127xu4x
k5OBG26QIfctzXurqpKw1I6OQ57nSTesedINa55U+T74sjq+VLc65uTIE64+fRp3fB09WvdOuRPB
15Ejcoy04wuw94VoNgexOIZbHb2Dda6OwZe9Cgrk6HTwtWtXNlJT0WjOV1kZcMstwODBwB/+4Mxj
jxolndS8uqM3FBXJNkfDiO3j3nMP8NVXjWswVFWVfd1ePM+TbljzpBvWPKnyffBlR8dXv37yTmPD
jq+9e+v+HuTga/bs2fbcETVi1aUV0JJ7WOfqGHzZa88eOfbu7ezjPPfcbFxwQf05X6YJ3Huv/H6b
N6/uKsF2Mwxg/HjgrbdYO15gBV+xdvHFclGeF15o/jZ2Bl88z5NuWPOkG9Y8qQpM8BVNx9fAgfL3
hh1foQNZvRZ8xcfzxYQflJfLv69dQ6OJ3MDzjb2sji+ngy9A5nxt3Fj37/fcc8D8+RJEnHSSs499
663yZtLSpc4+DrXOreDLMIC77pIAtLmLBNkZfBERERE1xffBV7TD7UODr4YdX1bw1a6dM1d1tGZ8
qXZ88Spr3ldezm2O5H/s+LJXfj6QmBibc8OFF8q/3aZNwKJFwE9+Avz0p8DNNzv/2GedBZx9Nrc7
ekFhYWwH24f6wQ/kIgf//GfTX2fwRURERE7zffBlx1bHAQPk70lJ9QMu64qOp5zibMeX28PtyTmH
DzP4Iv9j0G6v0N87Tjv3XPk9OWuWhF2ZmcCTT8bmsQHZ7rhwYd28Q3KHWx1fgDzuddcBf/tb00Pu
GXwRERGR03wffFndUipbHY8ckSeDoVsdG3Z8JSTICxSvbXW0M/jKzMy0546okfJyXtHRK1jn6hIS
gNpaoKbG7ZUEQ14e0L+/84+TmZmJuDggPV26rs46C3jttdhuvb7lFvldt3Bh7B6T6jNNd4MvALj7
bmDrVmDDhsZfszP44nmedMOaJ92w5kmV74OvNm0kOFLp+MrLk2Nox1dFRV2gVFIC9Owpl+QOcvA1
efJke+6IGuFWR+9gnauzXpSyy9QesQq+rJq/6SbgnHOA99+P/YU2TjwROO884PXXY/u4VKesTDo2
3Qy+Ro+WNxmbGnJvZ/DF8zzphjVPumHNkyrfB1+AdNSodHzl5MgxtOMLqOv60iX4ysjIsOeOqBFu
dfQO1rk6Bl/2itVWR6vm774b+OwzICXF+cdsyvjxwLJl9a+UTLFTVCRHt2Z8AfIm5V13yYUVDh6s
/zU7gy+e50k3rHnSDWueVAUi+OrYUa3jKzdXnoydcIJ8nJQkR2vOV0mJvFBwKviKdrg9X4R6H7c6
UhAw+LJPWZm88I9Fx1cow4jt44X63vdku91bb4V3+w0bZBg62cMKvtzs+AKACRPkHNKw+6+qSm3W
KREREVG4AhF8deqkFnzl5AB9+8pVG4GWO75KS5seyhqNaIbbx8fzRajl0CFg1Cjg22/dXklj3OpI
QRAfL0eec6JnbbGPdfDlptRU2eoWznbHrCw5n3/0kfPr0kVhoRzdDr769AGuvlqG3IeqrORweyIi
InJWIIKvjh3Vtjo23G7SsOOruLgu+KqpkYDFTkeOSOimMmjYzqusLViwwJ47csn27dIh8Omnbq+k
MW519A6/17mb2PFln4azJZ3kpZq/9VZg9Wpg1y75eMkS2fpmvQFkeeYZORYUxHZ9QVZUJOF1YqLb
K5Ftt9nZwKZNdZ+zc6ujl2qeKBZY86Qb1jypCkTwpdrxtXNn3XwvoK7jK3SroxV8AfZvdzxyRG2b
I2DvVse5c+fac0cusV5I7tnj7jqawq2O3uH3OneT9aLUrrBdZ7m5QFxcbOYteanmr7tOuptffBH4
8Y+Bq64C5sypC7oAYPdu4J135O+cB6buT3+SrjmrS926oqOb210tV14pnfahXV92Bl9eqnmiWGDN
k25Y86RK2+Br/37gk0+AtLS6z8XHy33t3y8dXqWlEnxZnWBBDb7mz59vzx25xAq+rO0cXsKtjt7h
9zp3Ezu+7JOXJy/8VTp9I+Wlmu/aFRg3Dpg5E3j1VeC554BJk4A//rHud+tf/iK/E1NSGHypOnYM
eOop6YL+4gv5XFGRu4PtQ8XFARMnyrbX8nL5nJ3Bl5dqnigWWPOkG9Y8qQpE8KWy1fHdd+UJ4g03
1P989+4SeFlPxJ3s+Kqs9Ebw5Xe5uXJk8EXkDAZf9snLi802Ry+aOlUG3X/2mXR9/e538nv4D3+Q
2nrhBeDOO2X+GYMvNUuWAPn5EjC9+658zur48orbb5fREdYcNzuDLyIiIqKmBCL4Uun4euMN4KKL
gN69638+KUk6vkpK5GMdtjr6nZc7vjjji4KAwZd9cnP1GmwfKi1Nfveecop8nJICTJsGzJoFPP64
zNWcNAno0YPBl6q//Q0YPFje1LOCr8JCbwVf3/mOhL8rVsjHDL6IiIjIaYEIviLt+Nq3D1i+HLjp
psZfszq+rOArJUWCtfh4Z4Iv1Ut4M/iq49Xgq7oaOHqUM77I/zp2lKPKLEWqLy9P3+CrKb/4hbzh
9OCDwJgxwGmnMfhSVVAALFokA+Svvx7YvFmuXu21ji/DAC6/HPjwQ/mYwRcRERE5LRDBV6QdX+++
K0NfG25zBOo6voqL5eOePeVJWnKytzq+4uPtC74mTJhgzx25JDdXXph7Lfiy5pew48sb/F7nbrKu
BldW5u46/O7oUQknYrXV0Q8136kTMGOG/H3KFDky+FLz8svy3OC22+TiAfHxwIIF3gu+AOCyy4At
W+S5lp3Blx9qnshOrHnSDWueVGkZfL3xBnDJJU0/EQzt+GrXTgbyAhJ8WVd7tItXtjpmZGTYc0cu
qKiQF0jDhsm/WU2N2yuqY9Ukgy9v8HOdu619ezkfMviKTkEBUFsbu44vv9T8XXfJvKdx4+RjBl+R
q62Vq2TefLME1V27AqNHA3//uzxX8Mpwe8tll8nxo4/sDb78UvNEdmHNk25Y86QqEMFXJFsdS0qk
vb6pbY5A/RlfVrcX4EzHV7TD7aur7VnH+PHj7bkjF+zaJce0NOnis7aoeoHV8cWtjt7g5zp3m2HI
i2kGX9GxLsQRq+DLLzXfpo28GWX9vu3RQ37f1ta6uixfWbEC2LlTtjlarr8e+M9/5O9e6/jq3Rs4
/XRZd1WV+tiHhvxS80R2Yc2TbljzpCoQwVckHV/WNsfvfrfpr4d2fPXsWfd5r2115IwvYc33GjlS
jl7a7sitjhQkDL6iZ52vOOOrZT16SOh14IDbK/G+Y8eAF18Evv994OyzgfT0uq9lZkqoCHgv+ALq
5nxVVnLGFxERETkrEMFXx47S/RTONrc33pAW+9BQK1TojK/Q2yQleXO4vWnauya/yc2VLoFhw+Rj
LwVf3OpIQcLgK3p5efImCrtAW9ajhxy53bFlq1YBI0ZIl9fo0cDixXVdc4BcnOf88+XvXgy+LrsM
+O9/GXwRERGR8wIRfFkvIlrb7lhUJPMkmtvmCEjH17FjwI4d8qTR4sWOL9O0Z6ZVVlZW9Hfikrw8
2TLRt6987KXgi1sdvcXPde4FDL6il5sb224vv9Y8g6+W5eTI85iLLwbi4oC1a4HXXgNOOKHxbceP
l/+e3brFfJmtCt3ealfw5deaJ1LFmifdsOZJVaCCr9a2O77zjjzJuv765m+TlCTHr77y/lZHwJ7t
jo899lj0d+KSvDx5IRkfL/9GXgy+2PHlDX6ucy9g8BW9vLzYXdER8G/NM/hqWnk58NvfAqedBmRl
Aa+8AqxfX397Y0M/+hHwzTf1O8G8ont3YOhQ+btdwZdfa55IFWuedMOaJ1WBCL46dpRjax1fb7wh
MyWsJ9VN6d697r4aBl8HD8rl6O0SzXD7+Hg52hF8zZs3L/o7cUlubt0LyV69gD173F1PKCuIteqT
3OXnOvcCBl/Rs4L6WPFrzVtvQDH4ErW1wKuvAoMGAU88Afzyl8DXXwN33FE3w6s5huHNbi/L5ZfL
0a7gy681T6SKNU+6Yc2TqkAEX+F0fBUWAitXtrzNEah7wg00Dr4Amf9lF690fHX0cTIT+kKyd2/v
dXx17Nj6CxOKDT/XuRcw+IqOacZ+q6Nfa75dO3kTisGXuPZa4Ac/AC64ANi+HXjkkeB0El92mRzt
Cr78WvNEqljzpBvWPKkKxEvycDq+3n4baNu25W2OQF3HF9B08GXndsdoh9sDMtRfV7W1wK5ddS8k
e/XyXvAVlBcnRAy+orN/v7w5wys6hqdHDwZfgMwmXbQIeO456VofONDtFdnr4ouBe+8Fhg93eyVE
REQUZIEIvsLp+HrjDWDMmPodXU1JTKybhRGL4MsLHV9+VVQkW09Dtzp6Kfg6fJjBFwVHYqJs9yY1
eXlyjOWMLz/r0QMoKXF7Fe5bs0aOmZnursMp7dsDf/lL/YsJEREREdlNi+CroABYvbr1bY6AbEuz
5mE4GXyZpoRWXgi+pk6dGv2duCA3V45e7vjiFR29w6917hWJicChQ9JpSZGzgq9Ydnz5uebZ8SWy
soATT2z6io3UmJ9rnkgFa550w5onVYEIvlrb6vj223LJ72uvDe/+rK6w0HcgrS2QdgVflZVy9ELw
1d+ne28avpDs1UtemLd2dc9Y4VZHb/FrnXtFYqIE9ocOub0Sf8rNlYuSxLKzxc81z+BLrF4ts70o
PH6ueSIVrHnSDWueVAUq+Gou8HjjDSAjo/78rpZ07y5BWeiVkNq1A7p2tS/4OnJEjl4IvqZMmRL9
nbggLw/o0qXu36lXLzkWFbm3plDc6ugtfq1zr0hMlCPnfKlZvRo47bTYXuzCzzXP4EvePNm8mcFX
JPxc80QqWPOkG9Y8qQpE8NW2rQRBTXV85efLVoFwtjlakpLkSbc168uSnAyUlka3Vku0wVd8vBx1
nvFlXSHN+neygi+ntzsePAi89BLw3/+2fDtudaQgYfClbtcu4J13gHvucXsl/lMrBiYAACAASURB
VMHgC9iwATh2jMEXERERUbQcCb4Mw+hsGMbThmHkGP+fvTuPl6qu/zj++rDLol5kTcMNNyQXcEMT
t0RFvS5plpoJVlbiUqZmVmBaCb/MDNE0UcsUd7HMFcwMJRdw14sLIKBiYCooKNv398fnHO/ce+fe
OzN39vN+Ph48hjtzZuZ7uB9mzvmcz/fzNVthZjPMbJeUx683s3WN/tzXlvfs1i19xdcdd3iSKJvG
sDU1Dft7xTbaKP8VX21d1THJia8FCxr2y8k18XXeeZmfkC5Y4Cchp5wCW20Fhx4K992Xvu+RpjpK
NVHiK3dXXeXfUSedVOqRVI5eveDDD30Bk6SaMcMvxG27balHIiIiIlLZClXxNRk4ADgBGAw8DEwz
s/4p29wP9AX6RX++0ZY3bC7xddttcNBBDacttubkk+Gss5ren8/EV756fK1alf7xEOD44+E//2n9
terq6nIbRIk1TnzV1PiU1GwSX088ARMm+DSk1jzzDOy+u/c4euYZuPZaf69DD/Uk2KWXNqwI1FTH
8lKpcV4ulPjKzcqVcM01nizv0aO4713JMd+rl9/mq8q6EsX9vYo5PbbSVXLMi+RCMS9Jo5iXXOX9
cMrMugBHA+eEEB4PIcwNIVwIvAF8P2XTz0IIS0II/43+tOl0qmvXplMdFyyAmTPhuOOye62DD4bR
o5veX4iKr0L1+Pr4Y5gyBb7zHVizpuXXOvfcc3MbRIktWACbblr/c7t20Ldv5omv1avh1FP9761N
qXnpJRg+HDbbzKefDB3qMfLMMx5jw4bBT3/qK2+dcgrMnq2pjuWmUuO8XCjxlZubb/bkzWmnFf+9
Kznm48RXUqc7rl7tF640zTE7lRzzIrlQzEvSKOYlV4W4jtgBaA80TsmsBFIP4fY1s/fMrM7MrjSz
nm1503QVX3fc4Qmiww9vyyvXq6TEV7zy2ksvwdVXt/xaV1xxRW6DKKGPP/aTycYLe/Trl3ni69JL
4dVX4fvf99dau7b5bW+7zZOrjzzScFU2M9hjD/jrX72Pz89/Dg8/7ImxOXNU8VVOKjHOy8l66/mi
H0p8ZS4EuPxyOOww2HLL4r9/Jcd8vhNf770Ht9+en9cqhuef92MaJb6yU8kxL5ILxbwkjWJecpX3
xFcI4WNgJvBzM+tvZu3M7ERgGBBPdbwfOAnYHzgX2Ae4z6xxO/nMpav4uu02OOQQX40xH8op8dWx
o982l/hatsxvBw/2ZExL467EZWHfestvc018vfkmXHgh/PCH8JWveI+uDz5ofvtp0+CAA1r+ffXp
41Vfc+d6I+ujj/bnSHmoxDgvJ2Ze9aXEV+b+9S948UU488zSvH8lx3y+E1/jx8PXv56+H2M5mjHD
e4AOHVrqkVSWSo55kVwo5iVpFPOSq0J1jjgRMOBt4FNgDHAzsA4ghHBbCOHeEMLLIYS/AYcBuwH7
5vqGjSu+5s/3KWnZrObYmo039qvGv/992w+e29rc3syrvlpLfP3ud17JNHZsbu8DcM89sPPOuT+/
EJ56yv8NBg1qeH+/fvDuuy0/NwT4wQ88UTVuXP1CBs2dYH30kb9fpkmsDh3gqKPgzjth770ze45I
JVDiKzuXXw7bbw/771/qkVSeDTf0FZvzkfgKAe6+27+342rocjdjhveUjFdwFhEREZHcFSTxFUKY
F0LYD+gGfDGEsAfQCZjb3PbAUmBgS687cuRIamtrG/wZNmwYU6dObZD4euihhzj00Fq6dPEpJrHT
TjuNyZMnN3jN2bNnU1tby9JGR9djx45l/PjxDe4bPnwBm25ayw9/WMc++8Abb/j9EydO5Jxzzmmw
7YoVK6itrWXGjBkN7p8yZQqjRo1q0tz+uOOOY+rUqQ22feihh6hNsxxlvB+dOtUnvhrvR5z4uvfe
sXz5y+O56iqvPABYsGABtbW1TZoDNrcfp59ey3PPzfh8zKn70Vgu+5Eq09/H9OkwePACRo1quB/9
+8Mbb7T8+7jlFnjoIZg0Cf72tyn87ne+H0uWpN+Pf/3Lk4edO+d/PyD730dLcdVYsX4f2o9k7Eec
+Kr0/YgVcj/OO288f/sbnHGGJ+krdT9K9fto186rrGfOzG4/Dj+8lkWLGu7H9743lvnzfT/iyt5y
/n0888xs/v73WoYMKZ/fRy77UY5xpf3Qfmg/tB/aD+2H9qNy9+Pss89ukgs68MADm2ybVgih4H+A
GuAD4JRmHt8EWAsc1szjQ4Awa9as0JwTTwxh773rf95llxCOPrrZzdvk0UdD2GKLENZbL4Tf/z6E
tWuzf43rrgsBQlizJvdx9OoVwq9+lf6xO+/013///RA++yyEbbYJYf/9Q1i3rum2l1xySYvvs/XW
/lrvvJP7WPNp3boQ+vYN4bzzmj42aVIIHTs2/zv53/9C6NMnhGOOqb9vyRLfv7vuSv+c008PYfPN
2z5uKa3W4lxat+++IRx/fKlHURnOPjuEmpoQPvmkdGOo9JgfNCiEs87K7jljxvj3f+p33dix/hkP
ITz7bF6H2MBf/hLCL36R/ns2Gw8+6GOdMSM/40qSSo95kWwp5iVpFPPS2KxZswIQgCGhhZxUQSq+
zGyEmR1kZpuZ2YHAI8ArwA1m1s3MJpjZ7ma2qZkdAEwFXgMezPU9Uyu+5s711faOPbbt+5LOPvvA
Cy/At78NZ50F++5bX/2VqZUrvU9X+/a5j6NzZ1i1Kv1jccVXjx4+VeKyy7wx+913N912RePmaCmW
LoXXXvO/t9QDq5heftmnnKabetivn6+G1dxYf/IT+PRTn4IUq6nxiozUiq9U06Z5HzCpbC3FuWRG
Ux0z8/HHcO21vqpu166lG0elx3yvXtlPdXzkEf/+v/fe+vvuvtunDULhvsfeestXCf7lL+Gaa9r2
WhMnwo47wp575mdsSVLpMS+SLcW8JI1iXnJVqB5fGwCTgFeBG4DHgINDCGvxyq4dgHuAOcCfgKeB
4SGE1bm+Ydeu9YmvW2/1n/O1mmM63brBH/4Ajz4Kb78NO+zgP2fa+2vlytwb28da6/HVpUt9E/xD
DoGRI+Hss2kwZRHgwgsvbPY9Zs6s//v//te28ebL9Om+7+lWu+rXz2/TNbh//HE/IfnNb+ALX6i/
v317n1KT7gTr7bd95UclvipfS3EumVHiKzM33ui9pH7wg9KOo9JjPtvE17Jl/nnduTNcfLHXeM2d
6xeqRo/2bT78sDBj/dGP/CLKqFE+vfXpp3N7nblz4R//gNNP9wsykp1Kj3mRbCnmJWkU85KrQvX4
uj2EMDCEsF4IYeMQwpkhhOXRY5+GEA4OIfQLIXQJIWwRQvh+CKGZepvMdOtWv6rjlClQW+v3FVpc
/XXKKb5y1377+YqB6Xz2mR+Igye+cm1sH2st8dV4NcvLLoNFi+DSSzN/jyeeqK9YKJeKr2nTYK+9
0icOm0t8rVoF3/2uX/U/9dSmz+vVK33F1/Tpfqvm1CJKfGUiBL8IctRRsOmmpR5NZcs28fX00/7v
f8klviDJtGle7dWlCxx3nG9TiO+xBx/0lXwvvRSuugp22gmOOSa3VaCvvNITaMcfn/9xioiIiCRV
oSq+ii6e6vjyy97E/RvfKO57T5wI//wnLFzo1V8TJzas/poyxVcPjJNOn35a2Iqv5cubJr623tqT
c7/+tVcyZeLxx+unFJZDxdfq1V5l19wKi3Hiq/HV9t/+FubMgauvTj+9tHfv9CdY06b5ipa9erVp
2CJVQYmv1j38MNTVedWPtE1zFySa8+STHqNnnAG77OJVX3ffDQce6Pd3757/iq/PPvPqrP328+Ra
585w++1+PHLCCb4wSqY++QQmT/YLaW09PhARERGRelWT+Ora1Su+br3VD3APOqj4Y9h33/opFWec
4QfCL77ovcCOP94PiP/0J78iXYypjo0TXwA//7kf/J93Xv19jVdoiK1a5Qmk/fbzf99yqPh6+mnv
n9Pc1MOuXWHMGPjFL+qnab7xBlx0kU9F2XHH9M9Ld4IVgvp7VZPm4lwyp8RX6/7wB/+c2XvvUo+k
8mM+24qvJ5+EXXf1FSF/9jN47DG/eHPUUf54TU3+v8cuuwzmzYMrrqifmjhgANx8s68efPHFmb/W
TTf5d3epp8hWskqPeZFsKeYlaRTzkquqSXx16+ZVVDffDEcf7UmhUujevWn11803w3XX+UHta695
4918JL46dco+8bXBBl7xddNNPo0RYHTc/KSR557zf9M99yzMCUMupk3zfRg6tPltLr0UdtsNvvpV
ePddP4no2xfGjm3+Oekqvl591Z+vxFd1aC7OJXMbbOCfLZn2Mkya11/3/kxnnlke/ZkqPeZ79fIq
qJUrW982BE98xU3sDz8cvvQlT4LF/T433DD/FV933+0L6Qwa1PD+ESPgwgv9zwMPZDb+K67wsW62
WX7HmCSVHvMi2VLMS9Io5iVXVZP4ivtQvflmcac5Nieu/powwRNdo0b59Lx+/bzxcakqvsDHMnSo
V6WtWwfjxo1Lu90TT3hvlJ139sRXOUx1nDbNK9BaWg2zUye44w4/8dxtN596dOWVLfd8S1fx9dhj
0KFD+ib6Unmai3PJ3AYb+An6xx+XeiTl6Yor/LOkHL6DoPJjPp5inkmvrAULfLXfOPHVrp1/7o8f
X/86hbiA8/rrMHhw+scuuAAOPtinPL71Vsuv88wzXiGuaq+2qfSYF8mWYl6SRjEvuaqaxFec1Ojd
2xMj5aB7dzjnnPorwe3b+5THW27xHlz5aG6/alX6x1pKfLVr59NxZs2CG26AIUOGpN3uiSd82kin
TtCzZ+krvj7+GP7zn8wqsPr1gzvv9BOhY47xFS1bkq7i6803vTl1nFSVytZcnEvmNtjAbzXdsall
y+D6633xjLZ+tudLpcd8nLDKZFbDk0/6bZz4Ar9o8eMf1/+c74qv99/378Wttkr/eLt28Ne/Qo8e
/j3U3IUq8Ob4G22khVTaqtJjXiRbinlJGsW85KrqEl/HHutVOuXqxBO9sujhhwtf8dWjR/PP3XNP
T8Kdf75v21gI3htlzz3953Ko+Pr3v725faZTD/fYwxc7uPHG1rft1ct7xMUrg4JfodeqbCL1lPhq
3g03eCXv979f6pFUj2wSX//5j08R7NOn+W3yXfH1+ut+21ziC/yi0Z13egX4WWel3yYE3+bII8v7
+EVERESkUlVN4qt3b7894YTSjqM1O+3kFWDLlpVuqmNs/HivopowoeljCxbAO+/UJ77KoeJr2jTY
eGNfnTJTW22VWfVFHD+pJ1jz56vXikgqJb7SW7fOezsec4x/Rkl+xImvm2/26t2WpPb3ak6+K77i
xNfAgS1vN3SoT4P94x/hL39p+vjLL/trHX10/sYmIiIiIvWqJvG1ww5+4BgnasqVmVd9QekTX5ts
4lMA77prcpPH4sb3w4b5bTk0t58+3au9CtE0Oj7BSu3zpcRXdZk8uWmcS3aU+Erv/vt99dgzzij1
SBqq9Jjv0cNX6L31Vl8pcdQoeP75ptutXg2zZ7ee+Mr399hrr0H//t7WoDXf/jacfDJ873te/ZXq
zjv9+/qAA/I3tqSq9JgXyZZiXpJGMS+5qprEF7R+1bVcHH+83xYy8bV8eeuJL/BeWO+9N7vJ/c89
59P84kqoUk91/O9//YSnUCssNq74+uQTT4Ip8VU9Zs9uGueSHSW+0rvySu+HuMcepR5JQ9UQ8xde
CIsWwUUXedXvTjt5gujvf69fXfSFF3wF4lJUfLU0zTGVGUya5BXLX/1qw/9Dd90Fhx1WutWoq0k1
xLxINhTzkjSKeclVVSW+KsWmm8J3vtP26rROndInvj77zP9kkvjq2xc6dJjU5P7Fi70iLBZPdQyh
DQNug0ce8dtCNf5tXPG1YIHfKvFVPSZNahrnkp2uXX2RDiW+6sX9EI88sjDVqG1RLTFfUwPnngtz
58KUKT5Fv7YWtt3Wk0mPPOK9sXbeufXXWbmy5Sbz2Xj99eym3nft6isOL1ni1V8heKXgCy94Mkza
rlpiXiRTinlJGsW85EptVEvkmmva/hrNVXwtX+63mSa+li6FtWv9hDb27rteDRarqYE1a/yEo6Wm
+YUyfbr3RvvCFwrz+l27egVeXPE1f77fqrm9SD0zr/pS4qveO+/4v8fgwaUeSfXr2BG+/nX/M3Mm
XHaZTy9dt877aLVWRb3hhn774Yf+3dcWIXji67jjsnvewIHw5z97ovS3v/XXWW89OOigto1HRERE
RJqnxFcF69wZVq1qen+8SmOmia916zzhk3oisHhxwyvZPXv67QcfFD/xFYKvgnnEEYV9n9696yu+
5s/3CoJCJdpEKpUSXw299JLfKvFVXMOG+Z+33oKrr/bEV2tqavz2gw/anvj673/9IlOmUx1THXEE
/OQn/ucLX4BDDqlfmVpERERE8k9THStYcxVf2Sa+oOmKWYsXN634gtI0uJ87109uCtXfK9arV8OK
ry9+UUvLizSmxFdDL73kFaOaFl0am24Kv/51ZlMFUyu+2ipe0TGXxBd4z7J99vH+ZVrNUURERKSw
lPiqYK0lvjKpzPLEVy2LF9fft3q1J4DSJb5K0eB++nSfhrnPPoV9n9SKr7fe0olstamtrS31EKqC
El8NvfyyT8NuV4bfpor5hvJ5ASdOfG25ZW7P79ABbrnFV6086qi2j0ecYl6SRjEvSaOYl1yV4aG6
ZCp/FV9jGlR8LVni0wv796+/L3WqY7FNmwa77ZbZ/rRF44ov9feqLmPGjCn1EKqCEl8NvfRS+U5z
VMw3lM+Kr9de86rgtqzO3KePr1rZtWvbxyNOMS9Jo5iXpFHMS66U+Kpgza3qmE3ia731YP31RzRI
fMXVX6kVX/EJQ7ETX+vW+YpdhZ7mCE17fKniq7qMGDGi1EOoCkp81Vu3ziu+yjXxpZhvqFs3r7TK
V8VXNis6SnEo5iVpFPOSNIp5yZUSXxWsc2dfjXHt2ob3L1/u024yvYrcty+tJr7at/dEWrGnOj7/
PLz/PhxwQOHfK674WrnS/z2U+BJpSomvem+9BStWwPbbl3okkgkzv4iTrx5fufb3EhEREZHiUuKr
gnXu7LeNq76WLfMklVlmr9Nc4qtPn4bb9exZ/IqvadM8gbfHHoV/r969PbE3b57/rMSXSFNKfNXT
io6Vp6am7d9jIcAbbyjxJSIiIlIplPiqYHHia9WqhvfHia9MrVkztUniq1cv6Nix4XY1NcWv+Jo2
DYYPr9/XQurVy6cuPfus/6zEV3WZOnVqqYdQFZT4qvfSS/7vsfHGpR5Jeor5pvJR8fXOO17pp8RX
+VHMS9Io5iVpFPOSKyW+KlhrFV+ZWrJkSoPE17vvNpzmGCt2xddnn8G//12caY7gFV8AzzzjUzvL
9WRWcjNlypRSD6EqbLCBf8aEkNvz77kHTj01v2MqljVrGv780ks+zTHT6tpiU8w3lY+Kr3hFRyW+
yo9iXpJGMS9Jo5iXXCnxVcHylfg66aRbm1R8pUt85eOEIRszZ3q/rWI0tgev+AJPfG2yiTdBlupx
6623lnoIVWGDDbwy8uOPc3v+fffBddc1rVQtd6tW+Uq3N95Yf185N7YHxXw6NTVtr/h6/XXvo7nF
FvkZk+SPYl6SRjEvSaOYl1wp8VXBWkp89eiR+ev07eurGa5b5z+3lPgq5lTHadM8GbXDDsV5v7ji
a/ZsTXMUac4GG/htrtMdFy70yqm6uvyNqRhef90Xvxg3zse/Zg28+mp5J76kqQ03bPsFnNde8++I
Tp3yMiQRERERKTAlvipYfNDd1oqvvn19Zcj33/efm0t8ZTrVceVK2H9/2Gsv+PrX4dxzYf78zMcT
mz7dX6ddkaK0psanLK1YocSXSHPykfgCePHF/IynWF55xW/nzoVbbvHm5qtWaUXHSpOvii9NcxQR
ERGpHEp8VbB8TXXs29dv49Uc21rxdcUV3ptriy18tchJk+B3v8t8POAn1U89VbxpjuB9vTbayP+u
xJdIevlKfL3wQn7GUyyvvupVoYcdBr/6VX3iThVflSUfFV+vvgpbb52f8YiIiIhI4SnxVcGaS3wt
X55d4uvSS0cBnqT6+GP/01zF10cf1U+JTOfDD+E3v4Hvftd74fzzn/C1r8Fjj2U+HoBHH/X3KWbi
C+r7fG26aXHfVwpv1KhRpR5CVWhL4mv5cn9e+/aVWfE1aBBccIFP0/z1rz0R1qdPqUfWPMV8UzU1
rX+PteSDD3yq4y675Hdckh+KeUkaxbwkjWJecqXEVwWLE1+Nm0RnW/F12GEjAE98xU3u+/dvul1N
ja/k1tIJ7//9nyfifvaz+vuGD/fqjmyusk+fDptv7n+KKe7zpYqv6jNixIhSD6EqtCXxFVd77bln
5Sa+9tjDE/LPPVf+1V6K+aY23NCTXsuX5/b8p5/22913z9+YJH8U85I0inlJGsW85EqJrwqWr6mO
J5/8Dbp396RXPN2xuamO0Px0x8WL4fe/h7POapg422cfT5g9/njmY5o2rfjVXlBf8aXEV/X5xje+
UeohVIVu3XzxjAULsn9unPgaORIWLSruKrFtsWaNV/lst53/HCf2y72/l2K+qfh7LNc+X08+6ckz
9fgqT4p5SRrFvCSNYl5ypcRXBUuX+IqvZGeT+ALv89Va4qtnT79t7mT14ot9TOec0/D+zTeHjTeG
f/0rs7G8/bb3UClF4qt3b2+mv8kmxX9vkUpgBttu6/9Hs7Vggf//Ougg/7lSqr7mzfPP2UGD/Ofh
w+H88+HEE0s7Lsnehhv6ba5J1yefhN12K96iKyIiIiLSdjp0q2DpEl8ff+y3uSa+3n0XOnasvyqe
qqWKr7lz4eqr4Sc/qT+xiJn5iWKmfb4eecRv99sv8/HnyxZb+El9x47Ff2+RSrHddrklvhYu9GrQ
wYP9/1ilJL7iFR3jxJeZ9/jSdLfK05aKrxA88aXfu4iIiEhlUeKrgnXq5Lepia9ly/w2m8TXjBkz
GlR89evnJ3aNxScM6a6U/+IX3uR5zJj077HPPjBrVn1iriXTpsFOO9X32yqmH/4QZswo/vtK4c3Q
LzZv4sRXCNk9b+FC+OIXPem17baVk/h69VXvbZauEracKeabakvF17x5sHSpEl/lTDEvSaOYl6RR
zEuulPiqYOkqvuLEV48emb/OhAkTmiS+0ll/fV+NrfEJw/PPw803w9ix0LVr+ucOHw5r18LMmS2P
JYTS9fcCTyamq3aTyjdhwoRSD6FqbLedf9a8+252z4sTXwA77OCLXlSCuLF9ugsC5Uwx31Sc+Mql
4uvJJ/12t93yNx7JL8W8JI1iXpJGMS+5UuKrgrVrBx06tL3i65Zbbsko8WXmJw2NpzpecAEMHAgt
rS677bZewdVan685c+Cdd+CAAzIfv0gmbrnlllIPoWrETd6zne6Ymvj60pfgpZeyrxorhVdfrd/n
SqKYb6pDB+jePbeKryef9OnwpahGlswo5iVpFPOSNIp5yZUSXxWuc2dYtar+53iJ9mwSX127dv08
8fXOOy1P5+nZs+EJw4wZ8I9/eGP7lvpiZdrna9o0f5299858/CKZ6NpcOaJkbYstvDoy7n2ViRCa
VnwtXw5vvVWYMeZq/nxfse+NN/zndes88RX396okivn0ampyr/jSNMfyppiXpFHMS9Io5iVXSnxV
uM6d217xBZ7sWrvWK65aSnzV1NQnvkLwZvZDhsAxx7T+HsOH+4nDp582v820abDnntCtW3bjF5Hi
6dABtt46u4qv//0PVq5sWPEF5TfdceZMT3r97nf+88KF8MknlZn4kvQ23DD7iq9Vq+DZZ5X4EhER
EalESnxVuOYSX9n0+AJf1RFgxYrWE1/xVMf77oPHH/fVzTJZ2n34cD95eOqp9I+vWQOPPqppjiKV
INuVHRcu9Ns48bXxxp6AKLcG93V1fnvDDfD++/X7WIlTHSW9XCq+nn/ev2uV+BIRERGpPEp8Vbh0
ia+uXb0iI1PnnHPO54kvyGyq47p1cP75sO++MGJEZu/zpS/5ymiPPpr+8Vmz4KOPStfYXqrbOeec
U+ohVJW2Jr7MfLpjuSW+5syBwYO9ovXqq306Z9euMGBAqUeWPcV8erlUfD35pE/D32mnwoxJ8kMx
L0mjmJekUcxLrpT4qnCdOjVNfGU7zXHAgAEZJ77iiq8pU/yE9Te/yXyls/btvZrr/vvTPz5tmleq
7bpr5mMXydSASsxclLHttvO+gJkmEBYu9MRB6mfNl75UfomvujrYay846SSYOBGee873NZOq1nKj
mE8vl4qvp57ypFeXLoUZk+SHYl6SRjEvSaOYl1xV4KG8pEpX8ZVt4uv000+ne3evagDo37/5bXv2
hP/+F37+czjySNhjj+zeq7bWr5wvXtz0senTvYIsm2o1kUydfvrppR5CVcl2ZccFC2CTTRomkHbZ
xRNN8+fnfXg5WbfOK7623RbOOss/p6ZMqdxpjor59HKp+HrqKU1zrASKeUkaxbwkjWJecqXEV4VL
l/jKtr9XLK7ESK3IaKymxk8G33rLV3LM1qGHeoXYvfc2vH/FCu8XpmmOIpVh6639/3Kmia/UFR1j
xx7rnymXXZb/8eViwQJffGObbTzZNXKk9x5UY/vqkm3F19q1vuCB4kBERESkMinxVeE6d/aG8bFc
Kr5iffv6c1taJbamxm9POgm23z779+jVC778Zbjnnob3z5jh+6HEl0hlWG892Hxz74GViXSJr27d
4LTT4NprvZF8qc2Z47fbbuu3P/qR3w4eXJrxSGFkW/H13nue/GocvyIiIiJSGZT4qnCNK76WL88+
8VUXLWPWt2/L/b3AKyF69oRx47J7j1S1td7P65NP6u+7/36fYlmpU4qk/MVxLvmTTYP7dIkvgDFj
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
7MdAAVrJAAAAAElFTkSuQmCC
"
>
</div>

</div>

<div class="output_area"><div class="prompt"></div>


<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
n8ViAAAAAElFTkSuQmCC
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered">
<div class="prompt input_prompt">
</div>
<div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The ADX can be interpretted as follows:</p>
<ul>
<li><p>If $+DMI > -DMI$ then ADX represents the strength of the uptrend, however, if $-DMI > +DMI$ then ADX represents the strength of the downtrend.</p>
</li>
<li><p>Many traders look for an ADX &gt; some threshold to indicate that a commodity is no longer ranging and use this to effectively trend trade.</p>
</li>
</ul>
<p>We can see here why the ADX is such a powerful technical indicator.  At points where apple stock stops ranging and begins to move constistently in a given direction, the ADX often peaks.</p>

</div>
</div>
</div>
    </div>
  </div>
</body>




</html>
