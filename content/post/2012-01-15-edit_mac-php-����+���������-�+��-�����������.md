---
title: edit_mac.php — изменение мак-адресса
author: wel
type: post
date: 2012-01-14T23:44:37+00:00
url: /billing/edit_mac-php-изменение-мак-адресса
wp-syntax-cache-content:
  - |
    a:1:{i:1;s:15376:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="php" style="font-family:monospace;"><span style="color: #000000; font-weight: bold;">&lt;?php</span>
    <span style="color: #b1b100;">include_once</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;top.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">include_once</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;mysql.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000000; font-weight: bold;">?&gt;</span>
    &lt;FORM ACTION=save_mac.php?host=<span style="color: #000000; font-weight: bold;">&lt;?php</span> <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;<span style="color: #006699; font-weight: bold;">$host</span>&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span> METHOD=POST&gt;
    <span style="color: #000000; font-weight: bold;">&lt;?php</span>
    &nbsp;
    <span style="color: #000088;">$err</span><span style="color: #339933;">=</span><span style="color: #000088;">$_GET</span><span style="color: #009900;">&#91;</span>err<span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$err</span><span style="color: #009900;">&#41;</span>
    <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$err</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000088;">$m</span><span style="color: #339933;">=</span><span style="color: #990000;">mysql_query</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;SELECT * FROM host WHERE id='&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$host</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;'&quot;</span><span style="color: #339933;">,</span><span style="color: #000088;">$LINK_MAC</span><span style="color: #009900;">&#41;</span> or <span style="color: #990000;">die</span> <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;не могу подключиться к MAC&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$n</span><span style="color: #339933;">=</span><span style="color: #990000;">mysql_num_rows</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$m</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$n</span><span style="color: #339933;">&gt;</span><span style="color: #cc66cc;">0</span><span style="color: #009900;">&#41;</span>
    <span style="color: #009900;">&#123;</span>
    <span style="color: #b1b100;">for</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$i</span><span style="color: #339933;">=</span><span style="color: #cc66cc;">0</span><span style="color: #339933;">;</span> <span style="color: #000088;">$i</span><span style="color: #339933;">&lt;</span><span style="color: #000088;">$n</span><span style="color: #339933;">;</span> <span style="color: #000088;">$i</span><span style="color: #339933;">++</span><span style="color: #009900;">&#41;</span>
            <span style="color: #009900;">&#123;</span>
            <span style="color: #000088;">$row</span><span style="color: #339933;">=</span><span style="color: #990000;">mysql_fetch_array</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$m</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;TABLE border=1&gt;
    &lt;TR&gt;
    &quot;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;TD BGCOLOR=<span style="color: #000099; font-weight: bold;">\&quot;</span>#99dd99<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;Название:&lt;/TD&gt;&lt;TD BGCOLOR=<span style="color: #000099; font-weight: bold;">\&quot;</span>#dddd99<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;
    &lt;INPUT TYPE=text SIZE=20 NAME=hostnam VALUE=<span style="color: #000099; font-weight: bold;">\&quot;</span>&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'host'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;&lt;/TD&gt;&lt;/TR&gt;&lt;BR&gt;&quot;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;TD BGCOLOR=<span style="color: #000099; font-weight: bold;">\&quot;</span>#99dd99<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;MAC-адресс:&lt;/TD&gt;&lt;TD BGCOLOR=<span style="color: #000099; font-weight: bold;">\&quot;</span>#dddd99<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;
    &lt;INPUT TYPE=text SIZE=20 NAME=mac VALUE=<span style="color: #000099; font-weight: bold;">\&quot;</span>&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'mac'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;&lt;/TD&gt;&lt;/TR&gt;&lt;BR&gt;&quot;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'en'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">==</span><span style="color: #0000ff;">'e'</span><span style="color: #009900;">&#41;</span>
    <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;TD BGCOLOR=<span style="color: #000099; font-weight: bold;">\&quot;</span>#99dd99<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;Статус:&lt;/TD&gt;&lt;TD BGCOLOR=<span style="color: #000099; font-weight: bold;">\&quot;</span>#dddd99<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;
    &lt;SELECT NAME=<span style="color: #000099; font-weight: bold;">\&quot;</span>en[]<span style="color: #000099; font-weight: bold;">\&quot;</span> &gt;
    &lt;OPTION&gt;Активный
    &lt;OPTION&gt;Неактивный
    &lt;/SELECT&gt;&lt;/TD&gt;&lt;/TR&gt;&lt;BR&gt;&quot;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'en'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">==</span><span style="color: #0000ff;">'d'</span><span style="color: #009900;">&#41;</span>
    <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;TD BGCOLOR=<span style="color: #000099; font-weight: bold;">\&quot;</span>#99dd99<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;Статус:&lt;/TD&gt;&lt;TD BGCOLOR=<span style="color: #000099; font-weight: bold;">\&quot;</span>#dddd99<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;&lt;SELECT NAME=<span style="color: #000099; font-weight: bold;">\&quot;</span>en[]<span style="color: #000099; font-weight: bold;">\&quot;</span> &gt;
    &lt;OPTION&gt;Неактивный
    &lt;OPTION&gt;Активный
    &lt;/SELECT&gt;&lt;/TD&gt;&lt;/TR&gt;&lt;BR&gt;&quot;</span><span style="color: #339933;">;</span>
    &nbsp;
    &nbsp;
    <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;TD BGCOLOR=<span style="color: #000099; font-weight: bold;">\&quot;</span>#99dd99<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;IP-адресс:&lt;/TD&gt;&lt;TD BGCOLOR=<span style="color: #000099; font-weight: bold;">\&quot;</span>#dddd99<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;
    &lt;INPUT TYPE=text SIZE=20 NAME=ip VALUE=<span style="color: #000099; font-weight: bold;">\&quot;</span>&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'ipv4'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;&lt;/TD&gt;&lt;/TR&gt;&lt;BR&gt;&quot;</span><span style="color: #339933;">;</span>
    &nbsp;
            <span style="color: #009900;">&#125;</span>
    &nbsp;
    <span style="color: #009900;">&#125;</span>
     <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;TD BGCOLOR=<span style="color: #000099; font-weight: bold;">\&quot;</span>#dddd99<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;&lt;BR&gt;&amp;nbsp;&amp;nbsp;&amp;nbsp;&lt;INPUT TYPE=submit VALUE=сохранить&gt;
    &lt;/TD&gt;&lt;BR&gt;
    &quot;</span><span style="color: #339933;">;</span>
    <span style="color: #666666; font-style: italic;">//&lt;A HREF=\&quot;edit_mac.php?host=&quot;.$host.&quot;\&quot;&gt;удалить&lt;/a&gt; &quot;;</span>
    <span style="color: #000000; font-weight: bold;">?&gt;</span>
    &lt;BR&gt;
    &lt;/FORM&gt;
    &lt;FORM ACTION=save_mac.php?delete=<span style="color: #000000; font-weight: bold;">&lt;?php</span> <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;<span style="color: #006699; font-weight: bold;">$host</span>&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span> METHOD=POST&gt;
    &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;BR&gt;&amp;nbsp;&amp;nbsp;&amp;nbsp;&lt;INPUT TYPE=submit VALUE=удалить&gt;
    &lt;/TD&gt;&lt;/TR&gt;&lt;BR&gt;
    &lt;/FORM&gt;
    &nbsp;
    &nbsp;
    <span style="color: #000000; font-weight: bold;">&lt;?php</span>
    <span style="color: #666666; font-style: italic;">/////////</span>
    <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;
     &lt;/TR&gt;
    &lt;/TABLE&gt;&quot;</span><span style="color: #339933;">;</span>
    &nbsp;
    &nbsp;
    &nbsp;
    <span style="color: #666666; font-style: italic;">////////</span>
    &nbsp;
    <span style="color: #000088;">$REF</span><span style="color: #339933;">=</span><span style="color: #000088;">$HTTP_REFERER</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #666666; font-style: italic;">//echo $PHP_SELF.&quot;:&quot;.$REF;</span>
    &nbsp;
    <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$REF</span><span style="color: #339933;">!=</span><span style="color: #000088;">$PHP_SELF</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">&amp;&amp;</span><span style="color: #990000;">strlen</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$REF</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">&gt;</span><span style="color: #cc66cc;">0</span><span style="color: #009900;">&#41;</span>
    &nbsp;
    <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;||&lt;A HREF=<span style="color: #000099; font-weight: bold;">\&quot;</span><span style="color: #006699; font-weight: bold;">$REF</span><span style="color: #000099; font-weight: bold;">\&quot;</span> &gt;Вернуться назад&lt;/A&gt;||&quot;</span><span style="color: #339933;">;</span>
    &nbsp;
    &nbsp;
    <span style="color: #b1b100;">include_once</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;bottom.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span></pre></td></tr></table><p class="theCode" style="display:none;">&lt;?php
    include_once(&quot;top.php&quot;);
    include_once(&quot;mysql.php&quot;);
    ?&gt;
    &lt;FORM ACTION=save_mac.php?host=&lt;?php echo &quot;$host&quot;; ?&gt; METHOD=POST&gt;
    &lt;?php
    
    $err=$_GET[err];
    if ($err)
    echo $err;
    
    $m=mysql_query(&quot;SELECT * FROM host WHERE id='&quot;.$host.&quot;'&quot;,$LINK_MAC) or die (&quot;не могу подключиться к MAC&quot;);
    $n=mysql_num_rows($m);
    if ($n&gt;0)
    {
    for ($i=0; $i&lt;$n; $i++)
            {
            $row=mysql_fetch_array($m);
    echo &quot;&lt;TABLE border=1&gt;
    &lt;TR&gt;
    &quot;;
    echo &quot;&lt;TD BGCOLOR=\&quot;#99dd99\&quot;&gt;Название:&lt;/TD&gt;&lt;TD BGCOLOR=\&quot;#dddd99\&quot;&gt;
    &lt;INPUT TYPE=text SIZE=20 NAME=hostnam VALUE=\&quot;&quot;.$row['host'].&quot;\&quot;&gt;&lt;/TD&gt;&lt;/TR&gt;&lt;BR&gt;&quot;;
    
    echo &quot;&lt;TD BGCOLOR=\&quot;#99dd99\&quot;&gt;MAC-адресс:&lt;/TD&gt;&lt;TD BGCOLOR=\&quot;#dddd99\&quot;&gt;
    &lt;INPUT TYPE=text SIZE=20 NAME=mac VALUE=\&quot;&quot;.$row['mac'].&quot;\&quot;&gt;&lt;/TD&gt;&lt;/TR&gt;&lt;BR&gt;&quot;;
    
    if ($row['en']=='e')
    echo &quot;&lt;TD BGCOLOR=\&quot;#99dd99\&quot;&gt;Статус:&lt;/TD&gt;&lt;TD BGCOLOR=\&quot;#dddd99\&quot;&gt;
    &lt;SELECT NAME=\&quot;en[]\&quot; &gt;
    &lt;OPTION&gt;Активный
    &lt;OPTION&gt;Неактивный
    &lt;/SELECT&gt;&lt;/TD&gt;&lt;/TR&gt;&lt;BR&gt;&quot;;
    if ($row['en']=='d')
    echo &quot;&lt;TD BGCOLOR=\&quot;#99dd99\&quot;&gt;Статус:&lt;/TD&gt;&lt;TD BGCOLOR=\&quot;#dddd99\&quot;&gt;&lt;SELECT NAME=\&quot;en[]\&quot; &gt;
    &lt;OPTION&gt;Неактивный
    &lt;OPTION&gt;Активный
    &lt;/SELECT&gt;&lt;/TD&gt;&lt;/TR&gt;&lt;BR&gt;&quot;;
    
    
    echo &quot;&lt;TD BGCOLOR=\&quot;#99dd99\&quot;&gt;IP-адресс:&lt;/TD&gt;&lt;TD BGCOLOR=\&quot;#dddd99\&quot;&gt;
    &lt;INPUT TYPE=text SIZE=20 NAME=ip VALUE=\&quot;&quot;.$row['ipv4'].&quot;\&quot;&gt;&lt;/TD&gt;&lt;/TR&gt;&lt;BR&gt;&quot;;
    
            }
    
    }
     echo &quot;&lt;TD BGCOLOR=\&quot;#dddd99\&quot;&gt;&lt;BR&gt;&amp;nbsp;&amp;nbsp;&amp;nbsp;&lt;INPUT TYPE=submit VALUE=сохранить&gt;
    &lt;/TD&gt;&lt;BR&gt;
    &quot;;
    //&lt;A HREF=\&quot;edit_mac.php?host=&quot;.$host.&quot;\&quot;&gt;удалить&lt;/a&gt; &quot;;
    ?&gt;
    &lt;BR&gt;
    &lt;/FORM&gt;
    &lt;FORM ACTION=save_mac.php?delete=&lt;?php echo &quot;$host&quot;; ?&gt; METHOD=POST&gt;
    &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;BR&gt;&amp;nbsp;&amp;nbsp;&amp;nbsp;&lt;INPUT TYPE=submit VALUE=удалить&gt;
    &lt;/TD&gt;&lt;/TR&gt;&lt;BR&gt;
    &lt;/FORM&gt;
    
    
    &lt;?php
    /////////
    echo &quot;
     &lt;/TR&gt;
    &lt;/TABLE&gt;&quot;;
    
    
    
    ////////
    
    $REF=$HTTP_REFERER;
    
    //echo $PHP_SELF.&quot;:&quot;.$REF;
    
    if (($REF!=$PHP_SELF)&amp;&amp;strlen($REF)&gt;0)
    
    echo &quot;||&lt;A HREF=\&quot;$REF\&quot; &gt;Вернуться назад&lt;/A&gt;||&quot;;
    
    
    include_once(&quot;bottom.php&quot;);</p></div>
    ";}
categories:
  - billing
  - FreeNIBS

---
edit_mac.php — изменение мак-адресса<!--more-->

<pre lang="php"><?php
include_once("top.php");
include_once("mysql.php");
?>
&lt;FORM ACTION=save_mac.php?host=

<?php echo "$host"; ?> METHOD=POST>


<?php

$err=$_GET[err];
if ($err)
echo $err;

$m=mysql_query("SELECT * FROM host WHERE id='".$host."'",$LINK_MAC) or die ("не могу подключиться к MAC");
$n=mysql_num_rows($m);
if ($n>0)
{
for ($i=0; $i&lt;$n; $i++)
        {
        $row=mysql_fetch_array($m);
echo "&lt;TABLE border=1>


<TR>
  ";
  echo "&lt;TD BGCOLOR=\"#99dd99\">Название:&lt;/TD>&lt;TD BGCOLOR=\"#dddd99\">
  &lt;INPUT TYPE=text SIZE=20 NAME=hostnam VALUE=\"".$row['host']."\">&lt;/TD>
</TR>

<BR />";

echo "&lt;TD BGCOLOR=\"#99dd99\">MAC-адресс:&lt;/TD>&lt;TD BGCOLOR=\"#dddd99\">
&lt;INPUT TYPE=text SIZE=20 NAME=mac VALUE=\"".$row['mac']."\">&lt;/TD>&lt;/TR><BR />";

if ($row['en']=='e')
echo "&lt;TD BGCOLOR=\"#99dd99\">Статус:&lt;/TD>&lt;TD BGCOLOR=\"#dddd99\">
&lt;SELECT NAME=\"en[]\" >
&lt;OPTION>Активный
&lt;OPTION>Неактивный
&lt;/SELECT>&lt;/TD>&lt;/TR><BR />";
if ($row['en']=='d')
echo "&lt;TD BGCOLOR=\"#99dd99\">Статус:&lt;/TD>&lt;TD BGCOLOR=\"#dddd99\">&lt;SELECT NAME=\"en[]\" >
&lt;OPTION>Неактивный
&lt;OPTION>Активный
&lt;/SELECT>&lt;/TD>&lt;/TR><BR />";


echo "&lt;TD BGCOLOR=\"#99dd99\">IP-адресс:&lt;/TD>&lt;TD BGCOLOR=\"#dddd99\">
&lt;INPUT TYPE=text SIZE=20 NAME=ip VALUE=\"".$row['ipv4']."\">&lt;/TD>&lt;/TR><BR />";

        }

}
 echo "&lt;TD BGCOLOR=\"#dddd99\"><BR />&nbsp;&nbsp;&nbsp;&lt;INPUT TYPE=submit VALUE=сохранить>
&lt;/TD><BR />
";
//&lt;A HREF=\"edit_mac.php?host=".$host."\">удалить&lt;/a> ";
?>
<BR />
&lt;/FORM>
&lt;FORM ACTION=save_mac.php?delete=<?php echo "$host"; ?> METHOD=POST>


<TD BGCOLOR="#dddd99">
  <BR />&nbsp;&nbsp;&nbsp;&lt;INPUT TYPE=submit VALUE=удалить>
  
</TD>&lt;/TR>

<BR />
&lt;/FORM>


<?php
/////////
echo "
 </TR>
&lt;/TABLE>";



////////

$REF=$HTTP_REFERER;

//echo $PHP_SELF.":".$REF;

if (($REF!=$PHP_SELF)&&strlen($REF)>0)

echo "||&lt;A HREF=\"$REF\" >Вернуться назад&lt;/A>||";


include_once("bottom.php");

</pre>