package ceshi;<br />
<br />
import java.awt.*;<br />
import java.io.*;<br />
import java.awt.event.*;<br />
public class IOtest extends Frame implements ActionListener{<br />
&nbsp; &nbsp; &nbsp;private Frame f;<br />
&nbsp; &nbsp; &nbsp;private TextArea ta; &nbsp; //ta用于显示打开的内容<br />
&nbsp; &nbsp; &nbsp;private Button btn;<br />
&nbsp; &nbsp; &nbsp;private FileDialog fd;<br />
&nbsp; &nbsp; &nbsp;private File file1 = null;<br />
&nbsp; &nbsp; &nbsp;public static void main(String []args){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;IOtest iof = new IOtest();//创建并初始化IOtest对象iof<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;iof.show();<br />
&nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp;//构造函数开始<br />
&nbsp; &nbsp; &nbsp; public IOtest(){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;btn = new Button("打开");<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;ta = new TextArea(5,50);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;btn.addActionListener(this);//给按钮添加事件监听器<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;}<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;//给按钮添加行为<br />
&nbsp; &nbsp; &nbsp; public void actionPerformed(ActionEvent e){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; if (e.getSource()==btn) { //单击打开按钮时 &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; fd = new FileDialog(f,"Open",FileDialog.LOAD);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; fd.setVisible(true); &nbsp; //创建并显示打开文件对话框<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //if ((fd.getDirectory()!=null) &amp;&amp; (fd.getFile()!=null)) {<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; try { &nbsp; //以缓冲区方式读取文件内容<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; file1 = new File(fd.getDirectory(),fd.getFile());<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; FileReader fr = new FileReader(file1);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; BufferedReader br = new BufferedReader(fr);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; String aline;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; while ((aline=br.readLine()) != null)//按行读取文本<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ta.append(aline+"\r\n");<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; fr.close();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; br.close();<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;catch (IOException ioe){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; System.out.println(ioe);<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;//}<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp;public void show()<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;{<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; f = new Frame("读入文件测试"); &nbsp; &nbsp; &nbsp; &nbsp; //初始化对象f<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; f.setSize(500,300); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;//设置窗口f的大小<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; //设置布局管理器为FlowLayout<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;f.setLayout(new FlowLayout(FlowLayout.LEFT,30,20));<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;f.add(btn); &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;f.add(ta); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;//为窗口f添加WindowListener监听器<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;f.addWindowListener(new WindowAdapter(){<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; public void windowClosing(WindowEvent evt){ //实现windowClosing方法<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; f.setVisible(false); &nbsp; &nbsp; &nbsp; &nbsp; //设置窗口f不可见<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; f.dispose(); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;//释放窗口及其子组件的屏幕资源<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; System.exit(0); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;//退出程序<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; }<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; });<br />
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; f.setLocation(200,200);<br />
&nbsp; &nbsp; &nbsp; &nbsp; f.setVisible(true); &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;//设置窗口f可视<br />
&nbsp; &nbsp; }<br />
}<br />