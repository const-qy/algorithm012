### 使用二分查找，寻找一个半有序数组 [4, 5, 6, 7, 0, 1, 2] 中间无序的地方
+ 参考：https://leetcode-cn.com/problems/search-in-rotated-sorted-array/solution/duo-tu-yan-shi-33-sou-suo-xuan-zhuan-pai-xu-shu-zu/

> 查找最小的元素'0',最小元素左右两侧是有序的，找到后就可以使用常规的二分查找

查找最小值的过程如下:
1. nums[0]<=nums[max]说明整个数组是有序的，下标0就是最小值
2. 如果num[i]>nums[i+1]，不满足升序，说明mid+1就是最小值，退出查找
3. 如果中间值numd[mid]>=nums[0]说明数组左边是有序的，最小值应该在右边
4. 如果中间值nums[mid]<nums[0]说明数组左边是无序的，最小值应该在数组左边

```cpp
int findMin(vector<int>& nums){
	int begin = 0;
	int end = nums.size() - 1;
	//如果第一个值比最后一个值小，说明整个数组是有序的
	if (nums[begin] <= nums[end]) {
		return begin;
	}
	while (begin <= end) {
		int mid = begin + (end - begin) / 2;
		//前一个值比后一个值大，找到了旋转点
		if (mid<nums.size() - 1 && nums[mid]>nums[mid + 1]) {
			return mid + 1;
		}
		//中间点大于等于第一个元素，左半边是有序的，转去右边查找
		if (nums[mid] >= nums[0]) {
			begin = mid + 1;
			//左边是无序的，继续在左边查找	
		}
		else {
			end = mid - 1;
		}
	}
	return 0;
}
```
