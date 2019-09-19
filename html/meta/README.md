#### HTML Meta标签

W3CSchools:
> Metadata is data (information) about data.
> The <meta> tag provides metadata about the HTML document. Metadata will not be displayed on the page, but will be machine parsable.
> Meta elements are typically used to specify page description, keywords, author of the document, last modified, and other metadata.
> HTML5 introduced a method to let web designers take control over the viewport (the user's visible area of a web page), through the <meta> tag (See "Setting The Viewport" example below).

大意就是metadata是关于数据的数据（元数据）。
<meta标签>给html文档提供元数据，这些数据不会被展示在页面上，但是会被机器解析。
Meta元素一般被用于指定页面的描述、关键字、作者、最后修改和其他的一些元数据
html5提供了通过<meta>标签让开发者控制视窗大小的方法

MDN:
> HTML <meta> 元素表示那些不能由其它HTML元相关元素 (<base>, <link>, <script>, <style> 或 <title>) 之一表示的任何元数据信息.
> 它的DOM接口 HTMLMetaElement

##### Meta标签的属性
在学习Meta标签的过程中，在MDN上看到了这么一句话 **此元素包括全局属性** ？？？
于是继续查看MDN，发现全局属性其实很好理解：**全局属性**是所有HTML元素共有的属性（比如class），它们可用于所有元素，即使属性可能对某些元素不起作用。
全局属性name在<meta>标签中有比较特殊的语义。

meta标签主要由三个属性组成：name, http-equiv, charset, content

###### charset
此特性声明当前文档所使用的字符编码，但该声明可以被任何一个元素的 lang 特性的值覆盖

###### content
content属性包含http-equiv或name属性的值

###### http-equiv
http-equiv顾名思义，相当于http的文件头的作用，它的属性值包括：
1. Expires(期限)：用于设定网页的到期时间，一旦网页过期，必须重新上服务器上获取
```javascript
＜meta http-equiv="expires" content="Wed, 20 Jun 2007 22:33:00 GMT"＞  
//设置每次访问都需要请求最新html代码
 <meta http-equiv="Expires" content="0">
```

2. Refresh(刷新): 指定时间刷新，可以指向新的页面，也可以刷新当前页面
```javascript
＜meta http-equiv="Refresh" content="2；URL=http://www.net.cn/"＞
```
3. Set-Cookie

4. content-Type(显示字符集的设定)(html5中推荐直接使用<meta charset="utf-8" />)

5. cache-control(设置网站的缓存策略)

6. X-UA-Compatible(浏览器采取何种版本渲染当前页面)
```javascript
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"/> //指定IE和Chrome使用最新版本渲染当前页面
```

###### name
name属性用于主要用于设置描述网页的元数据，如果设置了 http-equiv或者charset,就不能在设置这个属性了。

1. application-name，定义正运行在该网页上的网络应用名称
    **浏览器可能会通过使用该属性去区分应用。It is different from the <title> element, which usually consist of the application name but may also contain specific information like the document name or a status;简单的网页不应该去定义application-name meta标签**

2. author，就是这个文档的作者名称

3. description，其中包含页面内容的简短和精确的描述。 一些浏览器，如Firefox和Opera，将其用作书签页面的默认描述。

4. generator, 包含生成页面的软件的标识符。

5. keywords, 包含与逗号分隔的页面内容相关的单词。

6. referrer  控制所有从该文档发出的 HTTP 请求中HTTP Referer 首部的内容

7. viewport(移动端的窗口)

8. robots(定义搜索引擎爬虫的索引方式)

9. generator(网页制作软件)

10. copyright(版权)

11. revisit-after(搜索引擎爬虫重访时间)

12. renderer(双核浏览器渲染方式)


##### Examples:
1. <meta name="keywords" content="HTML, CSS, XML, XHTML, JavaScript">
2. <meta name="description" content="Free Web tutorials on HTML and CSS">
3. <meta name="author" content="John Doe">
4. <meta http-equiv="refresh" content="30">
5. <meta name="viewport" content="width=device-width, initial-scale=1.0">
6. <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"/> //指定IE和Chrome使用最新版本渲染当前页面
7. <meta http-equiv="cache-control" content="no-cache">
    no-cache: 先发送请求，与服务器确认该资源是否被更改，如果未被更改，则使用缓存。
    no-store: 不允许缓存，每次都要去服务器上，下载完整的响应。（安全措施）
    public : 缓存所有响应，但并非必须。因为max-age也可以做到相同效果
    private : 只为单个用户缓存，因此不允许任何中继进行缓存。（比如说CDN就不允许缓存private的响应）
    maxage : 表示当前请求开始，该响应在多久内能被缓存和重用，而不去服务器重新请求。例如：max-age=60表示响应可以再缓存和重用 60 秒。

<!--这个也是iphone私有标签，允许全屏浏览。-->
8. <meta content="yes" name="apple-mobile-web-app-capable">
<!--iphone的私有标签，iphone顶端状态条的样式。-->
9. <meta content="black" name="apple-mobile-web-app-status-bar-style">
<!--禁止数字自动识别为电话号码，这个比较有用，因为一串数字在iphone上会显示成蓝色，样式加成别的颜色也是不生效的。-->
10. <meta content="telephone=no" name="format-detection">

##### 来源：
1. W3CSchools: https://www.w3schools.com/tags/tag_meta.asp
2. MDN: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/meta
