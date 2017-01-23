---
title: 'Биллинговая система (billing system) 2011 &#8212; Эволюция систем учета трафика в Интернет за 6-ть лет'
author: wel
type: post
date: 2011-01-17T11:29:27+00:00
url: /billing/биллинговая-система-billing-system-2011-эволюция-си
short-url:
  - http://bit.ly/hAKgda
wp-syntax-cache-content:
  - |
    a:4:{i:1;s:1662:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="bash" style="font-family:monospace;"><span style="color: #666666; font-style: italic;">#/usr/local/sbin/radiusd -v</span>
    radiusd: FreeRADIUS Version 1.1.0, <span style="color: #000000; font-weight: bold;">for</span> host , built on Apr <span style="color: #000000;">27</span> <span style="color: #000000;">2007</span> at 01:<span style="color: #000000;">50</span>:<span style="color: #000000;">14</span>
    Copyright <span style="color: #7a0874; font-weight: bold;">&#40;</span>C<span style="color: #7a0874; font-weight: bold;">&#41;</span> <span style="color: #000000;">2000</span>-<span style="color: #000000;">2003</span> The FreeRADIUS server project.
    There is NO warranty; not even <span style="color: #000000; font-weight: bold;">for</span> MERCHANTABILITY or FITNESS FOR A
    PARTICULAR PURPOSE.
    You may redistribute copies of FreeRADIUS under the terms of the
    GNU General Public License.
    For <span style="color: #c20cb9; font-weight: bold;">more</span> information about these matters, see the <span style="color: #c20cb9; font-weight: bold;">file</span> named COPYRIGHT.</pre></td></tr></table><p class="theCode" style="display:none;">#/usr/local/sbin/radiusd -v
    radiusd: FreeRADIUS Version 1.1.0, for host , built on Apr 27 2007 at 01:50:14
    Copyright (C) 2000-2003 The FreeRADIUS server project.
    There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
    PARTICULAR PURPOSE.
    You may redistribute copies of FreeRADIUS under the terms of the
    GNU General Public License.
    For more information about these matters, see the file named COPYRIGHT.</p></div>
    ";i:2;s:2251:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="bash" style="font-family:monospace;"><span style="color: #666666; font-style: italic;">#ls -la</span>
    total <span style="color: #000000;">16</span>
    drwxr-xr-x   <span style="color: #000000;">7</span> root  wheel   <span style="color: #000000;">512</span> Apr <span style="color: #000000;">25</span>  <span style="color: #000000;">2007</span> .
    drwxr-xr-x  <span style="color: #000000;">39</span> root  wheel  <span style="color: #000000;">2560</span> Dec  <span style="color: #000000;">5</span> <span style="color: #000000;">11</span>:<span style="color: #000000;">37</span> ..
    drwxr-xr-x  <span style="color: #000000;">11</span> root  wheel   <span style="color: #000000;">512</span> Apr <span style="color: #000000;">25</span>  <span style="color: #000000;">2007</span> 1.1.9_radius1.1.0
    drwxr-xr-x  <span style="color: #000000;">10</span> root  wheel   <span style="color: #000000;">512</span> Apr <span style="color: #000000;">25</span>  <span style="color: #000000;">2007</span> 1.1.9_radius1.1.1
    drwxr-xr-x  <span style="color: #000000;">11</span> root  wheel   <span style="color: #000000;">512</span> Apr <span style="color: #000000;">25</span>  <span style="color: #000000;">2007</span> 1.1.9_radius1.1.4
    drwxr-xr-x  <span style="color: #000000;">12</span> root  wheel   <span style="color: #000000;">512</span> Apr <span style="color: #000000;">24</span>  <span style="color: #000000;">2007</span> 2.2.0_radius1.1.4
    drwxr-xr-x  <span style="color: #000000;">12</span> root  wheel   <span style="color: #000000;">512</span> Apr <span style="color: #000000;">24</span>  <span style="color: #000000;">2007</span> 3.0.0.b3_radius1.1.4</pre></td></tr></table><p class="theCode" style="display:none;">#ls -la
    total 16
    drwxr-xr-x   7 root  wheel   512 Apr 25  2007 .
    drwxr-xr-x  39 root  wheel  2560 Dec  5 11:37 ..
    drwxr-xr-x  11 root  wheel   512 Apr 25  2007 1.1.9_radius1.1.0
    drwxr-xr-x  10 root  wheel   512 Apr 25  2007 1.1.9_radius1.1.1
    drwxr-xr-x  11 root  wheel   512 Apr 25  2007 1.1.9_radius1.1.4
    drwxr-xr-x  12 root  wheel   512 Apr 24  2007 2.2.0_radius1.1.4
    drwxr-xr-x  12 root  wheel   512 Apr 24  2007 3.0.0.b3_radius1.1.4</p></div>
    ";i:3;s:3265:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="bash" style="font-family:monospace;"><span style="color: #666666; font-style: italic;">#fdisk</span>
    <span style="color: #000000; font-weight: bold;">*******</span> Working on device <span style="color: #000000; font-weight: bold;">/</span>dev<span style="color: #000000; font-weight: bold;">/</span>ad8 <span style="color: #000000; font-weight: bold;">*******</span>
    parameters extracted from in-core disklabel are:
    <span style="color: #007800;">cylinders</span>=<span style="color: #000000;">155061</span> <span style="color: #007800;">heads</span>=<span style="color: #000000;">16</span> sectors<span style="color: #000000; font-weight: bold;">/</span><span style="color: #007800;">track</span>=<span style="color: #000000;">63</span> <span style="color: #7a0874; font-weight: bold;">&#40;</span><span style="color: #000000;">1008</span> blks<span style="color: #000000; font-weight: bold;">/</span>cyl<span style="color: #7a0874; font-weight: bold;">&#41;</span>
    &nbsp;
    Figures below won<span style="color: #ff0000;">'t work with BIOS for partitions not in cyl 1
    parameters to be used for BIOS calculations are:
    cylinders=155061 heads=16 sectors/track=63 (1008 blks/cyl)
    &nbsp;
    Media sector size is 512
    Warning: BIOS sector numbering starts with sector 1
    Information from DOS bootblock is:
    The data for partition 1 is:
    sysid 165 (0xa5),(FreeBSD/NetBSD/386BSD)
        start 63, size 1044162 (509 Meg), flag 0
            beg: cyl 0/ head 1/ sector 1;
            end: cyl 64/ head 254/ sector 63
    The data for partition 2 is:
    sysid 165 (0xa5),(FreeBSD/NetBSD/386BSD)
        start 1044225, size 71665965 (34993 Meg), flag 80 (active)
            beg: cyl 65/ head 0/ sector 1;
            end: cyl 1023/ head 254/ sector 63
    The data for partition 3 is:
    sysid 165 (0xa5),(FreeBSD/NetBSD/386BSD)
        start 72710190, size 83586195 (40813 Meg), flag 0
            beg: cyl 1023/ head 255/ sector 63;
            end: cyl 1023/ head 254/ sector 63
    The data for partition 4 is:
    &lt;UNUSED&gt;</span></pre></td></tr></table><p class="theCode" style="display:none;">#fdisk
    ******* Working on device /dev/ad8 *******
    parameters extracted from in-core disklabel are:
    cylinders=155061 heads=16 sectors/track=63 (1008 blks/cyl)
    
    Figures below won't work with BIOS for partitions not in cyl 1
    parameters to be used for BIOS calculations are:
    cylinders=155061 heads=16 sectors/track=63 (1008 blks/cyl)
    
    Media sector size is 512
    Warning: BIOS sector numbering starts with sector 1
    Information from DOS bootblock is:
    The data for partition 1 is:
    sysid 165 (0xa5),(FreeBSD/NetBSD/386BSD)
        start 63, size 1044162 (509 Meg), flag 0
            beg: cyl 0/ head 1/ sector 1;
            end: cyl 64/ head 254/ sector 63
    The data for partition 2 is:
    sysid 165 (0xa5),(FreeBSD/NetBSD/386BSD)
        start 1044225, size 71665965 (34993 Meg), flag 80 (active)
            beg: cyl 65/ head 0/ sector 1;
            end: cyl 1023/ head 254/ sector 63
    The data for partition 3 is:
    sysid 165 (0xa5),(FreeBSD/NetBSD/386BSD)
        start 72710190, size 83586195 (40813 Meg), flag 0
            beg: cyl 1023/ head 255/ sector 63;
            end: cyl 1023/ head 254/ sector 63
    The data for partition 4 is:
    &lt;UNUSED&gt;</p></div>
    ";i:4;s:318:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="cpp" style="font-family:monospace;">USER_NT_HASH
    USER_LM_HASH
    RESULT<span style="color: #008080;">:</span>UNDEF</pre></td></tr></table><p class="theCode" style="display:none;">USER_NT_HASH
    USER_LM_HASH
    RESULT:UNDEF</p></div>
    ";}
categories:
  - billing
tags:
  - freebsd
  - freeNIBS
  - freeradius
  - mpd
  - netflow

---
# Биллинговая система 2011 &#8212; Эволюция систем учета трафика в Интернет за 6-ть лет

Короткие и логичные выводы по пунктам в конце, а сейчас рок-н-ролл)))

