---
title: bottom.php
author: wel
type: post
date: 2012-01-14T23:22:58+00:00
url: /billing/bottom-php
wp-syntax-cache-content:
  - |
    a:1:{i:1;s:1338:"
    <div class="wp_syntax" style="position:relative;"><table><tr><td class="code"><pre class="php" style="font-family:monospace;"><span style="color: #000000; font-weight: bold;">&lt;?php</span>
    <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$LINK</span><span style="color: #009900;">&#41;</span> <span style="color: #339933;">@</span><span style="color: #990000;">mysql_close</span><span style="color: #009900;">&#40;</span><span style="color: #000088;">$LINK</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #b1b100;">if</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$LINK_POSTFIX</span><span style="color: #009900;">&#41;</span> <span style="color: #339933;">@</span><span style="color: #990000;">mysql_close</span> <span style="color: #009900;">&#40;</span><span style="color: #000088;">$LINK_POSTFIX</span><span style="color: #009900;">&#41;</span><span style="color: #339933;">;</span>
    <span style="color: #000000; font-weight: bold;">?&gt;</span>
    &lt;/body&gt;
    &lt;/html&gt;</pre></td></tr></table><p class="theCode" style="display:none;">&lt;?php
    if ($LINK) @mysql_close($LINK);
    if ($LINK_POSTFIX) @mysql_close ($LINK_POSTFIX);
    ?&gt;
    &lt;/body&gt;
    &lt;/html&gt;</p></div>
    ";}
categories:
  - billing
  - FreeNIBS
tags:
  - bottom.php

---
<pre lang="php"><?php
if ($LINK) @mysql_close($LINK);
if ($LINK_POSTFIX) @mysql_close ($LINK_POSTFIX);
?>
&lt;/body>
&lt;/html>

</pre>