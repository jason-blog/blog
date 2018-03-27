package SOMETH;<br />
<br />
import java.io.BufferedReader;<br />
import java.io.IOException;<br />
import java.io.InputStream;<br />
import java.io.InputStreamReader;<br />
import java.io.OutputStream;<br />
import java.io.OutputStreamWriter;<br />
import java.net.HttpURLConnection;<br />
import java.net.InetSocketAddress;<br />
import java.net.Proxy;<br />
import java.net.URL;<br />
import java.net.URLConnection;<br />
import java.util.HashMap;<br />
import java.util.Iterator;<br />
import java.util.Map;<br />
import java.util.Scanner;<br />
<br />
<br />
public class HttpRequestor {<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; private String charset = "utf-8";<br />
&nbsp; &nbsp; private Integer connectTimeout = null;<br />
&nbsp; &nbsp; private Integer socketTimeout = null;<br />
&nbsp; &nbsp; private String proxyHost = null;<br />
&nbsp; &nbsp; private Integer proxyPort = null;<br />
&nbsp; &nbsp; private String sessionId="";<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; /**<br />
&nbsp; &nbsp; &nbsp;* Do GET request<br />
&nbsp; &nbsp; &nbsp;* @param url<br />
&nbsp; &nbsp; &nbsp;* @return<br />
&nbsp; &nbsp; &nbsp;* @throws Exception<br />
&nbsp; &nbsp; &nbsp;* @throws IOException<br />
&nbsp; &nbsp; &nbsp;*/<br />
&nbsp; &nbsp; public String doGet(String url) throws Exception {<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; URL localURL = new URL(url);<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; URLConnection connection = openConnection(localURL);<br />
&nbsp; &nbsp; &nbsp; &nbsp; HttpURLConnection httpURLConnection = (HttpURLConnection)connection;<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; httpURLConnection.setRequestProperty("Accept-Charset", charset);<br />
&nbsp; &nbsp; &nbsp; &nbsp; httpURLConnection.setRequestProperty("Content-Type", "application/x-www-form-urlencoded");<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; InputStream inputStream = null;<br />
&nbsp; &nbsp; &nbsp; &nbsp; InputStreamReader inputStreamReader = null;<br />
&nbsp; &nbsp; &nbsp; &nbsp; BufferedReader reader = null;<br />
&nbsp; &nbsp; &nbsp; &nbsp; StringBuffer resultBuffer = new StringBuffer();<br />
&nbsp; &nbsp; &nbsp; &nbsp; String tempLine = null;<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; if (httpURLConnection.getResponseCode() &gt;= 300) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; throw new Exception("HTTP Request is not success, Response code is " + httpURLConnection.getResponseCode());<br />
&nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; try {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; inputStream = httpURLConnection.getInputStream();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; inputStreamReader = new InputStreamReader(inputStream);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; reader = new BufferedReader(inputStreamReader);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; while ((tempLine = reader.readLine()) != null) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; resultBuffer.append(tempLine);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; } finally {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if (reader != null) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; reader.close();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if (inputStreamReader != null) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; inputStreamReader.close();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if (inputStream != null) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; inputStream.close();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; }<br />
<br />
&nbsp; &nbsp; &nbsp; &nbsp; return resultBuffer.toString();<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; /**<br />
&nbsp; &nbsp; &nbsp;* Do POST request<br />
&nbsp; &nbsp; &nbsp;* @param url<br />
&nbsp; &nbsp; &nbsp;* @param parameterMap<br />
&nbsp; &nbsp; &nbsp;* @return<br />
&nbsp; &nbsp; &nbsp;* @throws Exception&nbsp;<br />
&nbsp; &nbsp; &nbsp;*/<br />
&nbsp; &nbsp; public String doPost(String url, Map parameterMap ,String sessionids) throws Exception {<br />
&nbsp; &nbsp; 	String keys = "";<br />
String cookieVal = "";<br />
<br />
&nbsp; &nbsp; &nbsp; &nbsp; /* Translate parameter map to parameter date string */<br />
&nbsp; &nbsp; &nbsp; &nbsp; StringBuffer parameterBuffer = new StringBuffer();<br />
&nbsp; &nbsp; &nbsp; &nbsp; if (parameterMap != null) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Iterator iterator = parameterMap.keySet().iterator();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; String key = null;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; String value = null;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; while (iterator.hasNext()) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; key = (String)iterator.next();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if (parameterMap.get(key) != null) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; value = (String)parameterMap.get(key);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; } else {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; value = "";<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; parameterBuffer.append(key).append("=").append(value);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if (iterator.hasNext()) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; parameterBuffer.append("&amp;");<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; System.out.println("POST parameter : " + parameterBuffer.toString());<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; URL localURL = new URL(url);<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; URLConnection connection = openConnection(localURL);<br />
&nbsp; &nbsp; &nbsp; &nbsp; HttpURLConnection httpURLConnection = (HttpURLConnection)connection;<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; httpURLConnection.setDoOutput(true);<br />
&nbsp; &nbsp; &nbsp; &nbsp; httpURLConnection.setRequestMethod("POST");<br />
&nbsp; &nbsp; &nbsp; &nbsp; httpURLConnection.setRequestProperty("Accept-Charset", charset);<br />
&nbsp; &nbsp; &nbsp; &nbsp; httpURLConnection.setRequestProperty("Content-Type", "application/x-www-form-urlencoded");<br />
&nbsp; &nbsp; &nbsp; &nbsp; httpURLConnection.setRequestProperty("Content-Length", String.valueOf(parameterBuffer.length()));<br />
&nbsp; &nbsp; <br />
&nbsp; &nbsp; &nbsp; &nbsp; if(!sessionids.equals("")){<br />
&nbsp; &nbsp; &nbsp; &nbsp; 	System.out.println("================");<br />
connection.setRequestProperty("Cookie", sessionId);<br />
}else{<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp;	for(int i=1;(keys=httpURLConnection.getHeaderField(i))!=null;i++){<br />
cookieVal = httpURLConnection.getHeaderField(i);<br />
cookieVal = cookieVal.substring(0,cookieVal.indexOf(";")&gt;-1?cookieVal.indexOf(";"):cookieVal.length()-1);<br />
sessionId = sessionId + cookieVal + ";";<br />
}<br />
}<br />
&nbsp; &nbsp; 	System.out.println(sessionId);<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; OutputStream outputStream = null;<br />
&nbsp; &nbsp; &nbsp; &nbsp; OutputStreamWriter outputStreamWriter = null;<br />
&nbsp; &nbsp; &nbsp; &nbsp; InputStream inputStream = null;<br />
&nbsp; &nbsp; &nbsp; &nbsp; InputStreamReader inputStreamReader = null;<br />
&nbsp; &nbsp; &nbsp; &nbsp; BufferedReader reader = null;<br />
&nbsp; &nbsp; &nbsp; &nbsp; StringBuffer resultBuffer = new StringBuffer();<br />
&nbsp; &nbsp; &nbsp; &nbsp; String tempLine = null;<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; try {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; outputStream = httpURLConnection.getOutputStream();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; outputStreamWriter = new OutputStreamWriter(outputStream);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; outputStreamWriter.write(parameterBuffer.toString());<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; outputStreamWriter.flush();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if (httpURLConnection.getResponseCode() &gt;= 300) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; throw new Exception("HTTP Request is not success, Response code is " + httpURLConnection.getResponseCode());<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; inputStream = httpURLConnection.getInputStream();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; inputStreamReader = new InputStreamReader(inputStream);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; reader = new BufferedReader(inputStreamReader);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; while ((tempLine = reader.readLine()) != null) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; resultBuffer.append(tempLine);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; System.out.println(resultBuffer.toString());<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; }catch(Exception e){<br />
&nbsp; &nbsp; &nbsp; &nbsp; 	System.out.println(e);<br />
&nbsp; &nbsp; &nbsp; &nbsp; 	System.out.println(sessionId);<br />
&nbsp; &nbsp; &nbsp; &nbsp; <br />
&nbsp; &nbsp; &nbsp; &nbsp; 	 &nbsp; if (outputStreamWriter != null) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;outputStreamWriter.close();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;if (outputStream != null) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;outputStream.close();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;if (reader != null) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;reader.close();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;if (inputStreamReader != null) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;inputStreamReader.close();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;if (inputStream != null) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;inputStream.close();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;System.out.println("yibangshabi");<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Map dataMap = new HashMap();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; dataMap.put("username", "Nick Huang");<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; dataMap.put("blog", "IT");<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; doPost("http://www.ddf.com/index.php?s=/Index_test", dataMap,sessionId);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; } finally {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if (outputStreamWriter != null) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; outputStreamWriter.close();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if (outputStream != null) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; outputStream.close();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if (reader != null) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; reader.close();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if (inputStreamReader != null) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; inputStreamReader.close();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if (inputStream != null) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; inputStream.close();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; }<br />
<br />
&nbsp; &nbsp; &nbsp; &nbsp; return resultBuffer.toString();<br />
&nbsp; &nbsp; }<br />
<br />
&nbsp; &nbsp; private URLConnection openConnection(URL localURL) throws IOException {<br />
&nbsp; &nbsp; &nbsp; &nbsp; URLConnection connection;<br />
&nbsp; &nbsp; &nbsp; &nbsp; if (proxyHost != null &amp;&amp; proxyPort != null) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Proxy proxy = new Proxy(Proxy.Type.HTTP, new InetSocketAddress(proxyHost, proxyPort));<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; connection = localURL.openConnection(proxy);<br />
&nbsp; &nbsp; &nbsp; &nbsp; } else {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; connection = localURL.openConnection();<br />
&nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; return connection;<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; /**<br />
&nbsp; &nbsp; &nbsp;* Render request according setting<br />
&nbsp; &nbsp; &nbsp;* @param request<br />
&nbsp; &nbsp; &nbsp;*/<br />
&nbsp; &nbsp; private void renderRequest(URLConnection connection) {<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; if (connectTimeout != null) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; connection.setConnectTimeout(connectTimeout);<br />
&nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; if (socketTimeout != null) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; connection.setReadTimeout(socketTimeout);<br />
&nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; }<br />
<br />
&nbsp; &nbsp; /*<br />
&nbsp; &nbsp; &nbsp;* Getter &amp; Setter<br />
&nbsp; &nbsp; &nbsp;*/<br />
&nbsp; &nbsp; public Integer getConnectTimeout() {<br />
&nbsp; &nbsp; &nbsp; &nbsp; return connectTimeout;<br />
&nbsp; &nbsp; }<br />
<br />
&nbsp; &nbsp; public void setConnectTimeout(Integer connectTimeout) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; this.connectTimeout = connectTimeout;<br />
&nbsp; &nbsp; }<br />
<br />
&nbsp; &nbsp; public Integer getSocketTimeout() {<br />
&nbsp; &nbsp; &nbsp; &nbsp; return socketTimeout;<br />
&nbsp; &nbsp; }<br />
<br />
&nbsp; &nbsp; public void setSocketTimeout(Integer socketTimeout) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; this.socketTimeout = socketTimeout;<br />
&nbsp; &nbsp; }<br />
<br />
&nbsp; &nbsp; public String getProxyHost() {<br />
&nbsp; &nbsp; &nbsp; &nbsp; return proxyHost;<br />
&nbsp; &nbsp; }<br />
<br />
&nbsp; &nbsp; public void setProxyHost(String proxyHost) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; this.proxyHost = proxyHost;<br />
&nbsp; &nbsp; }<br />
<br />
&nbsp; &nbsp; public Integer getProxyPort() {<br />
&nbsp; &nbsp; &nbsp; &nbsp; return proxyPort;<br />
&nbsp; &nbsp; }<br />
<br />
&nbsp; &nbsp; public void setProxyPort(Integer proxyPort) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; this.proxyPort = proxyPort;<br />
&nbsp; &nbsp; }<br />
<br />
&nbsp; &nbsp; public String getCharset() {<br />
&nbsp; &nbsp; &nbsp; &nbsp; return charset;<br />
&nbsp; &nbsp; }<br />
<br />
&nbsp; &nbsp; public void setCharset(String charset) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; this.charset = charset;<br />
&nbsp; &nbsp; }<br />
public static void main(String[] args) throws Exception {<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
<br />
<br />
<br />
<br />
&nbsp; &nbsp; &nbsp; &nbsp; /* Post Request */<br />
&nbsp; &nbsp; &nbsp; &nbsp; Map dataMap = new HashMap();<br />
&nbsp; &nbsp; &nbsp; &nbsp; dataMap.put("username", "Nick Huang");<br />
&nbsp; &nbsp; &nbsp; &nbsp; dataMap.put("blog", "IT");<br />
&nbsp; &nbsp; &nbsp; &nbsp; System.out.println(new HttpRequestor().doPost("http://www.ddf.com/index.php?s=/Index_test", dataMap,""));<br />
&nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; /* Get Request */<br />
&nbsp; &nbsp; &nbsp;// &nbsp; System.out.println(new HttpRequestor().doGet("http://www.ddf.com/index.php?s=/Index_test"));<br />
&nbsp; &nbsp; }<br />
<br />
}<br />