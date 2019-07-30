## JavaWeb-MyStore  
### 项目名称：蚂蚁商城  
### 项目描述：
这是一个基于JavaWeb的购物商城，使用MVC设计模式模型【（Model）、视图（View）和控制器（Controller）】+三层架构，降低了各层之间代码的耦合度，并对一些类进行了封装，降低功能代码之间的关联，创建了更清晰的抽象，该项目实现了商城系统的一些基本功能  
### 环境部署：  
  * 我的环境：IDE工具用的是eclipse，JDK1.8.0+Tomcat8.5.33，数据库使用的是Mysql  
### 项目运行：  
  * 使用Eclipse导入项目（IDEA也行），这里以eclipse为例，导入后报错的请自行 **Configure Build Path** 进行配置Tomcat等操作       
  * 打开WebContent --> WEB-INF --> lib ,然后将所有jar包 **Build Path**  
  * 导入sql文件夹里的**mystore.sql**到Mysql数据库中，根据本机数据库的端口号、用户名和密码修改**db.properties**
  文件，以确保能成功加载配置文件并连接数据库  
  * 最后运行index.jsp文件或者直接将整个工程Run On Server  
### 关于项目中的包描述：
 * domain包：里面存放的都是domain实体类（domain类是Javabean的子类，所以要重写Getter和Setter方法，另外还需要重写toString方法，
 如果不重写toString方法，那么输出的会是内存地址而不是具体数据）  
   * user.java：用户的实体类，包括uid(唯一识别每个用户)、username（用户名）、password（登录密码）、phone（电话号码）、code（注册时的验证码）  
   * Goods.java：商品的实体类，包括id、name、price、image，其中image存放的并非图片，而是图片的路径  
 *  JDBCUtil包：里面存放jdbc工具类，将jdbc连接数据库的操作抽象成JDBC工具类，提高代码的可重用性。本项目通过原生JDBC加载配置文件 连接数据库 调用数据库连接池来获取数据，调用Statement接口的PrepareStatement子接口进行预编译，从而实现DML和DQL操作    
 * Web包：三层架构中的Web层，负责管理用户的请求和响应，提供控制器来将调用委托到Service层其他上游处理    
 * Service包：负责三层架构中的Service层（业务逻辑层），调用对应的Dao进行数据库的CRUD操作  
 * Dao包：负责三层架构中的Dao层（持久层），由DAO来管理各种数据源的连接和实现数据库的CRUD操作