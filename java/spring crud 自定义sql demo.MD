<pre class="prettyprint lang-java linenums">package black.box.gi.nyx.repository;

import java.util.List;



@Repository
public interface test extends CrudRepository&lt;GrUser, String&gt; {

    @Query(nativeQuery=true,value="SELECT username,gr_entity_id,token,user_id,id FROM gr_user" )
    List&lt;GrUser&gt; getIn();
    
    @Query(nativeQuery=true,value="SELECT username,gr_entity_id,token,user_id,id FROM gr_user where username = :username" )
    List&lt;GrUser&gt; getInWhere(@Param("username") String username);
}
</pre>