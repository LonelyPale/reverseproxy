# Reverse Proxy Debug Server


## 介绍

TCP 反向代理服务器,监听本地端口,并将请求全部转发到远端,
并将接收到的请求和远端的响应在标准输出中打印出来,方便做网络开发调试
目前支持远端的短连接。



## 范例
<pre>
bin/reverse -l localhost:9000 -r 19.45.79.21:80
1: 127.0.0.1:9000 .-> 127.0.0.1:59627
.................................
00000000  47 45 54 20 2f 73 74 64  6c 69 62 2d 31 2e 39 2e  |GET /stdlib-1.9.|
00000010  33 2f 6c 69 62 64 6f 63  2f 73 6f 63 6b 65 74 2f  |3/libdoc/socket/|
00000020  72 64 6f 63 2f 54 43 50  53 65 72 76 65 72 2e 68  |rdoc/TCPServer.h|
00000030  74 6d 6c e2 80 8e 20 48  54 54 50 2f 31 2e 31 0d  |tml... HTTP/1.1.|
00000040  0a 55 73 65 72 2d 41 67  65 6e 74 3a 20 63 75 72  |.User-Agent: cur|
00000050  6c 2f 37 2e 33 30 2e 30  0d 0a 48 6f 73 74 3a 20  |l/7.30.0..Host: |
00000060  31 32 37 2e 30 2e 30 2e  31 3a 39 30 30 30 0d 0a  |127.0.0.1:9000..|
00000070  41 63 63 65 70 74 3a 20  2a 2f 2a 0d 0a 0d 0a     |Accept: */*....|

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
00000000  48 54 54 50 2f 31 2e 31  20 34 30 34 20 4e 6f 74  |HTTP/1.1 404 Not|
00000010  20 46 6f 75 6e 64 0d 0a  53 65 72 76 65 72 3a 20  | Found..Server: |
00000020  6e 67 69 6e 78 0d 0a 44  61 74 65 3a 20 54 68 75  |nginx..Date: Thu|
00000030  2c 20 32 34 20 41 70 72  20 32 30 31 34 20 30 33  |, 24 Apr 2014 03|
00000040  3a 31 38 3a 34 33 20 47  4d 54 0d 0a 43 6f 6e 74  |:18:43 GMT..Cont|
00000050  65 6e 74 2d 54 79 70 65  3a 20 74 65 78 74 2f 68  |ent-Type: text/h|
00000060  74 6d 6c 3b 20 63 68 61  72 73 65 74 3d 75 74 66  |tml; charset=utf|
00000070  2d 38 0d 0a 43 6f 6e 74  65 6e 74 2d 4c 65 6e 67  |-8..Content-Leng|
00000080  74 68 3a 20 39 34 37 0d  0a 43 6f 6e 6e 65 63 74  |th: 947..Connect|
00000090  69 6f 6e 3a 20 6b 65 65  70 2d 61 6c 69 76 65 0d  |ion: keep-alive.|
000000a0  0a 43 61 63 68 65 2d 43  6f 6e 74 72 6f 6c 3a 20  |.Cache-Control: |
000000b0  6e 6f 2d 63 61 63 68 65  0d 0a 0d 0a 3c 21 44 4f  |no-cache.....!DO|
000000c0  43 54 59 50 45 20 68 74  6d 6c 20 50 55 42 4c 49  |CTYPE html PUBLI|
000000d0  43 20 22 2d 2f 2f 57 33  43 2f 2f 44 54 44 20 58  |C "-//W3C//DTD X|
000000e0  48 54 4d 4c 20 31 2e 30  20 54 72 61 6e 73 69 74  |HTML 1.0 Transit|
000000f0  69 6f 6e 61 6c 2f 2f 45  4e 22 0a 20 20 20 20 20  |ional//EN".     |
00000100  20 20 22 68 74 74 70 3a  2f 2f 77 77 77 2e 77 33  |  "http://www.w3|
00000110  2e 6f 72 67 2f 54 52 2f  78 68 74 6d 6c 31 2f 44  |.org/TR/xhtml1/D|
00000120  54 44 2f 78 68 74 6d 6c  31 2d 74 72 61 6e 73 69  |TD/xhtml1-transi|
00000130  74 69 6f 6e 61 6c 2e 64  74 64 22 3e 0a 0a 3c 68  |tional.dtd">...h|
00000140  74 6d 6c 20 78 6d 6c 6e  73 3d 22 68 74 74 70 3a  |tml xmlns="http:|
00000150  2f 2f 77 77 77 2e 77 33  2e 6f 72 67 2f 31 39 39  |//www.w3.org/199|
00000160  39 2f 78 68 74 6d 6c 22  20 78 6d 6c 3a 6c 61 6e  |9/xhtml" xml:lan|
00000170  67 3d 22 65 6e 22 20 6c  61 6e 67 3d 22 65 6e 22  |g="en" lang="en"|
00000180  3e 0a 0a 3c 68 65 61 64  3e 0a 20 20 3c 6d 65 74  |>...head>.  .met|
00000190  61 20 68 74 74 70 2d 65  71 75 69 76 3d 22 63 6f  |a http-equiv="co|
000001a0  6e 74 65 6e 74 2d 74 79  70 65 22 20 63 6f 6e 74  |ntent-type" cont|
000001b0  65 6e 74 3d 22 74 65 78  74 2f 68 74 6d 6c 3b 20  |ent="text/html; |
000001c0  63 68 61 72 73 65 74 3d  55 54 46 2d 38 22 20 2f  |charset=UTF-8" /|
000001d0  3e 0a 20 20 3c 74 69 74  6c 65 3e 54 68 65 20 70  |>.  .title>The p|
000001e0  61 67 65 20 79 6f 75 20  77 65 72 65 20 6c 6f 6f  |age you were loo|
000001f0  6b 69 6e 67 20 66 6f 72  20 64 6f 65 73 6e 27 74  |king for doesn't|
00000200  20 65 78 69 73 74 20 28  34 30 34 29 3c 2f 74 69  | exist (404)./ti|
00000210  74 6c 65 3e 0a 09 3c 73  74 79 6c 65 20 74 79 70  |tle>...style typ|
00000220  65 3d 22 74 65 78 74 2f  63 73 73 22 3e 0a 09 09  |e="text/css">...|
00000230  62 6f 64 79 20 7b 20 62  61 63 6b 67 72 6f 75 6e  |body { backgroun|
00000240  64 2d 63 6f 6c 6f 72 3a  20 23 66 66 66 3b 20 63  |d-color: #fff; c|
00000250  6f 6c 6f 72 3a 20 23 36  36 36 3b 20 74 65 78 74  |olor: #666; text|
00000260  2d 61 6c 69 67 6e 3a 20  63 65 6e 74 65 72 3b 20  |-align: center; |
00000270  66 6f 6e 74 2d 66 61 6d  69 6c 79 3a 20 61 72 69  |font-family: ari|
00000280  61 6c 2c 20 73 61 6e 73  2d 73 65 72 69 66 3b 20  |al, sans-serif; |
00000290  7d 0a 09 09 64 69 76 2e  64 69 61 6c 6f 67 20 7b  |}...div.dialog {|
000002a0  0a 09 09 09 77 69 64 74  68 3a 20 32 35 65 6d 3b  |....width: 25em;|
000002b0  0a 09 09 09 70 61 64 64  69 6e 67 3a 20 30 20 34  |....padding: 0 4|
000002c0  65 6d 3b 0a 09 09 09 6d  61 72 67 69 6e 3a 20 34  |em;....margin: 4|
000002d0  65 6d 20 61 75 74 6f 20  30 20 61 75 74 6f 3b 0a  |em auto 0 auto;.|
000002e0  09 09 09 62 6f 72 64 65  72 3a 20 31 70 78 20 73  |...border: 1px s|
000002f0  6f 6c 69 64 20 23 63 63  63 3b 0a 09 09 09 62 6f  |olid #ccc;....bo|
00000300  72 64 65 72 2d 72 69 67  68 74 2d 63 6f 6c 6f 72  |rder-right-color|
00000310  3a 20 23 39 39 39 3b 0a  09 09 09 62 6f 72 64 65  |: #999;....borde|
00000320  72 2d 62 6f 74 74 6f 6d  2d 63 6f 6c 6f 72 3a 20  |r-bottom-color: |
00000330  23 39 39 39 3b 0a 09 09  7d 0a 09 09 68 31 20 7b  |#999;...}...h1 {|
00000340  20 66 6f 6e 74 2d 73 69  7a 65 3a 20 31 30 30 25  | font-size: 100%|
00000350  3b 20 63 6f 6c 6f 72 3a  20 23 66 30 30 3b 20 6c  |; color: #f00; l|
00000360  69 6e 65 2d 68 65 69 67  68 74 3a 20 31 2e 35 65  |ine-height: 1.5e|
00000370  6d 3b 20 7d 0a 09 3c 2f  73 74 79 6c 65 3e 0a 3c  |m; }.../style>..|
00000380  2f 68 65 61 64 3e 0a 0a  3c 62 6f 64 79 3e 0a 20  |/head>...body>. |
00000390  20 3c 21 2d 2d 20 54 68  69 73 20 66 69 6c 65 20  | .!-- This file |
000003a0  6c 69 76 65 73 20 69 6e  20 70 75 62 6c 69 63 2f  |lives in public/|
000003b0  34 30 34 2e 68 74 6d 6c  20 2d 2d 3e 0a 20 20 3c  |404.html -->.  .|
000003c0  64 69 76 20 63 6c 61 73  73 3d 22 64 69 61 6c 6f  |div class="dialo|
000003d0  67 22 3e 0a 20 20 20 20  3c 68 31 3e 54 68 65 20  |g">.    .h1>The |
000003e0  70 61 67 65 20 79 6f 75  20 77 65 72 65 20 6c 6f  |page you were lo|
000003f0  6f 6b 69 6e 67 20 66 6f  72 20 64 6f 65 73 6e 27  |oking for doesn'|
00000400  74 20 65 78 69 73 74 2e  3c 2f 68 31 3e 0a 20 20  |t exist../h1>.  |
00000410  20 20 3c 70 3e 59 6f 75  20 6d 61 79 20 68 61 76  |  .p>You may hav|
00000420  65 20 6d 69 73 74 79 70  65 64 20 74 68 65 20 61  |e mistyped the a|
00000430  64 64 72 65 73 73 20 6f  72 20 74 68 65 20 70 61  |ddress or the pa|
00000440  67 65 20 6d 61 79 20 68  61 76 65 20 6d 6f 76 65  |ge may have move|
00000450  64 2e 3c 2f 70 3e 0a 20  20 3c 2f 64 69 76 3e 0a  |d../p>.  ./div>.|
00000460  3c 2f 62 6f 64 79 3e 0a  3c 2f 68 74 6d 6c 3e     |./body>../html>|
</pre>
