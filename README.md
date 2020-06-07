## 根据平时使用习惯，对ffuf的一些辅助脚本
### 1.起因   
根据平时的使用习惯，很多命令要重复敲，浪费时间和脑容量，稍微包装了使用场景，内置了常用的目录扫描大中小字典，并且写了个脚本，批量检测时候可以对结果进行汇总，并且根据返回包的大小进行去重,去重原因是批量时候经常会遇到waf之类的，会扫到很多垃圾数据，数据太多非常影阅读，很难去发现和验证存在的页面。   

### 2.ffuf简介
ffuf是一款Go语言编写的高速Web Fuzzer工具特性  
一个字，快！一般网站可以达到2000个包/秒   

官方地址：   
https://github.com/ffuf/ffuf   
   
简单使用如下所示    
需要指定字典、目标，还可以设置过滤参数   
ffuf -w /path/to/wordlist -u https://target/FUZZ   
   

   
### 3.安装：   
注意，需要Go 1.11及以上版本，参考如下链接安装最新版本Go   
https://blog.csdn.net/Magic_Ninja/article/details/103213358   
   
首先需要安装ffuf   
go get github.com/ffuf/ffuf   

然后下载本项目的脚本   
git clone https://github.com/possib1e/ffuf.git   
cd ffuf/   
chmod +x singe-ffuf  
chmod +x batch-ffuf  
  
### 4.使用  
#### 4.1 单个目标  
使用方式如下，输入目标url即可，共有3个字典可以选择，小、中、大，只需要输入1,2,3,即可使用，对于结果的过滤模式使用了-ac自动过滤，如果没能自动过滤，可以直接复制屏幕输出的完整运行命令，手动使用-fc -fs等参数进行过滤结果。   
**./singe-ffuf http://www.baidu.com**  
![image](https://github.com/possib1e/ffuf/blob/master/img/1.png)  
#### 4.2 多个目标  
批量使用的是dirsearch.txt 6k的轻量字典快速探测，会讲结果进行汇总，然后根据返回包大小去重，输出最终结果，创建了一个专属的文件夹用来存放结果，所以两个参数，第一个参数是目标url（包含http://）的txt文档，第二个参数是创建的文件夹，用来存放结果。   
**./batc-ffuf baidu.txt baidu**  
![image](https://github.com/possib1e/ffuf/blob/master/img/2.png)  
![image](https://github.com/possib1e/ffuf/blob/master/img/3.png)  