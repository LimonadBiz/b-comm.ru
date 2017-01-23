---
title: dhcp_unk.php
author: wel
type: post
date: 2012-01-14T23:39:50+00:00
url: /billing/dhcp_unk-php
wp-syntax-cache-content:
  - |
    a:1:{i:1;s:10813:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="php" style="font-family:monospace;"><span style="color: #000000; font-weight: bold;">&lt;?php</span>
    <span style="color: #b1b100;">include_once</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;top.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$link</span> <span style="color: #339933;">=</span> <span style="color: #339933;">@</span><span style="color: #990000;">mysql_connect</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">'10.200.205.224'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'dhcpd_log_unknow'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'hcpd_log_unknow'</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #339933;">!</span><span style="color: #000088;">$link</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
                <span style="color: #990000;">die</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">'Could not connect: '</span> <span style="color: #339933;">.</span> <span style="color: #990000;">mysql_error</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span>
    <span style="color: #000088;">$db_selected</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_select_db</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">'freenibs'</span><span style="color: #339933;">,</span> <span style="color: #000088;">$link</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000088;">$q</span><span style="color: #339933;">=</span><span style="color: #0000ff;">&quot;SELECT *
    FROM `dhcp_arp_unkn`
    ORDER BY `date` DESC&quot;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$q</span><span style="color: #339933;">=</span><span style="color: #0000ff;">&quot;
    &nbsp;
    SELECT `dhcp_arp_unkn`.`mac`, FROM_UNIXTIME(`dhcp_arp_unkn`.`date`) AS `date`,`dhcp_arp_unkn`.`vlan`,`users`.`user`,`users`.`uid`
     FROM `dhcp_arp_unkn` LEFT JOIN
     `users`
     ON
      `dhcp_arp_unkn`.`mac`=`users`.`mac_addr`
    &nbsp;
      ORDER BY `dhcp_arp_unkn`.`date` DESC
      &quot;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000088;">$result</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_query</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$q</span><span style="color: #339933;">,</span><span style="color: #000088;">$link</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$num_rows</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_num_rows</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;table border=1&gt;
        &lt;tr&gt;
            &lt;td&gt;N
            &lt;/td&gt;
            &lt;td&gt;mac&lt;/td&gt;
            &lt;td&gt;vlan&lt;/td&gt;
            &lt;td&gt;date&lt;/td&gt;
    &nbsp;
        &lt;/tr&gt;&quot;</span><span style="color: #339933;">;</span>
        <span style="color: #000088;">$i</span><span style="color: #339933;">=</span><span style="color: #cc66cc;">0</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">while</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$row</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_fetch_array</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #339933;">,</span> MYSQL_ASSOC<span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
               <span style="color: #666666; font-style: italic;">// printf (&quot;ID: %s  Name: %s&quot;, $row[0], $row[1]);</span>
                <span style="color: #000088;">$i</span><span style="color: #339933;">++;</span>
                 <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;
                  &lt;tr&gt;
                    &lt;td&gt;<span style="color: #006699; font-weight: bold;">$i</span>&lt;/td&gt;
                    &quot;</span><span style="color: #339933;">;</span>
                    <span style="color: #b1b100;">if</span><span style="color: #009900;">&#40;</span> <span style="color: #009900;">&#40;</span>int<span style="color: #009900;">&#41;</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'uid'</span><span style="color: #009900;">&#93;</span><span style="color: #009900;">&#41;</span> <span style="color: #339933;">&gt;</span><span style="color: #cc66cc;">1</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#123;</span>
                        <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;td&gt;&lt;a target=<span style="color: #000099; font-weight: bold;">\&quot;</span>_blank<span style="color: #000099; font-weight: bold;">\&quot;</span>  href=<span style="color: #000099; font-weight: bold;">\&quot;</span>/edit_user.php?uid=&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'uid'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot; <span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'mac'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;&lt;/a&gt;&lt;/td&gt;&quot;</span><span style="color: #339933;">;</span>
                    <span style="color: #009900;">&#125;</span><span style="color: #b1b100;">else</span><span style="color: #009900;">&#123;</span>
                        <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;td&gt;&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'mac'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;&lt;/td&gt;&quot;</span><span style="color: #339933;">;</span>
                    <span style="color: #009900;">&#125;</span>
    &nbsp;
                    <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;td&gt;&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'vlan'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;&lt;/td&gt;
                    &lt;td&gt;&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'date'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;&lt;/td&gt;
                  &lt;/tr&gt;
                 &quot;</span><span style="color: #339933;">;</span>
    &nbsp;
    &nbsp;
                    <span style="color: #009900;">&#125;</span>
    <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;/table&gt;&quot;</span><span style="color: #339933;">;</span>
                        <span style="color: #990000;">mysql_free_result</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #339933;">@</span><span style="color: #990000;">mysql_close</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$link</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    &nbsp;
    &nbsp;
    <span style="color: #000000; font-weight: bold;">?&gt;</span></pre></td></tr></table><p class="theCode" style="display:none;">&lt;?php
    include_once(&quot;top.php&quot;);
    $link = @mysql_connect('10.200.205.224', 'dhcpd_log_unknow', 'hcpd_log_unknow');
    if (!$link) {
                die('Could not connect: ' . mysql_error());
    }
    $db_selected = mysql_select_db('freenibs', $link);
    
    $q=&quot;SELECT *
    FROM `dhcp_arp_unkn`
    ORDER BY `date` DESC&quot;;
    $q=&quot;
    
    SELECT `dhcp_arp_unkn`.`mac`, FROM_UNIXTIME(`dhcp_arp_unkn`.`date`) AS `date`,`dhcp_arp_unkn`.`vlan`,`users`.`user`,`users`.`uid`
     FROM `dhcp_arp_unkn` LEFT JOIN
     `users`
     ON
      `dhcp_arp_unkn`.`mac`=`users`.`mac_addr`
    
      ORDER BY `dhcp_arp_unkn`.`date` DESC
      &quot;;
    
    $result = mysql_query($q,$link);
    $num_rows = mysql_num_rows($result);
    echo &quot;&lt;table border=1&gt;
        &lt;tr&gt;
            &lt;td&gt;N
            &lt;/td&gt;
            &lt;td&gt;mac&lt;/td&gt;
            &lt;td&gt;vlan&lt;/td&gt;
            &lt;td&gt;date&lt;/td&gt;
    
        &lt;/tr&gt;&quot;;
        $i=0;
    while ($row = mysql_fetch_array($result, MYSQL_ASSOC)) {
               // printf (&quot;ID: %s  Name: %s&quot;, $row[0], $row[1]);
                $i++;
                 echo &quot;
                  &lt;tr&gt;
                    &lt;td&gt;$i&lt;/td&gt;
                    &quot;;
                    if( (int)($row['uid']) &gt;1){
                        echo &quot;&lt;td&gt;&lt;a target=\&quot;_blank\&quot;  href=\&quot;/edit_user.php?uid=&quot;.$row['uid'].&quot; \&quot;&gt;&quot;.$row['mac'].&quot;&lt;/a&gt;&lt;/td&gt;&quot;;
                    }else{
                        echo &quot;&lt;td&gt;&quot;.$row['mac'].&quot;&lt;/td&gt;&quot;;
                    }
    
                    echo &quot;&lt;td&gt;&quot;.$row['vlan'].&quot;&lt;/td&gt;
                    &lt;td&gt;&quot;.$row['date'].&quot;&lt;/td&gt;
                  &lt;/tr&gt;
                 &quot;;
    
    
                    }
    echo &quot;&lt;/table&gt;&quot;;
                        mysql_free_result($result);
    
    @mysql_close($link);
    
    
    
    ?&gt;</p></div>
    ";}
categories:
  - billing
  - FreeNIBS
tags:
  - dhcp_unk.php

---
dhcp_unk.php<!--more-->

<pre lang="php"><?php
include_once("top.php");
$link = @mysql_connect('10.200.205.224', 'dhcpd_log_unknow', 'hcpd_log_unknow');
if (!$link) {
            die('Could not connect: ' . mysql_error());
}
$db_selected = mysql_select_db('freenibs', $link);

$q="SELECT *
FROM `dhcp_arp_unkn`
ORDER BY `date` DESC";
$q="

SELECT `dhcp_arp_unkn`.`mac`, FROM_UNIXTIME(`dhcp_arp_unkn`.`date`) AS `date`,`dhcp_arp_unkn`.`vlan`,`users`.`user`,`users`.`uid`
 FROM `dhcp_arp_unkn` LEFT JOIN
 `users`
 ON
  `dhcp_arp_unkn`.`mac`=`users`.`mac_addr`

  ORDER BY `dhcp_arp_unkn`.`date` DESC
  ";

$result = mysql_query($q,$link);
$num_rows = mysql_num_rows($result);
echo "<table border=1>
    

<tr>
  <td>
    N
            
  </td>
          
  
  <td>
    mac
  </td>
          
  
  <td>
    vlan
  </td>
          
  
  <td>
    date
  </td>
  
      
</tr>";
    $i=0;
while ($row = mysql_fetch_array($result, MYSQL_ASSOC)) {
           // printf ("ID: %s  Name: %s", $row[0], $row[1]);
            $i++;
             echo "
              

<tr>
  <td>
    $i
  </td>
                  ";
                  if( (int)($row['uid']) >1){
                      echo "
  
  <td>
    &lt;a target=\"_blank\"  href=\"/edit_user.php?uid=".$row['uid']." \">".$row['mac']."&lt;/a>
  </td>";
                  }else{
                      echo "
  
  <td>
    ".$row['mac']."
  </td>";
                  }
  
                  echo "
  
  <td>
    ".$row['vlan']."
  </td>
                  
  
  <td>
    ".$row['date']."
  </td>
                
</tr>
             ";


                }
echo "&lt;/table>";
                    mysql_free_result($result);

@mysql_close($link);



?>

</pre>