<pre class="prettyprint lang-php linenums">&lt;?php
header("Content-type:text/html;charset=utf-8");

set_time_limit(0);
error_reporting(E_ALL^E_NOTICE);

$dbConfig=array(
    'DB_HOST'=&gt;'localhost',
    'DB_USER'=&gt;'root',
    'DB_PWD'=&gt;'',
    'DB_NAME'=&gt;'d',
    'DB_PORT'=&gt;'3306',
    'DB_PREFIX'=&gt;'ab_'
    
);
define ( 'DB_CONFIG', serialize($dbConfig));
define ( 'DB_TIME_ZONE', '+8:00' );//+00:00
define ( 'DEFAULT_TIMEZONE', 'Asia/Shanghai' );//Etc/GMT


date_default_timezone_set(DEFAULT_TIMEZONE);
class mysqlSqlQuery{
    private  $dbhost;
    private  $dbuser;
    private  $dbpw;
    private  $dbname;
    private  $tablepre;
    public   $sql;
    /**
    * 构造函数 初始化配置项 
    */
    public function __construct(){
        $CONFIG=unserialize(DB_CONFIG);
        
        $this-&gt;dbhost=$CONFIG['DB_HOST'];
        $this-&gt;dbuser=$CONFIG['DB_USER'];
        $this-&gt;dbpw=$CONFIG['DB_PWD'];
        $this-&gt;dbname=$CONFIG['DB_NAME'];
        
        $this-&gt;dbport=$CONFIG['DB_PORT'];
        $this-&gt;tablepre=$CONFIG['DB_PREFIX'];
    }
    /**
    * 连接数据库
    */
    public function connects(){
        $con=new mysqli ( "$this-&gt;dbhost", "$this-&gt;dbuser", "$this-&gt;dbpw", "$this-&gt;dbname", "$this-&gt;dbport" );
        if (!$con)
        {
            die('Could not connect: ' . mysql_error());
        }
        $con-&gt;query('set names utf8');
        $con-&gt;query("set time_zone = '".DB_TIME_ZONE."';");
        
        return $con;
    }
  /**
   * insert操作
   * @param 操作的表名 $name
   * @param 操作的字段 $files
   * @param 新增的数据 $data
   * @return resource
   */
    public function inserts($name,$files='',$data=''){
        $con=$this-&gt;connects();
        if(!empty($name)){
            $sql="INSERT INTO {$this-&gt;tablepre}$name ($files) VALUES ($data)";
        }
        if($this-&gt;sql==true){
            echo '&lt;br/&gt;';
            echo $sql;
        }
        $result=$con-&gt;query($sql);
        $con-&gt;close();
        return $result;
    }
    
    /**
     * 执行一段sql
     * @param 执行的sql $sql
     * @return multitype:
     */
    public function querys($sql=''){
        $con=$this-&gt;connects();
        if(empty($sql)){
            $sql="SELECT COUNT(*) TABLES, table_schema FROM information_schema.TABLES WHERE table_schema = '$this-&gt;dbname' GROUP BY table_schema";
        }
        if($this-&gt;sql==true){
            echo '&lt;br/&gt;';
            echo $sql;
        }
        $result=$con-&gt;query($sql);
        $con-&gt;close();
        return $result;
    }
  
}</pre>
<br />