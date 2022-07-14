---
created: 2022-07-14T14:21:42.676Z
modified: 2022-07-14T14:51:02.335Z
---
```nginx
 #请求这些敏感词时跳转下载10g文件
 if ($request_uri ~* "(\.gz)|(")|(\.tar)|(admin)|(\.zip)|(\.sql)|(\.asp)|(\.rar)|(function)|($_GET)|(eval)|(\?php)|(config)|(\')|(\.bak)") {
            return 301 http://lg-dene.fdcservers.net/10GBtest.zip;
        }


 #禁止下载以 XXX 后缀的文件
 location ~ \.(zip|rar|sql|bak|gz|7z)$ 
 { 
   return 444;
  }


 #访问链接里含有 test 直接跳转到公安网
 if ($request_uri ~* test=) {
  return 301 https://www.mps.gov.cn;
 }


 #防止SB爬虫
 if ($http_user_agent ~* (SemrushBot|python|MJ12bot|AhrefsBot|AhrefsBot|hubspot|opensiteexplorer|leiki|webmeup)) {
      return 444;
    }


 #屏蔽非常见蜘蛛爬虫配置
 if ($http_user_agent ~* (SemrushBot|python|MJ12bot|AhrefsBot|AhrefsBot|hubspot|opensiteexplorer|leiki|webmeup)) {
     return 444;
  }


 #禁止某个目录执行脚本
#uploads|templets|data 这些目录禁止执行PHP
 location ~* ^/(uploads|templets|data)/.*.(php|php5)$ {
    return 444;
  }
 #防止爬虫
 if ($http_user_agent ~* (SemrushBot|python|MJ12bot|AhrefsBot|AhrefsBot|hubspot|opensiteexplorer|leiki|webmeup)) {
      return 444;
    }
```