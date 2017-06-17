## 屏幕

1. 屏幕的尺寸 3.5 4.0 5.5指的是对角线的长度 尺寸是固定

## 长度单位

1. px em pt （相对单位）   in cm (绝对单位)

## 像素密度

1. 像素密度指的是1英寸里面的像素的数量 比如1英寸里面是10px   通常有两种 163 3gs   330 4s 通常超过320的像素密度就是高清屏  计算方式 屏幕的分辨率高的平方+屏幕分辨率的宽的平方开根号 除以 英寸

## 设备独立像素

1. 表示真实像素和分辨率像素的一个比例  比如3gs手机 高度480px 宽度320px 分辨率  真实设备 高度480px 宽度320px 即分辨率和真实像素一样的时候 1pt=1px
但是有一些设备 高度960px 宽度640px 分辨率  真实设备 高度480px 宽度320px 即分辨率和真实像素一样的时候 1pt=2px  

## 物理像素和CSS像素

1. 物理像素(分辨率的像素) 960*640
2. CSS像素(真实像素)  模拟器里面看见的320*568

## 移动端调试

1. 模拟器的调试 f12 点击左上角的手机  选择设备切换屏幕宽度
2. 真机调试 电脑和手机要连接一个wifi 电脑使用ghostlab 开启一个网页服务  手机扫描二维码打开

## 视口

1. 视口: 浏览器的可视窗口 在PC端是会受到浏览器窗口变化而变化
2. 视口在PC端是可视窗口(会变的) 在移动端有一个固定的值 通常是默认980
3. 但是默认移动端的时候980会造成网页的缩放或者出滚动条
4. 解决移动端默认视口会造成网页缩放和滚动条 设置meta标签设置默认是视口的宽度等于设备的宽度
    <meta name="viewport" content="width=device-width">

5. 视口的其他属性 初始化缩放 initial-scale=1.0 是否允许用户缩放 user-scalable=no 最大 maximum-scale=1.0 和最小缩放  minimum-scale=1.0
6. meta:vp+tab 凡是写移动端页面一来就是加上视口

## 搭建JD项目结构

1. 创建项目的文件夹
2. 把images uploads 文件夹拷到项目里面
3. 创建index.html 创建css文件夹 创建base.css index.css
4. 写base.css的公共样式 
        1. 样式初始化  
              /*设置盒模型*/
          box-sizing: border-box; /*去除移动端特有的点击高亮效果*/
          -webkit-tap-highlight-color: transparent;
        2. 公共样式
            浮动清除浮动 间距等等


## 实现布局容器

1. 设置一个jd_layout的布局容器 设置默认是width:100% 最大宽度是640 最小宽度是320 居中显示

## 实现顶部搜索区域

1. 实现搜索区域的布局结构(左右两边固定宽度 中间自适应的布局)
        1. flex 实现
        2. margin: 0 100px 让中间的盒子距离两边有一定的距离 但是注意不能给他加上width:100%
        3. padding: 0 100px 让中间盒子的内容从100px开始 右边到100px结束  但是要注意盒模型border-box  width:100%（要写）
2. 实现左边的图标和搜索的图标
        1. 设置背景图 精灵
        2. 注意设置背景图的大小是原始图片的一半(因为移动端设计图片的时候会设计成真实的两倍) background-size:200px 200px;
        3. 背景的定位 要缩小一半(量的top是-200px 设置是-100px)
3. 给jd_search设置固定定位 fixed 同时z-index:999; 设置max-width:640px 因为固定定位的width:100% 相对于浏览器而言 

## 实现轮播图的区域

1. 轮播图的结构 .jd_banner>ul>li>img
2. 分析布局 .jd_banner是width:100%  ul是jd_banner的8倍 ul的宽度是800% ul里面的li元素的宽度是ul的1/8 12.5%(是相对于ul的12.5%也就相当于是jd_banner的100%) 
3. 设置li浮动 设置jd_banner 隐藏溢出 设置图片的宽度100%
4. 小圆点的制作
      1. ul>li*8
      2. 设置ul的宽度 设置li的宽度 加上圆角 加上白色边框 浮动
      3. 让ul定位居中 left:50% （相对于父元素的50%） transfrom:tanslateX(-50%) （相对于自身）
      4. 如果要完全居中 给第一个li元素的间距去掉

