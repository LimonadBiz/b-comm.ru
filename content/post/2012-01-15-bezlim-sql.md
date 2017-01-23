---
title: bezlim.sql
author: wel
type: post
date: 2012-01-14T23:20:44+00:00
url: /billing/bezlim-sql
wp-syntax-cache-content:
  - |
    a:1:{i:1;s:5683:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="php" style="font-family:monospace;"><span style="color: #990000;">FLUSH</span> PRIVILEGES<span style="color: #339933;">;</span>
    grant select<span style="color: #339933;">,</span>insert<span style="color: #339933;">,</span>update<span style="color: #339933;">,</span>delete<span style="color: #339933;">,</span>create<span style="color: #339933;">,</span>drop on bezlim<span style="color: #339933;">.*</span> to bezlim<span style="color: #339933;">@</span>localhost identified by <span style="color: #0000ff;">'bezlim'</span><span style="color: #339933;">;</span>
    grant select<span style="color: #339933;">,</span>insert<span style="color: #339933;">,</span>update<span style="color: #339933;">,</span>delete<span style="color: #339933;">,</span>create<span style="color: #339933;">,</span>drop on bezlim<span style="color: #339933;">.*</span> to bezlim<span style="color: #339933;">@</span>127<span style="color: #339933;">.</span>0<span style="color: #339933;">.</span>0<span style="color: #339933;">.</span>1 identified by <span style="color: #0000ff;">'bezlim'</span><span style="color: #339933;">;</span>
    &nbsp;
    DROP DATABASE <span style="color: #b1b100;">IF</span> EXISTS `bezlim`<span style="color: #339933;">;</span>
    CREATE DATABASE <span style="color: #b1b100;">IF</span> NOT EXISTS `bezlim`<span style="color: #339933;">;</span>
    <span style="color: #000000; font-weight: bold;">USE</span> `bezlim`<span style="color: #339933;">;</span>
    &nbsp;
    &nbsp;
    DROP TABLE <span style="color: #b1b100;">IF</span> EXISTS `all`<span style="color: #339933;">;</span>
    CREATE TABLE `all` <span style="color: #009900;">&#40;</span>
      `ip` varchar<span style="color: #009900;">&#40;</span><span style="color: #cc66cc;">48</span><span style="color: #009900;">&#41;</span> NOT <span style="color: #009900; font-weight: bold;">NULL</span> <span style="color: #b1b100;">default</span> <span style="color: #0000ff;">'192.168.0.1'</span><span style="color: #339933;">,</span>
      `rule` int<span style="color: #009900;">&#40;</span><span style="color: #cc66cc;">32</span><span style="color: #009900;">&#41;</span> NOT <span style="color: #009900; font-weight: bold;">NULL</span> <span style="color: #b1b100;">default</span> <span style="color: #0000ff;">'500'</span><span style="color: #339933;">,</span>
      `bw1` varchar<span style="color: #009900;">&#40;</span><span style="color: #cc66cc;">12</span><span style="color: #009900;">&#41;</span> NOT <span style="color: #009900; font-weight: bold;">NULL</span> <span style="color: #b1b100;">default</span> <span style="color: #0000ff;">'0'</span><span style="color: #339933;">,</span>
      `bw2` varchar<span style="color: #009900;">&#40;</span><span style="color: #cc66cc;">12</span><span style="color: #009900;">&#41;</span> NOT <span style="color: #009900; font-weight: bold;">NULL</span> <span style="color: #b1b100;">default</span> <span style="color: #0000ff;">'0'</span><span style="color: #339933;">,</span>
      `activ` char<span style="color: #009900;">&#40;</span><span style="color: #cc66cc;">1</span><span style="color: #009900;">&#41;</span> NOT <span style="color: #009900; font-weight: bold;">NULL</span> <span style="color: #b1b100;">default</span> <span style="color: #0000ff;">'y'</span><span style="color: #339933;">,</span>
      `id` int<span style="color: #009900;">&#40;</span><span style="color: #cc66cc;">32</span><span style="color: #009900;">&#41;</span> NOT <span style="color: #009900; font-weight: bold;">NULL</span> auto_increment<span style="color: #339933;">,</span>
      PRIMARY <span style="color: #990000;">KEY</span>  <span style="color: #009900;">&#40;</span>`id`<span style="color: #009900;">&#41;</span>
    <span style="color: #009900;">&#41;</span> ENGINE<span style="color: #339933;">=</span>MyISAM <span style="color: #b1b100;">DEFAULT</span> CHARSET<span style="color: #339933;">=</span>latin1<span style="color: #339933;">;</span>
    INSERT INTO `all` <span style="color: #009900;">&#40;</span> `ip` <span style="color: #339933;">,</span> `rule` <span style="color: #339933;">,</span> `bw1` <span style="color: #339933;">,</span> `bw2` <span style="color: #339933;">,</span> `activ`  <span style="color: #009900;">&#41;</span> VALUES <span style="color: #009900;">&#40;</span><span style="color: #0000ff;">'192.168.0.1'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'500'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'16Kbit/s'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'16Kbit/s'</span><span style="color: #339933;">,</span> <span style="color: #0000ff;">'y'</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span></pre></td></tr></table><p class="theCode" style="display:none;">FLUSH PRIVILEGES;
    grant select,insert,update,delete,create,drop on bezlim.* to bezlim@localhost identified by 'bezlim';
    grant select,insert,update,delete,create,drop on bezlim.* to bezlim@127.0.0.1 identified by 'bezlim';
    
    DROP DATABASE IF EXISTS `bezlim`;
    CREATE DATABASE IF NOT EXISTS `bezlim`;
    USE `bezlim`;
    
    
    DROP TABLE IF EXISTS `all`;
    CREATE TABLE `all` (
      `ip` varchar(48) NOT NULL default '192.168.0.1',
      `rule` int(32) NOT NULL default '500',
      `bw1` varchar(12) NOT NULL default '0',
      `bw2` varchar(12) NOT NULL default '0',
      `activ` char(1) NOT NULL default 'y',
      `id` int(32) NOT NULL auto_increment,
      PRIMARY KEY  (`id`)
    ) ENGINE=MyISAM DEFAULT CHARSET=latin1;
    INSERT INTO `all` ( `ip` , `rule` , `bw1` , `bw2` , `activ`  ) VALUES ('192.168.0.1', '500', '16Kbit/s', '16Kbit/s', 'y');</p></div>
    ";}
categories:
  - billing
  - FreeNIBS
tags:
  - bezlim.sql

---
bezlim.sql специальная таблица, которая нужна для моей модификации Фриинибса)))

