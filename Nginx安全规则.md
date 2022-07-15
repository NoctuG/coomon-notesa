---
created: 2022-07-14T14:21:42.676Z
modified: 2022-07-15T08:58:58.621Z
---
```nginx
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
 #非指定域名访问403

        if ($host != 'XX.XX.XX'){
    return 403; #非指定域名访问返回403
        }
 #仅允许特定IP访问并加上帐号密码验证
root /opt/hostloc/www;
allow  xx.xx.xx.xx;
allow  2xx.xx.x.xx;
deny  all;
auth_basic “test”;
auth_basic_user_file htpasswd;

 #隐藏nginx版本号
http块添加
                       
http {
...
server_tokens off;
...
}
 #防止攻击
if ($request_uri ~* "(\.gz)|(")|(\.tar)|(admin)|(\.zip)|(\.sql)|(\.asp)|(\.rar)|(function)|($_GET)|(eval)|(\?php)|(config)|(\')|(\.bak)") {
return 301 http://lg-dene.fdcservers.net/10GBtest.zip;
}

##禁止下载以 XXX 后缀的文件
location ~ \.(zip|rar|sql|bak|gz|7z)$
{
    return 444;
}


##访问链接里含有 test 直接跳转到公安网
if ($request_uri ~* test=) {
return 301 https://www.mps.gov.cn;
}
if ($http_user_agent ~* (SemrushBot|python|MJ12bot|AhrefsBot|AhrefsBot|hubspot|opensiteexplorer|leiki|webmeup)) {
      return 444;
    }
```