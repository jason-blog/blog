<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	MIME的全称是"Multipurpose Internet Mail Extensions"，中译为"多用途互联网邮件扩展"，指的是一系列的电子邮件技术规范，主要包括RFC 2045、RFC 2046、RFC 2047、RFC 4288、RFC 4289和RFC 2077。
</p>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	顾名思义，MIME是对传统电子邮件的一个扩展，现在已经成为电子邮件实际上的标准。
</p>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	2.
</p>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	传统的电子邮件是1982年定下技术规范的，文件是RFC 822。
</p>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	它的一个重要特点，就是规定电子邮件只能使用ASCII字符。这导致了三个结果：1）非英语字符都不能在电子邮件中使用；2）电子邮件中不能插入二进制文件（如图片）；3）电子邮件不能有附件。
</p>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	这实际上无法接受的，因此到了1992年，工程师们决定扩展电子邮件的技术规范，提出一系列补充规范，这就是MIME的由来。
</p>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	3.
</p>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	下面是一封传统的电子邮件。
</p>
<blockquote style="margin:2em;padding:1em;list-style-type:none;border:0.3em solid #E0DFCC;color:#111111;background-color:#F5F2F0;border-radius:1em;font-family:Consolas, Monaco, &quot;text-shadow:white 0px 1px;overflow:auto;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;">
	<div style="margin:0px;padding:0px;list-style-type:none;border:none;">
		<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;font-size:1.6em;line-height:28.8px;">
			From: "Tommy Lee" &lt;lee@example.com&gt;<br />
To: "Jack Zhang" &lt;zhang@example.com&gt;<br />
Subject: Test<br />
Date: Wed, 17 May 2000 19:08:29 -0400<br />
Message-ID: &lt;NDBBIAKOPKHFGPLCODIGIEKBCHAA.lee@example.com&gt;
		</p>
		<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;font-size:1.6em;line-height:28.8px;">
			Hello World.
		</p>
	</div>
</blockquote>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	从上面可以看出，这封信的发信人地址是lee@example.com，收信人地址是zhang@example.com，邮件主题是Test，发送时间是2000年5月17日，邮件内容是"Hello World."。
</p>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	在结构上，这封信分为三个部分：首先是信件头，然后是一个空行，最后是信件内容。收信人的客户端软件只会显示最后一部分，要查看全信，必须使用"查看原始邮件"功能。
</p>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	4.
</p>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	MIME对传统电子邮件的扩展，表现在它在信件头部分添加了几条语句，主要有三条。
</p>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	第一条是：
</p>
<blockquote style="margin:2em;padding:1em;list-style-type:none;border:0.3em solid #E0DFCC;color:#111111;background-color:#F5F2F0;border-radius:1em;font-family:Consolas, Monaco, &quot;text-shadow:white 0px 1px;overflow:auto;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;">
	<div style="margin:0px;padding:0px;list-style-type:none;border:none;">
		<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;font-size:1.6em;line-height:28.8px;">
			MIME-Version: 1.0
		</p>
	</div>
</blockquote>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	这条语句是必须的，而且1.0这个版本值是不变的，即使MIME本身已经升级了好几次。
</p>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	有了这条语句，收信端就知道这封信使用了MIME规范。
</p>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	5.
</p>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	第二条语句是：
</p>
<blockquote style="margin:2em;padding:1em;list-style-type:none;border:0.3em solid #E0DFCC;color:#111111;background-color:#F5F2F0;border-radius:1em;font-family:Consolas, Monaco, &quot;text-shadow:white 0px 1px;overflow:auto;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;">
	<div style="margin:0px;padding:0px;list-style-type:none;border:none;">
		<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;font-size:1.6em;line-height:28.8px;">
			Content-Type: text/plain; charset="ISO-8859-1"
		</p>
	</div>
</blockquote>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	这一行是极端重要的，它表明传递的信息类型和采用的编码。
</p>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	Content-Type表明信息类型，缺省值为" text/plain"。它包含了主要类型（primary type）和次要类型（subtype）两个部分，两者之间用"/"分割。主要类型有9种，分别是application、audio、example、image、message、model、multipart、text、video。
</p>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	每一种主要类型下面又有许多种次要类型，常见的有：
</p>
<blockquote style="margin:2em;padding:1em;list-style-type:none;border:0.3em solid #E0DFCC;color:#111111;background-color:#F5F2F0;border-radius:1em;font-family:Consolas, Monaco, &quot;text-shadow:white 0px 1px;overflow:auto;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;">
	<div style="margin:0px;padding:0px;list-style-type:none;border:none;">
		<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;font-size:1.6em;line-height:28.8px;">
			text/plain：纯文本，文件扩展名.txt<br />
