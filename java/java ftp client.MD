package ceshi;<br />
import java.io.File;<br />
import java.io.FileInputStream;<br />
import java.io.FileOutputStream;<br />
import java.io.IOException;<br />
import java.io.OutputStream;<br />
import java.util.ArrayList;<br />
import java.util.List;<br />
<br />
import org.apache.commons.io.IOUtils;<br />
import org.apache.commons.net.ftp.FTPClient;<br />
import org.apache.commons.net.ftp.FTPFile;<br />
import org.apache.commons.net.ftp.FTPReply;<br />
&nbsp;<br />
/**<br />
&nbsp;* &lt;p&gt;<br />
&nbsp;* ftp连接管理(使用apache commons-net-1.4.1 lib)<br />
&nbsp;* &lt;/p&gt;<br />
&nbsp;*/<br />
public class FtpClientUtil {<br />
&nbsp;private FTPClient ftpClient = null;<br />
&nbsp;private String server;<br />
&nbsp;private int port;<br />
&nbsp;private String userName;<br />
&nbsp;private String userPassword;<br />
&nbsp;<br />
&nbsp;public static void main(String[] args) {<br />
&nbsp; // 调用FTP传输g<br />
&nbsp; // FtpClientUtil f = new FtpClientUtil("10.50.20.8", 21, "suzy",<br />
&nbsp; // "123456");<br />
&nbsp; // FtpClientUtil f = new FtpClientUtil("10.7.4.56",21,"root","wonder");<br />
&nbsp; FtpClientUtil f = new FtpClientUtil("103.233.248.98", 21, "wolegequ18", "FA2C77B387eca5");<br />
&nbsp; // FtpClientUtil f = new<br />
&nbsp; // FtpClientUtil("10.50.20.213",21,"Administrator","administrator");<br />
&nbsp; try {<br />
&nbsp; &nbsp;if (f.open()) {<br />
&nbsp;<br />
// &nbsp; &nbsp; f.getFtpClient().sendServer("quote PASV");<br />
&nbsp;<br />
// &nbsp; &nbsp; f.getFtpClient().sendServer("quote PORT");<br />
&nbsp;<br />
// &nbsp; &nbsp; f.mkDir("put2/5/6\\8\\9");<br />
// &nbsp; &nbsp; f.mkDir("test6\\7/8/9");<br />
// &nbsp; &nbsp; f.mkDir("test6/7/8/9");<br />
// &nbsp; &nbsp; f.mkDir("test7");<br />
// &nbsp; &nbsp;f.put("d:/1.txt", "中国.txt", "put3/测试/6\\8\\9");// 远程路径为相对路径<br />
&nbsp; &nbsp; f.get("/wolegequ18/web/index.php", "E:/aa.txt");// 远程路径为相对路径<br />
&nbsp; &nbsp; f.close();<br />
&nbsp; &nbsp;}<br />
&nbsp; } catch (Exception e) {<br />
&nbsp;<br />
&nbsp; &nbsp;e.printStackTrace();<br />
&nbsp; }<br />
&nbsp;}<br />
&nbsp;<br />
&nbsp;public FtpClientUtil(String server, int port, String userName,<br />
&nbsp; &nbsp;String userPassword) {<br />
&nbsp; this.server = server;<br />
&nbsp; this.port = port;<br />
&nbsp; this.userName = userName;<br />
&nbsp; this.userPassword = userPassword;<br />
&nbsp;}<br />
&nbsp;<br />
&nbsp;/**<br />
&nbsp; * 链接到服务器<br />
&nbsp; *<br />
&nbsp; * @return<br />
&nbsp; * @throws Exception<br />
&nbsp; */<br />
&nbsp;public boolean open() {<br />
&nbsp; if (ftpClient != null &amp;&amp; ftpClient.isConnected()) {<br />
&nbsp; &nbsp;return true;<br />
&nbsp; }<br />
&nbsp; try {<br />
&nbsp; &nbsp;ftpClient = new FTPClient();<br />
&nbsp; &nbsp;// 连接<br />
&nbsp; &nbsp;ftpClient.connect(this.server, this.port);<br />
&nbsp; &nbsp;ftpClient.login(this.userName, this.userPassword);<br />
&nbsp; &nbsp;// 检测连接是否成功<br />
&nbsp; &nbsp;int reply = ftpClient.getReplyCode();<br />
&nbsp; &nbsp;if (!FTPReply.isPositiveCompletion(reply)) {<br />
&nbsp; &nbsp; this.close();<br />
&nbsp; &nbsp; System.err.println("FTP server refused connection.");<br />
&nbsp; &nbsp; System.exit(1);<br />
&nbsp; &nbsp;}<br />
&nbsp; &nbsp;System.out.println("open FTP success:" + this.server+";port:"+this.port + ";name:"<br />
&nbsp; &nbsp; &nbsp;+ this.userName + ";pwd:" + this.userPassword);<br />
&nbsp; &nbsp;ftpClient.setFileType(ftpClient.BINARY_FILE_TYPE); // 设置上传模式.binally<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; // or ascii<br />
&nbsp; &nbsp;return true;<br />
&nbsp; } catch (Exception ex) {<br />
&nbsp; &nbsp;// 关闭<br />
&nbsp; &nbsp;this.close();<br />
&nbsp; &nbsp;ex.printStackTrace();<br />
&nbsp; &nbsp;return false;<br />
&nbsp; }<br />
&nbsp;<br />
&nbsp;}<br />
&nbsp;<br />
&nbsp;private boolean cd(String dir) throws IOException {<br />
&nbsp; if (ftpClient.changeWorkingDirectory(dir)) {<br />
&nbsp; &nbsp;return true;<br />
&nbsp; } else {<br />
&nbsp; &nbsp;return false;<br />
&nbsp; }<br />
&nbsp;}<br />
&nbsp;<br />
&nbsp;/**<br />
&nbsp; * 获取目录下所有的文件名称<br />
&nbsp; *<br />
&nbsp; * @param filePath<br />
&nbsp; * @return<br />
&nbsp; * @throws IOException<br />
&nbsp; */<br />
&nbsp;<br />
&nbsp;private FTPFile[] getFileList(String filePath) throws IOException {<br />
&nbsp; FTPFile[] list = ftpClient.listFiles();<br />
&nbsp; return list;<br />
&nbsp;<br />
&nbsp;}<br />
&nbsp;<br />
&nbsp;/**<br />
&nbsp; * 循环将设置工作目录<br />
&nbsp; */<br />
&nbsp;public boolean changeDir(String ftpPath) {<br />
&nbsp; if (!ftpClient.isConnected()) {<br />
&nbsp; &nbsp;return false;<br />
&nbsp; }<br />
&nbsp; try {<br />
&nbsp;<br />
&nbsp; &nbsp;// 将路径中的斜杠统一<br />
&nbsp; &nbsp;char[] chars = ftpPath.toCharArray();<br />
&nbsp; &nbsp;StringBuffer sbStr = new StringBuffer(256);<br />
&nbsp; &nbsp;for (int i = 0; i &lt; chars.length; i++) {<br />
&nbsp;<br />
&nbsp; &nbsp; if ('\\' == chars[i]) {<br />
&nbsp; &nbsp; &nbsp;sbStr.append('/');<br />
&nbsp; &nbsp; } else {<br />
&nbsp; &nbsp; &nbsp;sbStr.append(chars[i]);<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp;}<br />
&nbsp; &nbsp;ftpPath = sbStr.toString();<br />
&nbsp; &nbsp;// System.out.println("ftpPath"+ftpPath);<br />
&nbsp;<br />
&nbsp; &nbsp;if (ftpPath.indexOf('/') == -1) {<br />
&nbsp; &nbsp; // 只有一层目录<br />
&nbsp; &nbsp; // System.out.println("change"+ftpPath);<br />
&nbsp; &nbsp; ftpClient.changeWorkingDirectory(new String(ftpPath.getBytes(),<br />
&nbsp; &nbsp; &nbsp; "iso-8859-1"));<br />
&nbsp; &nbsp;} else {<br />
&nbsp; &nbsp; // 多层目录循环创建<br />
&nbsp; &nbsp; String[] paths = ftpPath.split("/");<br />
&nbsp; &nbsp; // String pathTemp = "";<br />
&nbsp; &nbsp; for (int i = 0; i &lt; paths.length; i++) {<br />
&nbsp; &nbsp; &nbsp;// System.out.println("change "+paths[i]);<br />
&nbsp; &nbsp; &nbsp;ftpClient.changeWorkingDirectory(new String(paths[i]<br />
&nbsp; &nbsp; &nbsp; &nbsp;.getBytes(), "iso-8859-1"));<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp;}<br />
&nbsp;<br />
&nbsp; &nbsp;return true;<br />
&nbsp; } catch (Exception e) {<br />
&nbsp; &nbsp;e.printStackTrace();<br />
&nbsp; &nbsp;return false;<br />
&nbsp; }<br />
&nbsp;}<br />
&nbsp;<br />
&nbsp;/**<br />
&nbsp; * 循环创建目录，并且创建完目录后，设置工作目录为当前创建的目录下<br />
&nbsp; */<br />
&nbsp;public boolean mkDir(String ftpPath) {<br />
&nbsp; if (!ftpClient.isConnected()) {<br />
&nbsp; &nbsp;return false;<br />
&nbsp; }<br />
&nbsp; try {<br />
&nbsp;<br />
&nbsp; &nbsp;// 将路径中的斜杠统一<br />
&nbsp; &nbsp;char[] chars = ftpPath.toCharArray();<br />
&nbsp; &nbsp;StringBuffer sbStr = new StringBuffer(256);<br />
&nbsp; &nbsp;for (int i = 0; i &lt; chars.length; i++) {<br />
&nbsp;<br />
&nbsp; &nbsp; if ('\\' == chars[i]) {<br />
&nbsp; &nbsp; &nbsp;sbStr.append('/');<br />
&nbsp; &nbsp; } else {<br />
&nbsp; &nbsp; &nbsp;sbStr.append(chars[i]);<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp;}<br />
&nbsp; &nbsp;ftpPath = sbStr.toString();<br />
&nbsp; &nbsp;System.out.println("ftpPath" + ftpPath);<br />
&nbsp;<br />
&nbsp; &nbsp;if (ftpPath.indexOf('/') == -1) {<br />
&nbsp; &nbsp; // 只有一层目录<br />
&nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; ftpClient.makeDirectory(new String(ftpPath.getBytes(),<br />
&nbsp; &nbsp; &nbsp; "iso-8859-1"));<br />
&nbsp; &nbsp; ftpClient.changeWorkingDirectory(new String(ftpPath.getBytes(),<br />
&nbsp; &nbsp; &nbsp; "iso-8859-1"));<br />
&nbsp; &nbsp;} else {<br />
&nbsp; &nbsp; // 多层目录循环创建<br />
&nbsp; &nbsp; String[] paths = ftpPath.split("/");<br />
&nbsp; &nbsp; // String pathTemp = "";<br />
&nbsp; &nbsp; for (int i = 0; i &lt; paths.length; i++) {<br />
&nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; &nbsp;ftpClient.makeDirectory(new String(paths[i].getBytes(),<br />
&nbsp; &nbsp; &nbsp; &nbsp;"iso-8859-1"));<br />
&nbsp; &nbsp; &nbsp;ftpClient.changeWorkingDirectory(new String(paths[i]<br />
&nbsp; &nbsp; &nbsp; &nbsp;.getBytes(), "iso-8859-1"));<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp;}<br />
&nbsp;<br />
&nbsp; &nbsp;return true;<br />
&nbsp; } catch (Exception e) {<br />
&nbsp; &nbsp;e.printStackTrace();<br />
&nbsp; &nbsp;return false;<br />
&nbsp; }<br />
&nbsp;}<br />
&nbsp;<br />
&nbsp;/**<br />
&nbsp; * 上传文件到FTP服务器<br />
&nbsp; *<br />
&nbsp; * @param localPathAndFileName<br />
&nbsp; * &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;本地文件目录和文件名<br />
&nbsp; * @param ftpFileName<br />
&nbsp; * &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;上传后的文件名<br />
&nbsp; * @param ftpDirectory<br />
&nbsp; * &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;FTP目录如:/path1/pathb2/,如果目录不存在回自动创建目录<br />
&nbsp; * @throws Exception<br />
&nbsp; */<br />
&nbsp;public boolean put(String localDirectoryAndFileName, String ftpFileName,<br />
&nbsp; &nbsp;String ftpDirectory) {<br />
&nbsp; if (!ftpClient.isConnected()) {<br />
&nbsp; &nbsp;return false;<br />
&nbsp; }<br />
&nbsp; boolean flag = false;<br />
&nbsp; if (ftpClient != null) {<br />
&nbsp; &nbsp;File srcFile = new File(localDirectoryAndFileName);<br />
&nbsp; &nbsp;FileInputStream fis = null;<br />
&nbsp; &nbsp;try {<br />
&nbsp; &nbsp; fis = new FileInputStream(srcFile);<br />
&nbsp;<br />
&nbsp; &nbsp; // 创建目录<br />
&nbsp;<br />
&nbsp; &nbsp; this.mkDir(ftpDirectory);<br />
&nbsp;<br />
&nbsp; &nbsp; ftpClient.setBufferSize(1024);<br />
&nbsp; &nbsp; ftpClient.setControlEncoding("UTF-8");<br />
&nbsp;<br />
&nbsp; &nbsp; // 设置文件类型（二进制）<br />
&nbsp; &nbsp; ftpClient.setFileType(FTPClient.BINARY_FILE_TYPE);<br />
&nbsp; &nbsp; // 上传<br />
&nbsp; &nbsp; flag = ftpClient.storeFile(new String(ftpFileName.getBytes(),<br />
&nbsp; &nbsp; &nbsp; "iso-8859-1"), fis);<br />
&nbsp; &nbsp;} catch (Exception e) {<br />
&nbsp; &nbsp; this.close();<br />
&nbsp; &nbsp; e.printStackTrace();<br />
&nbsp; &nbsp; return false;<br />
&nbsp; &nbsp;} finally {<br />
&nbsp; &nbsp; IOUtils.closeQuietly(fis);<br />
&nbsp; &nbsp;}<br />
&nbsp; }<br />
&nbsp;<br />
&nbsp; System.out.println("success put file " + localDirectoryAndFileName<br />
&nbsp; &nbsp; + " to " + ftpDirectory + ftpFileName);<br />
&nbsp; return flag;<br />
&nbsp;}<br />
&nbsp;<br />
&nbsp;/**<br />
&nbsp; * 从FTP服务器上下载文件并返回下载文件长度<br />
&nbsp; *<br />
&nbsp; * @param ftpDirectoryAndFileName<br />
&nbsp; * @param localDirectoryAndFileName<br />
&nbsp; * @return<br />
&nbsp; * @throws Exception<br />
&nbsp; */<br />
&nbsp;public long get(String ftpDirectoryAndFileName,<br />
&nbsp; &nbsp;String localDirectoryAndFileName) {<br />
&nbsp;<br />
&nbsp; long result = 0;<br />
&nbsp; if (!ftpClient.isConnected()) {<br />
&nbsp; &nbsp;return 0;<br />
&nbsp; }<br />
&nbsp; ftpClient.enterLocalPassiveMode(); // Use passive mode as default<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;// because most of us are behind<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;// firewalls these days.<br />
&nbsp;<br />
&nbsp; try {<br />
&nbsp; &nbsp;// 将路径中的斜杠统一<br />
&nbsp; &nbsp;char[] chars = ftpDirectoryAndFileName.toCharArray();<br />
&nbsp; &nbsp;StringBuffer sbStr = new StringBuffer(256);<br />
&nbsp; &nbsp;for (int i = 0; i &lt; chars.length; i++) {<br />
&nbsp;<br />
&nbsp; &nbsp; if ('\\' == chars[i]) {<br />
&nbsp; &nbsp; &nbsp;sbStr.append('/');<br />
&nbsp; &nbsp; } else {<br />
&nbsp; &nbsp; &nbsp;sbStr.append(chars[i]);<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp;}<br />
&nbsp; &nbsp;ftpDirectoryAndFileName = sbStr.toString();<br />
&nbsp; &nbsp;String filePath = ftpDirectoryAndFileName.substring(0,<br />
&nbsp; &nbsp; &nbsp;ftpDirectoryAndFileName.lastIndexOf("/"));<br />
&nbsp; &nbsp;String fileName = ftpDirectoryAndFileName<br />
&nbsp; &nbsp; &nbsp;.substring(ftpDirectoryAndFileName.lastIndexOf("/") + 1);<br />
&nbsp; &nbsp;// System.out.println("filePath | "+filePath);<br />
&nbsp; &nbsp;// System.out.println("fileName | "+fileName);<br />
&nbsp; &nbsp;this.changeDir(filePath);<br />
&nbsp; &nbsp;System.out.println("sdf");&nbsp;<br />
<br />
&nbsp; &nbsp;ftpClient.retrieveFile( new String(fileName.getBytes(), "iso-8859-1"), new &nbsp;FileOutputStream(localDirectoryAndFileName)); // download<br />
&nbsp;<br />
&nbsp; &nbsp;// file<br />
&nbsp; &nbsp;System.out.print(ftpClient.getReplyString()); // check result<br />
&nbsp;<br />
&nbsp; } catch (IOException e) {<br />
&nbsp; &nbsp;e.printStackTrace();<br />
&nbsp; }<br />
&nbsp; System.out.println("Success get file" + ftpDirectoryAndFileName<br />
&nbsp; &nbsp; + " from " + localDirectoryAndFileName);<br />
&nbsp; return result;<br />
&nbsp;}<br />
&nbsp;<br />
&nbsp;/**<br />
&nbsp; * 返回FTP目录下的文件列表<br />
&nbsp; *<br />
&nbsp; * @param ftpDirectory<br />
&nbsp; * @return<br />
&nbsp; */<br />
&nbsp;public List getFileNameList(String ftpDirectory) {<br />
&nbsp; List list = new ArrayList();<br />
&nbsp; // if (!open())<br />
&nbsp; // return list;<br />
&nbsp; // try {<br />
&nbsp; // DataInputStream dis = new DataInputStream(ftpClient<br />
&nbsp; // .nameList(ftpDirectory));<br />
&nbsp; // String filename = "";<br />
&nbsp; // while ((filename = dis.readLine()) != null) {<br />
&nbsp; // list.add(filename);<br />
&nbsp; // }<br />
&nbsp; // } catch (Exception e) {<br />
&nbsp; // e.printStackTrace();<br />
&nbsp; // }<br />
&nbsp; return list;<br />
&nbsp;}<br />
&nbsp;<br />
&nbsp;/**<br />
&nbsp; * 删除FTP上的文件<br />
&nbsp; *<br />
&nbsp; * @param ftpDirAndFileName<br />
&nbsp; */<br />
&nbsp;public boolean deleteFile(String ftpDirAndFileName) {<br />
&nbsp; if (!ftpClient.isConnected()) {<br />
&nbsp; &nbsp;return false;<br />
&nbsp; }<br />
&nbsp; //Todo<br />
&nbsp; return true;<br />
&nbsp;}<br />
&nbsp;<br />
&nbsp;/**<br />
&nbsp; * 删除FTP目录<br />
&nbsp; *<br />
&nbsp; * @param ftpDirectory<br />
&nbsp; */<br />
&nbsp;public boolean deleteDirectory(String ftpDirectory) {<br />
&nbsp; if (!ftpClient.isConnected()) {<br />
&nbsp; &nbsp;return false;<br />
&nbsp; }<br />
&nbsp; //ToDo<br />
&nbsp; return true;<br />
&nbsp;}<br />
&nbsp;<br />
&nbsp;/**<br />
&nbsp; * 关闭链接<br />
&nbsp; */<br />
&nbsp;public void close() {<br />
&nbsp; &nbsp;try {<br />
&nbsp; &nbsp;if (ftpClient != null &amp;&amp; ftpClient.isConnected())<br />
&nbsp; &nbsp; ftpClient.disconnect();<br />
&nbsp; &nbsp;} catch (Exception e) {<br />
&nbsp; &nbsp; e.printStackTrace();<br />
&nbsp; &nbsp;}<br />
&nbsp; &nbsp;System.out.println("Close Server Success :"+this.server+";port:"+this.port);<br />
&nbsp;}<br />
&nbsp;<br />
&nbsp;public FTPClient getFtpClient() {<br />
&nbsp; return ftpClient;<br />
&nbsp;}<br />
&nbsp;<br />
}<br />