# 数组中的逆序对

**题目**
在数组中的两个数字，如果前面一个数字大于后面的数字，则这两个数字组成一个逆序对。
输入一个数组,求出这个数组中的逆序对的总数P。并将P对1000000007取模的结果输出。 
即输出P%1000000007 

**测试地址**
[数组中的逆序对](https://www.nowcoder.com/practice/96bd6684e04a44eb80e6a68efc0ec6c5?tpId=13&tqId=11188&tPage=2&rp=2&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

## 解题思路

采用类似归并排序的思想完成该题，时间复杂度是o(NLgN),空间复杂度是o(N)
归并排序的思想是先分解成一个个小数组，然后在不断合并，我们在合并的时候就可以统计逆序对。
当两个长度为1的数组进行合并的时候，根据数组中的值的大小，就判断出有没有逆序对，然后将两个数组合并成一个。
因为我们统计了逆序对，所有为了避免重复统计，我们合并的时候 按照从小到大进行排序放入。
以此类推，直到合并长度为n / 2的数组。因为我们合并之前每个子数组都是从小到大，因此，我们在比较两个子数组存在逆序对的时候，也是从后面向前比较。
对于左边的子数组leftArray，其下标为leftPoint,其初始的下标为leftInit,对于右边的子数组rightArray，其下标为rightPoint，其初始的下标为rightInit。
如果`leftArray[leftPoint]` > `rightArray[rightPoint]`,那么便存在逆序对，逆序对的个数是rightPoint - rightInit + 1;

这样，就统计了全部的逆序对的个数。不过因为该题目的数据限制，我们需要对每一步继续的逆序对个数取模。