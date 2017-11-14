# 代码规范
## 1.在引入文件时，将引入的react的内置文件放在一起，引入的第三方文件放在一起，自己编写的组件引入放在一起,分别换行隔开。

## 2.建议在引入多个'antd'中的组件时，将它们按字母顺序排列，以方便快速找到是否已引入。
```
// good
import { Icon, Layout, Menu, Steps } from 'antd';

```

## 3.创建 React Component的方式
如果组件拥有内部的 state 或 refs ,推荐使用 class extends React.Componet,除非你要使用 mixin.
```
// bad
const User = React.createClass({
    render() {
        return <div>{this.state.name}</div>
    }
}) 

//good
class User extends React.Component {
    render() {
        return <div>{this.state.name}</div>
    }
}

```
why: 这两种方法本质上都是用来创建组件,只不过一个是ES5语法,一个是ES6语法,createClass 支持定义PureRenderMixin,这种写法官方现不再推荐

## 4.命名

### 扩展名: 使用.jsx React组件的扩展

### 文件名: 文件名使用帕斯卡命名. 例: AddProject.jsx

### 引用命名: 引用实例采用驼峰命名法。
```

// bad
import addProject from './AddProject';

// good
import AddProject from './AddProject';

// bad 
const ProjectItem = <AddProject />;

// good 
const projectItem = <AddProject />;

```

### 组件命名:组件的名称应和文件名保持一致.如果是在目录中的组件,应该使用 index.jsx 作为文件名,使用文件夹名称作为组件名.
```

// bad 
import Tasks  from './Tasks/Tasks';

// bad
import Tasks from './Tasks/index';

// good
import Tasks from './Tasks';

```

## 5.声明
不要使用 displayName 属性命名组件,应该使用类的引用名称.
```

// bad 
export default React.createClass({
    displayName:'AddProject'
})

// good 
export default class AddProject extends React.component{

}

```
## 6.对齐
```
// bad
<WrappedFormExportData ref={this.saveFormRef}
  										 loading={this.state.loading}
/>

// good
<WrappedFormExportData
	ref={this.saveFormRef}
	loading={this.state.loading}
/>

```
组件的属性比较少时可以放在一行就放在一行中,属性很多时可换行,方便代码阅读

```
// bad
<Search className="search" placeholder="输入项目名" size="default" onSearch={this.onGroupProjectsSearch} />


// good
<Search
	className="search"
	placeholder="输入项目名"
	size="default"
	onSearch={this.onGroupProjectsSearch}
/>

```

## 7.空格
在自闭合标签前面添加一个空格.
```
// bad 
<Search/>

// good
<Search />

```

## 8.引号
一般都使用单引号. JSX属性都使用双引号,还有在编写JSON代码时使用双引号.

```
// bad 
<Search className='search' />

// good 
<Search className="search" />

// bad 
<Search style={{left: "10px"}} />

// good
<Search style={{left: '10px'}} />

```

## 9.属性
### 属性名称使用驼峰命名法

```
// bad
<Search UserName="zhangsan" />

// good 
<Search userName="zhangsan" />

```
### 当属性的值为true时,省略该属性的赋值

```
// bad
<Search loading={true}/>

// good
<Search loading/>

```

## 10.括号
用括号包裹起来多行JSX标签

```
// bad
render() {
	return <div className="page-searchSuggestShow">
					<h2>suggest查询结果</h2>
					<WrappedFormSuggestShow ref={this.saveFormRef} />
			   </div>
}

// good 
render() {
	return (
		<div className="page-searchSuggestShow">
			<h2>suggest查询结果</h2>
			<WrappedFormSuggestShow ref={this.saveFormRef} />
		</div>
	);
}
```
## 11.标签
### 当标签没有子元素时,使用自闭和标签
```
// bad
<Search className="search"></Search>

// good
<Search className="search" />

```
### 如果组件有多行属性时,关闭标签要另起一行.

```
// bad 
<Search className="search"
	placeholder="输入项目名"
	onSearch={this.onGroupProjectsSearch} />

// good
<Search className="search"
	placeholder="输入项目名"
	onSearch={this.onGroupProjectsSearch} 
/>
```


## 13.代码长度

建议将行限制为100个字符，以方便整个代码的阅读

## 14.缩进

使用双空格缩进。

## 15.结尾处以分号结尾

## 16.在条件语句之前和之后使用空格
```
// bad
if(true)
{
    console.log('Hello World');
}

//good
if (true) {
    console.log('Hello World');
}

注：花括号与需要的东西在同一条线上。
```

## 17.使用===来判断条件

相比==更加严谨

## 18.注释
将一些重要的信息或者是比较复杂的逻辑简洁的写在注释里，必要的注释会给自己和别人阅读代码时带来很大的方便。
描述变量的注释直接写在变量的右边。
this.setstate({
    columns: []   // 数据库表的列名
})


# 样式部分
### 1.类名
使用 xxx-xxx的格式,id和class的命名应反映该元素的功能，而不要使用抽象的命名。

### 2.在组件的最外层最好有个className，一般用component-文件名   或page-文件名



