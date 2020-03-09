在数组 arr 末尾添加元素 item。不要直接修改数组 arr，结果返回新的数组
示例1
输入[1, 2, 3, 4]，item=10，最后输出[1, 2, 3, 4, 10]
function append(arr, item) {}

解答：
function append(arr, item) {
     arr.push(item)
}
总结，不符合题意呀，push方法会变动数组，虽然作用确实是在数组最尾推入一个数字


大佬解答：
function append(arr, item) {
    return arr.concat(item)
}
很简洁的写法，只用到concat方法，arrayObject.concat(arrayX)将数组对象arrayObject最后加一个元素arrayX，然后返回一个生成新的数组。

补充内容：
concat方法，轻松缝合多个数组，并！且！会返回一个新的数组，不涉及原数组变动。
语法arrayObject.concat(arrayX,arrayX,......,arrayX)，arrayX可以是单个元素也可以是数组，多个arrayX按前后顺序拼接，最后统一拼接到arrayObject数组对象尾部。
记住！arrayObject是数组对象，因此concat方法也仅限于数组对象用

参考例子：https://www.w3school.com.cn/jsref/jsref_concat_array.asp


其他
题目描述
删除数组 arr 最后一个元素。不要直接修改数组 arr，结果返回新的数组 
输入例子:
truncate([1, 2, 3, 4])
输出例子:
[1, 2, 3]

function truncate(arr) {
	return arr.slice(0,-1);   
}


题目描述
在数组 arr 开头添加元素 item。不要直接修改数组 arr，结果返回新的数组 
输入例子:
prepend([1, 2, 3, 4], 10)
输出例子:
[10, 1, 2, 3, 4]

function prepend(arr, item) {
	var newarr=arr.slice(0);
	newarr.unshift(item);
	return newarr;
}


题目描述
删除数组 arr 第一个元素。不要直接修改数组 arr，结果返回新的数组 
输入例子:
curtail([1, 2, 3, 4])
输出例子:
[2, 3, 4]
function curtail(arr) {
	var newarr=arr.slice(1);
	return newarr;
}


push, pop, shift, unshift的区别：
push: 向数组末尾添加一个或多个元素，返回新的长度
pop: 从数组末尾删除一个元素，返回这个元素
shift：删除数组的第一个元素，返回这个元素
unshift:向数组开头添加一个或多个元素，返回新的长度