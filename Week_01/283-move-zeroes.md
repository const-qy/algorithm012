解法1 双指针（快慢指针），2 ms, 在所有 C++ 提交中击败了52.86%的用户,自己在做了“利用快慢指针移除数组中所有重复项”后独立做的，时间复杂度不是很好
```cpp
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int v_length = nums.size();
        
        for(int i = 0,j = 1;j<=v_length-1;j++){

          if(nums[i]==0&&nums[j]!=0){//
             swap(nums[i],nums[j]);
             i++;
          }
             
          if(nums[i]!=0) i++;   

        }
    }
};
```
解法2，双指针,先把所有的非零元素移动到数组前面，后边填充零--参考别人的
```cpp
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int v_length = nums.size();
        int lastNonzerofingat = 0;        
        for(int i=0;i<=v_length-1;i++){
            if(nums[i]!=0) 
           nums[lastNonzerofingat++] = nums[i];
        }
          
        for(int j = lastNonzerofingat;j<=v_length-1;j++){
             nums[j] = 0;   

        }
    }

        
    
};
```
解法3，参考别人的，当数组中0很多时，解法三时间复杂度更低
```cpp
class Solution{

public:
void moveZeroes(vector<int>& nums) {
    for (int lastNonZeroFoundAt = 0, cur = 0; cur < nums.size(); cur++) {
        if (nums[cur] != 0) {
            swap(nums[lastNonZeroFoundAt++], nums[cur]);
        }
    }
}
```

};
