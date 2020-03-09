题目：
function indexOf(arr, item) {};
要求找出元素 item 在给定数组 arr 中的位置，并输出不同情况:如果数组中存在 item，则返回元素在数组中的位置，否则返回 -1

代码：
学着写的
function indexOf(arr, item) {
    if(arr.prototype.indexOf){
        return arr.indexOf(item);
    }else{
        for(i=0,i<arr.length,i++>{
            return i;
        })
    }
    return -1;
}//问题：写的错误很多，rototype方法不懂，for循环写错，思路没有理清
//现在重新整理，首先题目给定function了一个函数indexOf，还有两个参数arr, item，要求arr中找到item，有就返回在arr的位置(第几个数字)，没有就返回-1；


//因此可以用到if判断、遍历数组需要用到for循环也是老惯例了；同时查阅资料明白还可以用indexof(),lastindexof()来表示要查找的项和起点位置的索引；

//因此最先进行一个if，判断条件是Array.prototype.indexOf()，符合条件就直接用这个ECMAScript提供的indexof方法去查找的某个项在数组中位置的索引，没有就返回-1；
//不符合条件写一个else，执行for循环遍历数组,for(var i=0;i<arr.length;i++){arr[i]}，这个arr[i]执行语句也要用if判断一下，改为if（arr[i]===item）{return i};这一串代码来在遍历数组arr时，如果arr的第i个元素===item时就算符合要求执行return i；输出这个i值(item在arr中的位置索引值)



标准的答案：
function indexOf(arr, item) {
  if (Array.prototype.indexOf){
      return arr.indexOf(item);
  } else {
      for (var i = 0; i < arr.length; i++){
          if (arr[i] === item){
              return i;
          }
      }
  }     
  return -1;
}
链接：https://www.nowcoder.com/questionTerminal/e7835a8113dd48afb15f77ef8d1dcb1d?f=discussion
来源：牛客网