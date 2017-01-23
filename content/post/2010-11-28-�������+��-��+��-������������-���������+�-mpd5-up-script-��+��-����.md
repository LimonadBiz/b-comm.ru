---
title: 'Скрипт для сервера доступа mpd5: up-script для информирования абонентов'
author: wel
type: post
date: 2010-11-28T11:19:09+00:00
url: /billing/скрипт-для-сервера-доступа-mpd5-up-script-для-инф
short-url:
  - http://bit.ly/eAyszI
wp-syntax-cache-content:
  - |
    a:6:{i:1;s:3133:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="line_numbers"><pre>1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    </pre></td><td class="code"><pre class="php" style="font-family:monospace;">#!/usr/loca/bin/php                          
    <span style="color: #000000; font-weight: bold;">&lt;?php</span>                                                                                                                                         <span style="color: #666666; font-style: italic;">/*
    * Скрипт для информирования абонентов при подключении к 
    * серверу доступа
    */</span>                                     
    <span style="color: #666666; font-style: italic;">//$interface=$argv['1'];                         </span>
    <span style="color: #000088;">$table_ipfw_for_warn_up</span><span style="color: #339933;">=</span><span style="color: #cc66cc;">7</span><span style="color: #339933;">;</span> <span style="color: #666666; font-style: italic;">// ЭТО таблица в фаерволе ipfw </span>
    <span style="color: #000088;">$fr_ip</span><span style="color: #339933;">=</span><span style="color: #000088;">$argv</span><span style="color: #009900;">&#91;</span><span style="color: #0000ff;">'4'</span><span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span>                                                                                                                          <span style="color: #000088;">$last_line</span> <span style="color: #339933;">=</span> <span style="color: #990000;">system</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">'/sbin/ipfw table '</span><span style="color: #339933;">.</span><span style="color: #000088;">$table_ipfw_for_warn_up</span><span style="color: #339933;">.</span><span style="color: #0000ff;">' add '</span><span style="color: #339933;">.</span><span style="color: #000088;">$fr_ip</span><span style="color: #339933;">.</span><span style="color: #0000ff;">&quot;&quot;</span><span style="color: #339933;">,</span> <span style="color: #000088;">$retval</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000000; font-weight: bold;">?&gt;</span></pre></td></tr></table><p class="theCode" style="display:none;">#!/usr/loca/bin/php                          
    &lt;?php                                                                                                                                         /*
    * Скрипт для информирования абонентов при подключении к 
    * серверу доступа
    */                                     
    //$interface=$argv['1'];                         
    $table_ipfw_for_warn_up=7; // ЭТО таблица в фаерволе ipfw 
    $fr_ip=$argv['4'];                                                                                                                          $last_line = system('/sbin/ipfw table '.$table_ipfw_for_warn_up.' add '.$fr_ip.&quot;&quot;, $retval);
                            
    ?&gt;</p></div>
    ";i:2;s:2934:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="bash" style="font-family:monospace;"><span style="color: #666666; font-style: italic;">#!/bin/sh</span>
    <span style="color: #000000; font-weight: bold;">/</span>sbin<span style="color: #000000; font-weight: bold;">/</span>ipfw delete <span style="color: #000000;">6</span>
    <span style="color: #000000; font-weight: bold;">/</span>sbin<span style="color: #000000; font-weight: bold;">/</span>ipfw table <span style="color: #000000;">6</span> flush                 
     <span style="color: #666666; font-style: italic;">#table 6 содержит ИП-адреса НАШЕГО адресного пространства, тут как минимум должен быть ВПН-сервер</span>
    <span style="color: #000000; font-weight: bold;">/</span>sbin<span style="color: #000000; font-weight: bold;">/</span>ipfw table <span style="color: #000000;">6</span> add 10.0.0.0<span style="color: #000000; font-weight: bold;">/</span><span style="color: #000000;">8</span>;               
    <span style="color: #000000; font-weight: bold;">/</span>sbin<span style="color: #000000; font-weight: bold;">/</span>ipfw table <span style="color: #000000;">6</span> add 192.168.0.0<span style="color: #000000; font-weight: bold;">/</span><span style="color: #000000;">16</span>;    
    &nbsp;
    <span style="color: #666666; font-style: italic;">#перенаправленние всего трафика абонента на траницу, котороя у нас висит на сервере: </span>
    <span style="color: #666666; font-style: italic;">#server 127.0.0.1 port 9988</span>
    &nbsp;
    <span style="color: #000000; font-weight: bold;">/</span>sbin<span style="color: #000000; font-weight: bold;">/</span>ipfw add <span style="color: #000000;">6</span> fwd 127.0.0.1,<span style="color: #000000;">9988</span> all from table\<span style="color: #7a0874; font-weight: bold;">&#40;</span><span style="color: #000000;">7</span>\<span style="color: #7a0874; font-weight: bold;">&#41;</span> to not table\<span style="color: #7a0874; font-weight: bold;">&#40;</span><span style="color: #000000;">6</span>\<span style="color: #7a0874; font-weight: bold;">&#41;</span>;</pre></td></tr></table><p class="theCode" style="display:none;">#!/bin/sh
    /sbin/ipfw delete 6
    /sbin/ipfw table 6 flush                 
     #table 6 содержит ИП-адреса НАШЕГО адресного пространства, тут как минимум должен быть ВПН-сервер
    /sbin/ipfw table 6 add 10.0.0.0/8;               
    /sbin/ipfw table 6 add 192.168.0.0/16;    
    
    #перенаправленние всего трафика абонента на траницу, котороя у нас висит на сервере: 
    #server 127.0.0.1 port 9988
    
    /sbin/ipfw add 6 fwd 127.0.0.1,9988 all from table\(7\) to not table\(6\);</p></div>
    ";i:3;s:11597:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="line_numbers"><pre>1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    16
    17
    18
    19
    20
    21
    22
    23
    24
    25
    26
    </pre></td><td class="code"><pre class="bash" style="font-family:monospace;">   server <span style="color: #7a0874; font-weight: bold;">&#123;</span>                                                                                                                                                                        
            listen       <span style="color: #000000;">9988</span>;                                                                                                                                                         
          location <span style="color: #000000; font-weight: bold;">/</span> <span style="color: #7a0874; font-weight: bold;">&#123;</span>                                                                                                                                                                 
               index index.php;                                                                                                                                                        
                    root  <span style="color: #000000; font-weight: bold;">/</span>usr<span style="color: #000000; font-weight: bold;">/</span>local<span style="color: #000000; font-weight: bold;">/</span>www<span style="color: #000000; font-weight: bold;">/</span>perevod_info;                                                                                                                                 
                    error_page  <span style="color: #000000;">404</span> <span style="color: #000000; font-weight: bold;">/</span>index.php;                                                                                                                                        
                    error_page <span style="color: #000000;">403</span> <span style="color: #000000; font-weight: bold;">/</span>index.php;                                                                                                                                         
                     <span style="color: #000000; font-weight: bold;">if</span> <span style="color: #7a0874; font-weight: bold;">&#40;</span><span style="color: #000000; font-weight: bold;">!</span>-e <span style="color: #007800;">$request_filename</span><span style="color: #7a0874; font-weight: bold;">&#41;</span> <span style="color: #7a0874; font-weight: bold;">&#123;</span>                                                                                                                                      
                            rewrite ^<span style="color: #7a0874; font-weight: bold;">&#40;</span>.<span style="color: #000000; font-weight: bold;">*</span><span style="color: #7a0874; font-weight: bold;">&#41;</span>$ <span style="color: #000000; font-weight: bold;">/</span>index.php <span style="color: #c20cb9; font-weight: bold;">last</span>;                                                                                                                            
                    <span style="color: #7a0874; font-weight: bold;">&#125;</span>                                                                                                                                                                  
           <span style="color: #7a0874; font-weight: bold;">&#125;</span>                                                                                                                                                                           
            location ~ \.php$ <span style="color: #7a0874; font-weight: bold;">&#123;</span>                                                                                                                                                        
                   fastcgi_pass    127.0.0.1:<span style="color: #000000;">9000</span>;                                                                                                                                     
    &nbsp;
                   fastcgi_index   index.php;                                                                                                                                          
             <span style="color: #666666; font-style: italic;">#      fastcgi_param     SCRIPT_FILENAME       /usr/local/www/forbid_inet/index.php;                                                                                      </span>
                    fastcgi_param     SCRIPT_FILENAME       <span style="color: #000000; font-weight: bold;">/</span>usr<span style="color: #000000; font-weight: bold;">/</span>local<span style="color: #000000; font-weight: bold;">/</span>www<span style="color: #000000; font-weight: bold;">/</span>perevod_info<span style="color: #007800;">$fastcgi_script_name</span>;                                                                           
                 include      fastcgi_params;                                                                                                                                          
            <span style="color: #7a0874; font-weight: bold;">&#125;</span>                                                                                                                                                                          
    &nbsp;
            error_page  <span style="color: #000000;">404</span> <span style="color: #000000; font-weight: bold;">/</span>index.php;                                                                                                                                                
            error_page   <span style="color: #000000;">500</span> <span style="color: #000000;">502</span> <span style="color: #000000;">503</span> <span style="color: #000000;">504</span>  <span style="color: #000000; font-weight: bold;">/</span>index.php;                                                                                                                                  
            location = <span style="color: #000000; font-weight: bold;">/</span>50x.html <span style="color: #7a0874; font-weight: bold;">&#123;</span>                                                                                                                                                     
                root   <span style="color: #000000; font-weight: bold;">/</span>usr<span style="color: #000000; font-weight: bold;">/</span>local<span style="color: #000000; font-weight: bold;">/</span>www<span style="color: #000000; font-weight: bold;">/</span>nginx-dist;                                                                                                                                      
            <span style="color: #7a0874; font-weight: bold;">&#125;</span>                                                                                                                                                                          
    <span style="color: #7a0874; font-weight: bold;">&#125;</span></pre></td></tr></table><p class="theCode" style="display:none;">   server {                                                                                                                                                                        
            listen       9988;                                                                                                                                                         
          location / {                                                                                                                                                                 
               index index.php;                                                                                                                                                        
                    root  /usr/local/www/perevod_info;                                                                                                                                 
                    error_page  404 /index.php;                                                                                                                                        
                    error_page 403 /index.php;                                                                                                                                         
                     if (!-e $request_filename) {                                                                                                                                      
                            rewrite ^(.*)$ /index.php last;                                                                                                                            
                    }                                                                                                                                                                  
           }                                                                                                                                                                           
            location ~ \.php$ {                                                                                                                                                        
                   fastcgi_pass    127.0.0.1:9000;                                                                                                                                     
                                                                                                                                                                                       
                   fastcgi_index   index.php;                                                                                                                                          
             #      fastcgi_param     SCRIPT_FILENAME       /usr/local/www/forbid_inet/index.php;                                                                                      
                    fastcgi_param     SCRIPT_FILENAME       /usr/local/www/perevod_info$fastcgi_script_name;                                                                           
                 include      fastcgi_params;                                                                                                                                          
            }                                                                                                                                                                          
                                                                                                                                                                                       
            error_page  404 /index.php;                                                                                                                                                
            error_page   500 502 503 504  /index.php;                                                                                                                                  
            location = /50x.html {                                                                                                                                                     
                root   /usr/local/www/nginx-dist;                                                                                                                                      
            }                                                                                                                                                                          
    }</p></div>
    ";i:4;s:614:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="php" style="font-family:monospace;"><span style="color: #000000; font-weight: bold;">&lt;?php</span> <span style="color: #b1b100;">include_once</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;index_.html&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span></pre></td></tr></table><p class="theCode" style="display:none;">&lt;?php include_once(&quot;index_.html&quot;); ?&gt;</p></div>
    ";i:5;s:61130:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="line_numbers"><pre>1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    16
    17
    18
    19
    20
    21
    22
    23
    24
    25
    26
    27
    28
    29
    30
    31
    32
    33
    34
    35
    36
    37
    38
    39
    40
    41
    42
    43
    44
    45
    46
    47
    48
    49
    50
    51
    52
    53
    54
    55
    56
    57
    58
    59
    60
    61
    62
    63
    64
    65
    66
    67
    68
    69
    70
    71
    72
    73
    74
    75
    76
    77
    78
    79
    80
    81
    82
    83
    84
    85
    86
    87
    88
    89
    90
    91
    92
    93
    94
    95
    96
    97
    98
    99
    100
    101
    102
    103
    104
    105
    106
    107
    108
    109
    110
    111
    112
    113
    114
    115
    116
    117
    118
    119
    120
    121
    122
    123
    124
    125
    126
    127
    128
    129
    130
    131
    132
    133
    134
    135
    136
    137
    138
    139
    140
    141
    </pre></td><td class="code"><pre class="html" style="font-family:monospace;">&lt;!DOCTYPE html PUBLIC &quot;-//W3C//DTD XHTML 1.0 Transitional//EN&quot; &quot;http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd&quot;&gt;                                                          
    &lt;html xmlns=&quot;http://www.w3.org/1999/xhtml&quot;&gt;                                                                                                                                        
    &lt;head&gt;                                                                                                                                                                             
    &lt;meta http-equiv=&quot;Content-Type&quot; content=&quot;text/html; charset=utf-8&quot; /&gt;                                                                                                              
    &lt;title&gt;Внимание!!!&lt;/title&gt;                                                                                                                                                         
    &lt;style type=&quot;text/css&quot;&gt;                                                                                                                                                            
    &lt;!--                                                                                                                                                                               
    body {                                                                                                                                                                             
            font: 100%/1.4 Verdana, Arial, Helvetica, sans-serif;                                                                                                                      
            background: #4E5869;                                                                                                                                                       
            margin: 0;                                                                                                                                                                 
            padding: 0;                                                                                                                                                                
            color: #000;                                                                                                                                                               
    }                                                                                                                                                                                  
    &nbsp;
    /* ~~ Селекторы элементов/тегов ~~ */                                                                                                                                              
    ul, ol, dl { /* Из-за различий между браузерами рекомендуется обнулять поля в списках. Для согласованности можно указать нужные величины либо здесь, либо в элементах списка (LI, DT, DD), которые они содержат. Помните, что сделанное здесь последовательно включается в список .nav, если только не будет прописан более конкретный селектор. */                   
            padding: 0;                                                                                                                                                                
            margin: 0;                                                                                                                                                                 
    }                                                                                                                                                                                  
    h1, h2, h3, h4, h5, h6, p {                                                                                                                                                        
            margin-top: 0;   /* удаление верхнего поля позволяет обойти проблему выхода полей за границы содержащего их контейнера DIV. Оставшееся нижнее поле отделит его от любых последующих элементов. */                                                                                                                                                             
            padding-right: 15px;                                                                                                                                                       
            padding-left: 15px; /* добавление боковых полей к элементам внутри контейнеров DIV, а не к самим контейнерам избавляет от необходимости расчетов рамочной модели. В качестве альтернативы можно использовать вложенный контейнер DIV с боковыми полями. */                                                                                                    
            text-align: center;                                                                                                                                                        
    }                                                                                                                                                                                  
    a img { /* этот селектор убирает стандартную синюю рамку, которая появляется у изображений в некоторых браузерах, если вокруг изображения есть ссылка */                           
            border: none;                                                                                                                                                              
    }                                                                                                                                                                                  
    &nbsp;
    /* ~~ Оформление ссылок на вашем сайте должно оставаться в этом порядке, включая группу селекторов, создающих эффект наведения. ~~ */                                              
    a:link {                                                                                                                                                                           
            color:#414958;                                                                                                                                                             
            text-decoration: underline; /* если только ссылки не должны выглядеть исключительно своеобразно, то для быстрого зрительного распознавания рекомендуется использовать подчеркивание */                                                                                                                                                                        
    }                                                                                                                                                                                  
    a:visited {                                                                                                                                                                        
            color: #4E5869;                                                                                                                                                            
            text-decoration: underline;                                                                                                                                                
    }                                                                                                                                                                                  
    a:hover, a:active, a:focus { /* эта группа селекторов обеспечивает пользователю, работающему с клавиатурой, такие же возможности наведения, как и при использовании мыши. */       
            text-decoration: none;                                                                                                                                                     
    }                                                                                                                                                                                  
    &nbsp;
    /* ~~ этот контейнер окружает все остальные контейнеры DIV, задавая их ширину на процентной основе ~~ */                                                                           
    .container {                                                                                                                                                                       
            width: 98%;                                                                                                                                                                
            max-width: 1260px;/* желательно задать максимальную ширину, чтобы макет не стал слишком широким на большом экране. Это повышает удобство чтения строк. В IE6 это объявление не соблюдается. */                                                                                                                                                                
            min-width: 780px;/* желательно задать минимальную ширину, чтобы макет не стал слишком узким. Это повышает удобство чтения строк в боковых столбцах. В IE6 это объявление не соблюдается. */                                                                                                                                                                   
            background: #FFF;                                                                                                                                                          
            margin: 0 auto; /* автоматическое задание величин по бокам в совокупности с шириной центрирует макет. Это необязательно, если ширина контейнера составляет 100 %. */       
    }                                                                                                                                                                                  
    &nbsp;
    /* ~~верхнему колонтитулу не задана ширина. Он растянется по всей ширине макета. Он содержит заполнитель для изображения, который должен быть заменен логотипом по ссылке~~ */     
    .header {                                                                                                                                                                          
            background: #6F7D94;                                                                                                                                                       
    }                                                                                                                                                                                  
    &nbsp;
    /* ~~ Информация по макету. ~~                                                                                                                                                     
    &nbsp;
    1) Поля размещены только вверху и/или внизу DIV. Элементы в этом DIV имеют боковые поля. Это избавляет пользователя от необходимости расчетов рамочной модели. Помните, что при добавлении боковых полей или границы к самому DIV их ширина будет добавлена к задаваемой ширине, что образует &quot;полную&quot; ширину. Кроме того, можно удалить поля элемента в DIV и поместить внутри него второй DIV без ширины и с необходимыми по проекту полями.                                                                                                           
    &nbsp;
    */                                                                                                                                                                                 
    .content {                                                                                                                                                                         
            padding: 10px 0;                                                                                                                                                           
    }                                                                                                                                                                                  
    &nbsp;
    /* ~~ Этот сгруппированный селектор выдает списки в пространстве .content ~~ */                                                                                                    
    .content ul, .content ol {                                                                                                                                                         
            padding: 0 15px 15px 40px; /* это поле зеркально повторяет правое поле в правиле для заголовков и параграфов выше. Внизу поле помещено как граница между элементами списков, а слева — как отступ. Поля можно настраивать по желанию. */                                                                                                                      
            font-weight: bold;                                                                                                                                                         
    }                                                                                                                                                                                  
    &nbsp;
    /* ~~ Нижний колонтитул ~~ */                                                                                                                                                      
    .footer {                                                                                                                                                                          
            padding: 10px 0;                                                                                                                                                           
            background: #6F7D94;                                                                                                                                                       
    }                                                                                                                                                                                  
    &nbsp;
    /* ~~ прочие классы float/clear ~~ */                                                                                                                                              
    .fltrt {  /* этот класс можно использовать для обтекания элемента справа на странице. Обтекаемый элемент должен предшествовать элементу, с которым он должен находиться рядом на странице. */                                                                                                                                                                         
            float: right;                                                                                                                                                              
            margin-left: 8px;                                                                                                                                                          
    }                                                                                                                                                                                  
    .fltlft { /* этот класс можно использовать для обтекания элемента слева на странице. Обтекаемый элемент должен предшествовать элементу, с которым он должен находиться рядом на странице. */                                                                                                                                                                          
            float: left;                                                                                                                                                               
            margin-right: 8px;                                                                                                                                                         
    }                                                                                                                                                                                  
    .clearfloat { /* этот класс можно поместить в теге &lt;br /&gt; или в пустом блоке DIV в качестве конечного элемента, следующего за последним обтекаемым DIV (внутри #container), если .#footer удален или извлечен из #container */                                                                                                                                        
            clear:both;                                                                                                                                                                
            height:0;                                                                                                                                                                  
            font-size: 1px;                                                                                                                                                            
            line-height: 0px;                                                                                                                                                          
    }                                                                                                                                                                                  
    .qqqq {                                                                                                                                                                            
            color: #F00;                                                                                                                                                               
    }                                                                                                                                                                                  
    .gggggggg {                                                                                                                                                                        
            font-weight: bold;                                                                                                                                                         
            color: #F00;                                                                                                                                                               
    }                                                                                                                                                                                  
    .ghghgh {                                                                                                                                                                          
            font-weight: bold;                                                                                                                                                         
    }                                                                                                                                                                                  
    .sddsfsdf {                                                                                                                                                                        
            font-style: italic;                                                                                                                                                        
    }                                                                                                                                                                                  
    .container .content div div ul .sddsfsdf {                                                                                                                                         
            color: #F00;                                                                                                                                                               
    }                                                                                                                                                                                  
    --&gt;                                                                                                                                                                                
    &lt;/style&gt;&lt;/head&gt;                                                                                                                                                                    
    &nbsp;
    &lt;body&gt;                                                                                                                                                                             
    &nbsp;
    &lt;div class=&quot;container&quot;&gt;                                                                                                                                                            
      &lt;div class=&quot;header&quot;&gt;&lt;a href=&quot;http://www.isp.pl.ua&quot;&gt;home&lt;/a&gt;                                                                                                                     
        &lt;!-- end .header --&gt;&lt;/div&gt;                                                                                                                                                     
      &lt;div class=&quot;content&quot;&gt;                                                                                                                                                            
        &lt;h1 align=&quot;center&quot; style=&quot;color:#F00&quot;&gt;Внимание!!!&lt;/h1&gt;                                                                                                                         
        &lt;p align=&quot;center&quot; style=&quot;color:#F00&quot;&gt;&lt;em&gt;Прочитайте полность, что бы это сообщение больше не появлялось!!!&lt;/em&gt;&lt;/p&gt;                                                            
    &nbsp;
        &lt;div&gt; Уважаемые клиент в связи с переходом на новый биллинг, произошли изменения. &lt;/div&gt;                                               
    &nbsp;
        &lt;div&gt; &lt;br /&gt;                                                                                                                                                                   
        &lt;/div&gt;                                                                                                                                                                         
        &lt;div&gt; Так же со сменой серверов изменился и способ подключения, теперь доступ к Интернету предоставляется по протоколу PPPoE(Инструкция для &lt;a href=&quot;http://b-comm.ru:9988/pppoe_winxp.html&quot;&gt;Windows XP&lt;/a&gt; &lt;a href=&quot;http://b-comm.ru:9988/pppoe_win7.html&quot;&gt;Windows 7&lt;/a&gt;!!!).  &lt;/div&gt;                                                                        
        &lt;div&gt;                                                                                                                                                                          
          &lt;p&gt;&lt;span class=&quot;gggggggg&quot;&gt;!!! Старые сервера будут отключены первого января 2011 года, уважительная просьба к этому времени создать новые подключения!!! &lt;/span&gt;&lt;!-- end .content --&gt;&lt;/p&gt;                  
          &lt;div&gt;                                                                                                                                                                        
          &lt;/div&gt;                                                                                                                                                                       
          &lt;div&gt; &lt;/div&gt;                                                                                                                                                                 
             &lt;p align=&quot;center&quot; style=&quot;color:#F00; font-style: italic;&quot;&gt;(!!!это сообщение пропадёт только через 10 минут!!!&lt;/p&gt;                                                                                                                                                                 
          &lt;p&gt;&amp;nbsp;&lt;/p&gt;                                                                                                                                                                
        &lt;/div&gt;                                                                                                                                                                         
    &lt;/div&gt;                                                                                                                                                                             
      &lt;div class=&quot;footer&quot;&gt;                                                                                                                                                             
        &lt;p&gt;К Вам обращается Администрация сети &amp;quot;home&amp;quot;&lt;/p&gt;                                                                                                                 
      &lt;!-- end .footer --&gt;&lt;/div&gt;                                                                                                                                                       
      &lt;!-- end .container --&gt;&lt;/div&gt;                                                                                                                                                    
    &lt;/body&gt;                                                                                                                                                                            
    &lt;/html&gt;</pre></td></tr></table><p class="theCode" style="display:none;">&lt;!DOCTYPE html PUBLIC &quot;-//W3C//DTD XHTML 1.0 Transitional//EN&quot; &quot;http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd&quot;&gt;                                                          
    &lt;html xmlns=&quot;http://www.w3.org/1999/xhtml&quot;&gt;                                                                                                                                        
    &lt;head&gt;                                                                                                                                                                             
    &lt;meta http-equiv=&quot;Content-Type&quot; content=&quot;text/html; charset=utf-8&quot; /&gt;                                                                                                              
    &lt;title&gt;Внимание!!!&lt;/title&gt;                                                                                                                                                         
    &lt;style type=&quot;text/css&quot;&gt;                                                                                                                                                            
    &lt;!--                                                                                                                                                                               
    body {                                                                                                                                                                             
            font: 100%/1.4 Verdana, Arial, Helvetica, sans-serif;                                                                                                                      
            background: #4E5869;                                                                                                                                                       
            margin: 0;                                                                                                                                                                 
            padding: 0;                                                                                                                                                                
            color: #000;                                                                                                                                                               
    }                                                                                                                                                                                  
                                                                                                                                                                                       
    /* ~~ Селекторы элементов/тегов ~~ */                                                                                                                                              
    ul, ol, dl { /* Из-за различий между браузерами рекомендуется обнулять поля в списках. Для согласованности можно указать нужные величины либо здесь, либо в элементах списка (LI, DT, DD), которые они содержат. Помните, что сделанное здесь последовательно включается в список .nav, если только не будет прописан более конкретный селектор. */                   
            padding: 0;                                                                                                                                                                
            margin: 0;                                                                                                                                                                 
    }                                                                                                                                                                                  
    h1, h2, h3, h4, h5, h6, p {                                                                                                                                                        
            margin-top: 0;   /* удаление верхнего поля позволяет обойти проблему выхода полей за границы содержащего их контейнера DIV. Оставшееся нижнее поле отделит его от любых последующих элементов. */                                                                                                                                                             
            padding-right: 15px;                                                                                                                                                       
            padding-left: 15px; /* добавление боковых полей к элементам внутри контейнеров DIV, а не к самим контейнерам избавляет от необходимости расчетов рамочной модели. В качестве альтернативы можно использовать вложенный контейнер DIV с боковыми полями. */                                                                                                    
            text-align: center;                                                                                                                                                        
    }                                                                                                                                                                                  
    a img { /* этот селектор убирает стандартную синюю рамку, которая появляется у изображений в некоторых браузерах, если вокруг изображения есть ссылка */                           
            border: none;                                                                                                                                                              
    }                                                                                                                                                                                  
                                                                                                                                                                                       
    /* ~~ Оформление ссылок на вашем сайте должно оставаться в этом порядке, включая группу селекторов, создающих эффект наведения. ~~ */                                              
    a:link {                                                                                                                                                                           
            color:#414958;                                                                                                                                                             
            text-decoration: underline; /* если только ссылки не должны выглядеть исключительно своеобразно, то для быстрого зрительного распознавания рекомендуется использовать подчеркивание */                                                                                                                                                                        
    }                                                                                                                                                                                  
    a:visited {                                                                                                                                                                        
            color: #4E5869;                                                                                                                                                            
            text-decoration: underline;                                                                                                                                                
    }                                                                                                                                                                                  
    a:hover, a:active, a:focus { /* эта группа селекторов обеспечивает пользователю, работающему с клавиатурой, такие же возможности наведения, как и при использовании мыши. */       
            text-decoration: none;                                                                                                                                                     
    }                                                                                                                                                                                  
                                                                                                                                                                                       
    /* ~~ этот контейнер окружает все остальные контейнеры DIV, задавая их ширину на процентной основе ~~ */                                                                           
    .container {                                                                                                                                                                       
            width: 98%;                                                                                                                                                                
            max-width: 1260px;/* желательно задать максимальную ширину, чтобы макет не стал слишком широким на большом экране. Это повышает удобство чтения строк. В IE6 это объявление не соблюдается. */                                                                                                                                                                
            min-width: 780px;/* желательно задать минимальную ширину, чтобы макет не стал слишком узким. Это повышает удобство чтения строк в боковых столбцах. В IE6 это объявление не соблюдается. */                                                                                                                                                                   
            background: #FFF;                                                                                                                                                          
            margin: 0 auto; /* автоматическое задание величин по бокам в совокупности с шириной центрирует макет. Это необязательно, если ширина контейнера составляет 100 %. */       
    }                                                                                                                                                                                  
                                                                                                                                                                                       
    /* ~~верхнему колонтитулу не задана ширина. Он растянется по всей ширине макета. Он содержит заполнитель для изображения, который должен быть заменен логотипом по ссылке~~ */     
    .header {                                                                                                                                                                          
            background: #6F7D94;                                                                                                                                                       
    }                                                                                                                                                                                  
                                                                                                                                                                                       
    /* ~~ Информация по макету. ~~                                                                                                                                                     
                                                                                                                                                                                       
    1) Поля размещены только вверху и/или внизу DIV. Элементы в этом DIV имеют боковые поля. Это избавляет пользователя от необходимости расчетов рамочной модели. Помните, что при добавлении боковых полей или границы к самому DIV их ширина будет добавлена к задаваемой ширине, что образует &quot;полную&quot; ширину. Кроме того, можно удалить поля элемента в DIV и поместить внутри него второй DIV без ширины и с необходимыми по проекту полями.                                                                                                           
                                                                                                                                                                                       
    */                                                                                                                                                                                 
    .content {                                                                                                                                                                         
            padding: 10px 0;                                                                                                                                                           
    }                                                                                                                                                                                  
                                                                                                                                                                                       
    /* ~~ Этот сгруппированный селектор выдает списки в пространстве .content ~~ */                                                                                                    
    .content ul, .content ol {                                                                                                                                                         
            padding: 0 15px 15px 40px; /* это поле зеркально повторяет правое поле в правиле для заголовков и параграфов выше. Внизу поле помещено как граница между элементами списков, а слева — как отступ. Поля можно настраивать по желанию. */                                                                                                                      
            font-weight: bold;                                                                                                                                                         
    }                                                                                                                                                                                  
                                                                                                                                                                                       
    /* ~~ Нижний колонтитул ~~ */                                                                                                                                                      
    .footer {                                                                                                                                                                          
            padding: 10px 0;                                                                                                                                                           
            background: #6F7D94;                                                                                                                                                       
    }                                                                                                                                                                                  
                                                                                                                                                                                       
    /* ~~ прочие классы float/clear ~~ */                                                                                                                                              
    .fltrt {  /* этот класс можно использовать для обтекания элемента справа на странице. Обтекаемый элемент должен предшествовать элементу, с которым он должен находиться рядом на странице. */                                                                                                                                                                         
            float: right;                                                                                                                                                              
            margin-left: 8px;                                                                                                                                                          
    }                                                                                                                                                                                  
    .fltlft { /* этот класс можно использовать для обтекания элемента слева на странице. Обтекаемый элемент должен предшествовать элементу, с которым он должен находиться рядом на странице. */                                                                                                                                                                          
            float: left;                                                                                                                                                               
            margin-right: 8px;                                                                                                                                                         
    }                                                                                                                                                                                  
    .clearfloat { /* этот класс можно поместить в теге &lt;br /&gt; или в пустом блоке DIV в качестве конечного элемента, следующего за последним обтекаемым DIV (внутри #container), если .#footer удален или извлечен из #container */                                                                                                                                        
            clear:both;                                                                                                                                                                
            height:0;                                                                                                                                                                  
            font-size: 1px;                                                                                                                                                            
            line-height: 0px;                                                                                                                                                          
    }                                                                                                                                                                                  
    .qqqq {                                                                                                                                                                            
            color: #F00;                                                                                                                                                               
    }                                                                                                                                                                                  
    .gggggggg {                                                                                                                                                                        
            font-weight: bold;                                                                                                                                                         
            color: #F00;                                                                                                                                                               
    }                                                                                                                                                                                  
    .ghghgh {                                                                                                                                                                          
            font-weight: bold;                                                                                                                                                         
    }                                                                                                                                                                                  
    .sddsfsdf {                                                                                                                                                                        
            font-style: italic;                                                                                                                                                        
    }                                                                                                                                                                                  
    .container .content div div ul .sddsfsdf {                                                                                                                                         
            color: #F00;                                                                                                                                                               
    }                                                                                                                                                                                  
    --&gt;                                                                                                                                                                                
    &lt;/style&gt;&lt;/head&gt;                                                                                                                                                                    
                                                                                                                                                                                       
    &lt;body&gt;                                                                                                                                                                             
                                                                                                                                                                                       
    &lt;div class=&quot;container&quot;&gt;                                                                                                                                                            
      &lt;div class=&quot;header&quot;&gt;&lt;a href=&quot;http://www.isp.pl.ua&quot;&gt;home&lt;/a&gt;                                                                                                                     
        &lt;!-- end .header --&gt;&lt;/div&gt;                                                                                                                                                     
      &lt;div class=&quot;content&quot;&gt;                                                                                                                                                            
        &lt;h1 align=&quot;center&quot; style=&quot;color:#F00&quot;&gt;Внимание!!!&lt;/h1&gt;                                                                                                                         
        &lt;p align=&quot;center&quot; style=&quot;color:#F00&quot;&gt;&lt;em&gt;Прочитайте полность, что бы это сообщение больше не появлялось!!!&lt;/em&gt;&lt;/p&gt;                                                            
                                                                                                                                                                                       
        &lt;div&gt; Уважаемые клиент в связи с переходом на новый биллинг, произошли изменения. &lt;/div&gt;                                               
                                                                                                                                  
        &lt;div&gt; &lt;br /&gt;                                                                                                                                                                   
        &lt;/div&gt;                                                                                                                                                                         
        &lt;div&gt; Так же со сменой серверов изменился и способ подключения, теперь доступ к Интернету предоставляется по протоколу PPPoE(Инструкция для &lt;a href=&quot;http://b-comm.ru:9988/pppoe_winxp.html&quot;&gt;Windows XP&lt;/a&gt; &lt;a href=&quot;http://b-comm.ru:9988/pppoe_win7.html&quot;&gt;Windows 7&lt;/a&gt;!!!).  &lt;/div&gt;                                                                        
        &lt;div&gt;                                                                                                                                                                          
          &lt;p&gt;&lt;span class=&quot;gggggggg&quot;&gt;!!! Старые сервера будут отключены первого января 2011 года, уважительная просьба к этому времени создать новые подключения!!! &lt;/span&gt;&lt;!-- end .content --&gt;&lt;/p&gt;                  
          &lt;div&gt;                                                                                                                                                                        
          &lt;/div&gt;                                                                                                                                                                       
          &lt;div&gt; &lt;/div&gt;                                                                                                                                                                 
             &lt;p align=&quot;center&quot; style=&quot;color:#F00; font-style: italic;&quot;&gt;(!!!это сообщение пропадёт только через 10 минут!!!&lt;/p&gt;                                                                                                                                                                 
          &lt;p&gt;&amp;nbsp;&lt;/p&gt;                                                                                                                                                                
        &lt;/div&gt;                                                                                                                                                                         
    &lt;/div&gt;                                                                                                                                                                             
      &lt;div class=&quot;footer&quot;&gt;                                                                                                                                                             
        &lt;p&gt;К Вам обращается Администрация сети &amp;quot;home&amp;quot;&lt;/p&gt;                                                                                                                 
      &lt;!-- end .footer --&gt;&lt;/div&gt;                                                                                                                                                       
      &lt;!-- end .container --&gt;&lt;/div&gt;                                                                                                                                                    
    &lt;/body&gt;                                                                                                                                                                            
    &lt;/html&gt;</p></div>
    ";i:6;s:848:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="php" style="font-family:monospace;"><span style="color: #339933;">*/</span><span style="color: #cc66cc;">10</span>    <span style="color: #339933;">*</span>       <span style="color: #339933;">*</span>       <span style="color: #339933;">*</span>       <span style="color: #339933;">*</span>       root <span style="color: #339933;">/</span>sbin<span style="color: #339933;">/</span>ipfw table <span style="color: #cc66cc;">7</span> <span style="color: #990000;">flush</span>  <span style="color: #cc66cc;">2</span><span style="color: #339933;">&gt;&amp;</span><span style="color: #cc66cc;">1</span></pre></td></tr></table><p class="theCode" style="display:none;">*/10    *       *       *       *       root /sbin/ipfw table 7 flush  2&gt;&amp;1</p></div>
    ";}
categories:
  - billing
  - дополнения
tags:
  - freebsd
  - ipfw
  - mpd5
  - nginx
  - php
  - up-script

---
Скрипт для сервера доступа mpd5: up-script для информирования абонентов.
  
Этот скрипт Мне понадобился при переводе людей с PPPtP на PPPoE. Дело в том, что обзванивать ВСЕХ не всегда лучшая идея, а вот уведомить людей можно при подключении)))

