##子目录下配置文件路径，以及vue-router，history
1. 修改router/index.js 下的代码
```
export default new Router({
  mode: 'history',//开启history模式
  base: 'vue/demo/dist',//网站所属的子目录
  routes: [
    {
      path: '/',
      component: HelloWorld
    },
    {
      path: '/home',
      component: home
    },
    {
      path: '/user/:username',
      component: user
    }
  ]
})
```
2. 修改config/index.js
```
##build 模式下的
assetsPublicPath: '/vue/demo/dist/',//修改为网站所属的子目录
```
3. 在网站所属目录下配置apache 的.htaccess（也就是/vue/demo/dist/下）
```
<IfModule mod_rewrite.c>
  RewriteEngine On
  Options +FollowSymLinks

  RewriteBase /vue/demo/dist/
  RewriteRule ^index\.html$ - [L]
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteRule . /vue/demo/dist/index.html [L]
</IfModule>
```