### vue-history模式 服务器非根目录nginx部署
 #### nginx配置
打开nginx配置文件 vim /usr/local/nginx/conf/nginx_conf

    server{
        ...
        location /html5 { // html5为url地址下的名称  如 http://xxx.com/html5
            alias /home/html5; // 前端文件资源
            index index.html; 
            try_files $uri $uri/ /html5/index.html //找不到文件重定向到的地址  
        }
        ...
    }

#### vue配置
vue-cli 3.0以上版本 新增配置文件 vue.config.js

    module.exports = {
        ...
        publicPath:'/html5/' //和nginx上的 location /html5 保持一致
    }