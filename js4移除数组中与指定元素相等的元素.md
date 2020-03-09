要求移除数组arr中，那些所有与item相等的元素，直接在给定的 arr 数组上进行操作，并将结果返回(不新建数组)
示例1
输入“[1, 2, 2, 3, 4, 2, 2], item=2”根据上述要求之后最后会输出[1, 3, 4]。

解答：function removeWithoutCopy(arr, item) {
    return arr.filter(function (elem){
        return elem == item;
    })                     
}
总结：模仿之前思路写的但还是没通过测试，问题出在filter用不转，题意要求其实更适合用splice方法，而且也压根没有想到遍历，相反大佬用for循环遍历数组+if+splice写出来的代码就很棒

大佬解法
function removeWithoutCopy(arr, item) {
    for(var i=0; i<arr.length; i++)
    {
        if(item == arr[i])
        {
            arr.splice(i,1);
            i--;
        }
    }
    return arr;
}
注释：用splice方法很合适，因为会改变原数组。
简单来说思路就是for循环遍历数组操作时加入if判断，每次循环都会进行if判断，符合==item就进行splice方法操作同时i自减（相当于单独对==item的数组元素删除，不影响整个数组），不符合条件就正常遍历，最后把这个被筛选删除过的数组return出来


类似的巧妙做法：
把数组看成是队列，等于item元素直接删除，不等于的，先push再删除。
function removeWithoutCopy(arr, item) {
    var n=arr.length;
     for(var i=0;i<n;i++){
         if(arr[0]!==item)   
             arr.push(arr[0]);
         arr.shift();
    }
    return arr;
}
链接：https://www.nowcoder.com/questionTerminal/a93dd26ebb8c425d844acc17bcce9411
来源：牛客网


补充内容：
①
用法：splice(index,len,[item])会根据参数来改变数组，splice有3个参数，它也可以用来替换/删除/添加数组内某一个或者几个值，参数不同对应操作不同：
index是数组元素下标，从第几个元素开始操作的意思（index=0为第一个元素）；
len是替换/删除操作涉及的元素范围有几个的意思；（如果为0，则数组不变）
item是替换的值，如果想删除操作就不写item值（是替换还是删除就看item参数存不存在）；  

②
用法举例：arr = ['a','b','c','d']想要删除数组第二个元素b，如何写？
根据用法写arr.splice(1,1)即可//含义是从数组下标为1的元素开始，替换/删除操作长度范围是下标1开始的1个元素，没有item参数那么就是删除操作，最后会输出['a','c','d']。

用法举例2：
arr = ['a','b','c','d']想要删除数组元素b和c，如何写？
思路：从b开始即从下标1元素开始，删除就不写参数item，c在b后一位，因此涉及删改长度范围是2，最后根据用法写arr.splice(1,2)即可//最后输出['a','d'] ,记得splice是对象方法因此需要跟在arr对象后面，splice方法里参数用逗号隔开


用法举例3：
arr = ['a','b','c','d']想要修改数组第二个元素b，替换为ttt，如何写？
思路：从b开始即从index为1的下标1元素开始，修改范围len为1即b本身这一个元素，替换item就写ttt，根据用法写出来是arr.splice(1,1,'ttt')//输出['a','ttt','c','d']，不是变量是字符串所以记得加引号

arr = ['a','b','c','d']想要修改数组第二个元素b和c，替换为ttt，如何写？
思路：照旧，从b开始那么index为1，到c结束那么len为2，需要替换为'ttt'那么item为'ttt',最后写出来就是arr.splice(1,2,'ttt')//输出['a','ttt','d']，b和c被ttt替换了


用法举例4 
arr = ['a','b','c','d']想要在下标1的位置给数组加入'ttt'，如何写？
思路：其实是反向操作，因为len为0时，删除操作就不起作用了，但替换操作就变成添加操作了，
因此根据题意和方法能写出index为1，len为0，item为'ttt'，arr.splice(1,0,'ttt') //输出['a','ttt','b','c','d']  
