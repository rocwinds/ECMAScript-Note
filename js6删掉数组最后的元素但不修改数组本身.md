题目描述:
删除数组 arr 最后一个元素。不要直接修改数组 arr，结果返回新的数组
输入[1, 2, 3, 4] 删除掉4，最后输出[1, 2, 3];
function truncate(arr) {
}

解答：
function truncate(arr,item) {
    return truncate(item)
}
还是错了，问题出在不了解slice和truncate方法，思路也有些问题不能随便改题目，题目本身还是很简单的只需要用slice方法选取arr中的要求部分[1, 2, 3]就变相达成要求了


大佬解答：
function truncate(arr) {
	return arr.slice(0,arr.length-1);    
}//还可以简写，return arr.slice(0,-1)也是ok的，因为end部分其实是默认stringObjecr.length的，end取负数时实际是stringObjecr.length减去对应负数的


补充：
slice()方法用于提取字符串的某个部分，返回值为一个新的字符串，里面字符串均来自stringObject，从start开始（包括 start到 end 结束（不包括 end）为止的所有字符。，并不影响原先字符串（因为用于字符串所以和之前对元素和数组对象操作是不一样的）。

语法：stringObject.slice(start,end)

第一个元素是下标0;值得一提的是这两参数可以用负数！负数参数在slice方法中代表了倒过来数，从字符串尾部倒数第一个字符是下标-1，倒数第二个字符下标为-2；

需要注意如果只有一个start并且取负数时，做法是倒过来数取到对应字符作为开头，然后一直选到字符串结尾；如果end是负数的话，也是倒过来数到对应字符，和start负数不同，end负数实际还是非选中部分的开头第一位数字，简单点说，end部分是永远不会被选中的。


实例
例子 1
在本例中，我们将提取从位置 6 开始的所有字符：
<script type="text/javascript">
    var str="Hello happy world!"
    document.write(str.slice(6))
</script>
输出：happy world!（可以看到空格也会计算字符）

例子 2
在本例中，我们将提取从位置-12开始的所有字符：
<script type="text/javascript">
    var str="Hello happy2world!"
    document.write(str.slice(-12))
</script>
输出：happy2world!（倒过来取开头也一样）


例子 3
在本例中，我们将提取从位置 6 到位置 11 的所有字符：
<script type="text/javascript">
    var str="Hello happy3world!"
    document.write(str.slice(6,11))
</script>
输出：happy（会看到第11位字符'3'其实没有被选中，说明end其实是不被选中的部分开头）

例子4
在本例中，我们将提取从位置 6 到位置 -7 的所有字符：
<script type="text/javascript">
    var str="Hello happy3world!"
    document.write(str.slice(6,-7))
</script>
输出：happy（其实等价于例子3，end参数为str.length-7）



再补充：
String 对象的方法 slice()、substring() 和 substr() （不建议使用）都可返回字符串的指定部分。slice() 比 substring() 要灵活一些，因为它允许使用负数作为参数。slice() 与 substr() 有所不同，因为它用两个字符的位置来指定子串，而 substr() 则用字符位置和长度来指定子串。

还要注意的是，String.slice() 与 Array.slice() 相似。



