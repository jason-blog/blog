<p>
	cd  $(cd `dirname $0`; pwd)
</p>
<p>
	<br />
</p>
<p>
	cd &nbsp;$(cd `dirname $0`; pwd)<br />
<br />
<br />
svn update /www/svn22/SVN-250-REAL/ &gt; /www/svn-10.1.2.22/version.log<br />
<br />
<br />
rsync -av --delete --exclude ".svn" --exclude "/UserApp/Conf/" --exclude "/AgentApp/Conf/" --exclude "db.config.php" --exclude "/UserApp/Runtime/" --exclude "/AgentApp/Runtime/" --exclude "/RfcmsApp/Runtime/" /www/svn22/SVN-250-REAL/trunk &nbsp;/www/svn-10.1.2.22/<br />
<br />
chmod -R 777 /www/svn-10.1.2.22/*<br />
</p>