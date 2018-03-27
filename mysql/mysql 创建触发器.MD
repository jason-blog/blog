DROP TRIGGER IF EXISTS t_afterinsert_on_tab1;<br />
CREATE TRIGGER t_afterinsert_on_tab1&nbsp;<br />
AFTER INSERT ON tab1<br />
FOR EACH ROW<br />
BEGIN<br />
&nbsp; insert into tab2(tab2_id) values(new.tab1_id);<br />
END;<br />