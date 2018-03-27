date=`date +%Y-%m-%d`<br />
<br />
filename=v_$date.zip<br />
<br />
filedir=/home/jason/Project/backup/<br />
<br />
#URL=<br />
URL=http://www.baidu.com<br />
<br />
wget &nbsp;$URL -O $filedir$filename<br />
<br />
<br />
#zip -Ppassword&nbsp;${filedir}s${filename} ${filename}${filename}<br />
zip -P123 -rj ${filedir}s${filename} ${filedir}${filename}<br />
<br />
rm -f ${filedir}${filename}<br />