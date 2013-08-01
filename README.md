weixin-mp-java
==============

基于Java，Spring，Maven实现的微信公众平台一整套代码，从前端Controller到后端的Dao的实现

实现功能：消息接口

未实现功能：通用接口和菜单接口（没内测号命苦啊）

==============

由于涉及的框架比较杂乱，在此一一解释：

1. 简便实用的前置条件：
   你的项目是基于Spring，Maven，Hibernate架构；
   你的项目至少有一个已经存在的配置文件；
   没有在线的Maven仓库，强烈建议clone代码到本地作为子工程使用；

2. 如果你是通过spring-annotation配置bean的话，那么只要在你的Spring xml配置文件里加入以下两句便可：
   	<context:component-scan base-package="com.hamster.weixinmp" />
	<util:properties id="wxProperties" location="classpath:/application.properties"/>
   如果没有util的话，在beans xml声明中加入：
      xmlns:util="http://www.springframework.org/schema/util"
      xsi:schemaLocation="…..
		http://www.springframework.org/schema/util http://www.springframework.org/schema/util/spring-util-3.1.xsd"

2.5. 又或者你实在很懒，那就直接在spring中include默认的配置文件applicationContext-weixinmp.xml便可……

3. 如果不想用数据库，那么只扫描com.hamster.weixinmp.service和com.hamster.weixinmp.controller即可，所有的dao在wxService中配置模式均为可选，如果没有注入，则不会执行存储操作；

4. 项目使用了lombok生成Getter/Setter, toString, hashCode, equals方法，lombok有eclipse插件，具体怎么安装请看这里：http://projectlombok.org/download.html，如果不想用lombok的话那么就手动删掉那些注解并用eclipse等工具重新生成一下这些方法便可。

5. 如果你的项目是通过xml的方式配置的话，你需要将所有的dao，service和controller配置到xml中（浩大的工程= =）

6. 数据库的前缀为wx_，一般来说不会有冲突，真冲突了那就自己手动改改吧，反正也不麻烦

7. 数据库有些额外的字段，比如自增长的id，created_date等，用不到就无视吧

8. 如果你不用maven的话……那就把java代码都拷贝到自己的工程里面去吧……