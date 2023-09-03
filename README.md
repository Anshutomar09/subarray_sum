# subarray_sum

class Solution {
public:
    int subarraySum(vector<int>& nums, int k) {
        int n=(int)nums.size();
        unordered_map<int,int>prev;//map having sum and count
        int count=0;
        int sum=0;//prefix sum
        for(int i=0;i<n;i++){
            sum+=nums[i];
            if(sum==k){
                count++;
            }
            if(prev.find(sum-k)!=prev.end())//if prefix sum-k is found in map
                count+=prev[sum-k]; //add its count in count
            prev[sum]++;//else update map
        }
        return count;
    }
};
