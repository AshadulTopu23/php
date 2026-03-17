২০০টি DSA সমস্যা ও সমাধান (JavaScript এ)
সূচিপত্র
অ্যারে সম্পর্কিত সমস্যা (১-৩০)

স্ট্রিং সম্পর্কিত সমস্যা (৩১-৫০)

লিংকড লিস্ট (৫১-৬৫)

স্ট্যাক ও কিউ (৬৬-৮০)

ট্রি ও গ্রাফ (৮১-৯৫)

রিকার্শন ও ব্যাকট্র্যাকিং (৯৬-১১০)

ডায়নামিক প্রোগ্রামিং (১১১-১২৫)

সর্টিং ও সার্চিং (১২৬-১৪০)

ম্যাথ ও নাম্বার থিওরি (১৪১-১৫৫)

ম্যাট্রিক্স (১৫৬-১৭০)

হ্যাশিং (১৭১-১৮০)

বিট ম্যানিপুলেশন (১৮১-১৯০)

স্লাইডিং উইন্ডো (১৯১-২০০)

১. অ্যারে সম্পর্কিত সমস্যা (১-৩০)
সমস্যা ১: অ্যারে থেকে ডুপ্লিকেট এলিমেন্ট রিমুভ করা
javascript
function removeDuplicates(arr) {
    return [...new Set(arr)];
}

// উদাহরণ
console.log(removeDuplicates([1, 2, 2, 3, 4, 4, 5])); // [1, 2, 3, 4, 5]
সমস্যা ২: অ্যারে রিভার্স করা (বিল্ট-ইন ফাংশন ছাড়া)
javascript
function reverseArray(arr) {
    let left = 0;
    let right = arr.length - 1;
    
    while (left < right) {
        [arr[left], arr[right]] = [arr[right], arr[left]];
        left++;
        right--;
    }
    
    return arr;
}

// উদাহরণ
console.log(reverseArray([1, 2, 3, 4, 5])); // [5, 4, 3, 2, 1]
সমস্যা ৩: অ্যারের দ্বিতীয় বৃহত্তম এলিমেন্ট বের করা
javascript
function secondLargest(arr) {
    let largest = -Infinity;
    let secondLargest = -Infinity;
    
    for (let num of arr) {
        if (num > largest) {
            secondLargest = largest;
            largest = num;
        } else if (num > secondLargest && num !== largest) {
            secondLargest = num;
        }
    }
    
    return secondLargest;
}

// উদাহরণ
console.log(secondLargest([10, 5, 8, 20, 15])); // 15
সমস্যা ৪: অ্যারে rotate করা (K পজিশন ডানে)
javascript
function rotateRight(arr, k) {
    const n = arr.length;
    k = k % n;
    
    return [...arr.slice(n - k), ...arr.slice(0, n - k)];
}

// উদাহরণ
console.log(rotateRight([1, 2, 3, 4, 5], 2)); // [4, 5, 1, 2, 3]
সমস্যা ৫: Majority এলিমেন্ট বের করা (n/2 এর বেশি বার আসে)
javascript
function majorityElement(arr) {
    let candidate = null;
    let count = 0;
    
    // Boyer-Moore Voting Algorithm
    for (let num of arr) {
        if (count === 0) {
            candidate = num;
        }
        count += (num === candidate) ? 1 : -1;
    }
    
    return candidate;
}

// উদাহরণ
console.log(majorityElement([2, 2, 1, 1, 1, 2, 2])); // 2
সমস্যা ৬: দুটি সর্টেড অ্যারে মার্জ করা
javascript
function mergeSortedArrays(arr1, arr2) {
    const result = [];
    let i = 0, j = 0;
    
    while (i < arr1.length && j < arr2.length) {
        if (arr1[i] < arr2[j]) {
            result.push(arr1[i++]);
        } else {
            result.push(arr2[j++]);
        }
    }
    
    return [...result, ...arr1.slice(i), ...arr2.slice(j)];
}

// উদাহরণ
console.log(mergeSortedArrays([1, 3, 5, 7], [2, 4, 6, 8])); 
// [1, 2, 3, 4, 5, 6, 7, 8]
সমস্যা ৭: Missing Number বের করা (1 থেকে n পর্যন্ত)
javascript
function missingNumber(arr) {
    const n = arr.length + 1;
    const expectedSum = (n * (n + 1)) / 2;
    const actualSum = arr.reduce((sum, num) => sum + num, 0);
    
    return expectedSum - actualSum;
}

// উদাহরণ
console.log(missingNumber([1, 2, 4, 5, 6])); // 3
সমস্যা ৮: Product of Array Except Self
javascript
function productExceptSelf(arr) {
    const n = arr.length;
    const result = new Array(n).fill(1);
    
    // বাম পাশের product
    let leftProduct = 1;
    for (let i = 0; i < n; i++) {
        result[i] = leftProduct;
        leftProduct *= arr[i];
    }
    
    // ডান পাশের product
    let rightProduct = 1;
    for (let i = n - 1; i >= 0; i--) {
        result[i] *= rightProduct;
        rightProduct *= arr[i];
    }
    
    return result;
}

// উদাহরণ
console.log(productExceptSelf([1, 2, 3, 4])); // [24, 12, 8, 6]
সমস্যা ৯: Maximum Subarray Sum (Kadane's Algorithm)
javascript
function maxSubarraySum(arr) {
    let maxSoFar = arr[0];
    let maxEndingHere = arr[0];
    
    for (let i = 1; i < arr.length; i++) {
        maxEndingHere = Math.max(arr[i], maxEndingHere + arr[i]);
        maxSoFar = Math.max(maxSoFar, maxEndingHere);
    }
    
    return maxSoFar;
}

// উদাহরণ
console.log(maxSubarraySum([-2, 1, -3, 4, -1, 2, 1, -5, 4])); // 6
সমস্যা ১০: Contains Duplicate
javascript
function containsDuplicate(arr) {
    const seen = new Set();
    
    for (let num of arr) {
        if (seen.has(num)) return true;
        seen.add(num);
    }
    
    return false;
}

// উদাহরণ
console.log(containsDuplicate([1, 2, 3, 1])); // true
সমস্যা ১১: Two Sum
javascript
function twoSum(arr, target) {
    const map = new Map();
    
    for (let i = 0; i < arr.length; i++) {
        const complement = target - arr[i];
        
        if (map.has(complement)) {
            return [map.get(complement), i];
        }
        
        map.set(arr[i], i);
    }
    
    return [];
}

// উদাহরণ
console.log(twoSum([2, 7, 11, 15], 9)); // [0, 1]
সমস্যা ১২: Three Sum
javascript
function threeSum(arr) {
    const result = [];
    arr.sort((a, b) => a - b);
    
    for (let i = 0; i < arr.length - 2; i++) {
        if (i > 0 && arr[i] === arr[i - 1]) continue;
        
        let left = i + 1;
        let right = arr.length - 1;
        
        while (left < right) {
            const sum = arr[i] + arr[left] + arr[right];
            
            if (sum === 0) {
                result.push([arr[i], arr[left], arr[right]]);
                
                while (left < right && arr[left] === arr[left + 1]) left++;
                while (left < right && arr[right] === arr[right - 1]) right--;
                
                left++;
                right--;
            } else if (sum < 0) {
                left++;
            } else {
                right--;
            }
        }
    }
    
    return result;
}

// উদাহরণ
console.log(threeSum([-1, 0, 1, 2, -1, -4])); // [[-1,-1,2],[-1,0,1]]
সমস্যা ১৩: Best Time to Buy and Sell Stock
javascript
function maxProfit(prices) {
    let minPrice = Infinity;
    let maxProfit = 0;
    
    for (let price of prices) {
        if (price < minPrice) {
            minPrice = price;
        } else if (price - minPrice > maxProfit) {
            maxProfit = price - minPrice;
        }
    }
    
    return maxProfit;
}

// উদাহরণ
console.log(maxProfit([7, 1, 5, 3, 6, 4])); // 5
সমস্যা ১৪: Merge Intervals
javascript
function mergeIntervals(intervals) {
    if (!intervals.length) return [];
    
    intervals.sort((a, b) => a[0] - b[0]);
    
    const result = [intervals[0]];
    
    for (let i = 1; i < intervals.length; i++) {
        const last = result[result.length - 1];
        
        if (intervals[i][0] <= last[1]) {
            last[1] = Math.max(last[1], intervals[i][1]);
        } else {
            result.push(intervals[i]);
        }
    }
    
    return result;
}

// উদাহরণ
console.log(mergeIntervals([[1,3],[2,6],[8,10],[15,18]])); 
// [[1,6],[8,10],[15,18]]
সমস্যা ১৫: Find Minimum in Rotated Sorted Array
javascript
function findMin(arr) {
    let left = 0;
    let right = arr.length - 1;
    
    while (left < right) {
        const mid = Math.floor((left + right) / 2);
        
        if (arr[mid] > arr[right]) {
            left = mid + 1;
        } else {
            right = mid;
        }
    }
    
    return arr[left];
}

// উদাহরণ
console.log(findMin([4, 5, 6, 7, 0, 1, 2])); // 0
সমস্যা ১৬: Container With Most Water
javascript
function maxArea(height) {
    let left = 0;
    let right = height.length - 1;
    let maxArea = 0;
    
    while (left < right) {
        const area = Math.min(height[left], height[right]) * (right - left);
        maxArea = Math.max(maxArea, area);
        
        if (height[left] < height[right]) {
            left++;
        } else {
            right--;
        }
    }
    
    return maxArea;
}

// উদাহরণ
console.log(maxArea([1,8,6,2,5,4,8,3,7])); // 49
সমস্যা ১৭: Trapping Rain Water
javascript
function trap(height) {
    if (!height.length) return 0;
    
    let left = 0;
    let right = height.length - 1;
    let leftMax = 0, rightMax = 0;
    let water = 0;
    
    while (left < right) {
        if (height[left] < height[right]) {
            if (height[left] >= leftMax) {
                leftMax = height[left];
            } else {
                water += leftMax - height[left];
            }
            left++;
        } else {
            if (height[right] >= rightMax) {
                rightMax = height[right];
            } else {
                water += rightMax - height[right];
            }
            right--;
        }
    }
    
    return water;
}

// উদাহরণ
console.log(trap([0,1,0,2,1,0,1,3,2,1,2,1])); // 6
সমস্যা ১৮: Find All Numbers Disappeared in an Array
javascript
function findDisappearedNumbers(arr) {
    const n = arr.length;
    
    // মার্ক করা যেসব সংখ্যা আছে
    for (let i = 0; i < n; i++) {
        const index = Math.abs(arr[i]) - 1;
        if (arr[index] > 0) {
            arr[index] = -arr[index];
        }
    }
    
    // যে ইনডেক্সে positive মান আছে, সেগুলো missing
    const result = [];
    for (let i = 0; i < n; i++) {
        if (arr[i] > 0) {
            result.push(i + 1);
        }
    }
    
    return result;
}

// উদাহরণ
console.log(findDisappearedNumbers([4,3,2,7,8,2,3,1])); // [5,6]
সমস্যা ১৯: Move Zeroes to End
javascript
function moveZeroes(arr) {
    let lastNonZeroFoundAt = 0;
    
    // non-zero এলিমেন্ট সামনে এনে রাখা
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] !== 0) {
            [arr[lastNonZeroFoundAt], arr[i]] = [arr[i], arr[lastNonZeroFoundAt]];
            lastNonZeroFoundAt++;
        }
    }
    
    return arr;
}

// উদাহরণ
console.log(moveZeroes([0,1,0,3,12])); // [1,3,12,0,0]
সমস্যা ২০: Maximum Product Subarray
javascript
function maxProduct(arr) {
    let maxSoFar = arr[0];
    let minSoFar = arr[0];
    let result = arr[0];
    
    for (let i = 1; i < arr.length; i++) {
        const temp = maxSoFar;
        maxSoFar = Math.max(arr[i], maxSoFar * arr[i], minSoFar * arr[i]);
        minSoFar = Math.min(arr[i], temp * arr[i], minSoFar * arr[i]);
        result = Math.max(result, maxSoFar);
    }
    
    return result;
}

// উদাহরণ
console.log(maxProduct([2,3,-2,4])); // 6
সমস্যা ২১: Find the Duplicate Number
javascript
function findDuplicate(arr) {
    // Floyd's Tortoise and Hare (Cycle Detection)
    let slow = arr[0];
    let fast = arr[0];
    
    do {
        slow = arr[slow];
        fast = arr[arr[fast]];
    } while (slow !== fast);
    
    // cycle এর শুরু খুঁজে বের করা
    slow = arr[0];
    while (slow !== fast) {
        slow = arr[slow];
        fast = arr[fast];
    }
    
    return slow;
}

// উদাহরণ
console.log(findDuplicate([1,3,4,2,2])); // 2
সমস্যা ২২: Sort Colors (Dutch National Flag Problem)
javascript
function sortColors(arr) {
    let low = 0;
    let mid = 0;
    let high = arr.length - 1;
    
    while (mid <= high) {
        switch (arr[mid]) {
            case 0:
                [arr[low], arr[mid]] = [arr[mid], arr[low]];
                low++;
                mid++;
                break;
            case 1:
                mid++;
                break;
            case 2:
                [arr[mid], arr[high]] = [arr[high], arr[mid]];
                high--;
                break;
        }
    }
    
    return arr;
}

