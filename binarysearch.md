# peak element

``` c++
class Solution {
public:
/* O(n) time 
    int findPeakElement(vector<int>& nums) {
        if (nums.size()==1 || nums[0]>nums[1])
            return 0;
        else if (nums[nums.size()-1]>nums[nums.size()-2])
            return nums.size()-1;
        else {
            for (int i=1; i<nums.size()-1; i++) {
                if (nums[i]>nums[i-1] && nums[i]>nums[i+1])
                    return i;
            }
            return -1;
        }
    }
*/
    int findPeakElement(vector<int>& nums) {
        if (nums.size()==1)
            return 0;
        
        vector<int> numsCopy(nums.size());
        copy(nums.begin(), nums.end(), numsCopy.begin());
        nums.insert(nums.begin(), INT_MIN);
        nums.insert(nums.end(), INT_MIN);
        
        int nS = 1, nE = nums.size()-2, nM = -1;
        while (nS<nE) {
            nM = nS + (nE-nS)/2;
            //cout << nS << ", " << nE << ", " << nM << endl;
            if (nums[nM-1] < nums[nM] && nums[nM] > nums[nM+1])
                return (nM-1);
            else if (nums[nM] < nums[nM-1])
                nE = nM-1;
            else
                nS = nM+1;
        }
        return (nS-1);
    }
};
```

``` c++
```