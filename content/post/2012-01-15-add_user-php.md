---
title: add_user.php
author: wel
type: post
date: 2012-01-14T22:01:29+00:00
url: /billing/add_user-php
wp-syntax-cache-content:
  - |
    a:1:{i:1;s:38822:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="php" style="font-family:monospace;">&nbsp;
    <span style="color: #000000; font-weight: bold;">&lt;?</span>
    <span style="color: #b1b100;">include_once</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;mysql.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">include_once</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;extern.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000088;">$ext_add</span> <span style="color: #339933;">=</span> extern_check<span style="color: #009900;">&#40;</span><span style="color: #000088;">$user</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$ext_add</span> <span style="color: #339933;">&gt;</span> <span style="color: #cc66cc;">0</span><span style="color: #009900;">&#41;</span>
    <span style="color: #009900;">&#123;</span>
      <span style="color: #000088;">$TOP</span> <span style="color: #339933;">=</span> <span style="color: #0000ff;">&quot;Пользователь &quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$user</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot; уже существует в системе!&quot;</span><span style="color: #339933;">;</span>
      <span style="color: #b1b100;">include</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;top.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
      <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;  &lt;FONT SIZE=+2 COLOR=red&gt;Пользователь `&lt;FONT COLOR=blue&gt;<span style="color: #006699; font-weight: bold;">$user</span>&lt;/FONT&gt;' &lt;U&gt;уже существует в системе&lt;/U&gt;!&lt;/FONT&gt;&lt;BR&gt;<span style="color: #000099; font-weight: bold;">\n</span>&quot;</span><span style="color: #339933;">;</span>
      <span style="color: #b1b100;">include</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;bottom.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span>
    &nbsp;
    <span style="color: #000088;">$result</span><span style="color: #339933;">=</span><span style="color: #990000;">mysql_query</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;SELECT * FROM &quot;</span><span style="color: #339933;">.</span>NIBS_PACKETS_TABLE<span style="color: #339933;">.</span><span style="color: #0000ff;">&quot; WHERE gid=<span style="color: #006699; font-weight: bold;">$gid</span>&quot;</span><span style="color: #339933;">,</span><span style="color: #000088;">$LINK</span><span style="color: #009900;">&#41;</span> or <span style="color: #990000;">die</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;users.php(new_user_form2)  Неверный запрос к &quot;</span><span style="color: #339933;">.</span>NIBS_PACKETS_TABLE<span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$packet</span><span style="color: #339933;">=</span><span style="color: #990000;">mysql_fetch_array</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #990000;">mysql_free_result</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000088;">$result</span><span style="color: #339933;">=</span><span style="color: #990000;">mysql_query</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;SELECT * FROM &quot;</span><span style="color: #339933;">.</span>NIBS_AUTH_TABLE<span style="color: #339933;">.</span><span style="color: #0000ff;">&quot; WHERE user='&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$user</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;'&quot;</span><span style="color: #339933;">,</span><span style="color: #000088;">$LINK</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #990000;">mysql_num_rows</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span> <span style="color: #339933;">&gt;</span> <span style="color: #cc66cc;">0</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
      <span style="color: #000088;">$tmp_u</span><span style="color: #339933;">=</span><span style="color: #990000;">mysql_fetch_array</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
      <span style="color: #990000;">mysql_free_result</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
      <span style="color: #000088;">$TOP</span> <span style="color: #339933;">=</span> <span style="color: #0000ff;">&quot;Пользователь &quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$user</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot; уже существует в базе!&quot;</span><span style="color: #339933;">;</span>
      <span style="color: #b1b100;">include</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;top.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
      <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;  &lt;FONT SIZE=+2 COLOR=red&gt;Пользователь `&lt;A HREF=<span style="color: #000099; font-weight: bold;">\&quot;</span>edit_user.php?uid=&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$tmp_u</span><span style="color: #009900;">&#91;</span>uid<span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$user</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;&lt;/A&gt;' &lt;U&gt;уже существует в базе&lt;/U&gt;!&lt;/FONT&gt;&lt;BR&gt;<span style="color: #000099; font-weight: bold;">\n</span>&quot;</span><span style="color: #339933;">;</span>
      <span style="color: #b1b100;">include</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;bottom.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span>
    &nbsp;
    <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>create_system_user<span style="color: #009900;">&#93;</span> <span style="color: #339933;">&gt;</span> <span style="color: #cc66cc;">0</span><span style="color: #009900;">&#41;</span> AND <span style="color: #009900;">&#40;</span>extern_add<span style="color: #009900;">&#40;</span><span style="color: #000088;">$user</span><span style="color: #009900;">&#41;</span> <span style="color: #339933;">&lt;=</span> <span style="color: #cc66cc;">0</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span>
    <span style="color: #009900;">&#123;</span>
      <span style="color: #000088;">$TOP</span> <span style="color: #339933;">=</span> <span style="color: #0000ff;">&quot;Ощибка создания системного пользователя &quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$user</span><span style="color: #339933;">;</span>
      <span style="color: #b1b100;">include</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;top.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
      <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;  &lt;FONT SIZE=+2 COLOR=red&gt;Ощибка создания системного пользователя `&lt;FONT COLOR=blue&gt;<span style="color: #006699; font-weight: bold;">$user</span>&lt;/FONT&gt;'&lt;/FONT&gt;&lt;BR&gt;<span style="color: #000099; font-weight: bold;">\n</span>&quot;</span><span style="color: #339933;">;</span>
      <span style="color: #b1b100;">include</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;bottom.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span>
    &nbsp;
    <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>activated<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">1</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
      <span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>add_date<span style="color: #009900;">&#93;</span> <span style="color: #339933;">=</span> <span style="color: #990000;">date</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;Y-m-d&quot;</span><span style="color: #339933;">,</span><span style="color: #990000;">mktime</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span> <span style="color: #b1b100;">else</span> <span style="color: #009900;">&#123;</span>
      <span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>add_date<span style="color: #009900;">&#93;</span> <span style="color: #339933;">=</span> <span style="color: #0000ff;">&quot;0000-00-00&quot;</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span>
    &nbsp;
    &nbsp;
    <span style="color: #666666; font-style: italic;">//#mysql_query(&quot;INSERT INTO &quot;.NIBS_AUTH_TABLE.&quot; (user,gid,deposit,credit,add_date,blocked,activated) values ('$user', $gid, $packet[deposit], $packet[credit], '$packet[add_date]', $packet[blocked], $packet[activated])&quot;,$LINK) or die(&quot;add_user.php -&gt; err1 &quot;.mysql_error($LINK));</span>
    &nbsp;
    <span style="color: #000088;">$result</span><span style="color: #339933;">=</span><span style="color: #990000;">mysql_query</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;SELECT `last_ip`,`last_local_ip` FROM `freenibs`.`system` LIMIT 1&quot;</span><span style="color: #339933;">,</span><span style="color: #000088;">$LINK</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$res</span><span style="color: #339933;">=</span><span style="color: #990000;">mysql_fetch_array</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #990000;">mysql_free_result</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$last_ip_ar</span><span style="color: #339933;">=</span><span style="color: #990000;">explode</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;.&quot;</span><span style="color: #339933;">,</span><span style="color: #000088;">$res</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'last_ip'</span><span style="color: #009900;">&#93;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$last_local_ip_ar</span><span style="color: #339933;">=</span><span style="color: #990000;">explode</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;.&quot;</span><span style="color: #339933;">,</span><span style="color: #000088;">$res</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'last_local_ip'</span><span style="color: #009900;">&#93;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #666666; font-style: italic;">//foreach($a as $val){</span>
    <span style="color: #666666; font-style: italic;">//}</span>
    <span style="color: #000088;">$last_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">3</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">++;</span>
    <span style="color: #b1b100;">if</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$last_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">3</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">&gt;</span><span style="color: #cc66cc;">255</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#123;</span>
        <span style="color: #000088;">$last_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">2</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">++;</span>
        <span style="color: #000088;">$last_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">3</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">=</span><span style="color: #cc66cc;">1</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span>
    <span style="color: #b1b100;">if</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$last_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">2</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">&gt;</span><span style="color: #cc66cc;">255</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#123;</span>
        <span style="color: #000088;">$last_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">1</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">++;</span>
        <span style="color: #000088;">$last_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">2</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">=</span><span style="color: #cc66cc;">1</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span>
    &nbsp;
    &nbsp;
    &nbsp;
    <span style="color: #000088;">$last_local_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">3</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">--;</span>
    <span style="color: #b1b100;">if</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$last_local_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">3</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">&gt;</span><span style="color: #cc66cc;">255</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#123;</span>
        <span style="color: #000088;">$last_local_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">3</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">=</span><span style="color: #cc66cc;">255</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span>
    &nbsp;
    <span style="color: #b1b100;">if</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$last_local_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">3</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">&lt;</span><span style="color: #cc66cc;">0</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#123;</span>
        <span style="color: #000088;">$last_local_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">2</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">--;</span>
        <span style="color: #000088;">$last_local_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">3</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">=</span><span style="color: #cc66cc;">255</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span>
    <span style="color: #b1b100;">if</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$last_local_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">2</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">&gt;</span><span style="color: #cc66cc;">255</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#123;</span>
        <span style="color: #000088;">$last_local_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">1</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">--;</span>
        <span style="color: #000088;">$last_local_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">2</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">=</span><span style="color: #cc66cc;">1</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span>
    <span style="color: #b1b100;">if</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$last_local_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">2</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">&lt;</span><span style="color: #cc66cc;">0</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#123;</span>
            <span style="color: #000088;">$last_local_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">1</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">--;</span>
            <span style="color: #000088;">$last_local_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">2</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">=</span><span style="color: #cc66cc;">255</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span>
    &nbsp;
    &nbsp;
    <span style="color: #000088;">$last_ip</span><span style="color: #339933;">=</span><span style="color: #000088;">$last_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">0</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;.&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$last_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">1</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;.&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$last_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">2</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;.&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$last_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">3</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$last_local_ip</span><span style="color: #339933;">=</span><span style="color: #000088;">$last_local_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">0</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;.&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$last_local_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">1</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;.&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$last_local_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">2</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;.&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$last_local_ip_ar</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">3</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #666666; font-style: italic;">//echo &quot;INSERT INTO &quot;.NIBS_AUTH_TABLE.&quot; (user,gid,deposit,credit,add_date,blocked,activated,framed_ip) values ('$user', $gid, $packet[deposit], $packet[credit], '$packet[add_date]', $packet[blocked], $packet[activated]),$last_ip&quot;;</span>
    &nbsp;
    <span style="color: #990000;">mysql_query</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;UPDATE `freenibs`.`system` SET `freenibs`.`system`.`last_ip`='<span style="color: #006699; font-weight: bold;">$last_ip</span>',`freenibs`.`system`.`last_local_ip`='<span style="color: #006699; font-weight: bold;">$last_local_ip</span>'&quot;</span><span style="color: #339933;">,</span><span style="color: #000088;">$LINK</span><span style="color: #009900;">&#41;</span> or <span style="color: #990000;">die</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;add_user.php last_ip -&gt; err1 &quot;</span><span style="color: #339933;">.</span><span style="color: #990000;">mysql_error</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$LINK</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000088;">$result</span><span style="color: #339933;">=</span><span style="color: #990000;">mysql_query</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;SELECT MAX(`rule`) AS `max` FROM `bezlim`.`all`&quot;</span><span style="color: #339933;">,</span><span style="color: #000088;">$LINK</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$res</span><span style="color: #339933;">=</span><span style="color: #990000;">mysql_fetch_array</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #990000;">mysql_free_result</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$max_rule</span><span style="color: #339933;">=</span><span style="color: #000088;">$res</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'max'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">+</span><span style="color: #cc66cc;">2</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$bw</span><span style="color: #339933;">=</span><span style="color: #cc66cc;">0</span><span style="color: #339933;">;</span>
    &nbsp;
    &nbsp;
    <span style="color: #990000;">mysql_query</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;INSERT INTO `bezlim`.`all` (`ip`,`rule`,`bw1`,`bw2`,`activ`) values ('<span style="color: #006699; font-weight: bold;">$last_ip</span>','<span style="color: #006699; font-weight: bold;">$max_rule</span>','<span style="color: #006699; font-weight: bold;">$bw</span>','<span style="color: #006699; font-weight: bold;">$bw</span>','y')  &quot;</span><span style="color: #339933;">,</span><span style="color: #000088;">$LINK</span><span style="color: #009900;">&#41;</span> or <span style="color: #990000;">die</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;add_user.php bezlim -&gt; err1 &quot;</span><span style="color: #339933;">.</span><span style="color: #990000;">mysql_error</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$LINK</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    &nbsp;
    <span style="color: #990000;">mysql_query</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;INSERT INTO &quot;</span><span style="color: #339933;">.</span>NIBS_AUTH_TABLE<span style="color: #339933;">.</span><span style="color: #0000ff;">&quot; (user,gid,deposit,credit,add_date,blocked,activated,framed_ip,local_addr) values ('<span style="color: #006699; font-weight: bold;">$user</span>', <span style="color: #006699; font-weight: bold;">$gid</span>, <span style="color: #006699; font-weight: bold;">$packet[deposit]</span>, <span style="color: #006699; font-weight: bold;">$packet[credit]</span>, '<span style="color: #006699; font-weight: bold;">$packet[add_date]</span>', <span style="color: #006699; font-weight: bold;">$packet[blocked]</span>, <span style="color: #006699; font-weight: bold;">$packet[activated]</span>,'<span style="color: #006699; font-weight: bold;">$last_ip</span>','<span style="color: #006699; font-weight: bold;">$last_local_ip</span>')&quot;</span><span style="color: #339933;">,</span><span style="color: #000088;">$LINK</span><span style="color: #009900;">&#41;</span> or <span style="color: #990000;">die</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;add_user.php -&gt; err1 &quot;</span><span style="color: #339933;">.</span><span style="color: #990000;">mysql_error</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$LINK</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$uid</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_insert_id</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$LINK</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000088;">$result</span><span style="color: #339933;">=</span><span style="color: #990000;">mysql_query</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;SELECT * FROM &quot;</span><span style="color: #339933;">.</span>NIBS_AUTH_TABLE<span style="color: #339933;">.</span><span style="color: #0000ff;">&quot; WHERE uid=<span style="color: #006699; font-weight: bold;">$uid</span>&quot;</span><span style="color: #339933;">,</span><span style="color: #000088;">$LINK</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$res</span><span style="color: #339933;">=</span><span style="color: #990000;">mysql_fetch_array</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #990000;">mysql_free_result</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000088;">$result</span><span style="color: #339933;">=</span><span style="color: #990000;">mysql_query</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;SELECT * FROM &quot;</span><span style="color: #339933;">.</span>NIBS_PACKETS_TABLE<span style="color: #339933;">.</span><span style="color: #0000ff;">&quot; WHERE gid=&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$res</span><span style="color: #009900;">&#91;</span>gid<span style="color: #009900;">&#93;</span><span style="color: #339933;">,</span><span style="color: #000088;">$LINK</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$packet</span><span style="color: #339933;">=</span><span style="color: #990000;">mysql_fetch_array</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #990000;">mysql_free_result</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000088;">$user</span> <span style="color: #339933;">=</span> <span style="color: #000088;">$res</span><span style="color: #009900;">&#91;</span>user<span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000088;">$TOP</span> <span style="color: #339933;">=</span> <span style="color: #0000ff;">&quot;Пользователь `&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$user</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;' добавлен (uid=&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$uid</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;)&quot;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">include</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;top.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000000; font-weight: bold;">?&gt;</span>
    &nbsp;
      &lt;FONT SIZE=+2 COLOR=green&gt;Пользователь &lt;FONT COLOR=blue&gt;`<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$user</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>'&lt;/FONT&gt; добавлен (uid=<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$uid</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>)&lt;/FONT&gt;
    &nbsp;
    <span style="color: #000000; font-weight: bold;">&lt;?</span>
    <span style="color: #b1b100;">include</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;edit_user_menu.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000000; font-weight: bold;">?&gt;</span>
      &lt;HR&gt;
      &lt;A HREF=&quot;packet.php?gid=<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$res</span><span style="color: #009900;">&#91;</span>gid<span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;Вернуться&lt;/A&gt;
    <span style="color: #000000; font-weight: bold;">&lt;?</span>
    <span style="color: #b1b100;">include</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;bottom.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000000; font-weight: bold;">?&gt;</span></pre></td></tr></table><p class="theCode" style="display:none;">
    &lt;?
    include_once (&quot;mysql.php&quot;);
    include_once (&quot;extern.php&quot;);
    
    $ext_add = extern_check($user);
    
    if ($ext_add &gt; 0)
    {
      $TOP = &quot;Пользователь &quot;.$user.&quot; уже существует в системе!&quot;;
      include(&quot;top.php&quot;);
      echo &quot;  &lt;FONT SIZE=+2 COLOR=red&gt;Пользователь `&lt;FONT COLOR=blue&gt;$user&lt;/FONT&gt;' &lt;U&gt;уже существует в системе&lt;/U&gt;!&lt;/FONT&gt;&lt;BR&gt;\n&quot;;
      include(&quot;bottom.php&quot;);
    }
    
    $result=mysql_query(&quot;SELECT * FROM &quot;.NIBS_PACKETS_TABLE.&quot; WHERE gid=$gid&quot;,$LINK) or die(&quot;users.php(new_user_form2)  Неверный запрос к &quot;.NIBS_PACKETS_TABLE);
    $packet=mysql_fetch_array($result);
    mysql_free_result($result);
    
    $result=mysql_query(&quot;SELECT * FROM &quot;.NIBS_AUTH_TABLE.&quot; WHERE user='&quot;.$user.&quot;'&quot;,$LINK);
    if (mysql_num_rows($result) &gt; 0) {
      $tmp_u=mysql_fetch_array($result);
      mysql_free_result($result);
      $TOP = &quot;Пользователь &quot;.$user.&quot; уже существует в базе!&quot;;
      include(&quot;top.php&quot;);
      echo &quot;  &lt;FONT SIZE=+2 COLOR=red&gt;Пользователь `&lt;A HREF=\&quot;edit_user.php?uid=&quot;.$tmp_u[uid].&quot;\&quot;&gt;&quot;.$user.&quot;&lt;/A&gt;' &lt;U&gt;уже существует в базе&lt;/U&gt;!&lt;/FONT&gt;&lt;BR&gt;\n&quot;;
      include(&quot;bottom.php&quot;);
    }
    
    if (($packet[create_system_user] &gt; 0) AND (extern_add($user) &lt;= 0))
    {
      $TOP = &quot;Ощибка создания системного пользователя &quot;.$user;
      include(&quot;top.php&quot;);
      echo &quot;  &lt;FONT SIZE=+2 COLOR=red&gt;Ощибка создания системного пользователя `&lt;FONT COLOR=blue&gt;$user&lt;/FONT&gt;'&lt;/FONT&gt;&lt;BR&gt;\n&quot;;
      include(&quot;bottom.php&quot;);
    }
    
    if ($packet[activated] == 1) {
      $packet[add_date] = date(&quot;Y-m-d&quot;,mktime());
    } else {
      $packet[add_date] = &quot;0000-00-00&quot;;
    }
    
    
    //#mysql_query(&quot;INSERT INTO &quot;.NIBS_AUTH_TABLE.&quot; (user,gid,deposit,credit,add_date,blocked,activated) values ('$user', $gid, $packet[deposit], $packet[credit], '$packet[add_date]', $packet[blocked], $packet[activated])&quot;,$LINK) or die(&quot;add_user.php -&gt; err1 &quot;.mysql_error($LINK));
    
    $result=mysql_query(&quot;SELECT `last_ip`,`last_local_ip` FROM `freenibs`.`system` LIMIT 1&quot;,$LINK);
    $res=mysql_fetch_array($result);
    mysql_free_result($result);
    $last_ip_ar=explode(&quot;.&quot;,$res['last_ip']);
    $last_local_ip_ar=explode(&quot;.&quot;,$res['last_local_ip']);
    //foreach($a as $val){
    //}
    $last_ip_ar[3]++;
    if($last_ip_ar[3]&gt;255){
        $last_ip_ar[2]++;
        $last_ip_ar[3]=1;
    }
    if($last_ip_ar[2]&gt;255){
        $last_ip_ar[1]++;
        $last_ip_ar[2]=1;
    }
    
    
    
    $last_local_ip_ar[3]--;
    if($last_local_ip_ar[3]&gt;255){
        $last_local_ip_ar[3]=255;
    }
    
    if($last_local_ip_ar[3]&lt;0){
        $last_local_ip_ar[2]--;
        $last_local_ip_ar[3]=255;
    }
    if($last_local_ip_ar[2]&gt;255){
        $last_local_ip_ar[1]--;
        $last_local_ip_ar[2]=1;
    }
    if($last_local_ip_ar[2]&lt;0){
            $last_local_ip_ar[1]--;
            $last_local_ip_ar[2]=255;
    }
    
    
    $last_ip=$last_ip_ar[0].&quot;.&quot;.$last_ip_ar[1].&quot;.&quot;.$last_ip_ar[2].&quot;.&quot;.$last_ip_ar[3];
    $last_local_ip=$last_local_ip_ar[0].&quot;.&quot;.$last_local_ip_ar[1].&quot;.&quot;.$last_local_ip_ar[2].&quot;.&quot;.$last_local_ip_ar[3];
    
    //echo &quot;INSERT INTO &quot;.NIBS_AUTH_TABLE.&quot; (user,gid,deposit,credit,add_date,blocked,activated,framed_ip) values ('$user', $gid, $packet[deposit], $packet[credit], '$packet[add_date]', $packet[blocked], $packet[activated]),$last_ip&quot;;
    
    mysql_query(&quot;UPDATE `freenibs`.`system` SET `freenibs`.`system`.`last_ip`='$last_ip',`freenibs`.`system`.`last_local_ip`='$last_local_ip'&quot;,$LINK) or die(&quot;add_user.php last_ip -&gt; err1 &quot;.mysql_error($LINK));
    
    $result=mysql_query(&quot;SELECT MAX(`rule`) AS `max` FROM `bezlim`.`all`&quot;,$LINK);
    $res=mysql_fetch_array($result);
    mysql_free_result($result);
    $max_rule=$res['max']+2;
    $bw=0;
    
    
    mysql_query(&quot;INSERT INTO `bezlim`.`all` (`ip`,`rule`,`bw1`,`bw2`,`activ`) values ('$last_ip','$max_rule','$bw','$bw','y')  &quot;,$LINK) or die(&quot;add_user.php bezlim -&gt; err1 &quot;.mysql_error($LINK));
    
    
    mysql_query(&quot;INSERT INTO &quot;.NIBS_AUTH_TABLE.&quot; (user,gid,deposit,credit,add_date,blocked,activated,framed_ip,local_addr) values ('$user', $gid, $packet[deposit], $packet[credit], '$packet[add_date]', $packet[blocked], $packet[activated],'$last_ip','$last_local_ip')&quot;,$LINK) or die(&quot;add_user.php -&gt; err1 &quot;.mysql_error($LINK));
    $uid = mysql_insert_id($LINK);
    
    $result=mysql_query(&quot;SELECT * FROM &quot;.NIBS_AUTH_TABLE.&quot; WHERE uid=$uid&quot;,$LINK);
    $res=mysql_fetch_array($result);
    mysql_free_result($result);
    
    $result=mysql_query(&quot;SELECT * FROM &quot;.NIBS_PACKETS_TABLE.&quot; WHERE gid=&quot;.$res[gid],$LINK);
    $packet=mysql_fetch_array($result);
    mysql_free_result($result);
    
    $user = $res[user];
    
    $TOP = &quot;Пользователь `&quot;.$user.&quot;' добавлен (uid=&quot;.$uid.&quot;)&quot;;
    include(&quot;top.php&quot;);
    ?&gt;
    
      &lt;FONT SIZE=+2 COLOR=green&gt;Пользователь &lt;FONT COLOR=blue&gt;`&lt;? echo $user; ?&gt;'&lt;/FONT&gt; добавлен (uid=&lt;? echo $uid; ?&gt;)&lt;/FONT&gt;
    
    &lt;?
    include(&quot;edit_user_menu.php&quot;);
    ?&gt;
      &lt;HR&gt;
      &lt;A HREF=&quot;packet.php?gid=&lt;? echo $res[gid]; ?&gt;&quot;&gt;Вернуться&lt;/A&gt;
    &lt;?
    include(&quot;bottom.php&quot;);
    ?&gt;</p></div>
    ";}