// উদাহরণ
console.log(sortColors([2,0,2,1,1,0])); // [0,0,1,1,2,2]
সমস্যা ২৩: Find First and Last Position of Element in Sorted Array
javascript
function searchRange(arr, target) {
    const result = [-1, -1];
    
    // প্রথম occurrence খুঁজে বের করা
    let left = 0;
    let right = arr.length - 1;
    
    while (left <= right) {
        const mid = Math.floor((left + right) / 2);
        
        if (arr[mid] === target) {
            result[0] = mid;
            right = mid - 1;
        } else if (arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    // শেষ occurrence খুঁজে বের করা
    left = 0;
    right = arr.length - 1;
    
    while (left <= right) {
        const mid = Math.floor((left + right) / 2);
        
        if (arr[mid] === target) {
            result[1] = mid;
            left = mid + 1;
        } else if (arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    return result;
}

// উদাহরণ
console.log(searchRange([5,7,7,8,8,10], 8)); // [3,4]
সমস্যা ২৪: Jump Game
javascript
function canJump(arr) {
    let maxReach = 0;
    
    for (let i = 0; i < arr.length; i++) {
        if (i > maxReach) return false;
        maxReach = Math.max(maxReach, i + arr[i]);
        if (maxReach >= arr.length - 1) return true;
    }
    
    return false;
}

// উদাহরণ
console.log(canJump([2,3,1,1,4])); // true
সমস্যা ২৫: Maximum Length of Subarray With Positive Product
javascript
function maxLengthPositiveProduct(arr) {
    let positive = 0, negative = 0, result = 0;
    
    for (let num of arr) {
        if (num > 0) {
            positive++;
            negative = negative > 0 ? negative + 1 : 0;
        } else if (num < 0) {
            const newPositive = negative > 0 ? negative + 1 : 0;
            const newNegative = positive + 1;
            positive = newPositive;
            negative = newNegative;
        } else {
            positive = 0;
            negative = 0;
        }
        
        result = Math.max(result, positive);
    }
    
    return result;
}

// উদাহরণ
console.log(maxLengthPositiveProduct([1,-2,-3,4])); // 4
সমস্যা ২৬: Subarray Sum Equals K
javascript
function subarraySum(arr, k) {
    const sumMap = new Map();
    sumMap.set(0, 1);
    
    let sum = 0;
    let count = 0;
    
    for (let num of arr) {
        sum += num;
        
        if (sumMap.has(sum - k)) {
            count += sumMap.get(sum - k);
        }
        
        sumMap.set(sum, (sumMap.get(sum) || 0) + 1);
    }
    
    return count;
}

// উদাহরণ
console.log(subarraySum([1,1,1], 2)); // 2
সমস্যা ২৭: Find Pivot Index
javascript
function pivotIndex(arr) {
    const totalSum = arr.reduce((sum, num) => sum + num, 0);
    let leftSum = 0;
    
    for (let i = 0; i < arr.length; i++) {
        if (leftSum === totalSum - leftSum - arr[i]) {
            return i;
        }
        leftSum += arr[i];
    }
    
    return -1;
}

// উদাহরণ
console.log(pivotIndex([1,7,3,6,5,6])); // 3
সমস্যা ২৮: Maximum Product of Three Numbers
javascript
function maximumProduct(arr) {
    arr.sort((a, b) => a - b);
    const n = arr.length;
    
    return Math.max(
        arr[n-1] * arr[n-2] * arr[n-3],
        arr[0] * arr[1] * arr[n-1]
    );
}

// উদাহরণ
console.log(maximumProduct([1,2,3,4])); // 24
সমস্যা ২৯: Find All Duplicates in an Array
javascript
function findDuplicates(arr) {
    const result = [];
    
    for (let i = 0; i < arr.length; i++) {
        const index = Math.abs(arr[i]) - 1;
        
        if (arr[index] < 0) {
            result.push(Math.abs(arr[i]));
        } else {
            arr[index] = -arr[index];
        }
    }
    
    return result;
}

// উদাহরণ
console.log(findDuplicates([4,3,2,7,8,2,3,1])); // [2,3]
সমস্যা ৩০: Next Permutation
javascript
function nextPermutation(arr) {
    const n = arr.length;
    let i = n - 2;
    
    // পিছন থেকে প্রথম ডিপ খুঁজে বের করা যেখানে arr[i] < arr[i+1]
    while (i >= 0 && arr[i] >= arr[i + 1]) {
        i--;
    }
    
    if (i >= 0) {
        let j = n - 1;
        // arr[i] এর চেয়ে বড় প্রথম এলিমেন্ট খুঁজে বের করা
        while (j >= 0 && arr[j] <= arr[i]) {
            j--;
        }
        
        // swap arr[i] and arr[j]
        [arr[i], arr[j]] = [arr[j], arr[i]];
    }
    
    // i+1 থেকে শেষ পর্যন্ত reverse করা
    let left = i + 1;
    let right = n - 1;
    
    while (left < right) {
        [arr[left], arr[right]] = [arr[right], arr[left]];
        left++;
        right--;
    }
    
    return arr;
}

// উদাহরণ
console.log(nextPermutation([1,2,3])); // [1,3,2]
২. স্ট্রিং সম্পর্কিত সমস্যা (৩১-৫০)
সমস্যা ৩১: Palindrome Check
javascript
function isPalindrome(str) {
    str = str.toLowerCase().replace(/[^a-z0-9]/g, '');
    return str === str.split('').reverse().join('');
}

// উদাহরণ
console.log(isPalindrome("A man, a plan, a canal: Panama")); // true
সমস্যা ৩২: Reverse String
javascript
function reverseString(str) {
    return str.split('').reverse().join('');
}

// In-place reversal (array হিসেবে)
function reverseStringInPlace(arr) {
    let left = 0;
    let right = arr.length - 1;
    
    while (left < right) {
        [arr[left], arr[right]] = [arr[right], arr[left]];
        left++;
        right--;
    }
    
    return arr;
}

// উদাহরণ
console.log(reverseString("hello")); // "olleh"
সমস্যা ৩৩: First Unique Character in a String
javascript
function firstUniqChar(str) {
    const count = {};
    
    for (let char of str) {
        count[char] = (count[char] || 0) + 1;
    }
    
    for (let i = 0; i < str.length; i++) {
        if (count[str[i]] === 1) {
            return i;
        }
    }
    
    return -1;
}

// উদাহরণ
console.log(firstUniqChar("leetcode")); // 0
সমস্যা ৩৪: Valid Anagram
javascript
function isAnagram(s, t) {
    if (s.length !== t.length) return false;
    
    const count = {};
    
    for (let i = 0; i < s.length; i++) {
        count[s[i]] = (count[s[i]] || 0) + 1;
        count[t[i]] = (count[t[i]] || 0) - 1;
    }
    
    return Object.values(count).every(val => val === 0);
}

// উদাহরণ
console.log(isAnagram("anagram", "nagaram")); // true
সমস্যা ৩৫: Longest Common Prefix
javascript
function longestCommonPrefix(strs) {
    if (!strs.length) return "";
    
    let prefix = strs[0];
    
    for (let i = 1; i < strs.length; i++) {
        while (strs[i].indexOf(prefix) !== 0) {
            prefix = prefix.slice(0, -1);
            if (!prefix) return "";
        }
    }
    
    return prefix;
}

// উদাহরণ
console.log(longestCommonPrefix(["flower","flow","flight"])); // "fl"
সমস্যা ৩৬: Count and Say
javascript
function countAndSay(n) {
    if (n === 1) return "1";
    
    let prev = countAndSay(n - 1);
    let result = "";
    let count = 1;
    
    for (let i = 0; i < prev.length; i++) {
        if (i + 1 < prev.length && prev[i] === prev[i + 1]) {
            count++;
        } else {
            result += count + prev[i];
            count = 1;
        }
    }
    
    return result;
}

// উদাহরণ
console.log(countAndSay(4)); // "1211"
সমস্যা ৩৭: String to Integer (atoi)
javascript
function myAtoi(str) {
    str = str.trim();
    if (!str) return 0;
    
    let sign = 1;
    let i = 0;
    
    if (str[0] === '+' || str[0] === '-') {
        sign = str[0] === '-' ? -1 : 1;
        i = 1;
    }
    
    let result = 0;
    while (i < str.length && /\d/.test(str[i])) {
        result = result * 10 + parseInt(str[i]);
        
        // overflow check
        if (result * sign > 2147483647) return 2147483647;
        if (result * sign < -2147483648) return -2147483648;
        
        i++;
    }
    
    return result * sign;
}

// উদাহরণ
console.log(myAtoi("   -42")); // -42
সমস্যা ৩৮: Valid Parentheses
javascript
function isValid(s) {
    const stack = [];
    const map = {
        ')': '(',
        '}': '{',
        ']': '['
    };
    
    for (let char of s) {
        if (char === '(' || char === '{' || char === '[') {
            stack.push(char);
        } else {
            if (stack.length === 0 || stack.pop() !== map[char]) {
                return false;
            }
        }
    }
    
    return stack.length === 0;
}

// উদাহরণ
console.log(isValid("()[]{}")); // true
console.log(isValid("([)]")); // false
সমস্যা ৩৯: Longest Palindromic Substring
javascript
function longestPalindrome(s) {
    if (s.length < 2) return s;
    
    let start = 0;
    let maxLength = 1;
    
    function expandAroundCenter(left, right) {
        while (left >= 0 && right < s.length && s[left] === s[right]) {
            left--;
            right++;
        }
        return right - left - 1;
    }
    
    for (let i = 0; i < s.length; i++) {
        const len1 = expandAroundCenter(i, i);
        const len2 = expandAroundCenter(i, i + 1);
        const len = Math.max(len1, len2);
        
        if (len > maxLength) {
            maxLength = len;
            start = i - Math.floor((len - 1) / 2);
        }
    }
    
    return s.substring(start, start + maxLength);
}

// উদাহরণ
console.log(longestPalindrome("babad")); // "bab" or "aba"
সমস্যা ৪০: Group Anagrams
javascript
function groupAnagrams(strs) {
    const map = {};
    
    for (let str of strs) {
        const sorted = str.split('').sort().join('');
        if (!map[sorted]) {
            map[sorted] = [];
        }
        map[sorted].push(str);
    }
    
    return Object.values(map);
}

// উদাহরণ
console.log(groupAnagrams(["eat","tea","tan","ate","nat","bat"]));
// [["eat","tea","ate"],["tan","nat"],["bat"]]
সমস্যা ৪১: Minimum Window Substring
javascript
function minWindow(s, t) {
    if (!s || !t) return "";
    
    const need = {};
    for (let char of t) {
        need[char] = (need[char] || 0) + 1;
    }
    
    const have = {};
    let left = 0;
    let minLen = Infinity;
    let minStart = 0;
    let required = Object.keys(need).length;
    let formed = 0;
    
    for (let right = 0; right < s.length; right++) {
        const char = s[right];
        have[char] = (have[char] || 0) + 1;
        
        if (need[char] && have[char] === need[char]) {
            formed++;
        }
        
        while (formed === required && left <= right) {
            if (right - left + 1 < minLen) {
                minLen = right - left + 1;
                minStart = left;
            }
            
            const leftChar = s[left];
            have[leftChar]--;
            
            if (need[leftChar] && have[leftChar] < need[leftChar]) {
                formed--;
            }
            
            left++;
        }
    }
    
    return minLen === Infinity ? "" : s.substring(minStart, minStart + minLen);
}

// উদাহরণ
console.log(minWindow("ADOBECODEBANC", "ABC")); // "BANC"
সমস্যা ৪২: Decode String
javascript
function decodeString(s) {
    const stack = [];
    let currentNum = 0;
    let currentStr = '';
    
    for (let char of s) {
        if (/\d/.test(char)) {
            currentNum = currentNum * 10 + parseInt(char);
        } else if (char === '[') {
            stack.push([currentStr, currentNum]);
            currentStr = '';
            currentNum = 0;
        } else if (char === ']') {
            const [prevStr, num] = stack.pop();
            currentStr = prevStr + currentStr.repeat(num);
        } else {
            currentStr += char;
        }
    }
    
    return currentStr;
}

// উদাহরণ
console.log(decodeString("3[a]2[bc]")); // "aaabcbc"
সমস্যা ৪৩: Longest Substring Without Repeating Characters
javascript
function lengthOfLongestSubstring(s) {
    const charMap = new Map();
    let left = 0;
    let maxLength = 0;
    
    for (let right = 0; right < s.length; right++) {
        const char = s[right];
        
        if (charMap.has(char) && charMap.get(char) >= left) {
            left = charMap.get(char) + 1;
        }
        
        charMap.set(char, right);
        maxLength = Math.max(maxLength, right - left + 1);
    }
    
    return maxLength;
}

// উদাহরণ
console.log(lengthOfLongestSubstring("abcabcbb")); // 3
সমস্যা ৪৪: Repeated DNA Sequences
javascript
function findRepeatedDnaSequences(s) {
    const seen = new Set();
    const result = new Set();
    
    for (let i = 0; i <= s.length - 10; i++) {
        const sequence = s.substring(i, i + 10);
        
        if (seen.has(sequence)) {
            result.add(sequence);
        } else {
            seen.add(sequence);
        }
    }
    
    return Array.from(result);
}

// উদাহরণ
console.log(findRepeatedDnaSequences("AAAAACCCCCAAAAACCCCCCAAAAAGGGTTT"));
সমস্যা ৪৫: Valid Palindrome II (একটি character delete করার সুযোগ)
javascript
function validPalindrome(s) {
    function isPalindromeRange(left, right) {
        while (left < right) {
            if (s[left] !== s[right]) return false;
            left++;
            right--;
        }
        return true;
    }
    
    let left = 0;
    let right = s.length - 1;
    
    while (left < right) {
        if (s[left] !== s[right]) {
            return isPalindromeRange(left + 1, right) || 
                   isPalindromeRange(left, right - 1);
        }
        left++;
        right--;
    }
    
    return true;
}

// উদাহরণ
console.log(validPalindrome("abca")); // true
সমস্যা ৪৬: String Compression
javascript
function compress(chars) {
    let write = 0;
    let read = 0;
    
    while (read < chars.length) {
        const char = chars[read];
        let count = 0;
        
        while (read < chars.length && chars[read] === char) {
            read++;
            count++;
        }
        
        chars[write++] = char;
        
        if (count > 1) {
            for (let digit of count.toString()) {
                chars[write++] = digit;
            }
        }
    }
    
    return write;
}

// উদাহরণ
const chars = ["a","a","b","b","c","c","c"];
console.log(compress(chars)); // 6
console.log(chars.slice(0, 6)); // ["a","2","b","2","c","3"]
সমস্যা ৪৭: Add Binary
javascript
function addBinary(a, b) {
    let result = '';
    let carry = 0;
    let i = a.length - 1;
    let j = b.length - 1;
    
    while (i >= 0 || j >= 0 || carry) {
        const sum = (parseInt(a[i] || 0) + parseInt(b[j] || 0) + carry);
        result = (sum % 2) + result;
        carry = Math.floor(sum / 2);
        i--;
        j--;
    }
    
    return result;
}

// উদাহরণ
console.log(addBinary("11", "1")); // "100"
সমস্যা ৪৮: Multiply Strings
javascript
function multiply(num1, num2) {
    if (num1 === "0" || num2 === "0") return "0";
    
    const result = new Array(num1.length + num2.length).fill(0);
    
    for (let i = num1.length - 1; i >= 0; i--) {
        for (let j = num2.length - 1; j >= 0; j--) {
            const mul = parseInt(num1[i]) * parseInt(num2[j]);
            const sum = mul + result[i + j + 1];
            
            result[i + j + 1] = sum % 10;
            result[i + j] += Math.floor(sum / 10);
        }
    }
    
    // leading zeros বাদ দেওয়া
    while (result[0] === 0) {
        result.shift();
    }
    
    return result.join('');
}

// উদাহরণ
console.log(multiply("123", "456")); // "56088"
সমস্যা ৪৯: Word Break
javascript
function wordBreak(s, wordDict) {
    const wordSet = new Set(wordDict);
    const dp = new Array(s.length + 1).fill(false);
    dp[0] = true;
    
    for (let i = 1; i <= s.length; i++) {
        for (let j = 0; j < i; j++) {
            if (dp[j] && wordSet.has(s.substring(j, i))) {
                dp[i] = true;
                break;
            }
        }
    }
    
    return dp[s.length];
}

// উদাহরণ
console.log(wordBreak("leetcode", ["leet","code"])); // true
সমস্যা ৫০: Basic Calculator II
javascript
function calculate(s) {
    const stack = [];
    let num = 0;
    let op = '+';
    s = s.replace(/\s/g, '');
    
    for (let i = 0; i < s.length; i++) {
        if (/\d/.test(s[i])) {
            num = num * 10 + parseInt(s[i]);
        }
        
        if (!/\d/.test(s[i]) || i === s.length - 1) {
            switch (op) {
                case '+':
                    stack.push(num);
                    break;
                case '-':
                    stack.push(-num);
                    break;
                case '*':
                    stack.push(stack.pop() * num);
                    break;
                case '/':
                    stack.push(Math.trunc(stack.pop() / num));
                    break;
            }
            op = s[i];
            num = 0;
        }
    }
    
    return stack.reduce((sum, num) => sum + num, 0);
}

// উদাহরণ
console.log(calculate("3+2*2")); // 7
৩. লিংকড লিস্ট (৫১-৬৫)
javascript
class ListNode {
    constructor(val = 0, next = null) {
        this.val = val;
        this.next = next;
    }
}

// লিংকড লিস্ট তৈরি করার helper function
function createLinkedList(arr) {
    if (!arr.length) return null;
    
    const head = new ListNode(arr[0]);
    let current = head;
    
    for (let i = 1; i < arr.length; i++) {
        current.next = new ListNode(arr[i]);
        current = current.next;
    }
    
    return head;
}

// লিংকড লিস্ট প্রিন্ট করার helper function
function printLinkedList(head) {
    const result = [];
    let current = head;
    
    while (current) {
        result.push(current.val);
        current = current.next;
    }
    
    console.log(result.join(' -> '));
}
সমস্যা ৫১: Reverse Linked List
javascript
function reverseList(head) {
    let prev = null;
    let current = head;
    
    while (current) {
        const next = current.next;
        current.next = prev;
        prev = current;
        current = next;
    }
    
    return prev;
}

// উদাহরণ
const head = createLinkedList([1,2,3,4,5]);
printLinkedList(reverseList(head)); // 5 -> 4 -> 3 -> 2 -> 1
সমস্যা ৫২: Detect Cycle in Linked List
javascript
function hasCycle(head) {
    if (!head) return false;
    
    let slow = head;
    let fast = head;
    
    while (fast && fast.next) {
        slow = slow.next;
        fast = fast.next.next;
        
        if (slow === fast) return true;
    }
    
    return false;
}
সমস্যা ৫৩: Merge Two Sorted Lists
javascript
function mergeTwoLists(l1, l2) {
    const dummy = new ListNode();
    let current = dummy;
    
    while (l1 && l2) {
        if (l1.val <= l2.val) {
            current.next = l1;
            l1 = l1.next;
        } else {
            current.next = l2;
            l2 = l2.next;
        }
        current = current.next;
    }
    
    current.next = l1 || l2;
    
    return dummy.next;
}

// উদাহরণ
const l1 = createLinkedList([1,2,4]);
const l2 = createLinkedList([1,3,4]);
printLinkedList(mergeTwoLists(l1, l2)); // 1 -> 1 -> 2 -> 3 -> 4 -> 4
সমস্যা ৫৪: Remove Nth Node From End of List
javascript
function removeNthFromEnd(head, n) {
    const dummy = new ListNode(0, head);
    let first = dummy;
    let second = dummy;
    
    // first pointer কে n+1 ধাপ এগিয়ে নেওয়া
    for (let i = 0; i <= n; i++) {
        first = first.next;
    }
    
    // যখন first শেষ হবে, second থাকবে delete করার node এর আগে
    while (first) {
        first = first.next;
        second = second.next;
    }
    
    // node delete করা
    second.next = second.next.next;
    
    return dummy.next;
}

// উদাহরণ
const head = createLinkedList([1,2,3,4,5]);
printLinkedList(removeNthFromEnd(head, 2)); // 1 -> 2 -> 3 -> 5
সমস্যা ৫৫: Middle of the Linked List
javascript
function middleNode(head) {
    let slow = head;
    let fast = head;
    
    while (fast && fast.next) {
        slow = slow.next;
        fast = fast.next.next;
    }
    
    return slow;
}

// উদাহরণ
const head = createLinkedList([1,2,3,4,5]);
console.log(middleNode(head).val); // 3
সমস্যা ৫৬: Palindrome Linked List
javascript
function isPalindromeList(head) {
    if (!head || !head.next) return true;
    
    // list এর মাঝখান খুঁজে বের করা
    let slow = head;
    let fast = head;
    
    while (fast && fast.next) {
        slow = slow.next;
        fast = fast.next.next;
    }
    
    // দ্বিতীয় half reverse করা
    let secondHalf = reverseList(slow);
    let firstHalf = head;
    
    // compare করা
    while (secondHalf) {
        if (firstHalf.val !== secondHalf.val) {
            return false;
        }
        firstHalf = firstHalf.next;
        secondHalf = secondHalf.next;
    }
    
    return true;
}

// উদাহরণ
const head = createLinkedList([1,2,2,1]);
console.log(isPalindromeList(head)); // true
সমস্যা ৫৭: Intersection of Two Linked Lists
javascript
function getIntersectionNode(headA, headB) {
    if (!headA || !headB) return null;
    
    let a = headA;
    let b = headB;
    
    while (a !== b) {
        a = a ? a.next : headB;
        b = b ? b.next : headA;
    }
    
    return a;
}
সমস্যা ৫৮: Add Two Numbers (Linked List)
javascript
function addTwoNumbers(l1, l2) {
    const dummy = new ListNode();
    let current = dummy;
    let carry = 0;
    
    while (l1 || l2 || carry) {
        const sum = (l1?.val || 0) + (l2?.val || 0) + carry;
        
        carry = Math.floor(sum / 10);
        current.next = new ListNode(sum % 10);
        current = current.next;
        
        l1 = l1?.next;
        l2 = l2?.next;
    }
    
    return dummy.next;
}

// উদাহরণ
const l1 = createLinkedList([2,4,3]);
const l2 = createLinkedList([5,6,4]);
printLinkedList(addTwoNumbers(l1, l2)); // 7 -> 0 -> 8
সমস্যা ৫৯: Remove Duplicates from Sorted List
javascript
function deleteDuplicates(head) {
    let current = head;
    
    while (current && current.next) {
        if (current.val === current.next.val) {
            current.next = current.next.next;
        } else {
            current = current.next;
        }
    }
    
    return head;
}

// উদাহরণ
const head = createLinkedList([1,1,2,3,3]);
printLinkedList(deleteDuplicates(head)); // 1 -> 2 -> 3
সমস্যা ৬০: Linked List Cycle II (Cycle শুরু হওয়া node)
javascript
function detectCycle(head) {
    if (!head) return null;
    
    let slow = head;
    let fast = head;
    let hasCycle = false;
    
    while (fast && fast.next) {
        slow = slow.next;
        fast = fast.next.next;
        
        if (slow === fast) {
            hasCycle = true;
            break;
        }
    }
    
    if (!hasCycle) return null;
    
    slow = head;
    while (slow !== fast) {
        slow = slow.next;
        fast = fast.next;
    }
    
    return slow;
}
সমস্যা ৬১: Rotate List
javascript
function rotateRightList(head, k) {
    if (!head || !head.next || k === 0) return head;
    
    // length বের করা
    let length = 1;
    let tail = head;
    
    while (tail.next) {
        tail = tail.next;
        length++;
    }
    
    k = k % length;
    if (k === 0) return head;
    
    // new head এর আগের node খুঁজে বের করা
    let newTail = head;
    for (let i = 0; i < length - k - 1; i++) {
        newTail = newTail.next;
    }
    
    const newHead = newTail.next;
    newTail.next = null;
    tail.next = head;
    
    return newHead;
}

// উদাহরণ
const head = createLinkedList([1,2,3,4,5]);
printLinkedList(rotateRightList(head, 2)); // 4 -> 5 -> 1 -> 2 -> 3
সমস্যা ৬২: Partition List
javascript
function partition(head, x) {
    const beforeHead = new ListNode(0);
    const afterHead = new ListNode(0);
    let before = beforeHead;
    let after = afterHead;
    
    while (head) {
        if (head.val < x) {
            before.next = head;
            before = before.next;
        } else {
            after.next = head;
            after = after.next;
        }
        head = head.next;
    }
    
    after.next = null;
    before.next = afterHead.next;
    
    return beforeHead.next;
}

// উদাহরণ
const head = createLinkedList([1,4,3,2,5,2]);
printLinkedList(partition(head, 3)); // 1 -> 2 -> 2 -> 4 -> 3 -> 5
সমস্যা ৬৩: Copy List with Random Pointer
javascript
class Node {
    constructor(val, next = null, random = null) {
        this.val = val;
        this.next = next;
        this.random = random;
    }
}

function copyRandomList(head) {
    if (!head) return null;
    
    // প্রথম পাস: প্রতিটি node এর পাশে তার copy বসানো
    let current = head;
    while (current) {
        const copy = new Node(current.val);
        copy.next = current.next;
        current.next = copy;
        current = copy.next;
    }
    
    // দ্বিতীয় পাস: random pointers কপি করা
    current = head;
    while (current) {
        if (current.random) {
            current.next.random = current.random.next;
        }
        current = current.next.next;
    }
    
    // তৃতীয় পাস: original এবং copy আলাদা করা
    current = head;
    const newHead = head.next;
    
    while (current) {
        const copy = current.next;
        current.next = copy.next;
        current = current.next;
        copy.next = current ? current.next : null;
    }
    
    return newHead;
}
সমস্যা ৬৪: Sort List (Merge Sort)
javascript
function sortList(head) {
    if (!head || !head.next) return head;
    
    // list এর মাঝখান খুঁজে বের করা
    let slow = head;
    let fast = head;
    let prev = null;
    
    while (fast && fast.next) {
        prev = slow;
        slow = slow.next;
        fast = fast.next.next;
    }
    
    prev.next = null; // দুই ভাগে ভাগ করা
    
    const left = sortList(head);
    const right = sortList(slow);
    
    return mergeTwoLists(left, right);
}

// উদাহরণ
const head = createLinkedList([4,2,1,3]);
printLinkedList(sortList(head)); // 1 -> 2 -> 3 -> 4
সমস্যা ৬৫: Reorder List
javascript
function reorderList(head) {
    if (!head || !head.next) return;
    
    // list এর মাঝখান খুঁজে বের করা
    let slow = head;
    let fast = head;
    
    while (fast && fast.next) {
        slow = slow.next;
        fast = fast.next.next;
    }
    
    // দ্বিতীয় half reverse করা
    let second = reverseList(slow.next);
    slow.next = null; // দুই ভাগে ভাগ করা
    
    // interleave করা
    let first = head;
    while (second) {
        const temp1 = first.next;
        const temp2 = second.next;
        
        first.next = second;
        second.next = temp1;
        
        first = temp1;
        second = temp2;
    }
}

// উদাহরণ
const head = createLinkedList([1,2,3,4]);
reorderList(head);
printLinkedList(head); // 1 -> 4 -> 2 -> 3
৪. স্ট্যাক ও কিউ (৬৬-৮০)
সমস্যা ৬৬: Implement Stack using Arrays
javascript
class Stack {
    constructor() {
        this.items = [];
    }
    
    push(item) {
        this.items.push(item);
    }
    
    pop() {
        return this.items.pop();
    }
    
    peek() {
        return this.items[this.items.length - 1];
    }
    
    isEmpty() {
        return this.items.length === 0;
    }
    
    size() {
        return this.items.length;
    }
}

// উদাহরণ
const stack = new Stack();
stack.push(1);
stack.push(2);
stack.push(3);
console.log(stack.pop()); // 3
console.log(stack.peek()); // 2
সমস্যা ৬৭: Implement Queue using Arrays
javascript
class Queue {
    constructor() {
        this.items = [];
    }
    
    enqueue(item) {
        this.items.push(item);
    }
    
    dequeue() {
        return this.items.shift();
    }
    
    front() {
        return this.items[0];
    }
    
    isEmpty() {
        return this.items.length === 0;
    }
    
    size() {
        return this.items.length;
    }
}

// উদাহরণ
const queue = new Queue();
queue.enqueue(1);
queue.enqueue(2);
queue.enqueue(3);
console.log(queue.dequeue()); // 1
console.log(queue.front()); // 2
সমস্যা ৬৮: Implement Stack using Queues
javascript
class StackUsingQueues {
    constructor() {
        this.q1 = [];
        this.q2 = [];
    }
    
    push(x) {
        this.q2.push(x);
        
        while (this.q1.length) {
            this.q2.push(this.q1.shift());
        }
        
        [this.q1, this.q2] = [this.q2, this.q1];
    }
    
    pop() {
        return this.q1.shift();
    }
    
    top() {
        return this.q1[0];
    }
    
    empty() {
        return this.q1.length === 0;
    }
}
সমস্যা ৬৯: Implement Queue using Stacks
javascript
class QueueUsingStacks {
    constructor() {
        this.stack1 = [];
        this.stack2 = [];
    }
    
    enqueue(x) {
        this.stack1.push(x);
    }
    
    dequeue() {
        if (this.stack2.length === 0) {
            while (this.stack1.length) {
                this.stack2.push(this.stack1.pop());
            }
        }
        
        return this.stack2.pop();
    }
    
    peek() {
        if (this.stack2.length === 0) {
            while (this.stack1.length) {
                this.stack2.push(this.stack1.pop());
            }
        }
        
        return this.stack2[this.stack2.length - 1];
    }
    
    empty() {
        return this.stack1.length === 0 && this.stack2.length === 0;
    }
}
সমস্যা ৭০: Min Stack
javascript
class MinStack {
    constructor() {
        this.stack = [];
        this.minStack = [];
    }
    
    push(val) {
        this.stack.push(val);
        
        if (this.minStack.length === 0 || val <= this.getMin()) {
            this.minStack.push(val);
        }
    }
    
    pop() {
        const val = this.stack.pop();
        
        if (val === this.getMin()) {
            this.minStack.pop();
        }
    }
    
    top() {
        return this.stack[this.stack.length - 1];
    }
    
    getMin() {
        return this.minStack[this.minStack.length - 1];
    }
}

// উদাহরণ
const minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
console.log(minStack.getMin()); // -3
minStack.pop();
console.log(minStack.top()); // 0
console.log(minStack.getMin()); // -2
সমস্যা ৭১: Valid Parentheses (Stack)
javascript
function isValidParentheses(s) {
    const stack = [];
    const map = {
        ')': '(',
        '}': '{',
        ']': '['
    };
    
    for (let char of s) {
        if (char === '(' || char === '{' || char === '[') {
            stack.push(char);
        } else {
            if (stack.length === 0 || stack.pop() !== map[char]) {
                return false;
            }
        }
    }
    
    return stack.length === 0;
}
সমস্যা ৭২: Next Greater Element
javascript
function nextGreaterElement(arr) {
    const result = new Array(arr.length).fill(-1);
    const stack = [];
    
    for (let i = 0; i < arr.length; i++) {
        while (stack.length && arr[i] > arr[stack[stack.length - 1]]) {
            const index = stack.pop();
            result[index] = arr[i];
        }
        stack.push(i);
    }
    
    return result;
}

// উদাহরণ
console.log(nextGreaterElement([4, 5, 2, 25])); // [5, 25, 25, -1]
সমস্যা ৭৩: Daily Temperatures
javascript
function dailyTemperatures(temps) {
    const result = new Array(temps.length).fill(0);
    const stack = [];
    
    for (let i = 0; i < temps.length; i++) {
        while (stack.length && temps[i] > temps[stack[stack.length - 1]]) {
            const prevIndex = stack.pop();
            result[prevIndex] = i - prevIndex;
        }
        stack.push(i);
    }
    
    return result;
}

// উদাহরণ
console.log(dailyTemperatures([73,74,75,71,69,72,76,73])); 
// [1,1,4,2,1,1,0,0]
সমস্যা ৭৪: Evaluate Reverse Polish Notation
javascript
function evalRPN(tokens) {
    const stack = [];
    
    for (let token of tokens) {
        if (['+', '-', '*', '/'].includes(token)) {
            const b = stack.pop();
            const a = stack.pop();
            
            switch (token) {
                case '+':
                    stack.push(a + b);
                    break;
                case '-':
                    stack.push(a - b);
                    break;
                case '*':
                    stack.push(a * b);
                    break;
                case '/':
                    stack.push(Math.trunc(a / b));
                    break;
            }
        } else {
            stack.push(parseInt(token));
        }
    }
    
    return stack.pop();
}

// উদাহরণ
console.log(evalRPN(["2","1","+","3","*"])); // 9
সমস্যা ৭৫: Backspace String Compare
javascript
function backspaceCompare(s, t) {
    function buildString(str) {
        const stack = [];
        
        for (let char of str) {
            if (char === '#') {
                stack.pop();
            } else {
                stack.push(char);
            }
        }
        
        return stack.join('');
    }
    
    return buildString(s) === buildString(t);
}

// উদাহরণ
console.log(backspaceCompare("ab#c", "ad#c")); // true
সমস্যা ৭৬: Asteroid Collision
javascript
function asteroidCollision(asteroids) {
    const stack = [];
    
    for (let ast of asteroids) {
        let exploded = false;
        
        while (stack.length && ast < 0 && stack[stack.length - 1] > 0) {
            if (Math.abs(ast) > stack[stack.length - 1]) {
                stack.pop();
                continue;
            } else if (Math.abs(ast) === stack[stack.length - 1]) {
                stack.pop();
                exploded = true;
                break;
            } else {
                exploded = true;
                break;
            }
        }
        
        if (!exploded) {
            stack.push(ast);
        }
    }
    
    return stack;
}

// উদাহরণ
console.log(asteroidCollision([5,10,-5])); // [5,10]
সমস্যা ৭৭: Simplify Path
javascript
function simplifyPath(path) {
    const stack = [];
    const parts = path.split('/');
    
    for (let part of parts) {
        if (part === '' || part === '.') {
            continue;
        } else if (part === '..') {
            stack.pop();
        } else {
            stack.push(part);
        }
    }
    
    return '/' + stack.join('/');
}

// উদাহরণ
console.log(simplifyPath("/home//foo/")); // "/home/foo"
console.log(simplifyPath("/a/./b/../../c/")); // "/c"
সমস্যা ৭৮: Remove K Digits
javascript
function removeKdigits(num, k) {
    const stack = [];
    
    for (let digit of num) {
        while (stack.length && k > 0 && stack[stack.length - 1] > digit) {
            stack.pop();
            k--;
        }
        stack.push(digit);
    }
    
    // যদি এখনও k বাকি থাকে, তাহলে শেষ থেকে remove করা
    while (k > 0) {
        stack.pop();
        k--;
    }
    
    // leading zeros বাদ দেওয়া
    const result = stack.join('').replace(/^0+/, '');
    
    return result || "0";
}

// উদাহরণ
console.log(removeKdigits("1432219", 3)); // "1219"
সমস্যা ৭৯: Largest Rectangle in Histogram
javascript
function largestRectangleArea(heights) {
    const stack = [];
    let maxArea = 0;
    let i = 0;
    
    while (i < heights.length) {
        if (stack.length === 0 || heights[i] >= heights[stack[stack.length - 1]]) {
            stack.push(i);
            i++;
        } else {
            const height = heights[stack.pop()];
            const width = stack.length === 0 ? i : i - stack[stack.length - 1] - 1;
            maxArea = Math.max(maxArea, height * width);
        }
    }
    
    while (stack.length) {
        const height = heights[stack.pop()];
        const width = stack.length === 0 ? i : i - stack[stack.length - 1] - 1;
        maxArea = Math.max(maxArea, height * width);
    }
    
    return maxArea;
}

// উদাহরণ
console.log(largestRectangleArea([2,1,5,6,2,3])); // 10
সমস্যা ৮০: Sliding Window Maximum
javascript
function maxSlidingWindow(nums, k) {
    if (!nums.length || k === 0) return [];
    
    const result = [];
    const deque = []; // indices
    
    for (let i = 0; i < nums.length; i++) {
        // window এর বাইরে চলে গেলে remove
        while (deque.length && deque[0] < i - k + 1) {
            deque.shift();
        }
        
        // ছোট মান গুলো remove করা
        while (deque.length && nums[deque[deque.length - 1]] < nums[i]) {
            deque.pop();
        }
        
        deque.push(i);
        
        // result এ যোগ করা
        if (i >= k - 1) {
            result.push(nums[deque[0]]);
        }
    }
    
    return result;
}

// উদাহরণ
console.log(maxSlidingWindow([1,3,-1,-3,5,3,6,7], 3)); // [3,3,5,5,6,7]
৫. ট্রি ও গ্রাফ (৮১-৯৫)
javascript
class TreeNode {
    constructor(val = 0, left = null, right = null) {
        this.val = val;
        this.left = left;
        this.right = right;
    }
}
সমস্যা ৮১: Binary Tree Inorder Traversal
javascript
function inorderTraversal(root) {
    const result = [];
    
    function inorder(node) {
        if (!node) return;
        
        inorder(node.left);
        result.push(node.val);
        inorder(node.right);
    }
    
    inorder(root);
    return result;
}

// উদাহরণ
const root = new TreeNode(1);
root.right = new TreeNode(2);
root.right.left = new TreeNode(3);
console.log(inorderTraversal(root)); // [1,3,2]
সমস্যা ৮২: Binary Tree Preorder Traversal
javascript
function preorderTraversal(root) {
    const result = [];
    
    function preorder(node) {
        if (!node) return;
        
        result.push(node.val);
        preorder(node.left);
        preorder(node.right);
    }
    
    preorder(root);
    return result;
}
সমস্যা ৮৩: Binary Tree Postorder Traversal
javascript
function postorderTraversal(root) {
    const result = [];
    
    function postorder(node) {
        if (!node) return;
        
        postorder(node.left);
        postorder(node.right);
        result.push(node.val);
    }
    
    postorder(root);
    return result;
}
সমস্যা ৮৪: Level Order Traversal (BFS)
javascript
function levelOrder(root) {
    if (!root) return [];
    
    const result = [];
    const queue = [root];
    
    while (queue.length) {
        const level = [];
        const levelSize = queue.length;
        
        for (let i = 0; i < levelSize; i++) {
            const node = queue.shift();
            level.push(node.val);
            
            if (node.left) queue.push(node.left);
            if (node.right) queue.push(node.right);
        }
        
        result.push(level);
    }
    
    return result;
}
সমস্যা ৮৫: Maximum Depth of Binary Tree
javascript
function maxDepth(root) {
    if (!root) return 0;
    
    return 1 + Math.max(maxDepth(root.left), maxDepth(root.right));
}

// উদাহরণ
const root = new TreeNode(3);
root.left = new TreeNode(9);
root.right = new TreeNode(20);
root.right.left = new TreeNode(15);
root.right.right = new TreeNode(7);
console.log(maxDepth(root)); // 3
সমস্যা ৮৬: Validate Binary Search Tree
javascript
function isValidBST(root) {
    function validate(node, min, max) {
        if (!node) return true;
        
        if ((min !== null && node.val <= min) || 
            (max !== null && node.val >= max)) {
            return false;
        }
        
        return validate(node.left, min, node.val) && 
               validate(node.right, node.val, max);
    }
    
    return validate(root, null, null);
}
সমস্যা ৮৭: Symmetric Tree
javascript
function isSymmetric(root) {
    if (!root) return true;
    
    function isMirror(left, right) {
        if (!left && !right) return true;
        if (!left || !right) return false;
        
        return (left.val === right.val) &&
               isMirror(left.left, right.right) &&
               isMirror(left.right, right.left);
    }
    
    return isMirror(root.left, root.right);
}
সমস্যা ৮৮: Binary Tree Level Order Traversal II (Bottom-up)
javascript
function levelOrderBottom(root) {
    if (!root) return [];
    
    const result = [];
    const queue = [root];
    
    while (queue.length) {
        const level = [];
        const levelSize = queue.length;
        
        for (let i = 0; i < levelSize; i++) {
            const node = queue.shift();
            level.push(node.val);
            
            if (node.left) queue.push(node.left);
            if (node.right) queue.push(node.right);
        }
        
        result.unshift(level);
    }
    
    return result;
}
সমস্যা ৮৯: Convert Sorted Array to Binary Search Tree
javascript
function sortedArrayToBST(nums) {
    function buildBST(left, right) {
        if (left > right) return null;
        
        const mid = Math.floor((left + right) / 2);
        const node = new TreeNode(nums[mid]);
        
        node.left = buildBST(left, mid - 1);
        node.right = buildBST(mid + 1, right);
        
        return node;
    }
    
    return buildBST(0, nums.length - 1);
}
সমস্যা ৯০: Path Sum
javascript
function hasPathSum(root, sum) {
    if (!root) return false;
    
    if (!root.left && !root.right) {
        return sum === root.val;
    }
    
    return hasPathSum(root.left, sum - root.val) ||
           hasPathSum(root.right, sum - root.val);
}
সমস্যা ৯১: Lowest Common Ancestor of BST
javascript
function lowestCommonAncestor(root, p, q) {
    if (!root) return null;
    
    if (p.val < root.val && q.val < root.val) {
        return lowestCommonAncestor(root.left, p, q);
    }
    
    if (p.val > root.val && q.val > root.val) {
        return lowestCommonAncestor(root.right, p, q);
    }
    
    return root;
}
সমস্যা ৯২: Binary Tree Right Side View
javascript
function rightSideView(root) {
    if (!root) return [];
    
    const result = [];
    const queue = [root];
    
    while (queue.length) {
        const levelSize = queue.length;
        
        for (let i = 0; i < levelSize; i++) {
            const node = queue.shift();
            
            if (i === levelSize - 1) {
                result.push(node.val);
            }
            
            if (node.left) queue.push(node.left);
            if (node.right) queue.push(node.right);
        }
    }
    
    return result;
}
সমস্যা ৯৩: Count Complete Tree Nodes
javascript
function countNodes(root) {
    if (!root) return 0;
    
    function getLeftHeight(node) {
        let height = 0;
        while (node) {
            height++;
            node = node.left;
        }
        return height;
    }
    
    function getRightHeight(node) {
        let height = 0;
        while (node) {
            height++;
            node = node.right;
        }
        return height;
    }
    
    const leftHeight = getLeftHeight(root);
    const rightHeight = getRightHeight(root);
    
    if (leftHeight === rightHeight) {
        return Math.pow(2, leftHeight) - 1;
    }
    
    return 1 + countNodes(root.left) + countNodes(root.right);
}
সমস্যা ৯৪: Binary Tree Zigzag Level Order Traversal
javascript
function zigzagLevelOrder(root) {
    if (!root) return [];
    
    const result = [];
    const queue = [root];
    let leftToRight = true;
    
    while (queue.length) {
        const level = [];
        const levelSize = queue.length;
        
        for (let i = 0; i < levelSize; i++) {
            const node = queue.shift();
            
            if (leftToRight) {
                level.push(node.val);
            } else {
                level.unshift(node.val);
            }
            
            if (node.left) queue.push(node.left);
            if (node.right) queue.push(node.right);
        }
        
        result.push(level);
        leftToRight = !leftToRight;
    }
    
    return result;
}
সমস্যা ৯৫: Serialize and Deserialize Binary Tree
javascript
class Codec {
    serialize(root) {
        if (!root) return "null";
        
        const left = this.serialize(root.left);
        const right = this.serialize(root.right);
        
        return `${root.val},${left},${right}`;
    }
    
    deserialize(data) {
        const nodes = data.split(',');
        
        function buildTree() {
            const val = nodes.shift();
            
            if (val === "null") return null;
            
            const node = new TreeNode(parseInt(val));
            node.left = buildTree();
            node.right = buildTree();
            
            return node;
        }
        
        return buildTree();
    }
}
৬. রিকার্শন ও ব্যাকট্র্যাকিং (৯৬-১১০)
সমস্যা ৯৬: Factorial using Recursion
javascript
function factorial(n) {
    if (n <= 1) return 1;
    return n * factorial(n - 1);
}

// উদাহরণ
console.log(factorial(5)); // 120
সমস্যা ৯৭: Fibonacci using Recursion
javascript
function fibonacci(n) {
    if (n <= 1) return n;
    return fibonacci(n - 1) + fibonacci(n - 2);
}

// উদাহরণ
console.log(fibonacci(6)); // 8
সমস্যা ৯৮: Power of Number using Recursion
javascript
function power(x, n) {
    if (n === 0) return 1;
    if (n < 0) return 1 / power(x, -n);
    
    const half = power(x, Math.floor(n / 2));
    
    if (n % 2 === 0) {
        return half * half;
    } else {
        return x * half * half;
    }
}

// উদাহরণ
console.log(power(2, 10)); // 1024
সমস্যা ৯৯: Tower of Hanoi
javascript
function towerOfHanoi(n, from, to, aux) {
    if (n === 1) {
        console.log(`Move disk 1 from ${from} to ${to}`);
        return;
    }
    
    towerOfHanoi(n - 1, from, aux, to);
    console.log(`Move disk ${n} from ${from} to ${to}`);
    towerOfHanoi(n - 1, aux, to, from);
}

// উদাহরণ
towerOfHanoi(3, 'A', 'C', 'B');
সমস্যা ১০০: Generate All Subsets (Power Set)
javascript
function subsets(nums) {
    const result = [];
    
    function backtrack(start, current) {
        result.push([...current]);
        
        for (let i = start; i < nums.length; i++) {
            current.push(nums[i]);
            backtrack(i + 1, current);
            current.pop();
        }
    }
    
    backtrack(0, []);
    return result;
}

// উদাহরণ
console.log(subsets([1,2,3]));
সমস্যা ১০১: Generate All Permutations
javascript
function permute(nums) {
    const result = [];
    
    function backtrack(start) {
        if (start === nums.length) {
            result.push([...nums]);
            return;
        }
        
        for (let i = start; i < nums.length; i++) {
            [nums[start], nums[i]] = [nums[i], nums[start]];
            backtrack(start + 1);
            [nums[start], nums[i]] = [nums[i], nums[start]];
        }
    }
    
    backtrack(0);
    return result;
}

// উদাহরণ
console.log(permute([1,2,3]));
সমস্যা ১০২: Combination Sum
javascript
function combinationSum(candidates, target) {
    const result = [];
    
    function backtrack(start, remaining, current) {
        if (remaining < 0) return;
        if (remaining === 0) {
            result.push([...current]);
            return;
        }
        
        for (let i = start; i < candidates.length; i++) {
            current.push(candidates[i]);
            backtrack(i, remaining - candidates[i], current);
            current.pop();
        }
    }
    
    backtrack(0, target, []);
    return result;
}

// উদাহরণ
console.log(combinationSum([2,3,6,7], 7));
সমস্যা ১০৩: N-Queens Problem
javascript
function solveNQueens(n) {
    const result = [];
    const board = Array(n).fill().map(() => Array(n).fill('.'));
    
    function isSafe(row, col) {
        // same column check
        for (let i = 0; i < row; i++) {
            if (board[i][col] === 'Q') return false;
        }
        
        // upper left diagonal
        for (let i = row - 1, j = col - 1; i >= 0 && j >= 0; i--, j--) {
            if (board[i][j] === 'Q') return false;
        }
        
        // upper right diagonal
        for (let i = row - 1, j = col + 1; i >= 0 && j < n; i--, j++) {
            if (board[i][j] === 'Q') return false;
        }
        
        return true;
    }
    
    function backtrack(row) {
        if (row === n) {
            result.push(board.map(row => row.join('')));
            return;
        }
        
        for (let col = 0; col < n; col++) {
            if (isSafe(row, col)) {
                board[row][col] = 'Q';
                backtrack(row + 1);
                board[row][col] = '.';
            }
        }
    }
    
    backtrack(0);
    return result;
}

// উদাহরণ
console.log(solveNQueens(4));

৬. রিকার্শন ও ব্যাকট্র্যাকিং (৯৬-১১০) - continued
সমস্যা ১০৪: Sudoku Solver (continued)
javascript
function solveSudoku(board) {
    function isValid(row, col, num) {
        // row check
        for (let j = 0; j < 9; j++) {
            if (board[row][j] === num) return false;
        }
        
        // column check
        for (let i = 0; i < 9; i++) {
            if (board[i][col] === num) return false;
        }
        
        // 3x3 box check
        const boxRow = Math.floor(row / 3) * 3;
        const boxCol = Math.floor(col / 3) * 3;
        
        for (let i = 0; i < 3; i++) {
            for (let j = 0; j < 3; j++) {
                if (board[boxRow + i][boxCol + j] === num) return false;
            }
        }
        
        return true;
    }
    
    function solve() {
        for (let i = 0; i < 9; i++) {
            for (let j = 0; j < 9; j++) {
                if (board[i][j] === '.') {
                    for (let num = 1; num <= 9; num++) {
                        const char = num.toString();
                        if (isValid(i, j, char)) {
                            board[i][j] = char;
                            
                            if (solve()) {
                                return true;
                            }
                            
                            board[i][j] = '.';
                        }
                    }
                    return false;
                }
            }
        }
        return true;
    }
    
    solve();
    return board;
}

// উদাহরণ
const board = [
    ['5','3','.','.','7','.','.','.','.'],
    ['6','.','.','1','9','5','.','.','.'],
    ['.','9','8','.','.','.','.','6','.'],
    ['8','.','.','.','6','.','.','.','3'],
    ['4','.','.','8','.','3','.','.','1'],
    ['7','.','.','.','2','.','.','.','6'],
    ['.','6','.','.','.','.','2','8','.'],
    ['.','.','.','4','1','9','.','.','5'],
    ['.','.','.','.','8','.','.','7','9']
];
console.log(solveSudoku(board));
সমস্যা ১০৫: Letter Combinations of a Phone Number
javascript
function letterCombinations(digits) {
    if (!digits.length) return [];
    
    const phone = {
        '2': 'abc',
        '3': 'def',
        '4': 'ghi',
        '5': 'jkl',
        '6': 'mno',
        '7': 'pqrs',
        '8': 'tuv',
        '9': 'wxyz'
    };
    
    const result = [];
    
    function backtrack(index, current) {
        if (index === digits.length) {
            result.push(current);
            return;
        }
        
        const letters = phone[digits[index]];
        for (let letter of letters) {
            backtrack(index + 1, current + letter);
        }
    }
    
    backtrack(0, '');
    return result;
}

// উদাহরণ
console.log(letterCombinations("23")); // ["ad","ae","af","bd","be","bf","cd","ce","cf"]
সমস্যা ১০৬: Generate Parentheses
javascript
function generateParenthesis(n) {
    const result = [];
    
    function backtrack(current, open, close) {
        if (current.length === n * 2) {
            result.push(current);
            return;
        }
        
        if (open < n) {
            backtrack(current + '(', open + 1, close);
        }
        
        if (close < open) {
            backtrack(current + ')', open, close + 1);
        }
    }
    
    backtrack('', 0, 0);
    return result;
}

// উদাহরণ
console.log(generateParenthesis(3)); // ["((()))","(()())","(())()","()(())","()()()"]
সমস্যা ১০৭: Palindrome Partitioning
javascript
function partition(s) {
    const result = [];
    
    function isPalindrome(str, left, right) {
        while (left < right) {
            if (str[left] !== str[right]) return false;
            left++;
            right--;
        }
        return true;
    }
    
    function backtrack(start, current) {
        if (start === s.length) {
            result.push([...current]);
            return;
        }
        
        for (let end = start; end < s.length; end++) {
            if (isPalindrome(s, start, end)) {
                current.push(s.substring(start, end + 1));
                backtrack(end + 1, current);
                current.pop();
            }
        }
    }
    
    backtrack(0, []);
    return result;
}

// উদাহরণ
console.log(partition("aab")); // [["a","a","b"],["aa","b"]]
সমস্যা ১০৮: Word Search
javascript
function exist(board, word) {
    const rows = board.length;
    const cols = board[0].length;
    
    function dfs(i, j, index) {
        if (index === word.length) return true;
        if (i < 0 || i >= rows || j < 0 || j >= cols || board[i][j] !== word[index]) {
            return false;
        }
        
        const temp = board[i][j];
        board[i][j] = '#';
        
        const found = dfs(i + 1, j, index + 1) ||
                      dfs(i - 1, j, index + 1) ||
                      dfs(i, j + 1, index + 1) ||
                      dfs(i, j - 1, index + 1);
        
        board[i][j] = temp;
        return found;
    }
    
    for (let i = 0; i < rows; i++) {
        for (let j = 0; j < cols; j++) {
            if (dfs(i, j, 0)) return true;
        }
    }
    
    return false;
}

// উদাহরণ
const board = [
    ['A','B','C','E'],
    ['S','F','C','S'],
    ['A','D','E','E']
];
console.log(exist(board, "ABCCED")); // true
সমস্যা ১০৯: Restore IP Addresses
javascript
function restoreIpAddresses(s) {
    const result = [];
    
    function backtrack(start, parts) {
        if (parts.length === 4) {
            if (start === s.length) {
                result.push(parts.join('.'));
            }
            return;
        }
        
        for (let len = 1; len <= 3; len++) {
            if (start + len > s.length) break;
            
            const part = s.substring(start, start + len);
            
            // leading zero check
            if (part.length > 1 && part[0] === '0') continue;
            
            // value range check
            if (parseInt(part) > 255) continue;
            
            parts.push(part);
            backtrack(start + len, parts);
            parts.pop();
        }
    }
    
    backtrack(0, []);
    return result;
}

// উদাহরণ
console.log(restoreIpAddresses("25525511135")); // ["255.255.11.135","255.255.111.35"]
সমস্যা ১১০: Rat in a Maze
javascript
function ratInAMaze(maze) {
    const n = maze.length;
    const solution = Array(n).fill().map(() => Array(n).fill(0));
    
    function isSafe(x, y) {
        return x >= 0 && x < n && y >= 0 && y < n && maze[x][y] === 1;
    }
    
    function solve(x, y) {
        if (x === n - 1 && y === n - 1) {
            solution[x][y] = 1;
            return true;
        }
        
        if (isSafe(x, y)) {
            solution[x][y] = 1;
            
            // move right
            if (solve(x + 1, y)) return true;
            
            // move down
            if (solve(x, y + 1)) return true;
            
            // backtrack
            solution[x][y] = 0;
            return false;
        }
        
        return false;
    }
    
    if (solve(0, 0)) {
        return solution;
    }
    
    return null;
}

// উদাহরণ
const maze = [
    [1, 0, 0, 0],
    [1, 1, 0, 1],
    [0, 1, 0, 0],
    [1, 1, 1, 1]
];
console.log(ratInAMaze(maze));
৭. ডায়নামিক প্রোগ্রামিং (১১১-১২৫)
সমস্যা ১১১: Fibonacci using DP (Memoization)
javascript
function fibDP(n, memo = {}) {
    if (n <= 1) return n;
    
    if (memo[n] === undefined) {
        memo[n] = fibDP(n - 1, memo) + fibDP(n - 2, memo);
    }
    
    return memo[n];
}

// উদাহরণ
console.log(fibDP(10)); // 55
সমস্যা ১১২: Climbing Stairs
javascript
function climbStairs(n) {
    if (n <= 2) return n;
    
    const dp = [1, 2];
    
    for (let i = 2; i < n; i++) {
        dp[i] = dp[i - 1] + dp[i - 2];
    }
    
    return dp[n - 1];
}

// উদাহরণ
console.log(climbStairs(5)); // 8
সমস্যা ১১৩: Coin Change (Minimum Coins)
javascript
function coinChange(coins, amount) {
    const dp = new Array(amount + 1).fill(amount + 1);
    dp[0] = 0;
    
    for (let i = 1; i <= amount; i++) {
        for (let coin of coins) {
            if (coin <= i) {
                dp[i] = Math.min(dp[i], dp[i - coin] + 1);
            }
        }
    }
    
    return dp[amount] > amount ? -1 : dp[amount];
}

// উদাহরণ
console.log(coinChange([1,2,5], 11)); // 3
সমস্যা ১১৪: Longest Increasing Subsequence
javascript
function lengthOfLIS(nums) {
    const n = nums.length;
    if (n === 0) return 0;
    
    const dp = new Array(n).fill(1);
    let maxLen = 1;
    
    for (let i = 1; i < n; i++) {
        for (let j = 0; j < i; j++) {
            if (nums[i] > nums[j]) {
                dp[i] = Math.max(dp[i], dp[j] + 1);
            }
        }
        maxLen = Math.max(maxLen, dp[i]);
    }
    
    return maxLen;
}

// উদাহরণ
console.log(lengthOfLIS([10,9,2,5,3,7,101,18])); // 4
সমস্যা ১১৫: 0/1 Knapsack
javascript
function knapsack(values, weights, capacity) {
    const n = values.length;
    const dp = Array(n + 1).fill().map(() => Array(capacity + 1).fill(0));
    
    for (let i = 1; i <= n; i++) {
        for (let w = 1; w <= capacity; w++) {
            if (weights[i - 1] <= w) {
                dp[i][w] = Math.max(
                    values[i - 1] + dp[i - 1][w - weights[i - 1]],
                    dp[i - 1][w]
                );
            } else {
                dp[i][w] = dp[i - 1][w];
            }
        }
    }
    
    return dp[n][capacity];
}

// উদাহরণ
console.log(knapsack([60,100,120], [10,20,30], 50)); // 220
সমস্যা ১১৬: Edit Distance
javascript
function minDistance(word1, word2) {
    const m = word1.length;
    const n = word2.length;
    
    const dp = Array(m + 1).fill().map(() => Array(n + 1).fill(0));
    
    for (let i = 0; i <= m; i++) {
        dp[i][0] = i;
    }
    
    for (let j = 0; j <= n; j++) {
        dp[0][j] = j;
    }
    
    for (let i = 1; i <= m; i++) {
        for (let j = 1; j <= n; j++) {
            if (word1[i - 1] === word2[j - 1]) {
                dp[i][j] = dp[i - 1][j - 1];
            } else {
                dp[i][j] = 1 + Math.min(
                    dp[i - 1][j],      // delete
                    dp[i][j - 1],      // insert
                    dp[i - 1][j - 1]   // replace
                );
            }
        }
    }
    
    return dp[m][n];
}

// উদাহরণ
console.log(minDistance("horse", "ros")); // 3
সমস্যা ১১৭: Longest Common Subsequence
javascript
function longestCommonSubsequence(text1, text2) {
    const m = text1.length;
    const n = text2.length;
    
    const dp = Array(m + 1).fill().map(() => Array(n + 1).fill(0));
    
    for (let i = 1; i <= m; i++) {
        for (let j = 1; j <= n; j++) {
            if (text1[i - 1] === text2[j - 1]) {
                dp[i][j] = dp[i - 1][j - 1] + 1;
            } else {
                dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1]);
            }
        }
    }
    
    return dp[m][n];
}

// উদাহরণ
console.log(longestCommonSubsequence("abcde", "ace")); // 3
সমস্যা ১১৮: Maximum Product Subarray
javascript
function maxProductSubarray(nums) {
    let maxSoFar = nums[0];
    let minSoFar = nums[0];
    let result = nums[0];
    
    for (let i = 1; i < nums.length; i++) {
        const temp = maxSoFar;
        maxSoFar = Math.max(nums[i], maxSoFar * nums[i], minSoFar * nums[i]);
        minSoFar = Math.min(nums[i], temp * nums[i], minSoFar * nums[i]);
        result = Math.max(result, maxSoFar);
    }
    
    return result;
}

// উদাহরণ
console.log(maxProductSubarray([2,3,-2,4])); // 6
সমস্যা ১১৯: House Robber
javascript
function rob(nums) {
    const n = nums.length;
    if (n === 0) return 0;
    if (n === 1) return nums[0];
    
    const dp = [nums[0], Math.max(nums[0], nums[1])];
    
    for (let i = 2; i < n; i++) {
        dp[i] = Math.max(dp[i - 1], dp[i - 2] + nums[i]);
    }
    
    return dp[n - 1];
}

// উদাহরণ
console.log(rob([1,2,3,1])); // 4
সমস্যা ১২০: Unique Paths
javascript
function uniquePaths(m, n) {
    const dp = Array(m).fill().map(() => Array(n).fill(1));
    
    for (let i = 1; i < m; i++) {
        for (let j = 1; j < n; j++) {
            dp[i][j] = dp[i - 1][j] + dp[i][j - 1];
        }
    }
    
    return dp[m - 1][n - 1];
}

// উদাহরণ
console.log(uniquePaths(3, 7)); // 28
সমস্যা ১২১: Minimum Path Sum
javascript
function minPathSum(grid) {
    const m = grid.length;
    const n = grid[0].length;
    
    for (let i = 1; i < m; i++) {
        grid[i][0] += grid[i - 1][0];
    }
    
    for (let j = 1; j < n; j++) {
        grid[0][j] += grid[0][j - 1];
    }
    
    for (let i = 1; i < m; i++) {
        for (let j = 1; j < n; j++) {
            grid[i][j] += Math.min(grid[i - 1][j], grid[i][j - 1]);
        }
    }
    
    return grid[m - 1][n - 1];
}

// উদাহরণ
const grid = [
    [1,3,1],
    [1,5,1],
    [4,2,1]
];
console.log(minPathSum(grid)); // 7
সমস্যা ১২২: Decode Ways
javascript
function numDecodings(s) {
    if (s[0] === '0') return 0;
    
    const n = s.length;
    const dp = new Array(n + 1).fill(0);
    dp[0] = 1;
    dp[1] = 1;
    
    for (let i = 2; i <= n; i++) {
        const oneDigit = parseInt(s.substring(i - 1, i));
        const twoDigits = parseInt(s.substring(i - 2, i));
        
        if (oneDigit >= 1) {
            dp[i] += dp[i - 1];
        }
        
        if (twoDigits >= 10 && twoDigits <= 26) {
            dp[i] += dp[i - 2];
        }
    }
    
    return dp[n];
}

// উদাহরণ
console.log(numDecodings("226")); // 3
সমস্যা ১২৩: Word Break
javascript
function wordBreakDP(s, wordDict) {
    const wordSet = new Set(wordDict);
    const n = s.length;
    const dp = new Array(n + 1).fill(false);
    dp[0] = true;
    
    for (let i = 1; i <= n; i++) {
        for (let j = 0; j < i; j++) {
            if (dp[j] && wordSet.has(s.substring(j, i))) {
                dp[i] = true;
                break;
            }
        }
    }
    
    return dp[n];
}

// উদাহরণ
console.log(wordBreakDP("leetcode", ["leet","code"])); // true
সমস্যা ১২৪: Coin Change 2 (Number of Ways)
javascript
function change(amount, coins) {
    const dp = new Array(amount + 1).fill(0);
    dp[0] = 1;
    
    for (let coin of coins) {
        for (let i = coin; i <= amount; i++) {
            dp[i] += dp[i - coin];
        }
    }
    
    return dp[amount];
}

// উদাহরণ
console.log(change(5, [1,2,5])); // 4
সমস্যা ১২৫: Partition Equal Subset Sum
javascript
function canPartition(nums) {
    const sum = nums.reduce((a, b) => a + b, 0);
    
    if (sum % 2 !== 0) return false;
    
    const target = sum / 2;
    const dp = new Array(target + 1).fill(false);
    dp[0] = true;
    
    for (let num of nums) {
        for (let i = target; i >= num; i--) {
            if (dp[i - num]) {
                dp[i] = true;
            }
        }
    }
    
    return dp[target];
}

// উদাহরণ
console.log(canPartition([1,5,11,5])); // true
৮. সর্টিং ও সার্চিং (১২৬-১৪০)
সমস্যা ১২৬: Bubble Sort
javascript
function bubbleSort(arr) {
    const n = arr.length;
    
    for (let i = 0; i < n - 1; i++) {
        let swapped = false;
        
        for (let j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];
                swapped = true;
            }
        }
        
        if (!swapped) break;
    }
    
    return arr;
}

