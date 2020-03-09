要求移除数组 arr 中的所有值与 item 相等的元素。不要直接修改数组 arr，结果返回新的数组。
具体来说就是：本来有[1,2,3,4,2] ，要求去掉和2一样的数组元素；到最后输出：[1,3,4]。
function remove(arr, item) {

}

解答：基于要求返回新的数组，filter方法很合适，filter()进行过滤满足的数组属性将保留，并返回一个新数组
function remove(arr, item) {
    var x = arr.filter(item==2);
    return x;
}
思路没问题，主要还是用法不熟练，filter会将数组里符合条件的部分抽出来形成新数组因此直接输出也是ok的，我写的错误集中在filter方法条件写错了因此无法过滤出正确的数组，





function remove(arr, item) {
    return arr.filter(function (elem) {
        return elem !== item;
    });
}


另一种方法
for循环push()进新的数组中（像这种循环遍历对数组无增删的也可以选用forEach，遇到与item不等的直接push进新数组
function remove(arr,item){
    var newarr = [];
    for(var i=0;i<arr.length;i++){
        if(arr[i] != item){
            newarr.push(arr[i]);
        }
    }
    return newarr;
}
//遇到与item相等直接进入下一轮循环
function remove(arr,item){
    var newarr = [];
    for(var i=0;i<arr.length;i++){
        if(arr[i] == item)continue;
       newarr.push(arr[i]);
    }
    return nawarr;
}

还有一种：
使用splice()删除与item相同的值并把数组索引回退一个值（i--）
（适用于在原数组移除）
function remove(arr,item){
    var newarr = arr.slice(0);
    for(var i=0;i<newarr.length;i++){
        if(newarr[i] == item){
            newarr.splice(i,1);
            i--;
        }
    }
    return newarr;
}


附录：filter方法
语法
var newArray = arr.filter(callback(element[, index[, array]])[, thisArg])
参数
callback
用来测试数组的每个元素的函数。返回 true 表示该元素通过测试，保留该元素，false 则不保留。它接受以下三个参数：
element
数组中当前正在处理的元素。
index可选
正在处理的元素在数组中的索引。
array可选
调用了 filter 的数组本身。
thisArg可选
执行 callback 时，用于 this 的值。
返回值
一个新的、由通过测试的元素组成的数组，如果没有任何数组元素通过测试，则返回空数组。



