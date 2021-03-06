# 数组中次数超过一半的数字

**题目**

数组中有一个数字出现的次数超过数组长度的一半，请找出这个数字。例如输入一个长度为9的数组{1,2,3,2,2,2,5,4,2}。
由于数字2在数组中出现了5次，超过数组长度的一半，因此输出2。如果不存在则输出0。

**测试地址**
[数组中次数超过一半的数字](https://www.nowcoder.com/practice/e8a1b01a2df14cb2b228b30ee6a92163?tpId=13&tqId=11181&tPage=2&rp=2&ru=/ta/coding-interviews&qru=/ta/coding-interviews/question-ranking)

## 解题思路

第一种，最容易想到的思路，时间复杂度o(N)，空间复杂度o(N)
建立一个HashMap，边遍历数组，边向map中放值，放值的原则如下：

1. map中key是数组中的值，value是数组中的值出现的次数。
2. 如果该值出现过，则次数加1，否则就记为新的key-value

最后，遍历一遍map，判断次数超过一半的数是哪个，直接输出

第二种，时间复杂度o(N)，空间复杂度o(1)
利用快速排序的`partition`方法的思想，改变数组的状态，设立一个分区的值，这里为第一个元素记为x，经过一次`partition`之后。
x之前的值都是小于x，x之后的值都是大于x，得到x的下标index,判断index是不是数组的中间值，因为有一个数超过数组的一半，那么经过分区之后，超过一半的数一定在数组的中间。
如果不是，那么如果index < middle 则说明所求的数字在后半段，如果大于，就是在前半段。
最后返回中间的那个值即可。

第三种，第一种的改进，时间复杂度o(N)，空间复杂度o(1)
因为该题只需要求得次数超过一半的数字，并不需要统计所有数字的出现次数，因此不需要用map来保存所有数字出现的次数。
只需要用一个res变量保存最终的结果，一个time变量保存次数。遍历一遍数组，即可出现结果，判断的标准如下：

1. 如果数组当前的数字等于res，则time++
2. 如果数组当前的数字不等于res,则time--;
3. 如果time == 0 ，则res = 数组当前的值，time = 1;

最后返回res，即可。

因为相同比不同的多，最后time一定大于0，而res就是存储的当前time大于0的那个value。