categories:
  - billing
  - FreeNIBS
tags:
  - add_user.php

---
add_user.php
  
<!--more-->

<pre lang="php"><?
include_once ("mysql.php");
include_once ("extern.php");

$ext_add = extern_check($user);

if ($ext_add > 0)
{
  $TOP = "Пользователь ".$user." уже существует в системе!";
  include("top.php");
  echo "  &lt;FONT SIZE=+2 COLOR=red>Пользователь `&lt;FONT COLOR=blue>$user&lt;/FONT>' &lt;U>уже существует в системе&lt;/U>!&lt;/FONT>

<BR />\n";
  include("bottom.php");
}

$result=mysql_query("SELECT * FROM ".NIBS_PACKETS_TABLE." WHERE gid=$gid",$LINK) or die("users.php(new_user_form2)  Неверный запрос к ".NIBS_PACKETS_TABLE);
$packet=mysql_fetch_array($result);
mysql_free_result($result);

$result=mysql_query("SELECT * FROM ".NIBS_AUTH_TABLE." WHERE user='".$user."'",$LINK);
if (mysql_num_rows($result) > 0) {
  $tmp_u=mysql_fetch_array($result);
  mysql_free_result($result);
  $TOP = "Пользователь ".$user." уже существует в базе!";
  include("top.php");
  echo "  &lt;FONT SIZE=+2 COLOR=red>Пользователь `&lt;A HREF=\"edit_user.php?uid=".$tmp_u[uid]."\">".$user."&lt;/A>' &lt;U>уже существует в базе&lt;/U>!&lt;/FONT><BR />\n";
  include("bottom.php");
}

