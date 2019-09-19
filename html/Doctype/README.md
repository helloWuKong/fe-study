#### DOCTYPE标签以及DOCTYPE的作用
在现在的HTML文件中的顶部基本都会发现<!DOCTYPE html>, 那么它到底是用来的干什么的呢？

##### 基础用法
<!DOCTYPE html>
在MDN中的解释
>In HTML, the doctype is the required "<!DOCTYPE html>" preamble found at the top of all documents.Its sole purpose is to prevent a browser from switching into so-called “quirks mode” when rendering a document;that is, the "<!DOCTYPE html>" doctype ensures that the browser makes a best-effort attempt at following the relevant specifications, rather than using a different rendering mode that is incompatible with some specifications.

大意就是说，在html中文档类型声明是必须的，并且是在文档的最顶端，这个声明是用来防止浏览器在渲染文档时进入到“怪异模式（兼容模式）”的渲染模式, "<!DOCTYPE html>"确保浏览器按照最佳的相关规范进行渲染，而不是使用一个不符合规范的渲染模式。

所以对于HTML文件来说，浏览器使用文件开头的DOCTYPE来决定用怪异模式处理还是用标准模式处理

##### 深入

###### 1.DOCTYPE标签
DOCTYPE标签是**标准通用标记语言（SGML）**的文档类型声明，它的目的是告诉标准通用语言解析器，它应该使用什么样的**文档类型定义（DTD）**来解析文档

所以DOCYTYPE标签是将该文档与对应的**文档类型定义（DTD）**联系起来，使得浏览器能够按照对应的文档类型定义去解析该文档。

###### 2. 浏览器解析时到底使用严格模式还是混杂模式，与网页中的 DTD 直接相关
1. 如果文档中包含严格的DOCTYPE，那么它一般以标准模式呈现
2. 包含过渡DTD和URI的DOCTYPE，也是标准模式呈现，但有过渡DTD而没有URI会导致页面以怪异模式呈现（有URI的过渡DTD--标准模式；没有URI的过渡DTD--怪异模式）
3. DOCTYPE不存在或形式不正确会导致文档以怪异模式呈现
4. HTML5没有DTD，因此没有标准和怪异模式的区分：原因是HTML5不再基于**SGML（标准通用标记语言）**，因此不需要对DTD进行引用，但是需要<!DOCTYPE html>来规范浏览器行为
5. HTML4.01基于**SGML（标准通用标记语言）**，所以需要引用DTD，才能告知浏览器文档所使用的文档类型，如下：<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">

###### 3.标准模式与怪异模式的区别
1. 盒模型的高宽包含内边距padding和边框border
    在W3C标准中，如果设置一个元素的宽度和高度，指的是元素内容的宽度和高度，而在IE5.5及以下的浏览器及其他版本的Quirks模式下，IE的宽度和高度还包含了padding和border。
2. 可以设置行内元素的高宽
    在Standards模式下，给span等行内元素设置wdith和height都不会生效，而在quirks模式下，则会生效。
3. 可设置百分比的高度
    在standards模式下，一个元素的高度是由其包含的内容来决定的，如果父元素没有设置高度，子元素设置一个百分比的高度是无效的
4. 用margin:0 auto设置水平居中在IE下会失效
    使用margin:0 auto在standards模式下可以使元素水平居中，但在quirks模式下却会失效,quirk模式下的解决办法，用text-align属性:
5. quirk模式下设置图片的padding会失效
6. quirk模式下Table中的字体属性不能继承上层的设置
7. quirk模式下white-space:pre会失效


##### 来源
1. MDN：https://developer.mozilla.org/en-US/docs/Glossary/Doctype
2. doctype的作用差异：https://www.cnblogs.com/wuqiutong/p/5986191.html
3. MDN: https://developer.mozilla.org/zh-CN/docs/Web/HTML/Quirks_Mode_and_Standards_Mode#How_does_Mozilla_determine_which_mode_to_use.3F






