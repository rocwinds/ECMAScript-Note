计算给定数组 arr 中所有元素的总和（数组中的元素均为 Number 类型）
自己写的
function sum(arr) {
    for(i=0;i<arr.lentgh;i++){
        x +=arr[i];
    }
    return x;
}
问题在哪？忘了声明和初始化变量x，也忘了声明初始化变量i，其实整体思路没问题，循环遍历数组的值们，赋值加法并用变量容纳


正确代码：感觉正确写法里稍微特别一点的地方是把sum变量声明成function(arr){语句}
        var sum = function(arr) {
            var length = arr.length,
                sum = 0;
            for (var i = 0; i < length; i++) {
                sum += arr[i];
        }
        return sum;



拓展一下：
①用forEach方法去做数组求和
 * @param arr
 * @returns {number}
 *  *  *  *  *  *  *  *  *  *  * 
    var sum3 = function(arr) {
        var sum = 0;
    
        arr.forEach(function(value, index, arr) {
            sum += value;
        }, 0);
    
        return sum;
    };
    链接：https://www.nowcoder.com/questionTerminal/cc3ce199461c4c4cb8f63db61d7eba30?f=discussion
    来源：牛客网



    ②eval
    function sum(arr) {
    return eval(arr.join("+"));
    };

    ③递归
    function sum(arr) {
        var len = arr.length;
        if(len == 0){
            return 0;
        } else if (len == 1){
            return arr[0];
        } else {
            return arr[0] + sum(arr.slice(1));
        }
    }