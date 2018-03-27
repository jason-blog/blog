<pre class="prettyprint lang-html linenums">&lt;!DOCTYPE html&gt;
&lt;html xmlns="http://www.w3.org/1999/xhtml"&gt;
&lt;head&gt;
    &lt;meta http-equiv="Content-Type" content="text/html; charset=utf-8" /&gt;
    &lt;title&gt;&lt;/title&gt;
    &lt;style type="text/css"&gt;
        textarea {
            width: 300px;
            height: 300px;
        }

        .button {
            width: 100px;
        }
    &lt;/style&gt;
&lt;/head&gt;
&lt;body onload="init()"&gt;
    &lt;script type="text/javascript"&gt;
        //使用HTML5 Web存储的localStorage和sessionStorage方式进行Web页面数据本地存储。
        //页面参考如下图，能将页面上的数据进行本地存储。并能读取存储的数据显示在页面上。
        var t1;
        var t2;
        var oStorage;
        var oStorage;
        function init() {//初始化t1，t2
            t1 = document.getElementById("t1");
            t2 = document.getElementById("t2");
            sStorage = window.sessionStorage;
            lStorage = window.localStorage
        }
        function saveSession() {
            sStorage.mydata = t2.value;
            t1.value += "sessionStorage保存mydata:" + t2.value + "\n";
        }
        function readSession() {
            t1.value += "sessionStorage读取mydata:" + sStorage.mydata + "\n";
        }
        function cleanSession() {
            t1.value += "sessionStorage清除mydata:" + sStorage.mydata + "\n";
            sStorage.removeItem("mydata");
        }
        function saveStorage() {
            lStorage.mydata = t2.value;
            t1.value += "localStorage保存mydata:" + t2.value + "\n";
        }
        function readStorage() {
            t1.value += "localStorage读取mydata:" + lStorage.mydata + "\n";
        }
        function cleanStorage() {
            t1.value += "localStorage清除mydata:" + lStorage.mydata + "\n";
            lStorage.removeItem("mydata");
        }
    &lt;/script&gt;
    &lt;div&gt;
        &lt;textarea id="t1"&gt;&lt;/textarea&gt;&lt;br /&gt;
        &lt;label&gt;需要保存的数据: &lt;/label&gt;
        &lt;input type="text" id="t2" /&gt;&lt;br /&gt;
        &lt;input type="button" class="button" onclick="saveSession()" name="b1" value="session保存" /&gt;
        &lt;input type="button" class="button" onclick="readSession()" value="session读取" /&gt;
        &lt;input type="button" class="button" onclick="cleanSession()" value="session清除" /&gt;&lt;br /&gt;
        &lt;input type="button" class="button" onclick="saveStorage()" value="local保存" /&gt;
        &lt;input type="button" class="button" onclick="readStorage()" value="local读取" /&gt;
        &lt;input type="button" class="button" onclick="cleanStorage()" value="local清除" /&gt;
    &lt;/div&gt;
&lt;/body&gt;
&lt;/html&gt;</pre>