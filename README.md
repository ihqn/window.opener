# window.opener
#window.opener安全

<h4>window.opener 的作用</h4>
<p>1，能获取父页面定义的方法</p>
<p>2，并且提供了父页面的整个window，可以直接使用winwindow.opener.location方法，与window.location所含有的一样，能使用window.opener.location.reload,window.opener.href,window.opener.location.replace()，所有location下的方法跟函数都可以使用</p>


<h4>window.opener 出现在哪里</h4>
<h5>a标签</h5>
<p>使用a标签的新窗打开后，链接的页面会出现一个对象window.opener这个对象既是父窗口的对象。这样就可以在点了a标签之后，跳转到其它页面后，改变主窗口的地址。实现钓鱼。<br/>
为所有的的a链接加上rel="noopener noreferrer"，清除掉window.opener这个东西，但是使用开发者工具，手动去掉这段代码后，还是能有window.opener
</p>


<h5>form标签</h5>
<p> 使用target="_blank"会使提交的页面也有window.opener对象。与a标签表现一样</p>
    \<form action="xss.html" method="get" target="_blank">
       \<button type="">提交</button>
    \</form>

<h5>Window.open</h5>
<p>在父页面上全局写了任何方法，子页面都可以调用</p>
    //在a页面
    document.getElementById('pageContent').onclick = function(argument) {
        window.open('b.html')//新打开b页面
    }
    function callback(){
        alert('it is callback')
    }

    //在b页面
    window.opener.callback();
