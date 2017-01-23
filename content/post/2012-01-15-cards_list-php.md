---
title: cards_list.php
author: wel
type: post
date: 2012-01-14T23:29:25+00:00
url: /billing/cards_list-php
wp-syntax-cache-content:
  - |
    a:1:{i:1;s:35267:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="php" style="font-family:monospace;"><span style="color: #000000; font-weight: bold;">&lt;?</span>
    <span style="color: #b1b100;">include_once</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;defines.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">if</span><span style="color: #009900;">&#40;</span><span style="color: #339933;">!</span>USE_CARDS<span style="color: #009900;">&#41;</span> <span style="color: #990000;">exit</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #b1b100;">include_once</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;utils.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
        <span style="color: #000088;">$result</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_query</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;SELECT * FROM &quot;</span><span style="color: #339933;">.</span>CARDS_TABLE<span style="color: #339933;">.</span><span style="color: #0000ff;">&quot; WHERE series='&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$series</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;' AND status='a'&quot;</span><span style="color: #339933;">,</span><span style="color: #000088;">$LINK_CARDS</span><span style="color: #009900;">&#41;</span> or <span style="color: #990000;">die</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;cards_list.php -&gt; err2 &quot;</span><span style="color: #339933;">.</span><span style="color: #990000;">mysql_error</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$LINK_CARDS</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
        <span style="color: #000088;">$actived</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_num_rows</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
        <span style="color: #990000;">mysql_free_result</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
        <span style="color: #000088;">$result</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_query</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;SELECT * FROM &quot;</span><span style="color: #339933;">.</span>CARDS_TABLE<span style="color: #339933;">.</span><span style="color: #0000ff;">&quot; WHERE series='&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$series</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;' AND status='l'&quot;</span><span style="color: #339933;">,</span><span style="color: #000088;">$LINK_CARDS</span><span style="color: #009900;">&#41;</span> or <span style="color: #990000;">die</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;cards_list.php -&gt; err2 &quot;</span><span style="color: #339933;">.</span><span style="color: #990000;">mysql_error</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$LINK_CARDS</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
        <span style="color: #000088;">$locked</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_num_rows</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
        <span style="color: #990000;">mysql_free_result</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
        <span style="color: #000088;">$result</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_query</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;SELECT * FROM &quot;</span><span style="color: #339933;">.</span>CARDS_TABLE<span style="color: #339933;">.</span><span style="color: #0000ff;">&quot; WHERE series='&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$series</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;' AND status='u'&quot;</span><span style="color: #339933;">,</span><span style="color: #000088;">$LINK_CARDS</span><span style="color: #009900;">&#41;</span> or <span style="color: #990000;">die</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;cards_list.php -&gt; err2 &quot;</span><span style="color: #339933;">.</span><span style="color: #990000;">mysql_error</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$LINK_CARDS</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
        <span style="color: #000088;">$used</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_num_rows</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
        <span style="color: #990000;">mysql_free_result</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
        <span style="color: #000088;">$result</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_query</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;SELECT unix_timestamp(added) as unix_added, unix_timestamp(expired) as unix_expired FROM &quot;</span><span style="color: #339933;">.</span>CARDS_TABLE<span style="color: #339933;">.</span><span style="color: #0000ff;">&quot; WHERE series='&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$series</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;' GROUP BY series&quot;</span><span style="color: #339933;">,</span><span style="color: #000088;">$LINK_CARDS</span><span style="color: #009900;">&#41;</span> or <span style="color: #990000;">die</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;cards_list.php -&gt; err2 &quot;</span><span style="color: #339933;">.</span><span style="color: #990000;">mysql_error</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$LINK_CARDS</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
        <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #990000;">mysql_num_rows</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span> <span style="color: #339933;">&gt;</span> <span style="color: #cc66cc;">0</span><span style="color: #009900;">&#41;</span>
          <span style="color: #000088;">$row</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_fetch_object</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
        <span style="color: #990000;">mysql_free_result</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
      <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;FONT FACE=arial COLOR=green&gt;&lt;B&gt;Серия `&lt;FONT COLOR=red&gt;<span style="color: #006699; font-weight: bold;">$series</span>&lt;/FONT&gt;' &lt;FONT COLOR=black&gt;[&quot;</span><span style="color: #339933;">.</span><span style="color: #990000;">date</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;Y/m/d&quot;</span><span style="color: #339933;">,</span> <span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">unix_expired</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;]&lt;/FONT&gt; (всего: &lt;FONT COLOR=blue&gt;<span style="color: #006699; font-weight: bold;">$total</span>&lt;/FONT&gt;, рабочих: &lt;FONT COLOR=blue&gt;<span style="color: #006699; font-weight: bold;">$actived</span>&lt;/FONT&gt;, блокированных: &lt;FONT COLOR=blue&gt;<span style="color: #006699; font-weight: bold;">$locked</span>&lt;/FONT&gt;, использованных: &lt;FONT COLOR=blue&gt;<span style="color: #006699; font-weight: bold;">$used</span>&lt;/FONT&gt;)&lt;/B&gt;&lt;/FONT&gt;&lt;BR&gt;&quot;</span><span style="color: #339933;">;</span>
      <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">unix_expired</span> <span style="color: #339933;">&lt;=</span> <span style="color: #990000;">time</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span> <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;FONT SIZE=+1 FACE=arial COLOR=red&gt;&lt;B&gt;Внимание!!! Серия устарела!&lt;/B&gt;&lt;/FONT&gt;&lt;BR&gt;&quot;</span><span style="color: #339933;">;</span>
      <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;FONT SIZE=+1 FACE=arial&gt;&lt;B&gt;&quot;</span><span style="color: #339933;">;</span>
      <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$total</span> <span style="color: #339933;">==</span> <span style="color: #000088;">$locked</span> <span style="color: #339933;">+</span> <span style="color: #000088;">$used</span><span style="color: #009900;">&#41;</span> <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;A HREF=save_series.php?series=<span style="color: #006699; font-weight: bold;">$series</span>&amp;action=unlock&gt;Разблокировать серию&lt;/A&gt;&quot;</span><span style="color: #339933;">;</span>
      <span style="color: #b1b100;">else</span> <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;A HREF=save_series.php?series=<span style="color: #006699; font-weight: bold;">$series</span>&amp;action=lock&gt;Блокировать серию&lt;/A&gt;&quot;</span><span style="color: #339933;">;</span>
      <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot; | &lt;A onclick=<span style="color: #000099; font-weight: bold;">\&quot;</span>return confirm('Вы действительно хотите УДАЛИТЬ серию <span style="color: #006699; font-weight: bold;">$series</span>?')<span style="color: #000099; font-weight: bold;">\&quot;</span> HREF=real_del_series.php?series=<span style="color: #006699; font-weight: bold;">$series</span>&gt;Удалить серию&lt;/A&gt;&quot;</span><span style="color: #339933;">;</span>
      <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;/B&gt;&lt;/FONT&gt;&lt;BR&gt;&quot;</span><span style="color: #339933;">;</span>
    <span style="color: #000000; font-weight: bold;">?&gt;</span>
      &lt;HR&gt;
      &lt;TABLE BORDER=0 CELLSPACING=2 CELLPADDING=4 BGCOLOR=black&gt;
       &lt;TR ALIGN=center BGCOLOR=&quot;#99dd99&quot;&gt;
       &lt;TD&gt;&lt;B&gt;Номер&lt;BR&gt;карточки&lt;/B&gt;&lt;/TD&gt;
    &nbsp;
        &lt;TD&gt;&lt;B&gt;Номинал&lt;/B&gt;&lt;/TD&gt;
        &lt;TD&gt;&lt;B&gt;Состояние&lt;/B&gt;&lt;/TD&gt;
        &lt;TD&gt;&lt;B&gt;Действия&lt;/B&gt;&lt;/TD&gt;
        <span style="color: #000000; font-weight: bold;">&lt;?php</span>
        <span style="color: #666666; font-style: italic;">// рср лш АСДЕЛ ОНОНКМЪРЭ :)</span>
        <span style="color: #000000; font-weight: bold;">?&gt;</span>
        &lt;TD&gt;&lt;B&gt;IP&lt;/B&gt;&lt;/TD&gt;
        &lt;TD&gt;&lt;B&gt;login&lt;/B&gt;&lt;/TD&gt;
    &nbsp;
            &lt;TD&gt;&lt;B&gt;Номер &lt;BR&gt;(код пополнения)&lt;/B&gt;&lt;/TD&gt;
            &lt;TD&gt;дата поподнения&lt;/TD&gt;
       &lt;/TR&gt;
    <span style="color: #000000; font-weight: bold;">&lt;?</span>
    &nbsp;
    <span style="color: #666666; font-style: italic;">//    $result = mysql_query (&quot;SELECT sn, nominal, status FROM &quot;.CARDS_TABLE.&quot; WHERE series='&quot;.$series.&quot;'&quot;,$LINK_CARDS) or die(&quot;cards_list.php -&gt; err2 &quot;.mysql_error($LINK_CARDS));</span>
        <span style="color: #000088;">$result</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_query</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;SELECT sn, nominal, status, used_at, used_by, n, login FROM &quot;</span><span style="color: #339933;">.</span>CARDS_TABLE<span style="color: #339933;">.</span><span style="color: #0000ff;">&quot; WHERE series='&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$series</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;'&quot;</span><span style="color: #339933;">,</span><span style="color: #000088;">$LINK_CARDS</span><span style="color: #009900;">&#41;</span> or <span style="color: #990000;">die</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;cards_list.php -&gt; err2 &quot;</span><span style="color: #339933;">.</span><span style="color: #990000;">mysql_error</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$LINK_CARDS</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
        <span style="color: #b1b100;">for</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$i</span> <span style="color: #339933;">=</span> <span style="color: #cc66cc;">0</span><span style="color: #339933;">;</span> <span style="color: #000088;">$i</span> <span style="color: #339933;">&lt;</span> <span style="color: #990000;">mysql_num_rows</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span> <span style="color: #000088;">$i</span><span style="color: #339933;">++</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
          <span style="color: #000088;">$row</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_fetch_object</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
              <span style="color: #666666; font-style: italic;">//poriadkovij nomer carti/////////</span>
    &nbsp;
    &nbsp;
              <span style="color: #666666; font-style: italic;">///</span>
              <span style="color: #990000;">printf</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;   &lt;TR ALIGN=center BGCOLOR=<span style="color: #000099; font-weight: bold;">\&quot;</span>#<span style="color: #009933; font-weight: bold;">%s</span><span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;<span style="color: #000099; font-weight: bold;">\n</span>&quot;</span><span style="color: #339933;">,</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">status</span> <span style="color: #339933;">==</span> <span style="color: #0000ff;">'a'</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot;eeeeee&quot;</span> <span style="color: #339933;">:</span> <span style="color: #009900;">&#40;</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">status</span> <span style="color: #339933;">==</span> <span style="color: #0000ff;">'u'</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot;dddd99&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot;ffcccc&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    &nbsp;
          <span style="color: #990000;">printf</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;    &lt;TD&gt;<span style="color: #009933; font-weight: bold;">%s</span>-<span style="color: #009933; font-weight: bold;">%s</span>-<span style="color: #009933; font-weight: bold;">%s</span>-<span style="color: #009933; font-weight: bold;">%s</span>-<span style="color: #009933; font-weight: bold;">%s</span>&lt;/TD&gt;<span style="color: #000099; font-weight: bold;">\n</span>&quot;</span><span style="color: #339933;">,</span> <span style="color: #000088;">$series</span><span style="color: #339933;">,</span> <span style="color: #990000;">substr</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">sn</span><span style="color: #339933;">,</span><span style="color: #cc66cc;">0</span><span style="color: #339933;">,</span><span style="color: #cc66cc;">4</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">,</span> <span style="color: #990000;">substr</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">sn</span><span style="color: #339933;">,</span><span style="color: #cc66cc;">4</span><span style="color: #339933;">,</span><span style="color: #cc66cc;">4</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">,</span> <span style="color: #990000;">substr</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">sn</span><span style="color: #339933;">,</span><span style="color: #cc66cc;">8</span><span style="color: #339933;">,</span><span style="color: #cc66cc;">4</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">,</span> <span style="color: #990000;">substr</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">sn</span><span style="color: #339933;">,</span><span style="color: #cc66cc;">12</span><span style="color: #339933;">,</span><span style="color: #cc66cc;">2</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
          <span style="color: #990000;">printf</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;    &lt;TD&gt;<span style="color: #009933; font-weight: bold;">%8.2f</span>&lt;/TD&gt;<span style="color: #000099; font-weight: bold;">\n</span>&quot;</span><span style="color: #339933;">,</span> <span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">nominal</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
          <span style="color: #990000;">printf</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;    &lt;TD&gt;<span style="color: #009933; font-weight: bold;">%s</span>&lt;/TD&gt;<span style="color: #000099; font-weight: bold;">\n</span>&quot;</span><span style="color: #339933;">,</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">status</span> <span style="color: #339933;">==</span> <span style="color: #0000ff;">'a'</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot;&lt;A HREF=save_card.php?series=<span style="color: #006699; font-weight: bold;">$series</span>&amp;sn=<span style="color: #006699; font-weight: bold;">$row-&gt;sn</span>&amp;action=lock&gt;рабочая&lt;/A&gt;&quot;</span> <span style="color: #339933;">:</span> <span style="color: #009900;">&#40;</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">status</span> <span style="color: #339933;">==</span> <span style="color: #0000ff;">'u'</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot;использованна&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot;&lt;A HREF=save_card.php?series=<span style="color: #006699; font-weight: bold;">$series</span>&amp;sn=<span style="color: #006699; font-weight: bold;">$row-&gt;sn</span>&amp;action=unlock&gt;блокированна&lt;/a&gt;&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
          <span style="color: #990000;">printf</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;    &lt;TD&gt;&lt;A onclick=<span style="color: #000099; font-weight: bold;">\&quot;</span>return confirm('Вы действительно хотите УДАЛИТЬ карточку : <span style="color: #009933; font-weight: bold;">%s</span>-<span style="color: #009933; font-weight: bold;">%s</span>-<span style="color: #009933; font-weight: bold;">%s</span>-<span style="color: #009933; font-weight: bold;">%s</span>-<span style="color: #009933; font-weight: bold;">%s</span>?')<span style="color: #000099; font-weight: bold;">\&quot;</span> HREF=real_del_card.php?series=<span style="color: #006699; font-weight: bold;">$series</span>&amp;sn=<span style="color: #006699; font-weight: bold;">$row-&gt;sn</span>&gt;Удалить&lt;/A&gt;&lt;/TD&gt;<span style="color: #000099; font-weight: bold;">\n</span>&quot;</span><span style="color: #339933;">,</span> <span style="color: #000088;">$series</span><span style="color: #339933;">,</span> <span style="color: #990000;">substr</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">sn</span><span style="color: #339933;">,</span><span style="color: #cc66cc;">0</span><span style="color: #339933;">,</span><span style="color: #cc66cc;">4</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">,</span> <span style="color: #990000;">substr</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">sn</span><span style="color: #339933;">,</span><span style="color: #cc66cc;">4</span><span style="color: #339933;">,</span><span style="color: #cc66cc;">4</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">,</span> <span style="color: #990000;">substr</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">sn</span><span style="color: #339933;">,</span><span style="color: #cc66cc;">8</span><span style="color: #339933;">,</span><span style="color: #cc66cc;">4</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">,</span> <span style="color: #990000;">substr</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">sn</span><span style="color: #339933;">,</span><span style="color: #cc66cc;">12</span><span style="color: #339933;">,</span><span style="color: #cc66cc;">2</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
        <span style="color: #666666; font-style: italic;">//my :)</span>
    <span style="color: #666666; font-style: italic;">//login from</span>
              <span style="color: #990000;">printf</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;    &lt;TD&gt;<span style="color: #009933; font-weight: bold;">%s</span>&lt;/TD&gt;<span style="color: #000099; font-weight: bold;">\n</span>&quot;</span><span style="color: #339933;">,</span> <span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">login</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
        <span style="color: #666666; font-style: italic;">//IP from</span>
              <span style="color: #990000;">printf</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;    &lt;TD&gt;<span style="color: #009933; font-weight: bold;">%s</span>&lt;/TD&gt;<span style="color: #000099; font-weight: bold;">\n</span>&quot;</span><span style="color: #339933;">,</span> <span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">used_by</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    &nbsp;
              <span style="color: #990000;">printf</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;  &lt;TD&gt;<span style="color: #009933; font-weight: bold;">%s</span>-<span style="color: #009933; font-weight: bold;">%s</span>&lt;/TD&gt;<span style="color: #000099; font-weight: bold;">\n</span>&quot;</span><span style="color: #339933;">,</span> <span style="color: #990000;">substr</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">n</span><span style="color: #339933;">,</span><span style="color: #cc66cc;">0</span><span style="color: #339933;">,</span><span style="color: #cc66cc;">4</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">,</span><span style="color: #990000;">substr</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">n</span><span style="color: #339933;">,</span><span style="color: #cc66cc;">4</span><span style="color: #339933;">,</span><span style="color: #cc66cc;">13</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #666666; font-style: italic;">//            printf (&quot;    &lt;TD&gt;%s-%s-%s-%s-%s&lt;/TD&gt;\n&quot;,$row-&gt;nominal);</span>
                  <span style="color: #666666; font-style: italic;">//, substr($row-&gt;n,0,4), substr($row-&gt;n,4,4), substr($row-&gt;n,8,4), substr($row-&gt;n,12,2));</span>
                <span style="color: #990000;">printf</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;    &lt;TD&gt;<span style="color: #009933; font-weight: bold;">%s</span>&lt;/TD&gt;<span style="color: #000099; font-weight: bold;">\n</span>&quot;</span><span style="color: #339933;">,</span> <span style="color: #000088;">$row</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">used_at</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
          <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;   &lt;/TR&gt;<span style="color: #000099; font-weight: bold;">\n</span>&quot;</span><span style="color: #339933;">;</span>
        <span style="color: #009900;">&#125;</span>
        <span style="color: #990000;">mysql_free_result</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000000; font-weight: bold;">?&gt;</span>
    &lt;/TABLE&gt;</pre></td></tr></table><p class="theCode" style="display:none;">&lt;?
    include_once(&quot;defines.php&quot;);
    if(!USE_CARDS) exit();
    
    include_once(&quot;utils.php&quot;);
    
        $result = mysql_query (&quot;SELECT * FROM &quot;.CARDS_TABLE.&quot; WHERE series='&quot;.$series.&quot;' AND status='a'&quot;,$LINK_CARDS) or die(&quot;cards_list.php -&gt; err2 &quot;.mysql_error($LINK_CARDS));
        $actived = mysql_num_rows ($result);
        mysql_free_result($result);
    
        $result = mysql_query (&quot;SELECT * FROM &quot;.CARDS_TABLE.&quot; WHERE series='&quot;.$series.&quot;' AND status='l'&quot;,$LINK_CARDS) or die(&quot;cards_list.php -&gt; err2 &quot;.mysql_error($LINK_CARDS));
        $locked = mysql_num_rows ($result);
        mysql_free_result($result);
    
        $result = mysql_query (&quot;SELECT * FROM &quot;.CARDS_TABLE.&quot; WHERE series='&quot;.$series.&quot;' AND status='u'&quot;,$LINK_CARDS) or die(&quot;cards_list.php -&gt; err2 &quot;.mysql_error($LINK_CARDS));
        $used = mysql_num_rows ($result);
        mysql_free_result($result);
    
        $result = mysql_query (&quot;SELECT unix_timestamp(added) as unix_added, unix_timestamp(expired) as unix_expired FROM &quot;.CARDS_TABLE.&quot; WHERE series='&quot;.$series.&quot;' GROUP BY series&quot;,$LINK_CARDS) or die(&quot;cards_list.php -&gt; err2 &quot;.mysql_error($LINK_CARDS));
        if (mysql_num_rows ($result) &gt; 0)
          $row = mysql_fetch_object($result);
        mysql_free_result($result);
    
      echo &quot;&lt;FONT FACE=arial COLOR=green&gt;&lt;B&gt;Серия `&lt;FONT COLOR=red&gt;$series&lt;/FONT&gt;' &lt;FONT COLOR=black&gt;[&quot;.date(&quot;Y/m/d&quot;, $row-&gt;unix_expired).&quot;]&lt;/FONT&gt; (всего: &lt;FONT COLOR=blue&gt;$total&lt;/FONT&gt;, рабочих: &lt;FONT COLOR=blue&gt;$actived&lt;/FONT&gt;, блокированных: &lt;FONT COLOR=blue&gt;$locked&lt;/FONT&gt;, использованных: &lt;FONT COLOR=blue&gt;$used&lt;/FONT&gt;)&lt;/B&gt;&lt;/FONT&gt;&lt;BR&gt;&quot;;
      if ($row-&gt;unix_expired &lt;= time()) echo &quot;&lt;FONT SIZE=+1 FACE=arial COLOR=red&gt;&lt;B&gt;Внимание!!! Серия устарела!&lt;/B&gt;&lt;/FONT&gt;&lt;BR&gt;&quot;;
      echo &quot;&lt;FONT SIZE=+1 FACE=arial&gt;&lt;B&gt;&quot;;
      if ($total == $locked + $used) echo &quot;&lt;A HREF=save_series.php?series=$series&amp;action=unlock&gt;Разблокировать серию&lt;/A&gt;&quot;;
      else echo &quot;&lt;A HREF=save_series.php?series=$series&amp;action=lock&gt;Блокировать серию&lt;/A&gt;&quot;;
      echo &quot; | &lt;A onclick=\&quot;return confirm('Вы действительно хотите УДАЛИТЬ серию $series?')\&quot; HREF=real_del_series.php?series=$series&gt;Удалить серию&lt;/A&gt;&quot;;
      echo &quot;&lt;/B&gt;&lt;/FONT&gt;&lt;BR&gt;&quot;;
    ?&gt;
      &lt;HR&gt;
      &lt;TABLE BORDER=0 CELLSPACING=2 CELLPADDING=4 BGCOLOR=black&gt;
       &lt;TR ALIGN=center BGCOLOR=&quot;#99dd99&quot;&gt;
       &lt;TD&gt;&lt;B&gt;Номер&lt;BR&gt;карточки&lt;/B&gt;&lt;/TD&gt;
    
        &lt;TD&gt;&lt;B&gt;Номинал&lt;/B&gt;&lt;/TD&gt;
        &lt;TD&gt;&lt;B&gt;Состояние&lt;/B&gt;&lt;/TD&gt;
        &lt;TD&gt;&lt;B&gt;Действия&lt;/B&gt;&lt;/TD&gt;
        &lt;?php
        // рср лш АСДЕЛ ОНОНКМЪРЭ :)
        ?&gt;
        &lt;TD&gt;&lt;B&gt;IP&lt;/B&gt;&lt;/TD&gt;
        &lt;TD&gt;&lt;B&gt;login&lt;/B&gt;&lt;/TD&gt;
    
            &lt;TD&gt;&lt;B&gt;Номер &lt;BR&gt;(код пополнения)&lt;/B&gt;&lt;/TD&gt;
            &lt;TD&gt;дата поподнения&lt;/TD&gt;
       &lt;/TR&gt;
    &lt;?
    
    //    $result = mysql_query (&quot;SELECT sn, nominal, status FROM &quot;.CARDS_TABLE.&quot; WHERE series='&quot;.$series.&quot;'&quot;,$LINK_CARDS) or die(&quot;cards_list.php -&gt; err2 &quot;.mysql_error($LINK_CARDS));
        $result = mysql_query (&quot;SELECT sn, nominal, status, used_at, used_by, n, login FROM &quot;.CARDS_TABLE.&quot; WHERE series='&quot;.$series.&quot;'&quot;,$LINK_CARDS) or die(&quot;cards_list.php -&gt; err2 &quot;.mysql_error($LINK_CARDS));
        for ($i = 0; $i &lt; mysql_num_rows ($result); $i++) {
          $row = mysql_fetch_object ($result);
              //poriadkovij nomer carti/////////
    
    
              ///
              printf (&quot;   &lt;TR ALIGN=center BGCOLOR=\&quot;#%s\&quot;&gt;\n&quot;, ($row-&gt;status == 'a') ? &quot;eeeeee&quot; : (($row-&gt;status == 'u') ? &quot;dddd99&quot; : &quot;ffcccc&quot;));
    
    
          printf (&quot;    &lt;TD&gt;%s-%s-%s-%s-%s&lt;/TD&gt;\n&quot;, $series, substr($row-&gt;sn,0,4), substr($row-&gt;sn,4,4), substr($row-&gt;sn,8,4), substr($row-&gt;sn,12,2));
          printf (&quot;    &lt;TD&gt;%8.2f&lt;/TD&gt;\n&quot;, $row-&gt;nominal);
          printf (&quot;    &lt;TD&gt;%s&lt;/TD&gt;\n&quot;, ($row-&gt;status == 'a') ? &quot;&lt;A HREF=save_card.php?series=$series&amp;sn=$row-&gt;sn&amp;action=lock&gt;рабочая&lt;/A&gt;&quot; : (($row-&gt;status == 'u') ? &quot;использованна&quot; : &quot;&lt;A HREF=save_card.php?series=$series&amp;sn=$row-&gt;sn&amp;action=unlock&gt;блокированна&lt;/a&gt;&quot;));
          printf (&quot;    &lt;TD&gt;&lt;A onclick=\&quot;return confirm('Вы действительно хотите УДАЛИТЬ карточку : %s-%s-%s-%s-%s?')\&quot; HREF=real_del_card.php?series=$series&amp;sn=$row-&gt;sn&gt;Удалить&lt;/A&gt;&lt;/TD&gt;\n&quot;, $series, substr($row-&gt;sn,0,4), substr($row-&gt;sn,4,4), substr($row-&gt;sn,8,4), substr($row-&gt;sn,12,2));
    
        //my :)
    //login from
              printf (&quot;    &lt;TD&gt;%s&lt;/TD&gt;\n&quot;, $row-&gt;login);
        //IP from
              printf (&quot;    &lt;TD&gt;%s&lt;/TD&gt;\n&quot;, $row-&gt;used_by);
    
    
              printf (&quot;  &lt;TD&gt;%s-%s&lt;/TD&gt;\n&quot;, substr($row-&gt;n,0,4),substr($row-&gt;n,4,13));
    
    //            printf (&quot;    &lt;TD&gt;%s-%s-%s-%s-%s&lt;/TD&gt;\n&quot;,$row-&gt;nominal);
                  //, substr($row-&gt;n,0,4), substr($row-&gt;n,4,4), substr($row-&gt;n,8,4), substr($row-&gt;n,12,2));
                printf (&quot;    &lt;TD&gt;%s&lt;/TD&gt;\n&quot;, $row-&gt;used_at);
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
  - cards_list.php

---
скрипт нужный для работы с карточками<!--more-->

<pre lang="php"><?
include_once("defines.php");
if(!USE_CARDS) exit();

include_once("utils.php");

    $result = mysql_query ("SELECT * FROM ".CARDS_TABLE." WHERE series='".$series."' AND status='a'",$LINK_CARDS) or die("cards_list.php -> err2 ".mysql_error($LINK_CARDS));
    $actived = mysql_num_rows ($result);
    mysql_free_result($result);

    $result = mysql_query ("SELECT * FROM ".CARDS_TABLE." WHERE series='".$series."' AND status='l'",$LINK_CARDS) or die("cards_list.php -> err2 ".mysql_error($LINK_CARDS));
    $locked = mysql_num_rows ($result);
    mysql_free_result($result);

    $result = mysql_query ("SELECT * FROM ".CARDS_TABLE." WHERE series='".$series."' AND status='u'",$LINK_CARDS) or die("cards_list.php -> err2 ".mysql_error($LINK_CARDS));
    $used = mysql_num_rows ($result);
    mysql_free_result($result);

    $result = mysql_query ("SELECT unix_timestamp(added) as unix_added, unix_timestamp(expired) as unix_expired FROM ".CARDS_TABLE." WHERE series='".$series."' GROUP BY series",$LINK_CARDS) or die("cards_list.php -> err2 ".mysql_error($LINK_CARDS));
    if (mysql_num_rows ($result) > 0)
      $row = mysql_fetch_object($result);
    mysql_free_result($result);

  echo "&lt;FONT FACE=arial COLOR=green>

<B>Серия `&lt;FONT COLOR=red>$series&lt;/FONT>' &lt;FONT COLOR=black>[".date("Y/m/d", $row->unix_expired)."]&lt;/FONT> (всего: &lt;FONT COLOR=blue>$total&lt;/FONT>, рабочих: &lt;FONT COLOR=blue>$actived&lt;/FONT>, блокированных: &lt;FONT COLOR=blue>$locked&lt;/FONT>, использованных: &lt;FONT COLOR=blue>$used&lt;/FONT>)</B>&lt;/FONT><BR />";
  if ($row->unix_expired &lt;= time()) echo "&lt;FONT SIZE=+1 FACE=arial COLOR=red><B>Внимание!!! Серия устарела!</B>&lt;/FONT><BR />";
  echo "&lt;FONT SIZE=+1 FACE=arial><B>";
  if ($total == $locked + $used) echo "&lt;A HREF=save_series.php?series=$series&#038;action=unlock>Разблокировать серию&lt;/A>";
  else echo "&lt;A HREF=save_series.php?series=$series&#038;action=lock>Блокировать серию&lt;/A>";
  echo " | &lt;A onclick=\"return confirm('Вы действительно хотите УДАЛИТЬ серию $series?')\" HREF=real_del_series.php?series=$series>Удалить серию&lt;/A>";
  echo "</B>&lt;/FONT><BR />";
?>
  

<HR />
&lt;TABLE BORDER=0 CELLSPACING=2 CELLPADDING=4 BGCOLOR=black>
   &lt;TR ALIGN=center BGCOLOR="#99dd99">
   

<TD>
  <B>Номер<BR />карточки</B>
</TD>

    

<TD>
  <B>Номинал</B>
</TD>
    

<TD>
  <B>Состояние</B>
</TD>
    

<TD>
  <B>Действия</B>
</TD>
    

<?php
    // рср лш АСДЕЛ ОНОНКМЪРЭ 🙂
    ?>
    

<TD>
  <B>IP</B>
</TD>
    

<TD>
  <B>login</B>
</TD>

        

<TD>
  <B>Номер <BR />(код пополнения)</B>
</TD>
        

<TD>
  дата поподнения
</TD>
   &lt;/TR>


<?

//    $result = mysql_query ("SELECT sn, nominal, status FROM ".CARDS_TABLE." WHERE series='".$series."'",$LINK_CARDS) or die("cards_list.php -> err2 ".mysql_error($LINK_CARDS));
    $result = mysql_query ("SELECT sn, nominal, status, used_at, used_by, n, login FROM ".CARDS_TABLE." WHERE series='".$series."'",$LINK_CARDS) or die("cards_list.php -> err2 ".mysql_error($LINK_CARDS));
    for ($i = 0; $i &lt; mysql_num_rows ($result); $i++) {
      $row = mysql_fetch_object ($result);
          //poriadkovij nomer carti/////////


          ///
          printf ("   &lt;TR ALIGN=center BGCOLOR=\"#%s\">\n", ($row->status == 'a') ? "eeeeee" : (($row->status == 'u') ? "dddd99" : "ffcccc"));


      printf ("    

<TD>
  %s-%s-%s-%s-%s
</TD>\n", $series, substr($row->sn,0,4), substr($row->sn,4,4), substr($row->sn,8,4), substr($row->sn,12,2));
      printf ("    

<TD>
  %8.2f
</TD>\n", $row->nominal);
      printf ("    

<TD>
  %s
</TD>\n", ($row->status == 'a') ? "&lt;A HREF=save_card.php?series=$series&#038;sn=$row->sn&action=lock>рабочая&lt;/A>" : (($row->status == 'u') ? "использованна" : "&lt;A HREF=save_card.php?series=$series&#038;sn=$row->sn&action=unlock>блокированна&lt;/a>"));
      printf ("    

<TD>
  &lt;A onclick=\"return confirm('Вы действительно хотите УДАЛИТЬ карточку : %s-%s-%s-%s-%s?')\" HREF=real_del_card.php?series=$series&#038;sn=$row->sn>Удалить&lt;/A>
</TD>\n", $series, substr($row->sn,0,4), substr($row->sn,4,4), substr($row->sn,8,4), substr($row->sn,12,2));

    //my 🙂
//login from
          printf ("    

<TD>
  %s
</TD>\n", $row->login);
    //IP from
          printf ("    

<TD>
  %s
</TD>\n", $row->used_by);


          printf ("  

<TD>
  %s-%s
</TD>\n", substr($row->n,0,4),substr($row->n,4,13));

//            printf ("    

<TD>
  %s-%s-%s-%s-%s
</TD>\n",$row->nominal);
              //, substr($row->n,0,4), substr($row->n,4,4), substr($row->n,8,4), substr($row->n,12,2));
            printf ("    

<TD>
  %s
</TD>\n", $row->used_at);
      echo "   &lt;/TR>\n";
    }
    mysql_free_result ($result);
?>
&lt;/TABLE>

</pre>