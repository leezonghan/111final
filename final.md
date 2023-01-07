# 題目
![GITHUB](https://github.com/leezonghan/111final/blob/main/picture/111final.1.png)
# 題目來源
https://cpe.cse.nsysu.edu.tw/cpe/file/attendance/problemPdf/108.pdf
# 解決方法1
One way to solve this problem is to use the Kadane's algorithm, which is an algorithm used to find the maximum sum subarray in a one-dimensional array.

We can apply this algorithm in a two-dimensional array by fixing one row and using Kadane's algorithm to find the maximum sum subarray for that row. Then, we can extend this subarray by including one row at a time and updating the sum accordingly. We can repeat this process for each possible starting row, and keep track of the maximum sum found so far. This will give us the maximum sum subarray for a fixed number of rows.

We can then repeat this process for different number of rows, starting from 1 and going up to the total number of rows in the array. This will give us the maximum sum subrectangle.  
解決這個問題的一種方法是使用 Kadane 算法，這是一種用於在一維數組中找到最大和子數組的算法。

我們可以通過固定一行並使用 Kadane 算法找到該行的最大和子數組來將此算法應用於二維數組。然後，我們可以通過一次包含一行並相應地更新總和來擴展這個子數組。我們可以對每個可能的起始行重複此過程，並跟踪到目前為止找到的最大總和。這將為我們提供固定行數的最大總和子數組。

然後，我們可以對不同的行數重複此過程，從 1 開始直到數組中的總行數。這將為我們提供最大和子矩形。  
# 程式碼1
```python
function maximum_sum_subrectangle(array A):
  rows = number of rows in A
  cols = number of columns in A
  max_sum = minimum possible integer value

  for r1 in 1 to rows:
    for r2 in r1 to rows:
      sum = 0
      for c in 1 to cols:
        for r in r1 to r2:
          sum = sum + A[r][c]
        max_sum = max(max_sum, sum)
  return max_sum
```
# 解決方法2
The idea is to keep track of the maximum sum ending at each position, and then at each step, you consider the maximum sum ending at the previous position and the current element, and take the maximum of the two.

To apply this algorithm to a two-dimensional array, you can do the following:

Loop through each column c in the array
Set the maximum sum ending at column c to 0
Loop through each row r in the array
Set the maximum sum ending at row r in column c to the maximum of the maximum sum ending at row r-1 in column c and the maximum sum ending at row r in column c-1 plus the value at row r in column c
Set the maximum sum to the maximum of the maximum sum and the maximum sum ending at row r in column c
Return the maximum sum
This algorithm has a time complexity of O(n^2), which is sufficient to solve this problem as N may be as large as 100.  
這個想法是跟踪每個位置結束的最大總和，然後在每個步驟中，考慮在前一個位置結束的最大總和和當前元素，並取兩者中的最大值。

要將此算法應用於二維數組，您可以執行以下操作：

遍歷數組中的每一列 c
將以 c 列結尾的最大總和設置為 0
遍歷數組中的每一行 r
將c列第r行結束的最大和設置為c列第r-1行結束的最大和和c-1列第r行結束的最大和加上c列第r行的值中的最大值
將最大和設置為最大和與第r行c列結束的最大和中的最大值
返回最大總和
該算法的時間複雜度為 O(n^2)，足以解決此問題，因為 N 可能大到 100。  
# 程式碼2
```python
def maximal_sub_rectangle(array):
    n = len(array)
    max_sum = 0
    for c in range(n):
        max_sum_ending_at_c = 0
        for r in range(n):
            max_sum_ending_at_c = max(max_sum_ending_at_c, max_sum_ending_at_c + array[r][c])
            max_sum = max(max_sum, max_sum_ending_at_c)
    return max_sum
```
# 結論
我用 ChatGPT 產生後直接交，有看懂一部分，但是有些部分沒有看懂，導致後面無法理解。
# 參考資料
https://ithelp.ithome.com.tw/articles/10213270  
https://blog.csdn.net/rg_lzm/article/details/96753220  
https://web.ntnu.edu.tw/~algo/MaximumSubarrayProblem.html
