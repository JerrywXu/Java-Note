# Spring

#### IOC自动装配（一般@autowire自动装配）

#### 1.ByName

```java

    <bean id="dog" class="com.heng.Tset2.Dog"/>
    <bean id="cat" class="com.heng.Tset2.Cat"/>
    <!--autowire="byName" 自动寻找和属性相关的bean，本质是set、方法，会自动匹配个个bean-->
    <bean id="add" class="com.heng.Tset2.Address" autowire="byName">
        <property name="name" value="主人"/>
        <!--<property name="cat" ref="cat"/>-->
        <!--<property name="dog" ref="dog"/>-->
    </bean>

```

#### 2.ByType（默认注入方式）

```java
    <!--
    byName: 会自动在容器上下文中查找，和自己对象set方法后面的值对应的 beanid！
    byType：会自动在容器上下文中查找，和自己对象属性类型相同的bean！
    -->
    <bean class="com.heng.Tset2.Cat"/>
    <bean class="com.heng.Tset2.Dog"/>
    <bean id="add2" class="com.heng.Tset2.Address" autowire="byType">
        <property name="name" value="主人"/>
    </bean>

```

#### 3.gett/set方法注入

#### 4.构造器注入



## AOP











# Spring MVC











# Spring Boot

**自动装配**



**整合WEB**



**整合数据库**



**整合全限**

如 Shiro

Spring Security



**整合中间件**

如缓存

MQ

RPC框架

NIO框架