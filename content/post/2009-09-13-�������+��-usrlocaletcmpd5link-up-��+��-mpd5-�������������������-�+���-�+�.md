---
title: Скрипт /usr/local/etc/mpd5/link-up для mpd5 срабатывающий при подключении
author: wel
type: post
date: 2009-09-12T23:32:22+00:00
url: /billing/скрипт-usrlocaletcmpd5link-up-для-mpd5-срабатывающий-при-по
short-url:
  - http://bit.ly/hulXY6
wp-syntax-cache-content:
  - |
    a:5:{i:1;s:515:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="php" style="font-family:monospace;">     set iface up<span style="color: #339933;">-</span>script <span style="color: #339933;">/</span>usr<span style="color: #339933;">/</span>local<span style="color: #339933;">/</span>etc<span style="color: #339933;">/</span>mpd5<span style="color: #339933;">/</span></pre></td></tr></table><p class="theCode" style="display:none;">     set iface up-script /usr/local/etc/mpd5/</p></div>
    ";i:2;s:766:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="line_numbers"><pre>1
    </pre></td><td class="code"><pre class="sql" style="font-family:monospace;"><span style="color: #993333; font-weight: bold;">SELECT</span> <span style="color: #66cc66;">*</span> <span style="color: #993333; font-weight: bold;">FROM</span> <span style="color: #ff0000;">`all`</span> <span style="color: #993333; font-weight: bold;">WHERE</span> <span style="color: #ff0000;">`ip`</span> <span style="color: #993333; font-weight: bold;">NOT</span> <span style="color: #993333; font-weight: bold;">LIKE</span> <span style="color: #ff0000;">'91.%'</span></pre></td></tr></table><p class="theCode" style="display:none;">SELECT * FROM `all` WHERE `ip` not LIKE '91.%'</p></div>
    ";i:3;s:40669:"
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
    142
    143
    144
    145
    146
    147
    148
    149
    150
    151
    152
    153
    154
    155
    156
    157
    158
    159
    160
    161
    162
    163
    164
    165
    166
    167
    168
    169
    170
    171
    172
    173
    174
    175
    176
    177
    178
    179
    180
    181
    182
    183
    184
    185
    186
    187
    188
    189
    190
    191
    192
    193
    194
    </pre></td><td class="code"><pre class="cpp" style="font-family:monospace;"><span style="color: #339900;">#include &lt;QtCore&gt;</span>
    <span style="color: #339900;">#include &lt;QCoreApplication&gt;</span>
    <span style="color: #339900;">#include &lt;QtSql&gt;</span>
    <span style="color: #339900;">#include &lt;iostream&gt;</span>
    <span style="color: #339900;">#include &lt;cstdlib&gt;</span>
    <span style="color: #339900;">#include &lt;iomanip&gt;</span>
    <span style="color: #339900;">#include &lt;stdio.h&gt;</span>
    <span style="color: #339900;">#include &lt;stdlib.h&gt;</span>
    <span style="color: #339900;">#include &lt;string.h&gt;</span>
    <span style="color: #339900;">#include &lt;time.h&gt;</span>
    <span style="color: #0000ff;">using</span> <span style="color: #0000ff;">namespace</span> std<span style="color: #008080;">;</span>
    &nbsp;
    &nbsp;
    <span style="color: #339900;">#define SQLDRIVER &quot;QMYSQL&quot;</span>
    <span style="color: #339900;">#define HOST &quot;10.1.1.1&quot;</span>
    <span style="color: #339900;">#define DBNAME &quot;bezlim&quot;</span>
    <span style="color: #339900;">#define USER &quot;bezlim&quot;</span>
    <span style="color: #339900;">#define PASSWORD &quot;bezlim&quot;</span>
    &nbsp;
    <span style="color: #0000ff;">int</span> main<span style="color: #008000;">&#40;</span><span style="color: #0000ff;">int</span> argc, <span style="color: #0000ff;">char</span> <span style="color: #000040;">*</span>argv<span style="color: #008000;">&#91;</span><span style="color: #008000;">&#93;</span><span style="color: #008000;">&#41;</span>
    <span style="color: #008000;">&#123;</span>
        QCoreApplication a<span style="color: #008000;">&#40;</span>argc, argv<span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
    &nbsp;
        QTextCodec <span style="color: #000040;">*</span>codec <span style="color: #000080;">=</span> QTextCodec<span style="color: #008080;">::</span><span style="color: #007788;">codecForName</span><span style="color: #008000;">&#40;</span><span style="color: #FF0000;">&quot;CP1251&quot;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
        QTextCodec<span style="color: #008080;">::</span><span style="color: #007788;">setCodecForTr</span><span style="color: #008000;">&#40;</span>codec<span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
        QTextCodec<span style="color: #008080;">::</span><span style="color: #007788;">setCodecForCStrings</span><span style="color: #008000;">&#40;</span>codec<span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
    &nbsp;
        QSqlDatabase db <span style="color: #000080;">=</span> QSqlDatabase<span style="color: #008080;">::</span><span style="color: #007788;">addDatabase</span><span style="color: #008000;">&#40;</span>SQLDRIVER<span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
    &nbsp;
        <span style="color: #0000ff;">if</span><span style="color: #008000;">&#40;</span> <span style="color: #000040;">!</span>db.<span style="color: #007788;">isDriverAvailable</span><span style="color: #008000;">&#40;</span>SQLDRIVER<span style="color: #008000;">&#41;</span><span style="color: #008000;">&#41;</span>
        <span style="color: #008000;">&#123;</span>
    &nbsp;
        <span style="color: #008000;">&#125;</span>
    &nbsp;
    &nbsp;
        db.<span style="color: #007788;">setHostName</span><span style="color: #008000;">&#40;</span>HOST<span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
        db.<span style="color: #007788;">setDatabaseName</span><span style="color: #008000;">&#40;</span>DBNAME<span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
        db.<span style="color: #007788;">setUserName</span><span style="color: #008000;">&#40;</span>USER<span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
        db.<span style="color: #007788;">setPassword</span><span style="color: #008000;">&#40;</span>PASSWORD<span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
        <span style="color: #666666;">//db.setPort(3306);</span>
        <span style="color: #0000ff;">bool</span> ok<span style="color: #000080;">=</span>db.<span style="color: #007788;">open</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
        <span style="color: #0000ff;">if</span><span style="color: #008000;">&#40;</span>ok<span style="color: #000040;">!</span><span style="color: #000080;">=</span><span style="color: #0000ff;">true</span><span style="color: #008000;">&#41;</span><span style="color: #008000;">&#123;</span>
            std<span style="color: #008080;">::</span><span style="color: #0000dd;">cout</span><span style="color: #000080;">&lt;&lt;</span><span style="color: #FF0000;">&quot;unable connec't&quot;</span><span style="color: #008080;">;</span>
            <span style="color: #0000dd;">exit</span><span style="color: #008000;">&#40;</span><span style="color: #0000dd;">1</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
        <span style="color: #008000;">&#125;</span>
         QString exec_this<span style="color: #008080;">;</span>
         <span style="color: #0000ff;">int</span> bw1<span style="color: #008080;">;</span>
    &nbsp;
         QString ip_argv<span style="color: #008080;">;</span>
         ip_argv<span style="color: #000080;">=</span>argv<span style="color: #008000;">&#91;</span><span style="color: #0000dd;">4</span><span style="color: #008000;">&#93;</span><span style="color: #008080;">;</span>
    &nbsp;
         <span style="color: #666666;">//qDebug()&lt;&lt;ip_argv;</span>
    &nbsp;
         QSqlQuery query<span style="color: #008000;">&#40;</span><span style="color: #FF0000;">&quot;SELECT * FROM `all` WHERE `ip` not LIKE '91.%' AND `activ`='y' AND `ip`='&quot;</span><span style="color: #000040;">+</span>ip_argv<span style="color: #000040;">+</span><span style="color: #FF0000;">&quot;' LIMIT 1&quot;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
         <span style="color: #0000ff;">while</span> <span style="color: #008000;">&#40;</span>query.<span style="color: #007788;">next</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008000;">&#41;</span> <span style="color: #008000;">&#123;</span>
             QString id <span style="color: #000080;">=</span> query.<span style="color: #007788;">value</span><span style="color: #008000;">&#40;</span><span style="color: #0000dd;">5</span><span style="color: #008000;">&#41;</span>.<span style="color: #007788;">toString</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
    &nbsp;
             QString ip <span style="color: #000080;">=</span> query.<span style="color: #007788;">value</span><span style="color: #008000;">&#40;</span><span style="color: #0000dd;">0</span><span style="color: #008000;">&#41;</span>.<span style="color: #007788;">toString</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
             QString in <span style="color: #000080;">=</span> query.<span style="color: #007788;">value</span><span style="color: #008000;">&#40;</span><span style="color: #0000dd;">3</span><span style="color: #008000;">&#41;</span>.<span style="color: #007788;">toString</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
             QString out <span style="color: #000080;">=</span> query.<span style="color: #007788;">value</span><span style="color: #008000;">&#40;</span><span style="color: #0000dd;">4</span><span style="color: #008000;">&#41;</span>.<span style="color: #007788;">toString</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
             QString n <span style="color: #000080;">=</span> query.<span style="color: #007788;">value</span><span style="color: #008000;">&#40;</span><span style="color: #0000dd;">1</span><span style="color: #008000;">&#41;</span>.<span style="color: #007788;">toString</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
             bw1 <span style="color: #000080;">=</span>query.<span style="color: #007788;">value</span><span style="color: #008000;">&#40;</span><span style="color: #0000dd;">3</span><span style="color: #008000;">&#41;</span>.<span style="color: #007788;">toInt</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
             QString bw2 <span style="color: #000080;">=</span>query.<span style="color: #007788;">value</span><span style="color: #008000;">&#40;</span><span style="color: #0000dd;">3</span><span style="color: #008000;">&#41;</span>.<span style="color: #007788;">toString</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
    <span style="color: #666666;">//pfctl - это закомментированная часть для pf nat</span>
    <span style="color: #666666;">//      exec_this=&quot;/sbin/pfctl -tinat -Tadd &quot;;</span>
    <span style="color: #666666;">//      exec_this +=ip;</span>
    <span style="color: #666666;">//      qDebug()&lt;&lt;exec_this&lt;&lt;endl;</span>
    &nbsp;
            exec_this <span style="color: #000080;">=</span><span style="color: #FF0000;">&quot;/sbin/ipfw table 1 add &quot;</span><span style="color: #008080;">;</span>
            exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span>ip<span style="color: #008080;">;</span>
    &nbsp;
            <span style="color: #0000dd;">system</span><span style="color: #008000;">&#40;</span>exec_this.<span style="color: #007788;">toStdString</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span>.<span style="color: #007788;">c_str</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
    &nbsp;
    &nbsp;
        <span style="color: #008000;">&#125;</span>
            qDebug<span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #000080;">&lt;&lt;</span>ip_argv<span style="color: #000080;">&lt;&lt;</span>endl<span style="color: #008080;">;</span>
    &nbsp;
            qDebug<span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #000080;">&lt;&lt;</span>exec_this<span style="color: #000080;">&lt;&lt;</span>endl<span style="color: #008080;">;</span>
    &nbsp;
         QSqlQuery query11<span style="color: #008000;">&#40;</span><span style="color: #FF0000;">&quot;SELECT * FROM `all` WHERE `activ`='y' AND `ip`='&quot;</span><span style="color: #000040;">+</span>ip_argv<span style="color: #000040;">+</span><span style="color: #FF0000;">&quot;' LIMIT 1&quot;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
         <span style="color: #0000ff;">while</span> <span style="color: #008000;">&#40;</span>query11.<span style="color: #007788;">next</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008000;">&#41;</span> <span style="color: #008000;">&#123;</span>
    <span style="color: #666666;">//pfctl это закомментированная часть для pf nat</span>
    <span style="color: #666666;">//      exec_this=&quot;/sbin/pfctl -tinat -Tadd &quot;;</span>
    <span style="color: #666666;">//      exec_this +=ip;</span>
    <span style="color: #666666;">//      qDebug()&lt;&lt;exec_this&lt;&lt;endl;</span>
    &nbsp;
             QString id <span style="color: #000080;">=</span> query11.<span style="color: #007788;">value</span><span style="color: #008000;">&#40;</span><span style="color: #0000dd;">5</span><span style="color: #008000;">&#41;</span>.<span style="color: #007788;">toString</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
    &nbsp;
             QString ip <span style="color: #000080;">=</span> query11.<span style="color: #007788;">value</span><span style="color: #008000;">&#40;</span><span style="color: #0000dd;">0</span><span style="color: #008000;">&#41;</span>.<span style="color: #007788;">toString</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
             QString in <span style="color: #000080;">=</span> query11.<span style="color: #007788;">value</span><span style="color: #008000;">&#40;</span><span style="color: #0000dd;">3</span><span style="color: #008000;">&#41;</span>.<span style="color: #007788;">toString</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
             QString out <span style="color: #000080;">=</span> query11.<span style="color: #007788;">value</span><span style="color: #008000;">&#40;</span><span style="color: #0000dd;">4</span><span style="color: #008000;">&#41;</span>.<span style="color: #007788;">toString</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
             QString n <span style="color: #000080;">=</span> query11.<span style="color: #007788;">value</span><span style="color: #008000;">&#40;</span><span style="color: #0000dd;">1</span><span style="color: #008000;">&#41;</span>.<span style="color: #007788;">toString</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
             bw1 <span style="color: #000080;">=</span>query11.<span style="color: #007788;">value</span><span style="color: #008000;">&#40;</span><span style="color: #0000dd;">3</span><span style="color: #008000;">&#41;</span>.<span style="color: #007788;">toInt</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
             QString bw2 <span style="color: #000080;">=</span>query11.<span style="color: #007788;">value</span><span style="color: #008000;">&#40;</span><span style="color: #0000dd;">3</span><span style="color: #008000;">&#41;</span>.<span style="color: #007788;">toString</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
    &nbsp;
    &nbsp;
          <span style="color: #666666;">//Эта часть у Меня отвечает за выделение скорости. Я использовал ipfw pipe</span>
            <span style="color: #0000ff;">if</span><span style="color: #008000;">&#40;</span>bw1<span style="color: #000080;">&gt;</span><span style="color: #0000dd;">0</span><span style="color: #008000;">&#41;</span>
            <span style="color: #008000;">&#123;</span>
                qint64 num <span style="color: #000080;">=</span> <span style="color: #0000dd;">0</span><span style="color: #008080;">;</span>
                QString num1<span style="color: #008080;">;</span>
                query.<span style="color: #007788;">clear</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
                 QSqlQuery query<span style="color: #008000;">&#40;</span><span style="color: #FF0000;">&quot;SELECT * FROM `freenibs`.`pipes` WHERE `freenibs`.`pipes`.`bw`='&quot;</span><span style="color: #000040;">+</span>bw2<span style="color: #000040;">+</span><span style="color: #FF0000;">&quot;' LIMIT 1&quot;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
                <span style="color: #666666;">//qDebug()&lt;&lt;&quot;SELECT `freenibs`.`pipes`.`n` FROM `freenibs`.`pipes` WHERE `freenibs`.`pipes`.`bw`='&quot;+bw2+&quot;' LIMIT 1&quot;&lt;&lt;endl;</span>
                 <span style="color: #0000ff;">while</span> <span style="color: #008000;">&#40;</span>query.<span style="color: #007788;">next</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008000;">&#41;</span> <span style="color: #008000;">&#123;</span>
                        num <span style="color: #000080;">=</span> query.<span style="color: #007788;">value</span><span style="color: #008000;">&#40;</span><span style="color: #0000dd;">1</span><span style="color: #008000;">&#41;</span>.<span style="color: #007788;">toInt</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
                        num1 <span style="color: #000080;">=</span> query.<span style="color: #007788;">value</span><span style="color: #008000;">&#40;</span><span style="color: #0000dd;">1</span><span style="color: #008000;">&#41;</span>.<span style="color: #007788;">toString</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
                    <span style="color: #008000;">&#125;</span>
                query.<span style="color: #007788;">clear</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
                <span style="color: #0000ff;">if</span><span style="color: #008000;">&#40;</span>num<span style="color: #000080;">&gt;</span><span style="color: #0000dd;">0</span><span style="color: #008000;">&#41;</span>
                <span style="color: #008000;">&#123;</span>
                        <span style="color: #666666;">//qDebug()&lt;&lt;&quot;NUM&gt;0|&quot;&lt;&lt;num1&lt;&lt;&quot;|&quot;&lt;&lt;endl;</span>
                        exec_this <span style="color: #000080;">=</span><span style="color: #FF0000;">&quot;/sbin/ipfw pipe &quot;</span><span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span>num1<span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span><span style="color: #FF0000;">&quot; config mask dst-ip 0x000000ff bw &quot;</span><span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span>bw2<span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span><span style="color: #FF0000;">&quot;Kbit/s&quot;</span><span style="color: #008080;">;</span>
                        <span style="color: #0000dd;">system</span><span style="color: #008000;">&#40;</span>exec_this.<span style="color: #007788;">toStdString</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span>.<span style="color: #007788;">c_str</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
                        <span style="color: #666666;">//qDebug()&lt;&lt;exec_this&lt;&lt;endl;</span>
                        exec_this <span style="color: #000080;">=</span><span style="color: #FF0000;">&quot;/sbin/ipfw table &quot;</span><span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span>num1<span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span><span style="color: #FF0000;">&quot; add &quot;</span><span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span>ip<span style="color: #008080;">;</span>
                        <span style="color: #0000dd;">system</span><span style="color: #008000;">&#40;</span>exec_this.<span style="color: #007788;">toStdString</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span>.<span style="color: #007788;">c_str</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
                        <span style="color: #666666;">//qDebug()&lt;&lt;exec_this&lt;&lt;endl;</span>
                <span style="color: #008000;">&#125;</span>
                <span style="color: #0000ff;">else</span>
                <span style="color: #008000;">&#123;</span>
                        QSqlQuery query1<span style="color: #008000;">&#40;</span><span style="color: #FF0000;">&quot; SELECT MAX(`n`)+1  FROM `freenibs`.`pipes` &quot;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
                        <span style="color: #666666;">//qDebug()&lt;&lt;num&lt;&lt;endl;</span>
                        <span style="color: #666666;">// qDebug()&lt;&lt;query1.lastError()&lt;&lt;endl;</span>
                        <span style="color: #666666;">// query.exec();</span>
                         <span style="color: #666666;">//qDebug()&lt;&lt;query1.lastError()&lt;&lt;endl;</span>
                         <span style="color: #0000ff;">while</span> <span style="color: #008000;">&#40;</span>query1.<span style="color: #007788;">next</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008000;">&#41;</span> <span style="color: #008000;">&#123;</span>
                                <span style="color: #666666;">//num = query1.value(0).toInt();</span>
                                num1 <span style="color: #000080;">=</span> query1.<span style="color: #007788;">value</span><span style="color: #008000;">&#40;</span><span style="color: #0000dd;">0</span><span style="color: #008000;">&#41;</span>.<span style="color: #007788;">toString</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
                            <span style="color: #008000;">&#125;</span>
                        <span style="color: #666666;">//qDebug()&lt;&lt;&quot;NUM:&quot;&lt;&lt;num1&lt;&lt;endl;</span>
                         <span style="color: #666666;">//QSqlQuery</span>
                         query.<span style="color: #007788;">prepare</span><span style="color: #008000;">&#40;</span><span style="color: #FF0000;">&quot;INSERT INTO `freenibs`.`pipes`  ( `bw`,`n`) values( '&quot;</span> <span style="color: #000040;">+</span>bw2<span style="color: #000040;">+</span> <span style="color: #FF0000;">&quot;','&quot;</span><span style="color: #000040;">+</span>num1<span style="color: #000040;">+</span><span style="color: #FF0000;">&quot;')&quot;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
                        <span style="color: #666666;">// qDebug()&lt;&lt;query.lastError()&lt;&lt;endl;</span>
                         query.<span style="color: #007788;">exec</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
    &nbsp;
                        exec_this <span style="color: #000080;">=</span><span style="color: #FF0000;">&quot;/sbin/ipfw delete &quot;</span><span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span>num1<span style="color: #008080;">;</span>
                        <span style="color: #0000dd;">system</span><span style="color: #008000;">&#40;</span>exec_this.<span style="color: #007788;">toStdString</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span>.<span style="color: #007788;">c_str</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
                        <span style="color: #666666;">//qDebug()&lt;&lt;exec_this&lt;&lt;endl;</span>
    &nbsp;
                        exec_this <span style="color: #000080;">=</span><span style="color: #FF0000;">&quot;/sbin/ipfw pipe &quot;</span><span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span>num1<span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span><span style="color: #FF0000;">&quot; config mask dst-ip 0x000000ff bw &quot;</span><span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span>bw2<span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span><span style="color: #FF0000;">&quot;Kbit/s&quot;</span><span style="color: #008080;">;</span>
                        <span style="color: #0000dd;">system</span><span style="color: #008000;">&#40;</span>exec_this.<span style="color: #007788;">toStdString</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span>.<span style="color: #007788;">c_str</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
                        <span style="color: #666666;">//qDebug()&lt;&lt;exec_this&lt;&lt;endl;</span>
    &nbsp;
                        exec_this <span style="color: #000080;">=</span><span style="color: #FF0000;">&quot;/sbin/ipfw -q add &quot;</span><span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span>num1<span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span><span style="color: #FF0000;">&quot; pipe &quot;</span><span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span>num1<span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span><span style="color: #FF0000;">&quot; all from table<span style="color: #000099; font-weight: bold;">\\</span>(&quot;</span><span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span>num1<span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span><span style="color: #FF0000;">&quot;<span style="color: #000099; font-weight: bold;">\\</span>) to not 10.0.0.0/8 out&quot;</span><span style="color: #008080;">;</span>
                        <span style="color: #0000dd;">system</span><span style="color: #008000;">&#40;</span>exec_this.<span style="color: #007788;">toStdString</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span>.<span style="color: #007788;">c_str</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
                        <span style="color: #666666;">//qDebug()&lt;&lt;exec_this&lt;&lt;endl;</span>
    &nbsp;
    &nbsp;
                        exec_this <span style="color: #000080;">=</span><span style="color: #FF0000;">&quot;/sbin/ipfw -q add &quot;</span><span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span>num1<span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span><span style="color: #FF0000;">&quot; pipe &quot;</span><span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span>num1<span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span><span style="color: #FF0000;">&quot; all from not 10.0.0.0/8 to table<span style="color: #000099; font-weight: bold;">\\</span>(&quot;</span><span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span>num1<span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span><span style="color: #FF0000;">&quot;<span style="color: #000099; font-weight: bold;">\\</span>) in &quot;</span><span style="color: #008080;">;</span>
                        <span style="color: #0000dd;">system</span><span style="color: #008000;">&#40;</span>exec_this.<span style="color: #007788;">toStdString</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span>.<span style="color: #007788;">c_str</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
                        <span style="color: #666666;">//qDebug()&lt;&lt;exec_this&lt;&lt;endl;</span>
    &nbsp;
    &nbsp;
                        exec_this <span style="color: #000080;">=</span><span style="color: #FF0000;">&quot;/sbin/ipfw table &quot;</span><span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span>num1<span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span> <span style="color: #FF0000;">&quot; add &quot;</span><span style="color: #008080;">;</span>
                        exec_this <span style="color: #000040;">+</span><span style="color: #000080;">=</span>ip<span style="color: #008080;">;</span>
                        <span style="color: #0000dd;">system</span><span style="color: #008000;">&#40;</span>exec_this.<span style="color: #007788;">toStdString</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span>.<span style="color: #007788;">c_str</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
                        <span style="color: #666666;">//qDebug()&lt;&lt;exec_this&lt;&lt;endl;</span>
                <span style="color: #008000;">&#125;</span>
            <span style="color: #008000;">&#125;</span>
    &nbsp;
           <span style="color: #666666;">//здесь Мы заполняем таблицу для того, что бы видеть что пользователь подключился</span>
            QSqlQuery query<span style="color: #008000;">&#40;</span><span style="color: #FF0000;">&quot;INSERT INTO `freenibs`.`updown` (`ip` ,`time` ,`status`) VALUES ( '&quot;</span><span style="color: #000040;">+</span>ip_argv<span style="color: #000040;">+</span><span style="color: #FF0000;">&quot;',CURRENT_TIMESTAMP , 'up');&quot;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
            query.<span style="color: #007788;">clear</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
        <span style="color: #008000;">&#125;</span>
         db.<span style="color: #007788;">close</span><span style="color: #008000;">&#40;</span><span style="color: #008000;">&#41;</span><span style="color: #008080;">;</span>
    <span style="color: #666666;">//    return a.exec();</span>
    <span style="color: #008000;">&#125;</span></pre></td></tr></table><p class="theCode" style="display:none;">#include &lt;QtCore&gt;
    #include &lt;QCoreApplication&gt;
    #include &lt;QtSql&gt;
    #include &lt;iostream&gt;
    #include &lt;cstdlib&gt;
    #include &lt;iomanip&gt;
    #include &lt;stdio.h&gt;
    #include &lt;stdlib.h&gt;
    #include &lt;string.h&gt;
    #include &lt;time.h&gt;
    using namespace std;
    
    
    #define SQLDRIVER &quot;QMYSQL&quot;
    #define HOST &quot;10.1.1.1&quot;
    #define DBNAME &quot;bezlim&quot;
    #define USER &quot;bezlim&quot;
    #define PASSWORD &quot;bezlim&quot;
    
    int main(int argc, char *argv[])
    {
        QCoreApplication a(argc, argv);
    
        QTextCodec *codec = QTextCodec::codecForName(&quot;CP1251&quot;);
        QTextCodec::setCodecForTr(codec);
        QTextCodec::setCodecForCStrings(codec);
    
        QSqlDatabase db = QSqlDatabase::addDatabase(SQLDRIVER);
    
        if( !db.isDriverAvailable(SQLDRIVER))
        {
    
        }
    
    
        db.setHostName(HOST);
        db.setDatabaseName(DBNAME);
        db.setUserName(USER);
        db.setPassword(PASSWORD);
        //db.setPort(3306);
        bool ok=db.open();
        if(ok!=true){
            std::cout&lt;&lt;&quot;unable connec't&quot;;
            exit(1);
        }
         QString exec_this;
         int bw1;
    
         QString ip_argv;
         ip_argv=argv[4];
    
         //qDebug()&lt;&lt;ip_argv;
    
         QSqlQuery query(&quot;SELECT * FROM `all` WHERE `ip` not LIKE '91.%' AND `activ`='y' AND `ip`='&quot;+ip_argv+&quot;' LIMIT 1&quot;);
         while (query.next()) {
             QString id = query.value(5).toString();
    
             QString ip = query.value(0).toString();
             QString in = query.value(3).toString();
             QString out = query.value(4).toString();
             QString n = query.value(1).toString();
             bw1 =query.value(3).toInt();
             QString bw2 =query.value(3).toString();
    //pfctl - это закомментированная часть для pf nat
    //      exec_this=&quot;/sbin/pfctl -tinat -Tadd &quot;;
    //      exec_this +=ip;
    //      qDebug()&lt;&lt;exec_this&lt;&lt;endl;
    
            exec_this =&quot;/sbin/ipfw table 1 add &quot;;
            exec_this +=ip;
    
            system(exec_this.toStdString().c_str());
    
    
        }
            qDebug()&lt;&lt;ip_argv&lt;&lt;endl;
    
            qDebug()&lt;&lt;exec_this&lt;&lt;endl;
    
         QSqlQuery query11(&quot;SELECT * FROM `all` WHERE `activ`='y' AND `ip`='&quot;+ip_argv+&quot;' LIMIT 1&quot;);
         while (query11.next()) {
    //pfctl это закомментированная часть для pf nat
    //      exec_this=&quot;/sbin/pfctl -tinat -Tadd &quot;;
    //      exec_this +=ip;
    //      qDebug()&lt;&lt;exec_this&lt;&lt;endl;
    
             QString id = query11.value(5).toString();
    
             QString ip = query11.value(0).toString();
             QString in = query11.value(3).toString();
             QString out = query11.value(4).toString();
             QString n = query11.value(1).toString();
             bw1 =query11.value(3).toInt();
             QString bw2 =query11.value(3).toString();
    
    
          //Эта часть у Меня отвечает за выделение скорости. Я использовал ipfw pipe
            if(bw1&gt;0)
            {
                qint64 num = 0;
                QString num1;
                query.clear();
                 QSqlQuery query(&quot;SELECT * FROM `freenibs`.`pipes` WHERE `freenibs`.`pipes`.`bw`='&quot;+bw2+&quot;' LIMIT 1&quot;);
                //qDebug()&lt;&lt;&quot;SELECT `freenibs`.`pipes`.`n` FROM `freenibs`.`pipes` WHERE `freenibs`.`pipes`.`bw`='&quot;+bw2+&quot;' LIMIT 1&quot;&lt;&lt;endl;
                 while (query.next()) {
                        num = query.value(1).toInt();
                        num1 = query.value(1).toString();
                    }
                query.clear();
                if(num&gt;0)
                {
                        //qDebug()&lt;&lt;&quot;NUM&gt;0|&quot;&lt;&lt;num1&lt;&lt;&quot;|&quot;&lt;&lt;endl;
                        exec_this =&quot;/sbin/ipfw pipe &quot;;
                        exec_this +=num1;
                        exec_this +=&quot; config mask dst-ip 0x000000ff bw &quot;;
                        exec_this +=bw2;
                        exec_this +=&quot;Kbit/s&quot;;
                        system(exec_this.toStdString().c_str());
                        //qDebug()&lt;&lt;exec_this&lt;&lt;endl;
                        exec_this =&quot;/sbin/ipfw table &quot;;
                        exec_this +=num1;
                        exec_this +=&quot; add &quot;;
                        exec_this +=ip;
                        system(exec_this.toStdString().c_str());
                        //qDebug()&lt;&lt;exec_this&lt;&lt;endl;
                }
                else
                {
                        QSqlQuery query1(&quot; SELECT MAX(`n`)+1  FROM `freenibs`.`pipes` &quot;);
                        //qDebug()&lt;&lt;num&lt;&lt;endl;
                        // qDebug()&lt;&lt;query1.lastError()&lt;&lt;endl;
                        // query.exec();
                         //qDebug()&lt;&lt;query1.lastError()&lt;&lt;endl;
                         while (query1.next()) {
                                //num = query1.value(0).toInt();
                                num1 = query1.value(0).toString();
                            }
                        //qDebug()&lt;&lt;&quot;NUM:&quot;&lt;&lt;num1&lt;&lt;endl;
                         //QSqlQuery
                         query.prepare(&quot;INSERT INTO `freenibs`.`pipes`  ( `bw`,`n`) values( '&quot; +bw2+ &quot;','&quot;+num1+&quot;')&quot;);
                        // qDebug()&lt;&lt;query.lastError()&lt;&lt;endl;
                         query.exec();
    
                        exec_this =&quot;/sbin/ipfw delete &quot;;
                        exec_this +=num1;
                        system(exec_this.toStdString().c_str());
                        //qDebug()&lt;&lt;exec_this&lt;&lt;endl;
    
                        exec_this =&quot;/sbin/ipfw pipe &quot;;
                        exec_this +=num1;
                        exec_this +=&quot; config mask dst-ip 0x000000ff bw &quot;;
                        exec_this +=bw2;
                        exec_this +=&quot;Kbit/s&quot;;
                        system(exec_this.toStdString().c_str());
                        //qDebug()&lt;&lt;exec_this&lt;&lt;endl;
    
                        exec_this =&quot;/sbin/ipfw -q add &quot;;
                        exec_this +=num1;
                        exec_this +=&quot; pipe &quot;;
                        exec_this +=num1;
                        exec_this +=&quot; all from table\\(&quot;;
                        exec_this +=num1;
                        exec_this +=&quot;\\) to not 10.0.0.0/8 out&quot;;
                        system(exec_this.toStdString().c_str());
                        //qDebug()&lt;&lt;exec_this&lt;&lt;endl;
    
    
                        exec_this =&quot;/sbin/ipfw -q add &quot;;
                        exec_this +=num1;
                        exec_this +=&quot; pipe &quot;;
                        exec_this +=num1;
                        exec_this +=&quot; all from not 10.0.0.0/8 to table\\(&quot;;
                        exec_this +=num1;
                        exec_this +=&quot;\\) in &quot;;
                        system(exec_this.toStdString().c_str());
                        //qDebug()&lt;&lt;exec_this&lt;&lt;endl;
    
    
                        exec_this =&quot;/sbin/ipfw table &quot;;
                        exec_this +=num1;
                        exec_this += &quot; add &quot;;
                        exec_this +=ip;
                        system(exec_this.toStdString().c_str());
                        //qDebug()&lt;&lt;exec_this&lt;&lt;endl;
                }
            }
    
           //здесь Мы заполняем таблицу для того, что бы видеть что пользователь подключился
            QSqlQuery query(&quot;INSERT INTO `freenibs`.`updown` (`ip` ,`time` ,`status`) VALUES ( '&quot;+ip_argv+&quot;',CURRENT_TIMESTAMP , 'up');&quot;);
            query.clear();
        }
         db.close();
    //    return a.exec();
    }</p></div>
    ";i:4;s:55471:"
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
    142
    143
    144
    145
    146
    147
    148
    149
    150
    151
    152
    153
    154
    155
    156
    157
    158
    159
    160
    161
    162
    163
    164
    165
    166
    167
    168
    169
    170
    171
    172
    173
    174
    175
    176
    177
    178
    179
    180
    181
    182
    183
    184
    185
    186
    187
    188
    </pre></td><td class="code"><pre class="make" style="font-family:monospace;"><span style="color: #339900; font-style: italic;">#############################################################################</span>
    <span style="color: #339900; font-style: italic;"># Makefile for building: link-up</span>
    <span style="color: #339900; font-style: italic;"># Generated by qmake (2.01a) (Qt 4.4.3) on: Thu Jul 23 00:40:54 2009</span>
    <span style="color: #339900; font-style: italic;"># Project:  pro.pro</span>
    <span style="color: #339900; font-style: italic;"># Template: app</span>
    <span style="color: #339900; font-style: italic;"># Command: /usr/local/bin/qmake-qt4 -unix -o Makefile pro.pro</span>
    <span style="color: #339900; font-style: italic;">#############################################################################</span>
    &nbsp;
    <span style="color: #339900; font-style: italic;">####### Compiler, tools and options</span>
    &nbsp;
    CC            <span style="color: #004400;">=</span> cc
    CXX           <span style="color: #004400;">=</span> c<span style="color: #004400;">++</span>
    DEFINES       <span style="color: #004400;">=</span> <span style="color: #004400;">-</span>DQT_NO_DEBUG <span style="color: #004400;">-</span>DQT_SQL_LIB <span style="color: #004400;">-</span>DQT_GUI_LIB <span style="color: #004400;">-</span>DQT_CORE_LIB <span style="color: #004400;">-</span>DQT_SHARED
    CFLAGS        <span style="color: #004400;">=</span> <span style="color: #004400;">-</span>pipe <span style="color: #004400;">-</span>O2 <span style="color: #004400;">-</span>fno<span style="color: #004400;">-</span>strict<span style="color: #004400;">-</span>aliasing <span style="color: #004400;">-</span>pipe <span style="color: #004400;">-</span>Wall <span style="color: #004400;">-</span>W <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">DEFINES</span><span style="color: #004400;">&#41;</span>
    CXXFLAGS      <span style="color: #004400;">=</span> <span style="color: #004400;">-</span>pipe <span style="color: #004400;">-</span>O2 <span style="color: #004400;">-</span>fno<span style="color: #004400;">-</span>strict<span style="color: #004400;">-</span>aliasing <span style="color: #004400;">-</span>pipe <span style="color: #004400;">-</span>Wall <span style="color: #004400;">-</span>W <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">DEFINES</span><span style="color: #004400;">&#41;</span>
    INCPATH       <span style="color: #004400;">=</span> <span style="color: #004400;">-</span>I<span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>freebsd<span style="color: #004400;">-</span>g<span style="color: #004400;">++</span> <span style="color: #004400;">-</span>I<span style="color: #004400;">.</span> <span style="color: #004400;">-</span>I<span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span><span style="color: #666622; font-weight: bold;">include</span><span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>QtCore <span style="color: #004400;">-</span>I<span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span><span style="color: #666622; font-weight: bold;">include</span><span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>QtCore <span style="color: #004400;">-</span>I<span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span><span style="color: #666622; font-weight: bold;">include</span><span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>QtGui <span style="color: #004400;">-</span>I<span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span><span style="color: #666622; font-weight: bold;">include</span><span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>QtGui <span style="color: #004400;">-</span>I<span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span><span style="color: #666622; font-weight: bold;">include</span><span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>QtSql <span style="color: #004400;">-</span>I<span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span><span style="color: #666622; font-weight: bold;">include</span><span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>QtSql <span style="color: #004400;">-</span>I<span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span><span style="color: #666622; font-weight: bold;">include</span><span style="color: #004400;">/</span>qt4 <span style="color: #004400;">-</span>I<span style="color: #004400;">.</span> <span style="color: #004400;">-</span>I<span style="color: #004400;">.</span> <span style="color: #004400;">-</span>I<span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span><span style="color: #666622; font-weight: bold;">include</span>
    LINK          <span style="color: #004400;">=</span> c<span style="color: #004400;">++</span>
    LFLAGS        <span style="color: #004400;">=</span> <span style="color: #004400;">-</span>pthread <span style="color: #004400;">-</span>Wl<span style="color: #004400;">,-</span>rpath<span style="color: #004400;">,/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>lib<span style="color: #004400;">/</span>qt4
    LIBS          <span style="color: #004400;">=</span> <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">SUBLIBS</span><span style="color: #004400;">&#41;</span>  <span style="color: #004400;">-</span>L<span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>lib <span style="color: #004400;">-</span>L<span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>lib<span style="color: #004400;">/</span>qt4 <span style="color: #004400;">-</span>lQtSql <span style="color: #004400;">-</span>L<span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>lib<span style="color: #004400;">/</span>qt4 <span style="color: #004400;">-</span>L<span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>lib <span style="color: #004400;">-</span>pthread <span style="color: #004400;">-</span>pthread <span style="color: #004400;">-</span>lQtGui <span style="color: #004400;">-</span>pthread <span style="color: #004400;">-</span>lpng <span style="color: #004400;">-</span>lSM <span style="color: #004400;">-</span>lICE <span style="color: #004400;">-</span>pthread <span style="color: #004400;">-</span>pthread <span style="color: #004400;">-</span>lXi <span style="color: #004400;">-</span>lXrender <span style="color: #004400;">-</span>lXrandr <span style="color: #004400;">-</span>lfreetype <span style="color: #004400;">-</span>lfontconfig <span style="color: #004400;">-</span>lXext <span style="color: #004400;">-</span>lX11 <span style="color: #004400;">-</span>lQtCore <span style="color: #004400;">-</span>lz <span style="color: #004400;">-</span>lm <span style="color: #004400;">-</span>pthread <span style="color: #004400;">-</span>lgthread<span style="color: #004400;">-</span><span style="color: #CC2200;">2.0</span> <span style="color: #004400;">-</span>lglib<span style="color: #004400;">-</span><span style="color: #CC2200;">2.0</span> <span style="color: #004400;">-</span>liconv
    AR            <span style="color: #004400;">=</span> ar cqs
    RANLIB        <span style="color: #004400;">=</span>
    QMAKE         <span style="color: #004400;">=</span> <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>bin<span style="color: #004400;">/</span>qmake<span style="color: #004400;">-</span>qt4
    TAR           <span style="color: #004400;">=</span> tar <span style="color: #004400;">-</span>cf
    COMPRESS      <span style="color: #004400;">=</span> gzip <span style="color: #004400;">-</span>9f
    COPY          <span style="color: #004400;">=</span> cp <span style="color: #004400;">-</span>f
    SED           <span style="color: #004400;">=</span> sed
    COPY_FILE     <span style="color: #004400;">=</span> <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">COPY</span><span style="color: #004400;">&#41;</span>
    COPY_DIR      <span style="color: #004400;">=</span> <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">COPY</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">-</span>R
    INSTALL_FILE  <span style="color: #004400;">=</span> <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">COPY_FILE</span><span style="color: #004400;">&#41;</span>
    INSTALL_DIR   <span style="color: #004400;">=</span> <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">COPY_DIR</span><span style="color: #004400;">&#41;</span>
    INSTALL_PROGRAM <span style="color: #004400;">=</span> <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">COPY_FILE</span><span style="color: #004400;">&#41;</span>
    DEL_FILE      <span style="color: #004400;">=</span> rm <span style="color: #004400;">-</span>f
    SYMLINK       <span style="color: #004400;">=</span> ln <span style="color: #004400;">-</span>sf
    DEL_DIR       <span style="color: #004400;">=</span> rmdir
    MOVE          <span style="color: #004400;">=</span> mv <span style="color: #004400;">-</span>f
    CHK_DIR_EXISTS<span style="color: #004400;">=</span> test <span style="color: #004400;">-</span>d
    MKDIR         <span style="color: #004400;">=</span> mkdir <span style="color: #004400;">-</span>p
    &nbsp;
    <span style="color: #339900; font-style: italic;">####### Output directory</span>
    &nbsp;
    OBJECTS_DIR   <span style="color: #004400;">=</span> <span style="color: #004400;">./</span>
    &nbsp;
    <span style="color: #339900; font-style: italic;">####### Files</span>
    &nbsp;
    SOURCES       <span style="color: #004400;">=</span> main<span style="color: #004400;">.</span>cpp
    OBJECTS       <span style="color: #004400;">=</span> main<span style="color: #004400;">.</span>o
    DIST          <span style="color: #004400;">=</span> <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>common<span style="color: #004400;">/</span>unix<span style="color: #004400;">.</span>conf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>qconfig<span style="color: #004400;">.</span>pri \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>qt_functions<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>qt_config<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>exclusive_builds<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>default_pre<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>release<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>default_post<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>unix<span style="color: #004400;">/</span>thread<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>warn_on<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>qt<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>moc<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>resources<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>uic<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>yacc<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>lex<span style="color: #004400;">.</span>prf \
                    pro<span style="color: #004400;">.</span>pro
    QMAKE_TARGET  <span style="color: #004400;">=</span> link<span style="color: #004400;">-</span>up
    DESTDIR       <span style="color: #004400;">=</span>
    TARGET        <span style="color: #004400;">=</span> link<span style="color: #004400;">-</span>up
    &nbsp;
    first<span style="color: #004400;">:</span> all
    <span style="color: #339900; font-style: italic;">####### Implicit rules</span>
    &nbsp;
    <span style="color: #990000;">.SUFFIXES</span><span style="color: #004400;">:</span> <span style="color: #004400;">.</span>o <span style="color: #004400;">.</span>c <span style="color: #004400;">.</span>cpp <span style="color: #004400;">.</span>cc <span style="color: #004400;">.</span>cxx <span style="color: #004400;">.</span>C
    &nbsp;
    <span style="color: #004400;">.</span>cpp<span style="color: #004400;">.</span>o<span style="color: #004400;">:</span>
            <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">CXX</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">-</span>c <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">CXXFLAGS</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">INCPATH</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">-</span>o <span style="color: #CC2200;">&quot;$@&quot;</span> <span style="color: #CC2200;">&quot;$&lt;&quot;</span>
    &nbsp;
    <span style="color: #004400;">.</span>cc<span style="color: #004400;">.</span>o<span style="color: #004400;">:</span>
            <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">CXX</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">-</span>c <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">CXXFLAGS</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">INCPATH</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">-</span>o <span style="color: #CC2200;">&quot;$@&quot;</span> <span style="color: #CC2200;">&quot;$&lt;&quot;</span>
    &nbsp;
    <span style="color: #004400;">.</span>cxx<span style="color: #004400;">.</span>o<span style="color: #004400;">:</span>
            <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">CXX</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">-</span>c <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">CXXFLAGS</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">INCPATH</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">-</span>o <span style="color: #CC2200;">&quot;$@&quot;</span> <span style="color: #CC2200;">&quot;$&lt;&quot;</span>
    &nbsp;
    <span style="color: #004400;">.</span>C<span style="color: #004400;">.</span>o<span style="color: #004400;">:</span>
            <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">CXX</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">-</span>c <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">CXXFLAGS</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">INCPATH</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">-</span>o <span style="color: #CC2200;">&quot;$@&quot;</span> <span style="color: #CC2200;">&quot;$&lt;&quot;</span>
    &nbsp;
    <span style="color: #004400;">.</span>c<span style="color: #004400;">.</span>o<span style="color: #004400;">:</span>
            <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">CC</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">-</span>c <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">CFLAGS</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">INCPATH</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">-</span>o <span style="color: #CC2200;">&quot;$@&quot;</span> <span style="color: #CC2200;">&quot;$&lt;&quot;</span>
    &nbsp;
    <span style="color: #339900; font-style: italic;">####### Build rules</span>
    &nbsp;
    all<span style="color: #004400;">:</span> Makefile <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">TARGET</span><span style="color: #004400;">&#41;</span>
    &nbsp;
    <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">TARGET</span><span style="color: #004400;">&#41;</span><span style="color: #004400;">:</span>  <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">OBJECTS</span><span style="color: #004400;">&#41;</span>
            <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">LINK</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">LFLAGS</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">-</span>o <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">TARGET</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">OBJECTS</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">OBJCOMP</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">LIBS</span><span style="color: #004400;">&#41;</span>
    &nbsp;
    Makefile<span style="color: #004400;">:</span> pro<span style="color: #004400;">.</span>pro  <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>freebsd<span style="color: #004400;">-</span>g<span style="color: #004400;">++/</span>qmake<span style="color: #004400;">.</span>conf <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>common<span style="color: #004400;">/</span>unix<span style="color: #004400;">.</span>conf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>qconfig<span style="color: #004400;">.</span>pri \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>qt_functions<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>qt_config<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>exclusive_builds<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>default_pre<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>release<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>default_post<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>unix<span style="color: #004400;">/</span>thread<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>warn_on<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>qt<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>moc<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>resources<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>uic<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>yacc<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>lex<span style="color: #004400;">.</span>prf \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>lib<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>libQtSql<span style="color: #004400;">.</span>prl \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>lib<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>libQtCore<span style="color: #004400;">.</span>prl \
                    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>lib<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>libQtGui<span style="color: #004400;">.</span>prl
            <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">QMAKE</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">-</span>unix <span style="color: #004400;">-</span>o Makefile pro<span style="color: #004400;">.</span>pro
    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>common<span style="color: #004400;">/</span>unix<span style="color: #004400;">.</span>conf<span style="color: #004400;">:</span>
    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>qconfig<span style="color: #004400;">.</span>pri<span style="color: #004400;">:</span>
    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>qt_functions<span style="color: #004400;">.</span>prf<span style="color: #004400;">:</span>
    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>qt_config<span style="color: #004400;">.</span>prf<span style="color: #004400;">:</span>
    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>exclusive_builds<span style="color: #004400;">.</span>prf<span style="color: #004400;">:</span>
    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>default_pre<span style="color: #004400;">.</span>prf<span style="color: #004400;">:</span>
    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>release<span style="color: #004400;">.</span>prf<span style="color: #004400;">:</span>
    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>default_post<span style="color: #004400;">.</span>prf<span style="color: #004400;">:</span>
    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>unix<span style="color: #004400;">/</span>thread<span style="color: #004400;">.</span>prf<span style="color: #004400;">:</span>
    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>warn_on<span style="color: #004400;">.</span>prf<span style="color: #004400;">:</span>
    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>qt<span style="color: #004400;">.</span>prf<span style="color: #004400;">:</span>
    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>moc<span style="color: #004400;">.</span>prf<span style="color: #004400;">:</span>
    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>resources<span style="color: #004400;">.</span>prf<span style="color: #004400;">:</span>
    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>uic<span style="color: #004400;">.</span>prf<span style="color: #004400;">:</span>
    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>yacc<span style="color: #004400;">.</span>prf<span style="color: #004400;">:</span>
    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>share<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>mkspecs<span style="color: #004400;">/</span>features<span style="color: #004400;">/</span>lex<span style="color: #004400;">.</span>prf<span style="color: #004400;">:</span>
    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>lib<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>libQtSql<span style="color: #004400;">.</span>prl<span style="color: #004400;">:</span>
    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>lib<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>libQtCore<span style="color: #004400;">.</span>prl<span style="color: #004400;">:</span>
    <span style="color: #004400;">/</span>usr<span style="color: #004400;">/</span>local<span style="color: #004400;">/</span>lib<span style="color: #004400;">/</span>qt4<span style="color: #004400;">/</span>libQtGui<span style="color: #004400;">.</span>prl<span style="color: #004400;">:</span>
    qmake<span style="color: #004400;">:</span>  FORCE
            <span style="color: #004400;">@$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">QMAKE</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">-</span>unix <span style="color: #004400;">-</span>o Makefile pro<span style="color: #004400;">.</span>pro
    &nbsp;
    dist<span style="color: #004400;">:</span>
            <span style="color: #004400;">@$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">CHK_DIR_EXISTS</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">.</span>tmp<span style="color: #004400;">/</span>link<span style="color: #004400;">-</span>up1<span style="color: #004400;">.</span>0<span style="color: #004400;">.</span>0 <span style="color: #004400;">||</span> <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">MKDIR</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">.</span>tmp<span style="color: #004400;">/</span>link<span style="color: #004400;">-</span>up1<span style="color: #004400;">.</span>0<span style="color: #004400;">.</span>0
            <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">COPY_FILE</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">--</span>parents <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">SOURCES</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">DIST</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">.</span>tmp<span style="color: #004400;">/</span>link<span style="color: #004400;">-</span>up1<span style="color: #004400;">.</span>0<span style="color: #004400;">.</span>0<span style="color: #004400;">/</span> <span style="color: #004400;">&amp;&amp;</span> <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">COPY_FILE</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">--</span>parents main<span style="color: #004400;">.</span>cpp <span style="color: #004400;">.</span>tmp<span style="color: #004400;">/</span>link<span style="color: #004400;">-</span>up1<span style="color: #004400;">.</span>0<span style="color: #004400;">.</span>0<span style="color: #004400;">/</span> <span style="color: #004400;">&amp;&amp;</span> <span style="color: #004400;">&#40;</span>cd `dirname <span style="color: #004400;">.</span>tmp<span style="color: #004400;">/</span>link<span style="color: #004400;">-</span>up1<span style="color: #004400;">.</span>0<span style="color: #004400;">.</span>0` <span style="color: #004400;">&amp;&amp;</span> <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">TAR</span><span style="color: #004400;">&#41;</span> link<span style="color: #004400;">-</span>up1<span style="color: #004400;">.</span>0<span style="color: #004400;">.</span>0<span style="color: #004400;">.</span>tar link<span style="color: #004400;">-</span>up1<span style="color: #004400;">.</span>0<span style="color: #004400;">.</span>0 <span style="color: #004400;">&amp;&amp;</span> <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">COMPRESS</span><span style="color: #004400;">&#41;</span> link<span style="color: #004400;">-</span>up1<span style="color: #004400;">.</span>0<span style="color: #004400;">.</span>0<span style="color: #004400;">.</span>tar<span style="color: #004400;">&#41;</span> <span style="color: #004400;">&amp;&amp;</span> <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">MOVE</span><span style="color: #004400;">&#41;</span> `dirname <span style="color: #004400;">.</span>tmp<span style="color: #004400;">/</span>link<span style="color: #004400;">-</span>up1<span style="color: #004400;">.</span>0<span style="color: #004400;">.</span>0`<span style="color: #004400;">/</span>link<span style="color: #004400;">-</span>up1<span style="color: #004400;">.</span>0<span style="color: #004400;">.</span>0<span style="color: #004400;">.</span>tar<span style="color: #004400;">.</span>gz <span style="color: #004400;">.</span> <span style="color: #004400;">&amp;&amp;</span> <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">DEL_FILE</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">-</span>r <span style="color: #004400;">.</span>tmp<span style="color: #004400;">/</span>link<span style="color: #004400;">-</span>up1<span style="color: #004400;">.</span>0<span style="color: #004400;">.</span>0
    &nbsp;
    &nbsp;
    clean<span style="color: #004400;">:</span>compiler_clean
            <span style="color: #004400;">-$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">DEL_FILE</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">OBJECTS</span><span style="color: #004400;">&#41;</span>
            <span style="color: #004400;">-$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">DEL_FILE</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">*</span>~ core <span style="color: #004400;">*.</span>core
    &nbsp;
    &nbsp;
    <span style="color: #339900; font-style: italic;">####### Sub-libraries</span>
    &nbsp;
    distclean<span style="color: #004400;">:</span> clean
            <span style="color: #004400;">-$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">DEL_FILE</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">TARGET</span><span style="color: #004400;">&#41;</span>
            <span style="color: #004400;">-$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">DEL_FILE</span><span style="color: #004400;">&#41;</span> Makefile
    &nbsp;
    &nbsp;
    mocclean<span style="color: #004400;">:</span> compiler_moc_header_clean compiler_moc_source_clean
    &nbsp;
    mocables<span style="color: #004400;">:</span> compiler_moc_header_make_all compiler_moc_source_make_all
    &nbsp;
    compiler_moc_header_make_all<span style="color: #004400;">:</span>
    compiler_moc_header_clean<span style="color: #004400;">:</span>
    compiler_rcc_make_all<span style="color: #004400;">:</span>
    compiler_rcc_clean<span style="color: #004400;">:</span>
    compiler_image_collection_make_all<span style="color: #004400;">:</span> qmake_image_collection<span style="color: #004400;">.</span>cpp
    compiler_image_collection_clean<span style="color: #004400;">:</span>
            <span style="color: #004400;">-$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">DEL_FILE</span><span style="color: #004400;">&#41;</span> qmake_image_collection<span style="color: #004400;">.</span>cpp
    compiler_moc_source_make_all<span style="color: #004400;">:</span>
    compiler_moc_source_clean<span style="color: #004400;">:</span>
    compiler_uic_make_all<span style="color: #004400;">:</span>
    compiler_uic_clean<span style="color: #004400;">:</span>
    compiler_yacc_decl_make_all<span style="color: #004400;">:</span>
    compiler_yacc_decl_clean<span style="color: #004400;">:</span>
    compiler_yacc_impl_make_all<span style="color: #004400;">:</span>
    compiler_yacc_impl_clean<span style="color: #004400;">:</span>
    compiler_lex_make_all<span style="color: #004400;">:</span>
    compiler_lex_clean<span style="color: #004400;">:</span>
    compiler_clean<span style="color: #004400;">:</span>
    &nbsp;
    <span style="color: #339900; font-style: italic;">####### Compile</span>
    &nbsp;
    main<span style="color: #004400;">.</span>o<span style="color: #004400;">:</span> main<span style="color: #004400;">.</span>cpp
            <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">CXX</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">-</span>c <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">CXXFLAGS</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">$</span><span style="color: #004400;">&#40;</span><span style="color: #000088;">INCPATH</span><span style="color: #004400;">&#41;</span> <span style="color: #004400;">-</span>o main<span style="color: #004400;">.</span>o main<span style="color: #004400;">.</span>cpp
    &nbsp;
    <span style="color: #339900; font-style: italic;">####### Install</span>
    &nbsp;
    install<span style="color: #004400;">:</span>   FORCE
    &nbsp;
    uninstall<span style="color: #004400;">:</span>   FORCE
    &nbsp;
    FORCE<span style="color: #004400;">:</span></pre></td></tr></table><p class="theCode" style="display:none;">#############################################################################
    # Makefile for building: link-up
    # Generated by qmake (2.01a) (Qt 4.4.3) on: Thu Jul 23 00:40:54 2009
    # Project:  pro.pro
    # Template: app
    # Command: /usr/local/bin/qmake-qt4 -unix -o Makefile pro.pro
    #############################################################################
    
    ####### Compiler, tools and options
    
    CC            = cc
    CXX           = c++
    DEFINES       = -DQT_NO_DEBUG -DQT_SQL_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED
    CFLAGS        = -pipe -O2 -fno-strict-aliasing -pipe -Wall -W $(DEFINES)
    CXXFLAGS      = -pipe -O2 -fno-strict-aliasing -pipe -Wall -W $(DEFINES)
    INCPATH       = -I/usr/local/share/qt4/mkspecs/freebsd-g++ -I. -I/usr/local/include/qt4/QtCore -I/usr/local/include/qt4/QtCore -I/usr/local/include/qt4/QtGui -I/usr/local/include/qt4/QtGui -I/usr/local/include/qt4/QtSql -I/usr/local/include/qt4/QtSql -I/usr/local/include/qt4 -I. -I. -I/usr/local/include
    LINK          = c++
    LFLAGS        = -pthread -Wl,-rpath,/usr/local/lib/qt4
    LIBS          = $(SUBLIBS)  -L/usr/local/lib -L/usr/local/lib/qt4 -lQtSql -L/usr/local/lib/qt4 -L/usr/local/lib -pthread -pthread -lQtGui -pthread -lpng -lSM -lICE -pthread -pthread -lXi -lXrender -lXrandr -lfreetype -lfontconfig -lXext -lX11 -lQtCore -lz -lm -pthread -lgthread-2.0 -lglib-2.0 -liconv
    AR            = ar cqs
    RANLIB        =
    QMAKE         = /usr/local/bin/qmake-qt4
    TAR           = tar -cf
    COMPRESS      = gzip -9f
    COPY          = cp -f
    SED           = sed
    COPY_FILE     = $(COPY)
    COPY_DIR      = $(COPY) -R
    INSTALL_FILE  = $(COPY_FILE)
    INSTALL_DIR   = $(COPY_DIR)
    INSTALL_PROGRAM = $(COPY_FILE)
    DEL_FILE      = rm -f
    SYMLINK       = ln -sf
    DEL_DIR       = rmdir
    MOVE          = mv -f
    CHK_DIR_EXISTS= test -d
    MKDIR         = mkdir -p
    
    ####### Output directory
    
    OBJECTS_DIR   = ./
    
    ####### Files
    
    SOURCES       = main.cpp
    OBJECTS       = main.o
    DIST          = /usr/local/share/qt4/mkspecs/common/unix.conf \
                    /usr/local/share/qt4/mkspecs/qconfig.pri \
                    /usr/local/share/qt4/mkspecs/features/qt_functions.prf \
                    /usr/local/share/qt4/mkspecs/features/qt_config.prf \
                    /usr/local/share/qt4/mkspecs/features/exclusive_builds.prf \
                    /usr/local/share/qt4/mkspecs/features/default_pre.prf \
                    /usr/local/share/qt4/mkspecs/features/release.prf \
                    /usr/local/share/qt4/mkspecs/features/default_post.prf \
                    /usr/local/share/qt4/mkspecs/features/unix/thread.prf \
                    /usr/local/share/qt4/mkspecs/features/warn_on.prf \
                    /usr/local/share/qt4/mkspecs/features/qt.prf \
                    /usr/local/share/qt4/mkspecs/features/moc.prf \
                    /usr/local/share/qt4/mkspecs/features/resources.prf \
                    /usr/local/share/qt4/mkspecs/features/uic.prf \
                    /usr/local/share/qt4/mkspecs/features/yacc.prf \
                    /usr/local/share/qt4/mkspecs/features/lex.prf \
                    pro.pro
    QMAKE_TARGET  = link-up
    DESTDIR       =
    TARGET        = link-up
    
    first: all
    ####### Implicit rules
    
    .SUFFIXES: .o .c .cpp .cc .cxx .C
    
    .cpp.o:
            $(CXX) -c $(CXXFLAGS) $(INCPATH) -o &quot;$@&quot; &quot;$&lt;&quot;
    
    .cc.o:
            $(CXX) -c $(CXXFLAGS) $(INCPATH) -o &quot;$@&quot; &quot;$&lt;&quot;
    
    .cxx.o:
            $(CXX) -c $(CXXFLAGS) $(INCPATH) -o &quot;$@&quot; &quot;$&lt;&quot;
    
    .C.o:
            $(CXX) -c $(CXXFLAGS) $(INCPATH) -o &quot;$@&quot; &quot;$&lt;&quot;
    
    .c.o:
            $(CC) -c $(CFLAGS) $(INCPATH) -o &quot;$@&quot; &quot;$&lt;&quot;
    
    ####### Build rules
    
    all: Makefile $(TARGET)
    
    $(TARGET):  $(OBJECTS)
            $(LINK) $(LFLAGS) -o $(TARGET) $(OBJECTS) $(OBJCOMP) $(LIBS)
    
    Makefile: pro.pro  /usr/local/share/qt4/mkspecs/freebsd-g++/qmake.conf /usr/local/share/qt4/mkspecs/common/unix.conf \
                    /usr/local/share/qt4/mkspecs/qconfig.pri \
                    /usr/local/share/qt4/mkspecs/features/qt_functions.prf \
                    /usr/local/share/qt4/mkspecs/features/qt_config.prf \
                    /usr/local/share/qt4/mkspecs/features/exclusive_builds.prf \
                    /usr/local/share/qt4/mkspecs/features/default_pre.prf \
                    /usr/local/share/qt4/mkspecs/features/release.prf \
                    /usr/local/share/qt4/mkspecs/features/default_post.prf \
                    /usr/local/share/qt4/mkspecs/features/unix/thread.prf \
                    /usr/local/share/qt4/mkspecs/features/warn_on.prf \
                    /usr/local/share/qt4/mkspecs/features/qt.prf \
                    /usr/local/share/qt4/mkspecs/features/moc.prf \
                    /usr/local/share/qt4/mkspecs/features/resources.prf \
                    /usr/local/share/qt4/mkspecs/features/uic.prf \
                    /usr/local/share/qt4/mkspecs/features/yacc.prf \
                    /usr/local/share/qt4/mkspecs/features/lex.prf \
                    /usr/local/lib/qt4/libQtSql.prl \
                    /usr/local/lib/qt4/libQtCore.prl \
                    /usr/local/lib/qt4/libQtGui.prl
            $(QMAKE) -unix -o Makefile pro.pro
    /usr/local/share/qt4/mkspecs/common/unix.conf:
    /usr/local/share/qt4/mkspecs/qconfig.pri:
    /usr/local/share/qt4/mkspecs/features/qt_functions.prf:
    /usr/local/share/qt4/mkspecs/features/qt_config.prf:
    /usr/local/share/qt4/mkspecs/features/exclusive_builds.prf:
    /usr/local/share/qt4/mkspecs/features/default_pre.prf:
    /usr/local/share/qt4/mkspecs/features/release.prf:
    /usr/local/share/qt4/mkspecs/features/default_post.prf:
    /usr/local/share/qt4/mkspecs/features/unix/thread.prf:
    /usr/local/share/qt4/mkspecs/features/warn_on.prf:
    /usr/local/share/qt4/mkspecs/features/qt.prf:
    /usr/local/share/qt4/mkspecs/features/moc.prf:
    /usr/local/share/qt4/mkspecs/features/resources.prf:
    /usr/local/share/qt4/mkspecs/features/uic.prf:
    /usr/local/share/qt4/mkspecs/features/yacc.prf:
    /usr/local/share/qt4/mkspecs/features/lex.prf:
    /usr/local/lib/qt4/libQtSql.prl:
    /usr/local/lib/qt4/libQtCore.prl:
    /usr/local/lib/qt4/libQtGui.prl:
    qmake:  FORCE
            @$(QMAKE) -unix -o Makefile pro.pro
    
    dist:
            @$(CHK_DIR_EXISTS) .tmp/link-up1.0.0 || $(MKDIR) .tmp/link-up1.0.0
            $(COPY_FILE) --parents $(SOURCES) $(DIST) .tmp/link-up1.0.0/ &amp;&amp; $(COPY_FILE) --parents main.cpp .tmp/link-up1.0.0/ &amp;&amp; (cd `dirname .tmp/link-up1.0.0` &amp;&amp; $(TAR) link-up1.0.0.tar link-up1.0.0 &amp;&amp; $(COMPRESS) link-up1.0.0.tar) &amp;&amp; $(MOVE) `dirname .tmp/link-up1.0.0`/link-up1.0.0.tar.gz . &amp;&amp; $(DEL_FILE) -r .tmp/link-up1.0.0
    
    
    clean:compiler_clean
            -$(DEL_FILE) $(OBJECTS)
            -$(DEL_FILE) *~ core *.core
    
    
    ####### Sub-libraries
    
    distclean: clean
            -$(DEL_FILE) $(TARGET)
            -$(DEL_FILE) Makefile
    
    
    mocclean: compiler_moc_header_clean compiler_moc_source_clean
    
    mocables: compiler_moc_header_make_all compiler_moc_source_make_all
    
    compiler_moc_header_make_all:
    compiler_moc_header_clean:
    compiler_rcc_make_all:
    compiler_rcc_clean:
    compiler_image_collection_make_all: qmake_image_collection.cpp
    compiler_image_collection_clean:
            -$(DEL_FILE) qmake_image_collection.cpp
    compiler_moc_source_make_all:
    compiler_moc_source_clean:
    compiler_uic_make_all:
    compiler_uic_clean:
    compiler_yacc_decl_make_all:
    compiler_yacc_decl_clean:
    compiler_yacc_impl_make_all:
    compiler_yacc_impl_clean:
    compiler_lex_make_all:
    compiler_lex_clean:
    compiler_clean:
    
    ####### Compile
    
    main.o: main.cpp
            $(CXX) -c $(CXXFLAGS) $(INCPATH) -o main.o main.cpp
    
    ####### Install
    
    install:   FORCE
    
    uninstall:   FORCE
    
    FORCE:</p></div>
    ";i:5;s:10476:"
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
    </pre></td><td class="code"><pre class="cpp" style="font-family:monospace;"><span style="color: #000040;">--</span> phpMyAdmin SQL Dump
    <span style="color: #000040;">--</span> version 3.1.2
    <span style="color: #000040;">--</span> http<span style="color: #008080;">:</span><span style="color: #666666;">//www.phpmyadmin.net</span>
    <span style="color: #000040;">--</span>
    SET SQL_MODE<span style="color: #000080;">=</span><span style="color: #FF0000;">&quot;NO_AUTO_VALUE_ON_ZERO&quot;</span><span style="color: #008080;">;</span>
    &nbsp;
    <span style="color: #000040;">--</span>
    <span style="color: #000040;">--</span> База данных<span style="color: #008080;">:</span> `bezlim`
    <span style="color: #000040;">--</span>
    &nbsp;
    <span style="color: #000040;">--</span> <span style="color: #000040;">--------------------------------------------------------</span>
    &nbsp;
    <span style="color: #000040;">--</span>
    <span style="color: #000040;">--</span> Структура таблицы `all`
    <span style="color: #000040;">--</span>
    &nbsp;
    DROP TABLE IF EXISTS `all`<span style="color: #008080;">;</span>
    CREATE TABLE IF NOT EXISTS `all` <span style="color: #008000;">&#40;</span>
      `ip` varchar<span style="color: #008000;">&#40;</span><span style="color: #0000dd;">48</span><span style="color: #008000;">&#41;</span> NOT <span style="color: #0000ff;">NULL</span> <span style="color: #0000ff;">default</span> <span style="color: #FF0000;">'192.168.0.1'</span>,
      `rule` <span style="color: #0000ff;">int</span><span style="color: #008000;">&#40;</span><span style="color: #0000dd;">32</span><span style="color: #008000;">&#41;</span> NOT <span style="color: #0000ff;">NULL</span> <span style="color: #0000ff;">default</span> <span style="color: #FF0000;">'500'</span>,
      `bw1` varchar<span style="color: #008000;">&#40;</span><span style="color: #0000dd;">12</span><span style="color: #008000;">&#41;</span> NOT <span style="color: #0000ff;">NULL</span> <span style="color: #0000ff;">default</span> <span style="color: #FF0000;">'0'</span>,
      `bw2` varchar<span style="color: #008000;">&#40;</span><span style="color: #0000dd;">12</span><span style="color: #008000;">&#41;</span> NOT <span style="color: #0000ff;">NULL</span> <span style="color: #0000ff;">default</span> <span style="color: #FF0000;">'0'</span>,
      `activ` <span style="color: #0000ff;">char</span><span style="color: #008000;">&#40;</span><span style="color: #0000dd;">1</span><span style="color: #008000;">&#41;</span> NOT <span style="color: #0000ff;">NULL</span> <span style="color: #0000ff;">default</span> <span style="color: #FF0000;">'y'</span>,
      `id` <span style="color: #0000ff;">int</span><span style="color: #008000;">&#40;</span><span style="color: #0000dd;">32</span><span style="color: #008000;">&#41;</span> NOT <span style="color: #0000ff;">NULL</span> auto_increment,
      PRIMARY KEY  <span style="color: #008000;">&#40;</span>`id`<span style="color: #008000;">&#41;</span>,
      UNIQUE KEY `ip` <span style="color: #008000;">&#40;</span>`ip`<span style="color: #008000;">&#41;</span>
    <span style="color: #008000;">&#41;</span> ENGINE<span style="color: #000080;">=</span>MyISAM  DEFAULT CHARSET<span style="color: #000080;">=</span>latin1 AUTO_INCREMENT<span style="color: #000080;">=</span><span style="color: #0000dd;">3326</span> <span style="color: #008080;">;</span>
    &nbsp;
    &nbsp;
    &nbsp;
    <span style="color: #000040;">--</span>
    <span style="color: #000040;">--</span> База данных<span style="color: #008080;">:</span> `freenibs`
    <span style="color: #000040;">--</span>
    &nbsp;
    <span style="color: #000040;">--</span> <span style="color: #000040;">--------------------------------------------------------</span>
    &nbsp;
    <span style="color: #000040;">--</span> <span style="color: #000040;">--------------------------------------------------------</span>
    &nbsp;
    <span style="color: #000040;">--</span>
    <span style="color: #000040;">--</span> Структура таблицы `pipes`
    <span style="color: #000040;">--</span>
    &nbsp;
    DROP TABLE IF EXISTS `pipes`<span style="color: #008080;">;</span>
    CREATE TABLE IF NOT EXISTS `pipes` <span style="color: #008000;">&#40;</span>
      `id` <span style="color: #0000ff;">int</span><span style="color: #008000;">&#40;</span><span style="color: #0000dd;">255</span><span style="color: #008000;">&#41;</span> NOT <span style="color: #0000ff;">NULL</span> auto_increment,
      `n` <span style="color: #0000ff;">int</span><span style="color: #008000;">&#40;</span><span style="color: #0000dd;">255</span><span style="color: #008000;">&#41;</span> NOT <span style="color: #0000ff;">NULL</span> <span style="color: #0000ff;">default</span> <span style="color: #FF0000;">'11'</span>,
      `bw` <span style="color: #0000ff;">int</span><span style="color: #008000;">&#40;</span><span style="color: #0000dd;">255</span><span style="color: #008000;">&#41;</span> <span style="color: #0000ff;">default</span> <span style="color: #FF0000;">'0'</span>,
      PRIMARY KEY  <span style="color: #008000;">&#40;</span>`id`<span style="color: #008000;">&#41;</span>,
      UNIQUE KEY `bw` <span style="color: #008000;">&#40;</span>`bw`<span style="color: #008000;">&#41;</span>
    <span style="color: #008000;">&#41;</span> ENGINE<span style="color: #000080;">=</span>MyISAM  DEFAULT CHARSET<span style="color: #000080;">=</span>utf8 AUTO_INCREMENT<span style="color: #000080;">=</span><span style="color: #0000dd;">63</span> <span style="color: #008080;">;</span>
    &nbsp;
    <span style="color: #000040;">--</span>
    <span style="color: #000040;">--</span> Дамп данных таблицы `pipes`
    <span style="color: #000040;">--</span>
    &nbsp;
    <span style="color: #000040;">--</span>
    <span style="color: #000040;">--</span> Структура таблицы `updown`
    <span style="color: #000040;">--</span>
    &nbsp;
    DROP TABLE IF EXISTS `updown`<span style="color: #008080;">;</span>
    CREATE TABLE IF NOT EXISTS `updown` <span style="color: #008000;">&#40;</span>
      `id` bigint<span style="color: #008000;">&#40;</span><span style="color: #0000dd;">255</span><span style="color: #008000;">&#41;</span> NOT <span style="color: #0000ff;">NULL</span> auto_increment,
      `ip` varchar<span style="color: #008000;">&#40;</span><span style="color: #0000dd;">100</span><span style="color: #008000;">&#41;</span> NOT <span style="color: #0000ff;">NULL</span> <span style="color: #0000ff;">default</span> <span style="color: #FF0000;">'0.0.0.0'</span>,
      `<span style="color: #0000dd;">time</span>` timestamp NOT <span style="color: #0000ff;">NULL</span> <span style="color: #0000ff;">default</span> CURRENT_TIMESTAMP,
      `status` <span style="color: #0000ff;">enum</span><span style="color: #008000;">&#40;</span><span style="color: #FF0000;">'up'</span>,<span style="color: #FF0000;">'down'</span><span style="color: #008000;">&#41;</span> NOT <span style="color: #0000ff;">NULL</span>,
      PRIMARY KEY  <span style="color: #008000;">&#40;</span>`id`<span style="color: #008000;">&#41;</span>
    <span style="color: #008000;">&#41;</span> ENGINE<span style="color: #000080;">=</span>MyISAM  DEFAULT CHARSET<span style="color: #000080;">=</span>latin1 AUTO_INCREMENT<span style="color: #000080;">=</span><span style="color: #0000dd;">1758553</span> <span style="color: #008080;">;</span>
    &nbsp;
    <span style="color: #000040;">--</span>
    <span style="color: #000040;">--</span> Триггеры `updown`
    <span style="color: #000040;">--</span>
    DROP TRIGGER IF EXISTS `freenibs`.`inserttest`<span style="color: #008080;">;</span>
    DELIMITER <span style="color: #666666;">//</span>
    CREATE TRIGGER `freenibs`.`inserttest` BEFORE INSERT ON `freenibs`.`updown`
     FOR EACH ROW BEGIN
    UPDATE `users` SET `users`.`up_n`<span style="color: #000080;">=</span>`users`.`up_n`<span style="color: #000040;">+</span><span style="color: #0000dd;">1</span> WHERE `users`.`framed_ip`<span style="color: #000080;">=</span>NEW.<span style="color: #007788;">ip</span><span style="color: #008080;">;</span>
    END
    <span style="color: #666666;">//</span>
    DELIMITER <span style="color: #008080;">;</span></pre></td></tr></table><p class="theCode" style="display:none;">-- phpMyAdmin SQL Dump
    -- version 3.1.2
    -- http://www.phpmyadmin.net
    --
    SET SQL_MODE=&quot;NO_AUTO_VALUE_ON_ZERO&quot;;
    
    --
    -- База данных: `bezlim`
    --
    
    -- --------------------------------------------------------
    
    --
    -- Структура таблицы `all`
    --
    
    DROP TABLE IF EXISTS `all`;
    CREATE TABLE IF NOT EXISTS `all` (
      `ip` varchar(48) NOT NULL default '192.168.0.1',
      `rule` int(32) NOT NULL default '500',
      `bw1` varchar(12) NOT NULL default '0',
      `bw2` varchar(12) NOT NULL default '0',
      `activ` char(1) NOT NULL default 'y',
      `id` int(32) NOT NULL auto_increment,
      PRIMARY KEY  (`id`),
      UNIQUE KEY `ip` (`ip`)
    ) ENGINE=MyISAM  DEFAULT CHARSET=latin1 AUTO_INCREMENT=3326 ;
    
    
    
    --
    -- База данных: `freenibs`
    --
    
    -- --------------------------------------------------------
    
    -- --------------------------------------------------------
    
    --
    -- Структура таблицы `pipes`
    --
    
    DROP TABLE IF EXISTS `pipes`;
    CREATE TABLE IF NOT EXISTS `pipes` (
      `id` int(255) NOT NULL auto_increment,
      `n` int(255) NOT NULL default '11',
      `bw` int(255) default '0',
      PRIMARY KEY  (`id`),
      UNIQUE KEY `bw` (`bw`)
    ) ENGINE=MyISAM  DEFAULT CHARSET=utf8 AUTO_INCREMENT=63 ;
    
    --
    -- Дамп данных таблицы `pipes`
    --
    
    --
    -- Структура таблицы `updown`
    --
    
    DROP TABLE IF EXISTS `updown`;
    CREATE TABLE IF NOT EXISTS `updown` (
      `id` bigint(255) NOT NULL auto_increment,
      `ip` varchar(100) NOT NULL default '0.0.0.0',
      `time` timestamp NOT NULL default CURRENT_TIMESTAMP,
      `status` enum('up','down') NOT NULL,
      PRIMARY KEY  (`id`)
    ) ENGINE=MyISAM  DEFAULT CHARSET=latin1 AUTO_INCREMENT=1758553 ;
    
    --
    -- Триггеры `updown`
    --
    DROP TRIGGER IF EXISTS `freenibs`.`inserttest`;
    DELIMITER //
    CREATE TRIGGER `freenibs`.`inserttest` BEFORE INSERT ON `freenibs`.`updown`
     FOR EACH ROW BEGIN
    UPDATE `users` SET `users`.`up_n`=`users`.`up_n`+1 WHERE `users`.`framed_ip`=NEW.ip;
    END
    //
    DELIMITER ;</p></div>
    ";}
categories:
  - billing
  - дополнения
tags:
  - freeNIBS
  - ipfw
  - ipfw nat
  - link up
  - mpd5
  - mysql
  - nat
  - ng_car
  - pf
  - pfctl
  - pfnat

---
Скрипт /usr/local/etc/mpd5/link-up для mpd5 срабатывающий при подключении.
  
При подключении:
  
Первым SELECT&#8217;ом из базы Мы смотрим &#8212; Натить ли пользователя? То есть если emty или 0 пользователей &#8212; не натим.
   
Вторым SELECT&#8217;ом из базы Мы смотрим &#8212; Надо ли менять скорость пользователя, если надо &#8212; меняем. У меня это сделано на ipfw pipe, но думаю перейти на ng_car:)))
   
Третим SELECT&#8217;ом из базы Мы &#8212; добавляем запись в базу данных, что пользователь подключился. 

С помощью данного скрипта Я решал следующую проблему:
  
Быстродействие &#8212; на php тормозило. Хотя может и руки из жо)))

Подключается скрипт в /usr/local/etc/mpd5/mpd.conf так вот, в секцию с вашим сервером (pptp/pppoe/etc)<!--more-->

<pre lang="php">set iface up-script /usr/local/etc/mpd5/
</pre>

Обязательно примите к сведению, что запрос 

<pre lang="sql" line="1">SELECT * FROM `all` WHERE `ip` not LIKE '91.%' 
</pre>

а именно его часть: \`ip\` not LIKE &#8217;91.%&#8217; добавлен, что бы НАТ не включался для реальных IP-адресов.
  
У Вас могут быть другие адреса )))

main.cpp :

<pre lang="cpp" line="1">#include &lt;QtCore>
#include &lt;QCoreApplication>
#include &lt;QtSql>
#include &lt;iostream>
#include &lt;cstdlib>
#include &lt;iomanip>
#include &lt;stdio.h>
#include &lt;stdlib.h>
#include &lt;string.h>
#include &lt;time.h>
using namespace std;


#define SQLDRIVER "QMYSQL"
#define HOST "10.1.1.1"
#define DBNAME "bezlim"
#define USER "bezlim"
#define PASSWORD "bezlim"

int main(int argc, char *argv[])
{
    QCoreApplication a(argc, argv);

    QTextCodec *codec = QTextCodec::codecForName("CP1251");
    QTextCodec::setCodecForTr(codec);
    QTextCodec::setCodecForCStrings(codec);

    QSqlDatabase db = QSqlDatabase::addDatabase(SQLDRIVER);

    if( !db.isDriverAvailable(SQLDRIVER))
    {

    }


    db.setHostName(HOST);
    db.setDatabaseName(DBNAME);
    db.setUserName(USER);
    db.setPassword(PASSWORD);
    //db.setPort(3306);
    bool ok=db.open();
    if(ok!=true){
        std::cout&lt;&lt;"unable connec't";
        exit(1);
    }
     QString exec_this;
     int bw1;

     QString ip_argv;
     ip_argv=argv[4];

     //qDebug()&lt;&lt;ip_argv;

     QSqlQuery query("SELECT * FROM `all` WHERE `ip` not LIKE '91.%' AND `activ`='y' AND `ip`='"+ip_argv+"' LIMIT 1");
     while (query.next()) {
         QString id = query.value(5).toString();

         QString ip = query.value(0).toString();
         QString in = query.value(3).toString();
         QString out = query.value(4).toString();
         QString n = query.value(1).toString();
         bw1 =query.value(3).toInt();
         QString bw2 =query.value(3).toString();
//pfctl - это закомментированная часть для pf nat
//      exec_this="/sbin/pfctl -tinat -Tadd ";
//      exec_this +=ip;
//      qDebug()&lt;&lt;exec_this&lt;&lt;endl;

        exec_this ="/sbin/ipfw table 1 add ";
        exec_this +=ip;

        system(exec_this.toStdString().c_str());


    }
        qDebug()&lt;&lt;ip_argv&lt;&lt;endl;

        qDebug()&lt;&lt;exec_this&lt;&lt;endl;

     QSqlQuery query11("SELECT * FROM `all` WHERE `activ`='y' AND `ip`='"+ip_argv+"' LIMIT 1");
     while (query11.next()) {
//pfctl это закомментированная часть для pf nat
//      exec_this="/sbin/pfctl -tinat -Tadd ";
//      exec_this +=ip;
//      qDebug()&lt;&lt;exec_this&lt;&lt;endl;

         QString id = query11.value(5).toString();

         QString ip = query11.value(0).toString();
         QString in = query11.value(3).toString();
         QString out = query11.value(4).toString();
         QString n = query11.value(1).toString();
         bw1 =query11.value(3).toInt();
         QString bw2 =query11.value(3).toString();


      //Эта часть у Меня отвечает за выделение скорости. Я использовал ipfw pipe
        if(bw1>0)
        {
            qint64 num = 0;
            QString num1;
            query.clear();
             QSqlQuery query("SELECT * FROM `freenibs`.`pipes` WHERE `freenibs`.`pipes`.`bw`='"+bw2+"' LIMIT 1");
            //qDebug()&lt;&lt;"SELECT `freenibs`.`pipes`.`n` FROM `freenibs`.`pipes` WHERE `freenibs`.`pipes`.`bw`='"+bw2+"' LIMIT 1"&lt;&lt;endl;
             while (query.next()) {
                    num = query.value(1).toInt();
                    num1 = query.value(1).toString();
                }
            query.clear();
            if(num>0)
            {
                    //qDebug()&lt;&lt;"NUM>0|"&lt;&lt;num1&lt;&lt;"|"&lt;&lt;endl;
                    exec_this ="/sbin/ipfw pipe ";
                    exec_this +=num1;
                    exec_this +=" config mask dst-ip 0x000000ff bw ";
                    exec_this +=bw2;
                    exec_this +="Kbit/s";
                    system(exec_this.toStdString().c_str());
                    //qDebug()&lt;&lt;exec_this&lt;&lt;endl;
                    exec_this ="/sbin/ipfw table ";
                    exec_this +=num1;
                    exec_this +=" add ";
                    exec_this +=ip;
                    system(exec_this.toStdString().c_str());
                    //qDebug()&lt;&lt;exec_this&lt;&lt;endl;
            }
            else
            {
                    QSqlQuery query1(" SELECT MAX(`n`)+1  FROM `freenibs`.`pipes` ");
                    //qDebug()&lt;&lt;num&lt;&lt;endl;
                    // qDebug()&lt;&lt;query1.lastError()&lt;&lt;endl;
                    // query.exec();
                     //qDebug()&lt;&lt;query1.lastError()&lt;&lt;endl;
                     while (query1.next()) {
                            //num = query1.value(0).toInt();
                            num1 = query1.value(0).toString();
                        }
                    //qDebug()&lt;&lt;"NUM:"&lt;&lt;num1&lt;&lt;endl;
                     //QSqlQuery
                     query.prepare("INSERT INTO `freenibs`.`pipes`  ( `bw`,`n`) values( '" +bw2+ "','"+num1+"')");
                    // qDebug()&lt;&lt;query.lastError()&lt;&lt;endl;
                     query.exec();

                    exec_this ="/sbin/ipfw delete ";
                    exec_this +=num1;
                    system(exec_this.toStdString().c_str());
                    //qDebug()&lt;&lt;exec_this&lt;&lt;endl;

                    exec_this ="/sbin/ipfw pipe ";
                    exec_this +=num1;
                    exec_this +=" config mask dst-ip 0x000000ff bw ";
                    exec_this +=bw2;
                    exec_this +="Kbit/s";
                    system(exec_this.toStdString().c_str());
                    //qDebug()&lt;&lt;exec_this&lt;&lt;endl;

                    exec_this ="/sbin/ipfw -q add ";
                    exec_this +=num1;
                    exec_this +=" pipe ";
                    exec_this +=num1;
                    exec_this +=" all from table\\(";
                    exec_this +=num1;
                    exec_this +="\\) to not 10.0.0.0/8 out";
                    system(exec_this.toStdString().c_str());
                    //qDebug()&lt;&lt;exec_this&lt;&lt;endl;


                    exec_this ="/sbin/ipfw -q add ";
                    exec_this +=num1;
                    exec_this +=" pipe ";
                    exec_this +=num1;
                    exec_this +=" all from not 10.0.0.0/8 to table\\(";
                    exec_this +=num1;
                    exec_this +="\\) in ";
                    system(exec_this.toStdString().c_str());
                    //qDebug()&lt;&lt;exec_this&lt;&lt;endl;


                    exec_this ="/sbin/ipfw table ";
                    exec_this +=num1;
                    exec_this += " add ";
                    exec_this +=ip;
                    system(exec_this.toStdString().c_str());
                    //qDebug()&lt;&lt;exec_this&lt;&lt;endl;
            }
        }

       //здесь Мы заполняем таблицу для того, что бы видеть что пользователь подключился
        QSqlQuery query("INSERT INTO `freenibs`.`updown` (`ip` ,`time` ,`status`) VALUES ( '"+ip_argv+"',CURRENT_TIMESTAMP , 'up');");
        query.clear();
    }
     db.close();
//    return a.exec();
}
</pre>

Makefile

<pre lang="make" line="1">#############################################################################
# Makefile for building: link-up
# Generated by qmake (2.01a) (Qt 4.4.3) on: Thu Jul 23 00:40:54 2009
# Project:  pro.pro
# Template: app
# Command: /usr/local/bin/qmake-qt4 -unix -o Makefile pro.pro
#############################################################################

####### Compiler, tools and options

CC            = cc
CXX           = c++
DEFINES       = -DQT_NO_DEBUG -DQT_SQL_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED
CFLAGS        = -pipe -O2 -fno-strict-aliasing -pipe -Wall -W $(DEFINES)
CXXFLAGS      = -pipe -O2 -fno-strict-aliasing -pipe -Wall -W $(DEFINES)
INCPATH       = -I/usr/local/share/qt4/mkspecs/freebsd-g++ -I. -I/usr/local/include/qt4/QtCore -I/usr/local/include/qt4/QtCore -I/usr/local/include/qt4/QtGui -I/usr/local/include/qt4/QtGui -I/usr/local/include/qt4/QtSql -I/usr/local/include/qt4/QtSql -I/usr/local/include/qt4 -I. -I. -I/usr/local/include
LINK          = c++
LFLAGS        = -pthread -Wl,-rpath,/usr/local/lib/qt4
LIBS          = $(SUBLIBS)  -L/usr/local/lib -L/usr/local/lib/qt4 -lQtSql -L/usr/local/lib/qt4 -L/usr/local/lib -pthread -pthread -lQtGui -pthread -lpng -lSM -lICE -pthread -pthread -lXi -lXrender -lXrandr -lfreetype -lfontconfig -lXext -lX11 -lQtCore -lz -lm -pthread -lgthread-2.0 -lglib-2.0 -liconv
AR            = ar cqs
RANLIB        =
QMAKE         = /usr/local/bin/qmake-qt4
TAR           = tar -cf
COMPRESS      = gzip -9f
COPY          = cp -f
SED           = sed
COPY_FILE     = $(COPY)
COPY_DIR      = $(COPY) -R
INSTALL_FILE  = $(COPY_FILE)
INSTALL_DIR   = $(COPY_DIR)
INSTALL_PROGRAM = $(COPY_FILE)
DEL_FILE      = rm -f
SYMLINK       = ln -sf
DEL_DIR       = rmdir
MOVE          = mv -f
CHK_DIR_EXISTS= test -d
MKDIR         = mkdir -p

####### Output directory

OBJECTS_DIR   = ./

####### Files

SOURCES       = main.cpp
OBJECTS       = main.o
DIST          = /usr/local/share/qt4/mkspecs/common/unix.conf \
                /usr/local/share/qt4/mkspecs/qconfig.pri \
                /usr/local/share/qt4/mkspecs/features/qt_functions.prf \
                /usr/local/share/qt4/mkspecs/features/qt_config.prf \
                /usr/local/share/qt4/mkspecs/features/exclusive_builds.prf \
                /usr/local/share/qt4/mkspecs/features/default_pre.prf \
                /usr/local/share/qt4/mkspecs/features/release.prf \
                /usr/local/share/qt4/mkspecs/features/default_post.prf \
                /usr/local/share/qt4/mkspecs/features/unix/thread.prf \
                /usr/local/share/qt4/mkspecs/features/warn_on.prf \
                /usr/local/share/qt4/mkspecs/features/qt.prf \
                /usr/local/share/qt4/mkspecs/features/moc.prf \
                /usr/local/share/qt4/mkspecs/features/resources.prf \
                /usr/local/share/qt4/mkspecs/features/uic.prf \
                /usr/local/share/qt4/mkspecs/features/yacc.prf \
                /usr/local/share/qt4/mkspecs/features/lex.prf \
                pro.pro
QMAKE_TARGET  = link-up
DESTDIR       =
TARGET        = link-up

first: all
####### Implicit rules

.SUFFIXES: .o .c .cpp .cc .cxx .C

.cpp.o:
        $(CXX) -c $(CXXFLAGS) $(INCPATH) -o "$@" "$&lt;"

.cc.o:
        $(CXX) -c $(CXXFLAGS) $(INCPATH) -o "$@" "$&lt;"

.cxx.o:
        $(CXX) -c $(CXXFLAGS) $(INCPATH) -o "$@" "$&lt;"

.C.o:
        $(CXX) -c $(CXXFLAGS) $(INCPATH) -o "$@" "$&lt;"

.c.o:
        $(CC) -c $(CFLAGS) $(INCPATH) -o "$@" "$&lt;"

####### Build rules

all: Makefile $(TARGET)

$(TARGET):  $(OBJECTS)
        $(LINK) $(LFLAGS) -o $(TARGET) $(OBJECTS) $(OBJCOMP) $(LIBS)

Makefile: pro.pro  /usr/local/share/qt4/mkspecs/freebsd-g++/qmake.conf /usr/local/share/qt4/mkspecs/common/unix.conf \
                /usr/local/share/qt4/mkspecs/qconfig.pri \
                /usr/local/share/qt4/mkspecs/features/qt_functions.prf \
                /usr/local/share/qt4/mkspecs/features/qt_config.prf \
                /usr/local/share/qt4/mkspecs/features/exclusive_builds.prf \
                /usr/local/share/qt4/mkspecs/features/default_pre.prf \
                /usr/local/share/qt4/mkspecs/features/release.prf \
                /usr/local/share/qt4/mkspecs/features/default_post.prf \
                /usr/local/share/qt4/mkspecs/features/unix/thread.prf \
                /usr/local/share/qt4/mkspecs/features/warn_on.prf \
                /usr/local/share/qt4/mkspecs/features/qt.prf \
                /usr/local/share/qt4/mkspecs/features/moc.prf \
                /usr/local/share/qt4/mkspecs/features/resources.prf \
                /usr/local/share/qt4/mkspecs/features/uic.prf \
                /usr/local/share/qt4/mkspecs/features/yacc.prf \
                /usr/local/share/qt4/mkspecs/features/lex.prf \
                /usr/local/lib/qt4/libQtSql.prl \
                /usr/local/lib/qt4/libQtCore.prl \
                /usr/local/lib/qt4/libQtGui.prl
        $(QMAKE) -unix -o Makefile pro.pro
/usr/local/share/qt4/mkspecs/common/unix.conf:
/usr/local/share/qt4/mkspecs/qconfig.pri:
/usr/local/share/qt4/mkspecs/features/qt_functions.prf:
/usr/local/share/qt4/mkspecs/features/qt_config.prf:
/usr/local/share/qt4/mkspecs/features/exclusive_builds.prf:
/usr/local/share/qt4/mkspecs/features/default_pre.prf:
/usr/local/share/qt4/mkspecs/features/release.prf:
/usr/local/share/qt4/mkspecs/features/default_post.prf:
/usr/local/share/qt4/mkspecs/features/unix/thread.prf:
/usr/local/share/qt4/mkspecs/features/warn_on.prf:
/usr/local/share/qt4/mkspecs/features/qt.prf:
/usr/local/share/qt4/mkspecs/features/moc.prf:
/usr/local/share/qt4/mkspecs/features/resources.prf:
/usr/local/share/qt4/mkspecs/features/uic.prf:
/usr/local/share/qt4/mkspecs/features/yacc.prf:
/usr/local/share/qt4/mkspecs/features/lex.prf:
/usr/local/lib/qt4/libQtSql.prl:
/usr/local/lib/qt4/libQtCore.prl:
/usr/local/lib/qt4/libQtGui.prl:
qmake:  FORCE
        @$(QMAKE) -unix -o Makefile pro.pro

dist:
        @$(CHK_DIR_EXISTS) .tmp/link-up1.0.0 || $(MKDIR) .tmp/link-up1.0.0
        $(COPY_FILE) --parents $(SOURCES) $(DIST) .tmp/link-up1.0.0/ &#038;&#038; $(COPY_FILE) --parents main.cpp .tmp/link-up1.0.0/ &#038;&#038; (cd `dirname .tmp/link-up1.0.0` &#038;&#038; $(TAR) link-up1.0.0.tar link-up1.0.0 &#038;&#038; $(COMPRESS) link-up1.0.0.tar) &#038;&#038; $(MOVE) `dirname .tmp/link-up1.0.0`/link-up1.0.0.tar.gz . &#038;&#038; $(DEL_FILE) -r .tmp/link-up1.0.0


clean:compiler_clean
        -$(DEL_FILE) $(OBJECTS)
        -$(DEL_FILE) *~ core *.core


####### Sub-libraries

distclean: clean
        -$(DEL_FILE) $(TARGET)
        -$(DEL_FILE) Makefile


mocclean: compiler_moc_header_clean compiler_moc_source_clean

mocables: compiler_moc_header_make_all compiler_moc_source_make_all

compiler_moc_header_make_all:
compiler_moc_header_clean:
compiler_rcc_make_all:
compiler_rcc_clean:
compiler_image_collection_make_all: qmake_image_collection.cpp
compiler_image_collection_clean:
        -$(DEL_FILE) qmake_image_collection.cpp
compiler_moc_source_make_all:
compiler_moc_source_clean:
compiler_uic_make_all:
compiler_uic_clean:
compiler_yacc_decl_make_all:
compiler_yacc_decl_clean:
compiler_yacc_impl_make_all:
compiler_yacc_impl_clean:
compiler_lex_make_all:
compiler_lex_clean:
compiler_clean:

####### Compile

main.o: main.cpp
        $(CXX) -c $(CXXFLAGS) $(INCPATH) -o main.o main.cpp

####### Install

install:   FORCE

uninstall:   FORCE

FORCE:


</pre>

дамп базы:

<pre lang="cpp" line="1">-- phpMyAdmin SQL Dump
-- version 3.1.2
-- http://www.phpmyadmin.net
--
SET SQL_MODE="NO_AUTO_VALUE_ON_ZERO";

--
-- База данных: `bezlim`
--

-- --------------------------------------------------------

--
-- Структура таблицы `all`
--

DROP TABLE IF EXISTS `all`;
CREATE TABLE IF NOT EXISTS `all` (
  `ip` varchar(48) NOT NULL default '192.168.0.1',
  `rule` int(32) NOT NULL default '500',
  `bw1` varchar(12) NOT NULL default '0',
  `bw2` varchar(12) NOT NULL default '0',
  `activ` char(1) NOT NULL default 'y',
  `id` int(32) NOT NULL auto_increment,
  PRIMARY KEY  (`id`),
  UNIQUE KEY `ip` (`ip`)
) ENGINE=MyISAM  DEFAULT CHARSET=latin1 AUTO_INCREMENT=3326 ;



--
-- База данных: `freenibs`
--

-- --------------------------------------------------------

-- --------------------------------------------------------

--
-- Структура таблицы `pipes`
--

DROP TABLE IF EXISTS `pipes`;
CREATE TABLE IF NOT EXISTS `pipes` (
  `id` int(255) NOT NULL auto_increment,
  `n` int(255) NOT NULL default '11',
  `bw` int(255) default '0',
  PRIMARY KEY  (`id`),
  UNIQUE KEY `bw` (`bw`)
) ENGINE=MyISAM  DEFAULT CHARSET=utf8 AUTO_INCREMENT=63 ;

--
-- Дамп данных таблицы `pipes`
--

--
-- Структура таблицы `updown`
--

DROP TABLE IF EXISTS `updown`;
CREATE TABLE IF NOT EXISTS `updown` (
  `id` bigint(255) NOT NULL auto_increment,
  `ip` varchar(100) NOT NULL default '0.0.0.0',
  `time` timestamp NOT NULL default CURRENT_TIMESTAMP,
  `status` enum('up','down') NOT NULL,
  PRIMARY KEY  (`id`)
) ENGINE=MyISAM  DEFAULT CHARSET=latin1 AUTO_INCREMENT=1758553 ;

--
-- Триггеры `updown`
--
DROP TRIGGER IF EXISTS `freenibs`.`inserttest`;
DELIMITER //
CREATE TRIGGER `freenibs`.`inserttest` BEFORE INSERT ON `freenibs`.`updown`
 FOR EACH ROW BEGIN
UPDATE `users` SET `users`.`up_n`=`users`.`up_n`+1 WHERE `users`.`framed_ip`=NEW.ip;
END
//
DELIMITER ;



</pre>