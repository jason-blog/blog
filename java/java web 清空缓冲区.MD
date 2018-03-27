<pre class="prettyprint lang-js linenums">   @RequestMapping(value="/test",method=RequestMethod.GET)
	   @ResponseBody
	   public String test(OutputStream out) throws  IOException{
		   out.flush();
	       PrintWriter ret =  new PrintWriter(new OutputStreamWriter(out,"UTF-8"),true);
		   while (true) {
			   ret.write("呵呵哒");
			   ret.flush();
			   try {
					Thread.sleep(1000);
				} catch (InterruptedException e) {
					// TODO Auto-generated catch block
					e.printStackTrace();
				}
			 }
	   }
	  
	   @RequestMapping(value="/test2",method=RequestMethod.GET)
	   @ResponseBody
	   public String test2(HttpServletResponse response) throws IOException{
		   while (true) {
			   response.setContentType("text/html;charset=utf-8");
			   response.getWriter().println("测试一下 ...");;
			   response.flushBuffer();
			   try {
				Thread.sleep(1000);
			} catch (InterruptedException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		   }
	   }</pre>