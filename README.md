# window.opener
window.opener安全

window.opener 的作用
1，能获取父页面定义的方法
2，并且提供了父页面的整个window，可以直接使用winwindow.opener.location方法，与window.location所含有的一样，能使用window.opener.location.reload,window.opener.href,window.opener.location.replace()，所有location下的方法跟函数都可以使用

window.opener 出现在哪里

a标签
使用a标签的新窗打开后，链接的页面会出现一个对象window.opener这个对象既是父窗口的对象。这样就可以在点了a标签之后，跳转到其它页面后，改变主窗口的地址。实现钓鱼。

为所有的a链接加上rel="noopener noreferrer"，清除掉window.opener这个东西，但是使用开发者工具，手动去掉这段代码后，还是能有window.opener

form标签
使用target="_blank"会使提交的页面也有window.opener对象。与a标签表现一样

Window.open
在父页面上全局写了任何方法，子页面都可以调用
//在a页面
document.getElementById('pageContent').onclick = function(argument) {
    window.open('b.html')//新打开b页面
}
function callback(){
    alert('it is callback')
}

//在b页面
window.opener.callback();
