title: sitemesh使用
---

## 0X1 说明
sitemesh可以将不同的页面进行组合，通过过滤器来给页面填充header，footer
+ sitemesh2.x无法使用嵌套装饰；另外不能装饰jsp，velocity，freemark以外的页面（其实可以，需要自定义Filter，然后对模板进行解析）
+ sitemesh3.x有装饰器链，可以将一个页面通过多个装饰器进行装饰；不依赖JSP，velocity等框架，可以装饰任何页面

## 0X2 使用
2.x版本就不在这里说明了，新项目需求使用 [jetbrick](http://subchen.github.io/jetbrick-template/2x)模板渲染，2.x中需要重写SitemeshFilter才行。

### sitemesh3.0.0
1. maven中使用，添加至pom
```xml
<dependency>
    <groupId>org.sitemesh</groupId>
    <artifactId>sitemesh</artifactId>
    <version>3.0.0</version>
</dependency>
```
2. 在WEB-INF下添加**sitemesh3.xml**文件
这里的decorator可以是WEB-INF下的页面路径，也可以是URL，区别是指定路径时不会渲染模板，纯html输出，而指定URL时会编译渲染模板，但是这里有点需要注意，/admin/main输出页面中的模板变量是不能引用body.jetx中的。原因：sitemesh过滤的时候，先请求path，然后在请求decorator，最后合并内容输出至页面。
```xml
<?xml version="1.0" encoding="UTF-8"?>
<sitemesh>
    <mapping path="/admin/main" decorator="/WEB-INF/view/body.jetx"/>
    <mapping path="/admin/index" decorator="/admin/base"/>
</sitemesh>
```
3. body.jetx
```html
<html>
  <head>
    <title><sitemesh:write property="title"/></title>
    <sitemesh:write property="head"/>
  </head>
  <body>
    <sitemesh:write property="body"/>
  </body>
</html>
```


+ 其它详细配置参考：[http://wiki.sitemesh.org/wiki/display/sitemesh3/Configuring+SiteMesh+3](http://wiki.sitemesh.org/wiki/display/sitemesh3/Configuring+SiteMesh+3)
+ sitemesh3源码分析：[http://my.oschina.net/321tiantian/blog/43262](http://my.oschina.net/321tiantian/blog/43262)