## APP的分类和区别

1. web App 就是现在学习的移动web在手机浏览器查看的网页  速度慢 开发简单
2. hybird App 混合APP  HTML5 App 也是混合APP 就是纯粹使用HTML5技术开发的APP 最终通过打包工具打包成APP安装程序 页面都是html页面 外壳是安卓ios的外壳 速度中 开发中等
3. Native App 原生APP 微信 QQ 纯粹使用安卓IOS的开发语言 开发的APP 安装程序 (但是里面也会嵌入一些HTML5写的网页) 大部分功能都是原生开发的 只是会混入一些html5的页面 速度快 开发难

## 导航条的制作

1. 写页面结构 ul>li>a>img+p 
2. 写样式
      1. 写布局 li 浮动 占25% 流式布局(百分比布局)
      2. 调整间距 父元素和子元素用padding 兄弟元素直接用margin
      3. 调整图片大小 居中文字大小居中
      4. 调整整体的背景色 (给ul清除浮动)


## 京东超市商品制作

1. 写页面结构 商品盒子>(商品标题>h3) + 商品内容 > a > img
2. 调整样式
      1. 调整标题的样式 h3的大小颜色 间距 行高 高度 底部边框 设置一个伪元素定位在左边
      2. 调整内容的样式 定义了一些公共样式 width:50 边框 分别给a加上宽度和边框的公共样式  浮动的公共样式 图片100%
      3. 第一个商品内容的图片底部少了一点通过背景颜色填充

## 秒杀商品的制作

1. 写页面结构 商品盒子>(秒杀标题>左边的标题内容和倒计时 + 右边的更多) + 秒杀内容(ul>li>a>img+p)
2. 调整样式
      1. 调整标题的样式 左边的样式 图标大小位置 整体要浮动
      2. 调整倒计时的span的背景色 nth-of-type设置3 和 6的颜色不一样
      3. 调整内容样式 li width 33.33% 浮动
      4. 调整Li里面的图片 60% 调整文字居中

## 搜索框的JS制作

1. 分析实现的原理 
        1. 滚动页面的时候 搜素框的透明度变化
2. 实现步骤
        1. 监听滚动条的滚动事件
        2. 获取滚动条滚动的距离
        3. 获取轮播图的高度
        4. 滚动条滚动的距离/轮播图的高度  求得透明度
        5. 把透明度值设置到搜索框上
        6. 判断 如果滚动条的距离超过了轮播图的高度就不设置透明度(只是性能考虑)
        7. 如果页面刚加载的时候已经到了下面要实现透明度 把获取滚动条距离和计算设置透明度代码放到事件的外面也执行一次


## 倒计时JS的制作

1. 定义一个总时间(秒数)
2. 定义一个定时器 每秒执行一次
3. 在定时器里面 总时间--
4. 分别计算减完之后的总时间的时分秒设置span上
5. 时 总时间 / 3600 分 总时间 % 3600 / 60  秒 总时间 % 60 但是要注意带上地板函数Math.floor()
6. 获取所有的span分别设置十位个位 十位 时/10 个位 时%10 也要地板函数

## 轮播图的制作 (样式的修改)

1. 把轮播图的结构变成10张 第一张是l8 最后一张是l1
2. 调整ul的宽度1000% 调整li元素的宽度10%
3. 调整ul的默认的偏移 ul设置 transform:translateX(-10%);

## 轮播图的动态添加动态设置样式