// উদাহরণ
console.log(bubbleSort([64,34,25,12,22,11,90]));
সমস্যা ১২৭: Selection Sort
javascript
function selectionSort(arr) {
    const n = arr.length;
    
    for (let i = 0; i < n - 1; i++) {
        let minIndex = i;
        
        for (let j = i + 1; j < n; j++) {
            if (arr[j] < arr[minIndex]) {
                minIndex = j;
            }
        }
        
        if (minIndex !== i) {
            [arr[i], arr[minIndex]] = [arr[minIndex], arr[i]];
        }
    }
    
    return arr;
}
সমস্যা ১২৮: Insertion Sort
javascript
function insertionSort(arr) {
    const n = arr.length;
    
    for (let i = 1; i < n; i++) {
        const key = arr[i];
        let j = i - 1;
        
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        
        arr[j + 1] = key;
    }
    
    return arr;
}
সমস্যা ১২৯: Merge Sort
javascript
function mergeSort(arr) {
    if (arr.length <= 1) return arr;
    
    const mid = Math.floor(arr.length / 2);
    const left = mergeSort(arr.slice(0, mid));
    const right = mergeSort(arr.slice(mid));
    
    return merge(left, right);
}

function merge(left, right) {
    const result = [];
    let i = 0, j = 0;
    
    while (i < left.length && j < right.length) {
        if (left[i] <= right[j]) {
            result.push(left[i++]);
        } else {
            result.push(right[j++]);
        }
    }
    
    return [...result, ...left.slice(i), ...right.slice(j)];
}

