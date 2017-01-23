---
title: credit_of_user.php —Кредиты пользователей
author: wel
type: post
date: 2012-01-14T23:36:42+00:00
url: /billing/credit_of_user-php-кредиты-пользователей
wp-syntax-cache-content:
  - |
    a:1:{i:1;s:26526:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="php" style="font-family:monospace;">&nbsp;
    &nbsp;
    <span style="color: #000000; font-weight: bold;">&lt;?</span>
    <span style="color: #000088;">$TOP</span> <span style="color: #339933;">=</span> <span style="color: #0000ff;">&quot; Кредиты пользователей &quot;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$META</span> <span style="color: #339933;">=</span> <span style="color: #0000ff;">&quot;&lt;META HTTP-EQUIV=<span style="color: #000099; font-weight: bold;">\&quot;</span>Cache-Control<span style="color: #000099; font-weight: bold;">\&quot;</span> CONTENT=<span style="color: #000099; font-weight: bold;">\&quot;</span>no-cache<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;<span style="color: #000099; font-weight: bold;">\n</span>&lt;META HTTP-EQUIV=<span style="color: #000099; font-weight: bold;">\&quot;</span>Pragma<span style="color: #000099; font-weight: bold;">\&quot;</span> CONTENT=<span style="color: #000099; font-weight: bold;">\&quot;</span>no-cache<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;&quot;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #b1b100;">include</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;top.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">include</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;class.loggin.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$log</span> <span style="color: #339933;">=</span> <span style="color: #000000; font-weight: bold;">new</span> Logging<span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$log</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">setfile</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;credit_of_user.php.log.html&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;a href='credit_of_user.php.log.html'&gt;Данные по операциям&lt;/a&gt;&quot;</span><span style="color: #339933;">;</span>
    <span style="color: #000000; font-weight: bold;">?&gt;</span>
    &lt;CENTER&gt;
    &nbsp;
    <span style="color: #000000; font-weight: bold;">&lt;?php</span>
    <span style="color: #000000; font-weight: bold;">function</span> quote_smart<span style="color: #009900;">&#40;</span><span style="color: #000088;">$value</span><span style="color: #009900;">&#41;</span>
    <span style="color: #009900;">&#123;</span>
        <span style="color: #666666; font-style: italic;">// если magic_quotes_gpc включена - используем stripslashes</span>
        <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #990000;">get_magic_quotes_gpc</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
            <span style="color: #000088;">$value</span> <span style="color: #339933;">=</span> <span style="color: #990000;">stripslashes</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$value</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
        <span style="color: #009900;">&#125;</span>
        <span style="color: #666666; font-style: italic;">// Если переменная - число, то экранировать её не нужно</span>
        <span style="color: #666666; font-style: italic;">// если нет - то окружем её кавычками, и экранируем</span>
        <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #339933;">!</span><span style="color: #990000;">is_numeric</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$value</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
            <span style="color: #000088;">$value</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_real_escape_string</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$value</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
        <span style="color: #009900;">&#125;</span>
        <span style="color: #b1b100;">return</span> <span style="color: #000088;">$value</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span>
    &nbsp;
    &nbsp;
    <span style="color: #666666; font-style: italic;">/* коннект к БД - меняем на свое */</span>
    <span style="color: #000088;">$link</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_connect</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">'10.200.205.224'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'freenibs'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'freenibs'</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #339933;">!</span><span style="color: #000088;">$link</span><span style="color: #009900;">&#41;</span> <span style="color: #009900;">&#123;</span>
        <span style="color: #990000;">die</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">'Could not connect: '</span> <span style="color: #339933;">.</span> <span style="color: #990000;">mysql_error</span><span style="color: #009900;">&#40;</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span>
    &nbsp;
    <span style="color: #990000;">mysql_select_db</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;freenibs&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #666666; font-style: italic;">// Выбираем дни за которые показывать Трафло</span>
    <span style="color: #000088;">$card_id</span><span style="color: #339933;">=</span><span style="color: #000088;">$_GET</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'id'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">if</span><span style="color: #009900;">&#40;</span><span style="color: #990000;">strlen</span><span style="color: #009900;">&#40;</span><span style="color: #990000;">trim</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$_GET</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'act'</span><span style="color: #009900;">&#93;</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">&gt;</span><span style="color: #cc66cc;">0</span><span style="color: #009900;">&#41;</span>
        <span style="color: #000088;">$act</span><span style="color: #339933;">=</span><span style="color: #000088;">$_GET</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'act'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">else</span>
         <span style="color: #000088;">$act</span><span style="color: #339933;">=</span><span style="color: #000088;">$_POST</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'act'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">switch</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$act</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#123;</span>
       <span style="color: #666666; font-style: italic;">/* case &quot;delete&quot;:
                if($card_id&gt;0){
                    $q=&quot;DELETE FROM  `privat24` WHERE `id`=&quot;.quote_smart($card_id).&quot; LIMIT 1&quot;;
                    //echo $q;
                    $log-&gt;lwrite('Удалена карта # '.$card_id.' user:'.$_GET['user'].' serial:'.$_GET['card'].&quot; &lt;br&gt;\n&quot;);
    &nbsp;
                    mysql_query($q);
                }
                break;
        */</span>
        <span style="color: #b1b100;">case</span> <span style="color: #0000ff;">&quot;update&quot;</span><span style="color: #339933;">:</span>
                 <span style="color: #b1b100;">if</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$_POST</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'uid'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">&gt;</span><span style="color: #cc66cc;">0</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#123;</span>
                      <span style="color: #000088;">$q</span><span style="color: #339933;">=</span><span style="color: #0000ff;">&quot;UPDATE `users` SET `credit`='&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$_POST</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'credit'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;' WHERE `uid`=&quot;</span><span style="color: #339933;">.</span>quote_smart<span style="color: #009900;">&#40;</span><span style="color: #000088;">$_POST</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'uid'</span><span style="color: #009900;">&#93;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot; LIMIT 1&quot;</span><span style="color: #339933;">;</span>
                      <span style="color: #000088;">$log</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">lwrite</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">'обновление кредита пользователю: &lt;a target=&quot;_open&quot; href=&quot;edit_user.php?uid='</span><span style="color: #339933;">.</span><span style="color: #000088;">$_POST</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'uid'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">'&quot;&gt;'</span><span style="color: #339933;">.</span><span style="color: #000088;">$_POST</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'user'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">'['</span><span style="color: #339933;">.</span><span style="color: #000088;">$_POST</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'uid'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">'] '</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;&lt;/a&gt;&lt;br&gt;<span style="color: #000099; font-weight: bold;">\n</span>&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
                       <span style="color: #990000;">mysql_query</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$q</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
                 <span style="color: #009900;">&#125;</span>
                 <span style="color: #b1b100;">break</span><span style="color: #339933;">;</span>
    &nbsp;
        <span style="color: #b1b100;">case</span> <span style="color: #0000ff;">&quot;updateall&quot;</span><span style="color: #339933;">:</span>
                     <span style="color: #b1b100;">if</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$_POST</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'uid'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">&gt;</span><span style="color: #cc66cc;">0</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#123;</span>
                        <span style="color: #000088;">$q</span><span style="color: #339933;">=</span><span style="color: #0000ff;">&quot;UPDATE `users` SET `credit`='0.00' &quot;</span><span style="color: #339933;">;</span>
                        <span style="color: #000088;">$log</span><span style="color: #339933;">-&gt;</span><span style="color: #004000;">lwrite</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">'обновление кредита всех пользователей'</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;&lt;/a&gt;&lt;br&gt;<span style="color: #000099; font-weight: bold;">\n</span>&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
                       <span style="color: #990000;">mysql_query</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$q</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
                      <span style="color: #009900;">&#125;</span>
    &nbsp;
                 <span style="color: #b1b100;">break</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #009900;">&#125;</span>
    <span style="color: #000088;">$q</span><span style="color: #339933;">=</span><span style="color: #0000ff;">&quot;SELECT * FROM `users` WHERE `credit`&gt;'0.01' OR `credit`&lt;'-0.01' ORDER BY `credit`  DESC &quot;</span><span style="color: #339933;">;</span>
    &nbsp;
      <span style="color: #000088;">$result</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_query</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$q</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
      <span style="color: #666666; font-style: italic;">//$days=array();</span>
      <span style="color: #000088;">$i</span><span style="color: #339933;">=</span><span style="color: #cc66cc;">0</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;table border='1'&gt;
             &lt;td&gt;N&lt;/td&gt;&lt;td&gt;user&lt;/td&gt;&lt;td&gt;credit&lt;/td&gt;&lt;td&gt;deposit&lt;/td&gt;&lt;td&gt;Установить кредит&lt;/td&gt;&quot;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #b1b100;">while</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$row</span> <span style="color: #339933;">=</span> <span style="color: #990000;">mysql_fetch_array</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$result</span><span style="color: #339933;">,</span> MYSQL_ASSOC<span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#123;</span>
        <span style="color: #000088;">$i</span><span style="color: #339933;">++;</span>
        <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot; &lt;tr&gt;
                    &lt;td&gt;<span style="color: #006699; font-weight: bold;">$i</span>&lt;/td&gt;&lt;td&gt;&lt;a target=<span style="color: #000099; font-weight: bold;">\&quot;</span>_open<span style="color: #000099; font-weight: bold;">\&quot;</span> href=<span style="color: #000099; font-weight: bold;">\&quot;</span>edit_user.php?uid=&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'uid'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt; &quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'user'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;&lt;/a&gt;&lt;/td&gt;
                    &lt;td&gt;&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'credit'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;&lt;/td&gt;
                    &lt;td&gt;&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'deposit'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;&lt;/td&gt;
                    &lt;td&gt;&lt;form action=<span style="color: #000099; font-weight: bold;">\&quot;</span>credit_of_user.php<span style="color: #000099; font-weight: bold;">\&quot;</span> method=<span style="color: #000099; font-weight: bold;">\&quot;</span>post<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;
                            &lt;input type=<span style="color: #000099; font-weight: bold;">\&quot;</span>hidden<span style="color: #000099; font-weight: bold;">\&quot;</span> name=<span style="color: #000099; font-weight: bold;">\&quot;</span>uid<span style="color: #000099; font-weight: bold;">\&quot;</span> value=<span style="color: #000099; font-weight: bold;">\&quot;</span>&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'uid'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;
                            &lt;input type=<span style="color: #000099; font-weight: bold;">\&quot;</span>hidden<span style="color: #000099; font-weight: bold;">\&quot;</span> name=<span style="color: #000099; font-weight: bold;">\&quot;</span>user<span style="color: #000099; font-weight: bold;">\&quot;</span> value=<span style="color: #000099; font-weight: bold;">\&quot;</span>&quot;</span><span style="color: #339933;">.</span><span style="color: #000088;">$row</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'user'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;
                            &lt;input type=<span style="color: #000099; font-weight: bold;">\&quot;</span>text<span style="color: #000099; font-weight: bold;">\&quot;</span> name=<span style="color: #000099; font-weight: bold;">\&quot;</span>credit<span style="color: #000099; font-weight: bold;">\&quot;</span>  size=<span style="color: #000099; font-weight: bold;">\&quot;</span>4<span style="color: #000099; font-weight: bold;">\&quot;</span> value=<span style="color: #000099; font-weight: bold;">\&quot;</span>0.00<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;
                            &lt;input type=<span style="color: #000099; font-weight: bold;">\&quot;</span>hidden<span style="color: #000099; font-weight: bold;">\&quot;</span> name=<span style="color: #000099; font-weight: bold;">\&quot;</span>act<span style="color: #000099; font-weight: bold;">\&quot;</span> value=<span style="color: #000099; font-weight: bold;">\&quot;</span>update<span style="color: #000099; font-weight: bold;">\&quot;</span> &gt;
                            &lt;input type=<span style="color: #000099; font-weight: bold;">\&quot;</span>submit<span style="color: #000099; font-weight: bold;">\&quot;</span> value=<span style="color: #000099; font-weight: bold;">\&quot;</span>установить кредит<span style="color: #000099; font-weight: bold;">\&quot;</span>&gt;
                        &lt;/form&gt;
                    &lt;/td&gt;
    &nbsp;
               &lt;/tr&gt; &quot;</span><span style="color: #339933;">;</span>
    <span style="color: #009900;">&#125;</span>
    <span style="color: #b1b100;">echo</span> <span style="color: #0000ff;">&quot;&lt;/table&gt;&quot;</span><span style="color: #339933;">;</span>
    <span style="color: #990000;">mysql_close</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$link</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000000; font-weight: bold;">?&gt;</span>
    &nbsp;
    <span style="color: #000000; font-weight: bold;">&lt;?</span>
    &nbsp;
    <span style="color: #000000; font-weight: bold;">?&gt;</span>
    &lt;/CENTER&gt;
    <span style="color: #000000; font-weight: bold;">&lt;?</span>
    <span style="color: #b1b100;">include</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;bottom.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000000; font-weight: bold;">?&gt;</span></pre></td></tr></table><p class="theCode" style="display:none;">
    
    &lt;?
    $TOP = &quot; Кредиты пользователей &quot;;
    $META = &quot;&lt;META HTTP-EQUIV=\&quot;Cache-Control\&quot; CONTENT=\&quot;no-cache\&quot;&gt;\n&lt;META HTTP-EQUIV=\&quot;Pragma\&quot; CONTENT=\&quot;no-cache\&quot;&gt;&quot;;
    
    include(&quot;top.php&quot;);
    include(&quot;class.loggin.php&quot;);
    $log = new Logging();
    $log-&gt;setfile(&quot;credit_of_user.php.log.html&quot;);
    echo &quot;&lt;a href='credit_of_user.php.log.html'&gt;Данные по операциям&lt;/a&gt;&quot;;
    ?&gt;
    &lt;CENTER&gt;
    
    &lt;?php
    function quote_smart($value)
    {
        // если magic_quotes_gpc включена - используем stripslashes
        if (get_magic_quotes_gpc()) {
            $value = stripslashes($value);
        }
        // Если переменная - число, то экранировать её не нужно
        // если нет - то окружем её кавычками, и экранируем
        if (!is_numeric($value)) {
            $value = mysql_real_escape_string($value);
        }
        return $value;
    }
    
    
    /* коннект к БД - меняем на свое */
    $link = mysql_connect('10.200.205.224', 'freenibs', 'freenibs');
    if (!$link) {
        die('Could not connect: ' . mysql_error());
    }
    
    mysql_select_db(&quot;freenibs&quot;);
    // Выбираем дни за которые показывать Трафло
    $card_id=$_GET['id'];
    if(strlen(trim($_GET['act']))&gt;0)
        $act=$_GET['act'];
    else
         $act=$_POST['act'];
    switch($act){
       /* case &quot;delete&quot;:
                if($card_id&gt;0){
                    $q=&quot;DELETE FROM  `privat24` WHERE `id`=&quot;.quote_smart($card_id).&quot; LIMIT 1&quot;;
                    //echo $q;
                    $log-&gt;lwrite('Удалена карта # '.$card_id.' user:'.$_GET['user'].' serial:'.$_GET['card'].&quot; &lt;br&gt;\n&quot;);
    
                    mysql_query($q);
                }
                break;
        */
        case &quot;update&quot;:
                 if($_POST['uid']&gt;0){
                      $q=&quot;UPDATE `users` SET `credit`='&quot;.$_POST['credit'].&quot;' WHERE `uid`=&quot;.quote_smart($_POST['uid']).&quot; LIMIT 1&quot;;
                      $log-&gt;lwrite('обновление кредита пользователю: &lt;a target=&quot;_open&quot; href=&quot;edit_user.php?uid='.$_POST['uid'].'&quot;&gt;'.$_POST['user'].'['.$_POST['uid'].'] '.&quot;&lt;/a&gt;&lt;br&gt;\n&quot;);
                       mysql_query($q);
                 }
                 break;
    
        case &quot;updateall&quot;:
                     if($_POST['uid']&gt;0){
                        $q=&quot;UPDATE `users` SET `credit`='0.00' &quot;;
                        $log-&gt;lwrite('обновление кредита всех пользователей'.&quot;&lt;/a&gt;&lt;br&gt;\n&quot;);
                       mysql_query($q);
                      }
    
                 break;
    
    }
    $q=&quot;SELECT * FROM `users` WHERE `credit`&gt;'0.01' OR `credit`&lt;'-0.01' ORDER BY `credit`  DESC &quot;;
    
      $result = mysql_query($q);
      //$days=array();
      $i=0;
    echo &quot;&lt;table border='1'&gt;
             &lt;td&gt;N&lt;/td&gt;&lt;td&gt;user&lt;/td&gt;&lt;td&gt;credit&lt;/td&gt;&lt;td&gt;deposit&lt;/td&gt;&lt;td&gt;Установить кредит&lt;/td&gt;&quot;;
    
    while($row = mysql_fetch_array($result, MYSQL_ASSOC)){
        $i++;
        echo &quot; &lt;tr&gt;
                    &lt;td&gt;$i&lt;/td&gt;&lt;td&gt;&lt;a target=\&quot;_open\&quot; href=\&quot;edit_user.php?uid=&quot;.$row['uid'].&quot;\&quot;&gt; &quot;.$row['user'].&quot;&lt;/a&gt;&lt;/td&gt;
                    &lt;td&gt;&quot;.$row['credit'].&quot;&lt;/td&gt;
                    &lt;td&gt;&quot;.$row['deposit'].&quot;&lt;/td&gt;
                    &lt;td&gt;&lt;form action=\&quot;credit_of_user.php\&quot; method=\&quot;post\&quot;&gt;
                            &lt;input type=\&quot;hidden\&quot; name=\&quot;uid\&quot; value=\&quot;&quot;.$row['uid'].&quot;\&quot;&gt;
                            &lt;input type=\&quot;hidden\&quot; name=\&quot;user\&quot; value=\&quot;&quot;.$row['user'].&quot;\&quot;&gt;
                            &lt;input type=\&quot;text\&quot; name=\&quot;credit\&quot;  size=\&quot;4\&quot; value=\&quot;0.00\&quot;&gt;
                            &lt;input type=\&quot;hidden\&quot; name=\&quot;act\&quot; value=\&quot;update\&quot; &gt;
                            &lt;input type=\&quot;submit\&quot; value=\&quot;установить кредит\&quot;&gt;
                        &lt;/form&gt;
                    &lt;/td&gt;
    
               &lt;/tr&gt; &quot;;
    }
    echo &quot;&lt;/table&gt;&quot;;
    mysql_close($link);
    ?&gt;
    
    &lt;?
    
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
  - credit_of_user.php

---
credit\_of\_user.php —Кредиты пользователей <!--more-->

<pre lang="php"><?
$TOP = " Кредиты пользователей ";
$META = "<META HTTP-EQUIV=\"Cache-Control\" CONTENT=\"no-cache\">\n&lt;META HTTP-EQUIV=\"Pragma\" CONTENT=\"no-cache\">";

include("top.php");
include("class.loggin.php");
$log = new Logging();
$log->setfile("credit_of_user.php.log.html");
echo "

<a href='credit_of_user.php.log.html'>Данные по операциям</a>";
?>


<CENTER>
  <?php
function quote_smart($value)
{
    // если magic_quotes_gpc включена - используем stripslashes
    if (get_magic_quotes_gpc()) {
        $value = stripslashes($value);
    }
    // Если переменная - число, то экранировать её не нужно
    // если нет - то окружем её кавычками, и экранируем
    if (!is_numeric($value)) {
        $value = mysql_real_escape_string($value);
    }
    return $value;
}


/* коннект к БД - меняем на свое */
$link = mysql_connect('10.200.205.224', 'freenibs', 'freenibs');
if (!$link) {
    die('Could not connect: ' . mysql_error());
}

mysql_select_db("freenibs");
// Выбираем дни за которые показывать Трафло
$card_id=$_GET['id'];
if(strlen(trim($_GET['act']))>0)
      $act=$_GET['act'];
  else
       $act=$_POST['act'];
  switch($act){
     /* case "delete":
              if($card_id>0){
                  $q="DELETE FROM  `privat24` WHERE `id`=".quote_smart($card_id)." LIMIT 1";
                  //echo $q;
                  $log->lwrite('Удалена карта # '.$card_id.' user:'.$_GET['user'].' serial:'.$_GET['card']." 
  
  <br />\n");
  
                  mysql_query($q);
              }
              break;
      */
      case "update":
               if($_POST['uid']>0){
                    $q="UPDATE `users` SET `credit`='".$_POST['credit']."' WHERE `uid`=".quote_smart($_POST['uid'])." LIMIT 1";
                    $log->lwrite('обновление кредита пользователю: <a target="_open" href="edit_user.php?uid='.$_POST['uid'].'">'.$_POST['user'].'['.$_POST['uid'].'] '."</a><br />\n");
                     mysql_query($q);
               }
               break;
  
      case "updateall":
                   if($_POST['uid']>0){
                      $q="UPDATE `users` SET `credit`='0.00' ";
                      $log->lwrite('обновление кредита всех пользователей'."&lt;/a><br />\n");
                     mysql_query($q);
                    }
  
               break;
  
  }
  $q="SELECT * FROM `users` WHERE `credit`>'0.01' OR `credit`&lt;'-0.01' ORDER BY `credit`  DESC ";
  
    $result = mysql_query($q);
    //$days=array();
    $i=0;
  echo "
  
  <table border='1'>
    <td>
      N
    </td>
    
    <td>
      user
    </td>
    
    <td>
      credit
    </td>
    
    <td>
      deposit
    </td>
    
    <td>
      Установить кредит
    </td>";
    
    while($row = mysql_fetch_array($result, MYSQL_ASSOC)){
        $i++;
        echo " 
    
    <tr>
      <td>
        $i
      </td>
      
      <td>
        &lt;a target=\"_open\" href=\"edit_user.php?uid=".$row['uid']."\"> ".$row['user']."&lt;/a>
      </td>
                      
      
      <td>
        ".$row['credit']."
      </td>
                      
      
      <td>
        ".$row['deposit']."
      </td>
                      
      
      <td>
        
      </td>
      
                 
    </tr> ";
    }
    echo "
  </table>";
  mysql_close($link);
  ?>
  
  
  
  <?

?>
  
</CENTER>


<?
include("bottom.php");
?>

</pre>