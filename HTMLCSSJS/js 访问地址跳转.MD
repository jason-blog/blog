&nbsp;var port;<br />
(window.location.port)?port=":"+window.location.port:port='';<br />
var URL=window.location.protocol+'//'+window.location.hostname+port+window.location.pathname+"ja/"+window.location.search;;<br />
window.location.href= URL;<br />
&nbsp;//	cookieUtil.get('name');<br />
// console.log(window.location);<br />
console.log(URL);<br />