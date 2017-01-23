---
title: add_cards.php
author: wel
type: post
date: 2006-01-14T21:54:33+00:00
url: /billing/add_cards-php
wp-syntax-cache-content:
  - |
    a:1:{i:1;s:16809:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="php" style="font-family:monospace;"><span style="color: #000000; font-weight: bold;">&lt;?</span>
    <span style="color: #b1b100;">include_once</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;defines.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">if</span><span style="color: #009900;">&#40;</span><span style="color: #339933;">!</span>USE_CARDS<span style="color: #009900;">&#41;</span> <span style="color: #990000;">exit</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #b1b100;">include_once</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;mysql.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$series</span> <span style="color: #339933;">=</span> <span style="color: #990000;">sprintf</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;<span style="color: #009933; font-weight: bold;">%04d</span>&quot;</span><span style="color: #339933;">,</span> <span style="color: #000088;">$series</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000088;">$flag</span> <span style="color: #339933;">=</span> <span style="color: #0000ff;">&quot;false&quot;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">while</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$flag</span> <span style="color: #339933;">==</span> <span style="color: #0000ff;">&quot;false&quot;</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
        <span style="color: #b1b100;">for</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$i</span> <span style="color: #339933;">=</span> <span style="color: #cc66cc;">1</span><span style="color: #339933;">;</span> <span style="color: #000088;">$i</span> <span style="color: #339933;">&lt;=</span> <span style="color: #000088;">$count</span><span style="color: #339933;">;</span> <span style="color: #000088;">$i</span><span style="color: #339933;">++</span> <span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
            <span style="color: #000088;">$arr</span><span style="color: #009900;">&#91;</span><span style="color: #000088;">$i</span><span style="color: #009900;">&#93;</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mt_rand</span><span style="color: #009900;">&#40;</span><span style="color: #cc66cc;">1000000</span><span style="color: #339933;">,</span><span style="color: #cc66cc;">9999999</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
            <span style="color: #000088;">$arr</span><span style="color: #009900;">&#91;</span><span style="color: #000088;">$i</span><span style="color: #009900;">&#93;</span> <span style="color: #339933;">.=</span> <span style="color: #990000;">mt_rand</span><span style="color: #009900;">&#40;</span><span style="color: #cc66cc;">1000000</span><span style="color: #339933;">,</span><span style="color: #cc66cc;">9999999</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
            <span style="color: #000088;">$arr1</span><span style="color: #009900;">&#91;</span><span style="color: #000088;">$i</span><span style="color: #009900;">&#93;</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mt_rand</span><span style="color: #009900;">&#40;</span><span style="color: #cc66cc;">1000000</span><span style="color: #339933;">,</span><span style="color: #cc66cc;">9999999</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
           <span style="color: #666666; font-style: italic;">// $arr1[$i] .= mt_rand(1000000,9999999);</span>
        <span style="color: #009900;">&#125;</span>
        <span style="color: #000088;">$flag</span> <span style="color: #339933;">=</span> <span style="color: #0000ff;">&quot;&quot;</span><span style="color: #339933;">;</span>
        <span style="color: #b1b100;">for</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$i</span> <span style="color: #339933;">=</span> <span style="color: #cc66cc;">1</span><span style="color: #339933;">;</span> <span style="color: #000088;">$i</span> <span style="color: #339933;">&lt;=</span> <span style="color: #000088;">$count</span><span style="color: #339933;">;</span> <span style="color: #000088;">$i</span><span style="color: #339933;">++</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
            <span style="color: #b1b100;">for</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$j</span> <span style="color: #339933;">=</span> <span style="color: #cc66cc;">1</span><span style="color: #339933;">;</span> <span style="color: #000088;">$j</span> <span style="color: #339933;">&lt;=</span> <span style="color: #000088;">$count</span><span style="color: #339933;">;</span> <span style="color: #000088;">$j</span><span style="color: #339933;">++</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
                <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$arr</span><span style="color: #009900;">&#91;</span><span style="color: #000088;">$i</span><span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #000088;">$arr</span><span style="color: #009900;">&#91;</span><span style="color: #000088;">$j</span><span style="color: #009900;">&#93;</span> <span style="color: #339933;">&amp;&amp;</span> <span style="color: #000088;">$i</span> <span style="color: #339933;">!=</span> <span style="color: #000088;">$j</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
                    <span style="color: #000088;">$flag</span> <span style="color: #339933;">=</span> <span style="color: #0000ff;">&quot;false&quot;</span><span style="color: #339933;">;</span> 
                <span style="color: #009900;">&#125;</span>
            <span style="color: #009900;">&#125;</span>
        <span style="color: #009900;">&#125;</span>
    <span style="color: #009900;">&#125;</span>
    &nbsp;
    <span style="color: #000088;">$result</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_query</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;SELECT series FROM &quot;</span><span style="color: #339933;">.</span>CARDS_TABLE<span style="color: #339933;">.</span><span style="color: #0000ff;">&quot; WHERE series='&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$series</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;'&quot;</span><span style="color: #339933;">,</span><span style="color: #000088;">$LINK_CARDS</span><span style="color: #009900;">&#41;</span> or <span style="color: #990000;">die</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;Error while insert cards `&quot;</span><span style="color: #339933;">.</span><span style="color: #990000;">mysql_error</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$LINK_CARDS</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;'&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #990000;">mysql_num_rows</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span> <span style="color: #339933;">&gt;</span> <span style="color: #cc66cc;">0</span> <span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
        <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;CENTER&gt;éÚ×ÅÎÉÔÅ. îÏ ÄÁÎÎÁÑ ÓÅÒÉÑ ÕÖÅ ÓÕÝÅÓÔ×ÕÅÔ.&lt;/CENTER&gt;&quot;</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span><span style="color: #b1b100;">else</span><span style="color: #009900;">&#123;</span>
        <span style="color: #b1b100;">for</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$i</span> <span style="color: #339933;">=</span> <span style="color: #cc66cc;">1</span><span style="color: #339933;">;</span> <span style="color: #000088;">$i</span> <span style="color: #339933;">&lt;=</span> <span style="color: #000088;">$count</span><span style="color: #339933;">;</span> <span style="color: #000088;">$i</span><span style="color: #339933;">++</span> <span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
    <span style="color: #666666; font-style: italic;">//	mysql_query(&quot;INSERT INTO &quot;.CARDS_TABLE.&quot; SET series='&quot;.$series.&quot;', nominal='&quot;.$nominal.&quot;', expired='&quot;.$year.&quot;-&quot;.$month.&quot;-&quot;.$day.&quot;', sn='&quot;.$arr[$i].&quot;', status='a'&quot;, $LINK_CARDS) or die(&quot;Error while insert cards serial-number `&quot;.mysql_error($LINK_CARDS).&quot;'&quot;);</span>
    &nbsp;
    	<span style="color: #990000;">mysql_query</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;INSERT INTO &quot;</span><span style="color: #339933;">.</span>CARDS_TABLE<span style="color: #339933;">.</span><span style="color: #0000ff;">&quot; SET series='&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$series</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;', nominal='&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$nominal</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;', n='&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$series</span><span style="color: #339933;">.</span><span style="color: #000088;">$arr1</span><span style="color: #009900;">&#91;</span><span style="color: #000088;">$i</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;',expired='&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$year</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;-&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$month</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;-&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$day</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;', sn='&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$arr</span><span style="color: #009900;">&#91;</span><span style="color: #000088;">$i</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;', status='a'&quot;</span><span style="color: #339933;">,</span> <span style="color: #000088;">$LINK_CARDS</span><span style="color: #009900;">&#41;</span> or <span style="color: #990000;">die</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;Error while insert cards serial-number `&quot;</span><span style="color: #339933;">.</span><span style="color: #990000;">mysql_error</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$LINK_CARDS</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;'&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
        <span style="color: #009900;">&#125;</span>
        <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;CENTER&gt;<span style="color: #006699; font-weight: bold;">$count</span> ËÁÒÔÏÞÅË ÓÅÒÉÉ <span style="color: #006699; font-weight: bold;">$series</span> ÎÏÍÉÎÁÌÏÍ <span style="color: #006699; font-weight: bold;">$nominal</span> ÓÏÚÄÁÎÙ.&lt;/CENTER&gt;&quot;</span><span style="color: #339933;">;</span>
    <span style="color: #666666; font-style: italic;">//echo &quot;w&quot;;</span>
    <span style="color: #666666; font-style: italic;">//,n='&quot;.$arr1[$i].&quot;'</span>
    &nbsp;
    <span style="color: #009900;">&#125;</span>
    <span style="color: #000088;">$TOP</span> <span style="color: #339933;">=</span> <span style="color: #0000ff;">&quot;ëÁÒÔÏÞËÉ&quot;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">include</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;top.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000000; font-weight: bold;">?&gt;</span>
      &lt;CENTER&gt;
    <span style="color: #000000; font-weight: bold;">&lt;?</span>
    <span style="color: #b1b100;">include</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;new_cards_menu.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">include</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;cards_series_list.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000000; font-weight: bold;">?&gt;</span>
      &lt;/CENTER&gt;
    <span style="color: #000000; font-weight: bold;">&lt;?</span>
    <span style="color: #b1b100;">include</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;bottom.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000000; font-weight: bold;">?&gt;</span></pre></td></tr></table><p class="theCode" style="display:none;">&lt;?
    include_once(&quot;defines.php&quot;);
    if(!USE_CARDS) exit();
    
    include_once(&quot;mysql.php&quot;);
    $series = sprintf(&quot;%04d&quot;, $series);
    
    $flag = &quot;false&quot;;
    while ($flag == &quot;false&quot;) {
        for ($i = 1; $i &lt;= $count; $i++ ) {
            $arr[$i] = mt_rand(1000000,9999999);
            $arr[$i] .= mt_rand(1000000,9999999);
    
            $arr1[$i] = mt_rand(1000000,9999999);
           // $arr1[$i] .= mt_rand(1000000,9999999);
        }
        $flag = &quot;&quot;;
        for ($i = 1; $i &lt;= $count; $i++) {
            for ($j = 1; $j &lt;= $count; $j++) {
                if ($arr[$i] == $arr[$j] &amp;&amp; $i != $j) {
                    $flag = &quot;false&quot;; 
                }
            }
        }
    }
    
    $result = mysql_query(&quot;SELECT series FROM &quot;.CARDS_TABLE.&quot; WHERE series='&quot;.$series.&quot;'&quot;,$LINK_CARDS) or die(&quot;Error while insert cards `&quot;.mysql_error($LINK_CARDS).&quot;'&quot;);
    if (mysql_num_rows($result) &gt; 0 ) {
        echo &quot;&lt;CENTER&gt;éÚ×ÅÎÉÔÅ. îÏ ÄÁÎÎÁÑ ÓÅÒÉÑ ÕÖÅ ÓÕÝÅÓÔ×ÕÅÔ.&lt;/CENTER&gt;&quot;;
    }else{
        for ($i = 1; $i &lt;= $count; $i++ ) {
    //	mysql_query(&quot;INSERT INTO &quot;.CARDS_TABLE.&quot; SET series='&quot;.$series.&quot;', nominal='&quot;.$nominal.&quot;', expired='&quot;.$year.&quot;-&quot;.$month.&quot;-&quot;.$day.&quot;', sn='&quot;.$arr[$i].&quot;', status='a'&quot;, $LINK_CARDS) or die(&quot;Error while insert cards serial-number `&quot;.mysql_error($LINK_CARDS).&quot;'&quot;);
    
    	mysql_query(&quot;INSERT INTO &quot;.CARDS_TABLE.&quot; SET series='&quot;.$series.&quot;', nominal='&quot;.$nominal.&quot;', n='&quot;.$series.$arr1[$i].&quot;',expired='&quot;.$year.&quot;-&quot;.$month.&quot;-&quot;.$day.&quot;', sn='&quot;.$arr[$i].&quot;', status='a'&quot;, $LINK_CARDS) or die(&quot;Error while insert cards serial-number `&quot;.mysql_error($LINK_CARDS).&quot;'&quot;);
    
        }
        echo &quot;&lt;CENTER&gt;$count ËÁÒÔÏÞÅË ÓÅÒÉÉ $series ÎÏÍÉÎÁÌÏÍ $nominal ÓÏÚÄÁÎÙ.&lt;/CENTER&gt;&quot;;
    //echo &quot;w&quot;;
    //,n='&quot;.$arr1[$i].&quot;'
    	
    }
    $TOP = &quot;ëÁÒÔÏÞËÉ&quot;;
    include(&quot;top.php&quot;);
    ?&gt;
      &lt;CENTER&gt;
    &lt;?
    include(&quot;new_cards_menu.php&quot;);
    include(&quot;cards_series_list.php&quot;);
    ?&gt;
      &lt;/CENTER&gt;
    &lt;?
    include(&quot;bottom.php&quot;);
    ?&gt;</p></div>
    ";}
categories:
  - billing
  - FreeNIBS
tags:
  - freeNIBS

---
add_cards.php 

<pre lang="php"><?
include_once("defines.php");
if(!USE_CARDS) exit();

include_once("mysql.php");
$series = sprintf("%04d", $series);

$flag = "false";
while ($flag == "false") {
    for ($i = 1; $i <= $count; $i++ ) {
        $arr[$i] = mt_rand(1000000,9999999);
        $arr[$i] .= mt_rand(1000000,9999999);

        $arr1[$i] = mt_rand(1000000,9999999);
       // $arr1[$i] .= mt_rand(1000000,9999999);
    }
    $flag = "";
    for ($i = 1; $i <= $count; $i++) {
        for ($j = 1; $j <= $count; $j++) {
            if ($arr[$i] == $arr[$j] &#038;&#038; $i != $j) {
                $flag = "false"; 
            }
        }
    }
}

$result = mysql_query("SELECT series FROM ".CARDS_TABLE." WHERE series='".$series."'",$LINK_CARDS) or die("Error while insert cards `".mysql_error($LINK_CARDS)."'");
if (mysql_num_rows($result) > 0 ) {
    echo "

<CENTER>
  éÚ×ÅÎÉÔÅ. îÏ ÄÁÎÎÁÑ ÓÅÒÉÑ ÕÖÅ ÓÕÝÅÓÔ×ÕÅÔ.
</CENTER>";
}else{
    for ($i = 1; $i &lt;= $count; $i++ ) {
//	mysql_query("INSERT INTO ".CARDS_TABLE." SET series='".$series."', nominal='".$nominal."', expired='".$year."-".$month."-".$day."', sn='".$arr[$i]."', status='a'", $LINK_CARDS) or die("Error while insert cards serial-number `".mysql_error($LINK_CARDS)."'");

	mysql_query("INSERT INTO ".CARDS_TABLE." SET series='".$series."', nominal='".$nominal."', n='".$series.$arr1[$i]."',expired='".$year."-".$month."-".$day."', sn='".$arr[$i]."', status='a'", $LINK_CARDS) or die("Error while insert cards serial-number `".mysql_error($LINK_CARDS)."'");

    }
    echo "

<CENTER>
  $count ËÁÒÔÏÞÅË ÓÅÒÉÉ $series ÎÏÍÉÎÁÌÏÍ $nominal ÓÏÚÄÁÎÙ.
</CENTER>";
//echo "w";
//,n='".$arr1[$i]."'
	
}
$TOP = "ëÁÒÔÏÞËÉ";
include("top.php");
?>
  

<CENTER>
  <?
include("new_cards_menu.php");
include("cards_series_list.php");
?>
    
</CENTER>


<?
include("bottom.php");
?>

</pre>

&#8212;&#8212;&#8212;
  
[2012 цвет черемухи смотреть][1]

 [1]: http://filmokat.ru/?p=21036