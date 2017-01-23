---
title: callback_changepacket.php и callback_changepacket_local.php — скрипт для отработки при вызове в веб-интерфейсе AJAX функций
author: wel
type: post
date: 2012-01-14T23:27:16+00:00
url: /billing/callback_changepacket-php-и-callback_changepacket_local-php-скрипт-для-отработки-пр
wp-syntax-cache-content:
  - |
    a:2:{i:1;s:11248:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="php" style="font-family:monospace;"><span style="color: #000000; font-weight: bold;">&lt;?php</span>
    <span style="color: #000088;">$reai_ip_gids</span><span style="color: #339933;">=</span><span style="color: #990000;">array</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">'14'</span> <span style="color: #339933;">=&gt;</span> <span style="color: #009900; font-weight: bold;">null</span><span style="color: #339933;">,</span>
                <span style="color: #0000ff;">'11'</span><span style="color: #339933;">=&gt;</span> <span style="color: #009900; font-weight: bold;">null</span><span style="color: #339933;">,</span><span style="color: #0000ff;">'30'</span><span style="color: #339933;">=&gt;</span> <span style="color: #009900; font-weight: bold;">null</span><span style="color: #339933;">,</span><span style="color: #0000ff;">'28'</span><span style="color: #339933;">=&gt;</span> <span style="color: #009900; font-weight: bold;">null</span><span style="color: #339933;">,</span>
                <span style="color: #0000ff;">'29'</span><span style="color: #339933;">=&gt;</span> <span style="color: #009900; font-weight: bold;">null</span><span style="color: #339933;">,</span><span style="color: #0000ff;">'36'</span><span style="color: #339933;">=&gt;</span> <span style="color: #009900; font-weight: bold;">null</span><span style="color: #339933;">,</span><span style="color: #0000ff;">'15'</span><span style="color: #339933;">=&gt;</span> <span style="color: #009900; font-weight: bold;">null</span><span style="color: #339933;">,</span>
                <span style="color: #0000ff;">'16'</span><span style="color: #339933;">=&gt;</span> <span style="color: #009900; font-weight: bold;">null</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000088;">$link</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_connect</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">'10.200.205.224'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'freenibs'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'freenibs'</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #339933;">!</span><span style="color: #000088;">$link</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
            <span style="color: #990000;">die</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">'Could not connect: '</span> <span style="color: #339933;">.</span> <span style="color: #990000;">mysql_error</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span>
    &nbsp;
    &nbsp;
    <span style="color: #000088;">$db_selected</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_select_db</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">'freenibs'</span><span style="color: #339933;">,</span> <span style="color: #000088;">$link</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #339933;">!</span><span style="color: #000088;">$db_selected</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
            <span style="color: #990000;">die</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">'Can\'t use  : '</span> <span style="color: #339933;">.</span> <span style="color: #990000;">mysql_error</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span>
    <span style="color: #000088;">$net_id</span><span style="color: #339933;">=</span><span style="color: #cc66cc;">0</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000088;">$gid</span><span style="color: #339933;">=</span><span style="color: #009900;">&#40;</span>int<span style="color: #009900;">&#41;</span><span style="color: #990000;">trim</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$_GET</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'gid'</span><span style="color: #009900;">&#93;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">if</span><span style="color: #009900;">&#40;</span><span style="color: #990000;">array_key_exists</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$gid</span><span style="color: #339933;">,</span><span style="color: #000088;">$reai_ip_gids</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#123;</span>
        <span style="color: #000088;">$net_id</span><span style="color: #339933;">=</span><span style="color: #cc66cc;">12</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span><span style="color: #b1b100;">else</span><span style="color: #009900;">&#123;</span>
        <span style="color: #000088;">$net_id</span><span style="color: #339933;">=</span><span style="color: #cc66cc;">4</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span>
    <span style="color: #000088;">$q</span><span style="color: #339933;">=</span><span style="color: #0000ff;">&quot;SELECT * FROM  `ip_manage` WHERE `net_id`='&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$net_id</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;' AND `uid`='0'&quot;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$result</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_query</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$q</span><span style="color: #339933;">,</span><span style="color: #000088;">$link</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$ips</span><span style="color: #339933;">=</span><span style="color: #990000;">array</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;gid:  <span style="color: #006699; font-weight: bold;">$gid</span>  net_id <span style="color: #006699; font-weight: bold;">$net_id</span> &lt;select name=<span style="color: #000099; font-weight: bold;">\&quot;</span>ip_net<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;
    &nbsp;
    &quot;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$i1</span><span style="color: #339933;">=</span><span style="color: #cc66cc;">1</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">while</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$row</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_fetch_assoc</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
        <span style="color: #666666; font-style: italic;">//$str.=$row['ip'].&quot; &quot;;</span>
        <span style="color: #000088;">$ips</span><span style="color: #009900;">&#91;</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">=</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'ip'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span><span style="color: #000088;">$i1</span><span style="color: #339933;">++;</span>
        <span style="color: #666666; font-style: italic;">//echo &quot;&lt;option value=\&quot;&quot;.$i1.&quot;\&quot;&gt;&quot;.$row['ip'].&quot;&lt;/option&gt; &quot;;</span>
        <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;option &gt;&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'ip'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;&lt;/option&gt; &quot;</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span>
    <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;/select&gt;&quot;</span><span style="color: #339933;">;</span>
    &nbsp;
         <span style="color: #666666; font-style: italic;">/*
          * echo json_encode(array(
            'jsArr'=&gt;$row
            ));
        */</span>
       <span style="color: #666666; font-style: italic;">//  echo json_encode($row);</span>
    <span style="color: #666666; font-style: italic;">//    echo $row['ip'];</span>
    <span style="color: #666666; font-style: italic;">//echo $_GET['gid'];</span>
    <span style="color: #990000;">mysql_close</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$link</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span></pre></td></tr></table><p class="theCode" style="display:none;">&lt;?php
    $reai_ip_gids=array('14' =&gt; null,
                '11'=&gt; null,'30'=&gt; null,'28'=&gt; null,
                '29'=&gt; null,'36'=&gt; null,'15'=&gt; null,
                '16'=&gt; null);
    
    $link = mysql_connect('10.200.205.224', 'freenibs', 'freenibs');
    if (!$link) {
            die('Could not connect: ' . mysql_error());
    }
    
    
    $db_selected = mysql_select_db('freenibs', $link);
    if (!$db_selected) {
            die ('Can\'t use  : ' . mysql_error());
    }
    $net_id=0;
    
    $gid=(int)trim($_GET['gid']);
    if(array_key_exists($gid,$reai_ip_gids)){
        $net_id=12;
    }else{
        $net_id=4;
    }
    $q=&quot;SELECT * FROM  `ip_manage` WHERE `net_id`='&quot;.$net_id.&quot;' AND `uid`='0'&quot;;
    $result = mysql_query($q,$link);
    $ips=array();
    
    echo &quot;gid:  $gid  net_id $net_id &lt;select name=\&quot;ip_net\&quot;&gt;
    
    &quot;;
    $i1=1;
    while ($row = mysql_fetch_assoc($result)) {
        //$str.=$row['ip'].&quot; &quot;;
        $ips[]=$row['ip'];$i1++;
        //echo &quot;&lt;option value=\&quot;&quot;.$i1.&quot;\&quot;&gt;&quot;.$row['ip'].&quot;&lt;/option&gt; &quot;;
        echo &quot;&lt;option &gt;&quot;.$row['ip'].&quot;&lt;/option&gt; &quot;;
    }
    echo &quot;&lt;/select&gt;&quot;;
    
         /*
          * echo json_encode(array(
            'jsArr'=&gt;$row
            ));
        */
       //  echo json_encode($row);
    //    echo $row['ip'];
    //echo $_GET['gid'];
    mysql_close($link);</p></div>
    ";i:2;s:9054:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="php" style="font-family:monospace;"><span style="color: #000000; font-weight: bold;">&lt;?php</span>
    &nbsp;
    <span style="color: #000088;">$link</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_connect</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">'10.200.205.224:3306'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'freenibs'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'freenibs'</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #339933;">!</span><span style="color: #000088;">$link</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
            <span style="color: #990000;">die</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">'Could not connect: '</span> <span style="color: #339933;">.</span> <span style="color: #990000;">mysql_error</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span>
    &nbsp;
    &nbsp;
    <span style="color: #000088;">$db_selected</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_select_db</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">'freenibs'</span><span style="color: #339933;">,</span> <span style="color: #000088;">$link</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #339933;">!</span><span style="color: #000088;">$db_selected</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
            <span style="color: #990000;">die</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">'Can\'t use  : '</span> <span style="color: #339933;">.</span> <span style="color: #990000;">mysql_error</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span>
    <span style="color: #000088;">$net_id</span><span style="color: #339933;">=</span><span style="color: #cc66cc;">0</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000088;">$gid</span><span style="color: #339933;">=</span><span style="color: #009900;">&#40;</span>int<span style="color: #009900;">&#41;</span><span style="color: #990000;">trim</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$_GET</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'vlan'</span><span style="color: #009900;">&#93;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$vlan_id</span><span style="color: #339933;">=</span><span style="color: #000088;">$gid</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$q</span><span style="color: #339933;">=</span><span style="color: #0000ff;">&quot;SELECT * FROM  `ip_manage` WHERE `vlan`='&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$vlan_id</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;' AND `uid`='0'&quot;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$q</span><span style="color: #339933;">=</span><span style="color: #0000ff;">&quot;SELECT `ip_manage`.`ip`
    FROM `ip_manage`
    RIGHT JOIN `ip_networks` ON ( `ip_networks`.`vlan` = '&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$vlan_id</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;'
    AND `ip_networks`.`net_id` = `ip_manage`.`net_id` )
    WHERE `uid` = '0'
    &quot;</span><span style="color: #339933;">;</span>
    <span style="color: #666666; font-style: italic;">//echo $q;</span>
    <span style="color: #000088;">$result</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_query</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$q</span><span style="color: #339933;">,</span><span style="color: #000088;">$link</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$ips</span><span style="color: #339933;">=</span><span style="color: #990000;">array</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;gid:  <span style="color: #006699; font-weight: bold;">$gid</span>  net_id <span style="color: #006699; font-weight: bold;">$net_id</span> &lt;select name=<span style="color: #000099; font-weight: bold;">\&quot;</span>ip_local_ip<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;
    &nbsp;
    &quot;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$i1</span><span style="color: #339933;">=</span><span style="color: #cc66cc;">1</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">while</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$row</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_fetch_array</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
        <span style="color: #666666; font-style: italic;">//$str.=$row['ip'].&quot; &quot;;</span>
        <span style="color: #666666; font-style: italic;">//  $ips[]=$row['ip'];$i1++;</span>
        <span style="color: #666666; font-style: italic;">//echo &quot;&lt;option value=\&quot;&quot;.$i1.&quot;\&quot;&gt;&quot;.$row['ip'].&quot;&lt;/option&gt; &quot;;</span>
        <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;option &gt;&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'ip'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;&lt;/option&gt; &quot;</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span>
    <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;/select&gt;&quot;</span><span style="color: #339933;">;</span>
    &nbsp;
         <span style="color: #666666; font-style: italic;">/*
          * echo json_encode(array(
            'jsArr'=&gt;$row
            ));
        */</span>
       <span style="color: #666666; font-style: italic;">//  echo json_encode($row);</span>
    <span style="color: #666666; font-style: italic;">//    echo $row['ip'];</span>
    <span style="color: #666666; font-style: italic;">//echo $_GET['gid'];</span>
    <span style="color: #990000;">mysql_close</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$link</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    &nbsp;
    <span style="color: #000000; font-weight: bold;">?&gt;</span></pre></td></tr></table><p class="theCode" style="display:none;">&lt;?php
    
    $link = mysql_connect('10.200.205.224:3306', 'freenibs', 'freenibs');
    if (!$link) {
            die('Could not connect: ' . mysql_error());
    }
    
    
    $db_selected = mysql_select_db('freenibs', $link);
    if (!$db_selected) {
            die ('Can\'t use  : ' . mysql_error());
    }
    $net_id=0;
    
    $gid=(int)trim($_GET['vlan']);
    $vlan_id=$gid;
    $q=&quot;SELECT * FROM  `ip_manage` WHERE `vlan`='&quot;.$vlan_id.&quot;' AND `uid`='0'&quot;;
    $q=&quot;SELECT `ip_manage`.`ip`
    FROM `ip_manage`
    RIGHT JOIN `ip_networks` ON ( `ip_networks`.`vlan` = '&quot;.$vlan_id.&quot;'
    AND `ip_networks`.`net_id` = `ip_manage`.`net_id` )
    WHERE `uid` = '0'
    &quot;;
    //echo $q;
    $result = mysql_query($q,$link);
    $ips=array();
    
    echo &quot;gid:  $gid  net_id $net_id &lt;select name=\&quot;ip_local_ip\&quot;&gt;
    
    &quot;;
    $i1=1;
    while ($row = mysql_fetch_array($result)) {
        //$str.=$row['ip'].&quot; &quot;;
        //  $ips[]=$row['ip'];$i1++;
        //echo &quot;&lt;option value=\&quot;&quot;.$i1.&quot;\&quot;&gt;&quot;.$row['ip'].&quot;&lt;/option&gt; &quot;;
        echo &quot;&lt;option &gt;&quot;.$row['ip'].&quot;&lt;/option&gt; &quot;;
    }
    echo &quot;&lt;/select&gt;&quot;;
    
         /*
          * echo json_encode(array(
            'jsArr'=&gt;$row
            ));
        */
       //  echo json_encode($row);
    //    echo $row['ip'];
    //echo $_GET['gid'];
    mysql_close($link);
    
    
    ?&gt;</p></div>
    ";}
categories:
  - billing
  - FreeNIBS
tags:
  - callback_changepacket_local.php
  - callback_changepacket.php

---
callback_changepacket.php — скрипт для отработки при вызове в веб-интерфейсе AJAX функций

Логика в том, что callback\_changepacket.php и callback\_changepacket\_local.php вызываются для frammed\_ip и local_ip
  
<!--more-->

<pre lang="php"><?php
$reai_ip_gids=array('14' => null,
            '11'=> null,'30'=> null,'28'=> null,
            '29'=> null,'36'=> null,'15'=> null,
            '16'=> null);

$link = mysql_connect('10.200.205.224', 'freenibs', 'freenibs');
if (!$link) {
        die('Could not connect: ' . mysql_error());
}


$db_selected = mysql_select_db('freenibs', $link);
if (!$db_selected) {
        die ('Can\'t use  : ' . mysql_error());
}
$net_id=0;

$gid=(int)trim($_GET['gid']);
if(array_key_exists($gid,$reai_ip_gids)){
    $net_id=12;
}else{
    $net_id=4;
}
$q="SELECT * FROM  `ip_manage` WHERE `net_id`='".$net_id."' AND `uid`='0'";
$result = mysql_query($q,$link);
$ips=array();

echo "gid:  $gid  net_id $net_id &lt;select name=\"ip_net\">

";
$i1=1;
while ($row = mysql_fetch_assoc($result)) {
    //$str.=$row['ip']." ";
    $ips[]=$row['ip'];$i1++;
    //echo "&lt;option value=\"".$i1."\">".$row['ip']."&lt;/option> ";
    echo "&lt;option >".$row['ip']."&lt;/option> ";
}
echo "&lt;/select>";

     /*
      * echo json_encode(array(
        'jsArr'=>$row
        ));
    */
   //  echo json_encode($row);
//    echo $row['ip'];
//echo $_GET['gid'];
mysql_close($link);
</pre>

**callback\_changepacket\_local.php**

<pre lang="php"><?php

$link = mysql_connect('10.200.205.224:3306', 'freenibs', 'freenibs');
if (!$link) {
        die('Could not connect: ' . mysql_error());
}


$db_selected = mysql_select_db('freenibs', $link);
if (!$db_selected) {
        die ('Can\'t use  : ' . mysql_error());
}
$net_id=0;

$gid=(int)trim($_GET['vlan']);
$vlan_id=$gid;
$q="SELECT * FROM  `ip_manage` WHERE `vlan`='".$vlan_id."' AND `uid`='0'";
$q="SELECT `ip_manage`.`ip`
FROM `ip_manage`
RIGHT JOIN `ip_networks` ON ( `ip_networks`.`vlan` = '".$vlan_id."'
AND `ip_networks`.`net_id` = `ip_manage`.`net_id` )
WHERE `uid` = '0'
";
//echo $q;
$result = mysql_query($q,$link);
$ips=array();

echo "gid:  $gid  net_id $net_id <select name=\"ip_local_ip\">

";
$i1=1;
while ($row = mysql_fetch_array($result)) {
    //$str.=$row['ip']." ";
    //  $ips[]=$row['ip'];$i1++;
    //echo "&lt;option value=\"".$i1."\">".$row['ip']."&lt;/option> ";
    echo "&lt;option >".$row['ip']."&lt;/option> ";
}
echo "&lt;/select>";

     /*
      * echo json_encode(array(
        'jsArr'=>$row
        ));
    */
   //  echo json_encode($row);
//    echo $row['ip'];
//echo $_GET['gid'];
mysql_close($link);


?>

</pre>