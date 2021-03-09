##### babel.js =>ES6转ES5

##### 先引入react(react核心库)|React

##### 再引入react-dom(react操作dom)|ReactDom

-------------

##### 引入prop-types(用于对组件标签属性进行限制)|PropTypes

对象.propTypes={

​	属性:PropTypes.string.isRequired,//该属性需为字符串(string)，且必填(isRequired)

}

对象.defaultProps={

​	属性:"默认值",//若该属性没有传值，则为默认值

}

放在class对象内则是

```react
static propTypes={ //使用static创建静态属性
	//code...
}
```

------

##### `render()`

`ReactDOM.render(element,container[,callback]);`

在容器(container)内渲染一个react元素(element)

组件开头大写

类式组件需继承父类React.Component，必须有render()

```react
class MyComponent extends React.Component{
    
    //构造器是否接收props,并传递给super,取决于：是否希望在构造器中通过this访问props
    constructor(props){
        super(props);
        //code...
    }
    //！render是必须的
	render(){
        //code...
        return
    }
}
```

构造器内初始化状态this.state={}

.bind(this)生成一个新的函数，改变函数内的this(改变视具体传值而定)

-------

##### ref

1. ###### 字符串形式的ref（官方不推荐使用）
```react
class MyComponent extends React.Component{
    showData=()=>{
   		const {tar}=this.refs;
   		console.log(tar)
   	}
   	render(){
        return <div ref="tar" onClick={this.showData}></div>
   	}
} 
```
2. ###### 回调形式的ref
```react
//如果 ref 回调函数是以内联函数的方式定义的，在更新过程中它会被执行两次，第一次传入参数 null，然后第二次会传入参数 DOM 元素。
class MyComponent extends React.Component{
    showData=()=>{
   		const {tar}=this;
   		console.log(tar)
   	}
    show=(c)=>{
       this.tar=c
        console.log(this.tar)
    }
   	render(){
        return <div ref={a=>this.tar=a}></div> //内联(常用)
        return <div ref={this.show}></div> //类绑定
   	}
}
```

3. ###### createRef() (官方推荐使用)

```react
class MyComponent extends React.Component{
    //React.createRef()调用后可以返回一个容器，该容器可以存储被ref所标识的节点，该容器是专人专用的
    myRef=React.createRef();
    showData=()=>{
   		console.log(this.myRef.current)
   	}
   	render(){
        return <div ref={this.myRef} onClick={this.showData}></div>
   	}
}
```

