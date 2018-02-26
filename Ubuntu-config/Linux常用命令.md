# Linux 基本命令

1. ls     (list 显示当前目录下文件和目录 ls -l 详细显示 =ll )

   [root@linux ~]# ls [-aAdfFhilRS] 目录名称 
   [root@linux ~]# ls [--color={none,auto,always}] 目录名称 
   [root@linux ~]# ls [--full-time] 目录名称 
   参数： 
   -a ：全部的档案，连同隐藏档( 开头为 . 的档案) 一起列出来～ 
   -A ：全部的档案，连同隐藏档，但不包括 . 与 .. 这两个目录，一起列出来～ 
   -d ：仅列出目录本身，而不是列出目录内的档案数据 
   -f ：直接列出结果，而不进行排序 (ls 预设会以档名排序！) 
   -F ：根据档案、目录等信息，给予附加数据结构，例如： 
   *：代表可执行档； /：代表目录； =：代表 socket 档案； |：代表 FIFO 档案； 
   -h ：将档案容量以人类较易读的方式(例如 GB, KB 等等)列出来； 
   -i ：列出 inode 位置，而非列出档案属性； 
   -l ：长数据串行出，包含档案的属性等等数据； 
   -n ：列出 UID 与 GID 而非使用者与群组的名称 (UID与GID会在账号管理提到！) 
   -r ：将排序结果反向输出，例如：原本档名由小到大，反向则为由大到小； 
   -R ：连同子目录内容一起列出来； 
   -S ：以档案容量大小排序！ 
   -t ：依时间排序 
   --color=never ：不要依据档案特性给予颜色显示； 
   --color=always ：显示颜色 
   --color=auto ：让系统自行依据设定来判断是否给予颜色 
   --full-time ：以完整时间模式 (包含年、月、日、时、分) 输出 
   --time={atime,ctime} ：输出 access 时间或 改变权限属性时间 (ctime) 
   而非内容变更时间 (modification time)      

2. cat 由第一行开始显示档案内容 

   [root@linux ~]# cat [-AEnTv] 
   参数： 
   -A ：相当于 -vET 的整合参数，可列出一些特殊字符～ 
   -E ：将结尾的断行字符 $ 显示出来； 
   -n ：打印出行号； 
   -T ：将 [tab] 按键以 ^I 显示出来； 
   -v ：列出一些看不出来的特殊字符      

3. tac 从最后一行开始显示，可以看出 tac 是 cat 的倒着写！

4. nl 显示的时候，顺道输出行号！ 

   [root@linux ~]# nl [-bnw] 档案 
   参数： 
   -b ：指定行号指定的方式，主要有两种： 
   -b a ：表示不论是否为空行，也同样列出行号； 
   -b t ：如果有空行，空的那一行不要列出行号； 
   -n ：列出行号表示的方法，主要有三种： 
   -n ln ：行号在屏幕的最左方显示； 
   -n rn ：行号在自己字段的最右方显示，且不加 0 ； 
   -n rz ：行号在自己字段的最右方显示，且加 0 ； 
   -w ：行号字段的占用的位数。      

5. more 一页一页的显示档案内容 

     空格键 (space)：代表向下翻一页；
    Enter ：代表向下翻『一行』；
    /字符串 ：代表在这个显示的内容当中，向下搜寻『字符串』；
    :f ：立刻显示出文件名以及目前显示的行数；
    q ：代表立刻离开 more ，不再显示该档案内容。 

6. less 与 more 类似，但是比 more 更好的是，他可以往前翻页！

   空格键 ：向下翻动一页； 
   [pagedown]：向下翻动一页； 
   [pageup] ：向上翻动一页； 
   /字符串 ：向下搜寻『字符串』的功能； 
   ?字符串 ：向上搜寻『字符串』的功能； 
   n ：重复前一个搜寻 (与 / 或 ? 有关！) 
   N ：反向的重复前一个搜寻 (与 / 或 ? 有关！) 
   q ：离开 less 这个程序； 

7. head 只看头几行 

   [root@linux ~]# head [-n number] 档案 
   参数： 
   -n ：后面接数字，代表显示几行的意思      

8. tail 只看尾巴几行   tail -200f logfile2 ( 显示日志最后 200 行 )

