

### 同源策略

1995年，同源策略由 Netscape 公司引入浏览器。目前，所有浏览器都实行这个策略。

同源策略，指的是浏览器对不同源的脚本或者文本的访问方式进行的限制。
> 比如 源a的js不能读取或设置引入的源b的元素属性

目的：是为了保证用户信息的安全，防止恶意的网站窃取数据。
> 比如：A网站是一家银行，用户登录以后，又去浏览其他网站。其他网站可以读取A网站的 Cookie
	


### 跨域

###### 浏览器中的错误提示

> XMLHttpRequest cannot load http://192.168.8.121:8081/iscascloudwatch/rest/node/globalView?_=1503298415246. No 'Access-Control-Allow-Origin' header is present on the requested resource. Origin 'http://192.168.8.121' is therefore not allowed access. The response had HTTP status code 500.
> 

### 主流的处理方式

### window.name + iframe

以前项目中的代码

    <iframe id="instancewatch" src="#" width="100%" height="1245px" frameborder="0">Hello</iframe>
    <script type="text/javascript">
	    $(document).ready(function(){
	    var Urlstr = window.location.host;
	    var Ipstr = Urlstr.split(":")[0];
	    var Reurl = 'http://'+Ipstr+':8081/iscascloudwatch/pages/cloudGlobalView_instance.jsp';
	    //alert(Reurl);
	    $("#instancewatch").attr("src",Reurl);
	    });
    </script>


##### jsonp

现在项目中的

    function instance_global_node() {
        $.ajax({
            url: 'http://' + window.location.host.split(":")[0] + ':8081/iscascloudwatch/rest/instance/globalView',
            type: 'get',
            cache: false,
            data: {
                'userID': document.getElementById('userIdInstance').innerText
            },
            dataType: "json",
            jsonp:'callback',
            jsonpCallback:'callback',
            charset: "utf-8",
            success: function (data) {
			}，
		}）；
	}


##### CORS

自定义的HTTP头部让浏览器与服务器进行沟通


浏览器端  

> Access-Control-Allow-Origin: http://api.bob.com  
> Access-Control-Allow-Credentials: true  
> Access-Control-Expose-Headers: FooBar  
> Content-Type: text/html; charset=utf-8'  

与jsonp进行简单比较  
+ CORS 支持post get请求 ，写法简单功能强大  
+ jsonp对旧版的浏览器兼容性较好  


### document.domain + iframe    
  
只有在主域相同的时候才能使用该方法

### 动态创建script 

### location.hash + iframe

### web sockets



