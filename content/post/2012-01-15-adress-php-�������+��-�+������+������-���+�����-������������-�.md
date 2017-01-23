---
title: adress.php Скрипт просмотра списка адрессов для ФрииНИБСа
author: wel
type: post
date: 2012-01-14T22:04:04+00:00
url: /billing/adress-php-скрипт-просмотра-списка-адрессов-д
wp-syntax-cache-content:
  - |
    a:1:{i:1;s:8529:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="php" style="font-family:monospace;">&nbsp;
    <span style="color: #000000; font-weight: bold;">&lt;?php</span>
    <span style="color: #b1b100;">include_once</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;top.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">include_once</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;engine.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    &nbsp;
    &nbsp;
    <span style="color: #000088;">$ip</span><span style="color: #339933;">=</span><span style="color: #000088;">$_GET</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'ip'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #666666; font-style: italic;">//$status=$argv[2];</span>
    <span style="color: #000088;">$db</span><span style="color: #339933;">=</span><span style="color: #000000; font-weight: bold;">new</span> db_mysql<span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$db</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">init</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;localhost&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;freenibs&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;freenibs,&quot;</span>freenibs<span style="color: #0000ff;">&quot;);
    &nbsp;
    /*<span style="color: #006699; font-weight: bold;">$q</span>=&quot;</span>SELECT `street`<span style="color: #339933;">,</span>`house` FROM `users`<span style="color: #0000ff;">&quot;;
    &nbsp;
    INSERT INTO `adress`.`street`,`adress`.`house`
    SELECT `users`.`street`,`users`.`house` FROM users u
    ON DUPLICATE KEY UPDATE `street`=u.street
    /*
    /*INSERT INTO product_offers (`id_product`, `price`)
    SLECT `id_product`, `new_price`
    FROM temp_table t
    WHERE `id_product` IS NOT NULL
    ON DUPLICATE KEY UPDATE `old_price`=`price`, `price`=t.`new_price`
    */
    <span style="color: #006699; font-weight: bold;">$q</span>=&quot;</span>DELETE FROM `adress`<span style="color: #0000ff;">&quot;;
    <span style="color: #006699; font-weight: bold;">$db-&gt;query</span>(<span style="color: #006699; font-weight: bold;">$q</span>);
    &nbsp;
    &nbsp;
    <span style="color: #006699; font-weight: bold;">$q</span>=&quot;</span>INSERT INTO `adress`<span style="color: #009900;">&#40;</span>`street`<span style="color: #339933;">,</span>`house`<span style="color: #009900;">&#41;</span>
    SELECT `users`<span style="color: #339933;">.</span>`street`<span style="color: #339933;">,</span>`users`<span style="color: #339933;">.</span>`house` FROM `users`
    ON DUPLICATE <span style="color: #990000;">KEY</span> UPDATE `adress`<span style="color: #339933;">.</span>`street`<span style="color: #339933;">=</span>`users`<span style="color: #339933;">.</span>`street`
    <span style="color: #0000ff;">&quot;;
    <span style="color: #006699; font-weight: bold;">$db-&gt;query</span>(<span style="color: #006699; font-weight: bold;">$q</span>);
    &nbsp;
    <span style="color: #006699; font-weight: bold;">$q</span>=&quot;</span>SELECT `street`<span style="color: #339933;">,</span>`house` FROM `adress` WHERE `street` not Like <span style="color: #0000ff;">''</span> AND `house` not Like <span style="color: #0000ff;">''</span><span style="color: #0000ff;">&quot;;
    <span style="color: #006699; font-weight: bold;">$db-&gt;query</span>(<span style="color: #006699; font-weight: bold;">$q</span>);
    &nbsp;
    <span style="color: #006699; font-weight: bold;">$n</span>=<span style="color: #006699; font-weight: bold;">$db-&gt;num_rows</span>();
    if(<span style="color: #006699; font-weight: bold;">$n</span>&gt;0)
    {
    <span style="color: #006699; font-weight: bold;">$n</span>++;
    echo &quot;</span><span style="color: #339933;">&lt;</span>TABLE border<span style="color: #339933;">=</span><span style="color: #0000ff;">'1'</span><span style="color: #339933;">&gt;</span>
        <span style="color: #339933;">&lt;</span>TR<span style="color: #339933;">&gt;&lt;</span>TD<span style="color: #339933;">&gt;&lt;/</span>TD<span style="color: #339933;">&gt;&lt;</span>TD<span style="color: #339933;">&gt;&lt;</span>B<span style="color: #339933;">&gt;</span>Улица<span style="color: #339933;">&lt;/</span>B<span style="color: #339933;">&gt;&lt;/</span>TD<span style="color: #339933;">&gt;&lt;</span>TD<span style="color: #339933;">&gt;&lt;</span>B<span style="color: #339933;">&gt;</span>Номер дома<span style="color: #339933;">&lt;/</span>B<span style="color: #339933;">&gt;&lt;/</span>TD<span style="color: #339933;">&gt;&lt;/</span>TR<span style="color: #339933;">&gt;</span><span style="color: #0000ff;">&quot;;
        for(<span style="color: #006699; font-weight: bold;">$i</span>=1;<span style="color: #006699; font-weight: bold;">$i</span>&lt;<span style="color: #006699; font-weight: bold;">$n</span>;<span style="color: #006699; font-weight: bold;">$i</span>++)
            {
            <span style="color: #006699; font-weight: bold;">$row</span>=<span style="color: #006699; font-weight: bold;">$db-&gt;fetch_array</span>();
                echo &quot;</span><span style="color: #339933;">&lt;</span>TR<span style="color: #339933;">&gt;&lt;</span>TD<span style="color: #339933;">&gt;</span><span style="color: #0000ff;">&quot;.<span style="color: #006699; font-weight: bold;">$i</span>.&quot;</span><span style="color: #339933;">&lt;/</span>td<span style="color: #339933;">&gt;&lt;</span>TD<span style="color: #339933;">&gt;</span><span style="color: #0000ff;">&quot;.<span style="color: #006699; font-weight: bold;">$row</span>['street'].&quot;</span><span style="color: #339933;">&lt;/</span>TD<span style="color: #339933;">&gt;&lt;</span>TD<span style="color: #339933;">&gt;</span><span style="color: #0000ff;">&quot;.<span style="color: #006699; font-weight: bold;">$row</span>['house'].&quot;</span><span style="color: #339933;">&lt;/</span>TD<span style="color: #339933;">&gt;&lt;/</span>TR<span style="color: #339933;">&gt;</span>\n<span style="color: #0000ff;">&quot;;
    &nbsp;
            }
    echo &quot;</span><span style="color: #339933;">&lt;/</span>TABLE<span style="color: #339933;">&gt;</span><span style="color: #0000ff;">&quot;;
    &nbsp;
    }
    &nbsp;
    @<span style="color: #006699; font-weight: bold;">$db-&gt;close_db</span>();
    include_once(&quot;</span>bottom<span style="color: #339933;">.</span>php<span style="color: #0000ff;">&quot;);
    ?&gt;</span></pre></td></tr></table><p class="theCode" style="display:none;">
    &lt;?php
    include_once(&quot;top.php&quot;);
    include_once(&quot;engine.php&quot;);
    
    
    
    $ip=$_GET['ip'];
    
    //$status=$argv[2];
    $db=new db_mysql();
    $db-&gt;init(&quot;localhost&quot;,&quot;freenibs&quot;,&quot;freenibs,&quot;freenibs&quot;);
    
    /*$q=&quot;SELECT `street`,`house` FROM `users`&quot;;
    
    INSERT INTO `adress`.`street`,`adress`.`house`
    SELECT `users`.`street`,`users`.`house` FROM users u
    ON DUPLICATE KEY UPDATE `street`=u.street
    /*
    /*INSERT INTO product_offers (`id_product`, `price`)
    SLECT `id_product`, `new_price`
    FROM temp_table t
    WHERE `id_product` IS NOT NULL
    ON DUPLICATE KEY UPDATE `old_price`=`price`, `price`=t.`new_price`
    */
    $q=&quot;DELETE FROM `adress`&quot;;
    $db-&gt;query($q);
    
    
    $q=&quot;INSERT INTO `adress`(`street`,`house`)
    SELECT `users`.`street`,`users`.`house` FROM `users`
    ON DUPLICATE KEY UPDATE `adress`.`street`=`users`.`street`
    &quot;;
    $db-&gt;query($q);
    
    $q=&quot;SELECT `street`,`house` FROM `adress` WHERE `street` not Like '' AND `house` not Like ''&quot;;
    $db-&gt;query($q);
    
    $n=$db-&gt;num_rows();
    if($n&gt;0)
    {
    $n++;
    echo &quot;&lt;TABLE border='1'&gt;
        &lt;TR&gt;&lt;TD&gt;&lt;/TD&gt;&lt;TD&gt;&lt;B&gt;Улица&lt;/B&gt;&lt;/TD&gt;&lt;TD&gt;&lt;B&gt;Номер дома&lt;/B&gt;&lt;/TD&gt;&lt;/TR&gt;&quot;;
        for($i=1;$i&lt;$n;$i++)
            {
            $row=$db-&gt;fetch_array();
                echo &quot;&lt;TR&gt;&lt;TD&gt;&quot;.$i.&quot;&lt;/td&gt;&lt;TD&gt;&quot;.$row['street'].&quot;&lt;/TD&gt;&lt;TD&gt;&quot;.$row['house'].&quot;&lt;/TD&gt;&lt;/TR&gt;\n&quot;;
    
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
  - adress.php

---
Скрипт просмотра списка адрессов для ФрииНИБСа<!--more-->

<pre lang="php"><?php
include_once("top.php");
include_once("engine.php");



$ip=$_GET['ip'];

//$status=$argv[2];
$db=new db_mysql();
$db->init("localhost","freenibs","freenibs,"freenibs");

/*$q="SELECT `street`,`house` FROM `users`";

INSERT INTO `adress`.`street`,`adress`.`house`
SELECT `users`.`street`,`users`.`house` FROM users u
ON DUPLICATE KEY UPDATE `street`=u.street
/*
/*INSERT INTO product_offers (`id_product`, `price`)
SLECT `id_product`, `new_price`
FROM temp_table t
WHERE `id_product` IS NOT NULL
ON DUPLICATE KEY UPDATE `old_price`=`price`, `price`=t.`new_price`
*/
$q="DELETE FROM `adress`";
$db->query($q);


$q="INSERT INTO `adress`(`street`,`house`)
SELECT `users`.`street`,`users`.`house` FROM `users`
ON DUPLICATE KEY UPDATE `adress`.`street`=`users`.`street`
";
$db->query($q);

$q="SELECT `street`,`house` FROM `adress` WHERE `street` not Like '' AND `house` not Like ''";
$db->query($q);

$n=$db->num_rows();
if($n>0)
{
$n++;
echo "

<TABLE border='1'>
  <TR>
    <TD>
      
    </TD>
    
    <TD>
      <B>Улица</B>
    </TD>
    
    <TD>
      <B>Номер дома</B>
    </TD>
  </TR>";
      for($i=1;$i&lt;$n;$i++)
          {
          $row=$db->fetch_array();
              echo "
  
  <TR>
    <TD>
      ".$i."
    </td>
    
    <TD>
      ".$row['street']."
    </TD>
    
    <TD>
      ".$row['house']."
    </TD>
  </TR>\n";
  
          }
  echo "
</TABLE>";

}

@$db->close_db();
include_once("bottom.php");
?>

</pre>