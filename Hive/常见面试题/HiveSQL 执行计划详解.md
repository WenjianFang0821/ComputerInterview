# 一、前言  
Hive SQL 的执行计划描述 SQL 实际执行的整体轮廓，通过执行计划能了解 SQL 程序在转换成相应计算引擎的执行逻辑，掌握了执行逻辑也就能更好地把握程序出现的瓶颈点，从而能够实现更有针对性的优化。此外还能帮助开发者识别看似等价的 SQL 其实是不等价的，看似不等价的 SQL 其实是等价的 SQL。<font color=orange>可以说执行计划是打开 SQL 优化大门的一把钥匙。</font>  

要想学 SQL 执行计划，就需要学习查看执行计划的命令：<font color=green>explain</font>，在查询语句的 SQL 前面加上关键字 explain 是查看执行计划的基本方法。学会 explain，能够给我们工作中使用 hive 带来极大的便利！  

# 二、SQL 的执行计划  
Hive 提供的执行计划目前可以查看的信息有以下几种：  

<font color=orange>explain</font>：查看执行计划的基本信息；  
<font color=orange>explain dependency</font>：dependency 在 explain 语句中使用会产生有关计划中输入的额外信息。它显示了输入的各种属性；    
<font color=orange>explain  authorization</font>：查看 SQL 操作相关权限的信息；  
<font color=orange>explain  vectorization</font>：查看 SQL 的向量化描述信息，显示为什么未对 Map 和 Reduce 进行矢量化。从 Hive 2.3.0 开始支持；  
<font color=orange>explain  analyze</font>：用实际的行数注释计划。从 Hive 2.2.0 开始支持；  
<font color=orange>explain  cbo</font>：输出由 Calcite 优化器生成的计划。CBO 从 Hive 4.0.0 版本开始支持；  
<font color=orange>explain  locks</font>：这对于了解系统将获得哪些锁以运行指定的查询很有用。LOCKS 从 Hive 3.2.0 开始支持；  
<font color=orange>explain  ast</font>：输出查询的抽象语法树。AST 在 Hive 2.1.0 版本删除了，
存在 bug，转储 AST 可能会导致 OOM 错误，将在 4.0.0 版本修复；  
<font color=orange>explain  extended</font>：加上 extended 可以输出有关计划的额外信息。这通
常是物理信息，例如文件名，这些额外信息对我们用处不大；  