9. od 以二进制的方式读取档案内容！ 

   [root@linux ~]# od [-t TYPE] 档案 
   参数： 
   -t ：后面可以接各种『类型 (TYPE)』的输出，例如： 
   a ：利用预设的字符来输出； 
   c ：使用 ASCII 字符来输出 
   d[size] ：利用十进制(decimal)来输出数据，每个整数占用 size bytes ； 
   f[size] ：利用浮点数值(floating)来输出数据，每个数占用 size bytes ； 
   o[size] ：利用八进位(octal)来输出数据，每个整数占用 size bytes ； 
   x[size] ：利用十六进制(hexadecimal)来输出数据，每个整数占用 size bytes ；      

10.  chmod  ( chmod +R filename增加文件读写执行权限,+R 可读,+W 可写,+X 可执行

     ( chmod 777 filename 增加文件读写执行权限的另一种方式,
                                 7=> 对应8进制的 111 可读可写可执行)
            
     chown  ( chown -R haowen .将当前目录下所有文件和目录权限赋给 haowen 
              ,-R 包括子目录)
     chgrp -R mysql . (把当前文件夹变更到mysql群组,mysql是已经有的群组)变更文件或目录的所属群组。

11. chattr (设定档案隐藏属性) 

12. lsattr (显示档案隐藏属性) 

13. find   ( find ./ -name file1 -print ,从当前目录向下查找名为 file1 的文件)

14.  mkdir  ( mkdir  dir1 ,新建目录 dir1 ) 

    mkdir [-mp] 目录名称 
    参数： 
    -m ：设定档案的权限喔！直接设定，不需要看预设权限 (umask) 的脸色～ 
    -p ：帮助你直接将所需要的目录递归建立起来！      

15. pwd   Print Working Directory  ( pwd  ,显示当前路径 ) pwd -P 显示出确实的路径,而非使用连接(link)路径

16.  cd     

    1.  cd /usr/local/   进入目录 /usr/local/ , cd ../ 返回到上一级目录  

                               ./ 当前目录 ../父目录 - 代表前一个工作目录 ~代表[目前使用者身份]所在的家目录  ~account代表account这个使用者的家目录)针对 cd 的使用方法，如果仅输入 cd 时，代表的就是『 cd           ~ 』

17. mv   

    [root@linux ~]# mv [-fiu] source destination 
    [root@linux ~]# mv [options] source1 source2 source3 .... directory 
    参数： 
    -f ：force 强制的意思，强制直接移动而不询问； 
    -i ：若目标档案 (destination) 已经存在时，就会询问是否覆盖！ 
    -u ：若目标档案已经存在，且 source 比较新，才会更新 (update)      

       mv file1  /home/haowen/ ,将文件移动到目录 /home/haowen/下 ,相当于 window 剪切 

         mv file1 filenew1 ,将文件名改为 filenew1 

18. cp 

     cp file1 /home/haowen/  ,将文件复制copy到目录 /home/haowen/下  

     cp -r dir1 /home/haowen/ 
     cp file1 ./file2 复制文件并改名

    [root@linux ~]# cp [-adfilprsu] 来源档(source) 目的檔(destination) 
    [root@linux ~]# cp [options] source1 source2 source3 .... directory 
    参数： 
    -a ：相当于 -pdr 的意思； 
    -d ：若来源文件为连结文件的属性(link file)，则复制连结文件属性而非档案本身； 
    -f ：为强制 (force) 的意思，若有重复或其它疑问时，不会询问使用者，而强制复制； 
    -i ：若目的檔(destination)已经存在时，在覆盖时会先询问是否真的动作！ 
    -l ：进行硬式连结 (hard link) 的连结档建立，而非复制档案本身； 
    -p ：连同档案的属性一起复制过去，而非使用预设属性； 
    -r ：递归持续复制，用于目录的复制行为； 
    -s ：复制成为符号连结文件 (symbolic link)，亦即『快捷方式』档案； 
    -u ：若 destination 比 source 旧才更新 destination ！      

