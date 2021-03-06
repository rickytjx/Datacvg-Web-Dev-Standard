# Sea.js 规范

---

### 目录结构定义

* 适用于全新开发

```
 |---build
   |---dist 发布
   |---src
     |---index.html 页面入口
     |---assets 资源
         |---sass  sass文件
         |---img  图片文件
         |---font/  字体图标
     |---modules 自定义CMD模块
         |---moduleWindow.js  弹出层组件
     |---plugins 插件
         |---seajs
           |---sea.2.12.1.js
         |---jquery
           |---jquery.1.12.1.js
     |---page 各个页面模块
       |---login    登陆模块
         |---login.html
         |---login.js
       |---welcome       欢迎页模块
         |---welcome.html
         |---welcome.js
```

### 模块代码规范

* 因产品使用的是Sea.js框架来进行模块化开发，阅读到此的人请先阅读[**CMD 模块定义规范**](https://github.com/seajs/seajs/issues/242)
* 遵循CMD规范，每个前端务必遵守以下模块化代码编写规范。

```js
/**
 * 模块化定义规范
 * 
 * @author Ricky Tang
 * Copyright 2016 Datacvg Inc. All Rights Reserved.
 */
define(function(require, exports, module){
    "use strict"; // 开启严格模式
    var $ = require('$'); // 加载jQuery

    /**
     * 定义初始化函数
     *
     * @param {string} options 接收外部参数对象
     * @return {Object} _publish对象
     */
    function _initPublish(options){
        // 默认参数对象
        var defaults = {
            $element: null // 接收DOM对象
        };

        var opts = $.extend(defaults, options); // 合并接收对象数据

        var _publish = {
            /**
             * 模块初始化入口
             *
             * @param {string} opts 外部参数对象与内部默认参数对象合并后的对象
             */
            _init: function(opts){
                $.extend(true, this, opts); // 把合并后接收的对象，继续合并为需要返回的对象

                this.renderData();
                this._initListeners();
                this.callback.afterInit.call(this);
            },
            /**
             * 内部所用的函数
             *
             */
            renderData: function(){
                // 渲染数据。。
            },
            /**
             * 绑定事件监听器
             *
             */
            _initListeners: function(){
                this.utils.delegates(this.$element, {
                    '.btn': function(){
                        // 点击事件
                    },
                    '.btn2': function(){
                        // 点击事件2
                    },
                    '.checkbox': {
                        'change': function(){
                            // change事件
                        }
                    }
                });
            },
            /**
             * 回调事件 外部调用
             *
             */
            callback: {
                'afterInit': function(){}
            },
            /**
             * 工具类事件
             *
             */
            utils: {
                delegates: function(element, configs){
                    var el = $(element);
                    for (var name in configs) {
                        var value = configs[name];
                        if (typeof value === 'function') {
                            var obj = {};
                            obj.click = value;
                            value = obj;
                        }
                        for (var type in value) {
                            el.delegate(name, type, value[type]);
                        }
                    }
                }
            }
        };
        _publish._init(opts);
        return _publish;
    }
    return _initPublish;
});
```