// উদাহরণ
console.log(mergeSort([64,34,25,12,22,11,90]));
সমস্যা ১৩০: Quick Sort
javascript
function quickSort(arr, low = 0, high = arr.length - 1) {
    if (low < high) {
        const pi = partition(arr, low, high);
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
    return arr;
}

function partition(arr, low, high) {
    const pivot = arr[high];
    let i = low - 1;
    
    for (let j = low; j < high; j++) {
        if (arr[j] <= pivot) {
            i++;
            [arr[i], arr[j]] = [arr[j], arr[i]];
        }
    }
    
    [arr[i + 1], arr[high]] = [arr[high], arr[i + 1]];
    return i + 1;
}

// উদাহরণ
console.log(quickSort([64,34,25,12,22,11,90]));
সমস্যা ১৩১: Heap Sort
javascript
function heapSort(arr) {
    const n = arr.length;
    
    // build heap
    for (let i = Math.floor(n / 2) - 1; i >= 0; i--) {
        heapify(arr, n, i);
    }
    
    // extract elements from heap
    for (let i = n - 1; i > 0; i--) {
        [arr[0], arr[i]] = [arr[i], arr[0]];
        heapify(arr, i, 0);
    }
    
    return arr;
}

function heapify(arr, n, i) {
    let largest = i;
    const left = 2 * i + 1;
    const right = 2 * i + 2;
    
    if (left < n && arr[left] > arr[largest]) {
        largest = left;
    }
    
    if (right < n && arr[right] > arr[largest]) {
        largest = right;
    }
    
    if (largest !== i) {
        [arr[i], arr[largest]] = [arr[largest], arr[i]];
        heapify(arr, n, largest);
    }
}
সমস্যা ১৩২: Binary Search (Iterative)
javascript
function binarySearch(arr, target) {
    let left = 0;
    let right = arr.length - 1;
    
    while (left <= right) {
        const mid = Math.floor((left + right) / 2);
        
        if (arr[mid] === target) return mid;
        
        if (arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    return -1;
}

// উদাহরণ
console.log(binarySearch([1,2,3,4,5,6,7,8,9], 5)); // 4
সমস্যা ১৩৩: Binary Search (Recursive)
javascript
function binarySearchRecursive(arr, target, left = 0, right = arr.length - 1) {
    if (left > right) return -1;
    
    const mid = Math.floor((left + right) / 2);
    
    if (arr[mid] === target) return mid;
    
    if (arr[mid] < target) {
        return binarySearchRecursive(arr, target, mid + 1, right);
    } else {
        return binarySearchRecursive(arr, target, left, mid - 1);
    }
}
সমস্যা ১৩৪: First Occurrence in Sorted Array
javascript
function firstOccurrence(arr, target) {
    let left = 0;
    let right = arr.length - 1;
    let result = -1;
    
    while (left <= right) {
        const mid = Math.floor((left + right) / 2);
        
        if (arr[mid] === target) {
            result = mid;
            right = mid - 1;
        } else if (arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    return result;
}

// উদাহরণ
console.log(firstOccurrence([1,2,3,3,3,4,5], 3)); // 2
সমস্যা ১৩৫: Last Occurrence in Sorted Array
javascript
function lastOccurrence(arr, target) {
    let left = 0;
    let right = arr.length - 1;
    let result = -1;
    
    while (left <= right) {
        const mid = Math.floor((left + right) / 2);
        
        if (arr[mid] === target) {
            result = mid;
            left = mid + 1;
        } else if (arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    return result;
}

// উদাহরণ
console.log(lastOccurrence([1,2,3,3,3,4,5], 3)); // 4
সমস্যা ১৩৬: Search in Rotated Sorted Array
javascript
function searchRotated(nums, target) {
    let left = 0;
    let right = nums.length - 1;
    
    while (left <= right) {
        const mid = Math.floor((left + right) / 2);
        
        if (nums[mid] === target) return mid;
        
        // left half is sorted
        if (nums[left] <= nums[mid]) {
            if (target >= nums[left] && target < nums[mid]) {
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        } 
        // right half is sorted
        else {
            if (target > nums[mid] && target <= nums[right]) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
    }
    
    return -1;
}

// উদাহরণ
console.log(searchRotated([4,5,6,7,0,1,2], 0)); // 4
সমস্যা ১৩৭: Find Peak Element
javascript
function findPeakElement(nums) {
    let left = 0;
    let right = nums.length - 1;
    
    while (left < right) {
        const mid = Math.floor((left + right) / 2);
        
        if (nums[mid] > nums[mid + 1]) {
            right = mid;
        } else {
            left = mid + 1;
        }
    }
    
    return left;
}

// উদাহরণ
console.log(findPeakElement([1,2,1,3,5,6,4])); // 5
সমস্যা ১৩৮: Search a 2D Matrix
javascript
function searchMatrix(matrix, target) {
    if (!matrix.length || !matrix[0].length) return false;
    
    const m = matrix.length;
    const n = matrix[0].length;
    
    let left = 0;
    let right = m * n - 1;
    
    while (left <= right) {
        const mid = Math.floor((left + right) / 2);
        const row = Math.floor(mid / n);
        const col = mid % n;
        
        if (matrix[row][col] === target) return true;
        
        if (matrix[row][col] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    return false;
}

// উদাহরণ
const matrix = [
    [1,3,5,7],
    [10,11,16,20],
    [23,30,34,60]
];
console.log(searchMatrix(matrix, 3)); // true
সমস্যা ১৩৯: Kth Smallest Element in Sorted Matrix
javascript
function kthSmallest(matrix, k) {
    const n = matrix.length;
    let left = matrix[0][0];
    let right = matrix[n - 1][n - 1];
    
    function countLessEqual(target) {
        let count = 0;
        let row = n - 1;
        let col = 0;
        
        while (row >= 0 && col < n) {
            if (matrix[row][col] <= target) {
                count += row + 1;
                col++;
            } else {
                row--;
            }
        }
        
        return count;
    }
    
    while (left < right) {
        const mid = Math.floor((left + right) / 2);
        const count = countLessEqual(mid);
        
        if (count < k) {
            left = mid + 1;
        } else {
            right = mid;
        }
    }
    
    return left;
}

// উদাহরণ
const matrix2 = [
    [1,5,9],
    [10,11,13],
    [12,13,15]
];
console.log(kthSmallest(matrix2, 8)); // 13
সমস্যা ১৪০: Median of Two Sorted Arrays
javascript
function findMedianSortedArrays(nums1, nums2) {
    if (nums1.length > nums2.length) {
        return findMedianSortedArrays(nums2, nums1);
    }
    
    const m = nums1.length;
    const n = nums2.length;
    let left = 0;
    let right = m;
    
    while (left <= right) {
        const partition1 = Math.floor((left + right) / 2);
        const partition2 = Math.floor((m + n + 1) / 2) - partition1;
        
        const maxLeft1 = partition1 === 0 ? -Infinity : nums1[partition1 - 1];
        const minRight1 = partition1 === m ? Infinity : nums1[partition1];
        
        const maxLeft2 = partition2 === 0 ? -Infinity : nums2[partition2 - 1];
        const minRight2 = partition2 === n ? Infinity : nums2[partition2];
        
        if (maxLeft1 <= minRight2 && maxLeft2 <= minRight1) {
            if ((m + n) % 2 === 0) {
                return (Math.max(maxLeft1, maxLeft2) + Math.min(minRight1, minRight2)) / 2;
            } else {
                return Math.max(maxLeft1, maxLeft2);
            }
        } else if (maxLeft1 > minRight2) {
            right = partition1 - 1;
        } else {
            left = partition1 + 1;
        }
    }
    
    return 0;
}

// উদাহরণ
console.log(findMedianSortedArrays([1,3], [2])); // 2
৯. ম্যাথ ও নাম্বার থিওরি (১৪১-১৫৫)
সমস্যা ১৪১: Prime Number Check
javascript
function isPrime(n) {
    if (n <= 1) return false;
    if (n <= 3) return true;
    if (n % 2 === 0 || n % 3 === 0) return false;
    
    for (let i = 5; i * i <= n; i += 6) {
        if (n % i === 0 || n % (i + 2) === 0) return false;
    }
    
    return true;
}

// উদাহরণ
console.log(isPrime(17)); // true
সমস্যা ১৪২: Sieve of Eratosthenes
javascript
function sieveOfEratosthenes(n) {
    const isPrime = new Array(n + 1).fill(true);
    isPrime[0] = isPrime[1] = false;
    
    for (let i = 2; i * i <= n; i++) {
        if (isPrime[i]) {
            for (let j = i * i; j <= n; j += i) {
                isPrime[j] = false;
            }
        }
    }
    
    const primes = [];
    for (let i = 2; i <= n; i++) {
        if (isPrime[i]) primes.push(i);
    }
    
    return primes;
}

// উদাহরণ
console.log(sieveOfEratosthenes(30));
সমস্যা ১৪৩: GCD (Greatest Common Divisor)
javascript
function gcd(a, b) {
    while (b !== 0) {
        const temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

// উদাহরণ
console.log(gcd(48, 18)); // 6
সমস্যা ১৪৪: LCM (Least Common Multiple)
javascript
function lcm(a, b) {
    return (a * b) / gcd(a, b);
}

// উদাহরণ
console.log(lcm(12, 18)); // 36
সমস্যা ১৪৫: Factorial (Iterative)
javascript
function factorialIterative(n) {
    let result = 1;
    for (let i = 2; i <= n; i++) {
        result *= i;
    }
    return result;
}

// উদাহরণ
console.log(factorialIterative(5)); // 120
সমস্যা ১৪৬: Trailing Zeroes in Factorial
javascript
function trailingZeroes(n) {
    let count = 0;
    
    for (let i = 5; i <= n; i *= 5) {
        count += Math.floor(n / i);
    }
    
    return count;
}

// উদাহরণ
console.log(trailingZeroes(25)); // 6
সমস্যা ১৪৭: Power Function (Iterative)
javascript
function powerIterative(x, n) {
    let result = 1;
    let base = x;
    let exponent = n;
    
    if (exponent < 0) {
        base = 1 / base;
        exponent = -exponent;
    }
    
    while (exponent > 0) {
        if (exponent % 2 === 1) {
            result *= base;
        }
        base *= base;
        exponent = Math.floor(exponent / 2);
    }
    
    return result;
}

// উদাহরণ
console.log(powerIterative(2, 10)); // 1024
সমস্যা ১৪৮: Fibonacci (Iterative)
javascript
function fibonacciIterative(n) {
    if (n <= 1) return n;
    
    let a = 0;
    let b = 1;
    
    for (let i = 2; i <= n; i++) {
        const c = a + b;
        a = b;
        b = c;
    }
    
    return b;
}

// উদাহরণ
console.log(fibonacciIterative(10)); // 55
সমস্যা ১৪৯: Happy Number
javascript
function isHappy(n) {
    const seen = new Set();
    
    function sumOfSquares(num) {
        let sum = 0;
        while (num > 0) {
            const digit = num % 10;
            sum += digit * digit;
            num = Math.floor(num / 10);
        }
        return sum;
    }
    
    while (n !== 1 && !seen.has(n)) {
        seen.add(n);
        n = sumOfSquares(n);
    }
    
    return n === 1;
}

// উদাহরণ
console.log(isHappy(19)); // true
সমস্যা ১৫০: Ugly Number
javascript
function isUgly(n) {
    if (n <= 0) return false;
    
    for (let prime of [2, 3, 5]) {
        while (n % prime === 0) {
            n /= prime;
        }
    }
    
    return n === 1;
}

// উদাহরণ
console.log(isUgly(14)); // false
সমস্যা ১৫১: Count Primes
javascript
function countPrimes(n) {
    if (n < 2) return 0;
    
    const isPrime = new Array(n).fill(true);
    isPrime[0] = isPrime[1] = false;
    
    for (let i = 2; i * i < n; i++) {
        if (isPrime[i]) {
            for (let j = i * i; j < n; j += i) {
                isPrime[j] = false;
            }
        }
    }
    
    return isPrime.filter(Boolean).length;
}

// উদাহরণ
console.log(countPrimes(10)); // 4
সমস্যা ১৫২: Perfect Number
javascript
function checkPerfectNumber(num) {
    if (num <= 1) return false;
    
    let sum = 1;
    for (let i = 2; i * i <= num; i++) {
        if (num % i === 0) {
            sum += i;
            if (i !== num / i) {
                sum += num / i;
            }
        }
    }
    
    return sum === num;
}

// উদাহরণ
console.log(checkPerfectNumber(28)); // true
সমস্যা ১৫৩: Roman to Integer
javascript
function romanToInt(s) {
    const values = {
        'I': 1,
        'V': 5,
        'X': 10,
        'L': 50,
        'C': 100,
        'D': 500,
        'M': 1000
    };
    
    let total = 0;
    let prev = 0;
    
    for (let i = s.length - 1; i >= 0; i--) {
        const current = values[s[i]];
        
        if (current < prev) {
            total -= current;
        } else {
            total += current;
        }
        
        prev = current;
    }
    
    return total;
}

// উদাহরণ
console.log(romanToInt("MCMXCIV")); // 1994
সমস্যা ১৫৪: Integer to Roman
javascript
function intToRoman(num) {
    const values = [1000,900,500,400,100,90,50,40,10,9,5,4,1];
    const symbols = ["M","CM","D","CD","C","XC","L","XL","X","IX","V","IV","I"];
    
    let result = "";
    
    for (let i = 0; i < values.length; i++) {
        while (num >= values[i]) {
            result += symbols[i];
            num -= values[i];
        }
    }
    
    return result;
}

// উদাহরণ
console.log(intToRoman(1994)); // "MCMXCIV"
সমস্যা ১৫৫: Excel Sheet Column Title
javascript
function convertToTitle(columnNumber) {
    let result = "";
    
    while (columnNumber > 0) {
        columnNumber--;
        result = String.fromCharCode(65 + (columnNumber % 26)) + result;
        columnNumber = Math.floor(columnNumber / 26);
    }
    
    return result;
}

// উদাহরণ
console.log(convertToTitle(701)); // "ZY"
১০. ম্যাট্রিক্স (১৫৬-১৭০)
সমস্যা ১৫৬: Spiral Matrix
javascript
function spiralOrder(matrix) {
    if (!matrix.length) return [];
    
    const result = [];
    let top = 0;
    let bottom = matrix.length - 1;
    let left = 0;
    let right = matrix[0].length - 1;
    
    while (top <= bottom && left <= right) {
        // top row
        for (let i = left; i <= right; i++) {
            result.push(matrix[top][i]);
        }
        top++;
        
        // right column
        for (let i = top; i <= bottom; i++) {
            result.push(matrix[i][right]);
        }
        right--;
        
        if (top <= bottom) {
            // bottom row
            for (let i = right; i >= left; i--) {
                result.push(matrix[bottom][i]);
            }
            bottom--;
        }
        
        if (left <= right) {
            // left column
            for (let i = bottom; i >= top; i--) {
                result.push(matrix[i][left]);
            }
            left++;
        }
    }
    
    return result;
}

// উদাহরণ
const matrix = [
    [1,2,3],
    [4,5,6],
    [7,8,9]
];
console.log(spiralOrder(matrix)); // [1,2,3,6,9,8,7,4,5]
সমস্যা ১৫৭: Rotate Image (90 degrees clockwise)
javascript
function rotate(matrix) {
    const n = matrix.length;
    
    // transpose
    for (let i = 0; i < n; i++) {
        for (let j = i + 1; j < n; j++) {
            [matrix[i][j], matrix[j][i]] = [matrix[j][i], matrix[i][j]];
        }
    }
    
    // reverse each row
    for (let i = 0; i < n; i++) {
        matrix[i].reverse();
    }
    
    return matrix;
}

// উদাহরণ
const matrix2 = [
    [1,2,3],
    [4,5,6],
    [7,8,9]
];
console.log(rotate(matrix2));
সমস্যা ১৫৮: Set Matrix Zeroes
javascript
function setZeroes(matrix) {
    const m = matrix.length;
    const n = matrix[0].length;
    
    let firstRowZero = false;
    let firstColZero = false;
    
    // check first row
    for (let j = 0; j < n; j++) {
        if (matrix[0][j] === 0) {
            firstRowZero = true;
            break;
        }
    }
    
    // check first column
    for (let i = 0; i < m; i++) {
        if (matrix[i][0] === 0) {
            firstColZero = true;
            break;
        }
    }
    
    // mark zeros on first row and column
    for (let i = 1; i < m; i++) {
        for (let j = 1; j < n; j++) {
            if (matrix[i][j] === 0) {
                matrix[i][0] = 0;
                matrix[0][j] = 0;
            }
        }
    }
    
    // set zeros based on marks
    for (let i = 1; i < m; i++) {
        for (let j = 1; j < n; j++) {
            if (matrix[i][0] === 0 || matrix[0][j] === 0) {
                matrix[i][j] = 0;
            }
        }
    }
    
    // set first row to zero
    if (firstRowZero) {
        for (let j = 0; j < n; j++) {
            matrix[0][j] = 0;
        }
    }
    
    // set first column to zero
    if (firstColZero) {
        for (let i = 0; i < m; i++) {
            matrix[i][0] = 0;
        }
    }
    
    return matrix;
}
সমস্যা ১৫৯: Search a 2D Matrix II
javascript
function searchMatrixII(matrix, target) {
    if (!matrix.length) return false;
    
    let row = 0;
    let col = matrix[0].length - 1;
    
    while (row < matrix.length && col >= 0) {
        if (matrix[row][col] === target) {
            return true;
        } else if (matrix[row][col] > target) {
            col--;
        } else {
            row++;
        }
    }
    
    return false;
}

// উদাহরণ
const matrix3 = [
    [1,4,7,11,15],
    [2,5,8,12,19],
    [3,6,9,16,22],
    [10,13,14,17,24],
    [18,21,23,26,30]
];
console.log(searchMatrixII(matrix3, 5)); // true
সমস্যা ১৬০: Transpose Matrix
javascript
function transpose(matrix) {
    const m = matrix.length;
    const n = matrix[0].length;
    
    const result = Array(n).fill().map(() => Array(m).fill(0));
    
    for (let i = 0; i < m; i++) {
        for (let j = 0; j < n; j++) {
            result[j][i] = matrix[i][j];
        }
    }
    
    return result;
}

// উদাহরণ
const matrix4 = [
    [1,2,3],
    [4,5,6]
];
console.log(transpose(matrix4));
সমস্যা ১৬১: Matrix Diagonal Sum
javascript
function diagonalSum(mat) {
    const n = mat.length;
    let sum = 0;
    
    for (let i = 0; i < n; i++) {
        sum += mat[i][i]; // primary diagonal
        sum += mat[i][n - 1 - i]; // secondary diagonal
    }
    
    // middle element counted twice, subtract if n is odd
    if (n % 2 === 1) {
        sum -= mat[Math.floor(n / 2)][Math.floor(n / 2)];
    }
    
    return sum;
}

// উদাহরণ
const mat = [
    [1,2,3],
    [4,5,6],
    [7,8,9]
];
console.log(diagonalSum(mat)); // 25
সমস্যা ১৬২: Island Perimeter
javascript
function islandPerimeter(grid) {
    let perimeter = 0;
    const m = grid.length;
    const n = grid[0].length;
    
    for (let i = 0; i < m; i++) {
        for (let j = 0; j < n; j++) {
            if (grid[i][j] === 1) {
                perimeter += 4;
                
                // check up
                if (i > 0 && grid[i - 1][j] === 1) perimeter -= 2;
                // check left
                if (j > 0 && grid[i][j - 1] === 1) perimeter -= 2;
            }
        }
    }
    
    return perimeter;
}

// উদাহরণ
const grid = [
    [0,1,0,0],
    [1,1,1,0],
    [0,1,0,0],
    [1,1,0,0]
];
console.log(islandPerimeter(grid)); // 16
সমস্যা ১৬৩: Flood Fill
javascript
function floodFill(image, sr, sc, newColor) {
    const originalColor = image[sr][sc];
    if (originalColor === newColor) return image;
    
    function dfs(i, j) {
        if (i < 0 || i >= image.length || j < 0 || j >= image[0].length || 
            image[i][j] !== originalColor) {
            return;
        }
        
        image[i][j] = newColor;
        
        dfs(i + 1, j);
        dfs(i - 1, j);
        dfs(i, j + 1);
        dfs(i, j - 1);
    }
    
    dfs(sr, sc);
    return image;
}
সমস্যা ১৬৪: Rotting Oranges
javascript
function orangesRotting(grid) {
    const m = grid.length;
    const n = grid[0].length;
    const queue = [];
    let fresh = 0;
    
    for (let i = 0; i < m; i++) {
        for (let j = 0; j < n; j++) {
            if (grid[i][j] === 2) {
                queue.push([i, j, 0]);
            } else if (grid[i][j] === 1) {
                fresh++;
            }
        }
    }
    
    if (fresh === 0) return 0;
    
    const dirs = [[1,0], [-1,0], [0,1], [0,-1]];
    let minutes = 0;
    
    while (queue.length) {
        const [x, y, time] = queue.shift();
        minutes = Math.max(minutes, time);
        
        for (let [dx, dy] of dirs) {
            const nx = x + dx;
            const ny = y + dy;
            
            if (nx >= 0 && nx < m && ny >= 0 && ny < n && grid[nx][ny] === 1) {
                grid[nx][ny] = 2;
                fresh--;
                queue.push([nx, ny, time + 1]);
            }
        }
    }
    
    return fresh === 0 ? minutes : -1;
}

// উদাহরণ
const grid2 = [
    [2,1,1],
    [1,1,0],
    [0,1,1]
];
console.log(orangesRotting(grid2)); // 4
সমস্যা ১৬৫: Number of Islands
javascript
function numIslands(grid) {
    if (!grid.length) return 0;
    
    const m = grid.length;
    const n = grid[0].length;
    let count = 0;
    
    function dfs(i, j) {
        if (i < 0 || i >= m || j < 0 || j >= n || grid[i][j] === '0') {
            return;
        }
        
        grid[i][j] = '0';
        
        dfs(i + 1, j);
        dfs(i - 1, j);
        dfs(i, j + 1);
        dfs(i, j - 1);
    }
    
    for (let i = 0; i < m; i++) {
        for (let j = 0; j < n; j++) {
            if (grid[i][j] === '1') {
                count++;
                dfs(i, j);
            }
        }
    }
    
    return count;
}

// উদাহরণ
const grid3 = [
    ['1','1','1','1','0'],
    ['1','1','0','1','0'],
    ['1','1','0','0','0'],
    ['0','0','0','0','0']
];
console.log(numIslands(grid3)); // 1
সমস্যা ১৬৬: Max Area of Island
javascript
function maxAreaOfIsland(grid) {
    const m = grid.length;
    const n = grid[0].length;
    let maxArea = 0;
    
    function dfs(i, j) {
        if (i < 0 || i >= m || j < 0 || j >= n || grid[i][j] === 0) {
            return 0;
        }
        
        grid[i][j] = 0;
        
        return 1 + dfs(i + 1, j) + dfs(i - 1, j) + dfs(i, j + 1) + dfs(i, j - 1);
    }
    
    for (let i = 0; i < m; i++) {
        for (let j = 0; j < n; j++) {
            if (grid[i][j] === 1) {
                maxArea = Math.max(maxArea, dfs(i, j));
            }
        }
    }
    
    return maxArea;
}
সমস্যা ১৬৭: Surrounded Regions
javascript
function solve(board) {
    if (!board.length) return;
    
    const m = board.length;
    const n = board[0].length;
    
    function dfs(i, j) {
        if (i < 0 || i >= m || j < 0 || j >= n || board[i][j] !== 'O') {
            return;
        }
        
        board[i][j] = '#';
        
        dfs(i + 1, j);
        dfs(i - 1, j);
        dfs(i, j + 1);
        dfs(i, j - 1);
    }
    
    // mark border-connected 'O's
    for (let i = 0; i < m; i++) {
        if (board[i][0] === 'O') dfs(i, 0);
        if (board[i][n - 1] === 'O') dfs(i, n - 1);
    }
    
    for (let j = 0; j < n; j++) {
        if (board[0][j] === 'O') dfs(0, j);
        if (board[m - 1][j] === 'O') dfs(m - 1, j);
    }
    
    // flip remaining 'O' to 'X' and border-marked to 'O'
    for (let i = 0; i < m; i++) {
        for (let j = 0; j < n; j++) {
            if (board[i][j] === 'O') {
                board[i][j] = 'X';
            } else if (board[i][j] === '#') {
                board[i][j] = 'O';
            }
        }
    }
}
সমস্যা ১৬৮: Word Search in Matrix
javascript
function existWord(board, word) {
    const m = board.length;
    const n = board[0].length;
    
    function dfs(i, j, index) {
        if (index === word.length) return true;
        if (i < 0 || i >= m || j < 0 || j >= n || board[i][j] !== word[index]) {
            return false;
        }
        
        const temp = board[i][j];
        board[i][j] = '#';
        
        const found = dfs(i + 1, j, index + 1) ||
                      dfs(i - 1, j, index + 1) ||
                      dfs(i, j + 1, index + 1) ||
                      dfs(i, j - 1, index + 1);
        
        board[i][j] = temp;
        return found;
    }
    
    for (let i = 0; i < m; i++) {
        for (let j = 0; j < n; j++) {
            if (dfs(i, j, 0)) return true;
        }
    }
    
    return false;
}
সমস্যা ১৬৯: Beautiful Arrangement
javascript
function countArrangement(n) {
    const visited = new Array(n + 1).fill(false);
    let count = 0;
    
    function backtrack(pos) {
        if (pos > n) {
            count++;
            return;
        }
        
        for (let i = 1; i <= n; i++) {
            if (!visited[i] && (i % pos === 0 || pos % i === 0)) {
                visited[i] = true;
                backtrack(pos + 1);
                visited[i] = false;
            }
        }
    }
    
    backtrack(1);
    return count;
}

// উদাহরণ
console.log(countArrangement(3)); // 3
সমস্যা ১৭০: Combination Sum IV
javascript
function combinationSum4(nums, target) {
    const dp = new Array(target + 1).fill(0);
    dp[0] = 1;
    
    for (let i = 1; i <= target; i++) {
        for (let num of nums) {
            if (i >= num) {
                dp[i] += dp[i - num];
            }
        }
    }
    
    return dp[target];
}

// উদাহরণ
console.log(combinationSum4([1,2,3], 4)); // 7
১১. হ্যাশিং (১৭১-১৮০)
সমস্যা ১৭১: Two Sum using Hash Map
javascript
function twoSumHash(nums, target) {
    const map = new Map();
    
    for (let i = 0; i < nums.length; i++) {
        const complement = target - nums[i];
        
        if (map.has(complement)) {
            return [map.get(complement), i];
        }
        
        map.set(nums[i], i);
    }
    
    return [];
}
সমস্যা ১৭২: First Repeating Character
javascript
function firstRepeatingChar(str) {
    const seen = new Set();
    
    for (let char of str) {
        if (seen.has(char)) {
            return char;
        }
        seen.add(char);
    }
    
    return null;
}

// উদাহরণ
console.log(firstRepeatingChar("abcdefghija")); // 'a'
সমস্যা ১৭৩: Count Frequency of Elements
javascript
function countFrequency(arr) {
    const freq = {};
    
    for (let num of arr) {
        freq[num] = (freq[num] || 0) + 1;
    }
    
    return freq;
}

// উদাহরণ
console.log(countFrequency([1,2,2,3,3,3,4]));
সমস্যা ১৭৪: Intersection of Two Arrays
javascript
function intersection(nums1, nums2) {
    const set1 = new Set(nums1);
    const result = new Set();
    
    for (let num of nums2) {
        if (set1.has(num)) {
            result.add(num);
        }
    }
    
    return Array.from(result);
}

// উদাহরণ
console.log(intersection([1,2,2,1], [2,2])); // [2]
সমস্যা ১৭৫: Jewels and Stones
javascript
function numJewelsInStones(jewels, stones) {
    const jewelSet = new Set(jewels);
    let count = 0;
    
    for (let stone of stones) {
        if (jewelSet.has(stone)) {
            count++;
        }
    }
    
    return count;
}

// উদাহরণ
console.log(numJewelsInStones("aA", "aAAbbbb")); // 3
সমস্যা ১৭৬: Subarray Sum Equals K (with Hash Map)
javascript
function subarraySumHash(nums, k) {
    const sumMap = new Map();
    sumMap.set(0, 1);
    
    let sum = 0;
    let count = 0;
    
    for (let num of nums) {
        sum += num;
        
        if (sumMap.has(sum - k)) {
            count += sumMap.get(sum - k);
        }
        
        sumMap.set(sum, (sumMap.get(sum) || 0) + 1);
    }
    
    return count;
}
সমস্যা ১৭৭: Longest Consecutive Sequence
javascript
function longestConsecutive(nums) {
    const numSet = new Set(nums);
    let longest = 0;
    
    for (let num of nums) {
        if (!numSet.has(num - 1)) {
            let currentNum = num;
            let currentStreak = 1;
            
            while (numSet.has(currentNum + 1)) {
                currentNum++;
                currentStreak++;
            }
            
            longest = Math.max(longest, currentStreak);
        }
    }
    
    return longest;
}

// উদাহরণ
console.log(longestConsecutive([100,4,200,1,3,2])); // 4
সমস্যা ১৭৮: Top K Frequent Elements
javascript
function topKFrequent(nums, k) {
    const freq = {};
    
    for (let num of nums) {
        freq[num] = (freq[num] || 0) + 1;
    }
    
    return Object.entries(freq)
        .sort((a, b) => b[1] - a[1])
        .slice(0, k)
        .map(entry => parseInt(entry[0]));
}

// উদাহরণ
console.log(topKFrequent([1,1,1,2,2,3], 2)); // [1,2]
সমস্যা ১৭৯: Group Anagrams (with Hash Map)
javascript
function groupAnagramsHash(strs) {
    const map = {};
    
    for (let str of strs) {
        const sorted = str.split('').sort().join('');
        if (!map[sorted]) {
            map[sorted] = [];
        }
        map[sorted].push(str);
    }
    
    return Object.values(map);
}
সমস্যা ১৮০: Isomorphic Strings
javascript
function isIsomorphic(s, t) {
    if (s.length !== t.length) return false;
    
    const mapST = {};
    const mapTS = {};
    
    for (let i = 0; i < s.length; i++) {
        const charS = s[i];
        const charT = t[i];
        
        if (mapST[charS] && mapST[charS] !== charT) {
            return false;
        }
        
        if (mapTS[charT] && mapTS[charT] !== charS) {
            return false;
        }
        
        mapST[charS] = charT;
        mapTS[charT] = charS;
    }
    
    return true;
}

// উদাহরণ
console.log(isIsomorphic("egg", "add")); // true
১২. বিট ম্যানিপুলেশন (১৮১-১৯০)
সমস্যা ১৮১: Check if number is power of two
javascript
function isPowerOfTwo(n) {
    if (n <= 0) return false;
    return (n & (n - 1)) === 0;
}

// উদাহরণ
console.log(isPowerOfTwo(16)); // true
সমস্যা ১৮২: Count Set Bits (Hamming Weight)
javascript
function countSetBits(n) {
    let count = 0;
    
    while (n > 0) {
        count += n & 1;
        n >>= 1;
    }
    
    return count;
}

// উদাহরণ
console.log(countSetBits(13)); // 3
সমস্যা ১৮৩: Single Number (Find element appearing once)
javascript
function singleNumber(nums) {
    let result = 0;
    
    for (let num of nums) {
        result ^= num;
    }
    
    return result;
}

// উদাহরণ
console.log(singleNumber([4,1,2,1,2])); // 4
সমস্যা ১৮৪: Reverse Bits
javascript
function reverseBits(n) {
    let result = 0;
    
    for (let i = 0; i < 32; i++) {
        result <<= 1;
        result |= (n & 1);
        n >>= 1;
    }
    
    return result;
}

// উদাহরণ
console.log(reverseBits(43261596)); // 964176192
সমস্যা ১৮৫: Missing Number (using XOR)
javascript
function missingNumberXOR(nums) {
    const n = nums.length;
    let xor = n;
    
    for (let i = 0; i < n; i++) {
        xor ^= i ^ nums[i];
    }
    
    return xor;
}
সমস্যা ১৮৬: Sum of Two Integers (without + operator)
javascript
function getSum(a, b) {
    while (b !== 0) {
        const carry = a & b;
        a = a ^ b;
        b = carry << 1;
    }
    
    return a;
}

// উদাহরণ
console.log(getSum(5, 3)); // 8
সমস্যা ১৮৭: Find the Difference
javascript
function findTheDifference(s, t) {
    let result = 0;
    
    for (let i = 0; i < s.length; i++) {
        result ^= s.charCodeAt(i);
    }
    
    for (let i = 0; i < t.length; i++) {
        result ^= t.charCodeAt(i);
    }
    
    return String.fromCharCode(result);
}

// উদাহরণ
console.log(findTheDifference("abcd", "abcde")); // 'e'
সমস্যা ১৮৮: Power of Four
javascript
function isPowerOfFour(n) {
    if (n <= 0) return false;
    
    // power of two and the only set bit at odd position
    return (n & (n - 1)) === 0 && (n & 0xAAAAAAAA) === 0;
}

// উদাহরণ
console.log(isPowerOfFour(16)); // true
সমস্যা ১৮৯: Binary Watch
javascript
function readBinaryWatch(turnedOn) {
    const result = [];
    
    function countBits(num) {
        let count = 0;
        while (num > 0) {
            count += num & 1;
            num >>= 1;
        }
        return count;
    }
    
    for (let h = 0; h < 12; h++) {
        for (let m = 0; m < 60; m++) {
            if (countBits(h) + countBits(m) === turnedOn) {
                result.push(`${h}:${m.toString().padStart(2, '0')}`);
            }
        }
    }
    
    return result;
}

// উদাহরণ
console.log(readBinaryWatch(1));
সমস্যা ১৯০: Bitwise AND of Numbers Range
javascript
function rangeBitwiseAnd(left, right) {
    let shift = 0;
    
    while (left < right) {
        left >>= 1;
        right >>= 1;
        shift++;
    }
    
    return left << shift;
}

// উদাহরণ
console.log(rangeBitwiseAnd(5, 7)); // 4
১৩. স্লাইডিং উইন্ডো (১৯১-২০০)
সমস্যা ১৯১: Maximum Average Subarray I
javascript
function findMaxAverage(nums, k) {
    let sum = 0;
    
    for (let i = 0; i < k; i++) {
        sum += nums[i];
    }
    
    let maxSum = sum;
    
    for (let i = k; i < nums.length; i++) {
        sum = sum - nums[i - k] + nums[i];
        maxSum = Math.max(maxSum, sum);
    }
    
    return maxSum / k;
}

// উদাহরণ
console.log(findMaxAverage([1,12,-5,-6,50,3], 4)); // 12.75
সমস্যা ১৯২: Minimum Size Subarray Sum
javascript
function minSubArrayLen(target, nums) {
    let left = 0;
    let sum = 0;
    let minLen = Infinity;
    
    for (let right = 0; right < nums.length; right++) {
        sum += nums[right];
        
        while (sum >= target) {
            minLen = Math.min(minLen, right - left + 1);
            sum -= nums[left];
            left++;
        }
    }
    
    return minLen === Infinity ? 0 : minLen;
}

// উদাহরণ
console.log(minSubArrayLen(7, [2,3,1,2,4,3])); // 2
সমস্যা ১৯৩: Longest Substring Without Repeating Characters (Sliding Window)
javascript
function lengthOfLongestSubstringSliding(s) {
    const charMap = new Map();
    let left = 0;
    let maxLength = 0;
    
    for (let right = 0; right < s.length; right++) {
        const char = s[right];
        
        if (charMap.has(char) && charMap.get(char) >= left) {
            left = charMap.get(char) + 1;
        }
        
        charMap.set(char, right);
        maxLength = Math.max(maxLength, right - left + 1);
    }
    
    return maxLength;
}
সমস্যা ১৯৪: Permutation in String
javascript
function checkInclusion(s1, s2) {
    if (s1.length > s2.length) return false;
    
    const count1 = new Array(26).fill(0);
    const count2 = new Array(26).fill(0);
    
    for (let i = 0; i < s1.length; i++) {
        count1[s1.charCodeAt(i) - 97]++;
        count2[s2.charCodeAt(i) - 97]++;
    }
    
    for (let i = 0; i <= s2.length - s1.length; i++) {
        if (count1.join('') === count2.join('')) return true;
        
        if (i < s2.length - s1.length) {
            count2[s2.charCodeAt(i) - 97]--;
            count2[s2.charCodeAt(i + s1.length) - 97]++;
        }
    }
    
    return false;
}

// উদাহরণ
console.log(checkInclusion("ab", "eidbaooo")); // true
সমস্যা ১৯৫: Find All Anagrams in a String
javascript
function findAnagrams(s, p) {
    const result = [];
    if (s.length < p.length) return result;
    
    const pCount = new Array(26).fill(0);
    const sCount = new Array(26).fill(0);
    
    for (let i = 0; i < p.length; i++) {
        pCount[p.charCodeAt(i) - 97]++;
        sCount[s.charCodeAt(i) - 97]++;
    }
    
    for (let i = 0; i <= s.length - p.length; i++) {
        if (pCount.join('') === sCount.join('')) {
            result.push(i);
        }
        
        if (i < s.length - p.length) {
            sCount[s.charCodeAt(i) - 97]--;
            sCount[s.charCodeAt(i + p.length) - 97]++;
        }
    }
    
    return result;
}

// উদাহরণ
console.log(findAnagrams("cbaebabacd", "abc")); // [0,6]
সমস্যা ১৯৬: Max Consecutive Ones III
javascript
function longestOnes(nums, k) {
    let left = 0;
    let zeroCount = 0;
    let maxLen = 0;
    
    for (let right = 0; right < nums.length; right++) {
        if (nums[right] === 0) {
            zeroCount++;
        }
        
        while (zeroCount > k) {
            if (nums[left] === 0) {
                zeroCount--;
            }
            left++;
        }
        
        maxLen = Math.max(maxLen, right - left + 1);
    }
    
    return maxLen;
}

// উদাহরণ
console.log(longestOnes([1,1,1,0,0,0,1,1,1,1,0], 2)); // 6
সমস্যা ১৯৭: Fruit Into Baskets
javascript
function totalFruit(fruits) {
    const basket = new Map();
    let left = 0;
    let maxFruits = 0;
    
    for (let right = 0; right < fruits.length; right++) {
        const fruit = fruits[right];
        basket.set(fruit, (basket.get(fruit) || 0) + 1);
        
        while (basket.size > 2) {
            const leftFruit = fruits[left];
            basket.set(leftFruit, basket.get(leftFruit) - 1);
            
            if (basket.get(leftFruit) === 0) {
                basket.delete(leftFruit);
            }
            
            left++;
        }
        
        maxFruits = Math.max(maxFruits, right - left + 1);
    }
    
    return maxFruits;
}

// উদাহরণ
console.log(totalFruit([1,2,3,2,2])); // 4
সমস্যা ১৯৮: Longest Repeating Character Replacement
javascript
function characterReplacement(s, k) {
    const count = new Array(26).fill(0);
    let left = 0;
    let maxCount = 0;
    let maxLength = 0;
    
    for (let right = 0; right < s.length; right++) {
        const index = s.charCodeAt(right) - 65;
        count[index]++;
        maxCount = Math.max(maxCount, count[index]);
        
        while (right - left + 1 - maxCount > k) {
            count[s.charCodeAt(left) - 65]--;
            left++;
        }
        
        maxLength = Math.max(maxLength, right - left + 1);
    }
    
    return maxLength;
}

// উদাহরণ
console.log(characterReplacement("AABABBA", 1)); // 4
সমস্যা ১৯৯: Minimum Window Substring (Sliding Window)
javascript
function minWindowSliding(s, t) {
    if (!s || !t) return "";
    
    const need = {};
    for (let char of t) {
        need[char] = (need[char] || 0) + 1;
    }
    
    const have = {};
    let left = 0;
    let minLen = Infinity;
    let minStart = 0;
    let required = Object.keys(need).length;
    let formed = 0;
    
    for (let right = 0; right < s.length; right++) {
        const char = s[right];
        have[char] = (have[char] || 0) + 1;
        
        if (need[char] && have[char] === need[char]) {
            formed++;
        }
        
        while (formed === required && left <= right) {
            if (right - left + 1 < minLen) {
                minLen = right - left + 1;
                minStart = left;
            }
            
            const leftChar = s[left];
            have[leftChar]--;
            
            if (need[leftChar] && have[leftChar] < need[leftChar]) {
                formed--;
            }
            
            left++;
        }
    }
    
    return minLen === Infinity ? "" : s.substring(minStart, minStart + minLen);
}
সমস্যা ২০০: Sliding Window Maximum (Deque)
javascript
function maxSlidingWindowDeque(nums, k) {
    if (!nums.length || k === 0) return [];
    
    const result = [];
    const deque = []; // indices
    
    for (let i = 0; i < nums.length; i++) {
        // remove out of window indices
        while (deque.length && deque[0] < i - k + 1) {
            deque.shift();
        }
        
        // remove smaller values from back
        while (deque.length && nums[deque[deque.length - 1]] < nums[i]) {
            deque.pop();
        }
        
        deque.push(i);
        
        if (i >= k - 1) {
            result.push(nums[deque[0]]);
        }
    }
    
    return result;
}

// উদাহরণ
console.log(maxSlidingWindowDeque([1,3,-1,-3,5,3,6,7], 3)); // [3,3,5,5,6,7]
উপসংহার
এই ২০০টি DSA সমস্যা ও সমাধান JavaScript-এ বিভিন্ন ধরণের অ্যালগরিদম এবং ডাটা স্ট্রাকচার কভার করে। প্রতিটি সমস্যার সমাধান বুঝে পড়ুন, নিজে নিজে কোড লিখে প্র্যাকটিস করুন, এবং প্রয়োজনে কাস্টমাইজ করে দেখুন।

প্র্যাকটিস করার টিপস:

প্রথমে সমস্যাটি ভালোভাবে বুঝুন

নিজে চেষ্টা করুন সমাধান বের করতে

সমাধান দেখে বুঝুন এবং বিশ্লেষণ করুন

টাইম কমপ্লেক্সিটি এবং স্পেস কমপ্লেক্সিটি বিশ্লেষণ করুন

ভিন্ন ভিন্ন পদ্ধতিতে সমাধান করার চেষ্টা করুন

নিয়মিত প্র্যাকটিস করুন

শুভ কামনা! 🚀

