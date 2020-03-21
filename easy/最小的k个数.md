- **题目地址**

  [题目传送门](https://leetcode-cn.com/problems/zui-xiao-de-kge-shu-lcof/)
  
- **题目描述**

    输入整数数组 arr ，找出其中最小的 k 个数。例如，输入4、5、1、6、2、7、3、8这8个数字，则最小的4个数字是1、2、3、4。

    示例 1：

    ```text
    输入：arr = [3,2,1], k = 2
    输出：[1,2] 或者 [2,1]
    示例 2：

    输入：arr = [0,1,2,1], k = 1
    输出：[0]
    ```
 
    限制：

    ```text
    0 <= k <= arr.length <= 10000
    0 <= arr[i] <= 10000
    ```
  
---
- **个人代码**

  ```javascript
    /**
    * @param {number[]} arr
    * @param {number} k
    * @return {number[]}
    */
    var getLeastNumbers = function(arr, k) {
        return arr.sort((a, b) => a - b).slice(0, k);
    };
  ```
  
- **其他解法**

  ```javascript
    // 使用快速排序
    var getLeastNumbers = function(arr, k) {
        return quickSort(arr).splice(0, k)
    }

    function quickSort(arr) {
        if( arr.length <= 1) return arr
        const [pivot] = arr.splice( Math.floor( arr.length/2 ), 1 ) 
        let left = [], right=[]
        for( let i=0;i<arr.length; i++ ){
            if( arr[i] < pivot ){
                left.push(arr[i])
            }else{
                right.push(arr[i])
            }
        }
        return quickSort(left).concat([pivot], quickSort(right))
    }
  ```
  
- **思考**

    这次使用的是 `JavaScript` 的内置函数，后续的话可以考虑不依赖这种方式，用一些算法的思想去解决，比如 `快速排序`、`堆排序` 等，主要还是要学习一些基本的算法排序。

  
- **参考链接**

    [快速排序算法详解（原理、实现和时间复杂度）](http://data.biancheng.net/view/117.html)