<pre lang="php">FLUSH PRIVILEGES;
grant select,insert,update,delete,create,drop on bezlim.* to bezlim@localhost identified by 'bezlim';
grant select,insert,update,delete,create,drop on bezlim.* to bezlim@127.0.0.1 identified by 'bezlim';

DROP DATABASE IF EXISTS `bezlim`;
CREATE DATABASE IF NOT EXISTS `bezlim`;
USE `bezlim`;


DROP TABLE IF EXISTS `all`;
CREATE TABLE `all` (
  `ip` varchar(48) NOT NULL default '192.168.0.1',
  `rule` int(32) NOT NULL default '500',
  `bw1` varchar(12) NOT NULL default '0',
  `bw2` varchar(12) NOT NULL default '0',
  `activ` char(1) NOT NULL default 'y',
  `id` int(32) NOT NULL auto_increment,
  PRIMARY KEY  (`id`)
) ENGINE=MyISAM DEFAULT CHARSET=latin1;
INSERT INTO `all` ( `ip` , `rule` , `bw1` , `bw2` , `activ`  ) VALUES ('192.168.0.1', '500', '16Kbit/s', '16Kbit/s', 'y');

</pre>

 [bezlim.sql специальная таблица, которая нужна для моей модификации Фриинибса)))

<pre lang="php">FLUSH PRIVILEGES;
grant select,insert,update,delete,create,drop on bezlim.* to bezlim@localhost identified by 'bezlim';
grant select,insert,update,delete,create,drop on bezlim.* to bezlim@127.0.0.1 identified by 'bezlim';

DROP DATABASE IF EXISTS `bezlim`;
CREATE DATABASE IF NOT EXISTS `bezlim`;
USE `bezlim`;


DROP TABLE IF EXISTS `all`;
CREATE TABLE `all` (
  `ip` varchar(48) NOT NULL default '192.168.0.1',
  `rule` int(32) NOT NULL default '500',
  `bw1` varchar(12) NOT NULL default '0',
  `bw2` varchar(12) NOT NULL default '0',
  `activ` char(1) NOT NULL default 'y',
  `id` int(32) NOT NULL auto_increment,
  PRIMARY KEY  (`id`)
) ENGINE=MyISAM DEFAULT CHARSET=latin1;
INSERT INTO `all` ( `ip` , `rule` , `bw1` , `bw2` , `activ`  ) VALUES ('192.168.0.1', '500', '16Kbit/s', '16Kbit/s', 'y');

</pre>

][1]

 [1]: http://www.kurs-autocad.ru/3d/