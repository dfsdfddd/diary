# iscroll练习  
工作中经常用到iscroll，在这里做个记录的demo  
＃ development && 运行  
```
npm install  
gulp  
```  
打开src的index.html
**因为访问Github上的json数据，所以会比较慢  

# 说明  
browser-sync是用来解决开发是跨域请求的，设置一个本地服务器代理转发至后台服务器  

```  
gulp.task('browser-sync', function () {
    var proxyMiddleware = require('http-proxy-middleware');
    var proxy1 = proxyMiddleware('https://raw.githubusercontent.com/fengnovo/diary/master/plugins-test/iscroll/ajax-json',
        {target: 'https://raw.githubusercontent.com/fengnovo/diary/master/plugins-test/iscroll/ajax-json/'});
    browserSync.init({
        server: {
            baseDir: DIST_DIR,
            middleware: [historyApiFallback(), proxy1]
        }
    });
});  
```