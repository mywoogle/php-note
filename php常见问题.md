#php常见问题
##第一组(jisheng)
一基础知识
2.指出下面URI格式存在的问题
http://www.51.com/index.php?url=http://blog/51.com/blog.php?user=boy&url=my.51.com

解答：存在参数的归属不清楚的问题。注意：URL中可以N多个问号的。不过第一个问号之后的都算参数了。

3、表格布局合并单元格

解答：
<table border="1">
	<tr>
		<td colspan="2">1</td>
		<td>2</td>
	</tr>
	<tr>
		<td rowspan="2">3</td>
		<td>4</td>
		<td>5</td>
	</tr>
	<tr>
		<td>6</td>
		<td>7</td>
	</tr>
</table>

4、<metahttp-equiv="Refresh"content="2;URL=http://www.jb51.net">

解答：2秒后调到jb51.net

5、简述html，xhtml，html5各自的特点

解答：HTML 指超文本标签语言。 是通向 WEB 技术世界的钥匙。
XHTML 是更严谨更纯净的 HTML 版本。
HTML5 是下一代的 HTML。

HTML标准不是很规范，浏览器也对HTML页面中的错误相当宽容。这反过来又导致了HTML作者写出了大量的含有错误的HTML页面。据说，时至今日web上99%的页面都含有HTML错误。

XHTML 是更严谨更纯净的 HTML 版本。 XHTML 元素必须被正确地嵌套。XHTML 元素必须被关闭。 标签名必须用小写字母。HTML 文档必须拥有根元素。不向后兼容。并定义了一个新的MIME type，application/xhtml+xml

HTML5确实引入了许多新的特性并且向后兼容。你可以将任何已有的网页的第一行改成<!DOCTYPE html>，它就成也一个HTML5页面

二js技术
6、分别介绍一下代码的执行效果
a.document.body.innerHTML = "<b>Hello World</b>";
b.document.write("<b>Hello World</b>");
c.document.body.innerText = "<b>Hello World</b>";

解答：a会输出hello world和脚本到页面并解析b标签，b和c都不会输出脚本到页面。b要解析b标签，c不解析b标签。

7、执行下面代码最终user值是
var user = 'boy';
function a() {
	user="girl";
}
function b() {
	var user;
	user="boy";
}
a();
b();
alert(user);

解答：user值为girl，第一个user是一个局部变量，a中的user是一个全局变量，可以在传到函数外面，b中的user是局部变量，不能传到函数外面。最后，a中的全局变量user覆盖了，以前一个局部变量user，所以值应该为girl

8、Ajax基础知识
异步和同步请求的区别是什么，readyState中1,4分别表示什么含义，status中出现200和0分别表示什么含义？

解答：
同步：提交请求->等待服务器处理->处理完毕返回 这个期间客户端浏览器不能干任何事
异步: 请求通过事件触发->服务器处理（这是浏览器仍然可以作其他事情）->处理完毕。
举个例子 打电话时同步 发消息是异步

readyState
0 － （未初始化）还没有调用send()方法
1 － （载入）已调用send()方法，正在发送请求
2 － （载入完成）send()方法执行完成，已经接收到全部响应内容
3 － （交互）正在解析响应内容
4 － （完成）响应内容解析完成，可以在客户端调用了

status
200-确定。客户端请求已成功。  
0-状态未初始化

0XX:状态未初始化
1xx-信息提示  
2xx-成功 
3xx-重定向  
4xx-客户端错误
5xx-服务器错误

9、根据要求编写代码
编写用户名格式验证函数，成功返回真。用户名只包含数字和字母，数字不能出现在首位，最长20字节。

解答：
function verify() {
	var strRegex = "/^[a-zA-Z]{1}[0-9a-zA-Z]{0,19}$/";
  	var re=new RegExp(strRegex);
    if(re.test(document.getElementById("username").value)){
    	return true;
    }
}

编写定时器函数，每秒计数加1，当计数器等于100是归零，大于100000则停止计数。

解答：题目有问题，主要记住这两个函数就用户，就ok
var id = setInterval("test()", 1000); 
clearInterval(id);
var id=setTimeout(test,100);
clearTimeout(id);

三php技术
10、说明下面操作符、函数直接的区别
==之比较值，===除了比较值还要比较类型。

sort($array)和arsort($array)的区别
sort() 函数用于对数组单元从低到高进行排序。
rsort() 函数用于对数组单元从高到低进行排序。
asort() 函数用于对数组单元从低到高进行排序并保持索引关系。
arsort() 函数用于对数组单元从高到低进行排序并保持索引关系。
ksort() 函数用于对数组单元按照键名从低到高进行排序。
krsort() 函数用于对数组单元按照键名从高到低进行排序。

