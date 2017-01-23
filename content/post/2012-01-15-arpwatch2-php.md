---
title: arpwatch2.php
author: wel
type: post
date: 2012-01-14T22:09:38+00:00
url: /billing/arpwatch2-php
wp-syntax-cache-content:
  - |
    a:1:{i:1;s:19624:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="php" style="font-family:monospace;">&nbsp;
    <span style="color: #000000; font-weight: bold;">&lt;?php</span>
    <span style="color: #b1b100;">include_once</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;top.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">include_once</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;engine.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$prev_month_date_start</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mktime</span> <span style="color: #009900;">&#40;</span><span style="color: #cc66cc;">0</span><span style="color: #339933;">,</span><span style="color: #cc66cc;">0</span><span style="color: #339933;">,</span><span style="color: #cc66cc;">0</span><span style="color: #339933;">,</span><span style="color: #990000;">date</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;m&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">-</span><span style="color: #cc66cc;">1</span><span style="color: #339933;">,</span><span style="color: #cc66cc;">1</span><span style="color: #339933;">,</span><span style="color: #990000;">date</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;Y&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    &nbsp;
    <span style="color: #000088;">$ip</span><span style="color: #339933;">=</span><span style="color: #000088;">$_GET</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'ip'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #666666; font-style: italic;">//$status=$argv[2];</span>
    <span style="color: #000088;">$db</span><span style="color: #339933;">=</span><span style="color: #000000; font-weight: bold;">new</span> db_mysql<span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$db</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">init</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;10.200.1.1&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;updown&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;updown&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;freenibs&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000088;">$db1</span><span style="color: #339933;">=</span><span style="color: #000000; font-weight: bold;">new</span> db_mysql<span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$db1</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">init</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;10.200.1.1&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;updown&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;updown&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;mac&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000088;">$q</span><span style="color: #339933;">=</span><span style="color: #0000ff;">&quot;SELECT `ip`,`arp` FROM `arpwatch`&quot;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #666666; font-style: italic;">//$q1=&quot;SELECT `freenibs`.`arpwatch`.`ip` , `freenibs`.`arpwatch`.`arp`,`mac`.`host`.`host` FROM `freenibs`.`arpwatch` INNER JOIN `mac`.`host` ON `freenibs`.`arpwatch`.`ip` = `mac`.`host`.`ipv4` AND `mac`.`host`.`en`='e'&quot;;</span>
    &nbsp;
    &nbsp;
    <span style="color: #000088;">$db</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">query</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$q</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000088;">$n</span><span style="color: #339933;">=</span><span style="color: #000088;">$db</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">num_rows</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">if</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$n</span><span style="color: #339933;">&gt;</span><span style="color: #cc66cc;">0</span><span style="color: #009900;">&#41;</span>
    <span style="color: #009900;">&#123;</span>
    <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;TABLE border='1'&gt;
        &lt;TR&gt;&lt;TD&gt;&lt;B&gt;ip&lt;/B&gt;&lt;/TD&gt;&lt;TD&gt;&lt;B&gt;mac-adress&lt;/B&gt;&lt;/TD&gt;&lt;TD&gt;mac for this ip in DHCP&lt;/TD&gt;&lt;TD&gt;user who login from ip&lt;/TD&gt;&lt;/TR&gt;&quot;</span><span style="color: #339933;">;</span>
        <span style="color: #b1b100;">for</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$i</span><span style="color: #339933;">=</span><span style="color: #cc66cc;">0</span><span style="color: #339933;">;</span><span style="color: #000088;">$i</span><span style="color: #339933;">&lt;</span><span style="color: #000088;">$n</span><span style="color: #339933;">;</span><span style="color: #000088;">$i</span><span style="color: #339933;">++</span><span style="color: #009900;">&#41;</span>
            <span style="color: #009900;">&#123;</span>
            <span style="color: #000088;">$row</span><span style="color: #339933;">=</span><span style="color: #000088;">$db</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">fetch_array</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
                <span style="color: #000088;">$q</span><span style="color: #339933;">=</span><span style="color: #0000ff;">&quot;SELECT `mac`.`host`.`mac` FROM `mac`.`host` WHERE `mac`.`host`.`ipv4`='&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'ip'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;'&quot;</span><span style="color: #339933;">;</span>
    <span style="color: #666666; font-style: italic;">//          echo $q;</span>
                <span style="color: #000088;">$db1</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">set_db</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;mac&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
                <span style="color: #000088;">$db1</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">query</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$q</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
                <span style="color: #000088;">$n1</span><span style="color: #339933;">=</span><span style="color: #000088;">$db1</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">num_rows</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
                <span style="color: #990000;">unset</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$row1</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
                <span style="color: #b1b100;">if</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$n1</span><span style="color: #339933;">&gt;</span><span style="color: #cc66cc;">0</span><span style="color: #009900;">&#41;</span>
                <span style="color: #009900;">&#123;</span>
    &nbsp;
                        <span style="color: #000088;">$row1</span><span style="color: #339933;">=</span><span style="color: #000088;">$db1</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">fetch_array</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
                <span style="color: #009900;">&#125;</span>
                <span style="color: #000088;">$iplocal</span><span style="color: #339933;">=</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'ip'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
                  <span style="color: #000088;">$q</span><span style="color: #339933;">=</span><span style="color: #0000ff;">&quot;SELECT `freenibs`.`users`.`user`,`freenibs`.`users`.`uid` FROM `freenibs`.`users` INNER JOIN `freenibs`.`actions` ON `freenibs`.`users`.`framed_ip`=`freenibs`.`actions`.`ip` AND `freenibs`.`actions`.`call_from`='&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$iplocal</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;' AND `freenibs`.`actions`.`stop_time`&gt; FROM_UNIXTIME(&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$prev_month_date_start</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;)  group by `freenibs`.`users`.`user`&quot;</span><span style="color: #339933;">;</span>
    <span style="color: #666666; font-style: italic;">//            $q=&quot;SELECT `freenibs`.`users`.`user` FROM `freenibs`.`users` INNER JOIN `freenibs`.`actions` ON `freenibs`.`users`.`framed_ip`=`freenibs`.`actions`.`ip` AND `freenibs`.`actions`.`call_from`='&quot;.$iplocal.&quot;'  group by `freenibs`.`users`.`user` LIMIT 10&quot;;</span>
    <span style="color: #666666; font-style: italic;">//        echo $q;</span>
                <span style="color: #000088;">$db1</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">set_db</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;freenibs&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
                <span style="color: #000088;">$db1</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">query</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$q</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
                <span style="color: #000088;">$n1</span><span style="color: #339933;">=</span><span style="color: #cc66cc;">0</span><span style="color: #339933;">;</span>
                <span style="color: #000088;">$n1</span><span style="color: #339933;">=</span><span style="color: #000088;">$db1</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">num_rows</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
                <span style="color: #990000;">unset</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$user</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
                <span style="color: #b1b100;">if</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$n1</span><span style="color: #339933;">&gt;</span><span style="color: #cc66cc;">0</span><span style="color: #009900;">&#41;</span>
                    <span style="color: #009900;">&#123;</span>
                        <span style="color: #b1b100;">for</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$i1</span><span style="color: #339933;">=</span><span style="color: #cc66cc;">0</span><span style="color: #339933;">;</span><span style="color: #000088;">$i1</span><span style="color: #339933;">&lt;</span><span style="color: #000088;">$n1</span><span style="color: #339933;">;</span><span style="color: #000088;">$i1</span><span style="color: #339933;">++</span><span style="color: #009900;">&#41;</span>
                        <span style="color: #009900;">&#123;</span>
                                <span style="color: #000088;">$row2</span><span style="color: #339933;">=</span><span style="color: #000088;">$db1</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">fetch_array</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
                                <span style="color: #000088;">$user</span> <span style="color: #339933;">.=</span><span style="color: #0000ff;">&quot;  &lt;a href=<span style="color: #000099; font-weight: bold;">\&quot;</span>edit_user.php?uid=&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$row2</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'uid'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$row2</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'user'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;&lt;/a&gt;<span style="color: #000099; font-weight: bold;">\n</span>&quot;</span><span style="color: #339933;">;</span>
                        <span style="color: #009900;">&#125;</span>
                    <span style="color: #009900;">&#125;</span>
    &nbsp;
    &nbsp;
    &nbsp;
                <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;TR&gt;&lt;TD&gt;&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'ip'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;&lt;/TD&gt;&lt;TD&gt;&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'arp'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;&lt;/TD&gt;&lt;TD&gt;&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$row1</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'mac'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;&lt;/TD&gt;&lt;TD&gt;<span style="color: #006699; font-weight: bold;">$user</span>&lt;/TD&gt;&lt;/TR&gt;&quot;</span><span style="color: #339933;">;</span>
    &nbsp;
            <span style="color: #009900;">&#125;</span>
    <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;/TABLE&gt;&quot;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #009900;">&#125;</span>
    &nbsp;
    <span style="color: #339933;">@</span><span style="color: #000088;">$db</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">close_db</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">include_once</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;bottom.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000000; font-weight: bold;">?&gt;</span></pre></td></tr></table><p class="theCode" style="display:none;">
    &lt;?php
    include_once(&quot;top.php&quot;);
    include_once(&quot;engine.php&quot;);
    $prev_month_date_start = mktime (0,0,0,date(&quot;m&quot;)-1,1,date(&quot;Y&quot;));
    
    
    $ip=$_GET['ip'];
    
    //$status=$argv[2];
    $db=new db_mysql();
    $db-&gt;init(&quot;10.200.1.1&quot;,&quot;updown&quot;,&quot;updown&quot;,&quot;freenibs&quot;);
    
    $db1=new db_mysql();
    $db1-&gt;init(&quot;10.200.1.1&quot;,&quot;updown&quot;,&quot;updown&quot;,&quot;mac&quot;);
    
    $q=&quot;SELECT `ip`,`arp` FROM `arpwatch`&quot;;
    
    //$q1=&quot;SELECT `freenibs`.`arpwatch`.`ip` , `freenibs`.`arpwatch`.`arp`,`mac`.`host`.`host` FROM `freenibs`.`arpwatch` INNER JOIN `mac`.`host` ON `freenibs`.`arpwatch`.`ip` = `mac`.`host`.`ipv4` AND `mac`.`host`.`en`='e'&quot;;
    
    
    $db-&gt;query($q);
    
    $n=$db-&gt;num_rows();
    if($n&gt;0)
    {
    echo &quot;&lt;TABLE border='1'&gt;
        &lt;TR&gt;&lt;TD&gt;&lt;B&gt;ip&lt;/B&gt;&lt;/TD&gt;&lt;TD&gt;&lt;B&gt;mac-adress&lt;/B&gt;&lt;/TD&gt;&lt;TD&gt;mac for this ip in DHCP&lt;/TD&gt;&lt;TD&gt;user who login from ip&lt;/TD&gt;&lt;/TR&gt;&quot;;
        for($i=0;$i&lt;$n;$i++)
            {
            $row=$db-&gt;fetch_array();
    
                $q=&quot;SELECT `mac`.`host`.`mac` FROM `mac`.`host` WHERE `mac`.`host`.`ipv4`='&quot;.$row['ip'].&quot;'&quot;;
    //          echo $q;
                $db1-&gt;set_db(&quot;mac&quot;);
                $db1-&gt;query($q);
                $n1=$db1-&gt;num_rows();
                unset($row1);
                if($n1&gt;0)
                {
    
                        $row1=$db1-&gt;fetch_array();
                }
                $iplocal=$row['ip'];
                  $q=&quot;SELECT `freenibs`.`users`.`user`,`freenibs`.`users`.`uid` FROM `freenibs`.`users` INNER JOIN `freenibs`.`actions` ON `freenibs`.`users`.`framed_ip`=`freenibs`.`actions`.`ip` AND `freenibs`.`actions`.`call_from`='&quot;.$iplocal.&quot;' AND `freenibs`.`actions`.`stop_time`&gt; FROM_UNIXTIME(&quot;.$prev_month_date_start.&quot;)  group by `freenibs`.`users`.`user`&quot;;
    //            $q=&quot;SELECT `freenibs`.`users`.`user` FROM `freenibs`.`users` INNER JOIN `freenibs`.`actions` ON `freenibs`.`users`.`framed_ip`=`freenibs`.`actions`.`ip` AND `freenibs`.`actions`.`call_from`='&quot;.$iplocal.&quot;'  group by `freenibs`.`users`.`user` LIMIT 10&quot;;
    //        echo $q;
                $db1-&gt;set_db(&quot;freenibs&quot;);
    
                $db1-&gt;query($q);
                $n1=0;
                $n1=$db1-&gt;num_rows();
                unset($user);
                if($n1&gt;0)
                    {
                        for($i1=0;$i1&lt;$n1;$i1++)
                        {
                                $row2=$db1-&gt;fetch_array();
                                $user .=&quot;  &lt;a href=\&quot;edit_user.php?uid=&quot;.$row2['uid'].&quot;\&quot;&gt;&quot;.$row2['user'].&quot;&lt;/a&gt;\n&quot;;
                        }
                    }
    
    
    
                echo &quot;&lt;TR&gt;&lt;TD&gt;&quot;.$row['ip'].&quot;&lt;/TD&gt;&lt;TD&gt;&quot;.$row['arp'].&quot;&lt;/TD&gt;&lt;TD&gt;&quot;.$row1['mac'].&quot;&lt;/TD&gt;&lt;TD&gt;$user&lt;/TD&gt;&lt;/TR&gt;&quot;;
    
            }
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
  - arpwatch2.php

---
arpwatch2.php — скрипт, который отображает кто и с какого (ип или мак-адресса) подключался к серверу
  
<!--more-->

<pre lang="php"><?php
include_once("top.php");
include_once("engine.php");
$prev_month_date_start = mktime (0,0,0,date("m")-1,1,date("Y"));


$ip=$_GET['ip'];

//$status=$argv[2];
$db=new db_mysql();
$db->init("10.200.1.1","updown","updown","freenibs");

$db1=new db_mysql();
$db1->init("10.200.1.1","updown","updown","mac");

$q="SELECT `ip`,`arp` FROM `arpwatch`";

//$q1="SELECT `freenibs`.`arpwatch`.`ip` , `freenibs`.`arpwatch`.`arp`,`mac`.`host`.`host` FROM `freenibs`.`arpwatch` INNER JOIN `mac`.`host` ON `freenibs`.`arpwatch`.`ip` = `mac`.`host`.`ipv4` AND `mac`.`host`.`en`='e'";


$db->query($q);

$n=$db->num_rows();
if($n>0)
{
echo "

<TABLE border='1'>
  <TR>
    <TD>
      <B>ip</B>
    </TD>
    
    <TD>
      <B>mac-adress</B>
    </TD>
    
    <TD>
      mac for this ip in DHCP
    </TD>
    
    <TD>
      user who login from ip
    </TD>
  </TR>";
      for($i=0;$i&lt;$n;$i++)
          {
          $row=$db->fetch_array();
  
              $q="SELECT `mac`.`host`.`mac` FROM `mac`.`host` WHERE `mac`.`host`.`ipv4`='".$row['ip']."'";
  //          echo $q;
              $db1->set_db("mac");
              $db1->query($q);
              $n1=$db1->num_rows();
              unset($row1);
              if($n1>0)
              {
  
                      $row1=$db1->fetch_array();
              }
              $iplocal=$row['ip'];
                $q="SELECT `freenibs`.`users`.`user`,`freenibs`.`users`.`uid` FROM `freenibs`.`users` INNER JOIN `freenibs`.`actions` ON `freenibs`.`users`.`framed_ip`=`freenibs`.`actions`.`ip` AND `freenibs`.`actions`.`call_from`='".$iplocal."' AND `freenibs`.`actions`.`stop_time`> FROM_UNIXTIME(".$prev_month_date_start.")  group by `freenibs`.`users`.`user`";
  //            $q="SELECT `freenibs`.`users`.`user` FROM `freenibs`.`users` INNER JOIN `freenibs`.`actions` ON `freenibs`.`users`.`framed_ip`=`freenibs`.`actions`.`ip` AND `freenibs`.`actions`.`call_from`='".$iplocal."'  group by `freenibs`.`users`.`user` LIMIT 10";
  //        echo $q;
              $db1->set_db("freenibs");
  
              $db1->query($q);
              $n1=0;
              $n1=$db1->num_rows();
              unset($user);
              if($n1>0)
                  {
                      for($i1=0;$i1&lt;$n1;$i1++)
                      {
                              $row2=$db1->fetch_array();
                              $user .="  &lt;a href=\"edit_user.php?uid=".$row2['uid']."\">".$row2['user']."&lt;/a>\n";
                      }
                  }
  
  
  
              echo "
  
  <TR>
    <TD>
      ".$row['ip']."
    </TD>
    
    <TD>
      ".$row['arp']."
    </TD>
    
    <TD>
      ".$row1['mac']."
    </TD>
    
    <TD>
      $user
    </TD>
  </TR>";
  
          }
  echo "
</TABLE>";

}

@$db->close_db();
include_once("bottom.php");
?>

</pre>