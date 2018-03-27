<pre class="prettyprint lang-js linenums">*filter
:INPUT ACCEPT [62:4384]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [34:4736]
:http-users - [0:0]
:ssh-users - [0:0]
-A INPUT -i lo -j ACCEPT
-A INPUT -p tcp -m tcp -m multiport --dports 80,443 -m state --state NEW -j http-users
-A INPUT -p tcp -m tcp -m multiport --dports 22 -m state --state NEW -j ssh-users
-A http-users -s 10.1.0.1/32 -m comment --comment "test commit" -j ACCEPT
-A http-users -m iprange --src-range 173.194.0.0-173.194.255.255 -m comment --comment "test comment" -j ACCEPT
-A http-users -j DROP
-A http-users -j ACCEPT
-A ssh-users -s 10.1.0.1/32 -m comment --comment "test coment" -j ACCEPT
-A ssh-users -m iprange --src-range 173.194.0.0-173.194.255.255 -m comment --comment "test comment" -j ACCEPT
-A ssh-users -j LOG --log-prefix "SSH-In: "
-A ssh-users -j DROP
COMMIT</pre>