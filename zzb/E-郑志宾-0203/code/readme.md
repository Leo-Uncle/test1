
# JavaScript 事件

### 1. 事件的绑定
- 事件作为 元素的属性
```javascript
    <button event="JS CODE"></button>
```
- 事件作为 元素对象的属性
```javascript
    element.event = function(){}
    element.event = funName;
```
- 事件监听(标准)
```javascript
    非IE:
        addEventListener('事件名字', funName, false);
    IE:
        attachEvent('事件名字', funName);
```

### 2. 解除绑定
- 第1种和第2种的绑定方式
```javascript
    重写覆盖属性为null 或 空的function(){}
    element.event = null
    element.event = function() {}
```
- 监听方式
```javascript
    非IE:
        removeEventListener('事件名字', funName, false);
    IE:
        detachEvent('事件名字', funName);
```

### 3. 给一组元素绑定事件和this的使用
- 循环绑定事件,获取触发事件的元素对象时,需要使用this
- 元素内部绑定事件时传入this.表示该元素对象自己

### 4. 闭包 closure
- 在循环绑定事件时,将循环变量保留下来,就必须使用闭包
- 用一组元素去控制另一组元素时 请使用闭包
- 语法:
```javascript
    for (...) {
        (function(i,x,y){
            element.event = function (){
                // i,x,y 值皆可用
            }
        })(i,x,y);
    }
```

### 5. 常用事件

### 5.1 鼠标事件
- onclick       单击触发
- ondblclick    双击触发
- oncontextmenu 右击触发/return false阻止系统菜单
- onmouseover   鼠标指向触发
- onmouseout    鼠标移开触发
- onmousedown   鼠标按下触发
- onmouseup     鼠标松开触发
- onmousemove   鼠标移动触发

### 5.2 键盘事件
- onkeydown    按下按键触发
- onkeyup      松开按键触发
- onkeypress   按下并松开按键触发(不是所有按键都能触发,高级事件)
    `上下左右/大小写切换/shift/ctrl/alt 不能触发`

### 5.3 表单事件
- onsubmit   表单被提交时触发
- onreset    表单被重置时触发
- onfocus    获取焦点
- onblur     失去焦点
- onchange   改变表单控件的内容或状态时就触发.
    `用于input元素时,value值变化且失焦才会触发`
- oninput    非IE: 输入时触发(input/textarea)
- onpropertychange  IE(-9.0): 输入时触发(input/textarea)
- onselect   选取文本时触发(input/textarea)

### 5.4 框架/对象事件
- onload    文档加载完触发/图片加载完触发
- onunload  文档关闭时触发 IE
- onbeforeunload  文档关闭时触发 非IE
    `浏览器阻止了关闭前的弹框 需要return "string..."`
- onabort   图片加载过程中中断触发
- onerror   图片加载错误触发
- onresize  窗口/框架大小变化时触发
- onscroll  元素滚动条在滚动时触发

### 5.5 其他事件
- oncopy   拷贝内容时触发
- oncut    剪切内容时触发
- onpaste  粘贴内容时触发
- onplay   音/视频开始播放时触发(audio/video)
- onpause  音/视频暂停时触发(audio/video)
- onended  音/视频播放结束时触发(audio/video)

### 6. Event事件对象
- 6.1 获取
`var e = en || window.event;`
- 6.2 属性
```javascript
    e.clientX  鼠标x坐标
    e.clientY  鼠标y坐标
    e.keyCode  按键码
```

### 7. 常用HTML元素属性
```javascript
    innerHTML   双标签之间的文本

    当前元素 相对与body 或已定位的父元素的 偏移量
    offsetTop
    offsetLeft

    当前元素 左边缘或顶边缘 滚过的像素值
    scrollTop
    scrollLeft

    className   当前元素的class属性值
    tagName     当前元素的标签名
```

--------------------------------------

# BOM

### 1. 什么是BOM
    Browser Object Model 浏览器对象模型

### 2. JavaScript 对象层次
#### 2.1 对象种类
    内置对象 A/S/N/R/D/M/B/G
    自定义对象 Object
    BOM
    DOM

#### 2.2 对象树 (倒树状结构)
                        window
                           |
    history    location  document  screen    navigator
                            |
                doc      html
                            |
                    head   body
                            |
                    h1 p div span h2 img

### 3. BOM 对象
#### 3.1 window
    - 描述整个窗口的
    - 它是JS中 所有对象的根对象
    - 使用window属性/方法时, 可以省略window的调用
    - 自定对象/变量/函数 都属于window

    属性: 见手册
    方法: 
        clearInterval() 取消由 setInterval() 设置的 timeout。 
        clearTimeout() 取消由 setTimeout() 方法设置的 timeout。 
        setInterval() 按照指定的周期（以毫秒计）来调用函数或计算表达式。 
        setTimeout() 在指定的毫秒数后调用函数或计算表达式。 
        
        alert()    警告框
        confirm()  确认框
        prompt()   输入框

        open()     打开
        close()    关闭自己打开过的页面
        print()    打印

        scrollTo() 滚到哪去
        scrollBy() 滚多少

#### 3.2 history
    属性
        length
    方法
        back
        forward
        go

#### 3.3 location
#### 3.4 screen
#### 3.5 navigator