text/html：HTML文本，文件扩展名.htm和.html<br />
image/jpeg：jpeg格式的图片，文件扩展名.jpg<br />
image/gif：GIF格式的图片，文件扩展名.gif<br />
audio/x-wave：WAVE格式的音频，文件扩展名.wav<br />
audio/mpeg：MP3格式的音频，文件扩展名.mp3<br />
video/mpeg：MPEG格式的视频，文件扩展名.mpg<br />
application/zip：PK-ZIP格式的压缩文件，文件扩展名.zip
		</p>
	</div>
</blockquote>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	详细的Content-Type列表，可以查看<a href="http://www.iana.org/assignments/media-types/" target="_blank" style="margin:0px;padding:0px;list-style-type:none;border:none;color:#112233;">这里</a>和<a href="http://www.utoronto.ca/webdocs/HTMLdocs/Book/Book-3ed/appb/mimetype.html" target="_blank" style="margin:0px;padding:0px;list-style-type:none;border:none;color:#112233;">这里</a>。
</p>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	如果信息的主要类型是"text"，那么还必须指明编码类型"charset"，缺省值是ASCII，其他可能值有"ISO-8859-1"、"UTF-8"、"GB2312"等等。
</p>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	整个Content-Type这一行，不仅使用在电子邮件，后来也被移植到了HTTP协议中，所以现在只要是在网上传播的HTTP信息，都带有Content-Type头，以表明信息类型。
</p>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	6.
</p>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	前面已经说过，电子邮件的传统格式不支持非ASCII编码和二进制数据。因此MIME规定了第三条语句：
</p>
<blockquote style="margin:2em;padding:1em;list-style-type:none;border:0.3em solid #E0DFCC;color:#111111;background-color:#F5F2F0;border-radius:1em;font-family:Consolas, Monaco, &quot;text-shadow:white 0px 1px;overflow:auto;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;">
	<div style="margin:0px;padding:0px;list-style-type:none;border:none;">
		<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;font-size:1.6em;line-height:28.8px;">
			Content-transfer-encoding: base64
		</p>
	</div>
</blockquote>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	这条语句指明了编码转换的方式。Content-transfer-encoding的值有<a href="http://www.iana.org/assignments/transfer-encodings" target="_blank" style="margin:0px;padding:0px;list-style-type:none;border:none;color:#112233;">5种</a>----"7bit"、"8bit"、"binary"、"quoted-printable"和"base64"----其中"7bit"是缺省值，即不用转化的ASCII字符。真正常用是"quoted-printable"和"base64"两种，它们的详细用法，我在明天的笔记中会详细介绍。
</p>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	7.
</p>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	下面是一封我收到的邮件的源码：
</p>
<blockquote style="margin:2em;padding:1em;list-style-type:none;border:0.3em solid #E0DFCC;color:#111111;background-color:#F5F2F0;border-radius:1em;font-family:Consolas, Monaco, &quot;text-shadow:white 0px 1px;overflow:auto;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;">
	<div style="margin:0px;padding:0px;list-style-type:none;border:none;">
		<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;font-size:1.6em;line-height:28.8px;">
			Date: Wed, 18 Jun 2008 18:07:51 +0800 (CST)<br />
From: xxx &lt;xxx@163.com&gt;<br />
To: yifeng.ruan@gmail.com<br />
Message-ID: &lt;14410503.1073611213783671983.JavaMail.coremail@bj163app54.163.com&gt;<br />
Subject: =?gbk?B?xOO6ww==?=<br />
MIME-Version: 1.0<br />
Content-Type: multipart/alternative;&nbsp;<br />
boundary=&amp;quot;----=_Part_287491_22998031.1213783671982&amp;quot;
		</p>
		<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;font-size:1.6em;line-height:28.8px;">
			------=_Part_287491_22998031.1213783671982<br />
Content-Type: text/plain; charset=gbk<br />
Content-Transfer-Encoding: base64
		</p>
		<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;font-size:1.6em;line-height:28.8px;">
			IAq4+b7dsr+209PQudi55raoo6yyu7XD1Nq12Le9yM66zs341b7Jz7nSz+DTprXEtqvO96Osx+vE<br />
