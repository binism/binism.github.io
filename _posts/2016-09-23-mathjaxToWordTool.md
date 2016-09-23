---
layout:    post
title:     公式转化页
mathjax:   true
date:      2016-09-23
author:     "BINISM"
header-img:  /images/pages/probability.jpg
---

$$ O \Join C $$

$$ \delta_{aid = 'a001'}(O \Join C) $$

$$ C - \pi_{cid, cname, city, discnt}(\delta_{aid = 'a001'}(O \Join C)) $$

$$ \pi_{cname}(C - \pi_{cid, cname, city, discnt}(\delta_{aid = 'a001'}(O \Join C)) $$

$$ \pi_{cid}(\delta_{city = '南京'}(C)) $$

$$ \pi_{cid,aid}(O) \div \pi_{cid}(\delta_{city = '南京'}(C)) $$

$$ \pi_{aid}(\pi_{cid,aid}(O) \div \pi_{cid}(\delta_{city = '南京'}(C))) $$

$$ \pi_{O.pid,O.oid}(\delta_{O.pid = S.pid \wedge O.dols < S.dols}(O \times S)) $$ 

$$ \pi_{O.pid,O.oid}(O) - \pi_{O.pid,O.oid}(\delta_{O.pid = S.pid \wedge O.dols < S.dols}(O \times S)) $$
