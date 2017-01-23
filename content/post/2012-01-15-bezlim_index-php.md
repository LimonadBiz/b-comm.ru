---
title: bezlim_index.php
author: wel
type: post
date: 2012-01-14T23:22:13+00:00
url: /billing/bezlim_index-php
wp-syntax-cache-content:
  - |
    a:1:{i:1;s:17903:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="php" style="font-family:monospace;">bezlim_index.php
    <span style="color: #000000; font-weight: bold;">&lt;?php</span>
    <span style="color: #b1b100;">include_once</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;top.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">include_once</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;mysql.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">include_once</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;my_fill.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$REF</span><span style="color: #339933;">=</span><span style="color: #000088;">$HTTP_REFERER</span><span style="color: #339933;">;</span>
    &nbsp;
    &nbsp;
    <span style="color: #000088;">$my_query</span> <span style="color: #339933;">=</span> <span style="color: #000000; font-weight: bold;">new</span> my_fill<span style="color: #009900;">&#40;</span><span style="color: #000088;">$LINK_BEZLIM</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #666666; font-style: italic;">//if (($REF!=$PHP_SELF)&amp;&amp;strlen($REF)&gt;0)</span>
    <span style="color: #666666; font-style: italic;">//echo &quot;||&lt;A HREF=\&quot;$REF\&quot; &gt;назад&lt;/A&gt;||&quot;;</span>
    <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$_GET</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;delete&quot;</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">==</span><span style="color: #0000ff;">&quot;all&quot;</span><span style="color: #009900;">&#41;</span>
    <span style="color: #009900;">&#123;</span>
    <span style="color: #000088;">$my_query</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">deleteall</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span>
    <span style="color: #000000; font-weight: bold;">?&gt;</span>
            &lt;A HREF=&quot; <span style="color: #000000; font-weight: bold;">&lt;?php</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$PHP_SELF</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>?view=activ&quot;&gt;&lt;B&gt;Просмотр незанятых ип:
                    <span style="color: #000000; font-weight: bold;">&lt;?php</span>
                            <span style="color: #000088;">$q</span><span style="color: #339933;">=</span><span style="color: #0000ff;">&quot;SELECT * FROM `all` WHERE activ='y' or activ='Y'&quot;</span><span style="color: #339933;">;</span>
                            <span style="color: #000088;">$my_query</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">getn</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$q</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
                    <span style="color: #000000; font-weight: bold;">?&gt;</span>
            &lt;/A&gt;
    &lt;BR&gt;
            &lt;A HREF=&quot; <span style="color: #000000; font-weight: bold;">&lt;?php</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$PHP_SELF</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>?view=deactiv&quot;&gt;&lt;B&gt;Просмотр отключенных ип:
                    <span style="color: #000000; font-weight: bold;">&lt;?php</span>
                            <span style="color: #000088;">$q</span><span style="color: #339933;">=</span><span style="color: #0000ff;">&quot;SELECT * FROM `all` WHERE activ='N' or activ='n'&quot;</span><span style="color: #339933;">;</span>
                            <span style="color: #000088;">$my_query</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">getn</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$q</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
                    <span style="color: #000000; font-weight: bold;">?&gt;</span>
            &lt;/A&gt;
    &lt;BR&gt;
    &nbsp;
            &lt;A HREF=&quot; <span style="color: #000000; font-weight: bold;">&lt;?php</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$PHP_SELF</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>?view=all&quot;&gt;&lt;B&gt;Просмотр всех ип:
                    <span style="color: #000000; font-weight: bold;">&lt;?php</span>
                                    <span style="color: #000088;">$q</span><span style="color: #339933;">=</span><span style="color: #0000ff;">&quot;SELECT * FROM `all`&quot;</span><span style="color: #339933;">;</span>
                                    <span style="color: #000088;">$my_query</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">getn</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$q</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
                    <span style="color: #000000; font-weight: bold;">?&gt;</span>
            &lt;/A&gt;
    &lt;BR&gt;
    &nbsp;
            &lt;A HREF=&quot; <span style="color: #000000; font-weight: bold;">&lt;?php</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$PHP_SELF</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>?add=<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$my_query</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">max_id</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span><span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;B&gt;Добавить ип
            &lt;/A&gt;
    &lt;BR&gt;
    &nbsp;
            &lt;A HREF=&quot;save_bez.php?save=save&quot;&gt;&lt;B&gt;Сохранить настройки
            &lt;/A&gt;
    &lt;BR&gt;
            &lt;A HREF=&quot;save_bez.php?save=view&quot;&gt;&lt;B&gt;Просмотреть настройки
            &lt;/A&gt;
    &lt;BR&gt;
            &lt;A HREF=&quot; <span style="color: #000000; font-weight: bold;">&lt;?php</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$PHP_SELF</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>?view=freenibs&quot;&gt;Просмотреть Всех в базе FreeNibs
            &lt;/A&gt;
    &lt;BR&gt;
    &lt;BR&gt;
    &nbsp;
    &lt;BR&gt;
            &lt;A HREF=&quot;save_bez.php?save=gen&quot;&gt;&lt;B&gt;Генерировать настройки
            &lt;/A&gt;
    &nbsp;
    &lt;BR&gt;
            &lt;A HREF=&quot;<span style="color: #000000; font-weight: bold;">&lt;?php</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$PHP_SELF</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>?delete=all&quot;&gt;&lt;B&gt;Удалить ВСЕ!!! настройки
            &lt;/A&gt;&lt;BR&gt;&lt;BR&gt;
    <span style="color: #000000; font-weight: bold;">&lt;?php</span>
    &nbsp;
    <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$_GET</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;view&quot;</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">==</span><span style="color: #0000ff;">&quot;activ&quot;</span><span style="color: #009900;">&#41;</span>
    <span style="color: #009900;">&#123;</span>
    <span style="color: #000088;">$q</span><span style="color: #339933;">=</span><span style="color: #0000ff;">&quot;SELECT * FROM `all` WHERE activ='y' or activ='Y'&quot;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$my_query</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">setquery</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$q</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$my_query</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">my_print</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span>
    <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$_GET</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;view&quot;</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">==</span><span style="color: #0000ff;">&quot;deactiv&quot;</span><span style="color: #009900;">&#41;</span>
    <span style="color: #009900;">&#123;</span>
    <span style="color: #000088;">$q</span><span style="color: #339933;">=</span><span style="color: #0000ff;">&quot;SELECT * FROM `all` WHERE activ='n' or activ='N'&quot;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$my_query</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">setquery</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$q</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$my_query</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">my_print</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span>
    <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$_GET</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;view&quot;</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">==</span><span style="color: #0000ff;">&quot;all&quot;</span><span style="color: #009900;">&#41;</span>
    <span style="color: #009900;">&#123;</span>
    <span style="color: #000088;">$q</span><span style="color: #339933;">=</span><span style="color: #0000ff;">&quot;SELECT * FROM `all`&quot;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$my_query</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">setquery</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$q</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$my_query</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">my_print</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span>
    <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$_GET</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;add&quot;</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">&gt;</span><span style="color: #cc66cc;">0</span><span style="color: #009900;">&#41;</span>
    <span style="color: #009900;">&#123;</span>
     <span style="color: #000088;">$my_query</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">maxrule</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$ru</span><span style="color: #339933;">=</span><span style="color: #000088;">$my_query</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">maxrule</span><span style="color: #339933;">;</span>
    &nbsp;
     <span style="color: #000088;">$my_query</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">ad</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;192.168.0.1&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;<span style="color: #006699; font-weight: bold;">$ru</span>&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;0&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;0&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
     <span style="color: #009900;">&#125;</span>
    <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$_GET</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">&quot;view&quot;</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">==</span><span style="color: #0000ff;">&quot;freenibs&quot;</span><span style="color: #009900;">&#41;</span>
    <span style="color: #009900;">&#123;</span>
    <span style="color: #666666; font-style: italic;">//echo &quot;saassadsadsadsdasads&quot;;</span>
    &nbsp;
    <span style="color: #000088;">$my_query</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">view_freenibs</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span>
    <span style="color: #000000; font-weight: bold;">?&gt;</span>
    &lt;/table&gt;
    &nbsp;
    <span style="color: #000000; font-weight: bold;">&lt;?</span>
    <span style="color: #666666; font-style: italic;">//phpinfo();</span>
    <span style="color: #666666; font-style: italic;">//deactiv</span>
    &nbsp;
    <span style="color: #666666; font-style: italic;">//include_once(&quot;bottom.php&quot;);</span>
    &nbsp;
    &nbsp;
    <span style="color: #000000; font-weight: bold;">?&gt;</span></pre></td></tr></table><p class="theCode" style="display:none;">bezlim_index.php
    &lt;?php
    include_once(&quot;top.php&quot;);
    include_once(&quot;mysql.php&quot;);
    include_once(&quot;my_fill.php&quot;);
    $REF=$HTTP_REFERER;
    
    
    $my_query = new my_fill($LINK_BEZLIM);
    
    //if (($REF!=$PHP_SELF)&amp;&amp;strlen($REF)&gt;0)
    //echo &quot;||&lt;A HREF=\&quot;$REF\&quot; &gt;назад&lt;/A&gt;||&quot;;
    if ($_GET[&quot;delete&quot;]==&quot;all&quot;)
    {
    $my_query-&gt;deleteall();
    }
    ?&gt;
            &lt;A HREF=&quot; &lt;?php echo $PHP_SELF; ?&gt;?view=activ&quot;&gt;&lt;B&gt;Просмотр незанятых ип:
                    &lt;?php
                            $q=&quot;SELECT * FROM `all` WHERE activ='y' or activ='Y'&quot;;
                            $my_query-&gt;getn($q);
                    ?&gt;
            &lt;/A&gt;
    &lt;BR&gt;
            &lt;A HREF=&quot; &lt;?php echo $PHP_SELF; ?&gt;?view=deactiv&quot;&gt;&lt;B&gt;Просмотр отключенных ип:
                    &lt;?php
                            $q=&quot;SELECT * FROM `all` WHERE activ='N' or activ='n'&quot;;
                            $my_query-&gt;getn($q);
                    ?&gt;
            &lt;/A&gt;
    &lt;BR&gt;
    
            &lt;A HREF=&quot; &lt;?php echo $PHP_SELF; ?&gt;?view=all&quot;&gt;&lt;B&gt;Просмотр всех ип:
                    &lt;?php
                                    $q=&quot;SELECT * FROM `all`&quot;;
                                    $my_query-&gt;getn($q);
                    ?&gt;
            &lt;/A&gt;
    &lt;BR&gt;
    
            &lt;A HREF=&quot; &lt;?php echo $PHP_SELF; ?&gt;?add=&lt;? echo $my_query-&gt;max_id();?&gt;&quot;&gt;&lt;B&gt;Добавить ип
            &lt;/A&gt;
    &lt;BR&gt;
    
            &lt;A HREF=&quot;save_bez.php?save=save&quot;&gt;&lt;B&gt;Сохранить настройки
            &lt;/A&gt;
    &lt;BR&gt;
            &lt;A HREF=&quot;save_bez.php?save=view&quot;&gt;&lt;B&gt;Просмотреть настройки
            &lt;/A&gt;
    &lt;BR&gt;
            &lt;A HREF=&quot; &lt;?php echo $PHP_SELF; ?&gt;?view=freenibs&quot;&gt;Просмотреть Всех в базе FreeNibs
            &lt;/A&gt;
    &lt;BR&gt;
    &lt;BR&gt;
    
    &lt;BR&gt;
            &lt;A HREF=&quot;save_bez.php?save=gen&quot;&gt;&lt;B&gt;Генерировать настройки
            &lt;/A&gt;
    
    &lt;BR&gt;
            &lt;A HREF=&quot;&lt;?php echo $PHP_SELF; ?&gt;?delete=all&quot;&gt;&lt;B&gt;Удалить ВСЕ!!! настройки
            &lt;/A&gt;&lt;BR&gt;&lt;BR&gt;
    &lt;?php
    
    if ($_GET[&quot;view&quot;]==&quot;activ&quot;)
    {
    $q=&quot;SELECT * FROM `all` WHERE activ='y' or activ='Y'&quot;;
    $my_query-&gt;setquery($q);
    $my_query-&gt;my_print();
    }
    if ($_GET[&quot;view&quot;]==&quot;deactiv&quot;)
    {
    $q=&quot;SELECT * FROM `all` WHERE activ='n' or activ='N'&quot;;
    $my_query-&gt;setquery($q);
    $my_query-&gt;my_print();
    }
    if ($_GET[&quot;view&quot;]==&quot;all&quot;)
    {
    $q=&quot;SELECT * FROM `all`&quot;;
    $my_query-&gt;setquery($q);
    $my_query-&gt;my_print();
    }
    if ($_GET[&quot;add&quot;]&gt;0)
    {
     $my_query-&gt;maxrule();
    $ru=$my_query-&gt;maxrule;
    
     $my_query-&gt;ad(&quot;192.168.0.1&quot;,&quot;$ru&quot;,&quot;0&quot;,&quot;0&quot;);
     }
    if ($_GET[&quot;view&quot;]==&quot;freenibs&quot;)
    {
    //echo &quot;saassadsadsadsdasads&quot;;
    
    $my_query-&gt;view_freenibs();
    }
    ?&gt;
    &lt;/table&gt;
    
    &lt;?
    //phpinfo();
    //deactiv
    
    //include_once(&quot;bottom.php&quot;);
    
    
    ?&gt;</p></div>
    ";}
categories:
  - billing
  - FreeNIBS
tags:
  - bezlim_index.php

---
Работа с безлимитом<!--more-->

<pre lang="php">bezlim_index.php
<?php
include_once("top.php");
include_once("mysql.php");
include_once("my_fill.php");
$REF=$HTTP_REFERER;


$my_query = new my_fill($LINK_BEZLIM);

//if (($REF!=$PHP_SELF)&#038;&#038;strlen($REF)>0)
//echo "||<A HREF=\"$REF\" >назад</A>||";
if ($_GET["delete"]=="all")
{
$my_query->deleteall();
}
?>
        

<A HREF=" <?php echo $PHP_SELF; ?>?view=activ"><B>Просмотр незанятых ип:
                <?php
                        $q="SELECT * FROM `all` WHERE activ='y' or activ='Y'";
                        $my_query->getn($q);
                ?>
        </A>


<BR />
        <A HREF=" <?php echo $PHP_SELF; ?>?view=deactiv"><B>Просмотр отключенных ип:
                <?php
                        $q="SELECT * FROM `all` WHERE activ='N' or activ='n'";
                        $my_query->getn($q);
                ?>
        </A>


<BR />

        <A HREF=" <?php echo $PHP_SELF; ?>?view=all"><B>Просмотр всех ип:
                <?php
                                $q="SELECT * FROM `all`";
                                $my_query->getn($q);
                ?>
        </A>


<BR />

        <A HREF=" <?php echo $PHP_SELF; ?>?add=<? echo $my_query->max_id();?>"><B>Добавить ип
        </A>
<BR />

        <A HREF="save_bez.php?save=save"><B>Сохранить настройки
        </A>
<BR />
        <A HREF="save_bez.php?save=view"><B>Просмотреть настройки
        </A>
<BR />
        <A HREF=" <?php echo $PHP_SELF; ?>?view=freenibs">Просмотреть Всех в базе FreeNibs
        </A>
<BR />
<BR />

<BR />
        <A HREF="save_bez.php?save=gen"><B>Генерировать настройки
        </A>

<BR />
        <A HREF="<?php echo $PHP_SELF; ?>?delete=all"><B>Удалить ВСЕ!!! настройки
        </A><BR /><BR />
<?php

if ($_GET["view"]=="activ")
{
$q="SELECT * FROM `all` WHERE activ='y' or activ='Y'";
$my_query->setquery($q);
$my_query->my_print();
}
if ($_GET["view"]=="deactiv")
{
$q="SELECT * FROM `all` WHERE activ='n' or activ='N'";
$my_query->setquery($q);
$my_query->my_print();
}
if ($_GET["view"]=="all")
{
$q="SELECT * FROM `all`";
$my_query->setquery($q);
$my_query->my_print();
}
if ($_GET["add"]>0)
{
 $my_query->maxrule();
$ru=$my_query->maxrule;

 $my_query->ad("192.168.0.1","$ru","0","0");
 }
if ($_GET["view"]=="freenibs")
{
//echo "saassadsadsadsdasads";

$my_query->view_freenibs();
}
?>
</table>



<?
//phpinfo();
//deactiv

//include_once("bottom.php");


?>

</pre>