1. 获取l1图片和l8图片元素
2. 分别把l1图片对象插入到最后面 appendChild() 要克隆插入
3. 把l8图片元素 插入到最前面 insetBefore(图片,第一张图的位置) 要克隆
4. 循环变量所有的Li元素 设置li元素的宽度等于轮播图容器的宽度
5. 设置Ul的宽度是li元素的长度*轮播图容器的宽度
6. 设置ul的默认偏移 -轮播图容器的宽度+"px"
7. 在页面改变的时候也要设置li元素和ul和偏移再次添加一个onresize事件  把获取轮播图容器宽度（不要再次声明变量）和 设置li元素 设置ul的宽度和偏移放到事件里面再次执行一次

## 轮播图的自动无缝轮播

1. 定义一个索引index=1 因为有一张图的默认偏移
2. 设置一个定时器 2秒执行一次
3. 在定时器里面 index++
4. 设置ul的过渡 和设置偏移  -index*bannerWidth+'px';
5. 设置一个定时器 定时器的时间就是过渡的时间 setTimeout() 只会执行一次的定时器 判断index==count-1 index=1 清除过渡 设置位移 


## 移动端的touch事件

1. touchstart 触摸开始触发
2. touchmove 触摸中会触发 持续触发
3. touchend 触摸结束触发
4. touchcancel 触摸中断会触发(了解)
4. 注意这3个事件只能用addEventListener这个方法添加事件

## touch对象

1. touchs 屏幕上的手指对象
2. targetTouches 元素上的手指对象
3. changedTouches 改变后的手指对象
4. 用法 touches 和 targetTouches用法一样 在touchstart 和 touchmouve 用来获取手指对象  在touchend事件里面不能用前两个因为手指都已经离开屏幕 屏幕和元素上就不存在手指对象   changedTouches通常是用在touchend事件

## touch对象里面的属性

1. clientX clientY 获取手指距离视口左上角的位置
2. pageX pageY 获取手指距离页面左上角的位置(包含滚动条的)
3. screenX screenY 获取手指距离屏幕最上角的位置
4. 通常在移动端没有滚动条 所以 clientX 和 pageX 和 screenX 通常使用  client系列


## 实现滑动拖拽元素

1. 注册滑动事件 滑动开始滑动中
2. 分别创建滑动开始的位置和滑动中的位置滑动距离的变量
3. 在开始的时候距离滑动开始是xy位置
4. 在滑动中的时候记录滑动中的xy位置
5. 用滑动中的xy的位置-滑动开始的xy的位置求到滑动的距离
6. 把滑动的距离设置到元素的位移上translate(x,y)
7. 如果要实现连续滑动要在滑动结束的时候每次记录最后结束的位置 下一次滑动加上这个位置

## 事件源对象e.target

1. 作用就是用来获取当前触发这个事件的元素 这样可以给body或者document注册事件来获取里面真正触发事件的元素


## 实现轮播图的滑动操作

1. 注册滑动事件 滑动开始滑动中  滑动开始的时候清除定时器
2. 分别创建滑动开始的位置和滑动中的位置滑动距离的变量
3. 在开始的时候距离滑动开始是x位置
4. 在滑动中的时候记录滑动中的x位置
5. 用滑动中的x的位置-滑动开始的x的位置求到滑动的距离
6. 把滑动的距离设置到ul上的时候还要加上ul已经到达的位置 -index*bannerWidth+distanceX
7. 但是要注意 在滑动中的时候要清除过渡

## 实现滑动结束后的判断翻页还是回弹

1. 注册滑动结束事件
2. 判断滑动的距离有没有大于100 
      1. 如果大于100 判断滑动的距离是正还是负的  如果是正 从左往右滑 切换到上一张 index-- 如果是负的是从右往左滑 切换到下一张 index++  设置位移设置过渡

3. 判断如果滑动距离没有大于100 并且滑动距离大于0 
      1. 直接设置位移设置过渡 回弹 -index*bannerWidth
4. 注意滑动结束后要把定时器加回去

## 过渡完成事件的添加（transitionend）

1. 当滑动到了最后一张 要跳到第一张的位置 当滑动到了第一张要跳到最后一张图的位置 
    index==count-1  index = 1  index=0; index=count-2  清除过渡设置位移