Скрипт до безобразия простой, Мы добавляем ИП-адрес клиента в таблицу фаервола
  
/usr/local/etc/mpd5/up_warn.php <!--more-->

<pre lang="php" line="1">#!/usr/loca/bin/php                          
<?php                                                                                                                                         /*
* Скрипт для информирования абонентов при подключении к 
* серверу доступа
*/                                     
//$interface=$argv['1'];                         
$table_ipfw_for_warn_up=7; // ЭТО таблица в фаерволе ipfw 
$fr_ip=$argv['4'];                                                                                                                          $last_line = system('/sbin/ipfw table '.$table_ipfw_for_warn_up.' add '.$fr_ip."", $retval);
                        
?>                                                         
</pre>

Далее у Меня OS freeBSD ! Это будет работать на любой freebsd 5, freebsd 6, freebsd 7, freebsd 8, freebsd 9, freebsd 10 =)

Вот простой скрипт. Всё что он делает &#8212; это создаёт правило для редиректа всего трафика от подключившихся абонентов на страницу которая висит на этом же сервере. Надо обратить внимание, что ИП-адреса &#171;у Меня&#187; включают все диапазоны фейковых адресов + реальных &#8212; то есть абоненто сможет спокойно сходить на страницу статистики, игровой сервер или еще что&#8230;.
  