## 2005-2006 время FreeNIBS )))

Сказать по правде с FreeNIBS Я очень долго мучался пока не запустил биллинг, а для этого Я походил по всем возможным граблям и невозможным(то есть Я их сам сочинил))).

**В 2006-2008 году:** Мы еще сидели на 64-128Кбитных безлимитных пакетах (сладкие безлимы))), причём большая часть людей на помегабайтном тарифе (помегабайтке). Биллинговая типичного провайдера состояла из пресловутых FreeBSD или Linux или же Windows Server у крутых парней был Solaris :).
   
Но потом всё резко начало меняться&#8230;
  
<!--more-->


  
В том же 2008 году стало ясно, что &#171;умные&#187; (а вообще &#8212; управляемые свичи) рулят!
  
На тот момент пошёл отток б/у Cisco, ZyXel, Planet, 3COM, etc. На лице появлялась улыбка &#8212; Вот ОНО, СЧАСТЬЕ на нашей улице!!! Монтажники в робах тягали оптику, сварочный аппарат для &#171;оптики&#187; уже не был в диковинку, а некоторые на этом начали подниматься. Хотя всё еще кто-то использовал переходники на оптику без пайки 😉
  
Нам казалась, что настал золотой век провайдеров)))
  
Цены резко упали вниз и в 2008 году доступно было ЦЕЛЫХ 256Кбит/с простым украинцем.
  