include和required
若引入时出错，前者是不致命的，后者是致命的。
前者是有条件包含函数，后者是无条件包含函数
include()执行时需要引用的文件每次都要进行读取和评估，require()执行时需要引用的文件只处理一次

11、用empty（$var）处理下面的变量，其返回值分别是
$var=0;//true
$var='0';//true
$var='';//true
$var='    ';//false
$var='a';//false
$var=null;//true
$var=false;//true

12、执行下面语句，$a,$b的值分别是
$a=1;$b=&b;unset($a);
解答：$a不存在了，$b为1。因为unset($a)已经销毁了变量a,同时对$a的初始值的引用减少1。因为$b是引用的a的初始值，所有$b的值为1.

14、执行下面语句输出什么
$val = 1;
foreach (range(1,9) as $key => $val);
echo $val;

解答：输出9.因为range（1,9）生产1-9的数字，他又遍历这个数组，每次都把新的值赋给$val，数组的最后一个值是9，所有$val的最终值为9

15、逐一说明以下全局变量、php函数的含义

$_SERVER[' HTTP_REFERER'] #链接到当前页面的前一页面的 URL 地址。
$_SERVER[' HTTP_USER_AGENT'] #当前请求的 User-Agent: 头部的内容。
$_SERVER['REMOTE_ADDR'] #正在浏览当前页面用户的 IP 地址。
$_SERVER['REQUEST_URI'] #访问此页面所需的 URI。例如，“/index.html”
$_SERVER['DOCUMENT_ROOT'] #当前 运行脚本所在的文档根目录。在服务器配置文件中定义。

set_time_limit(0); 程序执行多少秒后结束，若为0表示直到执行完为止。

error_reporting(E_ALL ^ E_NOTICE);//显示除去 E_NOTICE 之外的所有错误信息 和这个一样的E_ALL & ~E_NOTICE 

error_reporting(E_ERROR | E_WARNING | E_PARSE);//显示运行时错误

void var_dump ( mixed expression [, mixed expression [, ...]] )

var_dump()方法是判断一个变量的类型与长度,并输出变量的数值,如果变量有值输的是变量的值并回返数据类型.
此函数显示关于一个或多个表达式的结构信息，包括表达式的类型与值。数组将递归展开值，通过缩进显示其结构。

substr(string,start[,length])
start:
正数 - 在字符串的指定位置开始
负数 - 在从字符串结尾开始的指定位置开始
0 - 在字符串中的第一个字符处开始

length
正数 - 从 start 参数所在的位置返回的长度
负数 - 从字符串末端返回的长度(距末端的长度)

16请根据以下要求编写代码
需求一、在php5环境下，实现一个类的单例模式
作为一种常用的设计模式，单例模式被广泛的使用。那么如何设计一个单例才是最好的呢？
通常我们会这么写，网上能搜到的例子也大部分是这样:
复制代码 代码如下:

class A
{
    protected static $_instance = null;
    protected function __construct()
    {
        //disallow new instance
    }
    protected function __clone(){
        //disallow clone
    }
    public function getInstance()
    {
        if (self::$_instance === null) {
            self::$_instance = new self();
        }
        return self::$_instance;
    }
}
class B extends A
{
    protected static $_instance = null;
}
$a = A::getInstance();
$b = B::getInstance();
var_dump($a === $b);

将__construct方法设为私有，可以保证这个类不被其他人实例化。但这种写法一个显而易见的问题是：代码不能复用。比如我们在一个一个类继承A:
复制代码 代码如下:

class B extends A
{
    protected static $_instance = null;
}
$a = A::getInstance();
$b = B::getInstance();
var_dump($a === $b);

上面的代码会输出：
复制代码 代码如下:

bool(true)

问 题出在self上，self的引用是在类被定义时就决定的，也就是说，继承了B的A，他的self引用仍然指向A。为了解决这个问题，在PHP 5.3中引入了后期静态绑定的特性。简单说是通过static关键字来访问静态的方法或者变量，与self不同，static的引用是由运行时决定。于是 简单改写一下我们的代码，让单例模式可以复用。
复制代码 代码如下:
class C
{
    protected static $_instance = null;
    protected function __construct()
    {
    }
    protected function __clone()
    {
        //disallow clone
    }
    public function getInstance()
    {
        if (static::$_instance === null) {
            static::$_instance = new static;
        }
        return static::$_instance;
    }
}
class D extends C
{
    protected static $_instance = null;
}
$c = C::getInstance();
$d = D::getInstance();
var_dump($c === $d);

