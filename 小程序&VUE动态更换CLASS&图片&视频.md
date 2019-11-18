### 小程序&VUE动态更换CLASS/图片



##### 小程序：

- 变量更换class

```html
class="[{{nubtext[0]}}]"
```

- 三元表达式更换class

```php+HTML
class="{{listarr[index]=='实'?'crip':'crip-color'}}"
```

- 小程序 —— 动态图片更换

```
<image src="{{'http://jk.100xsys.cn/'+symptomLists[index].nerveNameImg}}" 
```

##### VUE：

- 变量更换class

```html
:class="[{'sliding-block':nubtext[0]==0},
{'sliding-block-right':nubtext[0]==1},
{'sliding-block-left':nubtext[0]==-1}]"
```

- **更换背景图**

```
 :style="{backgroundImage: 'url('+item.nerveNameImg + ')'}"
```

- 三元表达式更换class

```
 :class="listcrip[index]=='实'?'small-crip':'small-crip-color' "
```

- 点击更换class（点击变色）

```
<li class="liMenu" 
        :class="idx==index?'hover':''" @click="son(item,idx)" v-for="(item,idx) in menu"                 
        :key="idx">{{item}}
</li>
```

```

data(){
        return{
            menu:['首页','列表页','详情页'],
            index:0
        }
    },
    methods:{
      son(item,idx){
          this.index=idx;
      }
}
```

###### 绑定数据报错undefined

```
    <div v-if="symptomList[index]" class="text-block">
                {{symptomList[index].content}}
     </div>
```

> 原因：页面渲染时data中数据未加载/data中定义空数组，导致报错 解决方法1.空数组填充字段。2.v-if判断是否数据加载



