假设 http_proxy 的地址是 127.0.0.1:8118， socks5_proxy 的地址是 127.0.0.1:10100

1、go get 的命令则为 http_proxy=127.0.0.1:8118 go get github.com/nsqio/go-nsq

2、若要将 socks5_proxy 转为 http_proxy，则可使用 privoxy 进行转换

①sudo apt-get install privoxy

②sudo vim /etc/privoxy/config/

  确保文件内容中有如下配置（注意forward-sock5最后的 .）
  
  forward-sock5	/	127.0.0.1:10100	.
  
  listen-address  127.0.0.1:8118
  
③sudo service privoxy restart

至此，http proxy则可投入使用。
