#### shouldComponentUpdate

1. shouldComponentUpdate 默认情况下返回 true 还是 false ?
* 不显式定义 shouldComponentUpdate 勾子方法的情况下，shouldComponentUpdate 默认返回 true，即每次 state/props 的变化都会触发重新 render.

2. 如果在父组件里调用 forceUpdate, shouldComponentUpdate 返回什么值 ？/ 该方法什么时候不会被调用 ？ 
* initital render 或者在父组件使用 forceUpdate 的情况下，shouldComponentUpdate 是不会被触发的.

3. 如果组件 A 的 shouldComponentUpdate 返回 false, 它的子组件 state 改变时会 re-render 吗？
* 会。只要子组件的 state 改变了, 即使父组件的 shouldComponentUpdate 返回 false, 也不会阻碍子组件的 re-render

4. 该方法有什么作用 ？ 使用时有哪些注意点 ？
* shouldComponentUpdate

5. shouldComponentUpdate 的实际应用场景
* 假定有组件 parent, parent 里有子组件 childA, childB, childC, childA 有值需要依赖来自 parent 的 props, 修改 childA 里依赖 parent props 值的时候, parent 的所有子组件 A, B, C 都会被 re-render.
* 组件反复拿到相同输入值:
  * 比如 Tabs, 我们希望只在不同 tab 之间切换的时候去重新 re-render, 如果反复选中同一个 Tab 不去 re-render.
  * 比如 Input, 有一个 del btn 可以删除 Input 里的所有输入, 我希望反复点击 del btn, Input 清空 val 的 re-render 只执行一次, 就可以用 shouldComponentUpdate 根据字串长度来控制.

#### 受控组件和非受控组件

#### class component/functional component/pure component

#### hoc

#### 虚拟 DOM

#### 脏检查

#### react 引入的新生命周期

#### flux

#### forceUpdate

* 如果页面的 re-render 需要依赖除 state/props 以外的数据，那么可以使用 forceUpdate 来强制 re-render 页面。但实际 coding 过程中，没有真正使用过 forceUpdate，官方也不推荐，正常情况下，所有的数据应该要么来自 state，要么来自 props，个人感觉，react 组件设计不太合理，或者真的很特殊的情况下，才会出现来自 state/props 以外的数据源，一般来讲，react 提供的数据检查机制应该够用了.