Я использовал всё это время на своём стареньком сервере Целероне 1.6 512МБ FreeBSD 6.0 потом FreeBSD 6.2 и FreeRadius 1.1.0 + FreeNIBS 1.x. Дальше сервера доступа и биллинговый сервер &#8212; разделились, вот он [мой брас на freeBSD 7.2][1]

### Прикол со старой freeNibs 1.x и новой версией FreeNIBS 2.x

Итак у Меня сейчас FreeNIBS интегрированный в FreeRADIUS 1.1.0 а собран аж в апреле 2007 года.

<pre lang="bash">#/usr/local/sbin/radiusd -v
radiusd: FreeRADIUS Version 1.1.0, for host , built on Apr 27 2007 at 01:50:14
Copyright (C) 2000-2003 The FreeRADIUS server project.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.
You may redistribute copies of FreeRADIUS under the terms of the
GNU General Public License.
For more information about these matters, see the file named COPYRIGHT.
</pre>

Дело в том, что Я на радостях собрал FreeNIBS 2.0.x, прикрутил &#171;новый&#187; интерфейс и уехал. Но Мне начал звонить директор, дескать: &#171;Что Ты наделал? Людям деньги снимает по 100-200 грн за сессию!!!&#187; В общем Я промучался 3-и часа и так и не выяснил почему такая лажа. было решено, что сервер просто напросто откатится на FreeNIBS первой ветки. Но боже мой Я совсем забыл какой FreeNIBS Я накатывал на какой FreeRADIUS.
  
