## 根据平时时候习惯，对ffuf的一些辅助脚本
根据平时的使用习惯，很多命令要重复敲，浪费时间和脑容量，稍微包装了使用场景，内置了常用的大中小字典，并且写了个脚本，批量检测时候可以对结果进行汇总，并且根据返回包的大小进行去重。

### 1.安装：
git clone https://github.com/possib1e/ffuf.git
chmod +x singe-ffuf
chmod +x batc-ffuf
### 2.使用
#### 2.1 单个目标
使用方式如下，输入目标url即可，共有3个字典可以选择，小、中、大，只需要输入1,2,3,即可使用，对于结果的过滤模式使用了-ac自动过滤，如果没能自动过滤，可以直接复制屏幕输出的完整运行命令，手动使用-fc -fs等参数进行过滤结果。
./singe-ffuf http://www.baidu.com

#### 2.2 多个目标
批量使用的是dirsearch.txt 6k的轻量字典快速探测，会讲结果进行汇总，然后根据返回包大小去重，输出最终结果，创建了一个专属的文件夹用来存放结果
./batc-ffuf baidu.txt baidu

#### PS: ffuf是一款Go语言编写的高速Web Fuzzer工具特性
一个字，快！一般网站可以达到2000个包/秒

##### 简单使用如下所示
ffuf -w /path/to/wordlist -u https://target/FUZZ

##### 详细使用参考如下链接
https://github.com/ffuf/ffuf