if (($packet[create_system_user] > 0) AND (extern_add($user) &lt;= 0))
{
  $TOP = "Ощибка создания системного пользователя ".$user;
  include("top.php");
  echo "  &lt;FONT SIZE=+2 COLOR=red>Ощибка создания системного пользователя `&lt;FONT COLOR=blue>$user&lt;/FONT>'&lt;/FONT><BR />\n";
  include("bottom.php");
}

if ($packet[activated] == 1) {
  $packet[add_date] = date("Y-m-d",mktime());
} else {
  $packet[add_date] = "0000-00-00";
}


//#mysql_query("INSERT INTO ".NIBS_AUTH_TABLE." (user,gid,deposit,credit,add_date,blocked,activated) values ('$user', $gid, $packet[deposit], $packet[credit], '$packet[add_date]', $packet[blocked], $packet[activated])",$LINK) or die("add_user.php -> err1 ".mysql_error($LINK));

$result=mysql_query("SELECT `last_ip`,`last_local_ip` FROM `freenibs`.`system` LIMIT 1",$LINK);
$res=mysql_fetch_array($result);
mysql_free_result($result);
$last_ip_ar=explode(".",$res['last_ip']);
$last_local_ip_ar=explode(".",$res['last_local_ip']);
//foreach($a as $val){
//}
$last_ip_ar[3]++;
if($last_ip_ar[3]>255){
    $last_ip_ar[2]++;
    $last_ip_ar[3]=1;
}
if($last_ip_ar[2]>255){
    $last_ip_ar[1]++;
    $last_ip_ar[2]=1;
}