В общем с горем пополам на 9-ти или более вариациях Я закончил под утро. Лёг спать, а потом в ужасе не смог найти какой из вариантов Я засетапил)))

<pre lang="bash">#ls -la
total 16
drwxr-xr-x   7 root  wheel   512 Apr 25  2007 .
drwxr-xr-x  39 root  wheel  2560 Dec  5 11:37 ..
drwxr-xr-x  11 root  wheel   512 Apr 25  2007 1.1.9_radius1.1.0
drwxr-xr-x  10 root  wheel   512 Apr 25  2007 1.1.9_radius1.1.1
drwxr-xr-x  11 root  wheel   512 Apr 25  2007 1.1.9_radius1.1.4
drwxr-xr-x  12 root  wheel   512 Apr 24  2007 2.2.0_radius1.1.4
drwxr-xr-x  12 root  wheel   512 Apr 24  2007 3.0.0.b3_radius1.1.4

</pre>

В общем Я скрупулёзно копировал данные папки периодически Себе на винт &#8212; переодически)))

Потом с винта 6.2Гбайта в 2008 году Я перенёс на 30+Gb винт с помощью dump+restore.

<pre lang="bash">#fdisk
******* Working on device /dev/ad8 *******
parameters extracted from in-core disklabel are:
cylinders=155061 heads=16 sectors/track=63 (1008 blks/cyl)

Figures below won't work with BIOS for partitions not in cyl 1
parameters to be used for BIOS calculations are:
cylinders=155061 heads=16 sectors/track=63 (1008 blks/cyl)

Media sector size is 512
Warning: BIOS sector numbering starts with sector 1
Information from DOS bootblock is:
The data for partition 1 is:
sysid 165 (0xa5),(FreeBSD/NetBSD/386BSD)
    start 63, size 1044162 (509 Meg), flag 0
        beg: cyl 0/ head 1/ sector 1;
        end: cyl 64/ head 254/ sector 63
The data for partition 2 is:
sysid 165 (0xa5),(FreeBSD/NetBSD/386BSD)
    start 1044225, size 71665965 (34993 Meg), flag 80 (active)
        beg: cyl 65/ head 0/ sector 1;
        end: cyl 1023/ head 254/ sector 63
The data for partition 3 is:
sysid 165 (0xa5),(FreeBSD/NetBSD/386BSD)
    start 72710190, size 83586195 (40813 Meg), flag 0
        beg: cyl 1023/ head 255/ sector 63;
        end: cyl 1023/ head 254/ sector 63
The data for partition 4 is:
&lt;UNUSED>
</pre>

**За 2008-2009** год скорость увеличилась с 256Кбит/с до 10Мбит/с.
  
Я, нет &#8212; мой старый Целерон вздохнул с облегчением, когда Я вынес на новенький Атлон 4600++ + настоящая сетевай карта Intel Desctop PRO Gigabit)))
  
Теперь у Меня гемора стала в 2-а раза больше, пока Я не освоил загрузку FreeBSD без зависимости от названия раздела.
  
Правда Я часто когда был в отъезде говорил по телефону, что печатать &#8212; а Мне говорили результат &#8212; так и восстанавливали очень жестокие сбои подачи электричества)))

В общем IP KVM switch &#8212; это весчь)))
  
**В 2008-2009-ом году Мне сильно поднадоела FreeNIBS** &#8212; переписывать веб-интерфейс Я не хотел, так как Меня беспокоил падающий радиус, не обновлённая FreeBSD до 6.3, а потом и 6.4 и не радужные перспективы если это всё не запуститься, а Я за 400км и без бекапов. 

### Время NetFlow

**Я решил всё переписать используя netflow**. Взял С++ библиотеку для mysql, хранимые процедуры mysql 5.0.x и начал пытаться. Создал логику и всё такое. Но потом Я обнаружил, что труЪ способ снятия netflow прямо с нод mpd4.4 у Меня не заработал, и даже на mpd5.0 )))
  
