<pre name="code" class="java" style="box-sizing:border-box;font-family:Arial, &quot;font-size:13px;white-space:pre-wrap;padding:0px;margin-top:0px;margin-bottom:0px;line-height:1.42857;color:#333333;word-break:break-all;word-wrap:break-word;background-color:#F5F5F5;border:1px solid #CCCCCC;border-radius:4px;overflow:hidden;width:1863px;">	public static void main(String[] args) throws Exception{	
		// A File object pointing to your GeoIP2 or GeoLite2 database	
		File database = new File("F:/定位/GeoLite2-City.mmdb");	
		// This creates the DatabaseReader object, which should be reused across	
		// lookups.	  
		DatabaseReader reader = new DatabaseReader.Builder(database).build();	  
		InetAddress ipAddress = InetAddress.getByName("14.106.124.11");	  
		// Replace "city" with the appropriate method for your database, e.g.,	 
		// "country".	  
		CityResponse response = reader.city(ipAddress);	  
		/*Country country = response.getCountry();	  
		System.out.println(country.getIsoCode());            // 'US'	 
		System.out.println(country.getName()); // 'United States'	
		System.out.println(country.getNames().get("zh-CN")); // '美国'	
		Subdivision subdivision = response.getMostSpecificSubdivision();
		System.out.println(subdivision.getName());   // 'Minnesota'	 
		System.out.println(subdivision.getIsoCode()); // 'MN'	  
*/		
		City city = response.getCity();
		System.out.println(city.getName()); // 'Minneapolis'
		Postal postal = response.getPostal();	
		System.out.println(postal.getCode()); // '55455'	 
		Location location = response.getLocation();	 
		System.out.println(location.getLatitude());  // 44.9733	 
		System.out.println(location.getLongitude()); // -93.2323 
		
	}</pre>