49TaxOO1xLKpv83W0AogIArW0Ln6yr2x6tPvIC0gyO7Su7fltcTN+MLnyNXWvgoKtcS12jEy1cXN<br />
vMasyb6z/aOst/HU8s7Sw8fXt76/xOO1xM/gudjU8MjOoaPQu9C7us/X96OhtMvNvMas1Nq4vbz+<br />
wO/D5g==<br />
------=_Part_287491_22998031.1213783671982<br />
Content-Type: text/html; charset=gbk<br />
Content-Transfer-Encoding: quoted-printable
		</p>
		<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;font-size:1.6em;line-height:28.8px;">
			&lt;DIV&gt;&amp;amp;nbsp;&lt;/DIV&gt;<br />
&lt;DIV&gt;=B8=F9=BE=DD=B2=BF=B6=D3=D3=D0=B9=D8=B9=E6=B6=A8=A3=AC=B2=BB=B5=C3=D4=<br />
=DA=B5=D8=B7=BD=C8=CE=BA=CE=CD=F8=D5=BE=C9=CF=B9=D2=CF=E0=D3=A6=B5=C4=B6=AB=<br />
=CE=F7=A3=AC=C7=EB=C4=E3=D4=DA=C4=E3=B5=C4=B2=A9=BF=CD=D6=D0&lt;/DIV&gt;<br />
&lt;DIV&gt;&amp;amp;nbsp;<br />
......
		</p>
	</div>
</blockquote>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	可以看到这封信的MIME语句是：
</p>
<blockquote style="margin:2em;padding:1em;list-style-type:none;border:0.3em solid #E0DFCC;color:#111111;background-color:#F5F2F0;border-radius:1em;font-family:Consolas, Monaco, &quot;text-shadow:white 0px 1px;overflow:auto;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;">
	<div style="margin:0px;padding:0px;list-style-type:none;border:none;">
		<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;font-size:1.6em;line-height:28.8px;">
			MIME-Version: 1.0<br />
Content-Type: multipart/alternative;&nbsp;<br />
boundary="----=_Part_287491_22998031.1213783671982"
		</p>
	</div>
</blockquote>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	"Content-Type: multipart/alternative;"表明这封信的内容，是纯文本和HTML文本的混合。另两个可能的值是multipart/mixed和multipart/related，分别表示"信件内容中有二进制内容"和"信件带有附件"。
</p>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	"boundary="----=_Part_287491_22998031.1213783671982"<br />
"表明不同信件内容的分割线是"----=_Part_287491_22998031.1213783671982"，它通常是一个很长的随机字符串。
</p>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	信件内容部分又有两个子信件头：
</p>
<blockquote style="margin:2em;padding:1em;list-style-type:none;border:0.3em solid #E0DFCC;color:#111111;background-color:#F5F2F0;border-radius:1em;font-family:Consolas, Monaco, &quot;text-shadow:white 0px 1px;overflow:auto;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;">
	<div style="margin:0px;padding:0px;list-style-type:none;border:none;">
		<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;font-size:1.6em;line-height:28.8px;">
			Content-Type: text/plain; charset=gbk<br />
Content-Transfer-Encoding: base64
		</p>
	</div>
</blockquote>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	和
</p>
<blockquote style="margin:2em;padding:1em;list-style-type:none;border:0.3em solid #E0DFCC;color:#111111;background-color:#F5F2F0;border-radius:1em;font-family:Consolas, Monaco, &quot;text-shadow:white 0px 1px;overflow:auto;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;">
	<div style="margin:0px;padding:0px;list-style-type:none;border:none;">
		<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;font-size:1.6em;line-height:28.8px;">
			Content-Type: text/html; charset=gbk<br />
Content-Transfer-Encoding: quoted-printable
		</p>
	</div>
</blockquote>
<p style="margin-top:1em;margin-bottom:0px;margin-left:0.8em;padding:0px;list-style-type:none;border:none;color:#111111;font-size:1.6em;line-height:28.8px;font-family:Georgia, serif;letter-spacing:-0.12px;white-space:normal;word-spacing:2.4px;background-color:#F5F5D5;">
	它们表明，第一个部分是gbk编码的纯文本，编码转换格式是base64。第二个部分是gbk编码的HTML文本，编码转化格式是quoted-printable。
</p>