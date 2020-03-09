题目：
在数组 arr 开头添加元素 item。不要直接修改数组 arr，结果返回新的数组
输入[1, 2, 3, 4], item=10，输出[10, 1, 2, 3, 4]
function prepend(arr, item) {
}

解答：
function prepend(arr, item) {
    return item.concat(arr)
}
//还是出错，因为一开始还写成splice方法，完全忘了用法，其实和js5的concat方法一样，不过调换一下，item在前arr在后才对，虽然这么说，但直接把item用concat方法还是报错，因为item不是数组对象。。。

大佬解答：
function prepend(arr, item) {
    return [item].concat(arr)
}
//思路是一样的，concat方法组合，item一个元素没啥，直接加个方括号就变成了单个元素的数组，然后两个数组就能用concat方法拼接了

concat用法去看js5.md


其他写法
//使用push.apply
function prepend(arr, item) {
    var newArr=[item];
    [].push.apply(newArr, arr);
    return newArr;
}
//利用slice+unshift/splice
function prepend(arr, item) {
    var newArr=arr.slice(0);
    newArr.unshift(item);//newArr.splice(0,0,item);
    return newArr;
}
//使用join+split+unshift/splice组合
function prepend(arr, item) {
    var newArr=arr.join().split(',');
    newArr.unshift(item);//newArr.splice(0,0,item);
    return newArr;
}
//普通的迭代拷贝
function prepend(arr, item) {
    var newArr=[];
    for(var i=0;i<arr.length;i++){
        newArr.push(arr[i]);
    }
    newArr.unshift(item);
    return newArr;
}

链接：https://www.nowcoder.com/questionTerminal/93994cb28b1c4ec5ad7da4f9c33ebfbe?f=discussion 


