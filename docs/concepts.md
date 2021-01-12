### resolved value[mdn](https://developer.mozilla.org/en-US/docs/Web/CSS/resolved_value)
由 getComputedStyle 函数返回的值
### computed value
由父元素继承过来的值
### used value
computed value 上所有的计算都被执行之后所得到的 value
### specified value
1. 从 style [sheet](https://blog.csdn.net/qq449245884/category_10212382.html?utm_source=ffzl_BWzd) 中获取
2. 如果是 inherit 的属性, 从父元素继承
3. 使用 inital value
### initial value
1. 如果是 inherit properties, 只要是没有提供 specified value, 只应用于根元素
2. 如果不是 inherit properties, 只要是没有提供 specified value, 应用于所有元素