## 节流阀的添加

1. 定义一个isEnd=true
2. 在滑动中到时候判断isEnd==true才执行滑动操作
3. 在滑动结束的翻页或者回弹的时候把isEnd=false（因为翻页和回弹都会加过渡）
4. 在过渡完成事件里面isEnd=true

## 小圆点的添加

1. 获取所有小圆点 删除active类名
2. 给当前的轮播图index对应的小圆点加上active类名
3. 但是要注意小圆点的添加要在过渡完成事件里面加
4. 同时要注意 index-1 因为轮播图的index是从1开始 但是小圆点的索引是0开始


## zpepto的基本介绍

1. 是一个移动端的JS框架 类似于jquery 使用的方式和jquery几乎一模一样
2. 特点就是轻量级 分模块

## zepto的基本使用

1. 引包 
      1. 注意 zepto是分模块的 主模块里面只包含了5个基本的包
      2. 例如要使用一些高级的jquery的选择器 selector.js
      3. 要使用动画 fx.js
      4. 要使用touch相关事件 touch.js


## 使用zepto实现轮播图

1. 动态创建第一个和最后一个元素添加到首尾 克隆标签的方法clone() 
2. 在后面插入是ul.append(要插入的元素) 在前面插入  要插入的元素.inserBefore(要插入元素的位置)
3. 动态设置宽度 width(count*bannerWidth)  lis.width(bannerWidth)//可以给所有Li元素都设置这个宽度
4. 定义index=1索引 添加定时器  index++
5. 执行轮播轮播操作 animate函数
    imgBox.animate({
      要执行动画的属性:值
    },动画的执行时间,动画执行的速度,动画执行完毕的回调函数(类似于过渡完成事件)) 
    在动画完成事件里面进行判断Index==count-1 index=1 设置样式   imgBox.css("left",-index*bannerWidth);判断Index==0 index=count-2 设置样式   imgBox.css("left",-index*bannerWidth);


6. 实现轮播图的滑动
      1. zepto自带了滑动的事件 swipeLeft （从右往左滑动） swipeRight (从左往右滑)
      2.  swipeLeft  切换到下一张 index++ 调用动画
      2.  swipeRight  切换到上一张 index-- 调用动画
7. 实现小圆点的切换
      1. 在动画完成事件里面 indicators.removeClass("active").eq(index-1).addClass("active"); 移除所有active 给index-1添加active


## zepto的定制

1. 可以把一些依赖的包放到一个文件里面
2. 安装nodejs
3. 安装依赖包 npm install
4. 编辑make文件 的41 行 modules = (env['MODULES'] || 'zepto event ajax form ie fx selector touch').split(' ')
5. 运行编译的命令 npm run-script dist


## 分类页面全屏页面的制作

1. 给html 和 body加上高度100% 
2. 头部加上50px的高度 加上定位
3. 身体加上padding-top:50px （盒模型一定要是border-box）
4. 左右两边的自适应 左边浮动 给width:100px 右边加上margin-left:100px（右边的元素不能加width:100%）
5. 头部的图标是制作 左右两边的图标宽高固定 定位在左右两边 中间的表单width:100%加上左右的padding
6. 图标的实现
      1. 设置背景图
      2. 设置背景大小200px 200px
      3. 设置背景图的定位
      4. 设置背景图的定位原点 background-origin
      5. 设置背景图的裁切 裁切掉内容以外的背景部分 background-clip:content-box


## 分类页面左右两侧的内容

1. 左侧页面的布局和样式 调整a的高度行高转块文本居中边框 给左侧的盒子ct_Left加上overflow:hidden; 因为ul里面的内容会超出整个屏幕 出滚动条 要给父元素加overflow:hidden; 
2. 右侧页面  上面一个图片 中间一个标题 下面一些商品信息  百分比布局33.33%  右侧商品信息的内容也是会超出页面的高度出垂直滚动条 ct_Category 加上overflow:hidden; 但是保证ct_Category有一个具体的高度  
      1. 使用JS动态计算设置 ct_Category 高度
      2. 给ct_Right加上伸缩盒子 自动计算高度  display:flex;   flex-direction: column;


