---
title: edit_packet.php
author: wel
type: post
date: 2012-01-14T23:45:30+00:00
url: /billing/edit_packet-php
wp-syntax-cache-content:
  - |
    a:1:{i:1;s:4636:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="php" style="font-family:monospace;">edit_packet.php
    <span style="color: #000000; font-weight: bold;">&lt;?</span>
    <span style="color: #b1b100;">include_once</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;mysql.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000088;">$result</span><span style="color: #339933;">=</span><span style="color: #990000;">mysql_query</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;SELECT * FROM &quot;</span><span style="color: #339933;">.</span>NIBS_PACKETS_TABLE<span style="color: #339933;">.</span><span style="color: #0000ff;">&quot; WHERE gid=&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$gid</span><span style="color: #339933;">,</span><span style="color: #000088;">$LINK</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$packet</span><span style="color: #339933;">=</span><span style="color: #990000;">mysql_fetch_array</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #990000;">mysql_free_result</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000088;">$TOP</span> <span style="color: #339933;">=</span> <span style="color: #0000ff;">&quot;Изменение пакета `&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>packet<span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;'&quot;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">include</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;top.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000000; font-weight: bold;">?&gt;</span>
      &lt;FONT SIZE=+2 COLOR=green&gt;Изменение пакета `&lt;FONT COLOR=blue&gt;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>packet<span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&lt;/FONT&gt;' (<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$gid</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>)&lt;/FONT&gt;
      &lt;HR&gt;
    <span style="color: #000000; font-weight: bold;">&lt;?</span>
    <span style="color: #b1b100;">include</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;edit_packet_menu.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000000; font-weight: bold;">?&gt;</span>
      &lt;HR&gt;
      &lt;A HREF=/&gt;Вернуться&lt;/A&gt;
    <span style="color: #000000; font-weight: bold;">&lt;?</span>
    <span style="color: #b1b100;">include</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;bottom.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000000; font-weight: bold;">?&gt;</span></pre></td></tr></table><p class="theCode" style="display:none;">edit_packet.php
    &lt;?
    include_once(&quot;mysql.php&quot;);
    
    $result=mysql_query(&quot;SELECT * FROM &quot;.NIBS_PACKETS_TABLE.&quot; WHERE gid=&quot;.$gid,$LINK);
    $packet=mysql_fetch_array($result);
    mysql_free_result($result);
    
    $TOP = &quot;Изменение пакета `&quot;.$packet[packet].&quot;'&quot;;
    include(&quot;top.php&quot;);
    ?&gt;
      &lt;FONT SIZE=+2 COLOR=green&gt;Изменение пакета `&lt;FONT COLOR=blue&gt;&lt;? echo $packet[packet]; ?&gt;&lt;/FONT&gt;' (&lt;? echo $gid; ?&gt;)&lt;/FONT&gt;
      &lt;HR&gt;
    &lt;?
    include(&quot;edit_packet_menu.php&quot;);
    ?&gt;
      &lt;HR&gt;
      &lt;A HREF=/&gt;Вернуться&lt;/A&gt;
    &lt;?
    include(&quot;bottom.php&quot;);
    
    ?&gt;</p></div>
    ";}
categories:
  - billing
  - FreeNIBS
tags:
  - edit_packet.php

---
<pre lang="php">edit_packet.php
<?
include_once("mysql.php");

$result=mysql_query("SELECT * FROM ".NIBS_PACKETS_TABLE." WHERE gid=".$gid,$LINK);
$packet=mysql_fetch_array($result);
mysql_free_result($result);

$TOP = "Изменение пакета `".$packet[packet]."'";
include("top.php");
?>
  &lt;FONT SIZE=+2 COLOR=green>Изменение пакета `&lt;FONT COLOR=blue>

<? echo $packet[packet]; ?>&lt;/FONT>' (

<? echo $gid; ?>)&lt;/FONT>
  

<HR />

<?
include("edit_packet_menu.php");
?>
  

<HR />
&lt;A HREF=/>Вернуться&lt;/A>

<?
include("bottom.php");

?>

</pre>