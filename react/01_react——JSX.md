---
typora-root-url: ./images
---

# React——JSX

### JSX语法规则及使用：

- 创建虚拟DOM时，不要写引号；
- 标签中混入JS表达式要用{}；
- 样式的类名用className指定
- 内联样式，要用style = {{ key: value }},注意属性名转为小驼峰
- 只能有一个根标签
- 标签必须闭合
- 标签首字母
  - 若小写字母开头，则将改标签转为html中同名元素，若html中无该标签对应的同名元素。则报错
  - 若大写字母开头，react就去渲染对应的组件，若组件没有定义，则报错

```jsx
// 使用

<div id="root"></div>

<script type="text/babel"> 
        const VDOM = （
        	<div>
            	<div className="App">
                <h1 className="title">I am the title</h1>
                <p className="content">I am the content</p>
              </div>
        	</div>
        )
        ReactDOM.render(VDOM, document.getElementById('root'))
</script>
```





> 关于 JSX

![jsx_1](/jsx_1.png)

 		 JSX是JavaScript的一种语法拓展。它和模版语言很接近，但是它充分具备JavaScript的能力。Facebook公司给JSX的定位是JavaScript的“扩展”。直接决定了浏览器并不会像天然支持JavaScript一样支持JSX。JSX会被编译为React.createElement(),React.createElement()将返回一个叫做"React Element"的js对象。

​		**Babel**官网提出babel是一个工具链，主要用于将ECMAScript 2015+版本的代码转换为向后兼容的JavaScript语法，以便能够运行在当前和旧版本的浏览器或其他环境中。 

​		关于JSX的功能模块

```jsx
/*
* 创造一个元素需要知道哪些信息
* type 用于标识节点的类型
* config 以对象的形式传入，组件所有的属性都会以键值对的形式存储在config对象中
* children 以对象形式传入，它记录的是组件标签之间的嵌套内容
**/
export function createElement(type, config, children)

React.createElement('ul', {
  // 传入属性键值对
  className: "list"
},React.createElement("li", {
  key: '1'
},"1"),React.createElement("li", {
  key: '2'
}, '2'))

<ul>
  <li key="1">1</li>
	<li key="2">2</li>
</ul>


/*
* ReactElement
**/

const VDOM = (
	<div className="App">
  	<h1 className="title">I am the title</h1>
    <p className="content">I am the content</p>
  </div>
)

console.log(VDOM) // 标准的ReactElement对象实例---对虚拟DOM的描述



ReactDOM.render(
	// 需要渲染的元素（ReactElement）
  element,
  // 元素挂载的目标容器（一个真实的DOM）
  conteiner,
  // 回调函数，可以用来处理渲染结束后的逻辑
  [callback]
)

ReactDOM.render(<VDOM />, document.getElementById('root'));
```