$last_local_ip_ar[3]--;
if($last_local_ip_ar[3]>255){
    $last_local_ip_ar[3]=255;
}

if($last_local_ip_ar[3]&lt;0){
    $last_local_ip_ar[2]--;
    $last_local_ip_ar[3]=255;
}
if($last_local_ip_ar[2]>255){
    $last_local_ip_ar[1]--;
    $last_local_ip_ar[2]=1;
}
if($last_local_ip_ar[2]&lt;0){
        $last_local_ip_ar[1]--;
        $last_local_ip_ar[2]=255;
}


$last_ip=$last_ip_ar[0].".".$last_ip_ar[1].".".$last_ip_ar[2].".".$last_ip_ar[3];
$last_local_ip=$last_local_ip_ar[0].".".$last_local_ip_ar[1].".".$last_local_ip_ar[2].".".$last_local_ip_ar[3];

//echo "INSERT INTO ".NIBS_AUTH_TABLE." (user,gid,deposit,credit,add_date,blocked,activated,framed_ip) values ('$user', $gid, $packet[deposit], $packet[credit], '$packet[add_date]', $packet[blocked], $packet[activated]),$last_ip";

mysql_query("UPDATE `freenibs`.`system` SET `freenibs`.`system`.`last_ip`='$last_ip',`freenibs`.`system`.`last_local_ip`='$last_local_ip'",$LINK) or die("add_user.php last_ip -> err1 ".mysql_error($LINK));

