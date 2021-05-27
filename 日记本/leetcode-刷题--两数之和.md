给定一个整数数组和一个目标值，找出数组中和为目标值得两个数，你可以假设每个输入只对应一种答案，且同样的元素不能被重复利用。
示例：
```
给定 nums = [2, 7, 11, 15], target = 9
因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]
```
解题方法：
```
var twoSum = function(nums, target) {
       for(let i=0;i<nums.length;i++){
        let result=[]
	result.push(i)
	let newtarget = target-nums[i]
	let secondPlace = nums.indexOf(newtarget,i+1)
	if(secondPlace>0){
	  result.push(secondPlace)
	  return result
    }
 }
}
```