Я отложил все эти потуги и забил. Я еще пытался написать биллинг под FreeRADIUS. Так же пытался проинсталить или найти нормальный биллинг. Всё Мне попадалось что-то &#171;не то&#187;)))

Уже после выхода mpd5.1 Я с радостью обнаружил работающую функцию экспорта NetFlow потока. Я подвесил сенсор и ждал, пока сервер пару раз не завис. Я сказал ХМ&#8230;
  
Я посчитал скорость роста траффика, и количество И/О операций. Так же Я сделал тестовый скрипт,который &#171;расчитывал траффик и снимал деньги&#187;. В общем Я был огорчён &#8212; Нетфлоу был настолько &#171;тяжёлым&#187; &#8212; до безобразия. Я еще удивлялся как у знакомого на сетке в 3-и раза больше не дохнет сервак. Как потом оказалось его КСЕОНЫ дохли раз за разом ))) Он еще в РРРtP соеденении считал отдельно локалку+инет безлимитный)))

**В 2009-2010** Я несколько раз пробовал abills, но Меня тошнило от пёрла.
  
С выходом новой фичи для Меня в mpd5.2 ext acc Я захотел реализовать биллинг средствами скриптов.
  
<a rel="nofollow" href="https://sourceforge.net/projects/mpd/forums/forum/44692/topic/3036343">mpd 5 External authentication</a> как было сказано надо выдавать:

<pre lang="cpp">USER_NT_HASH
USER_LM_HASH
RESULT:UNDEF
</pre>

Я помыкался, поискал как это сделано в abills&#8217;е и забил)))
  
Замаячила возможная продажа моей любимой сети)))

Я работать стал в еще одной сети. На написание костылей времени не было.
  
**Потом летом 2010** Я решил сделать свой биллинг на FreeRADIUS&#8217;e.
  
В принципе Я относительно быстро на последнем 2.х радиусе поднял сервер. Дальше Я подруби его к mpd 5.5 на freeBSD 7.2 и сделал небольшой PPTP/PPPoE сервер. начал писать морду.
  
А потом стало реально понятно, что Мы будем скоро проданы в рабство &#8212; так Я и забросил написание биллинга)))

## Выводы

За 6-ть лет траффик шагнул, да нет &#8212; взлетел на реактивной ракете просто на невероятные высоты. С помегабайтного Интернета с общей скоростью на 50 человек 64Кбит/с до 240Мбит/сек с динамическим шейпингом в зависимости от нагрузки канала и пределом в 100Мбит/с.

Биллинг как прилип изначально FreeNIBS &#8212; так Я им и пользовался на FreeBSD, хоть и железо было &#8212; обычный старый компьютер, хоть жесткий диск &#8212; был с бедами, хоть электричество отключали и потом до часу беды фиксились. Не останавливало то, что было переполнение 32bit-ых counter-ов и трафик больше 4-х Гбайт обнулялся &#8212; Я костылём пофиксил)))

В итоге Я реализовал FreeRadius + ipfw redirect на nginx, реализовал динамический шейпинг в зависимости от нагрузки. А всего-лишь навсего надо было победить в Себе лень и не мучаться со всем этим старьём)))

## Будущее

Мы все знаем, что IPv4 доживает свой час.
  
Что траффик считать &#8212; неприлично, легче дать реальный ИП-к.
  
НАТить &#8212; позорно, ибо сервера больше перенапрягаются.
  
И тем не менее будущее росийчких провайдеров с СОРМ-ом не сильно прельщает.
  
Так же бешеный рост траффика просто поражает))) Мы &#171;кору&#187; меняли несколько раз, а &#171;Им все мало&#187;)))
  
И это не учитывая, что у пользователей 10/100Мбит последней мили и 10-40% торрент трафика оседает в сети провайдера.
  
[Дрели и шлифмашины][2]

 [1]: http://wel.org.ua/lang/bras-на-freebsd-freenibs
 [2]: http://electrobrand.ru/index.php