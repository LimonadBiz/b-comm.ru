---
title: cards_series_list.php
author: wel
type: post
date: 2012-01-14T23:30:21+00:00
url: /billing/cards_series_list-php
wp-syntax-cache-content:
  - |
    a:1:{i:1;s:11241:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="php" style="font-family:monospace;"><span style="color: #000000; font-weight: bold;">&lt;?</span>
    <span style="color: #b1b100;">if</span><span style="color: #009900;">&#40;</span><span style="color: #339933;">!</span>USE_CARDS<span style="color: #009900;">&#41;</span> <span style="color: #990000;">exit</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">include_once</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;utils.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
        <span style="color: #000088;">$result</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_query</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;SELECT *, count(*) as count, unix_timestamp(added) as unix_added, unix_timestamp(expired) as unix_expired FROM &quot;</span><span style="color: #339933;">.</span>CARDS_TABLE<span style="color: #339933;">.</span><span style="color: #0000ff;">&quot; GROUP BY series ORDER BY added DESC&quot;</span><span style="color: #339933;">,</span><span style="color: #000088;">$LINK_CARDS</span><span style="color: #009900;">&#41;</span> or <span style="color: #990000;">die</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;card_series_list.php -&gt; err1 &quot;</span><span style="color: #339933;">.</span><span style="color: #990000;">mysql_error</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$LINK_CARDS</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
        <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #339933;">!</span><span style="color: #990000;">mysql_num_rows</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span> <span style="color: #990000;">exit</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000000; font-weight: bold;">?&gt;</span>
      &lt;HR&gt;
      &lt;TABLE BORDER=0 CELLSPACING=2 CELLPADDING=4 BGCOLOR=black&gt;
       &lt;TR ALIGN=center BGCOLOR=&quot;#99dd99&quot;&gt;
        &lt;TD&gt;&lt;B&gt;Серия&lt;/B&gt;&lt;/TD&gt;
        &lt;TD&gt;&lt;B&gt;Время создания&lt;/B&gt;&lt;/TD&gt;
        &lt;TD&gt;&lt;B&gt;Номинал&lt;/B&gt;&lt;/TD&gt;
        &lt;TD&gt;&lt;B&gt;Количество&lt;/B&gt;&lt;/TD&gt;
        &lt;TD&gt;&lt;B&gt;Срок годности&lt;/B&gt;&lt;/TD&gt;
       &lt;/TR&gt;
    <span style="color: #000000; font-weight: bold;">&lt;?</span>
    &nbsp;
        <span style="color: #b1b100;">for</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$i</span> <span style="color: #339933;">=</span> <span style="color: #cc66cc;">0</span><span style="color: #339933;">;</span> <span style="color: #000088;">$i</span> <span style="color: #339933;">&lt;</span> <span style="color: #990000;">mysql_num_rows</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span> <span style="color: #000088;">$i</span><span style="color: #339933;">++</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
          <span style="color: #000088;">$row</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_fetch_object</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
          <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">unix_expired</span> <span style="color: #339933;">&lt;=</span> <span style="color: #990000;">time</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span>
            <span style="color: #990000;">printf</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;   &lt;TR ALIGN=center BGCOLOR=<span style="color: #000099; font-weight: bold;">\&quot;</span>#ffcccc<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;<span style="color: #000099; font-weight: bold;">\n</span>&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
          <span style="color: #b1b100;">else</span>
            <span style="color: #990000;">printf</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;   &lt;TR ALIGN=center BGCOLOR=<span style="color: #000099; font-weight: bold;">\&quot;</span>#dddd99<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;<span style="color: #000099; font-weight: bold;">\n</span>&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
          <span style="color: #990000;">printf</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;    &lt;TD&gt;&lt;A href=cards.php?series=<span style="color: #009933; font-weight: bold;">%s</span>&gt;<span style="color: #009933; font-weight: bold;">%s</span>&lt;/A&gt;&lt;/TD&gt;<span style="color: #000099; font-weight: bold;">\n</span>&quot;</span><span style="color: #339933;">,</span> <span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">series</span><span style="color: #339933;">,</span> <span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">series</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
          <span style="color: #990000;">printf</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;    &lt;TD&gt;<span style="color: #009933; font-weight: bold;">%s</span>&lt;/TD&gt;<span style="color: #000099; font-weight: bold;">\n</span>&quot;</span><span style="color: #339933;">,</span> <span style="color: #990000;">date</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;Y/m/d H:i:s&quot;</span><span style="color: #339933;">,</span><span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">unix_added</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
          <span style="color: #990000;">printf</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;    &lt;TD&gt;<span style="color: #009933; font-weight: bold;">%8.2f</span>&lt;/TD&gt;<span style="color: #000099; font-weight: bold;">\n</span>&quot;</span><span style="color: #339933;">,</span> <span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">nominal</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
          <span style="color: #990000;">printf</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;    &lt;TD&gt;<span style="color: #009933; font-weight: bold;">%d</span>&lt;/TD&gt;<span style="color: #000099; font-weight: bold;">\n</span>&quot;</span><span style="color: #339933;">,</span> <span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #990000;">count</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
          <span style="color: #990000;">printf</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;    &lt;TD&gt;<span style="color: #009933; font-weight: bold;">%s</span>&lt;/TD&gt;<span style="color: #000099; font-weight: bold;">\n</span>&quot;</span><span style="color: #339933;">,</span> <span style="color: #990000;">date</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;Y-m-d&quot;</span><span style="color: #339933;">,</span><span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">unix_expired</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
          <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;   &lt;/TR&gt;<span style="color: #000099; font-weight: bold;">\n</span>&quot;</span><span style="color: #339933;">;</span>
        <span style="color: #009900;">&#125;</span>
        <span style="color: #990000;">mysql_free_result</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000000; font-weight: bold;">?&gt;</span>
    &lt;/TABLE&gt;</pre></td></tr></table><p class="theCode" style="display:none;">&lt;?
    if(!USE_CARDS) exit();
    include_once(&quot;utils.php&quot;);
    
        $result = mysql_query (&quot;SELECT *, count(*) as count, unix_timestamp(added) as unix_added, unix_timestamp(expired) as unix_expired FROM &quot;.CARDS_TABLE.&quot; GROUP BY series ORDER BY added DESC&quot;,$LINK_CARDS) or die(&quot;card_series_list.php -&gt; err1 &quot;.mysql_error($LINK_CARDS));
        if (!mysql_num_rows ($result)) exit();
    ?&gt;
      &lt;HR&gt;
      &lt;TABLE BORDER=0 CELLSPACING=2 CELLPADDING=4 BGCOLOR=black&gt;
       &lt;TR ALIGN=center BGCOLOR=&quot;#99dd99&quot;&gt;
        &lt;TD&gt;&lt;B&gt;Серия&lt;/B&gt;&lt;/TD&gt;
        &lt;TD&gt;&lt;B&gt;Время создания&lt;/B&gt;&lt;/TD&gt;
        &lt;TD&gt;&lt;B&gt;Номинал&lt;/B&gt;&lt;/TD&gt;
        &lt;TD&gt;&lt;B&gt;Количество&lt;/B&gt;&lt;/TD&gt;
        &lt;TD&gt;&lt;B&gt;Срок годности&lt;/B&gt;&lt;/TD&gt;
       &lt;/TR&gt;
    &lt;?
    
        for ($i = 0; $i &lt; mysql_num_rows ($result); $i++) {
          $row = mysql_fetch_object ($result);
          if ($row-&gt;unix_expired &lt;= time())
            printf (&quot;   &lt;TR ALIGN=center BGCOLOR=\&quot;#ffcccc\&quot;&gt;\n&quot;);
          else
            printf (&quot;   &lt;TR ALIGN=center BGCOLOR=\&quot;#dddd99\&quot;&gt;\n&quot;);
          printf (&quot;    &lt;TD&gt;&lt;A href=cards.php?series=%s&gt;%s&lt;/A&gt;&lt;/TD&gt;\n&quot;, $row-&gt;series, $row-&gt;series);
          printf (&quot;    &lt;TD&gt;%s&lt;/TD&gt;\n&quot;, date(&quot;Y/m/d H:i:s&quot;,$row-&gt;unix_added));
          printf (&quot;    &lt;TD&gt;%8.2f&lt;/TD&gt;\n&quot;, $row-&gt;nominal);
          printf (&quot;    &lt;TD&gt;%d&lt;/TD&gt;\n&quot;, $row-&gt;count);
          printf (&quot;    &lt;TD&gt;%s&lt;/TD&gt;\n&quot;, date(&quot;Y-m-d&quot;,$row-&gt;unix_expired));
          echo &quot;   &lt;/TR&gt;\n&quot;;
        }
        mysql_free_result ($result);
    ?&gt;
    &lt;/TABLE&gt;</p></div>
    ";}
categories:
  - billing
  - FreeNIBS
tags:
  - cards_series_list.php

---
cards\_series\_list.php
  
<!--more-->

<pre lang="php"><?
if(!USE_CARDS) exit();
include_once("utils.php");

    $result = mysql_query ("SELECT *, count(*) as count, unix_timestamp(added) as unix_added, unix_timestamp(expired) as unix_expired FROM ".CARDS_TABLE." GROUP BY series ORDER BY added DESC",$LINK_CARDS) or die("card_series_list.php -> err1 ".mysql_error($LINK_CARDS));
    if (!mysql_num_rows ($result)) exit();
?>
  

<HR />
&lt;TABLE BORDER=0 CELLSPACING=2 CELLPADDING=4 BGCOLOR=black>
   &lt;TR ALIGN=center BGCOLOR="#99dd99">
    

<TD>
  <B>Серия</B>
</TD>
    

<TD>
  <B>Время создания</B>
</TD>
    

<TD>
  <B>Номинал</B>
</TD>
    

<TD>
  <B>Количество</B>
</TD>
    

<TD>
  <B>Срок годности</B>
</TD>
   &lt;/TR>


<?

    for ($i = 0; $i < mysql_num_rows ($result); $i++) {
      $row = mysql_fetch_object ($result);
      if ($row->unix_expired &lt;= time())
        printf ("   &lt;TR ALIGN=center BGCOLOR=\"#ffcccc\">\n");
      else
        printf ("   &lt;TR ALIGN=center BGCOLOR=\"#dddd99\">\n");
      printf ("    

<TD>
  &lt;A href=cards.php?series=%s>%s&lt;/A>
</TD>\n", $row->series, $row->series);
      printf ("    

<TD>
  %s
</TD>\n", date("Y/m/d H:i:s",$row->unix_added));
      printf ("    

<TD>
  %8.2f
</TD>\n", $row->nominal);
      printf ("    

<TD>
  %d
</TD>\n", $row->count);
      printf ("    

<TD>
  %s
</TD>\n", date("Y-m-d",$row->unix_expired));
      echo "   &lt;/TR>\n";
    }
    mysql_free_result ($result);
?>
&lt;/TABLE>

</pre>