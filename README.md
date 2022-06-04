# dom-event-training
dom-event-training

```
基本概念： DOM事件的级别
DOM事件模型
DOM事件流
描述DOM事件捕获的具体流程
Event对象的常见应用
自定义事件


DOM1没有和事件相关的定义
DOM2有和IE上区别的使用 attachEvent
DOM3的事件类型增加了很多，比如一些鼠标事件

true / false

true 为捕获
false 为冒泡



浏览器在用户交互的过程，比如鼠标点击

1、捕获，通过捕获到达目标元素
2、目标阶段
3、冒泡，目标元素上传到window对象



JS获取HTML标签： documentElement


event.preventDefault() 阻止默认事件
event.stopProgagation() 阻止事件冒泡
event.stopImmediatePropagation() 通过优先级的方式
事件委托，把子元素的事件绑定转移到父元素，一次性绑定
event.currentTarget  当前绑定事件的元素，比如父元素
event.target  表示被点击的元素


1、new Event声明一个事件
2、通过DOM2事件绑定
3、DOM节点触发这个自定义事件

CustomEvent可以定义事件以外的其他属性
```

```
<div class="target">
    click me!
</div>
```

```
 // 与捕获流程一致 capture为false即为冒泡
  var ev = document.querySelector(".target");

  window.addEventListener("click", function() {
      console.info("window capture")
  }, true);

  window.addEventListener("click", function() {
      console.info("document capture")
  }, true)

  document.documentElement.addEventListener("click", function() {
      console.info("html  capture")
  }, true)

  ev.addEventListener("click", function() {
      console.info("ev capture")
  }, true)

  document.body.addEventListener("click", function() {
      console.info("body capture")
  }, true)


  // 自定义事件
  var eve = new Event("test");
  ev.addEventListener("test", function() {
      console.info("test dispatch")   
  })
  setTimeout(function() {
      ev.dispatchEvent(eve); // 触发自定义事件
  }, 1000)
```
