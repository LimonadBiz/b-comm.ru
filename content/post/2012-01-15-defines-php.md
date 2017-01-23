---
title: defines.php
author: wel
type: post
date: 2012-01-14T23:38:24+00:00
url: /billing/defines-php
wp-syntax-cache-content:
  - |
    a:1:{i:1;s:28766:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="php" style="font-family:monospace;"><span style="color: #000000; font-weight: bold;">&lt;?</span>
    <span style="color: #990000;">define</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;BEZLIM_TABLE&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;bezlimit2&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #666666; font-style: italic;">// Также проверьте настройки в mysql.php</span>
    &nbsp;
    <span style="color: #666666; font-style: italic;">// Администратор, от имени которого происходят все изменения</span>
    <span style="color: #666666; font-style: italic;">// Имеет значения только в том случае, если не используется</span>
    <span style="color: #666666; font-style: italic;">// авторизация сервером</span>
    <span style="color: #990000;">define</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;ADMIN_USER&quot;</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">&quot;admin&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #666666; font-style: italic;">// Количество байт в мегабайте (иногда требуется 1000000)</span>
    <span style="color: #990000;">define</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;MBYTE&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;1048576&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #666666; font-style: italic;">// Если настроен sudo то перегружать radiusd</span>
    <span style="color: #666666; font-style: italic;">// при изменениях в пакетах и прайсах</span>
    <span style="color: #666666; font-style: italic;">// sudo настроить так: в файл /etc/sudoers добавить строку</span>
    <span style="color: #666666; font-style: italic;">// apache  ALL= NOPASSWD: ALL</span>
    <span style="color: #666666; font-style: italic;">// Соответственно apache это пользователь, от которого запущен WEB сервер</span>
    <span style="color: #990000;">define</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;SUDO_RADRELOAD&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;1&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #666666; font-style: italic;">// Настройки логирования</span>
    <span style="color: #666666; font-style: italic;">// Для корректной работы создайте файл NIBS_LOG_FILE в ручную</span>
    <span style="color: #666666; font-style: italic;">// и разрешите запись в него пользователю от которого</span>
    <span style="color: #666666; font-style: italic;">// запущен WEB сервер (в основном apache)</span>
    <span style="color: #990000;">define</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;NIBS_DO_LOG&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;1&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #990000;">define</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;NIBS_LOG_FILE&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;webnibs.log&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #666666; font-style: italic;">// Создавать пользователя в системе (см. extern.php)</span>
    <span style="color: #666666; font-style: italic;">// требует настройку sudo</span>
    <span style="color: #666666; font-style: italic;">// по умолчанию добавляет в группу raduser которую надо создать вручную</span>
    <span style="color: #666666; font-style: italic;">// домашний каталог ставит /home/users/$user (создать в /home подкаталог users</span>
    <span style="color: #666666; font-style: italic;">// скелет берет в /etc/skel_ppp (создать /etc/skel_ppp и в</span>
    <span style="color: #666666; font-style: italic;">// /etc/skel_ppp всего один подкаталог - html)</span>
    <span style="color: #666666; font-style: italic;">// пытается включить квоты: 2мб /home и 10мб /var</span>
    <span style="color: #990000;">define</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;CREATE_SYSTEM&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;0&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #666666; font-style: italic;">// Использовать карточную пристройку</span>
    <span style="color: #990000;">define</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;USE_CARDS&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;1&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #666666; font-style: italic;">// Активировать меню рассылки</span>
    <span style="color: #666666; font-style: italic;">// ОБЯЗАТЕЛЬНО настройте ниже MAIL_DOMAIN и COMPANY_NAME</span>
    <span style="color: #990000;">define</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;DELIVERY&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;1&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #666666; font-style: italic;">// Пока не реализованно</span>
    <span style="color: #990000;">define</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;PROF_MODE&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;0&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #666666; font-style: italic;">// Работа с почтовой базой postfix (см. extern.php)</span>
    <span style="color: #990000;">define</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;CREATE_POSTFIX_MAIL&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;0&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #990000;">define</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;MAIL_BASE&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;/var/spool/mail/virtual&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #990000;">define</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;MAIL_DOMAIN&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;your.domain&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #990000;">define</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;COMPANY_NAME&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;your.company&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #666666; font-style: italic;">// --- Остальное ---</span>
    <span style="color: #666666; font-style: italic;">// Цвет фона</span>
    <span style="color: #990000;">define</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;BGCOLOR&quot;</span><span style="color: #339933;">,</span><span style="color: #0000ff;">&quot;ddddff&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #666666; font-style: italic;">// Массив для привязки номеров телефонов к портам</span>
    <span style="color: #666666; font-style: italic;">// Удобно если NAS не посылает call_from</span>
    <span style="color: #000088;">$tel_nums</span><span style="color: #339933;">=</span><span style="color: #990000;">array</span><span style="color: #009900;">&#40;</span>
      <span style="color: #0000ff;">'0'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'LOCAL'</span><span style="color: #339933;">,</span>
      <span style="color: #0000ff;">'1'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'177-421'</span><span style="color: #339933;">,</span>
      <span style="color: #0000ff;">'2'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'177-422'</span><span style="color: #339933;">,</span>
      <span style="color: #0000ff;">'3'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'177-423'</span><span style="color: #339933;">,</span>
      <span style="color: #0000ff;">'4'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'177-334'</span><span style="color: #339933;">,</span>
      <span style="color: #0000ff;">'5'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'177-335'</span><span style="color: #339933;">,</span>
      <span style="color: #0000ff;">'6'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'177-416'</span><span style="color: #339933;">,</span>
      <span style="color: #0000ff;">'7'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'177-415'</span><span style="color: #339933;">,</span>
      <span style="color: #0000ff;">'8'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'177-418'</span><span style="color: #339933;">,</span>
      <span style="color: #0000ff;">'9'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'177-419'</span><span style="color: #339933;">,</span>
      <span style="color: #0000ff;">'10'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'177-420'</span><span style="color: #339933;">,</span>
      <span style="color: #0000ff;">'11'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'588-823'</span><span style="color: #339933;">,</span>
      <span style="color: #0000ff;">'12'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'588-826'</span><span style="color: #339933;">,</span>
      <span style="color: #0000ff;">'13'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'588-824'</span><span style="color: #339933;">,</span>
      <span style="color: #0000ff;">'14'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'177-413'</span><span style="color: #339933;">,</span>
      <span style="color: #0000ff;">'15'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'588-825'</span><span style="color: #339933;">,</span>
      <span style="color: #0000ff;">'33'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'LEASE'</span>
    <span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #666666; font-style: italic;">// Дальше желательно ничего не менять</span>
    <span style="color: #000088;">$col</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">0</span><span style="color: #009900;">&#93;</span> <span style="color: #339933;">=</span> <span style="color: #990000;">hexdec</span><span style="color: #009900;">&#40;</span><span style="color: #990000;">substr</span><span style="color: #009900;">&#40;</span>BGCOLOR<span style="color: #339933;">,</span> <span style="color: #cc66cc;">0</span><span style="color: #339933;">,</span> <span style="color: #cc66cc;">2</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span><span style="color: #000088;">$col</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">1</span><span style="color: #009900;">&#93;</span> <span style="color: #339933;">=</span> <span style="color: #990000;">hexdec</span><span style="color: #009900;">&#40;</span><span style="color: #990000;">substr</span><span style="color: #009900;">&#40;</span>BGCOLOR<span style="color: #339933;">,</span> <span style="color: #cc66cc;">2</span><span style="color: #339933;">,</span> <span style="color: #cc66cc;">2</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span><span style="color: #000088;">$col</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">2</span><span style="color: #009900;">&#93;</span> <span style="color: #339933;">=</span> <span style="color: #990000;">hexdec</span><span style="color: #009900;">&#40;</span><span style="color: #990000;">substr</span><span style="color: #009900;">&#40;</span>BGCOLOR<span style="color: #339933;">,</span> <span style="color: #cc66cc;">4</span><span style="color: #339933;">,</span> <span style="color: #cc66cc;">2</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000088;">$tmp</span> <span style="color: #339933;">=</span> <span style="color: #990000;">sprintf</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;<span style="color: #009933; font-weight: bold;">%X</span><span style="color: #009933; font-weight: bold;">%X</span><span style="color: #009933; font-weight: bold;">%X</span>&quot;</span><span style="color: #339933;">,</span> <span style="color: #000088;">$col</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">0</span><span style="color: #009900;">&#93;</span> <span style="color: #339933;">-</span> <span style="color: #cc66cc;">10</span><span style="color: #339933;">,</span> <span style="color: #000088;">$col</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">1</span><span style="color: #009900;">&#93;</span> <span style="color: #339933;">-</span> <span style="color: #cc66cc;">10</span><span style="color: #339933;">,</span> <span style="color: #000088;">$col</span><span style="color: #009900;">&#91;</span><span style="color: #cc66cc;">2</span><span style="color: #009900;">&#93;</span> <span style="color: #339933;">-</span> <span style="color: #cc66cc;">10</span> <span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #990000;">define</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;T_BGCOLOR&quot;</span><span style="color: #339933;">,</span> <span style="color: #000088;">$tmp</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000088;">$mon</span><span style="color: #339933;">=</span><span style="color: #990000;">array</span><span style="color: #009900;">&#40;</span>
       <span style="color: #0000ff;">'1'</span> <span style="color: #339933;">=&gt;</span> <span style="color: #0000ff;">'Январь'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'01'</span> <span style="color: #339933;">=&gt;</span> <span style="color: #0000ff;">'Январь'</span><span style="color: #339933;">,</span>
       <span style="color: #0000ff;">'2'</span> <span style="color: #339933;">=&gt;</span> <span style="color: #0000ff;">'Февраль'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'02'</span> <span style="color: #339933;">=&gt;</span> <span style="color: #0000ff;">'Февраль'</span><span style="color: #339933;">,</span>
       <span style="color: #0000ff;">'3'</span> <span style="color: #339933;">=&gt;</span> <span style="color: #0000ff;">'Март'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'03'</span> <span style="color: #339933;">=&gt;</span> <span style="color: #0000ff;">'Март'</span><span style="color: #339933;">,</span>
       <span style="color: #0000ff;">'4'</span> <span style="color: #339933;">=&gt;</span> <span style="color: #0000ff;">'Апрель'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'04'</span> <span style="color: #339933;">=&gt;</span> <span style="color: #0000ff;">'Апрель'</span><span style="color: #339933;">,</span>
       <span style="color: #0000ff;">'5'</span> <span style="color: #339933;">=&gt;</span> <span style="color: #0000ff;">'Май'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'05'</span> <span style="color: #339933;">=&gt;</span> <span style="color: #0000ff;">'Май'</span><span style="color: #339933;">,</span>
       <span style="color: #0000ff;">'6'</span> <span style="color: #339933;">=&gt;</span> <span style="color: #0000ff;">'Июнь'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'06'</span> <span style="color: #339933;">=&gt;</span> <span style="color: #0000ff;">'Июнь'</span><span style="color: #339933;">,</span>
       <span style="color: #0000ff;">'7'</span> <span style="color: #339933;">=&gt;</span> <span style="color: #0000ff;">'Июль'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'07'</span> <span style="color: #339933;">=&gt;</span> <span style="color: #0000ff;">'Июль'</span><span style="color: #339933;">,</span>
       <span style="color: #0000ff;">'8'</span> <span style="color: #339933;">=&gt;</span> <span style="color: #0000ff;">'Август'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'08'</span> <span style="color: #339933;">=&gt;</span> <span style="color: #0000ff;">'Август'</span><span style="color: #339933;">,</span>
       <span style="color: #0000ff;">'9'</span> <span style="color: #339933;">=&gt;</span> <span style="color: #0000ff;">'Сентябрь'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'09'</span> <span style="color: #339933;">=&gt;</span> <span style="color: #0000ff;">'Сентябрь'</span><span style="color: #339933;">,</span>
       <span style="color: #0000ff;">'10'</span> <span style="color: #339933;">=&gt;</span> <span style="color: #0000ff;">'Октябрь'</span><span style="color: #339933;">,</span>
       <span style="color: #0000ff;">'11'</span> <span style="color: #339933;">=&gt;</span> <span style="color: #0000ff;">'Ноябрь'</span><span style="color: #339933;">,</span>
       <span style="color: #0000ff;">'12'</span> <span style="color: #339933;">=&gt;</span> <span style="color: #0000ff;">'Декабрь'</span>
    <span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span><span style="color: #666666; font-style: italic;">//array($mon)</span>
    &nbsp;
    <span style="color: #000088;">$week_days</span><span style="color: #339933;">=</span><span style="color: #990000;">array</span><span style="color: #009900;">&#40;</span>
      <span style="color: #0000ff;">'0'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'Воскресенье'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'00'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'Воскресенье'</span><span style="color: #339933;">,</span>
      <span style="color: #0000ff;">'1'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'Понедельник'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'01'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'Понедельник'</span><span style="color: #339933;">,</span>
      <span style="color: #0000ff;">'2'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'Вторник'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'02'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'Вторник'</span><span style="color: #339933;">,</span>
      <span style="color: #0000ff;">'3'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'Среда'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'03'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'Среда'</span><span style="color: #339933;">,</span>
      <span style="color: #0000ff;">'4'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'Четверг'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'04'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'Четверг'</span><span style="color: #339933;">,</span>
      <span style="color: #0000ff;">'5'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'Пятница'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'05'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'Пятница'</span><span style="color: #339933;">,</span>
      <span style="color: #0000ff;">'6'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'Суббота'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'06'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'Суббота'</span><span style="color: #339933;">,</span>
      <span style="color: #0000ff;">'7'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'Праздник'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'07'</span><span style="color: #339933;">=&gt;</span><span style="color: #0000ff;">'Праздник'</span>
    <span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #990000;">define</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;ADMIN&quot;</span><span style="color: #339933;">,</span> <span style="color: #009900;">&#40;</span><span style="color: #990000;">getenv</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;REMOTE_USER&quot;</span><span style="color: #009900;">&#41;</span><span style="color: #009900;">&#41;</span> ? <span style="color: #990000;">getenv</span><span style="color: #009900;">&#40;</span><span style="color: #0000ff;">&quot;REMOTE_USER&quot;</span><span style="color: #009900;">&#41;</span> <span style="color: #339933;">:</span> ADMIN_USER<span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    &nbsp;
    <span style="color: #000000; font-weight: bold;">?&gt;</span></pre></td></tr></table><p class="theCode" style="display:none;">&lt;?
    define(&quot;BEZLIM_TABLE&quot;,&quot;bezlimit2&quot;);
    // Также проверьте настройки в mysql.php
    
    // Администратор, от имени которого происходят все изменения
    // Имеет значения только в том случае, если не используется
    // авторизация сервером
    define(&quot;ADMIN_USER&quot;, &quot;admin&quot;);
    
    // Количество байт в мегабайте (иногда требуется 1000000)
    define(&quot;MBYTE&quot;,&quot;1048576&quot;);
    
    // Если настроен sudo то перегружать radiusd
    // при изменениях в пакетах и прайсах
    // sudo настроить так: в файл /etc/sudoers добавить строку
    // apache  ALL= NOPASSWD: ALL
    // Соответственно apache это пользователь, от которого запущен WEB сервер
    define(&quot;SUDO_RADRELOAD&quot;,&quot;1&quot;);
    
    // Настройки логирования
    // Для корректной работы создайте файл NIBS_LOG_FILE в ручную
    // и разрешите запись в него пользователю от которого
    // запущен WEB сервер (в основном apache)
    define(&quot;NIBS_DO_LOG&quot;,&quot;1&quot;);
    define(&quot;NIBS_LOG_FILE&quot;,&quot;webnibs.log&quot;);
    
    // Создавать пользователя в системе (см. extern.php)
    // требует настройку sudo
    // по умолчанию добавляет в группу raduser которую надо создать вручную
    // домашний каталог ставит /home/users/$user (создать в /home подкаталог users
    // скелет берет в /etc/skel_ppp (создать /etc/skel_ppp и в
    // /etc/skel_ppp всего один подкаталог - html)
    // пытается включить квоты: 2мб /home и 10мб /var
    define(&quot;CREATE_SYSTEM&quot;,&quot;0&quot;);
    
    // Использовать карточную пристройку
    define(&quot;USE_CARDS&quot;,&quot;1&quot;);
    
    // Активировать меню рассылки
    // ОБЯЗАТЕЛЬНО настройте ниже MAIL_DOMAIN и COMPANY_NAME
    define(&quot;DELIVERY&quot;,&quot;1&quot;);
    
    // Пока не реализованно
    define(&quot;PROF_MODE&quot;,&quot;0&quot;);
    
    // Работа с почтовой базой postfix (см. extern.php)
    define(&quot;CREATE_POSTFIX_MAIL&quot;,&quot;0&quot;);
    define(&quot;MAIL_BASE&quot;,&quot;/var/spool/mail/virtual&quot;);
    define(&quot;MAIL_DOMAIN&quot;,&quot;your.domain&quot;);
    define(&quot;COMPANY_NAME&quot;,&quot;your.company&quot;);
    
    // --- Остальное ---
    // Цвет фона
    define(&quot;BGCOLOR&quot;,&quot;ddddff&quot;);
    
    // Массив для привязки номеров телефонов к портам
    // Удобно если NAS не посылает call_from
    $tel_nums=array(
      '0'=&gt;'LOCAL',
      '1'=&gt;'177-421',
      '2'=&gt;'177-422',
      '3'=&gt;'177-423',
      '4'=&gt;'177-334',
      '5'=&gt;'177-335',
      '6'=&gt;'177-416',
      '7'=&gt;'177-415',
      '8'=&gt;'177-418',
      '9'=&gt;'177-419',
      '10'=&gt;'177-420',
      '11'=&gt;'588-823',
      '12'=&gt;'588-826',
      '13'=&gt;'588-824',
      '14'=&gt;'177-413',
      '15'=&gt;'588-825',
      '33'=&gt;'LEASE'
    );
    
    // Дальше желательно ничего не менять
    $col[0] = hexdec(substr(BGCOLOR, 0, 2));$col[1] = hexdec(substr(BGCOLOR, 2, 2));$col[2] = hexdec(substr(BGCOLOR, 4, 2));
    $tmp = sprintf(&quot;%X%X%X&quot;, $col[0] - 10, $col[1] - 10, $col[2] - 10 );
    
    define(&quot;T_BGCOLOR&quot;, $tmp);
    
    $mon=array(
       '1' =&gt; 'Январь', '01' =&gt; 'Январь',
       '2' =&gt; 'Февраль', '02' =&gt; 'Февраль',
       '3' =&gt; 'Март', '03' =&gt; 'Март',
       '4' =&gt; 'Апрель', '04' =&gt; 'Апрель',
       '5' =&gt; 'Май', '05' =&gt; 'Май',
       '6' =&gt; 'Июнь', '06' =&gt; 'Июнь',
       '7' =&gt; 'Июль', '07' =&gt; 'Июль',
       '8' =&gt; 'Август', '08' =&gt; 'Август',
       '9' =&gt; 'Сентябрь', '09' =&gt; 'Сентябрь',
       '10' =&gt; 'Октябрь',
       '11' =&gt; 'Ноябрь',
       '12' =&gt; 'Декабрь'
    );//array($mon)
    
    $week_days=array(
      '0'=&gt;'Воскресенье', '00'=&gt;'Воскресенье',
      '1'=&gt;'Понедельник', '01'=&gt;'Понедельник',
      '2'=&gt;'Вторник', '02'=&gt;'Вторник',
      '3'=&gt;'Среда', '03'=&gt;'Среда',
      '4'=&gt;'Четверг', '04'=&gt;'Четверг',
      '5'=&gt;'Пятница', '05'=&gt;'Пятница',
      '6'=&gt;'Суббота', '06'=&gt;'Суббота',
      '7'=&gt;'Праздник', '07'=&gt;'Праздник'
    );
    
    define(&quot;ADMIN&quot;, (getenv(&quot;REMOTE_USER&quot;)) ? getenv(&quot;REMOTE_USER&quot;) : ADMIN_USER);
    
    ?&gt;</p></div>
    ";}
categories:
  - billing
  - FreeNIBS

---
defines.php — все основные переменные
  
<!--more-->

<pre lang="php"><?
define("BEZLIM_TABLE","bezlimit2");
// Также проверьте настройки в mysql.php

// Администратор, от имени которого происходят все изменения
// Имеет значения только в том случае, если не используется
// авторизация сервером
define("ADMIN_USER", "admin");

// Количество байт в мегабайте (иногда требуется 1000000)
define("MBYTE","1048576");

// Если настроен sudo то перегружать radiusd
// при изменениях в пакетах и прайсах
// sudo настроить так: в файл /etc/sudoers добавить строку
// apache  ALL= NOPASSWD: ALL
// Соответственно apache это пользователь, от которого запущен WEB сервер
define("SUDO_RADRELOAD","1");

// Настройки логирования
// Для корректной работы создайте файл NIBS_LOG_FILE в ручную
// и разрешите запись в него пользователю от которого
// запущен WEB сервер (в основном apache)
define("NIBS_DO_LOG","1");
define("NIBS_LOG_FILE","webnibs.log");

// Создавать пользователя в системе (см. extern.php)
// требует настройку sudo
// по умолчанию добавляет в группу raduser которую надо создать вручную
// домашний каталог ставит /home/users/$user (создать в /home подкаталог users
// скелет берет в /etc/skel_ppp (создать /etc/skel_ppp и в
// /etc/skel_ppp всего один подкаталог - html)
// пытается включить квоты: 2мб /home и 10мб /var
define("CREATE_SYSTEM","0");

// Использовать карточную пристройку
define("USE_CARDS","1");

// Активировать меню рассылки
// ОБЯЗАТЕЛЬНО настройте ниже MAIL_DOMAIN и COMPANY_NAME
define("DELIVERY","1");

// Пока не реализованно
define("PROF_MODE","0");

// Работа с почтовой базой postfix (см. extern.php)
define("CREATE_POSTFIX_MAIL","0");
define("MAIL_BASE","/var/spool/mail/virtual");
define("MAIL_DOMAIN","your.domain");
define("COMPANY_NAME","your.company");

// --- Остальное ---
// Цвет фона
define("BGCOLOR","ddddff");

// Массив для привязки номеров телефонов к портам
// Удобно если NAS не посылает call_from
$tel_nums=array(
  '0'=>'LOCAL',
  '1'=>'177-421',
  '2'=>'177-422',
  '3'=>'177-423',
  '4'=>'177-334',
  '5'=>'177-335',
  '6'=>'177-416',
  '7'=>'177-415',
  '8'=>'177-418',
  '9'=>'177-419',
  '10'=>'177-420',
  '11'=>'588-823',
  '12'=>'588-826',
  '13'=>'588-824',
  '14'=>'177-413',
  '15'=>'588-825',
  '33'=>'LEASE'
);

// Дальше желательно ничего не менять
$col[0] = hexdec(substr(BGCOLOR, 0, 2));$col[1] = hexdec(substr(BGCOLOR, 2, 2));$col[2] = hexdec(substr(BGCOLOR, 4, 2));
$tmp = sprintf("%X%X%X", $col[0] - 10, $col[1] - 10, $col[2] - 10 );

define("T_BGCOLOR", $tmp);

$mon=array(
   '1' => 'Январь', '01' => 'Январь',
   '2' => 'Февраль', '02' => 'Февраль',
   '3' => 'Март', '03' => 'Март',
   '4' => 'Апрель', '04' => 'Апрель',
   '5' => 'Май', '05' => 'Май',
   '6' => 'Июнь', '06' => 'Июнь',
   '7' => 'Июль', '07' => 'Июль',
   '8' => 'Август', '08' => 'Август',
   '9' => 'Сентябрь', '09' => 'Сентябрь',
   '10' => 'Октябрь',
   '11' => 'Ноябрь',
   '12' => 'Декабрь'
);//array($mon)

$week_days=array(
  '0'=>'Воскресенье', '00'=>'Воскресенье',
  '1'=>'Понедельник', '01'=>'Понедельник',
  '2'=>'Вторник', '02'=>'Вторник',
  '3'=>'Среда', '03'=>'Среда',
  '4'=>'Четверг', '04'=>'Четверг',
  '5'=>'Пятница', '05'=>'Пятница',
  '6'=>'Суббота', '06'=>'Суббота',
  '7'=>'Праздник', '07'=>'Праздник'
);

define("ADMIN", (getenv("REMOTE_USER")) ? getenv("REMOTE_USER") : ADMIN_USER);

?>

</pre>