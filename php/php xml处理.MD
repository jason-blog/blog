<pre class="prettyprint lang-php linenums">&lt;?php

    /**
     * xml 转换成数组
     * $file 文件路径
     */
     function xml_to_array($file){
        if($this-&gt;xml_parser($file)==false){
            return false;
        }
        $array = (array)(simplexml_load_string($file));
        foreach ($array as $key=&gt;$item){
            $array[$key]  =  $this-&gt;struct_to_array((array)$item);
        }
        return $array;
    }
     function struct_to_array($item) {
        if(!is_string($item)) {
            $item = (array)$item;
            foreach ($item as $key=&gt;$val){
                $item[$key]  = $this-&gt;struct_to_array($val);
            }
        }
        return $item;
    }
   function xml_parser($str){
      $xml_parser = xml_parser_create();
      if(!xml_parse($xml_parser,$str,true)){
          xml_parser_free($xml_parser);
          return false;
      }else {
          return (json_decode(json_encode(simplexml_load_string($str)),true));
      }
  }

/**
* 转xml
* @param unknown $data
* @param string $rootNodeName
* @param number $stand
* @return mixed
*/
function arraytoXml($data,$stand=1,$rootNodeName = 'resp'){
        header("Content-type: text/xml");
        $standalone='';
        ($stand==1)&amp;&amp;$standalone="standalone='yes'";
        $xml = simplexml_load_string("&lt;?xml version='1.0' encoding='utf-8' $standalone ?&gt;&lt;$rootNodeName /&gt;");

   foreach($data as $key =&gt; $value){
       if (is_numeric($key)){
           $key = "unknownNode_". (string) $key;
       }
       $key = preg_replace('/[^a-z-_]/i', '', $key);
       if (is_array($value)){
           $node = $xml-&gt;addChild($key);
           $this-&gt;toXml($value, $rootNodeName, $node);
       }else{
           $value = htmlentities($value);
           $xml-&gt;addChild($key,$value);
       }
   }
   $reXml=$xml-&gt;asXML();
   
   //记日志
   $backtrace = debug_backtrace();
   array_shift($backtrace);
   $this-&gt;setLog($reXml,$backtrace[0]['function']);
   return $reXml;
}



////////
//////////////////获取属性等///////////////////////
     $ptXml=file_get_contents($url);
     
        
         $doc=new DOMDocument();
         $doc-&gt;loadXML($ptXml);
         $A=$doc-&gt;getElementsByTagName("request");
         
         $A=$A-&gt;item(0)-&gt;getElementsByTagName("amount");
         
         $win=doubleval($A-&gt;item(0)-&gt;getattribute('wins'));
         
         $jackpot=doubleval($A-&gt;item(0)-&gt;nodeValue);
///////////////////////////////////////////////////
 






</pre>
<br />