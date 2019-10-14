---
layout: post_two
title: wireshark 抓包
categories: 其他技术
description: 抓包
keywords: 抓包
---

***女人的活动范围有限，所以完美的女人比完美的男人更完美。同时，一个坏女人往往比一个坏男人坏得更彻底。***

[Wireshark 常用过滤使用方法](https://www.cnblogs.com/nmap/p/6291683.html)  
1. dst host 192.168.0.118   目标 ip
2. src host 192.168.0.118   来源 ip
3. src host 192.168.0.118 and dst host 192.168.0.118    目标 ip 和来源 ip
4. port 5208                端口号 5208

## 16 进制转明文
```java
package com.ptshop.study;

/**
 * @Author 陈铨 
 * @Description 16 进制转明文
 * @Date 2019/10/6 14:16
 **/

public class HexChange {
    public static void main(String[] args) {
        String hex = "";
//        hex = strTo16("陈铨");
//        hex = strTo16("chenquan");
//        System.out.println("16 进制："+hex);
//        hex = "03010030000001001200730070005f00530065006c0063007500730074006f006d006500720074007900700065000000";
        hex = "e5b08fe4b880e8afb4efbc9a61736461730d0a\n";
        String s = toStringHex2(hex);
        String s1 = s.replaceAll("\u0000", "");
        System.out.println("原字符串："+s1);


    }

    /**
     * 字符串转化成为16进制字符串
     * @param s
     * @return
     */
    public static String strTo16(String s) {
        String str = "";
        for (int i = 0; i < s.length(); i++) {
            int ch = (int) s.charAt(i);
            String s4 = Integer.toHexString(ch);
            str = str + s4;
        }
        return str;
    }


    /**
     * 16进制转换成为string类型字符串
     * @param s
     * @return
     */
    public static String toStringHex2(String s) {
        byte[] baKeyword = new byte[s.length() / 2];
        for (int i = 0; i < baKeyword.length; i++) {
            try {
                baKeyword[i] = (byte) (0xff & Integer.parseInt(s.substring(
                        i * 2, i * 2 + 2), 16));
            } catch (Exception e) {
                e.printStackTrace();
            }
        }
        try {
//            s = new String(baKeyword, "gbk");// UTF-16le:Not
//            s = new String(baKeyword, "gb2312");// UTF-16le:Not
//            s = new String(baKeyword, "big5");// UTF-16le:Not
            s = new String(baKeyword, "UTF-8");// UTF-16le:Not
//            s = new String(baKeyword, "UTF-16");// UTF-16le:Not
        } catch (Exception e1) {
            e1.printStackTrace();
        }
        return s;
    }

}

```

## java 发送 tcp 协议
必须使用两台电脑，不然 wireshark 抓不到包
```java
// 客户端代码
package com.ptshop.study;

import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.io.PrintWriter;
import java.net.Socket;

public class SocketClient1 {
    public static void main(String args[])throws Exception{
        Socket socket = new Socket("192.168.0.127", 5208);
        System.out.println("小一连接成功");
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        PrintWriter pw = new PrintWriter(socket.getOutputStream());
        while(true){
            pw.println("小一说："+br.readLine());
            pw.flush();
        }
    }
}

```
```java
// 服务端启动代码
import java.net.ServerSocket;
import java.net.Socket;

public class SocketService {
    public static void main(String args[])throws Exception {
        ServerSocket serverSocket = new ServerSocket(5208);
        System.out.println("服务器启动成功");
        while (true) {
            Socket socket= serverSocket.accept();
            System.out.println("上线通知： " + socket.getInetAddress() + ":" +socket.getPort());
            new Thread(new ServerThread(socket)).start();
        }
    }
}
```
```java
// 服务端运行代码
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.net.Socket;

public class ServerThread implements Runnable {

    public Socket socket;

    public ServerThread (Socket socket) {
        this.socket = socket;
    }

    @Override
    public void run() {
        try {
            BufferedReader br = new BufferedReader(new InputStreamReader(socket.getInputStream()));
            while (true) {
                String str = br.readLine();
                System.out.println(str);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }

}
```

## wireshark 抓包效果图
![avatar](/images/204522.png)  
