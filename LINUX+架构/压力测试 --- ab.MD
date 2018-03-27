ab -n 20000 -c 20000 http://www.dd.com/index.php<br />
<br />
<br />
<br />
ab -n 100000 -c 149 &nbsp;-H keywords:dt -p &nbsp;/root/file/param.conf &nbsp;-T 'application/x-www-form-urlencoded' &nbsp;http://cc-tt.chinacloudapp.cn/restaurant<br />
<br />
<br />
<br />
解释：-p:包含post请求的参数文件。文件内容类似：sk=1babb55a0b4b4dd2a&amp;apitype=restaurant&amp;p=tJoLaT4mon<br />
<br />
-T:content-type 。请求内容类型<br />
<br />
n:总请求数<br />
<br />
c:并发客户端数<br />
<br />
H:自定义消息头<br />
<br />
<br />
-C cookie1_name=cookie1_value; cookie1_name=cookie1_value;<br />
<br />
<br />
GET COOKIE:<br />
<br />
ab -n 100 -c 100 &nbsp;-C PHPSESSID=3a62f5485732929620cf3 http://www.ddf.com/user.php?s=/Index_ceshi_BBB_123456789<br />
<br />
post COOKIE DATA -T * no '' * -p userName=admin&amp;userPassWord=admin<br />
<br />
ab -n 100 -c 100 &nbsp;-T application/x-www-form-urlencoded &nbsp;-p D:\zend\DDF-SVN\trunk\P.conf &nbsp;-C PHPSESSID=3a62f5485732929620cf3 http://www.ddf.com/user.php?s=/Index_ceshi<br />
<br />
<br />
C:\xampp\apache\bin\ab -n 1000 -c 1000 &nbsp;http://www.dd.com/index.php<br />
<br />
<br />
&nbsp;Usage: ab [options] [http[s]://]hostname[:port]/path<br />
&nbsp; &nbsp; Options are:<br />
&nbsp; &nbsp; -n requests Number of requests to perform<br />
&nbsp; &nbsp; -c concurrency Number of multiple requests to make<br />
&nbsp; &nbsp; -t timelimit Seconds to max. wait for responses<br />
&nbsp; &nbsp; -b windowsize Size of TCP send/receive buffer, in bytes<br />
&nbsp; &nbsp; -p postfile File containing data to POST. Remember also to set -T<br />
&nbsp; &nbsp; -u putfile File containing data to PUT. Remember also to set -T<br />
&nbsp; &nbsp; -T content-type Content-type header for POSTing, eg.<br />
&nbsp; &nbsp; ‘application/x-www-form-urlencoded’<br />
&nbsp; &nbsp; Default is ‘text/plain’<br />
&nbsp; &nbsp; -v verbosity How much troubleshooting info to print<br />
&nbsp; &nbsp; -w Print out results in HTML tables<br />
&nbsp; &nbsp; -i Use HEAD instead of GET<br />
&nbsp; &nbsp; -x attributes String to insert as table attributes<br />
&nbsp; &nbsp; -y attributes String to insert as tr attributes<br />
&nbsp; &nbsp; -z attributes String to insert as td or th attributes<br />
&nbsp; &nbsp; -C attribute Add cookie, eg. ‘Apache=1234. (repeatable)<br />
&nbsp; &nbsp; -H attribute Add Arbitrary header line, eg. ‘Accept-Encoding: gzip’<br />
&nbsp; &nbsp; Inserted after all normal header lines. (repeatable)<br />
&nbsp; &nbsp; -A attribute Add Basic WWW Authentication, the attributes<br />
&nbsp; &nbsp; are a colon separated username and password.<br />
&nbsp; &nbsp; -P attribute Add Basic Proxy Authentication, the attributes<br />
&nbsp; &nbsp; are a colon separated username and password.<br />
&nbsp; &nbsp; -X proxy:port Proxyserver and port number to use<br />
&nbsp; &nbsp; -V Print version number and exit<br />
&nbsp; &nbsp; -k Use HTTP KeepAlive feature<br />
&nbsp; &nbsp; -d Do not show percentiles served table.<br />
&nbsp; &nbsp; -S Do not show confidence estimators and warnings.<br />
&nbsp; &nbsp; -g filename Output collected data to gnuplot format file.<br />
&nbsp; &nbsp; -e filename Output CSV file with percentages served<br />
&nbsp; &nbsp; -r Don’t exit on socket receive errors.<br />
&nbsp; &nbsp; -h Display usage information (this message)<br />
&nbsp; &nbsp; -Z ciphersuite Specify SSL/TLS cipher suite (See openssl ciphers)<br />
&nbsp; &nbsp; -f protocol Specify SSL/TLS protocol<br />
&nbsp; &nbsp; (SSL2, SSL3, TLS1 or ALL)<br />