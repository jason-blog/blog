&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"&gt;<br />
&lt;html xmlns="http://www.w3.org/1999/xhtml"&gt;<br />
&lt;head&gt;<br />
&nbsp; &nbsp; &lt;title&gt;&lt;/title&gt;<br />
&nbsp; &nbsp; &lt;script type="text/javascript"&gt;<br />
&nbsp; &nbsp; // 得到航班信息查询结果后的回调函数<br />
&nbsp; &nbsp; var flightHandler = function(data){<br />
&nbsp; &nbsp; &nbsp; &nbsp; alert('你查询的航班结果是：票价 ' + data.price + ' 元，' + '余票 ' + data.tickets + ' 张。');<br />
&nbsp; &nbsp; };<br />
&nbsp; &nbsp; // 提供jsonp服务的url地址（不管是什么类型的地址，最终生成的返回值都是一段javascript代码）<br />
&nbsp; &nbsp; var url = "http://flightQuery.com/jsonp/flightResult.aspx?code=CA1998&amp;callback=flightHandler";<br />
&nbsp; &nbsp; // 创建script标签，设置其属性<br />
&nbsp; &nbsp; var script = document.createElement('script');<br />
&nbsp; &nbsp; script.setAttribute('src', url);<br />
&nbsp; &nbsp; // 把script标签加入head，此时调用开始<br />
&nbsp; &nbsp; document.getElementsByTagName('head')[0].appendChild(script);&nbsp;<br />
&nbsp; &nbsp; &lt;/script&gt;<br />
&lt;/head&gt;<br />
&lt;body&gt;<br />
<br />
&lt;/body&gt;<br />
&lt;/html&gt;<br />