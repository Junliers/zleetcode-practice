[[+Leetcode practice reporter]]
# 001 两数之和
给定一个整数数组 nums 和一个整数目标值 target，请你在该数组中找出 和为目标值 target  的那 两个 整数，并返回它们的数组下标。

你可以假设每种输入只会对应一个答案。但是，数组中同一个元素在答案里不能重复出现。

你可以按任意顺序返回答案。

链接：https://leetcode-cn.com/problems/two-sum

------------
## 代码1（T）：
```
/**

 * Note: The returned array must be malloced, assume caller calls free().

 */

int* twoSum(int* nums, int numsSize, int target, int* returnSize){

int i,j;
for(i=0;i<numsSize;i++)
{
	for(j=i+1;j<numsSize;j++)
	{
		if(nums[i]+nums[j]==target)
		{
			int *a=(int*)malloc(2*sizeof(int));
			a[0]=i;
			a[1]=j;
			*returnSize=2;
			return a;
		}
	}
}
return 0;  

}
```

## 代码2（F）：
```
int a[2000]={0};
int i,j,tem;
for(i=0;i<numsSize;i++)
{
	a[nums[i]+1000]++;
}
for(i=0;i<numsSize;i++)
{
	tem=target-nums[i];
	if(a[tem+1000]==1&&tem!=nums[i]||a[tem+1000]>1)
	{
		int *b=(int*)malloc(2*sizeof(int));
		b[0]=i;
		for(j=i+1;j<numsSize;j++)
		{
			if(nums[j]+nums[i]==target)
			break;
		}
		b[1]=j;
		*returnSize=2;
		return b;	
	}
}
return 0;

```
-----
## 题解1：
>本题遇到的困难主要是将*returnSize*误认为是返回数组，事实上是返回数组的大小

用暴力法ac了本题，但应该还有更好的解法

## 题解2：
>思路上是用哈希算法解，但不知道哪里出了问题，一直失败

mark一下目前遇到的问题：主要的问题开大数组直接对应的方式不能应对负数和超大数字的情况，这可以通过改变哈希算法来解决