## 分类左侧的滑动 

1. 实现连续滑动
      1. 注册滑动开始滑动中 滑动结束事件
      2. 在滑动开始记录startY
      3. 在滑动中距离MoveY
      4. 用distanceY = moveY-startY
      5. 设置位移 给ul设置 top = distanceY （但是这样只能滑动一次）
      6. 在滑动结束事件里面每一次记录上一次滑动的距离  currentY+=distanceY
      7. 在滑动中设置位移 top=currentY+distanceY

2. 滑动距离的判断和滑动结束后弹簧效果
      1. 静止状态下的最大值 0
      2. 静止状态下的最小值 父元素-子元素的高度
      3. 滑动状态下的最大值 0+100
      4. 滑动状态下的最小值  父元素-子元素的高度-100
      5. 在滑动中的时候判断 currentY+distanceY在 最大和最小滑动距离的区间
        if(currentY+distanceY < 100 && currentY+distanceY > 父元素-子元素的高度-100) 条件成立说明在这个区间 才设置滑动
      6. 滑动结束的时候弹簧效果
            1. 判断滑动距离 currentY+distanceY  > 静止状态下的最大值 如果大于静止状态下的最大值  设置位移静止状态下的最大值 同时记录currentY=静止状态下的最大值
            2. 判断滑动的距离 currentY+distanceY  < 静止状态下的最小值设置位移 静止状态下的最小值 同时 记录currentY = 静止状态下的最小值

## 移动端点击事件的延迟

1. 移动端click事件有大概300ms的延迟 原因就是要兼容双击操作
2. 在移动端就不直接使用click事件而使用移动优先的touch事件模拟一个click事件
      1. 判断手指只有一个
      2. 判断触摸开始到触摸结束耗费的时间小于150ms
      3. 判断滑动的距离小于6
      4. 分别注册滑动开始 和 滑动结束事件  
      5. 在滑动开始的时候判断手指的个数 记录滑动开始的位移 记录滑动开始的时间
      6. 在滑动结束的时候判断手指的个数  记录滑动结束的位置 记录滑动结束的时间
      7. 用滑动结束时间-滑动开始的时间<150ms 
      8. 滑动结束的位置-滑动开始的位置<6


## 移动端tap事件的封装

1. 封装到common.js 里面的itcast对象上的属性
2. 参数需要传入一个dom元素和callback回调函数 tap(dom,callback)  callback在最后判断里面调用callback(e);

## 使用tap事件完成左侧点击

1. 点击要切换active类名 
      1. 清空所有li的active
      2. 给当前点击的li添加active类名 e.target.parentNode
2. 设置偏移 
      1. 偏移的距离是当前li的索引(一开始给所有的li添加一个index索引)*li的高度
      2. li.index*li.height
      3. 设置位移设置过渡判断如果超过了最小静止状态的值就设置位移成minTop
      4. 注意不管是设置 li.index*li.height 还是minTop 都要同步currentY的值


## 移动tap和zeptotap事件

1. 问题就是在移动有点透的问题 并且不能兼容PC端

## 使用fastclick解决点透和PC移动兼容的click事件

1. 引入fastclick的包 
2. 初始化页面的所有元素都绑定fastclick  FastClick.attach(document.body);
3. 直接添加click事件 tap.addEventListener("click", function() {
     })  既没有延迟 又没有点透 PC移动都兼容


## iScroll.js插件的使用(做滑动和轮播图的插件)

1. 引入iScroll.js文件
2. 写页面的结构
    ```
        <div class="wrapper" id="wrapper">
            <div>
                <p>它只是需要这样的结构，而不是需要这样的标签</p>
                <p>它只是需要这样的结构，而不是需要这样的标签</p>
                <p>它只是需要这样的结构，而不是需要这样的标签</p>
            </div>
        </div>
    ```
