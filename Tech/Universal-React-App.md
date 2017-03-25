# Universal React App 总结。
1. 出现的目的。
single page application的问题有SEO的不友好，因为页码是在client端生成的。所以SEO就不太处理了。第二个是加载速度的问题，client render的page内容等到渲染完成了才能看到。所以有时候是比较慢的。所以因为上边的原因就出现了server rendering的技术。
其实从历史来讲，之前的web技术的都是server side render的，例如说JSP， rails使用的haml文件扥等。因为nodejs的出现使得client和server段可以共用一段代码，这样的背景下就出现了所谓的server side rendering的react app。

## 一个数据上的问题。
如果是server render的app 获取数据的逻辑放到哪里？如果还是放到client段，那么实际内容的页面还在client render出来的，所以应该放到server段加载，得到获取数据的异步请求回来会，再渲染页面，send response。这点是要特别注意的。