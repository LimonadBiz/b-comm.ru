---
title: duraki.php — скрипт отображающий давно не подключающихся пользователей с задолженостью
author: wel
type: post
date: 2012-01-14T23:43:17+00:00
url: /billing/duraki-php-скрипт-отображающий-давно-не-подк
wp-syntax-cache-content:
  - |
    a:1:{i:1;s:13436:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="php" style="font-family:monospace;"><span style="color: #000000; font-weight: bold;">&lt;?php</span>
    <span style="color: #b1b100;">include_once</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;top.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">include_once</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;engine.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000088;">$d</span><span style="color: #339933;">=</span><span style="color: #990000;">date</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;m&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">-</span><span style="color: #cc66cc;">2</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">if</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$d</span><span style="color: #339933;">&lt;</span><span style="color: #cc66cc;">10</span><span style="color: #009900;">&#41;</span>
        <span style="color: #000088;">$d</span><span style="color: #339933;">=</span><span style="color: #0000ff;">&quot;0&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$d</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;Подключалсь до &quot;</span><span style="color: #339933;">.</span><span style="color: #990000;">date</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;Y&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;-&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$d</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;-&quot;</span><span style="color: #339933;">.</span><span style="color: #990000;">date</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;d&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$ip</span><span style="color: #339933;">=</span><span style="color: #000088;">$_GET</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'ip'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #666666; font-style: italic;">//$status=$argv[2];</span>
    <span style="color: #000088;">$db</span><span style="color: #339933;">=</span><span style="color: #000000; font-weight: bold;">new</span> db_mysql<span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$db</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">init</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;10.200.205.224&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;updown&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;updownзфыы&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;freenibs&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000088;">$q</span><span style="color: #339933;">=</span><span style="color: #0000ff;">&quot;SELECT `users`.`user`,`users`.`last_connection`,`users`.`deposit`,`users`.`uid`,`packets`.`packet` FROM `users`,`packets` WHERE `users`.`last_connection` &lt;'&quot;</span><span style="color: #339933;">.</span><span style="color: #990000;">date</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;Y&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;-&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$d</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;-&quot;</span><span style="color: #339933;">.</span><span style="color: #990000;">date</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;d&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;' AND `users`.`deposit`&lt;0 AND `users`.`gid` not in ('35') AND `users`.`gid`=`packets`.`gid` &quot;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000088;">$q</span><span style="color: #339933;">=</span><span style="color: #0000ff;">&quot;
    SELECT
        `users`.`user`,`users`.`last_connection`,`users`.`deposit`,`users`.`uid`,`packets`.`packet`
    FROM
        `users`,`packets`
    WHERE
        `users`.`gid`=`packets`.`gid`
    &nbsp;
    ORDER BY `last_connection` DESC&quot;</span><span style="color: #339933;">;</span>
    <span style="color: #666666; font-style: italic;">//('35','11','6')</span>
    <span style="color: #666666; font-style: italic;">//$q1=&quot;SELECT `freenibs`.`arpwatch`.`ip` , `freenibs`.`arpwatch`.`arp`,`mac`.`host`.`host` FROM `freenibs`.`arpwatch` INNER JOIN `mac`.`host` ON `freenibs`.`arpwatch`.`ip` = `mac`.`host`.`ipv4` AND `mac`.`host`.`en`='e'&quot;;</span>
    &nbsp;
    &nbsp;
    <span style="color: #000088;">$db</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">query</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$q</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000088;">$n</span><span style="color: #339933;">=</span><span style="color: #000088;">$db</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">num_rows</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">if</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$n</span><span style="color: #339933;">&gt;</span><span style="color: #cc66cc;">0</span><span style="color: #009900;">&#41;</span>
    <span style="color: #009900;">&#123;</span>
    <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;TABLE border='1'&gt;
        &lt;TR&gt;&lt;TD&gt;n&lt;/TD&gt;&lt;TD&gt;user&lt;/TD&gt;&lt;TD&gt;&lt;B&gt;Last connection&lt;/B&gt;&lt;/TD&gt;&lt;TD&gt;Paket&lt;/TD&gt;&lt;/TR&gt;&quot;</span><span style="color: #339933;">;</span>
        <span style="color: #b1b100;">for</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$i</span><span style="color: #339933;">=</span><span style="color: #cc66cc;">0</span><span style="color: #339933;">;</span><span style="color: #000088;">$i</span><span style="color: #339933;">&lt;</span><span style="color: #000088;">$n</span><span style="color: #339933;">;</span><span style="color: #000088;">$i</span><span style="color: #339933;">++</span><span style="color: #009900;">&#41;</span>
            <span style="color: #009900;">&#123;</span>
            <span style="color: #000088;">$ii</span><span style="color: #339933;">=</span><span style="color: #000088;">$i</span><span style="color: #339933;">;</span>
            <span style="color: #000088;">$ii</span><span style="color: #339933;">++;</span>
            <span style="color: #000088;">$row</span><span style="color: #339933;">=</span><span style="color: #000088;">$db</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">fetch_array</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
                <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;TR&gt;&lt;TD&gt;&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$ii</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;&lt;/TD&gt;&lt;TD&gt;&lt;a href=<span style="color: #000099; font-weight: bold;">\&quot;</span>edit_user.php?uid=&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'uid'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;<span style="color: #000099; font-weight: bold;">\&quot;</span> &gt; &quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'user'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;&lt;/a&gt;&lt;/TD&gt;&lt;TD&gt;&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'last_connection'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;&lt;/TD&gt;
            &lt;TD&gt;&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'packet'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;&lt;/TD&gt;&lt;/TR&gt;&quot;</span><span style="color: #339933;">;</span>
            <span style="color: #000088;">$deposit</span> <span style="color: #339933;">+=</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'deposit'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
            <span style="color: #009900;">&#125;</span>
    <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;TR&gt;&lt;TD&gt;&lt;/TD&gt;&lt;TD&gt;&lt;/TD&gt;&lt;TD&gt;&lt;/TD&gt;&lt;TD&gt;&lt;/TD&gt;&lt;/TR&gt;&quot;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;/TABLE&gt;&quot;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #009900;">&#125;</span>
    &nbsp;
    &nbsp;
    <span style="color: #339933;">@</span><span style="color: #000088;">$db</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">close_db</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">include_once</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;bottom.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000000; font-weight: bold;">?&gt;</span></pre></td></tr></table><p class="theCode" style="display:none;">&lt;?php
    include_once(&quot;top.php&quot;);
    include_once(&quot;engine.php&quot;);
    
    $d=date(&quot;m&quot;)-2;
    if($d&lt;10)
        $d=&quot;0&quot;.$d;
    echo &quot;Подключалсь до &quot;.date(&quot;Y&quot;).&quot;-&quot;.$d.&quot;-&quot;.date(&quot;d&quot;);
    $ip=$_GET['ip'];
    
    //$status=$argv[2];
    $db=new db_mysql();
    $db-&gt;init(&quot;10.200.205.224&quot;,&quot;updown&quot;,&quot;updownзфыы&quot;,&quot;freenibs&quot;);
    
    $q=&quot;SELECT `users`.`user`,`users`.`last_connection`,`users`.`deposit`,`users`.`uid`,`packets`.`packet` FROM `users`,`packets` WHERE `users`.`last_connection` &lt;'&quot;.date(&quot;Y&quot;).&quot;-&quot;.$d.&quot;-&quot;.date(&quot;d&quot;).&quot;' AND `users`.`deposit`&lt;0 AND `users`.`gid` not in ('35') AND `users`.`gid`=`packets`.`gid` &quot;;
    
    $q=&quot;
    SELECT
        `users`.`user`,`users`.`last_connection`,`users`.`deposit`,`users`.`uid`,`packets`.`packet`
    FROM
        `users`,`packets`
    WHERE
        `users`.`gid`=`packets`.`gid`
    
    ORDER BY `last_connection` DESC&quot;;
    //('35','11','6')
    //$q1=&quot;SELECT `freenibs`.`arpwatch`.`ip` , `freenibs`.`arpwatch`.`arp`,`mac`.`host`.`host` FROM `freenibs`.`arpwatch` INNER JOIN `mac`.`host` ON `freenibs`.`arpwatch`.`ip` = `mac`.`host`.`ipv4` AND `mac`.`host`.`en`='e'&quot;;
    
    
    $db-&gt;query($q);
    
    $n=$db-&gt;num_rows();
    if($n&gt;0)
    {
    echo &quot;&lt;TABLE border='1'&gt;
        &lt;TR&gt;&lt;TD&gt;n&lt;/TD&gt;&lt;TD&gt;user&lt;/TD&gt;&lt;TD&gt;&lt;B&gt;Last connection&lt;/B&gt;&lt;/TD&gt;&lt;TD&gt;Paket&lt;/TD&gt;&lt;/TR&gt;&quot;;
        for($i=0;$i&lt;$n;$i++)
            {
            $ii=$i;
            $ii++;
            $row=$db-&gt;fetch_array();
                echo &quot;&lt;TR&gt;&lt;TD&gt;&quot;.$ii.&quot;&lt;/TD&gt;&lt;TD&gt;&lt;a href=\&quot;edit_user.php?uid=&quot;.$row['uid'].&quot;\&quot; &gt; &quot;.$row['user'].&quot;&lt;/a&gt;&lt;/TD&gt;&lt;TD&gt;&quot;.$row['last_connection'].&quot;&lt;/TD&gt;
            &lt;TD&gt;&quot;.$row['packet'].&quot;&lt;/TD&gt;&lt;/TR&gt;&quot;;
            $deposit +=$row['deposit'];
            }
    echo &quot;&lt;TR&gt;&lt;TD&gt;&lt;/TD&gt;&lt;TD&gt;&lt;/TD&gt;&lt;TD&gt;&lt;/TD&gt;&lt;TD&gt;&lt;/TD&gt;&lt;/TR&gt;&quot;;
    
    echo &quot;&lt;/TABLE&gt;&quot;;
    
    }
    
    
    @$db-&gt;close_db();
    include_once(&quot;bottom.php&quot;);
    ?&gt;</p></div>
    ";}
categories:
  - billing
  - FreeNIBS
tags:
  - duraki.php

---
duraki.php — скрипт отображающий давно не подключающихся пользователей с задолженостью<!--more-->

<pre lang="php"><?php
include_once("top.php");
include_once("engine.php");

$d=date("m")-2;
if($d<10)
    $d="0".$d;
echo "Подключалсь до ".date("Y")."-".$d."-".date("d");
$ip=$_GET['ip'];

//$status=$argv[2];
$db=new db_mysql();
$db->init("10.200.205.224","updown","updownзфыы","freenibs");

$q="SELECT `users`.`user`,`users`.`last_connection`,`users`.`deposit`,`users`.`uid`,`packets`.`packet` FROM `users`,`packets` WHERE `users`.`last_connection` &lt;'".date("Y")."-".$d."-".date("d")."' AND `users`.`deposit`&lt;0 AND `users`.`gid` not in ('35') AND `users`.`gid`=`packets`.`gid` ";

$q="
SELECT
    `users`.`user`,`users`.`last_connection`,`users`.`deposit`,`users`.`uid`,`packets`.`packet`
FROM
    `users`,`packets`
WHERE
    `users`.`gid`=`packets`.`gid`

ORDER BY `last_connection` DESC";
//('35','11','6')
//$q1="SELECT `freenibs`.`arpwatch`.`ip` , `freenibs`.`arpwatch`.`arp`,`mac`.`host`.`host` FROM `freenibs`.`arpwatch` INNER JOIN `mac`.`host` ON `freenibs`.`arpwatch`.`ip` = `mac`.`host`.`ipv4` AND `mac`.`host`.`en`='e'";


$db->query($q);

$n=$db->num_rows();
if($n>0)
{
echo "

<TABLE border='1'>
  <TR>
    <TD>
      n
    </TD>
    
    <TD>
      user
    </TD>
    
    <TD>
      <B>Last connection</B>
    </TD>
    
    <TD>
      Paket
    </TD>
  </TR>";
      for($i=0;$i&lt;$n;$i++)
          {
          $ii=$i;
          $ii++;
          $row=$db->fetch_array();
              echo "
  
  <TR>
    <TD>
      ".$ii."
    </TD>
    
    <TD>
      &lt;a href=\"edit_user.php?uid=".$row['uid']."\" > ".$row['user']."&lt;/a>
    </TD>
    
    <TD>
      ".$row['last_connection']."
    </TD>
            
    
    <TD>
      ".$row['packet']."
    </TD>
  </TR>";
          $deposit +=$row['deposit'];
          }
  echo "
  
  <TR>
    <TD>
      
    </TD>
    
    <TD>
      
    </TD>
    
    <TD>
      
    </TD>
    
    <TD>
      
    </TD>
  </TR>";
  
  echo "
</TABLE>";

}


@$db->close_db();
include_once("bottom.php");
?>

</pre>