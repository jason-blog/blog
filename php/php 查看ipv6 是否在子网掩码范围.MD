<p>
	https://stackoverflow.com/questions/7951061/matching-ipv6-address-to-a-cidr-subnet
</p>
<p>
<pre class="prettyprint lang-js linenums">$ip='21DA:00D3:0000:2F3B:02AC:00FF:FE28:9C5A';
$cidrnet='21DA:00D3:0000:2F3B::/64';

// converts inet_pton output to string with bits
function inet_to_bits($inet) 
{
   $unpacked = unpack('A16', $inet);
   $unpacked = str_split($unpacked[1]);
   $binaryip = '';
   foreach ($unpacked as $char) {
             $binaryip .= str_pad(decbin(ord($char)), 8, '0', STR_PAD_LEFT);
   }
   return $binaryip;
}    

$ip = inet_pton($ip);
$binaryip=inet_to_bits($ip);

list($net,$maskbits)=explode('/',$cidrnet);
$net=inet_pton($net);
$binarynet=inet_to_bits($net);

$ip_net_bits=substr($binaryip,0,$maskbits);
$net_bits   =substr($binarynet,0,$maskbits);

if($ip_net_bits!==$net_bits) echo 'Not in subnet';
else echo 'In subnet';</pre>
</p>