&lt;?php<br />
/**<br />
&nbsp;* 仿写CodeIgniter的FTP类<br />
&nbsp;* FTP基本操作：<br />
&nbsp;* 1) 登陆; 			connect<br />
&nbsp;* 2) 当前目录文件列表; &nbsp;filelist<br />
&nbsp;* 3) 目录改变;			chgdir<br />
&nbsp;* 4) 重命名/移动;		rename<br />
&nbsp;* 5) 创建文件夹;		mkdir<br />
&nbsp;* 6) 删除;				delete_dir/delete_file<br />
&nbsp;* 7) 上传;				upload<br />
&nbsp;* 8) 下载				download<br />
&nbsp;*<br />
&nbsp;* @author quanshuidingdang<br />
&nbsp;*/<br />
class Ftp {<br />
<br />
private $hostname	= '118.193.237.97';<br />
private $username	= 'tb4942422k183';<br />
private $password	= 'songjian';<br />
private $port 		= 21;<br />
private $passive 	= TRUE;<br />
private $debug		= TRUE;<br />
private $conn_id 	= FALSE;<br />
<br />
/**<br />
* 构造函数<br />
*<br />
* @param	array	配置数组 : $config = array('hostname'=&gt;'','username'=&gt;'','password'=&gt;'','port'=&gt;''...);<br />
*/<br />
public function __construct($config = array()) {<br />
if(count($config) &gt; 0) {<br />
$this-&gt;_init($config);<br />
}<br />
}<br />
<br />
/**<br />
* FTP连接<br />
*<br />
* @access 	public<br />
* @param 	array 	配置数组<br />
* @return	boolean<br />
*/<br />
public function connect($config = array()) {<br />
if(count($config) &gt; 0) {<br />
$this-&gt;_init($config);<br />
}<br />
<br />
if(FALSE === ($this-&gt;conn_id = @ftp_connect($this-&gt;hostname,$this-&gt;port))) {<br />
if($this-&gt;debug === TRUE) {<br />
$this-&gt;_error("ftp_unable_to_connect");<br />
}<br />
return FALSE;<br />
}<br />
<br />
if( ! $this-&gt;_login()) {<br />
if($this-&gt;debug === TRUE) {<br />
$this-&gt;_error("ftp_unable_to_login");<br />
}<br />
return FALSE;<br />
}<br />
<br />
if($this-&gt;passive === TRUE) {<br />
ftp_pasv($this-&gt;conn_id, TRUE);<br />
}<br />
<br />
return TRUE;<br />
}<br />
<br />
<br />
/**<br />
* 目录改变<br />
*<br />
* @access 	public<br />
* @param 	string 	目录标识(ftp)<br />
* @param	boolean <br />
* @return	boolean<br />
*/<br />
public function chgdir($path = '', $supress_debug = FALSE) {<br />
if($path == '' OR ! $this-&gt;_isconn()) {<br />
return FALSE;<br />
}<br />
<br />
$result = @ftp_chdir($this-&gt;conn_id, $path);<br />
<br />
if($result === FALSE) {<br />
if($this-&gt;debug === TRUE AND $supress_debug == FALSE) {<br />
$this-&gt;_error("ftp_unable_to_chgdir:dir[".$path."]");<br />
}<br />
return FALSE;<br />
}<br />
<br />
return TRUE;<br />
}<br />
<br />
/**<br />
* 目录生成<br />
*<br />
* @access 	public<br />
* @param 	string 	目录标识(ftp)<br />
* @param	int &nbsp;	文件权限列表 <br />
* @return	boolean<br />
*/<br />
public function mkdir($path = '', $permissions = NULL) {<br />
if($path == '' OR ! $this-&gt;_isconn()) {<br />
return FALSE;<br />
}<br />
<br />
$result = @ftp_mkdir($this-&gt;conn_id, $path);<br />
<br />
if($result === FALSE) {<br />
if($this-&gt;debug === TRUE) {<br />
$this-&gt;_error("ftp_unable_to_mkdir:dir[".$path."]");<br />
}<br />
return FALSE;<br />
}<br />
<br />
if( ! is_null($permissions)) {<br />
$this-&gt;chmod($path,(int)$permissions);<br />
}<br />
<br />
return TRUE;<br />
}<br />
<br />
/**<br />
* 上传<br />
*<br />
* @access 	public<br />
* @param 	string 	本地目录标识<br />
* @param	string	远程目录标识(ftp)<br />
* @param	string	上传模式 auto || ascii<br />
* @param	int		上传后的文件权限列表 <br />
* @return	boolean<br />
*/<br />
public function upload($localpath, $remotepath, $mode = 'auto', $permissions = NULL) {<br />
if( ! $this-&gt;_isconn()) {<br />
return FALSE;<br />
}<br />
<br />
if( ! file_exists($localpath)) {<br />
if($this-&gt;debug === TRUE) {<br />
$this-&gt;_error("ftp_no_source_file:".$localpath);<br />
}<br />
return FALSE;<br />
}<br />
<br />
if($mode == 'auto') {<br />
$ext = $this-&gt;_getext($localpath);<br />
$mode = $this-&gt;_settype($ext);<br />
}<br />
<br />
$mode = ($mode == 'ascii') ? FTP_ASCII : FTP_BINARY;<br />
<br />
$result = @ftp_put($this-&gt;conn_id, $remotepath, $localpath, $mode);<br />
<br />
if($result === FALSE) {<br />
if($this-&gt;debug === TRUE) {<br />
$this-&gt;_error("ftp_unable_to_upload:localpath[".$localpath."]/remotepath[".$remotepath."]");<br />
}<br />
return FALSE;<br />
}<br />
<br />
if( ! is_null($permissions)) {<br />
$this-&gt;chmod($remotepath,(int)$permissions);<br />
}<br />
<br />
return TRUE;<br />
}<br />
<br />
/**<br />
* 下载<br />
*<br />
* @access 	public<br />
* @param 	string 	远程目录标识(ftp)<br />
* @param	string	本地目录标识<br />
* @return	boolean<br />
* @param	string	下载模式 auto || ascii <br />
*/<br />
public function download($remotepath, $localpath, $mode = 'auto') {<br />
if( ! $this-&gt;_isconn()) {<br />
return FALSE;<br />
}<br />
<br />
if($mode == 'auto') {<br />
$ext = $this-&gt;_getext($remotepath);<br />
$mode = $this-&gt;_settype($ext);<br />
}<br />
<br />
$mode = ($mode == 'ascii') ? FTP_ASCII : FTP_BINARY;<br />
<br />
$result = @ftp_get($this-&gt;conn_id, $localpath, $remotepath, $mode);<br />
<br />
if($result === FALSE) {<br />
if($this-&gt;debug === TRUE) {<br />
$this-&gt;_error("ftp_unable_to_download:localpath[".$localpath."]-remotepath[".$remotepath."]");<br />
}<br />
return FALSE;<br />
}<br />
<br />
return TRUE;<br />
}<br />
<br />
/**<br />
* 重命名/移动<br />
*<br />
* @access 	public<br />
* @param 	string 	远程目录标识(ftp)<br />
* @param	string	新目录标识<br />
* @param	boolean	判断是重命名(FALSE)还是移动(TRUE) <br />
* @return	boolean<br />
*/<br />
public function rename($oldname, $newname, $move = FALSE) {<br />
if( ! $this-&gt;_isconn()) {<br />
return FALSE;<br />
}<br />
<br />
$result = @ftp_rename($this-&gt;conn_id, $oldname, $newname);<br />
<br />
if($result === FALSE) {<br />
if($this-&gt;debug === TRUE) {<br />
$msg = ($move == FALSE) ? "ftp_unable_to_rename" : "ftp_unable_to_move";<br />
$this-&gt;_error($msg);<br />
}<br />
return FALSE;<br />
}<br />
<br />
return TRUE;<br />
}<br />
<br />
/**<br />
* 删除文件<br />
*<br />
* @access 	public<br />
* @param 	string 	文件标识(ftp)<br />
* @return	boolean<br />
*/<br />
public function delete_file($file) {<br />
if( ! $this-&gt;_isconn()) {<br />
return FALSE;<br />
}<br />
<br />
$result = @ftp_delete($this-&gt;conn_id, $file);<br />
<br />
if($result === FALSE) {<br />
if($this-&gt;debug === TRUE) {<br />
$this-&gt;_error("ftp_unable_to_delete_file:file[".$file."]");<br />
}<br />
return FALSE;<br />
}<br />
<br />
return TRUE;<br />
}<br />
<br />
/**<br />
* 删除文件夹<br />
*<br />
* @access 	public<br />
* @param 	string 	目录标识(ftp)<br />
* @return	boolean<br />
*/<br />
public function delete_dir($path) {<br />
if( ! $this-&gt;_isconn()) {<br />
return FALSE;<br />
}<br />
<br />
//对目录宏的'/'字符添加反斜杠'\'<br />
$path = preg_replace("/(.+?)\/*$/", "\\1/", $path);<br />
<br />
//获取目录文件列表<br />
$filelist = $this-&gt;filelist($path);<br />
<br />
if($filelist !== FALSE AND count($filelist) &gt; 0) {<br />
foreach($filelist as $item) {<br />
//如果我们无法删除,那么就可能是一个文件夹<br />
//所以我们递归调用delete_dir()<br />
if( ! @delete_file($item)) {<br />
$this-&gt;delete_dir($item);<br />
}<br />
}<br />
}<br />
<br />
//删除文件夹(空文件夹)<br />
$result = @ftp_rmdir($this-&gt;conn_id, $path);<br />
<br />
if($result === FALSE) {<br />
if($this-&gt;debug === TRUE) {<br />
$this-&gt;_error("ftp_unable_to_delete_dir:dir[".$path."]");<br />
}<br />
return FALSE;<br />
}<br />
<br />
return TRUE;<br />
}<br />
<br />
/**<br />
* 修改文件权限<br />
*<br />
* @access 	public<br />
* @param 	string 	目录标识(ftp)<br />
* @return	boolean<br />
*/<br />
public function chmod($path, $perm) {<br />
if( ! $this-&gt;_isconn()) {<br />
return FALSE;<br />
}<br />
<br />
//只有在PHP5中才定义了修改权限的函数(ftp)<br />
if( ! function_exists('ftp_chmod')) {<br />
if($this-&gt;debug === TRUE) {<br />
$this-&gt;_error("ftp_unable_to_chmod(function)");<br />
}<br />
return FALSE;<br />
}<br />
<br />
$result = @ftp_chmod($this-&gt;conn_id, $perm, $path);<br />
<br />
if($result === FALSE) {<br />
if($this-&gt;debug === TRUE) {<br />
$this-&gt;_error("ftp_unable_to_chmod:path[".$path."]-chmod[".$perm."]");<br />
}<br />
return FALSE;<br />
}<br />
return TRUE;<br />
}<br />
<br />
/**<br />
* 获取目录文件列表<br />
*<br />
* @access 	public<br />
* @param 	string 	目录标识(ftp)<br />
* @return	array<br />
*/<br />
public function filelist($path = '.') {<br />
if( ! $this-&gt;_isconn()) {<br />
return FALSE;<br />
}<br />
return ftp_nlist($this-&gt;conn_id, $path);<br />
}<br />
<br />
<br />
public function filechdir($path = '.'){<br />
&nbsp; // echo "Dir: ".ftp_pwd($conn);<br />
&nbsp; &nbsp;if( ! $this-&gt;_isconn()) {<br />
&nbsp; &nbsp; &nbsp; &nbsp;return FALSE;<br />
&nbsp; &nbsp;}<br />
&nbsp; &nbsp;return ftp_chdir($this-&gt;conn_id, $path);<br />
&nbsp; &nbsp;<br />
}<br />
<br />
<br />
/**<br />
* 关闭FTP<br />
*<br />
* @access 	public<br />
* @return	boolean<br />
*/<br />
public function close() {<br />
if( ! $this-&gt;_isconn()) {<br />
return FALSE;<br />
}<br />
<br />
return @ftp_close($this-&gt;conn_id);<br />
}<br />
<br />
/**<br />
* FTP成员变量初始化<br />
*<br />
* @access	private<br />
* @param	array	配置数组	&nbsp;<br />
* @return	void<br />
*/<br />
private function _init($config = array()) {<br />
foreach($config as $key =&gt; $val) {<br />
if(isset($this-&gt;$key)) {<br />
$this-&gt;$key = $val;<br />
}<br />
}<br />
<br />
//特殊字符过滤<br />
$this-&gt;hostname = preg_replace('|.+?://|','',$this-&gt;hostname);<br />
}<br />
<br />
/**<br />
* FTP登陆<br />
*<br />
* @access 	private<br />
* @return	boolean<br />
*/<br />
private function _login() {<br />
return @ftp_login($this-&gt;conn_id, $this-&gt;username, $this-&gt;password);<br />
}<br />
<br />
/**<br />
* 判断con_id<br />
*<br />
* @access 	private<br />
* @return	boolean<br />
*/<br />
private function _isconn() {<br />
if( ! is_resource($this-&gt;conn_id)) {<br />
if($this-&gt;debug === TRUE) {<br />
$this-&gt;_error("ftp_no_connection");<br />
}<br />
return FALSE;<br />
}<br />
return TRUE;<br />
}<br />
<br />
/**<br />
* 从文件名中获取后缀扩展<br />
*<br />
* @access 	private<br />
* @param 	string 	目录标识<br />
* @return	string<br />
*/<br />
private function _getext($filename) {<br />
if(FALSE === strpos($filename, '.')) {<br />
return 'txt';<br />
}<br />
<br />
$extarr = explode('.', $filename);<br />
return end($extarr);<br />
}<br />
<br />
/**<br />
* 从后缀扩展定义FTP传输模式 &nbsp;ascii 或 binary<br />
*<br />
* @access 	private<br />
* @param 	string 	后缀扩展<br />
* @return	string<br />
*/<br />
private function _settype($ext) {<br />
$text_type = array (<br />
'txt',<br />
'text',<br />
'php',<br />
'phps',<br />
'php4',<br />
'js',<br />
'css',<br />
'htm',<br />
'html',<br />
'phtml',<br />
'shtml',<br />
'log',<br />
'xml'<br />
);<br />
<br />
return (in_array($ext, $text_type)) ? 'ascii' : 'binary';<br />
}<br />
<br />
/**<br />
* 错误日志记录<br />
*<br />
* @access 	prvate<br />
* @return	boolean<br />
*/<br />
private function _error($msg) {<br />
return @file_put_contents('ftp_err.log', "date[".date("Y-m-d H:i:s")."]-hostname[".$this-&gt;hostname."]-username[".$this-&gt;username."]-password[".$this-&gt;password."]-msg[".$msg."]\n", FILE_APPEND);<br />
}<br />
}<br />
<br />
<br />
$conn=new Ftp();<br />
$a=$conn-&gt;connect();<br />
//进入目录<br />
print_R($conn-&gt;filechdir('/wwwroot/my/data/2015/10'));<br />
<br />
print_R($conn-&gt;filelist());<br />
<br />
//var_dump($conn-&gt;download('./wwwroot/index.php',"E:\\12123.php"));<br />
<br />
// $conn-&gt;download($remotepath, $localpath);<br />
<br />
/*End of file ftp.php*/<br />
/*Location /Apache Group/htdocs/ftp.php*/<br />