/usr/local/etc/rc.d/ipfw.sh

<pre lang="bash">#!/bin/sh
/sbin/ipfw delete 6
/sbin/ipfw table 6 flush                 
 #table 6 содержит ИП-адреса НАШЕГО адресного пространства, тут как минимум должен быть ВПН-сервер
/sbin/ipfw table 6 add 10.0.0.0/8;               
/sbin/ipfw table 6 add 192.168.0.0/16;    

#перенаправленние всего трафика абонента на траницу, котороя у нас висит на сервере: 
#server 127.0.0.1 port 9988

/sbin/ipfw add 6 fwd 127.0.0.1,9988 all from table\(7\) to not table\(6\);
                                                                        
</pre>

Теперь настраиваем тот самый сервер &#8212; server 127.0.0.1 port 9988.
  
Я использовал nginx &#8212; что бы не грузить сервер)))
  
/usr/local/etc/nginx/nginx.conf:

<pre lang="bash" line="1">server {                                                                                                                                                                        
        listen       9988;                                                                                                                                                         
      location / {                                                                                                                                                                 
           index index.php;                                                                                                                                                        
                root  /usr/local/www/perevod_info;                                                                                                                                 
                error_page  404 /index.php;                                                                                                                                        
                error_page 403 /index.php;                                                                                                                                         
                 if (!-e $request_filename) {                                                                                                                                      
                        rewrite ^(.*)$ /index.php last;                                                                                                                            
                }                                                                                                                                                                  
       }                                                                                                                                                                           
        location ~ \.php$ {                                                                                                                                                        
               fastcgi_pass    127.0.0.1:9000;                                                                                                                                     
                                                                                                                                                                                   
               fastcgi_index   index.php;                                                                                                                                          
         #      fastcgi_param     SCRIPT_FILENAME       /usr/local/www/forbid_inet/index.php;                                                                                      
                fastcgi_param     SCRIPT_FILENAME       /usr/local/www/perevod_info$fastcgi_script_name;                                                                           
             include      fastcgi_params;                                                                                                                                          
        }                                                                                                                                                                          
                                                                                                                                                                                   
        error_page  404 /index.php;                                                                                                                                                
        error_page   500 502 503 504  /index.php;                                                                                                                                  
        location = /50x.html {                                                                                                                                                     
            root   /usr/local/www/nginx-dist;                                                                                                                                      
        }                                                                                                                                                                          
}    
</pre>

