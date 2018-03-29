## Flexbox布局

### 1.布局模型
flexbox由Flex容器和Flex项目组成，容器即父元素，项目即子元素
任何一个元素可以指定flexbox布局，设为display:flex或display:inline-flex。

更好理解伸缩流，看下图

![image](http://jbcdn2.b0.upaiyun.com/2016/06/05efb4770a9d86050e799aeb8f326476.png)

主轴既可以是水平轴，也可以是垂直轴,项目默认沿主轴排列,还是看图比较明了。

### 2.伸缩容器属性

浏览器支持属性有

- display
- flex-direction
- flex-wrap
- flex-flow
- justify-content
- align-items
- align-content

#### 2.1 display
指定元素是否为伸缩容器
    
    display:flex | inline-flex
注意设为flex布局后，子元素的float、clear和vertical-align属性失效(vertical-align设置元素的垂直对齐方式)
    
#### 2.2 flex-direction    
指定主轴的方向
    
    flex-direction:row | row-reverse | column | column-reverse
row(默认值)：伸缩容器若为水平方向轴，伸缩项目的排版方式为从左到右排列。

row-reverse：伸缩容器若为水平方向轴，伸缩项目排版方式为从右到左排列。

column：伸缩容器若为垂直方向轴，伸缩项目的排版方式为从上到下排列。

column-reverse：伸缩容器若为垂直方向轴，伸缩项目的排版方式为从下到上排列。

#### 2.3 flex-wrap
指定主轴方向空间不足时，是否换行及该如何换行
    
    flex-wrap:nowrap | wrap | wrap-reverse
    
nowrap：即使空间不足，伸缩容器也不允许换行。

wrap：空间不足时，允许换行，若主轴为水平轴，则换行方向为从上到下。

wrap-reverse：空间不足时，允许换行，若主轴为水平轴，则换行方向为从下到上（与wrap时候相反）。
#### 2.4 flex-flow

    flex-flow:flex-direction flex-wrap
    
此属性是flex-direction和flex-wrap的缩写版本

#### 2.5 justify-content

指定沿主轴线的对齐方式
    
    justify-content:flex-start | flex-end | center | space-between | space-around
    
flex-start：向主轴线的其实位置靠齐（默认值）

flex-end：向主轴线的结束位置靠齐

center：向主轴线的中心位置靠齐

space-between：平均分布在主轴线里，第一个伸缩项目在主轴线的开始位置，最后一个伸缩项目在主轴线的结束位置

space-around：伸缩项目平均分布在主轴线里，两端保留一半的空间

#### 2.6 align-items

指定伸缩项目在侧轴方向上的对齐方式

    align-items:flex-start | flex-end | center | baseline | stretch
    
flex-start：向侧轴的起始位置靠齐

flex-end：向侧轴的结束位置靠齐

center：向侧轴的中心位置靠齐

baseline：如伸缩项目的行内轴与侧轴为同一条，则该值与"flex-start"等效，其他情况，该值参与基线对齐

stretch：向侧轴方向拉伸填充整个容器

#### 2.7 align-content

伸缩项目出现换行后在侧轴方向上的对齐方式，要换行必须要有flex-wrap:wrap,其实意思就是换行后每行之间的对齐方式

    align-content:flex-start | flex-end | center | space-between | space-around | stretch
    
flex-start：向侧轴的起始位置靠齐

flex-end：向侧轴的结束位置靠齐

center：向侧轴的中心位置靠齐

space-between：在侧轴中平均分布

space-around：在侧轴中平均分布，且在两边各有一半的空间

stretch：在侧轴上伸展以占用剩余的空间

### 3.伸缩项目属性
    
伸缩项目支持属性有

- order
- flex-grow
- flex-shrink
- flex-basis
- flex
- align-self
3e
#### 4.1 order

这个属性定义项目的排列顺序，数值越小，排列越靠前，默认值为0

    order:integer
    
#### 3.2 flex-grow

定义伸缩项目的放大比例，默认值为0，即若存在剩余空间，也不放大。比如所有伸缩项目的flex-grow为1，那么每个伸缩项目将设置为一个大小相等的剩余空间；如果你将其中一个伸缩项目的flex-grow设置为2，那么这个伸缩项目所占的剩余空间是其他伸缩项目所占剩余空间的2倍。

    flex-grow:number

#### 3.3 flex-shrink

定义伸缩项目的收缩能力,即如果空间不足，该项目将缩小

    flex-shrink:number//默认值为1
    
如果所有项目的flex-shrink的值都为1，当空间不足时，都将等比例缩小，如果一个项目的flex-shrink的值为0，其他项目为1，当空间不足时，前者不缩小。

#### 3.4 flex-basis

设置伸缩项目的基准值，剩余的空间按比率进行伸缩

    flex-basis:length | auto
    
#### 3.5 flex

flex是flex-grow、flex-shrink和flex-basis这三个的缩写

    flex:none | flex-grow flex-shrink flex-basis
    /*
        flex-shrink和flex-basis是可选参数
    */

此处如果flex值为1,相当于flex-grow值为1，该元素把伸缩容器的剩余空间占满。

#### 3.6 align-self

设置单个的伸缩项目在侧轴上的对齐方式，可以覆盖align-items属性，默认值为auto

    align-self:auto | flex-start | flex-end | center | baseline | stretch
    
auto是继承父元素的align-items属性，如果没有父元素，则按照stretch来计算其值，其他的同align-items。

接下来总结一下下react-native中flexbox的使用，在react-native中flexDirection、alignItems和justifyContent可以满足大多数布局需求。

### react-native目前主要支持flexbox的属性

- alignItems
- alignSelf
- flex
- flexDirection
- flexWrap
- justifyContent

#### 1.alignItems

用法同前面说的align-items，区别在与react-native中需要使用驼峰写法

    alignItems:flex-start | flex-end | center | stretch

#### 2.alignSelf

用法同前面说的align-self，区别在与react-native中需要使用驼峰写法

    alignSelf: auto | flex-start | flex-end | center | stretch

#### 3.flex

用法同前面说的flex

    flex：number

#### 4.flexDirection    

用法同前面说的flex-direciton，但react-native中默认是column

    flexDirection: row | column
    
#### 5.flexWrap

用法同前面说的flex-wrap，区别在与react-native中需要使用驼峰写法

    flexWrap:wrap | nowrap

#### 6.justifyContent

用法同前面说的justifyContent，区别在与react-native中需要使用驼峰写法
    
    justifyContent: flex-start | flex-end | center | space-between | space-around
哈哈哈😆！！！

    