3. 创建iScroll对象
    var myScroll = new IScroll('#wrapper',{
        mouseWheel: true,//支持鼠标滚轮
        scrollbars: true//有滚动条
    }); 传入最外层盒子的选择器


## swipe插件的使用(轮播图插件) (了解)

1. 引入swipe.js
2. 写页面结构
      ```
          <div class="jd_banner">
            <!--图片-->
            <ul class="jd_bannerImg">
                <li>
                    <a href="javascript:;">
                        <img src="./uploads/l1.jpg" alt="">
                    </a>
                </li>
            </ul>
        </div>

      ```
      ```
           .jd_banner {
                width: 300px;
                overflow: hidden;
                /*默认不可见*/
                visibility: hidden;
                position: relative;
            }
            .jd_bannerImg {
                overflow: hidden;
                position: relative;
            }
            .jd_bannerImg > li {
                float:left;
                width:100%;
                position: relative;
            }
            .jd_bannerImg > li img{
                width: 100%;
                display: block;
            }
      ```
  3. 创建swipe对象
     window.mySwipe = Swipe(document.querySelector(".jd_banner"),{
        auto:2000 //自动播放的时间毫秒
    });



## swiper.js插件的使用

1. 引入swiper.css swiper.js （要引入他的css文件）
2. 去官网复制想要的结构
      ```
        <div class="swiper-container" id="swiper0">
            <!--图片-->
            <ul class="swiper-wrapper">
                <li class="swiper-slide">
                    <a href="javascript:;">
                        <img src="./uploads/l1.jpg" alt="">
                    </a>
                </li>
            </ul>
        </div>
      ```
3. 创建swiper对象
     ```
      var mySwiper1 = new Swiper('#swiper0',{
          effect : 'cube',
          cube: {
              slideShadows: true,
              shadow: true,
              shadowOffset: 100,
              shadowScale: 0.6
          }
      }) 如果有多个轮播图 传入选择器推荐使用id
      参数 autoplay:1000定时器时间 loop:true;循环
     ```

## 使用iScroll.js完成右侧分类

1. 注意 ul里面的li浮动了ul没有高度 只能使用overflow:hidden的方式清除浮动 不能用clearfix
2. 给父元素加上相对定位


## 常见的网页布局方式

1. 固定宽度的方式 用在PC端的一些老网站
2. 百分比布局(流式布局) 通常用在专门的移动端网站 移动的京东 淘宝
3. 栅格化布局 把页面分成等分
4. 响应式布局 通过媒体查询判断 适配多个终端 在不同屏幕下改变布局方式

## 什么是响应式布局

1. 一个页面适配多个终端  使用媒体查询来实现 好处就是一个页面适配多个终端只要开发一套页面开发效率高 维护效率也高 缺点代码冗余浪费流量

## 什么是响应式开发

1. 就是使用媒体查询 判断不同屏幕宽度根据不同屏幕调整不同的样式 

## 媒体查询

1. 语法
    @media screen and (条件){
        //满足条件要执行的代码
    }

    @media (条件){
        //满足条件要执行的代码
    }

    但是注意如果要加and and的前后都必须有空格

2. 条件的判断方式
    1. max-width的方式 判断屏幕宽度小于等于某个值的时候生效 比如  max-width:1200px 屏幕宽度小于等于1200px
    2. min-width的方式 判断屏幕宽度大于等于某个值的时候生效 比如 min-width:768px 屏幕宽度大于768px会生效
    3. 通常的屏幕判断有4个档次
        1. 超大屏幕 w>1200 现代的大屏电脑
        2. 中等屏幕 992 < w <1200  2000几年的老式电脑
        3. 小屏幕 768< w < 992 平板设备
        4. 超小屏幕 w < 768 手机设备
