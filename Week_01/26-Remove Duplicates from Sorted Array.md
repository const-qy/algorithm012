

双指针(快慢指针)，思路：利用慢指针i和快指针j最少差1，慢的不会追上快的；
快指针j从第二个元素开始扫描直到最后一个元素，每次都与慢指针i指向的元素比较，相同则j++,慢指针不变；
不同则把j指针指向的元素复制到i指针的下一个位置。
```cpp
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
    int length = nums.size();
    if(length == 1) return 1;
    if(length == 0) return 0;
    int res=0;
     for(int i = 0, j = 1;j <= length-1;j++){
         if(nums[i]!=nums[j])
            nums[++i] = nums[j];
        res = i+1;
     }
    return res;
    } 
     
};
```
