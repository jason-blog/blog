package h2;<br />
<br />
import java.sql.Connection;<br />
import java.sql.DriverManager;<br />
import java.sql.ResultSet;<br />
import java.sql.SQLException;<br />
import java.sql.Statement;<br />
<br />
import org.h2.tools.Server;&nbsp;&nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp;&nbsp;<br />
public class H2Demo {&nbsp;&nbsp;<br />
&nbsp; &nbsp; private Server server;&nbsp;&nbsp;<br />
&nbsp; &nbsp; private String port = "11111";&nbsp;&nbsp;<br />
&nbsp; &nbsp; private String dbDir = "./h2db/sample";&nbsp;&nbsp;<br />
&nbsp; &nbsp; private String user = "test";&nbsp;&nbsp;<br />
&nbsp; &nbsp; private String password = "123456";&nbsp;&nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp; public void startServer() {&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; try {&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; System.out.println("正在启动h2...");&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; server = Server.createTcpServer(&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; new String[] { "-tcpPort", port }).start();&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; } catch (SQLException e) {&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; System.out.println("启动h2出错：" + e.toString());&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; // TODO Auto-generated catch block&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; e.printStackTrace();&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; throw new RuntimeException(e);&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; }&nbsp;&nbsp;<br />
&nbsp; &nbsp; }&nbsp;&nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp; public void stopServer() {&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; if (server != null) {&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; System.out.println("正在关闭h2...");&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; server.stop();&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; System.out.println("关闭成功.");&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; }&nbsp;&nbsp;<br />
&nbsp; &nbsp; }&nbsp;&nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp; public void useH2() {&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; try {&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Class.forName("org.h2.Driver");&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Connection conn = DriverManager.getConnection("jdbc:h2:" + dbDir,&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; user, password);&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Statement stat = conn.createStatement();&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; // insert data&nbsp;&nbsp;<br />
//&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; stat.execute("CREATE TABLE TEST(NAME VARCHAR)");&nbsp;&nbsp;<br />
//&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; stat.execute("INSERT INTO TEST VALUES('Hello World')");&nbsp;&nbsp;<br />
//&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; // use data&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ResultSet result = stat.executeQuery("select name from test ");&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; int i = 1;&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; while (result.next()) {&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; System.out.println(i++ + ":" + result.getString("name"));&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; result.close();&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; stat.close();&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; conn.close();&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; } catch (Exception e) {&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; // TODO Auto-generated catch block&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; e.printStackTrace();&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; }&nbsp;&nbsp;<br />
&nbsp; &nbsp; }&nbsp;&nbsp;<br />
&nbsp;&nbsp;<br />
&nbsp; &nbsp; public static void main(String[] args) {&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; H2Demo h2 = new H2Demo();&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; h2.startServer();&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; h2.useH2();&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; h2.stopServer();&nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; System.out.println("==END==");&nbsp;&nbsp;<br />
&nbsp; &nbsp; }&nbsp;&nbsp;<br />
}&nbsp;&nbsp;<br />