3. 条件判断的顺序和媒体查询特性
    1. 媒体查询会向上兼容 比如@media (min-width:768px) 如果没有写大屏的判断
    2. 媒体查询会向下覆盖  比如@media (min-width:768px)   @media (min-width:992px)  如果屏幕1000两个条件都会满足后面的会把前面的覆盖
    3. 当使用min-width判断条件的时候 条件要从小到大写
    4. 当使用max-width判断体条件的时候 条件要从大到小写
4. 媒体查询的一些补充
    1. min-device-width max-device-width 带device的表示判断设备的宽度 在PC端不会受到浏览器窗口变化而变化 但是移动端没有区别
    2. 可以通过媒体查询动态加载样式 
       <link rel="stylesheet" media="screen and (min-width:992px) and (max-width:1200px)" href="b.css">-
    3. not表示取反 
5. 通过媒体查询实现网页的布局
     1. 超大屏幕 w>1200 现代的大屏电脑  一行放4个div   @media screen and (min-width: 1200px)  设置div宽度25% 浮动
     2. 中等屏幕 992 < w <1200  2000几年的老式电脑 一行放3个div   @media screen and (min-width: 992px) 设置div 33.33% 浮动
     3. 小屏幕 768< w < 992 平板设备 一行放2个div   @media screen and (min-width: 768px)    设置div宽度 50% 浮动
     4. 超小屏幕 w < 768 手机设备  一行放1个div 设置div宽度100% 


## 响应式开发框架的介绍

1. 妹子UI
2. framework7
3. bootstrap （重点）

## bootstrap框架

1. 他是一个用来开发响应式的前端最流行的框架


## bootstrap框架的基本使用

1. 下载文件
    1. css  min.css 压缩 theme 主题文件 map映射文件
    2. js min压缩的
    3. fonts(字体文件) 字体文件 字体图标 必须要
    4. 使用的时候要注意不要修改目录结构

## 基本模板的介绍

1. 引包 
  1. 引入bootstrap的css文件 
     <link href="./lib/bootstrap/css/bootstrap.min.css" rel="stylesheet">
  2. 引入jquery (因为bootstrap的js插件依赖jquery)
    <script src="./lib/jquery/jquery.min.js"></script>
  3.引入bootstrap的js文件
      <script src="./lib/bootstrap/js/bootstrap.min.js"></script>
2. 条件注释
   <!--[if lt IE 9]>
    <script src="./lib/html5shiv/html5shiv.min.js"></script>
    <script src="./lib/respond/respond.js"></script>
    <![endif]-->
    当条件成立会执行 永久解决IE兼容 如果条件不成立 就是注释不执行 
3. IE兼容模式
       <meta http-equiv="X-UA-Compatible" content="IE=edge">

## 版心容器container contaienr-fluid

1. contaienr 固定宽度且居中的版心 在不同屏幕会有不同的宽度 媒体查询实现
2. contaienr-fluid 全屏百分百的容器

## 栅格系统

1. 栅格系统默认划分为12份
2. 栅格系统的档次
  1. col-lg w>1200
  2. col-md 992< w < 1200
  3. col-sm 768< w< 992
  4. col-xs 什么屏幕都会生效但是通常是w<768会生效
3. 常见的栅格系统的布局方式
  1. 在lg占4列 在md占3列 在sm占2列 在xs占1列
      col-lg-3  col-md-4 col-sm-6 col-xs-12
4. 列偏移 offset margin 列嵌套 在col-xs-6里面在嵌套一个.row 列排序 push pull 定位
5. 响应式工具  hidden-xs hidden-sm hidden-md hidden-lg

## less的环境搭建

1. 安装node
2. 安装lessc 教学资料 npm里面的所有文件 拷贝到  C:\Program Files\nodejs 或者 C:\Users\zhengwei\AppData\Roaming\npm
3. 编译less文件  lessc test.less test.css
4. 使用webstrom编译less 
  1. 创建less文件 打开右上角的add watcher
  2. program 选中lessc.cmd所在目录
  3. 点击确定
  4. 如果没有add watcher 手动 点击设置 到tools 里面的file watcher 点击+ 加less
