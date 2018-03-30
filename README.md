# 概述
    1.本工程采用spring+spring MVC+spring data jpa的架构;
    2.本工程采用thymeleaf作为模板引擎;
    3.本工程采用logback日志框架。
    4.test
### 【注意事项】
#### 1.日志记录
    (0)logback日志框架在工程启动时会自动检测logback配置文件，默认目录是src/resources/;
    先检索logback-test.xml文件，如果不存在则检索logback.xml文件;
    当logback-test.xml和logback.xml文件都存在时，logback-test.xml文件为有效配置文件;
    当logback-test.xml文件不存在时，则logback.xml文件为有效配置文件;
    【注意】在利用maven打包时，logback-test.xml文件不会被打包到war中。因此，logback-test.xml文件可以用于本地测试开发环境,logback.xml文件可作为生产环境的配置文件来使用;
    (1)logback日志级别由低到高为trace、debug、info、warning和error;当日志级别设定为info时，比info级别低的日志都不予打印.日志级别在logback配置文件中设定；
    (2)在一个类中使用logback进行日志纪录需要导入以下两个类并建立一个private static final的Logger对象，如下所示:
    import org.slf4j.Logger;
    import org.slf4j.LoggerFactory;
    private static final Logger logger = LoggerFactory.getLogger(LoginController.class);
    logger.debug("需要打印的日志信息")
    (3)如果想利用Logger打印一个Object，为减少类型转换引起的时间损耗，应该采用如下方式:
    Object test = new Object();
    logger.debug(""说明信息, {}",test)
    这样，logback会自动识别英文大括号{},并在打印时用后面的test对象替换{}.