以上代码输出：
复制代码 代码如下:

bool(false)

这样，简单的继承并重新初始化$_instance变量就能实现单例模式。注意上面的方法只有在PHP 5.3中才能使用，对于之前版本的PHP，还是老老实实为每个单例类写一个getInstance()方法吧。
需要提醒的是，PHP中单例模式虽然没有像Java一样的线程安全问题，但是对于有状态的类，还是要小心的使用单例模式。单例模式的类会伴随PHP运行的整个生命周期，对于内存也是一种开销。




需求二、编写用户个人信息展示页面，详细需求如下
1）要求使用php自带的mysql操作函数
2）用户名参数user通过url以get方式传递
3）用户个人信息展示布局随意
4）数据库配置
host:localhost,port:3308
user:db1,password:123,database:user
5)table_userb表结构如下
CREATE TABLE `table_user`(
`user` varchar(20) default NULL,--用户名
`nick` varchar(20) default NULL,--昵称
`resume` varchar(100) default NULL,--个人介绍
PRIMARY KEY (`user`)
)

PHP操作mysql函数详解，mysql和php交互函数实现代码，需要的朋友可以参考下。
1. 建立和关闭连接 
1)resource mysql_connect/mysql_pconnect()([string hostname [:port][:/path/to/socket][,string username] [,string password]]) 
    mysql_pconnect() 会首先查找现有链接,不存在时才创建. 
    $link1 = @mysql_connect(“server1″, “user”, “password”)or die(“Could not connect to mysql server!”); 
2)boolean mysql_close([resource link_id])
    关闭连接不是必须的,因为可以由mysql的垃圾回收来处理.
    如果没有指定link_id,则关闭最近的链接. 

2. 选择数据库 
    boolean mysql_select_db(string db_name [, resource link_id]) 

3. 查询MySql
1) resource mysql_query(string query [,resource link_id])
    负责执行query.
2) resource mysql_db_query(string database, string query [, resource link_id])
    等价于mysql_select_db() + mysql_query(),从参数中就可以清楚的看出来. 

4. 获取和显示数据
1)array mysql_fetch_array(resource result_set [,int result_type])
    mysql_fetch_row()的增强版.
    将result_set的每一行获取为一个关联数组或/和数值索引数组.
    默认获取两种数组,result_type可以设置:
    MYSQL_ASSOC:返回关联数组,字段名=>字段值
    MYSQL_NUM:返回数值索引数组.
    MYSQL_BOTH:获取两种数组.因此每个字段可以按索引偏移引用,也可以按字段名引用. 
    $query = “select id, name from product order by name”;
    $result = mysql_query($query);
    while($row = mysql_fetch_array($result, MYSQL_BOTH)) {
        $name = $row['name'];//或者 $name = $row[1];
        $name = $row['id'];//或者 $name = $row[0];
        echo “Product: $name ($id)”;
    } 
2)object mysql_fetch_object(resource result_set)
    和mysql_fetch_array()功能一样,不过返回的不是数组,而是一个对象. 

5. 所选择的记录和受影响的记录 
1) mysql_num_rows()
    int mysql_num_rows(resource result_set)
    返回result_set中的行数.
    注意,mysql_num_rows()只在确定select语句查询获得的记录数有效,如果要获取insert/updata/delete查询影响的记录数,需要使用mysql_affected_rows().
2) mysql_affected_rows()
    int mysql_affected_rows([resource link_id])
    获取insert/updata/delete查询影响的记录数
    注意,不需要输入参数,默认使用最近建立的数据库连接的最近结果.可以使用可选参数link_id来选择数据库连接. 


6. 获取数据库和表的信息
1)resource mysql_list_dbs([resource link_id])获取服务器上所有数据库名称. 
2)string mysql_db_name(resource result_set, interger index)获取在mysql_list_dbs()返回的result_set中位置为index的数据库名. 
3)resource mysql_list_tables(string database [,resource link_id])获取database中的所有表名. 
4)string mysql_tablename(resource result_set, interger index)获取mysql_list_tables()返回的result_set中位置为index的表名. 






