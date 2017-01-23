---
title: edit_packet_menu.php — cкрипт для FreeNIBS, который изменяет пакет пользователя
author: wel
type: post
date: 2012-01-14T23:47:16+00:00
url: /billing/edit_packet_menu-php-cкрипт-для-freenibs-который-изменяет-па
wp-syntax-cache-content:
  - |
    a:1:{i:1;s:56667:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="php" style="font-family:monospace;"><span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">include_once</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;utils.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span> <span style="color: #b1b100;">include_once</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;defines.php&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span><span style="color: #000000; font-weight: bold;">?&gt;</span>
    &lt;FORM ACTION=save_packet.php METHOD=POST&gt;
    &lt;INPUT TYPE=hidden NAME=gid VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$gid</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;
    &lt;TABLE CELLSPACING=2 CELLPADDING=4 BGCOLOR=black WIDTH=80%&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Название&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=packet VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>packet<span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Номер&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=2 NAME=num VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>num<span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Счет по умолчанию&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=deposit VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #990000;">printf</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;<span style="color: #009933; font-weight: bold;">%.2f</span>&quot;</span><span style="color: #339933;">,</span> <span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>deposit<span style="color: #009900;">&#93;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Кредит по умолчанию&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=credit VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #990000;">printf</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;<span style="color: #009933; font-weight: bold;">%.2f</span>&quot;</span><span style="color: #339933;">,</span> <span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>credit<span style="color: #009900;">&#93;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;За что считать дегьги&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;SELECT NAME=tos&gt;
       &lt;OPTION VALUE=0<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>tos<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">0</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot; SELECTED&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot;&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;Не считать
       &lt;OPTION VALUE=1<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>tos<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">1</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot; SELECTED&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot;&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;За время
       &lt;OPTION VALUE=2<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>tos<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">2</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot; SELECTED&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot;&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;За трафик
       &lt;OPTION VALUE=3<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>tos<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">3</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot; SELECTED&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot;&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;За трафик + время
     &lt;/SELECT&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Снимать деньги с депозита&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;SELECT NAME=do_with_tos&gt;
       &lt;OPTION VALUE=0<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>do_with_tos<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">0</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot; SELECTED&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot;&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;Нет, только вести статистику
       &lt;OPTION VALUE=1<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>do_with_tos<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">1</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot; SELECTED&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot;&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;Снимать и проверять наличие
     &lt;/SELECT&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Какой трафик учитывать&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;SELECT NAME=direction&gt;
       &lt;OPTION VALUE=0<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>direction<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">0</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot; SELECTED&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot;&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;Не учитывать
       &lt;OPTION VALUE=1<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>direction<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">1</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot; SELECTED&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot;&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;Входящий
       &lt;OPTION VALUE=2<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>direction<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">2</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot; SELECTED&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot;&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;Исходящий
       &lt;OPTION VALUE=3<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>direction<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">3</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot; SELECTED&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot;&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;Суммарный
       &lt;OPTION VALUE=4<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>direction<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">4</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot; SELECTED&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot;&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;Больший
       &lt;OPTION VALUE=5<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>direction<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">5</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot; SELECTED&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot;&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;Меньший
     &lt;/SELECT&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Снимать фиксированную сумму&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;SELECT NAME=fixed&gt;
       &lt;OPTION VALUE=0<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>fixed<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">0</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot; SELECTED&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot;&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;Не снимать
       &lt;OPTION VALUE=1<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>fixed<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">1</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot; SELECTED&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot;&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;Раз в сутки, если было подключение
       &lt;OPTION VALUE=2<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>fixed<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">2</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot; SELECTED&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot;&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;Каждые сутки
       &lt;OPTION VALUE=3<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>fixed<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">3</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot; SELECTED&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot;&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;При каждом подключении
     &lt;/SELECT&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Фиксированная сумма&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=fixed_cost VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>fixed_cost<span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Блокирован по умолчанию&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=radio NAME=blocked VALUE=1<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>blocked<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">1</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot; CHECKED&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot;&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;Да&lt;INPUT TYPE=radio NAME=blocked VALUE=0<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>blocked<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">1</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot;&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot; CHECKED&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;Нет&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Активирован по умолчанию&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=radio NAME=activated VALUE=1<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>activated<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">1</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot; CHECKED&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot;&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;Да&lt;INPUT TYPE=radio NAME=activated VALUE=0<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>activated<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">1</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot;&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot; CHECKED&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;Нет&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Время активации&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=activation_time VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> sectime<span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;h:m:s&quot;</span><span style="color: #339933;">,</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>activation_time<span style="color: #009900;">&#93;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Общий лимит на время&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=total_time_limit VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> sectime<span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;h:m:s&quot;</span><span style="color: #339933;">,</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>total_time_limit<span style="color: #009900;">&#93;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Месячный лимит на время&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=month_time_limit VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> sectime<span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;h:m:s&quot;</span><span style="color: #339933;">,</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>month_time_limit<span style="color: #009900;">&#93;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Недельный лимит на время&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=week_time_limit VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> sectime<span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;h:m:s&quot;</span><span style="color: #339933;">,</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>week_time_limit<span style="color: #009900;">&#93;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Дневной лимит на время&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=day_time_limit VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> sectime<span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;h:m:s&quot;</span><span style="color: #339933;">,</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>day_time_limit<span style="color: #009900;">&#93;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Общий лимит на трафик (мб)&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=total_traffic_limit VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>total_traffic_limit<span style="color: #009900;">&#93;</span> <span style="color: #339933;">/</span> MBYTE<span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Месячный лимит на трафик (мб)&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=month_traffic_limit VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>month_traffic_limit<span style="color: #009900;">&#93;</span> <span style="color: #339933;">/</span> MBYTE<span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Недельный лимит на трафик (мб)&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=week_traffic_limit VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>week_traffic_limit<span style="color: #009900;">&#93;</span> <span style="color: #339933;">/</span> MBYTE<span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Дневной лимит на трафик (мб)&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=day_traffic_limit VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>day_traffic_limit<span style="color: #009900;">&#93;</span> <span style="color: #339933;">/</span> MBYTE<span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Общий лимит на деньги&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=total_money_limit VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #990000;">printf</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;<span style="color: #009933; font-weight: bold;">%.2f</span>&quot;</span><span style="color: #339933;">,</span> <span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>total_money_limit<span style="color: #009900;">&#93;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Месячный лимит на деньги&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=month_money_limit VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #990000;">printf</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;<span style="color: #009933; font-weight: bold;">%.2f</span>&quot;</span><span style="color: #339933;">,</span> <span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>month_money_limit<span style="color: #009900;">&#93;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Недельный лимит на деньги&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=week_money_limit VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #990000;">printf</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;<span style="color: #009933; font-weight: bold;">%.2f</span>&quot;</span><span style="color: #339933;">,</span> <span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>week_money_limit<span style="color: #009900;">&#93;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Дневной лимит на деньги&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=day_money_limit VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #990000;">printf</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;<span style="color: #009933; font-weight: bold;">%.2f</span>&quot;</span><span style="color: #339933;">,</span> <span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>day_money_limit<span style="color: #009900;">&#93;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Разрешенное время подключения&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=login_time VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>login_time<span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Имя списка разрешенных NAS&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=huntgroup_name VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>huntgroup_name<span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Одновременно подключений по одному логину&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=simultaneous_use VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>simultaneous_use<span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Одновременно портов с одним логином&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=port_limit VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>port_limit<span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Максимальное время сессии&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=session_timeout VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>session_timeout<span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Максимальное время простоя&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=idle_timeout VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>idle_timeout<span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Выделенный IP+&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=framed_ip VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>framed_ip<span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Выделенная маска&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=framed_mask VALUE=&quot;<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>framed_mask<span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Другие Reply пары&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=100 NAME=other_params VALUE='<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>other_params<span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>'&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Без пароля&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=radio NAME=no_pass VALUE=1<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>no_pass<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">1</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot; CHECKED&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot;&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;Да
        &lt;INPUT TYPE=radio NAME=no_pass VALUE=0<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>no_pass<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">1</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot;&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot; CHECKED&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span> &gt;Нет&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Без статистики&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=radio NAME=no_acct VALUE=1<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>no_acct<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">1</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot; CHECKED&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot;&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;Да&lt;INPUT TYPE=radio NAME=no_acct VALUE=0<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>no_acct<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">1</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot;&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot; CHECKED&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;Нет&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Разрешить callback&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=radio NAME=allow_callback VALUE=1<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>allow_callback<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">1</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot; CHECKED&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot;&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;Да&lt;INPUT TYPE=radio NAME=allow_callback VALUE=0<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>allow_callback<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">1</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot;&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot; CHECKED&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;Нет&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Создавать системного пользователя&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=radio NAME=create_system_user VALUE=1<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>create_system_user<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">1</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot; CHECKED&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot;&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;Да&lt;INPUT TYPE=radio NAME=create_system_user VALUE=0<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>create_system_user<span style="color: #009900;">&#93;</span> <span style="color: #339933;">==</span> <span style="color: #cc66cc;">1</span><span style="color: #009900;">&#41;</span> ? <span style="color: #0000ff;">&quot;&quot;</span> <span style="color: #339933;">:</span> <span style="color: #0000ff;">&quot; CHECKED&quot;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;Нет&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR BGCOLOR=&quot;#dddddd&quot;&gt;
     &lt;TD&gt;&lt;A onclick=&quot;return confirm('ВНИМАНИЕ!!! Все пользователи пакета `<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$packet</span><span style="color: #009900;">&#91;</span>packet<span style="color: #009900;">&#93;</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>\' и все данные\nоб их статистике будут БЕЗВОЗВРАТНО удалены!')&quot; HREF=real_del_packet.php?gid=<span style="color: #000000; font-weight: bold;">&lt;?</span> <span style="color: #b1b100;">echo</span> <span style="color: #000088;">$gid</span><span style="color: #339933;">;</span> <span style="color: #000000; font-weight: bold;">?&gt;</span>&gt;Удалить&lt;/A&gt;&lt;/TD&gt;
     &lt;TD ALIGN=right&gt;&lt;INPUT TYPE=submit VALUE=Принять&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;/TABLE&gt;
    &lt;/FORM&gt;</pre></td></tr></table><p class="theCode" style="display:none;">&lt;? include_once(&quot;utils.php&quot;); include_once(&quot;defines.php&quot;);?&gt;
    &lt;FORM ACTION=save_packet.php METHOD=POST&gt;
    &lt;INPUT TYPE=hidden NAME=gid VALUE=&quot;&lt;? echo $gid; ?&gt;&quot;&gt;
    &lt;TABLE CELLSPACING=2 CELLPADDING=4 BGCOLOR=black WIDTH=80%&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Название&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=packet VALUE=&quot;&lt;? echo $packet[packet]; ?&gt;&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Номер&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=2 NAME=num VALUE=&quot;&lt;? echo $packet[num]; ?&gt;&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Счет по умолчанию&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=deposit VALUE=&quot;&lt;? printf(&quot;%.2f&quot;, $packet[deposit]); ?&gt;&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Кредит по умолчанию&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=credit VALUE=&quot;&lt;? printf(&quot;%.2f&quot;, $packet[credit]); ?&gt;&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;За что считать дегьги&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;SELECT NAME=tos&gt;
       &lt;OPTION VALUE=0&lt;? echo ($packet[tos] == 0) ? &quot; SELECTED&quot; : &quot;&quot;; ?&gt;&gt;Не считать
       &lt;OPTION VALUE=1&lt;? echo ($packet[tos] == 1) ? &quot; SELECTED&quot; : &quot;&quot;; ?&gt;&gt;За время
       &lt;OPTION VALUE=2&lt;? echo ($packet[tos] == 2) ? &quot; SELECTED&quot; : &quot;&quot;; ?&gt;&gt;За трафик
       &lt;OPTION VALUE=3&lt;? echo ($packet[tos] == 3) ? &quot; SELECTED&quot; : &quot;&quot;; ?&gt;&gt;За трафик + время
     &lt;/SELECT&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Снимать деньги с депозита&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;SELECT NAME=do_with_tos&gt;
       &lt;OPTION VALUE=0&lt;? echo ($packet[do_with_tos] == 0) ? &quot; SELECTED&quot; : &quot;&quot;; ?&gt;&gt;Нет, только вести статистику
       &lt;OPTION VALUE=1&lt;? echo ($packet[do_with_tos] == 1) ? &quot; SELECTED&quot; : &quot;&quot;; ?&gt;&gt;Снимать и проверять наличие
     &lt;/SELECT&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Какой трафик учитывать&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;SELECT NAME=direction&gt;
       &lt;OPTION VALUE=0&lt;? echo ($packet[direction] == 0) ? &quot; SELECTED&quot; : &quot;&quot;; ?&gt;&gt;Не учитывать
       &lt;OPTION VALUE=1&lt;? echo ($packet[direction] == 1) ? &quot; SELECTED&quot; : &quot;&quot;; ?&gt;&gt;Входящий
       &lt;OPTION VALUE=2&lt;? echo ($packet[direction] == 2) ? &quot; SELECTED&quot; : &quot;&quot;; ?&gt;&gt;Исходящий
       &lt;OPTION VALUE=3&lt;? echo ($packet[direction] == 3) ? &quot; SELECTED&quot; : &quot;&quot;; ?&gt;&gt;Суммарный
       &lt;OPTION VALUE=4&lt;? echo ($packet[direction] == 4) ? &quot; SELECTED&quot; : &quot;&quot;; ?&gt;&gt;Больший
       &lt;OPTION VALUE=5&lt;? echo ($packet[direction] == 5) ? &quot; SELECTED&quot; : &quot;&quot;; ?&gt;&gt;Меньший
     &lt;/SELECT&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Снимать фиксированную сумму&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;SELECT NAME=fixed&gt;
       &lt;OPTION VALUE=0&lt;? echo ($packet[fixed] == 0) ? &quot; SELECTED&quot; : &quot;&quot;; ?&gt;&gt;Не снимать
       &lt;OPTION VALUE=1&lt;? echo ($packet[fixed] == 1) ? &quot; SELECTED&quot; : &quot;&quot;; ?&gt;&gt;Раз в сутки, если было подключение
       &lt;OPTION VALUE=2&lt;? echo ($packet[fixed] == 2) ? &quot; SELECTED&quot; : &quot;&quot;; ?&gt;&gt;Каждые сутки
       &lt;OPTION VALUE=3&lt;? echo ($packet[fixed] == 3) ? &quot; SELECTED&quot; : &quot;&quot;; ?&gt;&gt;При каждом подключении
     &lt;/SELECT&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Фиксированная сумма&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=fixed_cost VALUE=&quot;&lt;? echo $packet[fixed_cost]; ?&gt;&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Блокирован по умолчанию&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=radio NAME=blocked VALUE=1&lt;? echo ($packet[blocked] == 1) ? &quot; CHECKED&quot; : &quot;&quot;; ?&gt;&gt;Да&lt;INPUT TYPE=radio NAME=blocked VALUE=0&lt;? echo ($packet[blocked] == 1) ? &quot;&quot; : &quot; CHECKED&quot;; ?&gt;&gt;Нет&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Активирован по умолчанию&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=radio NAME=activated VALUE=1&lt;? echo ($packet[activated] == 1) ? &quot; CHECKED&quot; : &quot;&quot;; ?&gt;&gt;Да&lt;INPUT TYPE=radio NAME=activated VALUE=0&lt;? echo ($packet[activated] == 1) ? &quot;&quot; : &quot; CHECKED&quot;; ?&gt;&gt;Нет&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Время активации&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=activation_time VALUE=&quot;&lt;? echo sectime(&quot;h:m:s&quot;,$packet[activation_time]); ?&gt;&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Общий лимит на время&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=total_time_limit VALUE=&quot;&lt;? echo sectime(&quot;h:m:s&quot;,$packet[total_time_limit]); ?&gt;&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Месячный лимит на время&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=month_time_limit VALUE=&quot;&lt;? echo sectime(&quot;h:m:s&quot;,$packet[month_time_limit]); ?&gt;&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Недельный лимит на время&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=week_time_limit VALUE=&quot;&lt;? echo sectime(&quot;h:m:s&quot;,$packet[week_time_limit]); ?&gt;&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Дневной лимит на время&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=day_time_limit VALUE=&quot;&lt;? echo sectime(&quot;h:m:s&quot;,$packet[day_time_limit]); ?&gt;&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Общий лимит на трафик (мб)&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=total_traffic_limit VALUE=&quot;&lt;? echo ($packet[total_traffic_limit] / MBYTE); ?&gt;&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Месячный лимит на трафик (мб)&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=month_traffic_limit VALUE=&quot;&lt;? echo ($packet[month_traffic_limit] / MBYTE); ?&gt;&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Недельный лимит на трафик (мб)&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=week_traffic_limit VALUE=&quot;&lt;? echo ($packet[week_traffic_limit] / MBYTE); ?&gt;&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Дневной лимит на трафик (мб)&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=day_traffic_limit VALUE=&quot;&lt;? echo ($packet[day_traffic_limit] / MBYTE); ?&gt;&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Общий лимит на деньги&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=total_money_limit VALUE=&quot;&lt;? printf(&quot;%.2f&quot;, $packet[total_money_limit]); ?&gt;&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Месячный лимит на деньги&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=month_money_limit VALUE=&quot;&lt;? printf(&quot;%.2f&quot;, $packet[month_money_limit]); ?&gt;&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Недельный лимит на деньги&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=week_money_limit VALUE=&quot;&lt;? printf(&quot;%.2f&quot;, $packet[week_money_limit]); ?&gt;&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Дневной лимит на деньги&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=day_money_limit VALUE=&quot;&lt;? printf(&quot;%.2f&quot;, $packet[day_money_limit]); ?&gt;&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Разрешенное время подключения&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=login_time VALUE=&quot;&lt;? echo $packet[login_time]; ?&gt;&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Имя списка разрешенных NAS&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=huntgroup_name VALUE=&quot;&lt;? echo $packet[huntgroup_name]; ?&gt;&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Одновременно подключений по одному логину&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=simultaneous_use VALUE=&quot;&lt;? echo $packet[simultaneous_use]; ?&gt;&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Одновременно портов с одним логином&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=port_limit VALUE=&quot;&lt;? echo $packet[port_limit]; ?&gt;&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Максимальное время сессии&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=session_timeout VALUE=&quot;&lt;? echo $packet[session_timeout]; ?&gt;&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Максимальное время простоя&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=idle_timeout VALUE=&quot;&lt;? echo $packet[idle_timeout]; ?&gt;&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Выделенный IP+&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=framed_ip VALUE=&quot;&lt;? echo $packet[framed_ip]; ?&gt;&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Выделенная маска&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=20 NAME=framed_mask VALUE=&quot;&lt;? echo $packet[framed_mask]; ?&gt;&quot;&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Другие Reply пары&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=text SIZE=100 NAME=other_params VALUE='&lt;? echo $packet[other_params]; ?&gt;'&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Без пароля&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=radio NAME=no_pass VALUE=1&lt;? echo ($packet[no_pass] == 1) ? &quot; CHECKED&quot; : &quot;&quot;; ?&gt;&gt;Да
        &lt;INPUT TYPE=radio NAME=no_pass VALUE=0&lt;? echo ($packet[no_pass] == 1) ? &quot;&quot; : &quot; CHECKED&quot;; ?&gt; &gt;Нет&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Без статистики&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=radio NAME=no_acct VALUE=1&lt;? echo ($packet[no_acct] == 1) ? &quot; CHECKED&quot; : &quot;&quot;; ?&gt;&gt;Да&lt;INPUT TYPE=radio NAME=no_acct VALUE=0&lt;? echo ($packet[no_acct] == 1) ? &quot;&quot; : &quot; CHECKED&quot;; ?&gt;&gt;Нет&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Разрешить callback&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=radio NAME=allow_callback VALUE=1&lt;? echo ($packet[allow_callback] == 1) ? &quot; CHECKED&quot; : &quot;&quot;; ?&gt;&gt;Да&lt;INPUT TYPE=radio NAME=allow_callback VALUE=0&lt;? echo ($packet[allow_callback] == 1) ? &quot;&quot; : &quot; CHECKED&quot;; ?&gt;&gt;Нет&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR&gt;
     &lt;TD BGCOLOR=&quot;#99dd99&quot;&gt;Создавать системного пользователя&lt;/TD&gt;
     &lt;TD BGCOLOR=&quot;#dddd99&quot;&gt;&lt;INPUT TYPE=radio NAME=create_system_user VALUE=1&lt;? echo ($packet[create_system_user] == 1) ? &quot; CHECKED&quot; : &quot;&quot;; ?&gt;&gt;Да&lt;INPUT TYPE=radio NAME=create_system_user VALUE=0&lt;? echo ($packet[create_system_user] == 1) ? &quot;&quot; : &quot; CHECKED&quot;; ?&gt;&gt;Нет&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;TR BGCOLOR=&quot;#dddddd&quot;&gt;
     &lt;TD&gt;&lt;A onclick=&quot;return confirm('ВНИМАНИЕ!!! Все пользователи пакета `&lt;? echo $packet[packet]; ?&gt;\' и все данные\nоб их статистике будут БЕЗВОЗВРАТНО удалены!')&quot; HREF=real_del_packet.php?gid=&lt;? echo $gid; ?&gt;&gt;Удалить&lt;/A&gt;&lt;/TD&gt;
     &lt;TD ALIGN=right&gt;&lt;INPUT TYPE=submit VALUE=Принять&gt;&lt;/TD&gt;
    &lt;/TR&gt;
    &lt;/TABLE&gt;
    &lt;/FORM&gt;</p></div>
    ";}
categories:
  - billing
  - FreeNIBS

---
edit\_packet\_menu.php — cкрипт для FreeNIBS, который изменяет пакет пользователя<!--more-->

<pre lang="php"><? include_once("utils.php"); include_once("defines.php");?>
&lt;FORM ACTION=save_packet.php METHOD=POST>
&lt;INPUT TYPE=hidden NAME=gid VALUE="

<? echo $gid; ?>">
&lt;TABLE CELLSPACING=2 CELLPADDING=4 BGCOLOR=black WIDTH=80%>


<TR>
  <TD BGCOLOR="#99dd99">
    Название
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=20 NAME=packet VALUE="<? echo $packet[packet]; ?>">
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Номер
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=2 NAME=num VALUE="<? echo $packet[num]; ?>">
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Счет по умолчанию
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=20 NAME=deposit VALUE="<? printf("%.2f", $packet[deposit]); ?>">
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Кредит по умолчанию
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=20 NAME=credit VALUE="<? printf("%.2f", $packet[credit]); ?>">
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    За что считать дегьги
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;SELECT NAME=tos>
       &lt;OPTION VALUE=0<? echo ($packet[tos] == 0) ? " SELECTED" : ""; ?>>Не считать
       &lt;OPTION VALUE=1
    
    <? echo ($packet[tos] == 1) ? " SELECTED" : ""; ?>>За время
       &lt;OPTION VALUE=2
    
    <? echo ($packet[tos] == 2) ? " SELECTED" : ""; ?>>За трафик
       &lt;OPTION VALUE=3
    
    <? echo ($packet[tos] == 3) ? " SELECTED" : ""; ?>>За трафик + время
     &lt;/SELECT>
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Снимать деньги с депозита
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;SELECT NAME=do_with_tos>
       &lt;OPTION VALUE=0<? echo ($packet[do_with_tos] == 0) ? " SELECTED" : ""; ?>>Нет, только вести статистику
       &lt;OPTION VALUE=1
    
    <? echo ($packet[do_with_tos] == 1) ? " SELECTED" : ""; ?>>Снимать и проверять наличие
     &lt;/SELECT>
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Какой трафик учитывать
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;SELECT NAME=direction>
       &lt;OPTION VALUE=0<? echo ($packet[direction] == 0) ? " SELECTED" : ""; ?>>Не учитывать
       &lt;OPTION VALUE=1
    
    <? echo ($packet[direction] == 1) ? " SELECTED" : ""; ?>>Входящий
       &lt;OPTION VALUE=2
    
    <? echo ($packet[direction] == 2) ? " SELECTED" : ""; ?>>Исходящий
       &lt;OPTION VALUE=3
    
    <? echo ($packet[direction] == 3) ? " SELECTED" : ""; ?>>Суммарный
       &lt;OPTION VALUE=4
    
    <? echo ($packet[direction] == 4) ? " SELECTED" : ""; ?>>Больший
       &lt;OPTION VALUE=5
    
    <? echo ($packet[direction] == 5) ? " SELECTED" : ""; ?>>Меньший
     &lt;/SELECT>
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Снимать фиксированную сумму
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;SELECT NAME=fixed>
       &lt;OPTION VALUE=0<? echo ($packet[fixed] == 0) ? " SELECTED" : ""; ?>>Не снимать
       &lt;OPTION VALUE=1
    
    <? echo ($packet[fixed] == 1) ? " SELECTED" : ""; ?>>Раз в сутки, если было подключение
       &lt;OPTION VALUE=2
    
    <? echo ($packet[fixed] == 2) ? " SELECTED" : ""; ?>>Каждые сутки
       &lt;OPTION VALUE=3
    
    <? echo ($packet[fixed] == 3) ? " SELECTED" : ""; ?>>При каждом подключении
     &lt;/SELECT>
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Фиксированная сумма
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=20 NAME=fixed_cost VALUE="<? echo $packet[fixed_cost]; ?>">
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Блокирован по умолчанию
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=radio NAME=blocked VALUE=1<? echo ($packet[blocked] == 1) ? " CHECKED" : ""; ?>>Да&lt;INPUT TYPE=radio NAME=blocked VALUE=0
    
    <? echo ($packet[blocked] == 1) ? "" : " CHECKED"; ?>>Нет
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Активирован по умолчанию
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=radio NAME=activated VALUE=1<? echo ($packet[activated] == 1) ? " CHECKED" : ""; ?>>Да&lt;INPUT TYPE=radio NAME=activated VALUE=0
    
    <? echo ($packet[activated] == 1) ? "" : " CHECKED"; ?>>Нет
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Время активации
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=20 NAME=activation_time VALUE="<? echo sectime("h:m:s",$packet[activation_time]); ?>">
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Общий лимит на время
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=20 NAME=total_time_limit VALUE="<? echo sectime("h:m:s",$packet[total_time_limit]); ?>">
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Месячный лимит на время
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=20 NAME=month_time_limit VALUE="<? echo sectime("h:m:s",$packet[month_time_limit]); ?>">
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Недельный лимит на время
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=20 NAME=week_time_limit VALUE="<? echo sectime("h:m:s",$packet[week_time_limit]); ?>">
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Дневной лимит на время
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=20 NAME=day_time_limit VALUE="<? echo sectime("h:m:s",$packet[day_time_limit]); ?>">
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Общий лимит на трафик (мб)
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=20 NAME=total_traffic_limit VALUE="<? echo ($packet[total_traffic_limit] / MBYTE); ?>">
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Месячный лимит на трафик (мб)
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=20 NAME=month_traffic_limit VALUE="<? echo ($packet[month_traffic_limit] / MBYTE); ?>">
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Недельный лимит на трафик (мб)
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=20 NAME=week_traffic_limit VALUE="<? echo ($packet[week_traffic_limit] / MBYTE); ?>">
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Дневной лимит на трафик (мб)
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=20 NAME=day_traffic_limit VALUE="<? echo ($packet[day_traffic_limit] / MBYTE); ?>">
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Общий лимит на деньги
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=20 NAME=total_money_limit VALUE="<? printf("%.2f", $packet[total_money_limit]); ?>">
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Месячный лимит на деньги
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=20 NAME=month_money_limit VALUE="<? printf("%.2f", $packet[month_money_limit]); ?>">
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Недельный лимит на деньги
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=20 NAME=week_money_limit VALUE="<? printf("%.2f", $packet[week_money_limit]); ?>">
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Дневной лимит на деньги
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=20 NAME=day_money_limit VALUE="<? printf("%.2f", $packet[day_money_limit]); ?>">
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Разрешенное время подключения
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=20 NAME=login_time VALUE="<? echo $packet[login_time]; ?>">
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Имя списка разрешенных NAS
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=20 NAME=huntgroup_name VALUE="<? echo $packet[huntgroup_name]; ?>">
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Одновременно подключений по одному логину
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=20 NAME=simultaneous_use VALUE="<? echo $packet[simultaneous_use]; ?>">
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Одновременно портов с одним логином
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=20 NAME=port_limit VALUE="<? echo $packet[port_limit]; ?>">
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Максимальное время сессии
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=20 NAME=session_timeout VALUE="<? echo $packet[session_timeout]; ?>">
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Максимальное время простоя
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=20 NAME=idle_timeout VALUE="<? echo $packet[idle_timeout]; ?>">
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Выделенный IP+
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=20 NAME=framed_ip VALUE="<? echo $packet[framed_ip]; ?>">
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Выделенная маска
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=20 NAME=framed_mask VALUE="<? echo $packet[framed_mask]; ?>">
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Другие Reply пары
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=text SIZE=100 NAME=other_params VALUE='<? echo $packet[other_params]; ?>'>
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Без пароля
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=radio NAME=no_pass VALUE=1<? echo ($packet[no_pass] == 1) ? " CHECKED" : ""; ?>>Да
        &lt;INPUT TYPE=radio NAME=no_pass VALUE=0
    
    <? echo ($packet[no_pass] == 1) ? "" : " CHECKED"; ?> >Нет
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Без статистики
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=radio NAME=no_acct VALUE=1<? echo ($packet[no_acct] == 1) ? " CHECKED" : ""; ?>>Да&lt;INPUT TYPE=radio NAME=no_acct VALUE=0
    
    <? echo ($packet[no_acct] == 1) ? "" : " CHECKED"; ?>>Нет
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Разрешить callback
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=radio NAME=allow_callback VALUE=1<? echo ($packet[allow_callback] == 1) ? " CHECKED" : ""; ?>>Да&lt;INPUT TYPE=radio NAME=allow_callback VALUE=0
    
    <? echo ($packet[allow_callback] == 1) ? "" : " CHECKED"; ?>>Нет
  </TD>
  
</TR>


<TR>
  <TD BGCOLOR="#99dd99">
    Создавать системного пользователя
  </TD>
   
  
  <TD BGCOLOR="#dddd99">
    &lt;INPUT TYPE=radio NAME=create_system_user VALUE=1<? echo ($packet[create_system_user] == 1) ? " CHECKED" : ""; ?>>Да&lt;INPUT TYPE=radio NAME=create_system_user VALUE=0
    
    <? echo ($packet[create_system_user] == 1) ? "" : " CHECKED"; ?>>Нет
  </TD>
  
</TR>


<TR BGCOLOR="#dddddd">
  <TD>
    &lt;A onclick="return confirm('ВНИМАНИЕ!!! Все пользователи пакета `<? echo $packet[packet]; ?>\' и все данные\nоб их статистике будут БЕЗВОЗВРАТНО удалены!')" HREF=real_del_packet.php?gid=
    
    <? echo $gid; ?>>Удалить&lt;/A>
  </TD>
   &lt;TD ALIGN=right>&lt;INPUT TYPE=submit VALUE=Принять>&lt;/TD>
  
</TR>
&lt;/TABLE>
&lt;/FORM>

</pre>