$result=mysql_query("SELECT MAX(`rule`) AS `max` FROM `bezlim`.`all`",$LINK);
$res=mysql_fetch_array($result);
mysql_free_result($result);
$max_rule=$res['max']+2;
$bw=0;


mysql_query("INSERT INTO `bezlim`.`all` (`ip`,`rule`,`bw1`,`bw2`,`activ`) values ('$last_ip','$max_rule','$bw','$bw','y')  ",$LINK) or die("add_user.php bezlim -> err1 ".mysql_error($LINK));


mysql_query("INSERT INTO ".NIBS_AUTH_TABLE." (user,gid,deposit,credit,add_date,blocked,activated,framed_ip,local_addr) values ('$user', $gid, $packet[deposit], $packet[credit], '$packet[add_date]', $packet[blocked], $packet[activated],'$last_ip','$last_local_ip')",$LINK) or die("add_user.php -> err1 ".mysql_error($LINK));
$uid = mysql_insert_id($LINK);

$result=mysql_query("SELECT * FROM ".NIBS_AUTH_TABLE." WHERE uid=$uid",$LINK);
$res=mysql_fetch_array($result);
mysql_free_result($result);

$result=mysql_query("SELECT * FROM ".NIBS_PACKETS_TABLE." WHERE gid=".$res[gid],$LINK);
$packet=mysql_fetch_array($result);
mysql_free_result($result);

$user = $res[user];

$TOP = "Пользователь `".$user."' добавлен (uid=".$uid.")";
include("top.php");
?>

  &lt;FONT SIZE=+2 COLOR=green>Пользователь &lt;FONT COLOR=blue>`<? echo $user; ?>'&lt;/FONT> добавлен (uid=

<? echo $uid; ?>)&lt;/FONT>



<?
include("edit_user_menu.php");
?>
  

<HR />

<A HREF="packet.php?gid=<? echo $res[gid]; ?>">Вернуться</A>
<?
include("bottom.php");
?>

</pre>