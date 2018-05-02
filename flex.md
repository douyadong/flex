# flex布局
## flex布局是什么？
1. flex：弹性布局，用来为盒状模型提供最大的灵活性;
2. **任何一个元素(包括固定宽高的元素)**都可以指定为flex布局。
```
.father{
    display:flex;
}
```
3. webkit内核的浏览器，必须加上-webkit前缀。
```
.father{
    display:-webkit-flex;
    display:flex;
}
```
4. **设置为flex布局以后，子元素的float、clear和vertical-align属性将失效。**
5. 采用flex布局的元素，称为flex容器，简称"容器"。它的所有子元素自动成为容器成员，称为flex项目，简称'项目'。

## 容器的属性
1. flex-direction:决定主轴的方向(即项目的排列方向)
```
.father{
    display:flex;
    display:-webkit-flex;
    flex-direction:row (默认值，主轴为水平方向，七点在左端，即项目水平排列，从左至右);
    flex-direction:row-reverse(主轴为水平方向，七点在右端);
    flex-direction:column(主轴为垂直方向，七点在上沿，即项目从上到下排列);
    flex-direction:column-reverse(主轴为垂直方向，起点在下沿)
}
```
2. flex-wrap:如果项目在一行排列不下，如何换行;
```
.father{
    display:flex;
    display:-webkit-flex;
    flex-wrap:nowrap(默认值，项目不换行，即使当父元素设置宽高，子元素也设置宽高，子元素总的宽高大于父元素宽高也不换行，会溢出);
    flex-wrap:wrap(项目超出容器尺寸，自动换行，按正常顺序排列，第一行在上);
    flex-wrap:wrap-reverse(换行，第一行在下方);
}
```
3. flex-flow :该属性是flex-direction属性和flex-wrap属性的简写方式，默认为row nowrap;
```
.father{
    flex-flow:<flex-direction>||<flex-wrap>;
}
```
4. justify-content：该属性定义了项目在水平主轴上的对齐方式;
```
.father{
    display:flex;
    display:-webkit-flex;
    justify-content:flex-start(左对齐，从左边开始排列);
    justify-content:flex-end(右对齐，最后一个元素在最右边);
    justify-content:center(项目居中对齐);
    justify-content:space-between(两端对齐，项目之间的间隔相等,第一个项目位于左端，最后一个位于右端，中间等距排列);
    justify-content:space-around(每个项目两侧的间隔相等，所以项目之间的间隔比项目与边框的间隔大一倍);
}
```
5. align-items:该属性定义项目在交叉轴(垂直轴)上如何对齐;(当项目为水平排列时)
```
.father{
    display:flex;
    display:-webkit-flex;
    align-items:flex-start(交叉轴的起点对齐);
    align-items:flex-end(交叉轴的终点对齐);
    align-items:center(交叉轴的中点对齐);
    align-items:baseline(项目的第一行文字的基线对齐);
    strech(默认值)：如果项目未设置高度或设为auto，将占满整个容器的高度;
}
```
6. align-content:该属性定义了多根轴线的对齐方式，如果项目只有一根轴线，该属性不起作用;
```
.father{
    display:flex;
    display:-webkit-flex;
    align-content:flex-start(与交叉轴的起点对齐);
    align-content:flex-end(与交叉轴的终点对齐);
    align-content:flex-center(与交叉轴的中点对齐);
    align-content:space-between(与交叉轴的两端对齐,轴线之间的间隔平均分布);
    align-content:space-around(每根轴线两侧的间隔都相等，所以轴线之间的间隔比轴线与边框的间隔大一倍);
    align-content:stretch(默认值，轴线占满整个交叉轴);
}
```
## 项目的属性
1. order:定义项目的排列顺序，数值越小，排列越靠前，默认为0;
```
.item{
	order:<integer>(整数)；
}
```
2. flex-grow:定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大;
```
.item{
	flex-grow:<number>;/*default 0 */
}
如果所有项目的flex-grow属性都为1，则他们将等分剩余空间（如果有的话），如果一个项目的flex-grow属相为2，其它项目都为1，则牵着占据的剩余空间将比其它项多一倍。
```
3. flex-shrink：定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。
```
.item{
	flex-shrink:<number>;/* default 1 */
}
如果所有项目的flex-shrink属性都为1,当空间不足时，都将等比例缩小。如果一个项目的flex-shrink属性为0，其它项目都为1，则空间不足时，前者不缩小。负值对该属性无效。
```
4. flex-basis :flex-basis属性定义了在分配多余空间之前，项目占据的主轴空间（main size）。浏览器根据这个属性，计算主轴是否有多余空间。它的默认值为auto，即项目的本来大小。
```
.item{
	flex-basis:<length> | auto; /* default auto */
}
它可以设为跟width或height属性一样的值（比如350px），则项目将占据固定空间。
```
5. flex：flex属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。后两个属性可选。
```
.item {
  flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ]
}
该属性有两个快捷值：auto (1 1 auto) 和 none (0 0 auto)。
建议优先使用这个属性，而不是单独写三个分离的属性，因为浏览器会推算相关值。
```
6. align-self:align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。
```
.item {
  align-self: auto | flex-start | flex-end | center | baseline | stretch;
}
该属性可能取6个值，除了auto，其他都与align-items属性完全一致。
```
