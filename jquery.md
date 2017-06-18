###jQuery
####- 选择器

    使用jQuery获取元素返回的是一个jQuery对象。才能够调用jQuery原型上的方法
	   id：#id
	   class：.class
	   tag：tag
	   如何把jQ对象转化为一个原生dom对象  ==》通过索引值来获取
	   var $res4 = $('#div1 p')[0] 
	   var $res4 = $('#div1 p').get(index);

> 基本选择器

    var $res = $('#div1');
    var $res2 = $('.div');
    var $res3 = $('div');

>层级选择器

    var $res4 = $('#div1 p');//获取div1下所有的p元素
    var $res5 = $('#div1 *');//获取div1下所有元素
    var $res6 = $('#div1，#div2');//同时获取多个元素
    var $res7 = $('#div1 p+');//获取的是p元素的弟弟元素
    var $res8 = $('#div1 p~');//获取p元素所有的弟弟

> 筛选

    var $res = $('#div1 p:first');//第一个p元素
    var $res = $('#div1 p:last');//最后一个元素
    var $res = $('#div1 span:not(.span3)'); // 除了.span3类的其他
    var $res = $('#div1 span:odd'); // 索引为奇数的元素
    var $res = $('#div1 span:even'); // 索引为偶数的元素
    var $res = $('#div1 span:eq(0)'); // 索引等于
    var $res = $('#div1 span:gt(0)'); // 大于索引值
    var $res = $('#div1 span:lt(0)'); // 小于索引值
>内容过滤

    var $res = $('#div1 span:contains(珠)'); // 获取内容包含具体某个字的
    var $res = $('#div1 span:empty'); // 获取内容为空的
    var $res = $('#div1 span:has(.a)');//获取所有span中包含一个.a的span

>表单元素属性过滤

    var $res = $('input:text'); // 属性过滤
    var $res = $('input:radio'); // 属性过滤
    var $res = $('input[type=checkbox][name=b]'); // input:checkbox
    var $res = $('div[xx=abc]');
    var $res = $('input:checked');
    var $res = $('input:disabled');

>筛选方法

    $('#div1').hasClass('div'); 
    // 返回一个布尔值，#div1是否包含div这个class => 作为一个判断的条件
    $('#div1').children('.c1'); 
    // 获取div1内所有元素子节点中包含.c1这个类样式的
    $('#div1').parent(); // 获取div1的父元素
    $('#div1').siblings(); // 获取所有的兄弟节点
    $('#div1').prev(); // 获取哥哥节点
    $('#div1').next(); // 获取弟弟节点
    $('#div1').nextAll(); // 所有弟弟
    $('#div1').prevAll(); // 所有哥哥
> filter find closest

    find : 先获取一个父元素,然后在这个范围内继续获取一般采用find方法
    $div1.find('p');
    $div1.find('span');
    closest : 在所有祖先元素中获取和当前最近的哪一个
    var $res = $div1.closest('.c1');
    filter : 属性过滤
    var $res = $div1.find('span').filter('[a=b][price='+ price +']');

> end() 返回到开头
####-文档操作

    创建元素：
    var $p = $('<p></p>'); 
	append：父元素添加子元素-------------------$div1.append($p);
    appendTo：子元素添加到父元素中---------$span.appendTo($div1); 
    prepend：添加到开头----------------------div1.prepend($h3);
    insertBefore：把A添加到B的前面-------- $(A).insertBefore(B);
    insertAfter：把A添加到B的后面-----------$(A).insertAfter(B);
    after, before：在前面/后面添加元素--- $div1.after('<i></i>'); 
    warp unwarp：给div1添加一个包裹元素- $div1.wrap('<h2></h2>');
    remove：移除元素----------------------------$div1.remove(); 
    replaceWidth replaceAll 替换

####-属性方法

    jq对象----$('#div1');
    dom对象转换成jq对象----$(dom)；
    html(): 如果有参数就是来设置html的值，如果没有参数获取html;
    text(): 如果有就是设置，没有获取;
    attr(): 两个参数是设置，一个参数获取--$(div1).attr('school','zf');
    prop:尤其是表单元素的checked等布尔操作必须要用这个方法,如果是原生可以使用prop，自定义属性attr
    prop : 如果是两个参数就是设置，一个参数就是获取 ,可以用prop('checked')去判定是否是选中状态
    addClass 添加类
    removeClass 移除类
    toggleClass 如果有这个类就删除，没有就增加
    val : 一般用于表单元素，如果有参数就是设置，否则获取value
> css方法：

    $('#div1').css({
        width : 200,
        height : 200,
        opacity : .7
    }).scrollTop(200).css('width',400);
	盒子模型 : 
	offset() innerWidth() innerHeight() scrollTop() scrollLeft()
	offset()获取相对于body的偏移量
	innerWidth()相当于 clientWidth

####-事件
 
    jq对象.click(function);
    jq对象.mouseover(function);
    链式写法:
    $('#div1').css({
        width : 100,
        height : 100,
        background : 'red',
        position : 'absolute',
        left : 0,
        top : 0
    }).click(function (){
        //$(this).css('width',200);
    }).mouseover(function (){
        console.log('mouseover');
    }).mouseout(function (){
    });
 on  jq绑定事件, 同一个事件可以绑定多个函数,如果使用on方法绑定事件，那么当需要移除事件的时候那么绑定实名函数。
 off 移除事件 : 如果移除那么需要指定具体的函数，否则就是把所有的全部移除掉。

     var fn1 = function (){
        console.log(1);
    }
    $('#div1').on('click',fn1).on('click',function (){
        console.log(2);
    }).on('mouseover',function (){
        console.log(this);
    }).off('click',fn1);
     
动画

    animate方法 :
    $(div).animate({},300,'linear',function (){})
    param 1 : 终点 对象  {width : 200, opacity : 1}
	param 2 : 完成时间  duration
    param 3 : 效果 默认linear匀速
    param 4 : 回调 => 动画完成之后要做什么...
	 ps : 在调用animate方法之前我们可以先stop(),防止动画累积问题

ajax

    $.ajax({
        type : 'get/post',
        url : 'data.txt',
        async : false/true,
        cache : false/true,
        dataType : 'json',
        data : {sex : 1, age: 30}, //传递给后台的参数
        success : function (result){
            // result就是我要获取的数据
        },
        error : function (){
            // 404  window.location.href...
        }
    });
工具方法：

    $.toArray()
    $.isArray; // 判断是否是数组
    $.isPlainObject; // 判断是否是{}的对象
    $.isEmptyObject; //
    $.trim(' a  '); // 去首尾空格
    $.makeArray(); // listToArray
    $.each(ary,function (index,item){
		   //遍历
    });
     each :
    $.each 
    定义在jQuery.each 定义在$本身上的 => 遍历数组等集合
    $('div').each 
    定义在jQuery.prototype上的 => 直接遍历获取回来jq对象用的 => 总结 :  jq定义方法，一个是在自己本身添加属性，另外一个在prototype原型上添加属性, 例如css、html等方法依赖jq元素对象的定义在原型上，ajax、each等不以来元素的定义在本身上。

jq拓展：

    $.extend({   => 拓展在jq本身
      fn : function(){}
    })
    $.fn.extend({ => 拓展在原型上的
          fn : function (){}
      })


  








     




























    