19. rm     

    ( rm file1 ,rm -r dir1,rm -rf dir2 删除文件或目录, f不提示输入y 

    [root@linux ~]# rm [-fir] 档案或目录 
    参数： 
    -f ：就是 force 的意思，强制移除； 
    -i ：互动模式，在删除前会询问使用者是否动作 
    -r ：递归删除啊！最常用在目录的删除了      

20. touch 建立一个空的档案,将某个档案日期修订为目前 (mtime 与 atime)     

    [root@linux ~]# touch [-acdmt] 档案 
    参数： 
    -a ：仅修订 access time； 
    -c ：仅修改时间，而不建立档案；
    -d ：后面可以接日期，也可以使用 --date="日期或时间" 
    -m ：仅修改 mtime ； 
    -t ：后面可以接时间，格式为[YYMMDDhhmm]      

21. file 如果你想要知道某个档案的基本数据，例如是属于 ASCII 或者是 data 档案，或者是 binary ， 且其中有没有使用到动态函式库 (share library) 等等的信息，就可以利用 file 这个指令来检阅喔！ 

22. which (寻找『执行档』) 这个指令是根据『PATH』这个环境变量所规范的路径，去搜寻『执行档』的档名whereis (从数据库寻找特定档案)

    [root@linux ~]# which [-a] command 
    参数： 
    -a ：将所有可以找到的指令均列出，而不止第一个被找到的指令名称      

23. whereis

    [root@linux ~]# whereis [-bmsu] 档案或目录名 
    参数： 
    -b :只找 binary 的档案 
    -m :只找在说明文件 manual 路径下的档案 
    -s :只找 source 来源档案 
    -u :没有说明档的档案！      

24. wc

    功能说明：计算字数。
    语 　 法：wc [-clw][--help][--version][文件名]
    补充说明：利用wc指令我们可以计算文件的Byte数、字数、或是列数，若不指定任何文件名称，或是所给予的文件名为"-"，则wc指令会从标准输入设备读取数据。假设不给予其参数，wc指令会一并显示列数、字数和Byte数
    参 　 数：
    -c 只显示Byte数，亦即字符数；
    -l 只显示列数；
    -w 只显示字数；
    -m 同样显示字符数
    --help 在线帮助；
    --version 显示此软件的版本信息。

25. locate 从数据库列出某个档案的完整档名

26. find ./ -name index.jsp 查找当前目录下名称为index.jsp的文件

27. grep   ( grep "mobile=13712345678"  logfile1 ,在logfile1中 

          搜索查找内容 "mobile=13712345678" )

28. ping   ( ping 61.129.78.9 ,ping www.163.com ,测试网络连接是否正常 )
29. ifconfig  ( ifconfig ,查看本机 IP地址，子网掩码等 )
30. ps    ( ps aux 查看系统中已经启动的进程, ps aux | grep programe1 ,

         查看程序1是否正在运行

31. kill  ( kill -9  2325 ,杀死进程号为 2325的进程, 

         killall  programe1 ,杀死programe1进程 )

32. reboot ( 重启系统 )

33. init 0 ( 关机 ,仅 root 用户有权操作 )

34. init 6 ( 重启系统 ,仅 root 用户有权操作 )

35. gzip   ( gzip file1 ,压缩文件 file1 )

36. gunzip ( gunzip file1.gz  解压缩文件 file1.gz )

37. tar -zcvf ( tar -zcvf  dir1.tar.gz ./dir1  ,将当前目录下 dir1目录所有内容压缩打包,包名dir1.tar.gz )

    tar -zxvf ( tar -zxvf  dir1.tar.gz ,解开压缩包 )

38. echo "hello!" >> file1  ( 将 "hello" 添加到文件 file1后面, 

                           当 file1 不存在就创建 file1

39. vi file2    

         ( 按 i 进入 insert 状态 即插入模式 ,按 Esc 退出插入模式
                      在非插入模式下按 dd 删除光标当前行,按 x 删除当前字,
                      按 j,n,l移动光标 )

      :wq  ( 保存退出 ) :q! (不保存退出) 

40. 增加环境变量

    [root@linux ~]# echo $PATH        
    [root@linux ~]# PATH="$PATH":/root      

    env  显示系统的一些环境变量 
    set  显示系统的所有变量 

41.  chmod

     Linux/Unix 的档案调用权限分为三级 : 档案拥有者、群组、其他。
     利用 chmod 可以藉以控制档案如何被他人所调用。   

    - 表示增加权限、- 表示取消权限、= 表示唯一设定权限。 
      r 表示可读取，w 表示可写入，x 表示可执行，

    1. 将档案 file1.txt 设为所有人皆可读取 : 
       chmod ugo+r file1.txt   或  chmod 444 file1.txt
    2. 将文件 file2 设为属主可读写执行,Group,other ,只能读
       chmod 744 file2   ( 7=> "111" ,4=>"100" 二进制 )
    3. 将文件 file3 设为属主可读写执行,Group,other ,无权限操作不能读写执行)
       chmod 700 file3   ( 7=> "111" ,0=>"000"  )

       其中a,b,c各为一个数字，分别表示User、Group、及Other的权限。 
    　 
    　 r=4，w=2，x=1 若要rwx属性则4+2+1=7； 若要rw-属性则4+2=6；
                      若要r-x属性则4+1=5　 　

42. date 显示日期的指令： 

43. cal 显示日历的指令： 

44. bc 简单好用的计算器： 

45. [Tab] 按键   (按两次) 命令补全: 

46. [Ctrl]-c 按键 中断目前程序: 

47. [Ctrl]-d 按键  (相当于输入 exit) 键盘输入结束:     

48. finger 显示关于系统用户的信息

49. netstat -a     看网络的联机状态: 

50. ntsysv 设置服务随系统启动时同时启动    

51. shutdown  ,shutdown -h now  惯用的关机指令： 

52. reboot, halt, poweroff 重新开机，关机： 

###  系统相关的命令

 dmesg : 例如 dmesg | more  显示系统的诊断信息,操作系统版本号,物理内及其它信息
 df : 例如 df -h 显示硬盘空间
 du :   查看目录中各级子目录使用的硬盘空间
 free:  查看系统内存,虚拟内存(交换空间)的大小占用情况
 top: 动态实时查看系统内存,CPU,进程

 hostname 查看主机名:

 hostname 新主机名 修改主机名(临时的,重启就没了):

man 命令:查看该命令的基础用法 
info 命令:查看该命令的基础用法
ls -l /lib/modules/`uname -r`/kernel/fs 查看Linux 支持的档案系统有哪些
cat /proc/filesystems  查看Linux目前已启用的档案系统

type 查询某个指令是来自于外部指令(指的是其它非 bash 套件所提供的指令) 或是内建在 bash 当中的指令

[root@linux ~]# type [-tpa] name 
参数： 
：不加任何参数时，则 type 会显示出那个 name 是外部指令还是 bash 内建的指令！ 
-t ：当加入 -t 参数时，type 会将 name 以底下这些字眼显示出他的意义： 
file ：表示为外部指令； 
alias ：表示该指令为命令别名所设定的名称； 
builtin ：表示该指令为 bash 内建的指令功能； 
-p ：如果后面接的 name 为指令时，会显示完整文件名(外部指令)或显示为内建指令； 
-a ：会将由 PATH 变量定义的路径中，将所有含有 name 的指令都列出来，包含 alias      

myname=pqb 变量的设定
PATH="$PATH":/home/dmtsai/bin  变量的累加
echo $myname 变量的查看
unset myname 变量的取消

在来看看关机，关闭系统使用Shutdown命令，确保用户和系统的资料完整。只有root用户才能使用这个命令。
一般的用户是不允许执行这个命令的。
我们先看看showdown语法：
shutdown [options] when [message]
options:　-r 表示重启，-h表示系统服务停滞(halt)后，立刻关机，-f表示快速重启
when：　为shutdown指定时间。hh:mm：绝对时间，hh指小时，mm指分钟；如08:30，+m:m分钟后执行，
now=+0，也就是立刻执行
message：表示系统的广播信息，一般提示各个用户系统关机或重启，要求用户保存资料后退出。

创建文件
创建文件是指创建一个一般的普通文件，并且这个文件为空，我们可以使
用touch命令来建立一般文件，如下操作：
[root@Linux two]# touch 111.txt

搜索文件
我们先来学习一下如何搜索文件，特别是刚开始学习Linux的时候，自己建立的文件不知道放在哪里了，常有发
生。如果知道文件名，却不知道文件在那个目录下面了，我们就可以使用locate命令来搜索文件。看如下操作
：
[root@Linux one]# locate install.log
/root/install.log
/root/install.log.syslog
看一下，我们一下就搜索了两个与install.log相关的文件，他们都在/root目录下，同时我们感觉到，使用这个命
令搜索文件的速度比较快，其实要使用这个命令，必须配合数据库来使用，因为这个命令是从数据库中来搜索
文件，这个数据库的更新速度是7天更新一次。如下操作：
[root@Linux one]# touch 001.txt
[root@Linux one]# locate 001.txt
发现这个命令找不到新建立的文件，所以我们要使用这个命令搜索文件之前，必须自己更新一下数据库(更新数据库需要root权限)，如下
操作：
[root@Linux one]# updatedb
[root@Linux one]# locate 001.txt
/root/one/001.txt
看看，如果执行updatedb这个命令更新数据库之后，我们就可以找到我们所需要的数据。不过更新数据库的时
间需要一段时间。


locale能看语言环境
保存语言信息的文件在/etc/sysconfig/i18n中。

/sbin/service xinetd restart|start|stop 启动后台服务， 

/sbin/chkconfig --list |more 显示系统服务启动情况，显示了运行级别0到运行级别6的情况.
这些服务都是靠系统脚本init启动的。还有一些不是靠系统脚本启动的而下面会看到一些特殊服务，他们不是
靠init 启动的。是靠xinetd启动的，是一个独立的互联网服务器的服务器是一个超级服务其，可以启动很多的子服
务器。

大家看到 xinetd这个服务只要他是开启的，就可以运行他下面的服务器，它下面的大部分都是关闭的，只
有一个是开启的，如果我们想开启一个服务可以使用chkconfig命令，例如我们想开启 rsync服务，我们可以使
用chkconfig rsync on|off 命令。

mount
在mount命令不使用任何选项和参数的时候将显示当前linux系统中以挂载的文件系统信息。

mount Cttype dev dir
光盘文件系统类型是：iso9660；dev表示需要挂载文件系统的设备名称，光盘驱动器的设备名称是/dev/cdrom; dir表示挂载点，即挂载到的文件目录路径。
首先介绍光盘的挂载方法：
mount -t iso9660 /dev/cdrom /media/cdrom

列出系统中所有存储设备
fdisk -l命令

使用“vfat”文件系统类型表示所有的fat文件系统类型，包括fat16和fat32，ntfs还是使用ntfs表示。
u盘的挂载方法
mount -t vfat /dev/sdb1 /mnt/
mount -t ntfs /dev/sdb1 /mnt/

umount命令用于卸载已经挂载的文件系统，基本格式如：umount dir device

对于光盘文件系统的卸载可以使用，以下两条命令中的任意一条
umount /dev/cdrom
umount /media/cdrom

u盘的卸载
umount /dev/sdb1

eject命令
eject 弹出光盘命令
eject -t 光盘驱动器自动回收

cut 
使用权限：所有使用者 
用法：cut -cnum1-num2 filename 
说明：显示每行从开头算起 num1 到 num2 的文字。 
范例： 
shell>> cat example 
test2 
this is test1 
shell>> cut -c0-6 example 开头算起前 6 个字元 
test2 
this i 

指令名称:ln 
　　使用权限:所有使用者 
　　使用方式:ln [options] source dist,其中 option 的格式为:
　　[-bdfinsvF][-S backup-suffix] [-V {numbered,existing,simple}] 
　　[--help] [--version] [--] 

　　说明:Linux/Unix 档案系统中,有所谓的连结(link),我们可以将其视为档案的别名,而连结又可分为两种:硬连结(hard link)与软连结(symbolic link),硬连结的意思是一个档案可以有多个名称,而软连结的方式则是产生一个特殊的档案,该档案的内容是指向另一个档案的位置。硬连结是存在同一个档案系统中,而软连结却可以跨越不同的档案系统。 

　　ln source dist 是产生一个连结(dist)到 source,至于使用硬连结或软链结则由参数决定。 

　　不论是硬连结或软链结都不会将原本的档案复制一份,只会占用非常少量的磁碟空间。

　　-f:链结时先将与 dist 同档名的档案删除-d:允许系统管理者硬链结自己的目录-i:在删除与 dist 同档名的档案时先进行询问-n:在进行软连结时,将 dist 视为一般的档案-s:进行软链结(symbolic link)-v:在连结之前显示其档名-b:将在链结时会被覆写或删除的档案进行备份-S SUFFIX:将备份的档案都加上 SUFFIX 的字尾-V METHOD:指定备份的方式--help:显示辅助说明--version:显示版本 
　　范例:
　　将档案 yy 产生一个 symbolic link:zz 
　　ln -s yy zz 
　　将档案 yy 产生一个 hard link:zz 
　　ln yy xx 

名称:at 
　　使用权限:所有使用者 
　　使用方式:at -V [-q queue] [-f file] [-mldbv] TIME 
　　说明:at 可以让使用者指定在 TIME 这个特定时刻执行某个程式或指令,TIME 的格式是 HH:MM其中的 HH 为小时,MM 为分钟,甚至你也可以指定 am, pm, midnight, noon, teatime(就是下午 4 点锺)等口语词。 
　　如果想要指定超过一天内的时间,则可以用 MMDDYY 或者 MM/DD/YY 的格式,其中 MM 是分钟,DD 是第几日,YY 是指年份。另外,使用者甚至也可以使用像是 now + 时间间隔来弹性指定时间,其中的时间间隔可以是 minutes, hours, days, weeks 
　　另外,使用者也可指定 today 或 tomorrow 来表示今天或明天。当指定了时间并按下 enter 之后,at 会进入交谈模式并要求输入指令或程式,当你输入完后按下 ctrl+D 即可完成所有动作,至于执行的结果将会寄回你的帐号中。
　　把计:
　　-V:印出版本编号 
　　-q:使用指定的伫列(Queue)来储存,at 的资料是存放在所谓的 queue 中,使用者可以同时使用多个 queue,而 queue 的编号为 a, b, c... z 以及 A, B, ... Z 共 52 个 
　　-m:即使程式/指令执行完成后没有输出结果, 也要寄封信给使用者 
　　-f file:读入预先写好的命令档。使用者不一定要使用交谈模式来输入,可以先将所有的指定先写入档案后再一次读入 
　　-l:列出所有的指定 (使用者也可以直接使用 atq 而不用 at -l) 
　　-d:删除指定 (使用者也可以直接使用 atrm 而不用 at -d) 
　　-v:列出所有已经完成但尚未删除的指定 
　　例子:
　　三天后的下午 5 点锺执行 /bin/ls:
　　at 5pm + 3 days /bin/ls 

　　三个星期后的下午 5 点锺执行 /bin/ls:
　　at 5pm + 2 weeks /bin/ls 

　　明天的 17:20 执行 /bin/date:
　　at 17:20 tomorrow /bin/date 
　　1999 年的最后一天的最后一分钟印出 the end of world ! 
　　at 23:59 12/31/1999 echo the end of world ! 

名称：cal 
　　使用权限：所有使用者 
　　使用方式：cal [-mjy] [month [year]] 
　　说明： 
　　显示日历。若只有一个参数,则代表年份(1-9999),显示该年的年历。年份必须全部写出：``cal 89\ 将不会是显示 1989 年的年历。使用两个参数,则表示月份及年份。若没有参数则显示这个月的月历。 
　　1752 年 9 月第 3 日起改用西洋新历,因这时大部份的国家都采用新历,有 10 天被去除,所以该月份的月历有些不同。在此之前为西洋旧历。 
　　匡兜: 
　　-m:以星期一为每周的第一天方式显示。 
　　-j:以凯撒历显示,即以一月一日起的天数显示。 
　　-y:显示今年年历。 
　　范例： 
　　cal:显示本月的月历。
　　[root@mylinux /root]# date 
　　Tue Aug 15 08:00:18 CST 2000 
　　[root@mylinux /root]# cal 
　　...

　　cal 2001:显示公元 2001 年年历。
　　[root@mylinux /root]# cal 2001 
　　...

    cal 5 2001:显示公元 2001 年 5 月月历。
　　[root@mylinux /root]# cal 5 2001 


名称:crontab 
　　使用权限:所有使用者 
　　使用方式:
　　crontab [ -u user ] filecrontab [ -u user ] { -l | -r | -e } 
　　说明:
　　crontab 是用来让使用者在固定时间或固定间隔执行程式之用,换句话说,也就是类似使用者的时程表。-u user 是指设定指定 user 的时程表,这个前提是你必须要有其权限(比如说是 root)才能够指定他人的时程表。如果不使用 -u user 的话,就是表示设定自己的时程表。 
　　参数:

　　-e:执行文字编辑器来设定时程表,内定的文字编辑器是 VI,如果你想用别的文字编辑器,则请先设定 VISUAL 环境变数来指定使用那个文字编辑器(比如说 setenv VISUAL joe) 
　　-r:删除目前的时程表 
　　-l:列出目前的时程表 

　　时程表的格式如下:
　　f1 f2 f3 f4 f5 program 

　　其中 f1 是表示分钟,f2 表示小时,f3 表示一个月份中的第几日,f4 表示月份,f5 表示一个星期中的第几天。program 表示要执行的程式。 
　　当 f1 为 * 时表示每分钟都要执行 program,f2 为 * 时表示每小时都要执行程式,其余类推 
　　当 f1 为 a-b 时表示从第 a 分钟到第 b 分钟这段时间内要执行,f2 为 a-b 时表示从第 a 到第 b 小时都要执行,其余类推 
　　当 f1 为 */n 时表示每 n 分钟个时间间隔执行一次,f2 为 */n 表示每 n 小时个时间间隔执行一次,其余类推 
　　当 f1 为 a, b, c,... 时表示第 a, b, c,... 分钟要执行,f2 为 a, b, c,... 时表示第 a, b, c...个小时要执行,其余类推 
　　使用者也可以将所有的设定先存放在档案 file 中,用 crontab file 的方式来设定时程表。 
　　例子:
　　每月每天每小时的第 0 分钟执行一次 /bin/ls:
　　0 7 * * * /bin/ls 

　　在 12 月内, 每天的早上 6 点到 12 点中,每隔 20 分钟执行一次 /usr/bin/backup:
　　0 6-12/3 * 12 * /usr/bin/backup 

　　周一到周五每天下午 5:00 寄一封信给 alex@domain.name:
　　0 17 * * 1-5 mail -s "hi" alex@domain.name < /tmp/maildata 

　　每月每天的午夜 0 点 20 分, 2 点 20 分, 4 点 20 分....执行 echo "haha" 
　　20 0-23/2 * * * echo "haha" 

　　注意:
　　当程式在你所指定的时间执行后,系统会寄一封信给你,显示该程式执行的内容,若是你不希望收到这样的信,请在每一行空一格之后加上 > /dev/null 2>&1 即可。


名称:sleep 
　　使用权限:所有使用者 
　　使用方式:sleep [--help] [--version] number[smhd] 
　　说明:sleep 可以用来将目前动作延迟一段时间 
　　参数说明:
　　--help:显示辅助讯息 
　　--version:显示版本编号 
　　number:时间长度,后面可接 s,m,h 或 d 
　　其中 s 为秒,m 为 分钟,h 为小时,d 为日数 
　　例子:
　　显示目前时间后延迟 1 分钟,之后再次显示时间:
　　date;sleep 1m;date 


　　名称： finger 
　　使用权限： 所有使用者 
　　使用方式： finger [options] user[@address] 
　　说明：finger 可以让使用者查询一些其他使用者的资料。
    范例：下列指令可以查询本机管理员的资料： 
　　finger root 

名称：last 
　　使用权限：所有使用者 
　　使用方式：shell>> last [options] 
　　说明：显示系统开机以来获是从每月初登入者的讯息 
　　把计: 
　　-R 省略 hostname 的栏位 
　　-num 展示前 num 个 
　　username 展示 username 的登入讯息 
　　tty 限制登入讯息包含终端机代号 
　　范例： 

　　shell>> last -R -2 

　名称:write 
　　使用权限:所有使用者 
　　使用方式:
　　write user [ttyname] 
　　说明:传讯息给其他使用者 
　　把计:
　　user:预备传讯息的使用者帐号 
　　ttyname:如果使用者同时有两个以上的 tty 连线,可以自行选择合适的 tty 传讯息 
　　例子.1:
　　传讯息给 Rollaend,此时 Rollaend 只有一个连线:
　　write Rollaend 
    接下来就是将讯息打上去,结束请按 ctrl+c 

　　例子.2 :传讯息给 Rollaend,Rollaend 的连线有 pts/2,pts/3:
　　write Rollaend pts/2

　　接下来就是将讯息打上去,结束请按 ctrl+c 
　　注意:若对方设定 mesg n,则此时讯席将无法传给对方 



指令：clear 
　　用途：清除萤幕用。 
　　使用方法：在 console 上输入 clear。 