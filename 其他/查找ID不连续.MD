select id+1 from `password` a<br />
where not exists(select * from `password` b where b.id = a.id + 1)<br />
and id &lt; (select MAX(id) from `password`)&nbsp;<br />