四综合技术题
17、请解释以下shell命令行的详细功能
$>php -l test.php		对test.php进行语法检查
$>shutdown -h now	马上关机
$>rm -rf /home/boy/soft	删除/home/boy/soft目录及里面的目录和文件
$>scp -rp /home/boy/a.sh    root@192.168.1.2:/root/		把文件和文件夹复制到远程，包括他们各自的属性
$>httpd -k graceful-stop	优雅的停止http		http://yijiangyanyu.iteye.com/blog/1682018   	使用-k命令通知httpd进程   	-k start|restart|graceful|stop|graceful-stop		fraceful会等工作中的子进程，先完成工作再退出
$>ps aux | grep httpd | grep -v grep | wc -l

ps -ef |grep cusip_full_is | grep -v grep | wc -l | awk '{ print $1; }' 这句话是什么意思呢？
等价于下面的
ps -ef |                              全格式显示当前所有进程
grep cusip_full_is             滤出''cusip_full_is''的进程
grep -v grep                     把''grep''这个进程忽略掉
wc -l                                 看看有多少个进程
awk '{ print $1; }'              输出第一列



18、技术术语解释
SOAP/RPC/REST	
REST：表象化状态转变 (软件架构风格）
SOAP：简单对象访问协议
XML-RPC：远程过程调用协议
http://www.cnblogs.com/lanxuezaipiao/archive/2013/05/11/3072436.html

XML/JSON
XML扩展标记语言，XML是标准通用标记语言 (SGML) 的子集，非常适合 Web 传输。
JSON(JavaScript Object Notation)一种轻量级的数据交换格式，具有良好的可读和便于快速编写的特性。
http://www.cnblogs.com/SanMaoSpace/p/3139186.html


SVN/CVS
http://www.cnblogs.com/allenblogs/archive/2010/12/01/1893519.html
http://blog.csdn.net/sfdev/article/details/2835073


MVC
是一种，用业务逻辑、数据、界面显示分离的方法组织代码的设计模式


19、请介绍以下crontab运行含义
*/5 * * * * /bin/monitor_cpu.sh---------每5分钟执行cpu监控脚本
30 6 1,10,20 * * /bin/run_backup.sh-----------每月在1,10,20日的6时30分执行备份脚本


20、介绍以下http协议状态码含义
200------确定。客户端请求已成功。
304------未修改，服务器返回此响应时，不会返回网页内容


21、请介绍以下socket操作函数的含义
socket()
创建一个套接字接口。
#include <sys/socket.h>
int socket( int af, int type, int protocol);

bind()
把socket绑定在一个IP地址和端口上

connect(),accept()
开始一个socket连接
接受一个Socket连接

listen()
监听由指定socket的所有连接

send(),recv()
这个函数发送数据到已连接的socket
从socket里结束数据到缓存

select(),poll(),epool()
多路选择


close()
关闭一个socket资源


http://www.jb51.net/article/38383.htm
http://php.net/manual/zh/ref.sockets.php


22、请解释php.ini中以下配置项的含义	http://www.ccvita.com/81.html
1register_globals = Off   影响到php 如何接收传递过来的参数比如：GET，POST，Cookie。当为On时可以用$user_name直接访问$_POST['user_name']否则不行。	http://blog.sina.com.cn/s/blog_98e9966801010ib8.html

2magic_quotes_gpc=On	 magic_quotes_gpc 为 on，它主要是对所有的 GET、POST 和 COOKIE 数据自动运行 addslashes()进行转义。	http://www.jb51.net/article/35868.htm	http://www.jb51.net/article/38990.htm	http://www.2cto.com/Article/201110/109573.html	http://www.myhack58.com/Article/html/3/7/2009/25528.htm	

3auto_prepend_file=/root/helle.php	在所有页面顶部require  /root/helle.php  	http://www.jb51.net/article/55468.htm

4allow_url_include=Off	不允许include/require远程文件。	http://www.ccvita.com/81.html

5session.auto_start=0 	关闭自动开启session	session.auto_start = on 的优点在于，任何时候都不会因忘记执行 session_start() 或 session_start() 在程序里的位置不对，而导致错误缺点在于，如果你使用的是第三方代码，则必须删去其中的全部 session_start() 。否则将不能得到正确的结果

##第二组(kuaibao)
1:多线程、多进程
2:设计模式
3:php相关框架的优劣势，尤其是Yii
4:高并发，分布式
5:数据库（mango DB，sql ，mysql）
6:代码管理
7:打包
8:算法，常用的以及基本算法：冒泡，快速排序，二分法（有很大可能让你在纸上写一些基本算法）
9:js，html，css等前端技术
10:uml建模，
11:还可能会考察一些 redis 呀 socket之类的
12:统计一个大文件的词语频率
