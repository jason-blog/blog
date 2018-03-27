<p style="margin:10px auto;padding:0px;white-space:normal;">
	&nbsp;Jackson，我感觉是在Java与Json之间相互转换的最快速的框架，当然Google的Gson也很不错，但是参照网上有人的性能测试，看起来还是Jackson比较快一点

</p>
<p style="margin:10px auto;padding:0px;white-space:normal;">
	&nbsp;&nbsp;&nbsp; Jackson处理一般的JavaBean和Json之间的转换只要使用ObjectMapper 对象的readValue和writeValueAsString两个方法就能实现。但是如果要转换复杂类型Collection如 List&lt;YourBean&gt;，那么就需要先反序列化复杂类型 为泛型的Collection Type。
</p>
<p style="margin:10px auto;padding:0px;white-space:normal;">
	如果是ArrayList&lt;YourBean&gt;那么使用ObjectMapper 的getTypeFactory().constructParametricType(collectionClass, elementClasses);
</p>
<p style="margin:10px auto;padding:0px;white-space:normal;">
	如果是HashMap&lt;String,YourBean&gt;那么 ObjectMapper 的getTypeFactory().constructParametricType(HashMap.class,String.class, YourBean.class);
</p>
<p style="margin:10px auto;padding:0px;white-space:normal;">
	&nbsp;
</p>
<div class="cnblogs_code" style="margin:5px 0px;padding:5px;border:1px solid #CCCCCC;overflow:auto;white-space:normal;">
	<div class="cnblogs_code_toolbar" style="margin:5px 0px 0px;padding:0px;">
		<br />
	</div>
	<div class="cnblogs_code_toolbar" style="margin:5px 0px 0px;padding:0px;">
		public final ObjectMapper mapper = new ObjectMapper();&nbsp;<br />
&nbsp; &nbsp; &nbsp;<br />
&nbsp; &nbsp; public static void main(String[] args) throws Exception{ &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; JavaType javaType = getCollectionType(ArrayList.class, YourBean.class);&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; List&lt;YourBean&gt; lst = &nbsp;(List&lt;YourBean&gt;)mapper.readValue(jsonString, javaType);&nbsp;<br />
&nbsp; &nbsp; } &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp;/** &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; * 获取泛型的Collection Type &nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; * @param collectionClass 泛型的Collection &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; * @param elementClasses 元素类 &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; * @return JavaType Java类型 &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; * @since 1.0 &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; */ &nbsp;&nbsp;<br />
&nbsp; &nbsp; public static JavaType getCollectionType(Class&lt;?&gt; collectionClass, Class&lt;?&gt;... elementClasses) { &nbsp;&nbsp;<br />
&nbsp; &nbsp; &nbsp; &nbsp; return mapper.getTypeFactory().constructParametricType(collectionClass, elementClasses); &nbsp;&nbsp;<br />
&nbsp; &nbsp; }<br />
<br />
	</div>
</div>