index.php 

<pre lang="php"><?php include_once("index_.html"); ?>      
</pre>

index_.html 

<pre lang="html" line="1">                                                          
                                                                                                                                        
                                                                                                                                                                    
                                                                                                                                                                                   
                                                                                                                                                                             
                                                                                                                                                                                   


<div class="container">
  <div class="header">
    <a href="http://www.isp.pl.ua">home</a>                                                                                                                     
        <!-- end .header -->
  </div>                                                                                                                                                     
    
  
  <div class="content">
    <h1 align="center" style="color:#F00">
      Внимание!!!
    </h1>                                                                                                                         
        
    
    <p align="center" style="color:#F00">
      <em>Прочитайте полность, что бы это сообщение больше не появлялось!!!</em>
    </p>                                                            
                                                                                                                                                                                       
        
    
    <div>
      Уважаемые клиент в связи с переходом на новый биллинг, произошли изменения. 
    </div>                                               
                                                                                                                                  
        
    
    <div>
      <br />                                                                                                                                                                   
          
    </div>                                                                                                                                                                         
        
    
    <div>
      Так же со сменой серверов изменился и способ подключения, теперь доступ к Интернету предоставляется по протоколу PPPoE(Инструкция для <a href="http://b-comm.ru:9988/pppoe_winxp.html">Windows XP</a> <a href="http://b-comm.ru:9988/pppoe_win7.html">Windows 7</a>!!!).  
    </div>                                                                        
        
    
    <div>
      <p>
        <span class="gggggggg">!!! Старые сервера будут отключены первого января 2011 года, уважительная просьба к этому времени создать новые подключения!!! </span><!-- end .content -->
      </p>                  
            
      
      <div>
        
      </div>                                                                                                                                                                       
            
      
      <div>
        
      </div>                                                                                                                                                                 
               
      
      <p align="center" style="color:#F00; font-style: italic;">
        (!!!это сообщение пропадёт только через 10 минут!!!
      </p>                                                                                                                                                                 
            
      
      <p>
        &nbsp;
      </p>                                                                                                                                                                
          
    </div>                                                                                                                                                                         
    
  </div>                                                                                                                                                                             
    
  
  <div class="footer">
    <p>
      К Вам обращается Администрация сети "home"
    </p>                                                                                                                 
      
    
    <!-- end .footer -->
  </div>                                                                                                                                                       
    
  
  <!-- end .container -->
</div>                                                                                                                                                    
                                                                                                                                                                            
  
</pre>

И самое последнее &#8212; если Вам всё же нужно что бы пользователи работали в Интернете делайте так:
  
/etc/crontab 

<pre lang="php">*/10    *       *       *       *       root /sbin/ipfw table 7 flush  2>&1                                                                                                        
</pre>