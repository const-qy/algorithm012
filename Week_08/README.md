1.选择排序
```cpp
void SelectSort(vector<int>& nums) {
	int length = nums.size();
	for (int i = 0; i < length-1; i++) {
		int min_index = i;
		for (int j = i + 1; j < length; j++) {
			if (nums[j] < nums[min_index])
				min_index = j;

		}
		swap(nums[i],nums[min_index]);
	}
	return;
 }
```
2.插入排序
```cpp
void InsertSort(vector<int>& nums) {
	int length = nums.size();
	for (int i = 1; i < length; i++) {
		int preIndex = i - 1;
		int cur = nums[i];
		while (preIndex>=0&& nums[preIndex]>cur)
		{
			nums[preIndex + 1] = nums[preIndex];
			preIndex--;
		}
		nums[preIndex + 1] = cur;

	}

	return;
 }
 ```
3.冒泡排序
循环嵌套，每次查看相邻的元素，如果逆序则交换。（实际中基本不会使用）
```cpp
void BubbleSort(vector<int>&a) {
	int length = a.size();
	for (int i = 0; i < length; i++) {
		bool flag = false;
		for (int j = length - 1; j > i; j--) {
			if (a[j - 1] > a[j]) {//当前元素与前驱比较，若逆序，则交换
				swap(a[j-1],a[j]);
				flag = true;
			}
			
		}
		if (flag == false) {

			return;
		}

	}
	return;
}
```


4. 快速排序
数组取pivot标杆，小于pivot的放在左边，大于pivot的放右边，然后继续对左边的和右边的子数组进行快排，以达到整个数组有序。
```cpp
int random_partition(vector<int>& nums, int idx_l, int idx_r) {

	int random_pivot_index = rand() % (idx_r - idx_l + 1) + idx_l;
	int pivot = nums[random_pivot_index];
	swap(nums[random_pivot_index],nums[idx_r]);

	int i = idx_l - 1; //统计有多少个小于pivit的元素，类似于双指针思想（快慢指针）
	for (int j = idx_l; j < idx_r; j++) {
		if (nums[j] < pivot) {
			i++;
			swap(nums[j],nums[i]);
		}
	}
	int idx_pivot = i + 1;
	swap(nums[idx_pivot],nums[idx_r]);
	return idx_pivot;

}

void random_quicksort(vector<int>& nums,int idx_l,int idx_r) {
	if (idx_l < idx_r) {

		int pivot_index = random_partition(nums,idx_l,idx_r);
		random_quicksort(nums,idx_l, pivot_index -1);
		random_quicksort(nums, pivot_index +1,idx_r);
	}
}

int main() {
	
	vector<int> a = { 5,4,3,2,1,4,5,6 };
	int l = 0;
	int r = a.size() - 1;
	random_quicksort(a,l,r);
	for (int it : a) {
		cout<<it<<endl;
	}


	
	return 0;
}
```

5 归并排序

```cpp
void merge(vector<int>&nums, int left, int mid, int right) {
	vector<int> tmp(right - left + 1);
	int i = left, j = mid + 1, k = 0;
	while (i <= mid && j <= right) {
		tmp[k++] = nums[i] < nums[j] ? nums[i++] : nums[j++];
	}
	while (i <= mid)  tmp[k++] = nums[i++];
	while (j <= right) tmp[k++] = nums[j++];
	for (i = left, k = 0; i <= right;) nums[i++] = tmp[k++];
}
void  mergeSort(vector<int>& nums, int left, int right) {

	if (left >= right)  return;
		int mid = left + ((right - left)>>1);
		mergeSort(nums, left, mid);
		mergeSort(nums, mid + 1, right);
		merge(nums, left, mid, right);
	
	
}

int main() {
	
	vector<int> a = { 5,4,3,2,1,4,5,6 };
	int l = 0;
	int r = a.size() - 1;
	mergeSort(a,l,r);
	for (int it : a) {
		cout<<it<<endl;
	}


	
	return 0;
}
```
