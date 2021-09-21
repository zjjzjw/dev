0. 作者
PHP标准委员会（php-styleguide@baidu.com）

主席：王伟冰（EE）
委员：
崔燕（商业信用平台部），高松（商业平台部），黎博（百度APP技术平台部），李鸿斌（个人云部），王芃（小度云平台部）
参与规则制定：
张天鸿（商务搜索架构部），颜金洲(大数据部），贾晨辉（PS），许立强（贴吧），贾春鑫（PS），廖慧琴（LBS），仇昊（VS），全伟（CS），王岩（KS），颜玉刚（音乐），张东进（移动云）， 张振平（CID），雷国强（GIS），李红亮（GPM），王霄池（SCloud），张健（CS），许鹏（GIS），鲁超伍（移动搜索），杜伟（KS），孙笑（WD），v_sunhuai
1. 前言
源码文件必须采用UTF-8编码，且不得有BOM头，某些历史遗留的GBK模块除外。

编码风格没有太多的好坏之分, 最重要的是风格保持一致，编码规范有助于规范我们编码的风格，使代码具有更好的可读性。

PHP在百度内部应用得越来越广泛，但是却缺乏相应的编码规范支持，编码风格百家齐放，不利于我们代码的维护和传承， 根据大家平时的开发情况，制定了此PHP编码规范。

本文档风格约定部分可能跟你的喜好有冲突，请尽量用包容的心态来阅读。有任何问题或建议，欢迎跟我们讨论: php-styleguide@baidu.com

级别说明：

ERROR：禁止，iCode上会阻止提交
WARNING：警告，iCode上会提示警告
ADVICE：建议，仅供参考
2. 排版
2.1
[ERROR] [PHP002] 程序块要采用缩进风格编写，缩进的空格数建议为4个，单模块内必须统一。

解释

不同的缩进风格对代码的可读性影响很大，以tab为缩进单位在不同的tab step 下可读性也相差很多，所以将缩进定为一个soft tab即4个空格，这样在所有环境下缩进都会保持一致。
2.2
[WARNING] [PHP040] 关键字与其后的左括号之间有一个空格，而函数名与左括号之间不应有任何字符包括空格。

解释

虽然很多情况下编辑器的highlight已经做了区分，但是从格式上区分关键字和函数适用于所有的情况。
示例

if ($a > $b) { // 关键字
    funcA(); // 函数
}
2.3
[WARNING] [PHP041] 开始的大括号位于一行的末尾，结束的括号位于最末一行后，且独占一行。首括号也可另起一行，但一个模块内必须统一。

示例

if ($a > $b) {
   // do something
}
2.4
[ERROR] [PHP003] if/while等结构体，即使只有一行，也必须加上花括号，不得写成一行。

解释

这样做可读性更好，并且方便修改。
示例

if ($a > $b) {
    $a = 1;
}
2.5
[WARNING ][PHP042] 一行代码不得超过120个字节，建议控制在80字节内；一个函数不得超过500行，建议控制在100行以内。

解释

代码更美观， 可读性更好
2.6
[ADVISE] [PHP043] else-if语句使用else if形式，不使用elseif形式。

2.7
[WARNING] [PHP044] 函数名与其后的左括号之间不应有任何字符(包括空格) 函数调用的左括号与其第一个参数之间不应有任何字符(包括空格) 最后一个参数与右括号之间不应有任何字符(包括空格) 参数列表的逗号后面应有一个空格

示例

function funcA($a, $b, $c) {
    // do something
}
2.8
[ADVICE] [PHP045] 避免由于对错误的条件做判断带来if的嵌套。

解释

减少if/else嵌套， 更利于代码逻辑的理解。
示例

不推荐的方式:

if ($a === false) {
    // error handle
    return;
} else {
    if ($b === false) {
        // handle
    }
}
推荐的方式:

if ($a === false) {
    // error handle
    return;
}
 
if ($b === false) {
    // handle
}
2.9
[ADVICE] [PHP046] 如果过长的话需要另起一行。if 语句的条件若较多较长，应折行；新行以逻辑运算符起始，与第一行 if 左括号后的第一个字符对齐；折行后，每行条件具有独立而明确的语义

解释

这样做逻辑更一目了然。
示例

if ($a > $b && $c > $d
    && $e > $f && $h > $j
    && $z > $x) {
    // do something
}
2.10
[ADVICE] [PHP047] 多行的"="可能的话尽量用空格对齐。

示例

$a   = 1;
$ab  = 2;
$abc = 3;
2.11
[ERROR] [PHP009] Switch语句中每个case的break必须和case间有缩进。

示例

switch ($a) {
case 'A':
    $b = 2;
    break;
}
2.12
[ERROR] [PHP008] 初始化array如果采用多行结构时，数据项部分需要缩进，且最后一个数据项后面的逗号不可省略。

解释

这样做在修改代码增加数据项的时候不容易出现语法错误。
示例

$a = [
    'a' => 'b',
    'b' => 'c',
    'c' => 'd',
];
2.13
[ADVICE] [PHP048] 复杂的表达式, 使用括号表明优先级, 而不完全依赖运算符优先级。

示例

// 不推荐方式
if ($a && $b || $c + $b && $e) {
}
 
// 推荐方式
if (($a && $b) || (($c + $b) && $e)){
}
2.14
[ADVICE] [PHP049] 同一个代码块的变量定义, 应该尽可能集中在块开始位置，提高可读性。

2.15
[WARNING] [PHP050] 除模板外，不允许使用?>标记结尾, 避免其后误加的字符干扰页面渲染。

2.16
[WARNING] [PHP051] 产品线内必须统一换行符的使用, 推荐"\n"。

2.17
[WARNING] 除模板外，在<?php前不允许加任何字符，避免字符干扰输出结果。(2021-09-09补充)



3. 命名
3.1
[WARNING] [PHP025] 全局变量以g_开头。

解释

全局变量对代码影响很大，以g_开头便能在代码中一眼看出是全局变量。
示例

global $g_count;
3.2
[WARNING] [PHP004] 常量命名使用全部大写字符，单词之间以'_'连接。

示例：PAGE_NUM


3.3

[ADVICE] [PHP052] 对于代码中的常量，建议用常量或define表示，不应直接写在代码中。

示例

define('PAGE_NUM', 3);
3.4
[ERROR] [PHP010] 关键字true、false、null必须小写

3.5
[WARNING] [PHP026] 类method命名采用驼峰命名, 普通function采用过程函数风格命名。

示例

// 类method
class A {
    public function getName() {
    }
}
 
 
// 普通function
function show_me_the_money() {
 
}
3.6
[WARNING] [PHP053] 类成员变量和局部变量必须采用小写开头的驼峰命名法。

示例：$userName, $userId

3.7
[ADVICE] [PHP054] 目录命名采用小写字母，文件命名使用大写开头的驼峰命名法。

示例：actions/ShowLemma.php

3.8
[ADVICE] [PHP055] 配置文件建议使用bd conf格式 或者ini格式，命名用小写字母，以下划分分配单词。

示例：conf/good_version.conf

3.9
[WARNING] [PHP056] 类名应以大写字母开头，每个单词的首字母大写。

示例：ActionController

3.10
[ADVICE] [PHP057] final放在访问控制符的前面、访问控制符放在static的前面

示例：

final public static function getInstance() {
}
4. 注释
4.1
[ADVICE] [PHP058] 文件、函数、类以及成员变量都应包含注释，关键代码必须有注释。

类文件/普通文件的注释, 说明该文件的主要作用。

示例

/**
 * A simple class describing employees
 *
 * @package Employee
 * @author George Schlossnagle
 */


类的注释, 说明该类的主要作用。

示例

/**
 * An example of documenting a class
 */
class Employee {
    /**
     * @var string
     */
    private $name;
 
    /**
     * The employees annual salary
     * @var number
     */
    private $salary;
 
    /**
     * @var number
     */
    private $employeeId;
 
    /**
     * The class constructor
     * @param employeeId int
     * @return void
     */
    public function __construct($employeeId = false) {
        if ($employeeId) {
            $this->employeeId = $employeeId;
            $this->fetchInfo();
        }
    }
 
    /**
     * Fetches info for employee
     *
     * @param void
     * @return void
     */
    private function fetchInfo() {
        $query = "SELECT name, salary
                    FROM employees
                    WHERE employee_id = $this->employeeId";
        $result = mysqli_query($query);
        list($this->name, $this->salary) = mysqli_fetch_row($result);
    }
 
    /**
     * Returns the monthly salary for the employee
     * @param void
     * @return int Monthly salary in dollars
     */
    public function monthlySalary() {
        return $this->salary / 12;
    }
}
4.2
[ERROR] [PHP027] 不能使用#作为单行注释, 多行注释/ * **/不能出现在同一行。

4.3
[WARNING] [PHP028] 函数必须通过param和return标记指明其参数和返回值的类型，对于php7，也可用类型声明的方式指明类型。


示例

// php5示例
/**
 * @param a int
 * @param b int
 * @return float
 */
function sum($a, $b) {
    return $a + $b;
}
 
 
// php7示例
function sum(int $a, int $b): float {
    return $a + $b;
}
4.4
[ADVICE] [PHP059] 注释需要遵守phpDocumentor等注释规范，同一团队内部必须保持一致。

参考资料：https://docs.phpdoc.org/references/phpdoc/index.html

4.5
[ADVICE] [PHP060] 必要的地方使用非文档性注释，提高代码易读性。

5. 编码原则
5.1
[ADVICE] [PHP061] 对传入或返回的参数进行类型检查和显式转换。

示例

$intSalary = (int)$salary;
5.2
[WARNING] [PHP062] 对于函数返回值的判断，特别是true/false, 必须用===或!==。

5.3
[ERROR] [PHP029] 生成对象时，必须使用new Classname()，不能用new Classname。

5.4
[WARNING] [PHP063] 所有文件路径都需要利用框架提供的宏写成绝对路径。

5.5
[ADVICE] [PHP064] 对于长时间运行的CLI程序，需要及时unset无用变量。

5.6
[WARNING] [PHP065] 对于一些系统操作，使用php内置的函数例如rename、touch等即可。尽量避免使用exec调用shell命令。

5.7
[ADVICE] [PHP066] 除非特殊情况，否则不允许使用require和include,而使用对应的require_once/include_once。

5.8
[WARNING] [PHP067] 配置项与PHP代码分离，不随Git发布。建议使用PaaS平台提供的配置管理功能管理配置项。

5.9
[ERROR] [PHP068] 预定义变量一律使用短格式，即：$_POST、$_GET、$_SERVER、$_ENV等，不再使用长格式：$_HTTP_POST_VARS、$_HTTP_GET_VARS。

5.10
[WARNING] [PHP069] 类文件名必须符合所用框架自动加载规范，常见的是PSR-0。

5.11
[ADVICE] [PHP070] 除模板外，尽量不要在php代码中出现html标签。

5.12
[ADVICE] [PHP071] 能用foreach的就不要用for,能用for的就不要用while。

5.13
[WARNING] [PHP072] 每个前端访问请求必须有且仅有一条notice日志。

5.14
[ADVICE] [PHP073] 数据库写操作必须有日志记录；记录条数应与操作一一对应。

5.15
[WARNING] [PHP074] 文件更新操作，必须使用临时文件+mv的方式，切忌直接写在原文件。

5.16
[ADVICE] [PHP075] 字符串尽量用'而不是"进行引用，一个是效率问题，一个是安全问题。

5.17
[ERROR] [PHP031] 所有的define语句，常量必须用''包括起来。

示例

define('PAGE_NUM', 3);
5.18
[ADVICE] [PHP076] require/include后面不使用括号。

示例

require_once 'a.php';
5.19
[ERROR] [PHP020] 函数允许使用默认参数,但是默认参数需要放到参数列表最后面，但如果有可变数量参数，则可变数量参数在最后面。

示例

public function insert($sql, $types = '', ...$params) {
}
5.20
[ERROR] [PHP032] 所有的全局变量应该写在函数的最开头，并且和后面的代码以空行隔开。

示例

function a() {
    global $g_count;
    global $g_time;
 
    $a = 1;
}
5.21
[ERROR] [PHP033] 禁止使用and, or, 而是使用&&, ||

5.22
[ADVICE] [PHP077] 避免使用$i, $j这样无意义的变量名, 除非是用作循环计数变量。

5.23
[ADVICE] [PHP078] 避免使用php逻辑代码作为配置, 以降低改配置的危险性。

5.24
[ADVICE] [PHP079] 进行==判断时，建议把常量放在前面, 避免误写成赋值操作。

示例

// 不推荐形式
if ($a == 1) {
}
// 推荐形式
if (1 == $a) {
}
5.25
[ADVICE] [PHP080] 使用变量前赋初值，提高可读性，也可避免误用别处定义的同名变量。

5.26
[ADVICE] [PHP081] 错误码使用统一文件集中配置，并且使用常量，而不应裸写数字

5.27
[ADVICE] [PHP082] 对于无需子类化的实体类以及不应重载的方法使用final关键字限定。

5.28
[ADVICE] [PHP083] 对于不应实例化的父类使用abstract关键字限定。

5.29
[ADVICE] [PHP084] 避免重载父类的static成员，这在5.2.x存在问题。

5.30
[ADVICE] [PHP085] 对于仅用于某个函数或类的全局变量，使用static的局部变量或者类成员变量代替。

5.31
[ADVICE] [PHP086] 在头文件中用$GLOBALS定义全局变量，避免局部包含导致的作用域问题。

6. 代码性能
6.1
[WARNING] [PHP034] 把重复调用放在循环体外。

示例

// 不推荐形式
for ($i = 0; $i < count($arr); $i++) {
}
 
 
// 推荐形式
$arrCount = count($arr);
for ($i = 0; $i < $arrCount; $i++) {
}
7. PHP安全编码规范
详见：PHP 安全类编码规范

8. 工具支持
对所有标记的有“eagle支持”的规则，大家可以本地调用客户端检查代码是否符合这部分规则，参考编码规范检查使用说明。

对于编码风格部分规范，可以使用本地工具自动格式化编码，参考使用phpfmt格式化代码。

在iCode发起代码评审时也将自动触发检查，结果会以行间评论的形式插入到代码评审中，帮助作者检查代码、帮助评审人评审代码。

PHP IDE，支持远程浏览、编辑开发机上的代码，支持代码跳转、编辑补全、语法检查、自动格式化、运行单测、调试等，在线手册