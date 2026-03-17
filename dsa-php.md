২০০টি DSA সমস্যা ও সমাধান (PHP তে)
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
php
function removeDuplicates($arr) {
    return array_values(array_unique($arr));
}

// উদাহরণ
$arr = [1, 2, 2, 3, 4, 4, 5];
print_r(removeDuplicates($arr));
// আউটপুট: [1, 2, 3, 4, 5]
সমস্যা ২: অ্যারে রিভার্স করা (বিল্ট-ইন ফাংশন ছাড়া)
php
function reverseArray($arr) {
    $left = 0;
    $right = count($arr) - 1;
    
    while ($left < $right) {
        $temp = $arr[$left];
        $arr[$left] = $arr[$right];
        $arr[$right] = $temp;
        $left++;
        $right--;
    }
    
    return $arr;
}

// উদাহরণ
$arr = [1, 2, 3, 4, 5];
print_r(reverseArray($arr));
// আউটপুট: [5, 4, 3, 2, 1]
সমস্যা ৩: অ্যারের দ্বিতীয় বৃহত্তম এলিমেন্ট বের করা
php
function secondLargest($arr) {
    $largest = PHP_INT_MIN;
    $secondLargest = PHP_INT_MIN;
    
    foreach ($arr as $num) {
        if ($num > $largest) {
            $secondLargest = $largest;
            $largest = $num;
        } elseif ($num > $secondLargest && $num != $largest) {
            $secondLargest = $num;
        }
    }
    
    return $secondLargest;
}

// উদাহরণ
$arr = [10, 5, 8, 20, 15];
echo secondLargest($arr); // আউটপুট: 15
সমস্যা ৪: অ্যারে rotate করা (K পজিশন ডানে)
php
function rotateRight($arr, $k) {
    $n = count($arr);
    $k = $k % $n;
    
    // শেষের k এলিমেন্ট নিয়ে শুরুতে বসাই
    $rotated = array_merge(
        array_slice($arr, $n - $k),
        array_slice($arr, 0, $n - $k)
    );
    
    return $rotated;
}

// উদাহরণ
$arr = [1, 2, 3, 4, 5];
print_r(rotateRight($arr, 2));
// আউটপুট: [4, 5, 1, 2, 3]
সমস্যা ৫: Majority এলিমেন্ট বের করা (n/2 এর বেশি বার আসে)
php
function majorityElement($arr) {
    $candidate = null;
    $count = 0;
    
    // Boyer-Moore Voting Algorithm
    foreach ($arr as $num) {
        if ($count == 0) {
            $candidate = $num;
        }
        $count += ($num == $candidate) ? 1 : -1;
    }
    
    return $candidate;
}

// উদাহরণ
$arr = [2, 2, 1, 1, 1, 2, 2];
echo majorityElement($arr); // আউটপুট: 2
সমস্যা ৬: দুটি সর্টেড অ্যারে মার্জ করা
php
function mergeSortedArrays($arr1, $arr2) {
    $result = [];
    $i = $j = 0;
    
    while ($i < count($arr1) && $j < count($arr2)) {
        if ($arr1[$i] < $arr2[$j]) {
            $result[] = $arr1[$i];
            $i++;
        } else {
            $result[] = $arr2[$j];
            $j++;
        }
    }
    
    // বাকি এলিমেন্ট যোগ করা
    while ($i < count($arr1)) {
        $result[] = $arr1[$i];
        $i++;
    }
    
    while ($j < count($arr2)) {
        $result[] = $arr2[$j];
        $j++;
    }
    
    return $result;
}

// উদাহরণ
$arr1 = [1, 3, 5, 7];
$arr2 = [2, 4, 6, 8];
print_r(mergeSortedArrays($arr1, $arr2));
// আউটপুট: [1, 2, 3, 4, 5, 6, 7, 8]
সমস্যা ৭: Missing Number বের করা (1 থেকে n পর্যন্ত)
php
function missingNumber($arr) {
    $n = count($arr) + 1;
    $expectedSum = $n * ($n + 1) / 2;
    $actualSum = array_sum($arr);
    
    return $expectedSum - $actualSum;
}

// উদাহরণ
$arr = [1, 2, 4, 5, 6];
echo missingNumber($arr); // আউটপুট: 3
সমস্যা ৮: Product of Array Except Self
php
function productExceptSelf($arr) {
    $n = count($arr);
    $result = array_fill(0, $n, 1);
    
    // বাম পাশের product
    $leftProduct = 1;
    for ($i = 0; $i < $n; $i++) {
        $result[$i] = $leftProduct;
        $leftProduct *= $arr[$i];
    }
    
    // ডান পাশের product
    $rightProduct = 1;
    for ($i = $n - 1; $i >= 0; $i--) {
        $result[$i] *= $rightProduct;
        $rightProduct *= $arr[$i];
    }
    
    return $result;
}

// উদাহরণ
$arr = [1, 2, 3, 4];
print_r(productExceptSelf($arr));
// আউটপুট: [24, 12, 8, 6]
সমস্যা ৯: Maximum Subarray Sum (Kadane's Algorithm)
php
function maxSubarraySum($arr) {
    $maxSoFar = $arr[0];
    $maxEndingHere = $arr[0];
    
    for ($i = 1; $i < count($arr); $i++) {
        $maxEndingHere = max($arr[$i], $maxEndingHere + $arr[$i]);
        $maxSoFar = max($maxSoFar, $maxEndingHere);
    }
    
    return $maxSoFar;
}

// উদাহরণ
$arr = [-2, 1, -3, 4, -1, 2, 1, -5, 4];
echo maxSubarraySum($arr); // আউটপুট: 6 (4 + -1 + 2 + 1)
সমস্যা ১০: Contains Duplicate
php
function containsDuplicate($arr) {
    $seen = [];
    
    foreach ($arr as $num) {
        if (isset($seen[$num])) {
            return true;
        }
        $seen[$num] = true;
    }
    
    return false;
}

// উদাহরণ
$arr = [1, 2, 3, 1];
echo containsDuplicate($arr) ? 'true' : 'false'; // আউটপুট: true
সমস্যা ১১: Two Sum
php
function twoSum($arr, $target) {
    $map = [];
    
    foreach ($arr as $i => $num) {
        $complement = $target - $num;
        
        if (array_key_exists($complement, $map)) {
            return [$map[$complement], $i];
        }
        
        $map[$num] = $i;
    }
    
    return [];
}

// উদাহরণ
$arr = [2, 7, 11, 15];
print_r(twoSum($arr, 9)); // আউটপুট: [0, 1]
সমস্যা ১২: Three Sum
php
function threeSum($arr) {
    $result = [];
    $n = count($arr);
    sort($arr);
    
    for ($i = 0; $i < $n - 2; $i++) {
        if ($i > 0 && $arr[$i] == $arr[$i - 1]) continue;
        
        $left = $i + 1;
        $right = $n - 1;
        
        while ($left < $right) {
            $sum = $arr[$i] + $arr[$left] + $arr[$right];
            
            if ($sum == 0) {
                $result[] = [$arr[$i], $arr[$left], $arr[$right]];
                
                while ($left < $right && $arr[$left] == $arr[$left + 1]) $left++;
                while ($left < $right && $arr[$right] == $arr[$right - 1]) $right--;
                
                $left++;
                $right--;
            } elseif ($sum < 0) {
                $left++;
            } else {
                $right--;
            }
        }
    }
    
    return $result;
}

// উদাহরণ
$arr = [-1, 0, 1, 2, -1, -4];
print_r(threeSum($arr));
সমস্যা ১৩: Best Time to Buy and Sell Stock
php
function maxProfit($prices) {
    $minPrice = PHP_INT_MAX;
    $maxProfit = 0;
    
    foreach ($prices as $price) {
        if ($price < $minPrice) {
            $minPrice = $price;
        } elseif ($price - $minPrice > $maxProfit) {
            $maxProfit = $price - $minPrice;
        }
    }
    
    return $maxProfit;
}

// উদাহরণ
$prices = [7, 1, 5, 3, 6, 4];
echo maxProfit($prices); // আউটপুট: 5
সমস্যা ১৪: Merge Intervals
php
function mergeIntervals($intervals) {
    if (empty($intervals)) return [];
    
    // intervals সর্ট করা
    usort($intervals, function($a, $b) {
        return $a[0] - $b[0];
    });
    
    $result = [$intervals[0]];
    
    for ($i = 1; $i < count($intervals); $i++) {
        $last = &$result[count($result) - 1];
        
        if ($intervals[$i][0] <= $last[1]) {
            // ওভারল্যাপ আছে, মার্জ করা
            $last[1] = max($last[1], $intervals[$i][1]);
        } else {
            // নতুন interval যোগ করা
            $result[] = $intervals[$i];
        }
    }
    
    return $result;
}

// উদাহরণ
$intervals = [[1,3], [2,6], [8,10], [15,18]];
print_r(mergeIntervals($intervals));
// আউটপুট: [[1,6], [8,10], [15,18]]
সমস্যা ১৫: Find Minimum in Rotated Sorted Array
php
function findMin($arr) {
    $left = 0;
    $right = count($arr) - 1;
    
    while ($left < $right) {
        $mid = floor(($left + $right) / 2);
        
        if ($arr[$mid] > $arr[$right]) {
            $left = $mid + 1;
        } else {
            $right = $mid;
        }
    }
    
    return $arr[$left];
}

// উদাহরণ
$arr = [4, 5, 6, 7, 0, 1, 2];
echo findMin($arr); // আউটপুট: 0
সমস্যা ১৬: Container With Most Water
php
function maxArea($height) {
    $left = 0;
    $right = count($height) - 1;
    $maxArea = 0;
    
    while ($left < $right) {
        $area = min($height[$left], $height[$right]) * ($right - $left);
        $maxArea = max($maxArea, $area);
        
        if ($height[$left] < $height[$right]) {
            $left++;
        } else {
            $right--;
        }
    }
    
    return $maxArea;
}

// উদাহরণ
$height = [1,8,6,2,5,4,8,3,7];
echo maxArea($height); // আউটপুট: 49
সমস্যা ১৭: Trapping Rain Water
php
function trap($height) {
    if (empty($height)) return 0;
    
    $left = 0;
    $right = count($height) - 1;
    $leftMax = $rightMax = $water = 0;
    
    while ($left < $right) {
        if ($height[$left] < $height[$right]) {
            if ($height[$left] >= $leftMax) {
                $leftMax = $height[$left];
            } else {
                $water += $leftMax - $height[$left];
            }
            $left++;
        } else {
            if ($height[$right] >= $rightMax) {
                $rightMax = $height[$right];
            } else {
                $water += $rightMax - $height[$right];
            }
            $right--;
        }
    }
    
    return $water;
}

// উদাহরণ
$height = [0,1,0,2,1,0,1,3,2,1,2,1];
echo trap($height); // আউটপুট: 6
সমস্যা ১৮: Find All Numbers Disappeared in an Array
php
function findDisappearedNumbers($arr) {
    $n = count($arr);
    
    // মার্ক করা যেসব সংখ্যা আছে
    for ($i = 0; $i < $n; $i++) {
        $index = abs($arr[$i]) - 1;
        if ($arr[$index] > 0) {
            $arr[$index] = -$arr[$index];
        }
    }
    
    // যে ইনডেক্সে positive মান আছে, সেগুলো missing
    $result = [];
    for ($i = 0; $i < $n; $i++) {
        if ($arr[$i] > 0) {
            $result[] = $i + 1;
        }
    }
    
    return $result;
}

// উদাহরণ
$arr = [4,3,2,7,8,2,3,1];
print_r(findDisappearedNumbers($arr));
// আউটপুট: [5,6]
সমস্যা ১৯: Move Zeroes to End
php
function moveZeroes(&$arr) {
    $lastNonZeroFoundAt = 0;
    
    // non-zero এলিমেন্ট সামনে এনে রাখা
    for ($i = 0; $i < count($arr); $i++) {
        if ($arr[$i] != 0) {
            $arr[$lastNonZeroFoundAt++] = $arr[$i];
        }
    }
    
    // বাকি পজিশনে zero বসানো
    for ($i = $lastNonZeroFoundAt; $i < count($arr); $i++) {
        $arr[$i] = 0;
    }
    
    return $arr;
}

// উদাহরণ
$arr = [0,1,0,3,12];
print_r(moveZeroes($arr));
// আউটপুট: [1,3,12,0,0]
সমস্যা ২০: Maximum Product Subarray
php
function maxProduct($arr) {
    $maxSoFar = $minSoFar = $result = $arr[0];
    
    for ($i = 1; $i < count($arr); $i++) {
        $temp = $maxSoFar;
        $maxSoFar = max($arr[$i], $maxSoFar * $arr[$i], $minSoFar * $arr[$i]);
        $minSoFar = min($arr[$i], $temp * $arr[$i], $minSoFar * $arr[$i]);
        $result = max($result, $maxSoFar);
    }
    
    return $result;
}

// উদাহরণ
$arr = [2,3,-2,4];
echo maxProduct($arr); // আউটপুট: 6 (2*3)
সমস্যা ২১: Find the Duplicate Number
php
function findDuplicate($arr) {
    // Floyd's Tortoise and Hare (Cycle Detection)
    $slow = $arr[0];
    $fast = $arr[0];
    
    do {
        $slow = $arr[$slow];
        $fast = $arr[$arr[$fast]];
    } while ($slow != $fast);
    
    // cycle এর শুরু খুঁজে বের করা
    $slow = $arr[0];
    while ($slow != $fast) {
        $slow = $arr[$slow];
        $fast = $arr[$fast];
    }
    
    return $slow;
}

// উদাহরণ
$arr = [1,3,4,2,2];
echo findDuplicate($arr); // আউটপুট: 2
সমস্যা ২২: Sort Colors (Dutch National Flag Problem)
php
function sortColors(&$arr) {
    $low = 0;
    $mid = 0;
    $high = count($arr) - 1;
    
    while ($mid <= $high) {
        switch ($arr[$mid]) {
            case 0: // red
                $temp = $arr[$low];
                $arr[$low] = $arr[$mid];
                $arr[$mid] = $temp;
                $low++;
                $mid++;
                break;
            case 1: // white
                $mid++;
                break;
            case 2: // blue
                $temp = $arr[$mid];
                $arr[$mid] = $arr[$high];
                $arr[$high] = $temp;
                $high--;
                break;
        }
    }
    
    return $arr;
}

// উদাহরণ
$arr = [2,0,2,1,1,0];
print_r(sortColors($arr));
// আউটপুট: [0,0,1,1,2,2]
সমস্যা ২৩: Find First and Last Position of Element in Sorted Array
php
function searchRange($arr, $target) {
    $result = [-1, -1];
    
    // প্রথম occurrence খুঁজে বের করা
    $left = 0;
    $right = count($arr) - 1;
    
    while ($left <= $right) {
        $mid = floor(($left + $right) / 2);
        
        if ($arr[$mid] == $target) {
            $result[0] = $mid;
            $right = $mid - 1; // বাম পাশে আরও আছে কিনা দেখার জন্য
        } elseif ($arr[$mid] < $target) {
            $left = $mid + 1;
        } else {
            $right = $mid - 1;
        }
    }
    
    // শেষ occurrence খুঁজে বের করা
    $left = 0;
    $right = count($arr) - 1;
    
    while ($left <= $right) {
        $mid = floor(($left + $right) / 2);
        
        if ($arr[$mid] == $target) {
            $result[1] = $mid;
            $left = $mid + 1; // ডান পাশে আরও আছে কিনা দেখার জন্য
        } elseif ($arr[$mid] < $target) {
            $left = $mid + 1;
        } else {
            $right = $mid - 1;
        }
    }
    
    return $result;
}

// উদাহরণ
$arr = [5,7,7,8,8,10];
print_r(searchRange($arr, 8)); // আউটপুট: [3,4]
সমস্যা ২৪: Jump Game
php
function canJump($arr) {
    $maxReach = 0;
    $n = count($arr);
    
    for ($i = 0; $i < $n; $i++) {
        if ($i > $maxReach) return false;
        $maxReach = max($maxReach, $i + $arr[$i]);
        if ($maxReach >= $n - 1) return true;
    }
    
    return false;
}

// উদাহরণ
$arr = [2,3,1,1,4];
echo canJump($arr) ? 'true' : 'false'; // আউটপুট: true
সমস্যা ২৫: Maximum Length of Subarray With Positive Product
php
function maxLengthPositiveProduct($arr) {
    $positive = $negative = $result = 0;
    
    foreach ($arr as $num) {
        if ($num > 0) {
            $positive++;
            $negative = $negative > 0 ? $negative + 1 : 0;
        } elseif ($num < 0) {
            $newPositive = $negative > 0 ? $negative + 1 : 0;
            $newNegative = $positive + 1;
            $positive = $newPositive;
            $negative = $newNegative;
        } else {
            $positive = $negative = 0;
        }
        
        $result = max($result, $positive);
    }
    
    return $result;
}

// উদাহরণ
$arr = [1,-2,-3,4];
echo maxLengthPositiveProduct($arr); // আউটপুট: 4
সমস্যা ২৬: Subarray Sum Equals K
php
function subarraySum($arr, $k) {
    $count = 0;
    $sum = 0;
    $sumMap = [0 => 1];
    
    foreach ($arr as $num) {
        $sum += $num;
        
        if (isset($sumMap[$sum - $k])) {
            $count += $sumMap[$sum - $k];
        }
        
        $sumMap[$sum] = ($sumMap[$sum] ?? 0) + 1;
    }
    
    return $count;
}

// উদাহরণ
$arr = [1,1,1];
echo subarraySum($arr, 2); // আউটপুট: 2
সমস্যা ২৭: Find Pivot Index
php
function pivotIndex($arr) {
    $totalSum = array_sum($arr);
    $leftSum = 0;
    
    for ($i = 0; $i < count($arr); $i++) {
        if ($leftSum == $totalSum - $leftSum - $arr[$i]) {
            return $i;
        }
        $leftSum += $arr[$i];
    }
    
    return -1;
}

// উদাহরণ
$arr = [1,7,3,6,5,6];
echo pivotIndex($arr); // আউটপুট: 3
সমস্যা ২৮: Maximum Product of Three Numbers
php
function maximumProduct($arr) {
    sort($arr);
    $n = count($arr);
    
    // দুটি কেস চেক করা: সবচেয়ে বড় তিনটি অথবা দুটি সবচেয়ে ছোট (negative) এবং সবচেয়ে বড়
    return max(
        $arr[$n-1] * $arr[$n-2] * $arr[$n-3],
        $arr[0] * $arr[1] * $arr[$n-1]
    );
}

// উদাহরণ
$arr = [1,2,3,4];
echo maximumProduct($arr); // আউটপুট: 24 (2*3*4)
সমস্যা ২৯: Find All Duplicates in an Array
php
function findDuplicates($arr) {
    $result = [];
    
    for ($i = 0; $i < count($arr); $i++) {
        $index = abs($arr[$i]) - 1;
        
        if ($arr[$index] < 0) {
            $result[] = abs($arr[$i]);
        } else {
            $arr[$index] = -$arr[$index];
        }
    }
    
    return $result;
}

// উদাহরণ
$arr = [4,3,2,7,8,2,3,1];
print_r(findDuplicates($arr)); // আউটপুট: [2,3]
সমস্যা ৩০: Next Permutation
php
function nextPermutation(&$arr) {
    $n = count($arr);
    $i = $n - 2;
    
    // পিছন থেকে প্রথম ডিপ খুঁজে বের করা যেখানে arr[i] < arr[i+1]
    while ($i >= 0 && $arr[$i] >= $arr[$i + 1]) {
        $i--;
    }
    
    if ($i >= 0) {
        $j = $n - 1;
        // arr[i] এর চেয়ে বড় প্রথম এলিমেন্ট খুঁজে বের করা
        while ($j >= 0 && $arr[$j] <= $arr[$i]) {
            $j--;
        }
        
        // swap arr[i] and arr[j]
        $temp = $arr[$i];
        $arr[$i] = $arr[$j];
        $arr[$j] = $temp;
    }
    
    // i+1 থেকে শেষ পর্যন্ত reverse করা
    $left = $i + 1;
    $right = $n - 1;
    
    while ($left < $right) {
        $temp = $arr[$left];
        $arr[$left] = $arr[$right];
        $arr[$right] = $temp;
        $left++;
        $right--;
    }
    
    return $arr;
}

// উদাহরণ
$arr = [1,2,3];
print_r(nextPermutation($arr)); // আউটপুট: [1,3,2]
২. স্ট্রিং সম্পর্কিত সমস্যা (৩১-৫০)
সমস্যা ৩১: Palindrome Check
php
function isPalindrome($str) {
    $str = preg_replace('/[^a-zA-Z0-9]/', '', strtolower($str));
    return $str == strrev($str);
}

// উদাহরণ
echo isPalindrome("A man, a plan, a canal: Panama") ? 'true' : 'false'; // true
সমস্যা ৩২: Reverse String
php
function reverseString(&$str) {
    $left = 0;
    $right = strlen($str) - 1;
    
    while ($left < $right) {
        $temp = $str[$left];
        $str[$left] = $str[$right];
        $str[$right] = $temp;
        $left++;
        $right--;
    }
    
    return $str;
}

// উদাহরণ
$str = "hello";
echo reverseString($str); // আউটপুট: "olleh"
সমস্যা ৩৩: First Unique Character in a String
php
function firstUniqChar($str) {
    $count = [];
    
    for ($i = 0; $i < strlen($str); $i++) {
        $char = $str[$i];
        $count[$char] = ($count[$char] ?? 0) + 1;
    }
    
    for ($i = 0; $i < strlen($str); $i++) {
        if ($count[$str[$i]] == 1) {
            return $i;
        }
    }
    
    return -1;
}

// উদাহরণ
echo firstUniqChar("leetcode"); // আউটপুট: 0
সমস্যা ৩৪: Valid Anagram
php
function isAnagram($s, $t) {
    if (strlen($s) != strlen($t)) return false;
    
    $count = [];
    
    for ($i = 0; $i < strlen($s); $i++) {
        $count[$s[$i]] = ($count[$s[$i]] ?? 0) + 1;
        $count[$t[$i]] = ($count[$t[$i]] ?? 0) - 1;
    }
    
    foreach ($count as $c) {
        if ($c != 0) return false;
    }
    
    return true;
}

// উদাহরণ
echo isAnagram("anagram", "nagaram") ? 'true' : 'false'; // true
সমস্যা ৩৫: Longest Common Prefix
php
function longestCommonPrefix($strs) {
    if (empty($strs)) return "";
    
    $prefix = $strs[0];
    
    for ($i = 1; $i < count($strs); $i++) {
        while (strpos($strs[$i], $prefix) !== 0) {
            $prefix = substr($prefix, 0, -1);
            if (empty($prefix)) return "";
        }
    }
    
    return $prefix;
}

// উদাহরণ
$strs = ["flower","flow","flight"];
echo longestCommonPrefix($strs); // আউটপুট: "fl"
সমস্যা ৩৬: Count and Say
php
function countAndSay($n) {
    if ($n == 1) return "1";
    
    $prev = countAndSay($n - 1);
    $result = "";
    $count = 1;
    
    for ($i = 0; $i < strlen($prev); $i++) {
        if ($i + 1 < strlen($prev) && $prev[$i] == $prev[$i + 1]) {
            $count++;
        } else {
            $result .= $count . $prev[$i];
            $count = 1;
        }
    }
    
    return $result;
}

// উদাহরণ
echo countAndSay(4); // আউটপুট: "1211"
সমস্যা ৩৭: String to Integer (atoi)
php
function myAtoi($str) {
    $str = ltrim($str);
    if (empty($str)) return 0;
    
    $sign = 1;
    $i = 0;
    
    if ($str[0] == '+' || $str[0] == '-') {
        $sign = ($str[0] == '-') ? -1 : 1;
        $i = 1;
    }
    
    $result = 0;
    while ($i < strlen($str) && ctype_digit($str[$i])) {
        $result = $result * 10 + intval($str[$i]);
        
        // overflow check
        if ($result * $sign > 2147483647) return 2147483647;
        if ($result * $sign < -2147483648) return -2147483648;
        
        $i++;
    }
    
    return $result * $sign;
}

// উদাহরণ
echo myAtoi("   -42"); // আউটপুট: -42
সমস্যা ৩৮: Valid Parentheses
php
function isValid($s) {
    $stack = [];
    $map = [
        ')' => '(',
        '}' => '{',
        ']' => '['
    ];
    
    for ($i = 0; $i < strlen($s); $i++) {
        $char = $s[$i];
        
        if (in_array($char, ['(', '{', '['])) {
            array_push($stack, $char);
        } elseif (isset($map[$char])) {
            if (empty($stack) || array_pop($stack) != $map[$char]) {
                return false;
            }
        }
    }
    
    return empty($stack);
}

// উদাহরণ
echo isValid("()[]{}") ? 'true' : 'false'; // true
সমস্যা ৩৯: Longest Palindromic Substring
php
function longestPalindrome($s) {
    if (strlen($s) < 2) return $s;
    
    $start = 0;
    $maxLength = 1;
    
    for ($i = 0; $i < strlen($s); $i++) {
        // odd length palindrome
        $len1 = expandAroundCenter($s, $i, $i);
        // even length palindrome
        $len2 = expandAroundCenter($s, $i, $i + 1);
        
        $len = max($len1, $len2);
        
        if ($len > $maxLength) {
            $maxLength = $len;
            $start = $i - floor(($len - 1) / 2);
        }
    }
    
    return substr($s, $start, $maxLength);
}

function expandAroundCenter($s, $left, $right) {
    while ($left >= 0 && $right < strlen($s) && $s[$left] == $s[$right]) {
        $left--;
        $right++;
    }
    return $right - $left - 1;
}

// উদাহরণ
echo longestPalindrome("babad"); // আউটপুট: "bab" বা "aba"
সমস্যা ৪০: Group Anagrams
php
function groupAnagrams($strs) {
    $result = [];
    
    foreach ($strs as $str) {
        $chars = str_split($str);
        sort($chars);
        $key = implode('', $chars);
        
        $result[$key][] = $str;
    }
    
    return array_values($result);
}

// উদাহরণ
$strs = ["eat", "tea", "tan", "ate", "nat", "bat"];
print_r(groupAnagrams($strs));
সমস্যা ৪১: Minimum Window Substring
php
function minWindow($s, $t) {
    if (empty($s) || empty($t)) return "";
    
    $need = [];
    for ($i = 0; $i < strlen($t); $i++) {
        $need[$t[$i]] = ($need[$t[$i]] ?? 0) + 1;
    }
    
    $have = [];
    $left = 0;
    $minLen = PHP_INT_MAX;
    $minStart = 0;
    $required = count($need);
    $formed = 0;
    
    for ($right = 0; $right < strlen($s); $right++) {
        $char = $s[$right];
        
        $have[$char] = ($have[$char] ?? 0) + 1;
        
        if (isset($need[$char]) && $have[$char] == $need[$char]) {
            $formed++;
        }
        
        while ($formed == $required && $left <= $right) {
            if ($right - $left + 1 < $minLen) {
                $minLen = $right - $left + 1;
                $minStart = $left;
            }
            
            $leftChar = $s[$left];
            $have[$leftChar]--;
            
            if (isset($need[$leftChar]) && $have[$leftChar] < $need[$leftChar]) {
                $formed--;
            }
            
            $left++;
        }
    }
    
    return $minLen == PHP_INT_MAX ? "" : substr($s, $minStart, $minLen);
}

// উদাহরণ
echo minWindow("ADOBECODEBANC", "ABC"); // আউটপুট: "BANC"
সমস্যা ৪২: Decode String
php
function decodeString($s) {
    $stack = [];
    $currentNum = 0;
    $currentStr = '';
    
    for ($i = 0; $i < strlen($s); $i++) {
        $char = $s[$i];
        
        if (is_numeric($char)) {
            $currentNum = $currentNum * 10 + intval($char);
        } elseif ($char == '[') {
            array_push($stack, [$currentStr, $currentNum]);
            $currentStr = '';
            $currentNum = 0;
        } elseif ($char == ']') {
            list($prevStr, $num) = array_pop($stack);
            $currentStr = $prevStr . str_repeat($currentStr, $num);
        } else {
            $currentStr .= $char;
        }
    }
    
    return $currentStr;
}

// উদাহরণ
echo decodeString("3[a]2[bc]"); // আউটপুট: "aaabcbc"
সমস্যা ৪৩: Longest Substring Without Repeating Characters
php
function lengthOfLongestSubstring($s) {
    $charMap = [];
    $left = 0;
    $maxLength = 0;
    
    for ($right = 0; $right < strlen($s); $right++) {
        $char = $s[$right];
        
        if (isset($charMap[$char]) && $charMap[$char] >= $left) {
            $left = $charMap[$char] + 1;
        }
        
        $charMap[$char] = $right;
        $maxLength = max($maxLength, $right - $left + 1);
    }
    
    return $maxLength;
}

// উদাহরণ
echo lengthOfLongestSubstring("abcabcbb"); // আউটপুট: 3
সমস্যা ৪৪: Repeated DNA Sequences
php
function findRepeatedDnaSequences($s) {
    $seen = [];
    $result = [];
    
    for ($i = 0; $i <= strlen($s) - 10; $i++) {
        $sequence = substr($s, $i, 10);
        
        if (isset($seen[$sequence])) {
            if ($seen[$sequence] == 1) {
                $result[] = $sequence;
            }
            $seen[$sequence] = 2;
        } else {
            $seen[$sequence] = 1;
        }
    }
    
    return $result;
}

// উদাহরণ
$s = "AAAAACCCCCAAAAACCCCCCAAAAAGGGTTT";
print_r(findRepeatedDnaSequences($s));
সমস্যা ৪৫: Valid Palindrome II (একটি character delete করার সুযোগ)
php
function validPalindrome($s) {
    $left = 0;
    $right = strlen($s) - 1;
    
    while ($left < $right) {
        if ($s[$left] != $s[$right]) {
            return isPalindromeRange($s, $left + 1, $right) || 
                   isPalindromeRange($s, $left, $right - 1);
        }
        $left++;
        $right--;
    }
    
    return true;
}

function isPalindromeRange($s, $left, $right) {
    while ($left < $right) {
        if ($s[$left] != $s[$right]) return false;
        $left++;
        $right--;
    }
    return true;
}

// উদাহরণ
echo validPalindrome("abca") ? 'true' : 'false'; // true
সমস্যা ৪৬: String Compression
php
function compress(&$chars) {
    $write = 0;
    $read = 0;
    
    while ($read < count($chars)) {
        $char = $chars[$read];
        $count = 0;
        
        while ($read < count($chars) && $chars[$read] == $char) {
            $read++;
            $count++;
        }
        
        $chars[$write++] = $char;
        
        if ($count > 1) {
            foreach (str_split((string)$count) as $digit) {
                $chars[$write++] = $digit;
            }
        }
    }
    
    return $write;
}

// উদাহরণ
$chars = ["a","a","b","b","c","c","c"];
echo compress($chars); // আউটপুট: 6
print_r(array_slice($chars, 0, 6)); // ["a","2","b","2","c","3"]
সমস্যা ৪৭: Add Binary
php
function addBinary($a, $b) {
    $result = '';
    $carry = 0;
    $i = strlen($a) - 1;
    $j = strlen($b) - 1;
    
    while ($i >= 0 || $j >= 0 || $carry) {
        $sum = $carry;
        
        if ($i >= 0) {
            $sum += intval($a[$i]);
            $i--;
        }
        
        if ($j >= 0) {
            $sum += intval($b[$j]);
            $j--;
        }
        
        $result = ($sum % 2) . $result;
        $carry = intdiv($sum, 2);
    }
    
    return $result;
}

// উদাহরণ
echo addBinary("11", "1"); // আউটপুট: "100"
সমস্যা ৪৮: Multiply Strings
php
function multiply($num1, $num2) {
    if ($num1 == "0" || $num2 == "0") return "0";
    
    $len1 = strlen($num1);
    $len2 = strlen($num2);
    $result = array_fill(0, $len1 + $len2, 0);
    
    for ($i = $len1 - 1; $i >= 0; $i--) {
        for ($j = $len2 - 1; $j >= 0; $j--) {
            $mul = intval($num1[$i]) * intval($num2[$j]);
            $sum = $mul + $result[$i + $j + 1];
            
            $result[$i + $j + 1] = $sum % 10;
            $result[$i + $j] += intdiv($sum, 10);
        }
    }
    
    // leading zeros বাদ দেওয়া
    $start = 0;
    while ($start < count($result) && $result[$start] == 0) {
        $start++;
    }
    
    $resultStr = '';
    for ($i = $start; $i < count($result); $i++) {
        $resultStr .= $result[$i];
    }
    
    return $resultStr;
}

// উদাহরণ
echo multiply("123", "456"); // আউটপুট: "56088"
সমস্যা ৪৯: Word Break
php
function wordBreak($s, $wordDict) {
    $wordSet = array_flip($wordDict);
    $dp = array_fill(0, strlen($s) + 1, false);
    $dp[0] = true;
    
    for ($i = 1; $i <= strlen($s); $i++) {
        for ($j = 0; $j < $i; $j++) {
            if ($dp[$j] && isset($wordSet[substr($s, $j, $i - $j)])) {
                $dp[$i] = true;
                break;
            }
        }
    }
    
    return $dp[strlen($s)];
}

// উদাহরণ
$s = "leetcode";
$wordDict = ["leet", "code"];
echo wordBreak($s, $wordDict) ? 'true' : 'false'; // true
সমস্যা ৫০: Basic Calculator II
php
function calculate($s) {
    $stack = [];
    $num = 0;
    $op = '+';
    $s = str_replace(' ', '', $s);
    
    for ($i = 0; $i < strlen($s); $i++) {
        if (is_numeric($s[$i])) {
            $num = $num * 10 + intval($s[$i]);
        }
        
        if (!is_numeric($s[$i]) || $i == strlen($s) - 1) {
            switch ($op) {
                case '+':
                    array_push($stack, $num);
                    break;
                case '-':
                    array_push($stack, -$num);
                    break;
                case '*':
                    array_push($stack, array_pop($stack) * $num);
                    break;
                case '/':
                    array_push($stack, intval(array_pop($stack) / $num));
                    break;
            }
            $op = $s[$i];
            $num = 0;
        }
    }
    
    return array_sum($stack);
}

// উদাহরণ
echo calculate("3+2*2"); // আউটপুট: 7
৩. লিংকড লিস্ট (৫১-৬৫)
প্রথমে Node class ডিফাইন করা যাক:

php
class ListNode {
    public $val = 0;
    public $next = null;
    
    function __construct($val = 0, $next = null) {
        $this->val = $val;
        $this->next = $next;
    }
}

// লিংকড লিস্ট তৈরি করার helper function
function createLinkedList($arr) {
    if (empty($arr)) return null;
    
    $head = new ListNode($arr[0]);
    $current = $head;
    
    for ($i = 1; $i < count($arr); $i++) {
        $current->next = new ListNode($arr[$i]);
        $current = $current->next;
    }
    
    return $head;
}

// লিংকড লিস্ট প্রিন্ট করার helper function
function printLinkedList($head) {
    $result = [];
    $current = $head;
    
    while ($current != null) {
        $result[] = $current->val;
        $current = $current->next;
    }
    
    echo implode(" -> ", $result) . "\n";
}
সমস্যা ৫১: Reverse Linked List
php
function reverseList($head) {
    $prev = null;
    $current = $head;
    
    while ($current != null) {
        $next = $current->next;
        $current->next = $prev;
        $prev = $current;
        $current = $next;
    }
    
    return $prev;
}

// উদাহরণ
$head = createLinkedList([1,2,3,4,5]);
printLinkedList(reverseList($head)); // 5 -> 4 -> 3 -> 2 -> 1
সমস্যা ৫২: Detect Cycle in Linked List
php
function hasCycle($head) {
    if ($head == null) return false;
    
    $slow = $head;
    $fast = $head;
    
    while ($fast != null && $fast->next != null) {
        $slow = $slow->next;
        $fast = $fast->next->next;
        
        if ($slow == $fast) {
            return true;
        }
    }
    
    return false;
}

// উদাহরণ
$head = createLinkedList([3,2,0,-4]);
// creating cycle for demonstration
$head->next->next->next->next = $head->next;
echo hasCycle($head) ? 'true' : 'false'; // true
সমস্যা ৫৩: Merge Two Sorted Lists
php
function mergeTwoLists($l1, $l2) {
    $dummy = new ListNode();
    $current = $dummy;
    
    while ($l1 != null && $l2 != null) {
        if ($l1->val <= $l2->val) {
            $current->next = $l1;
            $l1 = $l1->next;
        } else {
            $current->next = $l2;
            $l2 = $l2->next;
        }
        $current = $current->next;
    }
    
    if ($l1 != null) {
        $current->next = $l1;
    }
    
    if ($l2 != null) {
        $current->next = $l2;
    }
    
    return $dummy->next;
}

// উদাহরণ
$l1 = createLinkedList([1,2,4]);
$l2 = createLinkedList([1,3,4]);
printLinkedList(mergeTwoLists($l1, $l2)); // 1 -> 1 -> 2 -> 3 -> 4 -> 4
সমস্যা ৫৪: Remove Nth Node From End of List
php
function removeNthFromEnd($head, $n) {
    $dummy = new ListNode(0, $head);
    $first = $dummy;
    $second = $dummy;
    
    // প্রথম pointer কে n+1 ধাপ এগিয়ে নেওয়া
    for ($i = 0; $i <= $n; $i++) {
        $first = $first->next;
    }
    
    // যখন প্রথম pointer শেষ হবে, দ্বিতীয় pointer থাকবে delete করার node এর আগে
    while ($first != null) {
        $first = $first->next;
        $second = $second->next;
    }
    
    // node delete করা
    $second->next = $second->next->next;
    
    return $dummy->next;
}

// উদাহরণ
$head = createLinkedList([1,2,3,4,5]);
printLinkedList(removeNthFromEnd($head, 2)); // 1 -> 2 -> 3 -> 5
সমস্যা ৫৫: Middle of the Linked List
php
function middleNode($head) {
    $slow = $head;
    $fast = $head;
    
    while ($fast != null && $fast->next != null) {
        $slow = $slow->next;
        $fast = $fast->next->next;
    }
    
    return $slow;
}

// উদাহরণ
$head = createLinkedList([1,2,3,4,5]);
echo middleNode($head)->val; // আউটপুট: 3
সমস্যা ৫৬: Palindrome Linked List
php
function isPalindromeList($head) {
    if ($head == null) return true;
    
    // list এর মাঝখান খুঁজে বের করা
    $slow = $head;
    $fast = $head;
    
    while ($fast != null && $fast->next != null) {
        $slow = $slow->next;
        $fast = $fast->next->next;
    }
    
    // দ্বিতীয় half reverse করা
    $secondHalf = reverseList($slow);
    $firstHalf = $head;
    
    // compare করা
    while ($secondHalf != null) {
        if ($firstHalf->val != $secondHalf->val) {
            return false;
        }
        $firstHalf = $firstHalf->next;
        $secondHalf = $secondHalf->next;
    }
    
    return true;
}

// উদাহরণ
$head = createLinkedList([1,2,2,1]);
echo isPalindromeList($head) ? 'true' : 'false'; // true
সমস্যা ৫৭: Intersection of Two Linked Lists
php
function getIntersectionNode($headA, $headB) {
    if ($headA == null || $headB == null) return null;
    
    $a = $headA;
    $b = $headB;
    
    while ($a != $b) {
        $a = ($a == null) ? $headB : $a->next;
        $b = ($b == null) ? $headA : $b->next;
    }
    
    return $a;
}

// উদাহরণ
$common = createLinkedList([8,4,5]);
$headA = createLinkedList([4,1]);
$headA->next->next = $common;
$headB = createLinkedList([5,6,1]);
$headB->next->next->next = $common;

$intersection = getIntersectionNode($headA, $headB);
echo $intersection ? $intersection->val : 'null'; // আউটপুট: 8
সমস্যা ৫৮: Add Two Numbers (Linked List)
php
function addTwoNumbers($l1, $l2) {
    $dummy = new ListNode();
    $current = $dummy;
    $carry = 0;
    
    while ($l1 != null || $l2 != null || $carry != 0) {
        $sum = $carry;
        
        if ($l1 != null) {
            $sum += $l1->val;
            $l1 = $l1->next;
        }
        
        if ($l2 != null) {
            $sum += $l2->val;
            $l2 = $l2->next;
        }
        
        $carry = intdiv($sum, 10);
        $current->next = new ListNode($sum % 10);
        $current = $current->next;
    }
    
    return $dummy->next;
}

// উদাহরণ
$l1 = createLinkedList([2,4,3]); // 342
$l2 = createLinkedList([5,6,4]); // 465
printLinkedList(addTwoNumbers($l1, $l2)); // 7 -> 0 -> 8 (807)
সমস্যা ৫৯: Remove Duplicates from Sorted List
php
function deleteDuplicates($head) {
    $current = $head;
    
    while ($current != null && $current->next != null) {
        if ($current->val == $current->next->val) {
            $current->next = $current->next->next;
        } else {
            $current = $current->next;
        }
    }
    
    return $head;
}

// উদাহরণ
$head = createLinkedList([1,1,2,3,3]);
printLinkedList(deleteDuplicates($head)); // 1 -> 2 -> 3
সমস্যা ৬০: Linked List Cycle II (Cycle শুরু হওয়া node খুঁজে বের করা)
php
function detectCycle($head) {
    if ($head == null) return null;
    
    $slow = $head;
    $fast = $head;
    $hasCycle = false;
    
    while ($fast != null && $fast->next != null) {
        $slow = $slow->next;
        $fast = $fast->next->next;
        
        if ($slow == $fast) {
            $hasCycle = true;
            break;
        }
    }
    
    if (!$hasCycle) return null;
    
    $slow = $head;
    while ($slow != $fast) {
        $slow = $slow->next;
        $fast = $fast->next;
    }
    
    return $slow;
}

// উদাহরণ
$head = createLinkedList([3,2,0,-4]);
$head->next->next->next->next = $head->next; // cycle at index 1
$cycleNode = detectCycle($head);
echo $cycleNode ? $cycleNode->val : 'null'; // আউটপুট: 2
সমস্যা ৬১: Rotate List
php
function rotateRightList($head, $k) {
    if ($head == null || $k == 0) return $head;
    
    // length বের করা
    $length = 1;
    $tail = $head;
    
    while ($tail->next != null) {
        $tail = $tail->next;
        $length++;
    }
    
    $k = $k % $length;
    if ($k == 0) return $head;
    
    // new head এর আগের node খুঁজে বের করা
    $stepsToNewHead = $length - $k - 1;
    $newTail = $head;
    
    for ($i = 0; $i < $stepsToNewHead; $i++) {
        $newTail = $newTail->next;
    }
    
    $newHead = $newTail->next;
    $newTail->next = null;
    $tail->next = $head;
    
    return $newHead;
}

// উদাহরণ
$head = createLinkedList([1,2,3,4,5]);
printLinkedList(rotateRightList($head, 2)); // 4 -> 5 -> 1 -> 2 -> 3
সমস্যা ৬২: Partition List
php
function partition($head, $x) {
    $beforeHead = new ListNode(0);
    $before = $beforeHead;
    $afterHead = new ListNode(0);
    $after = $afterHead;
    
    while ($head != null) {
        if ($head->val < $x) {
            $before->next = $head;
            $before = $before->next;
        } else {
            $after->next = $head;
            $after = $after->next;
        }
        $head = $head->next;
    }
    
    $after->next = null;
    $before->next = $afterHead->next;
    
    return $beforeHead->next;
}

// উদাহরণ
$head = createLinkedList([1,4,3,2,5,2]);
printLinkedList(partition($head, 3)); // 1 -> 2 -> 2 -> 4 -> 3 -> 5
সমস্যা ৬৩: Copy List with Random Pointer
php
class Node {
    public $val;
    public $next;
    public $random;
    
    function __construct($val = 0) {
        $this->val = $val;
        $this->next = null;
        $this->random = null;
    }
}

function copyRandomList($head) {
    if ($head == null) return null;
    
    // প্রথম পাস: প্রতিটি node এর পাশে তার copy বসানো
    $current = $head;
    while ($current != null) {
        $copy = new Node($current->val);
        $copy->next = $current->next;
        $current->next = $copy;
        $current = $copy->next;
    }
    
    // দ্বিতীয় পাস: random pointers কপি করা
    $current = $head;
    while ($current != null) {
        if ($current->random != null) {
            $current->next->random = $current->random->next;
        }
        $current = $current->next->next;
    }
    
    // তৃতীয় পাস: original এবং copy আলাদা করা
    $current = $head;
    $newHead = $head->next;
    
    while ($current != null) {
        $copy = $current->next;
        $current->next = $copy->next;
        $current = $current->next;
        $copy->next = ($current != null) ? $current->next : null;
    }
    
    return $newHead;
}
সমস্যা ৬৪: Sort List (Merge Sort ব্যবহার করে)
php
function sortList($head) {
    if ($head == null || $head->next == null) return $head;
    
    // list এর মাঝখান খুঁজে বের করা
    $slow = $head;
    $fast = $head;
    $prev = null;
    
    while ($fast != null && $fast->next != null) {
        $prev = $slow;
        $slow = $slow->next;
        $fast = $fast->next->next;
    }
    
    $prev->next = null; // দুই ভাগে ভাগ করা
    
    $left = sortList($head);
    $right = sortList($slow);
    
    return mergeTwoLists($left, $right);
}

// উদাহরণ
$head = createLinkedList([4,2,1,3]);
printLinkedList(sortList($head)); // 1 -> 2 -> 3 -> 4
সমস্যা ৬৫: Reorder List
php
function reorderList(&$head) {
    if ($head == null || $head->next == null) return;
    
    // list এর মাঝখান খুঁজে বের করা
    $slow = $head;
    $fast = $head;
    
    while ($fast != null && $fast->next != null) {
        $slow = $slow->next;
        $fast = $fast->next->next;
    }
    
    // দ্বিতীয় half reverse করা
    $second = reverseList($slow->next);
    $slow->next = null; // দুই ভাগে ভাগ করা
    
    // interleave করা
    $first = $head;
    while ($second != null) {
        $temp1 = $first->next;
        $temp2 = $second->next;
        
        $first->next = $second;
        $second->next = $temp1;
        
        $first = $temp1;
        $second = $temp2;
    }
}

// উদাহরণ
$head = createLinkedList([1,2,3,4]);
reorderList($head);
printLinkedList($head); // 1 -> 4 -> 2 -> 3
৪. স্ট্যাক ও কিউ (৬৬-৮০)
সমস্যা ৬৬: Implement Stack using Arrays
php
class Stack {
    private $stack;
    private $top;
    
    public function __construct() {
        $this->stack = [];
        $this->top = -1;
    }
    
    public function push($item) {
        $this->top++;
        $this->stack[$this->top] = $item;
    }
    
    public function pop() {
        if ($this->isEmpty()) {
            return null;
        }
        $item = $this->stack[$this->top];
        $this->top--;
        return $item;
    }
    
    public function peek() {
        if ($this->isEmpty()) {
            return null;
        }
        return $this->stack[$this->top];
    }
    
    public function isEmpty() {
        return $this->top == -1;
    }
    
    public function size() {
        return $this->top + 1;
    }
}

// উদাহরণ
$stack = new Stack();
$stack->push(1);
$stack->push(2);
$stack->push(3);
echo $stack->pop() . "\n"; // 3
echo $stack->peek() . "\n"; // 2
সমস্যা ৬৭: Implement Queue using Arrays
php
class Queue {
    private $queue;
    private $front;
    private $rear;
    
    public function __construct() {
        $this->queue = [];
        $this->front = 0;
        $this->rear = -1;
    }
    
    public function enqueue($item) {
        $this->rear++;
        $this->queue[$this->rear] = $item;
    }
    
    public function dequeue() {
        if ($this->isEmpty()) {
            return null;
        }
        $item = $this->queue[$this->front];
        $this->front++;
        return $item;
    }
    
    public function peek() {
        if ($this->isEmpty()) {
            return null;
        }
        return $this->queue[$this->front];
    }
    
    public function isEmpty() {
        return $this->front > $this->rear;
    }
    
    public function size() {
        return $this->rear - $this->front + 1;
    }
}

// উদাহরণ
$queue = new Queue();
$queue->enqueue(1);
$queue->enqueue(2);
$queue->enqueue(3);
echo $queue->dequeue() . "\n"; // 1
echo $queue->peek() . "\n"; // 2
সমস্যা ৬৮: Implement Stack using Queues
php
class StackUsingQueues {
    private $q1;
    private $q2;
    
    public function __construct() {
        $this->q1 = new Queue();
        $this->q2 = new Queue();
    }
    
    public function push($x) {
        $this->q2->enqueue($x);
        
        while (!$this->q1->isEmpty()) {
            $this->q2->enqueue($this->q1->dequeue());
        }
        
        // swap queues
        $temp = $this->q1;
        $this->q1 = $this->q2;
        $this->q2 = $temp;
    }
    
    public function pop() {
        if ($this->q1->isEmpty()) {
            return null;
        }
        return $this->q1->dequeue();
    }
    
    public function top() {
        if ($this->q1->isEmpty()) {
            return null;
        }
        return $this->q1->peek();
    }
    
    public function empty() {
        return $this->q1->isEmpty();
    }
}
সমস্যা ৬৯: Implement Queue using Stacks
php
class QueueUsingStacks {
    private $stack1;
    private $stack2;
    
    public function __construct() {
        $this->stack1 = new Stack();
        $this->stack2 = new Stack();
    }
    
    public function enqueue($x) {
        $this->stack1->push($x);
    }
    
    public function dequeue() {
        if ($this->stack2->isEmpty()) {
            while (!$this->stack1->isEmpty()) {
                $this->stack2->push($this->stack1->pop());
            }
        }
        
        if ($this->stack2->isEmpty()) {
            return null;
        }
        
        return $this->stack2->pop();
    }
    
    public function peek() {
        if ($this->stack2->isEmpty()) {
            while (!$this->stack1->isEmpty()) {
                $this->stack2->push($this->stack1->pop());
            }
        }
        
        if ($this->stack2->isEmpty()) {
            return null;
        }
        
        return $this->stack2->peek();
    }
    
    public function empty() {
        return $this->stack1->isEmpty() && $this->stack2->isEmpty();
    }
}
সমস্যা ৭০: Min Stack (Minimum element track রাখা)
php
class MinStack {
    private $stack;
    private $minStack;
    
    public function __construct() {
        $this->stack = [];
        $this->minStack = [];
    }
    
    public function push($val) {
        array_push($this->stack, $val);
        
        if (empty($this->minStack) || $val <= $this->getMin()) {
            array_push($this->minStack, $val);
        }
    }
    
    public function pop() {
        if (empty($this->stack)) return;
        
        $val = array_pop($this->stack);
        
        if ($val == $this->getMin()) {
            array_pop($this->minStack);
        }
    }
    
    public function top() {
        return end($this->stack);
    }
    
    public function getMin() {
        return end($this->minStack);
    }
}

// উদাহরণ
$minStack = new MinStack();
$minStack->push(-2);
$minStack->push(0);
$minStack->push(-3);
echo $minStack->getMin() . "\n"; // -3
$minStack->pop();
echo $minStack->top() . "\n"; // 0
echo $minStack->getMin() . "\n"; // -2
সমস্যা ৭১: Valid Parentheses (Stack ব্যবহার করে)
php
function isValidParentheses($s) {
    $stack = [];
    $map = [
        ')' => '(',
        '}' => '{',
        ']' => '['
    ];
    
    for ($i = 0; $i < strlen($s); $i++) {
        $char = $s[$i];
        
        if (in_array($char, ['(', '{', '['])) {
            array_push($stack, $char);
        } else {
            if (empty($stack) || array_pop($stack) != $map[$char]) {
                return false;
            }
        }
    }
    
    return empty($stack);
}

// উদাহরণ
echo isValidParentheses("()[]{}") ? 'true' : 'false'; // true
echo isValidParentheses("([)]") ? 'true' : 'false'; // false
সমস্যা ৭২: Next Greater Element
php
function nextGreaterElement($arr) {
    $result = array_fill(0, count($arr), -1);
    $stack = [];
    
    for ($i = 0; $i < count($arr); $i++) {
        while (!empty($stack) && $arr[$i] > $arr[end($stack)]) {
            $index = array_pop($stack);
            $result[$index] = $arr[$i];
        }
        array_push($stack, $i);
    }
    
    return $result;
}

// উদাহরণ
$arr = [4, 5, 2, 25];
print_r(nextGreaterElement($arr)); // [5, 25, 25, -1]
সমস্যা ৭৩: Daily Temperatures (কত দিন পর temperature বেশি হবে)
php
function dailyTemperatures($temps) {
    $n = count($temps);
    $result = array_fill(0, $n, 0);
    $stack = [];
    
    for ($i = 0; $i < $n; $i++) {
        while (!empty($stack) && $temps[$i] > $temps[end($stack)]) {
            $prevIndex = array_pop($stack);
            $result[$prevIndex] = $i - $prevIndex;
        }
        array_push($stack, $i);
    }
    
    return $result;
}

// উদাহরণ
$temps = [73,74,75,71,69,72,76,73];
print_r(dailyTemperatures($temps)); // [1,1,4,2,1,1,0,0]
সমস্যা ৭৪: Evaluate Reverse Polish Notation
php
function evalRPN($tokens) {
    $stack = [];
    
    foreach ($tokens as $token) {
        if (in_array($token, ['+', '-', '*', '/'])) {
            $b = array_pop($stack);
            $a = array_pop($stack);
            
            switch ($token) {
                case '+':
                    array_push($stack, $a + $b);
                    break;
                case '-':
                    array_push($stack, $a - $b);
                    break;
                case '*':
                    array_push($stack, $a * $b);
                    break;
                case '/':
                    array_push($stack, intval($a / $b));
                    break;
            }
        } else {
            array_push($stack, intval($token));
        }
    }
    
    return array_pop($stack);
}

// উদাহরণ
$tokens = ["2","1","+","3","*"];
echo evalRPN($tokens); // 9 ((2+1)*3)
সমস্যা ৭৫: Backspace String Compare
php
function backspaceCompare($s, $t) {
    return buildString($s) == buildString($t);
}

function buildString($str) {
    $stack = [];
    
    for ($i = 0; $i < strlen($str); $i++) {
        if ($str[$i] == '#') {
            if (!empty($stack)) {
                array_pop($stack);
            }
        } else {
            array_push($stack, $str[$i]);
        }
    }
    
    return implode('', $stack);
}

// উদাহরণ
echo backspaceCompare("ab#c", "ad#c") ? 'true' : 'false'; // true (both become "ac")
সমস্যা ৭৬: Asteroid Collision
php
function asteroidCollision($asteroids) {
    $stack = [];
    
    foreach ($asteroids as $ast) {
        $exploded = false;
        
        while (!empty($stack) && $ast < 0 && end($stack) > 0) {
            if (abs($ast) > end($stack)) {
                array_pop($stack);
                continue;
            } elseif (abs($ast) == end($stack)) {
                array_pop($stack);
                $exploded = true;
                break;
            } else {
                $exploded = true;
                break;
            }
        }
        
        if (!$exploded) {
            array_push($stack, $ast);
        }
    }
    
    return $stack;
}

// উদাহরণ
$asteroids = [5,10,-5];
print_r(asteroidCollision($asteroids)); // [5,10]
সমস্যা ৭৭: Simplify Path
php
function simplifyPath($path) {
    $stack = [];
    $parts = explode('/', $path);
    
    foreach ($parts as $part) {
        if ($part == '' || $part == '.') {
            continue;
        } elseif ($part == '..') {
            if (!empty($stack)) {
                array_pop($stack);
            }
        } else {
            array_push($stack, $part);
        }
    }
    
    return '/' . implode('/', $stack);
}

// উদাহরণ
echo simplifyPath("/home//foo/"); // "/home/foo"
echo simplifyPath("/a/./b/../../c/"); // "/c"
সমস্যা ৭৮: Remove K Digits
php
function removeKdigits($num, $k) {
    $stack = [];
    
    for ($i = 0; $i < strlen($num); $i++) {
        $digit = $num[$i];
        
        while (!empty($stack) && $k > 0 && end($stack) > $digit) {
            array_pop($stack);
            $k--;
        }
        
        array_push($stack, $digit);
    }
    
    // যদি এখনও k বাকি থাকে, তাহলে শেষ থেকে remove করা
    while ($k > 0 && !empty($stack)) {
        array_pop($stack);
        $k--;
    }
    
    // leading zeros বাদ দেওয়া
    $result = ltrim(implode('', $stack), '0');
    
    return empty($result) ? "0" : $result;
}

// উদাহরণ
echo removeKdigits("1432219", 3); // "1219"
সমস্যা ৭৯: Largest Rectangle in Histogram
php
function largestRectangleArea($heights) {
    $stack = [];
    $maxArea = 0;
    $i = 0;
    
    while ($i < count($heights)) {
        if (empty($stack) || $heights[$i] >= $heights[end($stack)]) {
            array_push($stack, $i);
            $i++;
        } else {
            $height = $heights[array_pop($stack)];
            $width = empty($stack) ? $i : $i - end($stack) - 1;
            $maxArea = max($maxArea, $height * $width);
        }
    }
    
    while (!empty($stack)) {
        $height = $heights[array_pop($stack)];
        $width = empty($stack) ? $i : $i - end($stack) - 1;
        $maxArea = max($maxArea, $height * $width);
    }
    
    return $maxArea;
}

// উদাহরণ
$heights = [2,1,5,6,2,3];
echo largestRectangleArea($heights); // 10
সমস্যা ৮০: Sliding Window Maximum
php
function maxSlidingWindow($nums, $k) {
    if (empty($nums) || $k == 0) return [];
    
    $result = [];
    $deque = []; // indices store করা হবে
    
    for ($i = 0; $i < count($nums); $i++) {
        // window এর বাইরে চলে গেলে remove
        while (!empty($deque) && $deque[0] < $i - $k + 1) {
            array_shift($deque);
        }
        
        // ছোট মান গুলো remove করা
        while (!empty($deque) && $nums[end($deque)] < $nums[$i]) {
            array_pop($deque);
        }
        
        array_push($deque, $i);
        
        // result এ যোগ করা
        if ($i >= $k - 1) {
            $result[] = $nums[$deque[0]];
        }
    }
    
    return $result;
}

// উদাহরণ
$nums = [1,3,-1,-3,5,3,6,7];
print_r(maxSlidingWindow($nums, 3)); // [3,3,5,5,6,7]
৫. ট্রি ও গ্রাফ (৮১-৯৫)
প্রথমে Tree Node class ডিফাইন করা যাক:

php
class TreeNode {
    public $val;
    public $left;
    public $right;
    
    public function __construct($val = 0, $left = null, $right = null) {
        $this->val = $val;
        $this->left = $left;
        $this->right = $right;
    }
}
সমস্যা ৮১: Binary Tree Inorder Traversal
php
function inorderTraversal($root) {
    $result = [];
    inorderHelper($root, $result);
    return $result;
}

function inorderHelper($node, &$result) {
    if ($node == null) return;
    
    inorderHelper($node->left, $result);
    $result[] = $node->val;
    inorderHelper($node->right, $result);
}

// উদাহরণ
$root = new TreeNode(1);
$root->right = new TreeNode(2);
$root->right->left = new TreeNode(3);
print_r(inorderTraversal($root)); // [1,3,2]
সমস্যা ৮২: Binary Tree Preorder Traversal
php
function preorderTraversal($root) {
    $result = [];
    preorderHelper($root, $result);
    return $result;
}

function preorderHelper($node, &$result) {
    if ($node == null) return;
    
    $result[] = $node->val;
    preorderHelper($node->left, $result);
    preorderHelper($node->right, $result);
}
সমস্যা ৮৩: Binary Tree Postorder Traversal
php
function postorderTraversal($root) {
    $result = [];
    postorderHelper($root, $result);
    return $result;
}

function postorderHelper($node, &$result) {
    if ($node == null) return;
    
    postorderHelper($node->left, $result);
    postorderHelper($node->right, $result);
    $result[] = $node->val;
}
সমস্যা ৮৪: Level Order Traversal (BFS)
php
function levelOrder($root) {
    if ($root == null) return [];
    
    $result = [];
    $queue = [$root];
    
    while (!empty($queue)) {
        $level = [];
        $levelSize = count($queue);
        
        for ($i = 0; $i < $levelSize; $i++) {
            $node = array_shift($queue);
            $level[] = $node->val;
            
            if ($node->left) array_push($queue, $node->left);
            if ($node->right) array_push($queue, $node->right);
        }
        
        $result[] = $level;
    }
    
    return $result;
}
সমস্যা ৮৫: Maximum Depth of Binary Tree
php
function maxDepth($root) {
    if ($root == null) return 0;
    
    return 1 + max(maxDepth($root->left), maxDepth($root->right));
}

// উদাহরণ
$root = new TreeNode(3);
$root->left = new TreeNode(9);
$root->right = new TreeNode(20);
$root->right->left = new TreeNode(15);
$root->right->right = new TreeNode(7);
echo maxDepth($root); // 3
সমস্যা ৮৬: Validate Binary Search Tree
php
function isValidBST($root) {
    return isValidBSTHelper($root, null, null);
}

function isValidBSTHelper($node, $min, $max) {
    if ($node == null) return true;
    
    if (($min !== null && $node->val <= $min) || 
        ($max !== null && $node->val >= $max)) {
        return false;
    }
    
    return isValidBSTHelper($node->left, $min, $node->val) && 
           isValidBSTHelper($node->right, $node->val, $max);
}
সমস্যা ৮৭: Symmetric Tree
php
function isSymmetric($root) {
    if ($root == null) return true;
    return isMirror($root->left, $root->right);
}

function isMirror($left, $right) {
    if ($left == null && $right == null) return true;
    if ($left == null || $right == null) return false;
    
    return ($left->val == $right->val) &&
           isMirror($left->left, $right->right) &&
           isMirror($left->right, $right->left);
}
সমস্যা ৮৮: Binary Tree Level Order Traversal II (Bottom-up)
php
function levelOrderBottom($root) {
    if ($root == null) return [];
    
    $result = [];
    $queue = [$root];
    
    while (!empty($queue)) {
        $level = [];
        $levelSize = count($queue);
        
        for ($i = 0; $i < $levelSize; $i++) {
            $node = array_shift($queue);
            $level[] = $node->val;
            
            if ($node->left) array_push($queue, $node->left);
            if ($node->right) array_push($queue, $node->right);
        }
        
        array_unshift($result, $level);
    }
    
    return $result;
}
সমস্যা ৮৯: Convert Sorted Array to Binary Search Tree
php
function sortedArrayToBST($nums) {
    return buildBST($nums, 0, count($nums) - 1);
}

function buildBST($nums, $left, $right) {
    if ($left > $right) return null;
    
    $mid = floor(($left + $right) / 2);
    $node = new TreeNode($nums[$mid]);
    
    $node->left = buildBST($nums, $left, $mid - 1);
    $node->right = buildBST($nums, $mid + 1, $right);
    
    return $node;
}
সমস্যা ৯০: Path Sum
php
function hasPathSum($root, $sum) {
    if ($root == null) return false;
    
    if ($root->left == null && $root->right == null) {
        return $sum == $root->val;
    }
    
    return hasPathSum($root->left, $sum - $root->val) ||
           hasPathSum($root->right, $sum - $root->val);
}
সমস্যা ৯১: Lowest Common Ancestor of BST
php
function lowestCommonAncestor($root, $p, $q) {
    if ($root == null) return null;
    
    if ($p->val < $root->val && $q->val < $root->val) {
        return lowestCommonAncestor($root->left, $p, $q);
    }
    
    if ($p->val > $root->val && $q->val > $root->val) {
        return lowestCommonAncestor($root->right, $p, $q);
    }
    
    return $root;
}
সমস্যা ৯২: Binary Tree Right Side View
php
function rightSideView($root) {
    if ($root == null) return [];
    
    $result = [];
    $queue = [$root];
    
    while (!empty($queue)) {
        $levelSize = count($queue);
        
        for ($i = 0; $i < $levelSize; $i++) {
            $node = array_shift($queue);
            
            if ($i == $levelSize - 1) {
                $result[] = $node->val;
            }
            
            if ($node->left) array_push($queue, $node->left);
            if ($node->right) array_push($queue, $node->right);
        }
    }
    
    return $result;
}
সমস্যা ৯৩: Count Complete Tree Nodes
php
function countNodes($root) {
    if ($root == null) return 0;
    
    $leftHeight = getLeftHeight($root);
    $rightHeight = getRightHeight($root);
    
    if ($leftHeight == $rightHeight) {
        return pow(2, $leftHeight) - 1;
    }
    
    return 1 + countNodes($root->left) + countNodes($root->right);
}

function getLeftHeight($node) {
    $height = 0;
    while ($node != null) {
        $height++;
        $node = $node->left;
    }
    return $height;
}

function getRightHeight($node) {
    $height = 0;
    while ($node != null) {
        $height++;
        $node = $node->right;
    }
    return $height;
}
সমস্যা ৯৪: Binary Tree Zigzag Level Order Traversal
php
function zigzagLevelOrder($root) {
    if ($root == null) return [];
    
    $result = [];
    $queue = [$root];
    $leftToRight = true;
    
    while (!empty($queue)) {
        $level = [];
        $levelSize = count($queue);
        
        for ($i = 0; $i < $levelSize; $i++) {
            $node = array_shift($queue);
            
            if ($leftToRight) {
                $level[] = $node->val;
            } else {
                array_unshift($level, $node->val);
            }
            
            if ($node->left) array_push($queue, $node->left);
            if ($node->right) array_push($queue, $node->right);
        }
        
        $result[] = $level;
        $leftToRight = !$leftToRight;
    }
    
    return $result;
}
সমস্যা ৯৫: Serialize and Deserialize Binary Tree
php
class Codec {
    function serialize($root) {
        if ($root == null) return "null";
        
        $left = $this->serialize($root->left);
        $right = $this->serialize($root->right);
        
        return $root->val . "," . $left . "," . $right;
    }
    
    function deserialize($data) {
        $nodes = explode(',', $data);
        return $this->deserializeHelper($nodes);
    }
    
    private function deserializeHelper(&$nodes) {
        $val = array_shift($nodes);
        
        if ($val == "null") return null;
        
        $node = new TreeNode(intval($val));
        $node->left = $this->deserializeHelper($nodes);
        $node->right = $this->deserializeHelper($nodes);
        
        return $node;
    }
}
৬. রিকার্শন ও ব্যাকট্র্যাকিং (৯৬-১১০)
সমস্যা ৯৬: Factorial using Recursion
php
function factorial($n) {
    if ($n <= 1) return 1;
    return $n * factorial($n - 1);
}

// উদাহরণ
echo factorial(5); // 120
সমস্যা ৯৭: Fibonacci using Recursion
php
function fibonacci($n) {
    if ($n <= 1) return $n;
    return fibonacci($n - 1) + fibonacci($n - 2);
}

// উদাহরণ
echo fibonacci(6); // 8
সমস্যা ৯৮: Power of Number using Recursion
php
function power($x, $n) {
    if ($n == 0) return 1;
    if ($n < 0) return 1 / power($x, -$n);
    
    $half = power($x, floor($n / 2));
    
    if ($n % 2 == 0) {
        return $half * $half;
    } else {
        return $x * $half * $half;
    }
}

// উদাহরণ
echo power(2, 10); // 1024
সমস্যা ৯৯: Tower of Hanoi
php
function towerOfHanoi($n, $from, $to, $aux) {
    if ($n == 1) {
        echo "Move disk 1 from $from to $to\n";
        return;
    }
    
    towerOfHanoi($n - 1, $from, $aux, $to);
    echo "Move disk $n from $from to $to\n";
    towerOfHanoi($n - 1, $aux, $to, $from);
}

// উদাহরণ
towerOfHanoi(3, 'A', 'C', 'B');
সমস্যা ১০০: Generate All Subsets (Power Set)
php
function subsets($nums) {
    $result = [];
    backtrackSubsets($nums, 0, [], $result);
    return $result;
}

function backtrackSubsets($nums, $start, $current, &$result) {
    $result[] = $current;
    
    for ($i = $start; $i < count($nums); $i++) {
        $current[] = $nums[$i];
        backtrackSubsets($nums, $i + 1, $current, $result);
        array_pop($current);
    }
}

// উদাহরণ
$nums = [1,2,3];
print_r(subsets($nums));
সমস্যা ১০১: Generate All Permutations
php
function permute($nums) {
    $result = [];
    backtrackPermute($nums, 0, $result);
    return $result;
}

function backtrackPermute(&$nums, $start, &$result) {
    if ($start == count($nums)) {
        $result[] = $nums;
        return;
    }
    
    for ($i = $start; $i < count($nums); $i++) {
        // swap
        $temp = $nums[$start];
        $nums[$start] = $nums[$i];
        $nums[$i] = $temp;
        
        backtrackPermute($nums, $start + 1, $result);
        
        // backtrack (swap back)
        $temp = $nums[$start];
        $nums[$start] = $nums[$i];
        $nums[$i] = $temp;
    }
}

// উদাহরণ
$nums = [1,2,3];
print_r(permute($nums));
সমস্যা ১০২: Combination Sum
php
function combinationSum($candidates, $target) {
    $result = [];
    backtrackCombinationSum($candidates, $target, 0, [], $result);
    return $result;
}

function backtrackCombinationSum($candidates, $remaining, $start, $current, &$result) {
    if ($remaining < 0) return;
    if ($remaining == 0) {
        $result[] = $current;
        return;
    }
    
    for ($i = $start; $i < count($candidates); $i++) {
        $current[] = $candidates[$i];
        backtrackCombinationSum($candidates, $remaining - $candidates[$i], $i, $current, $result);
        array_pop($current);
    }
}

// উদাহরণ
$candidates = [2,3,6,7];
print_r(combinationSum($candidates, 7));
সমস্যা ১০৩: N-Queens Problem
php
function solveNQueens($n) {
    $result = [];
    $board = array_fill(0, $n, array_fill(0, $n, '.'));
    backtrackNQueens($board, 0, $result);
    return $result;
}

function backtrackNQueens(&$board, $row, &$result) {
    if ($row == count($board)) {
        $solution = [];
        foreach ($board as $r) {
            $solution[] = implode('', $r);
        }
        $result[] = $solution;
        return;
    }
    
    for ($col = 0; $col < count($board); $col++) {
        if (isSafe($board, $row, $col)) {
            $board[$row][$col] = 'Q';
            backtrackNQueens($board, $row + 1, $result);
            $board[$row][$col] = '.';
        }
    }
}

function isSafe($board, $row, $col) {
    // same column check
    for ($i = 0; $i < $row; $i++) {
        if ($board[$i][$col] == 'Q') return false;
    }
    
    // upper left diagonal
    for ($i = $row - 1, $j = $col - 1; $i >= 0 && $j >= 0; $i--, $j--) {
        if ($board[$i][$j] == 'Q') return false;
    }
    
    // upper right diagonal
    for ($i = $row - 1, $j = $col + 1; $i >= 0 && $j < count($board); $i--, $j++) {
        if ($board[$i][$j] == 'Q') return false;
    }
    
    return true;
}
সমস্যা ১০৪: Sudoku Solver
php
function solveSudoku(&$board) {
    solveSudokuHelper($board);
}

function solveSudokuHelper(&$board) {
    for ($i = 0; $i < 9; $i++) {
        for ($j = 0; $j < 9; $j++) {
            if ($board[$i][$j] == '.') {
                for ($num = 1; $num <= 9; $num++) {
                    $char = (string)$num;
                    if (isValidMove($board, $i, $j, $char)) {
                        $board[$i][$j] = $char;
                        
                        if (solveSudokuHelper($board)) {
                            return true;
                        }
                        
                        $board[$i][$j] = '.';
                    }
                }
                return false;
            }
        }
    }
    return true;
}

function isValidMove($board, $row, $col, $num) {
    // row check
    for ($j = 0; $j < 9; $j++) {
        if ($board[$row][$j] == $num) return false;
    }
    
    // column check
    for ($i = 0; $i < 9; $i++) {
        if ($board[$i][$col] == $num) return false;
    }
    
    // 3x3 box check
    $boxRow = floor($row / 3) * 3;
    $boxCol = floor($col / 3) * 3;
    
    for ($i = 0; $i < 3; $i++) {
        for ($j = 0; $j < 3; $j++) {
            if ($board[$boxRow + $i][$boxCol + $j] == $num) return false;
        }
    }
    
    return true;
}
সমস্যা ১০৫: Letter Combinations of a Phone Number
php
function letterCombinations($digits) {
    if (empty($digits)) return [];
    
    $phone = [
        '2' => 'abc',
        '3' => 'def',
        '4' => 'ghi',
        '5' => 'jkl',
        '6' => 'mno',
        '7' => 'pqrs',
        '8' => 'tuv',
        '9' => 'wxyz'
    ];
    
    $result = [];
    backtrackLetterCombos($digits, $phone, 0, '', $result);
    return $result;
}

function backtrackLetterCombos($digits, $phone, $index, $current, &$result) {
    if ($index == strlen($digits)) {
        $result[] = $current;
        return;
    }
    
    $letters = $phone[$digits[$index]];
    for ($i = 0; $i < strlen($letters); $i++) {
        backtrackLetterCombos($digits, $phone, $index + 1, $current . $letters[$i], $result);
    }
}

// উদাহরণ
print_r(letterCombinations("23"));
সমস্যা ১০৬: Generate Parentheses
php
function generateParenthesis($n) {
    $result = [];
    backtrackParenthesis($result, '', 0, 0, $n);
    return $result;
}

function backtrackParenthesis(&$result, $current, $open, $close, $max) {
    if (strlen($current) == $max * 2) {
        $result[] = $current;
        return;
    }
    
    if ($open < $max) {
        backtrackParenthesis($result, $current . '(', $open + 1, $close, $max);
    }
    
    if ($close < $open) {
        backtrackParenthesis($result, $current . ')', $open, $close + 1, $max);
    }
}

// উদাহরণ
print_r(generateParenthesis(3));
সমস্যা ১০৭: Palindrome Partitioning
php
function partition($s) {
    $result = [];
    backtrackPartition($s, 0, [], $result);
    return $result;
}

function backtrackPartition($s, $start, $current, &$result) {
    if ($start == strlen($s)) {
        $result[] = $current;
        return;
    }
    
    for ($end = $start; $end < strlen($s); $end++) {
        if (isPalindromeSubstring($s, $start, $end)) {
            $current[] = substr($s, $start, $end - $start + 1);
            backtrackPartition($s, $end + 1, $current, $result);
            array_pop($current);
        }
    }
}

function isPalindromeSubstring($s, $left, $right) {
    while ($left < $right) {
        if ($s[$left] != $s[$right]) return false;
        $left++;
        $right--;
    }
    return true;
}

// উদাহরণ
print_r(partition("aab"));
সমস্যা ১০৮: Word Search
php
function exist($board, $word) {
    for ($i = 0; $i < count($board); $i++) {
        for ($j = 0; $j < count($board[0]); $j++) {
            if (dfsWordSearch($board, $word, $i, $j, 0)) {
                return true;
            }
        }
    }
    return false;
}

function dfsWordSearch(&$board, $word, $i, $j, $index) {
    if ($index == strlen($word)) return true;
    
    if ($i < 0 || $i >= count($board) || $j < 0 || $j >= count($board[0]) || 
        $board[$i][$j] != $word[$index]) {
        return false;
    }
    
    $temp = $board[$i][$j];
    $board[$i][$j] = '#';
    
    $found = dfsWordSearch($board, $word, $i + 1, $j, $index + 1) ||
             dfsWordSearch($board, $word, $i - 1, $j, $index + 1) ||
             dfsWordSearch($board, $word, $i, $j + 1, $index + 1) ||
             dfsWordSearch($board, $word, $i, $j - 1, $index + 1);
    
    $board[$i][$j] = $temp;
    
    return $found;
}

// উদাহরণ
$board = [
    ['A','B','C','E'],
    ['S','F','C','S'],
    ['A','D','E','E']
];
echo exist($board, "ABCCED") ? 'true' : 'false'; // true
সমস্যা ১০৯: Restore IP Addresses
php
function restoreIpAddresses($s) {
    $result = [];
    backtrackIP($s, 0, [], $result);
    return $result;
}

function backtrackIP($s, $start, $current, &$result) {
    if (count($current) == 4) {
        if ($start == strlen($s)) {
            $result[] = implode('.', $current);
        }
        return;
    }
    
    for ($len = 1; $len <= 3; $len++) {
        if ($start + $len > strlen($s)) break;
        
        $part = substr($s, $start, $len);
        
        // leading zero check
        if (strlen($part) > 1 && $part[0] == '0') continue;
        
        // value range check
        if (intval($part) > 255) continue;
        
        $current[] = $part;
        backtrackIP($s, $start + $len, $current, $result);
        array_pop($current);
    }
}

// উদাহরণ
print_r(restoreIpAddresses("25525511135"));
সমস্যা ১১০: Rat in a Maze
php
function ratInAMaze($maze) {
    $n = count($maze);
    $solution = array_fill(0, $n, array_fill(0, $n, 0));
    
    if (solveMaze($maze, 0, 0, $solution)) {
        return $solution;
    }
    
    return null;
}

function solveMaze($maze, $x, $y, &$solution) {
    $n = count($maze);
    
    if ($x == $n - 1 && $y == $n - 1) {
        $solution[$x][$y] = 1;
        return true;
    }
    
    if (isSafeMaze($maze, $x, $y)) {
        $solution[$x][$y] = 1;
        
        // move right
        if (solveMaze($maze, $x + 1, $y, $solution)) {
            return true;
        }
        
        // move down
        if (solveMaze($maze, $x, $y + 1, $solution)) {
            return true;
        }
        
        // backtrack
        $solution[$x][$y] = 0;
        return false;
    }
    
    return false;
}

function isSafeMaze($maze, $x, $y) {
    $n = count($maze);
    return ($x >= 0 && $x < $n && $y >= 0 && $y < $n && $maze[$x][$y] == 1);
}

// উদাহরণ
$maze = [
    [1, 0, 0, 0],
    [1, 1, 0, 1],
    [0, 1, 0, 0],
    [1, 1, 1, 1]
];
print_r(ratInAMaze($maze));
৭. ডায়নামিক প্রোগ্রামিং (১১১-১২৫)
সমস্যা ১১১: Fibonacci using DP (Memoization)
php
function fibDP($n, &$memo = []) {
    if ($n <= 1) return $n;
    
    if (!isset($memo[$n])) {
        $memo[$n] = fibDP($n - 1, $memo) + fibDP($n - 2, $memo);
    }
    
    return $memo[$n];
}

// উদাহরণ
echo fibDP(10); // 55
সমস্যা ১১২: Climbing Stairs
php
function climbStairs($n) {
    if ($n <= 2) return $n;
    
    $dp = [1, 2];
    
    for ($i = 2; $i < $n; $i++) {
        $dp[$i] = $dp[$i - 1] + $dp[$i - 2];
    }
    
    return $dp[$n - 1];
}

// উদাহরণ
echo climbStairs(5); // 8
সমস্যা ১১৩: Coin Change (Minimum Coins)
php
function coinChange($coins, $amount) {
    $dp = array_fill(0, $amount + 1, $amount + 1);
    $dp[0] = 0;
    
    for ($i = 1; $i <= $amount; $i++) {
        foreach ($coins as $coin) {
            if ($coin <= $i) {
                $dp[$i] = min($dp[$i], $dp[$i - $coin] + 1);
            }
        }
    }
    
    return $dp[$amount] > $amount ? -1 : $dp[$amount];
}

// উদাহরণ
$coins = [1,2,5];
echo coinChange($coins, 11); // 3 (5+5+1)
সমস্যা ১১৪: Longest Increasing Subsequence
php
function lengthOfLIS($nums) {
    $n = count($nums);
    if ($n == 0) return 0;
    
    $dp = array_fill(0, $n, 1);
    $maxLen = 1;
    
    for ($i = 1; $i < $n; $i++) {
        for ($j = 0; $j < $i; $j++) {
            if ($nums[$i] > $nums[$j]) {
                $dp[$i] = max($dp[$i], $dp[$j] + 1);
            }
        }
        $maxLen = max($maxLen, $dp[$i]);
    }
    
    return $maxLen;
}

// উদাহরণ
$nums = [10,9,2,5,3,7,101,18];
echo lengthOfLIS($nums); // 4 (2,3,7,101)
সমস্যা ১১৫: 0/1 Knapsack
php
function knapsack($values, $weights, $capacity) {
    $n = count($values);
    $dp = array_fill(0, $n + 1, array_fill(0, $capacity + 1, 0));
    
    for ($i = 1; $i <= $n; $i++) {
        for ($w = 1; $w <= $capacity; $w++) {
            if ($weights[$i - 1] <= $w) {
                $dp[$i][$w] = max(
                    $values[$i - 1] + $dp[$i - 1][$w - $weights[$i - 1]],
                    $dp[$i - 1][$w]
                );
            } else {
                $dp[$i][$w] = $dp[$i - 1][$w];
            }
        }
    }
    
    return $dp[$n][$capacity];
}

// উদাহরণ
$values = [60,100,120];
$weights = [10,20,30];
echo knapsack($values, $weights, 50); // 220
সমস্যা ১১৬: Edit Distance
php
function minDistance($word1, $word2) {
    $m = strlen($word1);
    $n = strlen($word2);
    
    $dp = array_fill(0, $m + 1, array_fill(0, $n + 1, 0));
    
    for ($i = 0; $i <= $m; $i++) {
        $dp[$i][0] = $i;
    }
    
    for ($j = 0; $j <= $n; $j++) {
        $dp[0][$j] = $j;
    }
    
    for ($i = 1; $i <= $m; $i++) {
        for ($j = 1; $j <= $n; $j++) {
            if ($word1[$i - 1] == $word2[$j - 1]) {
                $dp[$i][$j] = $dp[$i - 1][$j - 1];
            } else {
                $dp[$i][$j] = 1 + min(
                    $dp[$i - 1][$j],      // delete
                    $dp[$i][$j - 1],      // insert
                    $dp[$i - 1][$j - 1]   // replace
                );
            }
        }
    }
    
    return $dp[$m][$n];
}

// উদাহরণ
echo minDistance("horse", "ros"); // 3
সমস্যা ১১৭: Longest Common Subsequence
php
function longestCommonSubsequence($text1, $text2) {
    $m = strlen($text1);
    $n = strlen($text2);
    
    $dp = array_fill(0, $m + 1, array_fill(0, $n + 1, 0));
    
    for ($i = 1; $i <= $m; $i++) {
        for ($j = 1; $j <= $n; $j++) {
            if ($text1[$i - 1] == $text2[$j - 1]) {
                $dp[$i][$j] = $dp[$i - 1][$j - 1] + 1;
            } else {
                $dp[$i][$j] = max($dp[$i - 1][$j], $dp[$i][$j - 1]);
            }
        }
    }
    
    return $dp[$m][$n];
}

// উদাহরণ
echo longestCommonSubsequence("abcde", "ace"); // 3
সমস্যা ১১৮: Maximum Product Subarray
php
function maxProductSubarray($nums) {
    $maxSoFar = $minSoFar = $result = $nums[0];
    
    for ($i = 1; $i < count($nums); $i++) {
        $temp = $maxSoFar;
        $maxSoFar = max($nums[$i], $maxSoFar * $nums[$i], $minSoFar * $nums[$i]);
        $minSoFar = min($nums[$i], $temp * $nums[$i], $minSoFar * $nums[$i]);
        $result = max($result, $maxSoFar);
    }
    
    return $result;
}

// উদাহরণ
$nums = [2,3,-2,4];
echo maxProductSubarray($nums); // 6
সমস্যা ১১৯: House Robber
php
function rob($nums) {
    $n = count($nums);
    if ($n == 0) return 0;
    if ($n == 1) return $nums[0];
    
    $dp = [0 => $nums[0], 1 => max($nums[0], $nums[1])];
    
    for ($i = 2; $i < $n; $i++) {
        $dp[$i] = max($dp[$i - 1], $dp[$i - 2] + $nums[$i]);
    }
    
    return $dp[$n - 1];
}

// উদাহরণ
$nums = [1,2,3,1];
echo rob($nums); // 4 (1+3)
সমস্যা ১২০: Unique Paths
php
function uniquePaths($m, $n) {
    $dp = array_fill(0, $m, array_fill(0, $n, 1));
    
    for ($i = 1; $i < $m; $i++) {
        for ($j = 1; $j < $n; $j++) {
            $dp[$i][$j] = $dp[$i - 1][$j] + $dp[$i][$j - 1];
        }
    }
    
    return $dp[$m - 1][$n - 1];
}

// উদাহরণ
echo uniquePaths(3, 7); // 28
সমস্যা ১২১: Minimum Path Sum
php
function minPathSum($grid) {
    $m = count($grid);
    $n = count($grid[0]);
    
    for ($i = 1; $i < $m; $i++) {
        $grid[$i][0] += $grid[$i - 1][0];
    }
    
    for ($j = 1; $j < $n; $j++) {
        $grid[0][$j] += $grid[0][$j - 1];
    }
    
    for ($i = 1; $i < $m; $i++) {
        for ($j = 1; $j < $n; $j++) {
            $grid[$i][$j] += min($grid[$i - 1][$j], $grid[$i][$j - 1]);
        }
    }
    
    return $grid[$m - 1][$n - 1];
}

// উদাহরণ
$grid = [
    [1,3,1],
    [1,5,1],
    [4,2,1]
];
echo minPathSum($grid); // 7
সমস্যা ১২২: Decode Ways
php
function numDecodings($s) {
    if ($s[0] == '0') return 0;
    
    $n = strlen($s);
    $dp = array_fill(0, $n + 1, 0);
    $dp[0] = 1;
    $dp[1] = 1;
    
    for ($i = 2; $i <= $n; $i++) {
        $oneDigit = intval(substr($s, $i - 1, 1));
        $twoDigits = intval(substr($s, $i - 2, 2));
        
        if ($oneDigit >= 1) {
            $dp[$i] += $dp[$i - 1];
        }
        
        if ($twoDigits >= 10 && $twoDigits <= 26) {
            $dp[$i] += $dp[$i - 2];
        }
    }
    
    return $dp[$n];
}

// উদাহরণ
echo numDecodings("226"); // 3 (BZ, VF, BB)
সমস্যা ১২৩: Word Break
php
function wordBreakDP($s, $wordDict) {
    $wordSet = array_flip($wordDict);
    $n = strlen($s);
    $dp = array_fill(0, $n + 1, false);
    $dp[0] = true;
    
    for ($i = 1; $i <= $n; $i++) {
        for ($j = 0; $j < $i; $j++) {
            if ($dp[$j] && isset($wordSet[substr($s, $j, $i - $j)])) {
                $dp[$i] = true;
                break;
            }
        }
    }
    
    return $dp[$n];
}

// উদাহরণ
$s = "leetcode";
$wordDict = ["leet", "code"];
echo wordBreakDP($s, $wordDict) ? 'true' : 'false'; // true
সমস্যা ১২৪: Coin Change 2 (Number of Ways)
php
function change($amount, $coins) {
    $dp = array_fill(0, $amount + 1, 0);
    $dp[0] = 1;
    
    foreach ($coins as $coin) {
        for ($i = $coin; $i <= $amount; $i++) {
            $dp[$i] += $dp[$i - $coin];
        }
    }
    
    return $dp[$amount];
}

// উদাহরণ
$coins = [1,2,5];
echo change(5, $coins); // 4
সমস্যা ১২৫: Partition Equal Subset Sum
php
function canPartition($nums) {
    $sum = array_sum($nums);
    
    if ($sum % 2 != 0) return false;
    
    $target = $sum / 2;
    $dp = array_fill(0, $target + 1, false);
    $dp[0] = true;
    
    foreach ($nums as $num) {
        for ($i = $target; $i >= $num; $i--) {
            if ($dp[$i - $num]) {
                $dp[$i] = true;
            }
        }
    }
    
    return $dp[$target];
}

// উদাহরণ
$nums = [1,5,11,5];
echo canPartition($nums) ? 'true' : 'false'; // true
৮. সর্টিং ও সার্চিং (১২৬-১৪০)
সমস্যা ১২৬: Bubble Sort
php
function bubbleSort(&$arr) {
    $n = count($arr);
    
    for ($i = 0; $i < $n - 1; $i++) {
        $swapped = false;
        
        for ($j = 0; $j < $n - $i - 1; $j++) {
            if ($arr[$j] > $arr[$j + 1]) {
                $temp = $arr[$j];
                $arr[$j] = $arr[$j + 1];
                $arr[$j + 1] = $temp;
                $swapped = true;
            }
        }
        
        if (!$swapped) break;
    }
    
    return $arr;
}

// উদাহরণ
$arr = [64,34,25,12,22,11,90];
print_r(bubbleSort($arr));
সমস্যা ১২৭: Selection Sort
php
function selectionSort(&$arr) {
    $n = count($arr);
    
    for ($i = 0; $i < $n - 1; $i++) {
        $minIndex = $i;
        
        for ($j = $i + 1; $j < $n; $j++) {
            if ($arr[$j] < $arr[$minIndex]) {
                $minIndex = $j;
            }
        }
        
        if ($minIndex != $i) {
            $temp = $arr[$i];
            $arr[$i] = $arr[$minIndex];
            $arr[$minIndex] = $temp;
        }
    }
    
    return $arr;
}
সমস্যা ১২৮: Insertion Sort
php
function insertionSort(&$arr) {
    $n = count($arr);
    
    for ($i = 1; $i < $n; $i++) {
        $key = $arr[$i];
        $j = $i - 1;
        
        while ($j >= 0 && $arr[$j] > $key) {
            $arr[$j + 1] = $arr[$j];
            $j--;
        }
        
        $arr[$j + 1] = $key;
    }
    
    return $arr;
}
সমস্যা ১২৯: Merge Sort
php
function mergeSort(&$arr) {
    $n = count($arr);
    if ($n <= 1) return $arr;
    
    $mid = floor($n / 2);
    $left = array_slice($arr, 0, $mid);
    $right = array_slice($arr, $mid);
    
    mergeSort($left);
    mergeSort($right);
    
    merge($arr, $left, $right);
    return $arr;
}

function merge(&$arr, $left, $right) {
    $i = $j = $k = 0;
    
    while ($i < count($left) && $j < count($right)) {
        if ($left[$i] <= $right[$j]) {
            $arr[$k++] = $left[$i++];
        } else {
            $arr[$k++] = $right[$j++];
        }
    }
    
    while ($i < count($left)) {
        $arr[$k++] = $left[$i++];
    }
    
    while ($j < count($right)) {
        $arr[$k++] = $right[$j++];
    }
}
সমস্যা ১৩০: Quick Sort
php
function quickSort(&$arr, $low, $high) {
    if ($low < $high) {
        $pi = partition($arr, $low, $high);
        quickSort($arr, $low, $pi - 1);
        quickSort($arr, $pi + 1, $high);
    }
    return $arr;
}

function partition(&$arr, $low, $high) {
    $pivot = $arr[$high];
    $i = $low - 1;
    
    for ($j = $low; $j < $high; $j++) {
        if ($arr[$j] <= $pivot) {
            $i++;
            $temp = $arr[$i];
            $arr[$i] = $arr[$j];
            $arr[$j] = $temp;
        }
    }
    
    $temp = $arr[$i + 1];
    $arr[$i + 1] = $arr[$high];
    $arr[$high] = $temp;
    
    return $i + 1;
}
সমস্যা ১৩১: Heap Sort
php
function heapSort(&$arr) {
    $n = count($arr);
    
    // build heap
    for ($i = floor($n / 2) - 1; $i >= 0; $i--) {
        heapify($arr, $n, $i);
    }
    
    // extract elements from heap
    for ($i = $n - 1; $i > 0; $i--) {
        $temp = $arr[0];
        $arr[0] = $arr[$i];
        $arr[$i] = $temp;
        
        heapify($arr, $i, 0);
    }
    
    return $arr;
}

function heapify(&$arr, $n, $i) {
    $largest = $i;
    $left = 2 * $i + 1;
    $right = 2 * $i + 2;
    
    if ($left < $n && $arr[$left] > $arr[$largest]) {
        $largest = $left;
    }
    
    if ($right < $n && $arr[$right] > $arr[$largest]) {
        $largest = $right;
    }
    
    if ($largest != $i) {
        $temp = $arr[$i];
        $arr[$i] = $arr[$largest];
        $arr[$largest] = $temp;
        
        heapify($arr, $n, $largest);
    }
}
সমস্যা ১৩২: Binary Search (Iterative)
php
function binarySearch($arr, $target) {
    $left = 0;
    $right = count($arr) - 1;
    
    while ($left <= $right) {
        $mid = floor(($left + $right) / 2);
        
        if ($arr[$mid] == $target) {
            return $mid;
        }
        
        if ($arr[$mid] < $target) {
            $left = $mid + 1;
        } else {
            $right = $mid - 1;
        }
    }
    
    return -1;
}

// উদাহরণ
$arr = [1,2,3,4,5,6,7,8,9];
echo binarySearch($arr, 5); // 4
সমস্যা ১৩৩: Binary Search (Recursive)
php
function binarySearchRecursive($arr, $target, $left, $right) {
    if ($left > $right) return -1;
    
    $mid = floor(($left + $right) / 2);
    
    if ($arr[$mid] == $target) return $mid;
    
    if ($arr[$mid] < $target) {
        return binarySearchRecursive($arr, $target, $mid + 1, $right);
    } else {
        return binarySearchRecursive($arr, $target, $left, $mid - 1);
    }
}
সমস্যা ১৩৪: First Occurrence in Sorted Array
php
function firstOccurrence($arr, $target) {
    $left = 0;
    $right = count($arr) - 1;
    $result = -1;
    
    while ($left <= $right) {
        $mid = floor(($left + $right) / 2);
        
        if ($arr[$mid] == $target) {
            $result = $mid;
            $right = $mid - 1; // বাম পাশে আরও খুঁজি
        } elseif ($arr[$mid] < $target) {
            $left = $mid + 1;
        } else {
            $right = $mid - 1;
        }
    }
    
    return $result;
}

// উদাহরণ
$arr = [1,2,3,3,3,4,5];
echo firstOccurrence($arr, 3); // 2
সমস্যা ১৩৫: Last Occurrence in Sorted Array
php
function lastOccurrence($arr, $target) {
    $left = 0;
    $right = count($arr) - 1;
    $result = -1;
    
    while ($left <= $right) {
        $mid = floor(($left + $right) / 2);
        
        if ($arr[$mid] == $target) {
            $result = $mid;
            $left = $mid + 1; // ডান পাশে আরও খুঁজি
        } elseif ($arr[$mid] < $target) {
            $left = $mid + 1;
        } else {
            $right = $mid - 1;
        }
    }
    
    return $result;
}

// উদাহরণ
$arr = [1,2,3,3,3,4,5];
echo lastOccurrence($arr, 3); // 4
সমস্যা ১৩৬: Search in Rotated Sorted Array
php
function searchRotated($nums, $target) {
    $left = 0;
    $right = count($nums) - 1;
    
    while ($left <= $right) {
        $mid = floor(($left + $right) / 2);
        
        if ($nums[$mid] == $target) return $mid;
        
        // left half is sorted
        if ($nums[$left] <= $nums[$mid]) {
            if ($target >= $nums[$left] && $target < $nums[$mid]) {
                $right = $mid - 1;
            } else {
                $left = $mid + 1;
            }
        } 
        // right half is sorted
        else {
            if ($target > $nums[$mid] && $target <= $nums[$right]) {
                $left = $mid + 1;
            } else {
                $right = $mid - 1;
            }
        }
    }
    
    return -1;
}

// উদাহরণ
$nums = [4,5,6,7,0,1,2];
echo searchRotated($nums, 0); // 4
সমস্যা ১৩৭: Find Peak Element
php
function findPeakElement($nums) {
    $left = 0;
    $right = count($nums) - 1;
    
    while ($left < $right) {
        $mid = floor(($left + $right) / 2);
        
        if ($nums[$mid] > $nums[$mid + 1]) {
            $right = $mid;
        } else {
            $left = $mid + 1;
        }
    }
    
    return $left;
}

// উদাহরণ
$nums = [1,2,1,3,5,6,4];
echo findPeakElement($nums); // 5 (index of 6)
সমস্যা ১৩৮: Search a 2D Matrix
php
function searchMatrix($matrix, $target) {
    if (empty($matrix) || empty($matrix[0])) return false;
    
    $m = count($matrix);
    $n = count($matrix[0]);
    
    $left = 0;
    $right = $m * $n - 1;
    
    while ($left <= $right) {
        $mid = floor(($left + $right) / 2);
        $row = floor($mid / $n);
        $col = $mid % $n;
        
        if ($matrix[$row][$col] == $target) return true;
        
        if ($matrix[$row][$col] < $target) {
            $left = $mid + 1;
        } else {
            $right = $mid - 1;
        }
    }
    
    return false;
}

// উদাহরণ
$matrix = [
    [1,3,5,7],
    [10,11,16,20],
    [23,30,34,60]
];
echo searchMatrix($matrix, 3) ? 'true' : 'false'; // true
সমস্যা ১৩৯: Kth Smallest Element in Sorted Matrix
php
function kthSmallest($matrix, $k) {
    $n = count($matrix);
    $left = $matrix[0][0];
    $right = $matrix[$n - 1][$n - 1];
    
    while ($left < $right) {
        $mid = floor(($left + $right) / 2);
        $count = countLessEqual($matrix, $mid);
        
        if ($count < $k) {
            $left = $mid + 1;
        } else {
            $right = $mid;
        }
    }
    
    return $left;
}

function countLessEqual($matrix, $target) {
    $count = 0;
    $n = count($matrix);
    $row = $n - 1;
    $col = 0;
    
    while ($row >= 0 && $col < $n) {
        if ($matrix[$row][$col] <= $target) {
            $count += $row + 1;
            $col++;
        } else {
            $row--;
        }
    }
    
    return $count;
}

// উদাহরণ
$matrix = [
    [1,5,9],
    [10,11,13],
    [12,13,15]
];
echo kthSmallest($matrix, 8); // 13
সমস্যা ১৪০: Median of Two Sorted Arrays
php
function findMedianSortedArrays($nums1, $nums2) {
    if (count($nums1) > count($nums2)) {
        return findMedianSortedArrays($nums2, $nums1);
    }
    
    $m = count($nums1);
    $n = count($nums2);
    $left = 0;
    $right = $m;
    
    while ($left <= $right) {
        $partition1 = floor(($left + $right) / 2);
        $partition2 = floor(($m + $n + 1) / 2) - $partition1;
        
        $maxLeft1 = ($partition1 == 0) ? PHP_INT_MIN : $nums1[$partition1 - 1];
        $minRight1 = ($partition1 == $m) ? PHP_INT_MAX : $nums1[$partition1];
        
        $maxLeft2 = ($partition2 == 0) ? PHP_INT_MIN : $nums2[$partition2 - 1];
        $minRight2 = ($partition2 == $n) ? PHP_INT_MAX : $nums2[$partition2];
        
        if ($maxLeft1 <= $minRight2 && $maxLeft2 <= $minRight1) {
            if (($m + $n) % 2 == 0) {
                return (max($maxLeft1, $maxLeft2) + min($minRight1, $minRight2)) / 2;
            } else {
                return max($maxLeft1, $maxLeft2);
            }
        } elseif ($maxLeft1 > $minRight2) {
            $right = $partition1 - 1;
        } else {
            $left = $partition1 + 1;
        }
    }
    
    return 0;
}

// উদাহরণ
$nums1 = [1,3];
$nums2 = [2];
echo findMedianSortedArrays($nums1, $nums2); // 2
৯. ম্যাথ ও নাম্বার থিওরি (১৪১-১৫৫)
সমস্যা ১৪১: Prime Number Check
php
function isPrime($n) {
    if ($n <= 1) return false;
    if ($n <= 3) return true;
    if ($n % 2 == 0 || $n % 3 == 0) return false;
    
    for ($i = 5; $i * $i <= $n; $i += 6) {
        if ($n % $i == 0 || $n % ($i + 2) == 0) return false;
    }
    
    return true;
}

// উদাহরণ
echo isPrime(17) ? 'true' : 'false'; // true
সমস্যা ১৪২: Sieve of Eratosthenes (Find all primes up to n)
php
function sieveOfEratosthenes($n) {
    $isPrime = array_fill(0, $n + 1, true);
    $isPrime[0] = $isPrime[1] = false;
    
    for ($i = 2; $i * $i <= $n; $i++) {
        if ($isPrime[$i]) {
            for ($j = $i * $i; $j <= $n; $j += $i) {
                $isPrime[$j] = false;
            }
        }
    }
    
    $primes = [];
    for ($i = 2; $i <= $n; $i++) {
        if ($isPrime[$i]) {
            $primes[] = $i;
        }
    }
    
    return $primes;
}

// উদাহরণ
print_r(sieveOfEratosthenes(30));
সমস্যা ১৪৩: GCD (Greatest Common Divisor)
php
function gcd($a, $b) {
    while ($b != 0) {
        $temp = $b;
        $b = $a % $b;
        $a = $temp;
    }
    return $a;
}

// উদাহরণ
echo gcd(48, 18); // 6
সমস্যা ১৪৪: LCM (Least Common Multiple)
php
function lcm($a, $b) {
    return ($a * $b) / gcd($a, $b);
}

// উদাহরণ
echo lcm(12, 18); // 36
সমস্যা ১৪৫: Factorial (Non-recursive)
php
function factorialIterative($n) {
    $result = 1;
    for ($i = 2; $i <= $n; $i++) {
        $result *= $i;
    }
    return $result;
}

// উদাহরণ
echo factorialIterative(5); // 120
সমস্যা ১৪৬: Trailing Zeroes in Factorial
php
function trailingZeroes($n) {
    $count = 0;
    
    for ($i = 5; $i <= $n; $i *= 5) {
        $count += floor($n / $i);
    }
    
    return $count;
}

// উদাহরণ
echo trailingZeroes(25); // 6
সমস্যা ১৪৭: Power Function
php
function powerIterative($x, $n) {
    $result = 1;
    $base = $x;
    $exponent = $n;
    
    if ($exponent < 0) {
        $base = 1 / $base;
        $exponent = -$exponent;
    }
    
    while ($exponent > 0) {
        if ($exponent % 2 == 1) {
            $result *= $base;
        }
        $base *= $base;
        $exponent = floor($exponent / 2);
    }
    
    return $result;
}

// উদাহরণ
echo powerIterative(2, 10); // 1024
সমস্যা ১৪৮: Fibonacci (Iterative)
php
function fibonacciIterative($n) {
    if ($n <= 1) return $n;
    
    $a = 0;
    $b = 1;
    
    for ($i = 2; $i <= $n; $i++) {
        $c = $a + $b;
        $a = $b;
        $b = $c;
    }
    
    return $b;
}

// উদাহরণ
echo fibonacciIterative(10); // 55
সমস্যা ১৪৯: Happy Number
php
function isHappy($n) {
    $seen = [];
    
    while ($n != 1 && !isset($seen[$n])) {
        $seen[$n] = true;
        $n = sumOfSquares($n);
    }
    
    return $n == 1;
}

function sumOfSquares($n) {
    $sum = 0;
    while ($n > 0) {
        $digit = $n % 10;
        $sum += $digit * $digit;
        $n = floor($n / 10);
    }
    return $sum;
}

// উদাহরণ
echo isHappy(19) ? 'true' : 'false'; // true
সমস্যা ১৫০: Ugly Number
php
function isUgly($n) {
    if ($n <= 0) return false;
    
    foreach ([2,3,5] as $prime) {
        while ($n % $prime == 0) {
            $n /= $prime;
        }
    }
    
    return $n == 1;
}

// উদাহরণ
echo isUgly(14) ? 'true' : 'false'; // false
সমস্যা ১৫১: Count Primes
php
function countPrimes($n) {
    if ($n < 2) return 0;
    
    $isPrime = array_fill(0, $n, true);
    $isPrime[0] = $isPrime[1] = false;
    
    for ($i = 2; $i * $i < $n; $i++) {
        if ($isPrime[$i]) {
            for ($j = $i * $i; $j < $n; $j += $i) {
                $isPrime[$j] = false;
            }
        }
    }
    
    return count(array_filter($isPrime));
}

// উদাহরণ
echo countPrimes(10); // 4 (2,3,5,7)
সমস্যা ১৫২: Perfect Number
php
function checkPerfectNumber($num) {
    if ($num <= 1) return false;
    
    $sum = 1;
    for ($i = 2; $i * $i <= $num; $i++) {
        if ($num % $i == 0) {
            $sum += $i;
            if ($i != $num / $i) {
                $sum += $num / $i;
            }
        }
    }
    
    return $sum == $num;
}

// উদাহরণ
echo checkPerfectNumber(28) ? 'true' : 'false'; // true (1+2+4+7+14=28)
সমস্যা ১৫৩: Roman to Integer
php
function romanToInt($s) {
    $values = [
        'I' => 1,
        'V' => 5,
        'X' => 10,
        'L' => 50,
        'C' => 100,
        'D' => 500,
        'M' => 1000
    ];
    
    $total = 0;
    $prev = 0;
    
    for ($i = strlen($s) - 1; $i >= 0; $i--) {
        $current = $values[$s[$i]];
        
        if ($current < $prev) {
            $total -= $current;
        } else {
            $total += $current;
        }
        
        $prev = $current;
    }
    
    return $total;
}

// উদাহরণ
echo romanToInt("MCMXCIV"); // 1994
সমস্যা ১৫৪: Integer to Roman
php
function intToRoman($num) {
    $values = [1000,900,500,400,100,90,50,40,10,9,5,4,1];
    $symbols = ["M","CM","D","CD","C","XC","L","XL","X","IX","V","IV","I"];
    
    $result = "";
    
    for ($i = 0; $i < count($values); $i++) {
        while ($num >= $values[$i]) {
            $result .= $symbols[$i];
            $num -= $values[$i];
        }
    }
    
    return $result;
}

// উদাহরণ
echo intToRoman(1994); // "MCMXCIV"
সমস্যা ১৫৫: Excel Sheet Column Title
php
function convertToTitle($columnNumber) {
    $result = "";
    
    while ($columnNumber > 0) {
        $columnNumber--;
        $result = chr(65 + $columnNumber % 26) . $result;
        $columnNumber = floor($columnNumber / 26);
    }
    
    return $result;
}

// উদাহরণ
echo convertToTitle(701); // "ZY"
১০. ম্যাট্রিক্স (১৫৬-১৭০)
সমস্যা ১৫৬: Spiral Matrix
php
function spiralOrder($matrix) {
    if (empty($matrix)) return [];
    
    $result = [];
    $top = 0;
    $bottom = count($matrix) - 1;
    $left = 0;
    $right = count($matrix[0]) - 1;
    
    while ($top <= $bottom && $left <= $right) {
        // top row
        for ($i = $left; $i <= $right; $i++) {
            $result[] = $matrix[$top][$i];
        }
        $top++;
        
        // right column
        for ($i = $top; $i <= $bottom; $i++) {
            $result[] = $matrix[$i][$right];
        }
        $right--;
        
        if ($top <= $bottom) {
            // bottom row
            for ($i = $right; $i >= $left; $i--) {
                $result[] = $matrix[$bottom][$i];
            }
            $bottom--;
        }
        
        if ($left <= $right) {
            // left column
            for ($i = $bottom; $i >= $top; $i--) {
                $result[] = $matrix[$i][$left];
            }
            $left++;
        }
    }
    
    return $result;
}

// উদাহরণ
$matrix = [
    [1,2,3],
    [4,5,6],
    [7,8,9]
];
print_r(spiralOrder($matrix));
সমস্যা ১৫৭: Rotate Image (90 degrees clockwise)
php
function rotate(&$matrix) {
    $n = count($matrix);
    
    // transpose
    for ($i = 0; $i < $n; $i++) {
        for ($j = $i + 1; $j < $n; $j++) {
            $temp = $matrix[$i][$j];
            $matrix[$i][$j] = $matrix[$j][$i];
            $matrix[$j][$i] = $temp;
        }
    }
    
    // reverse each row
    for ($i = 0; $i < $n; $i++) {
        $matrix[$i] = array_reverse($matrix[$i]);
    }
    
    return $matrix;
}

// উদাহরণ
$matrix = [
    [1,2,3],
    [4,5,6],
    [7,8,9]
];
print_r(rotate($matrix));
সমস্যা ১৫৮: Set Matrix Zeroes
php
function setZeroes(&$matrix) {
    $m = count($matrix);
    $n = count($matrix[0]);
    
    $firstRowZero = false;
    $firstColZero = false;
    
    // check first row
    for ($j = 0; $j < $n; $j++) {
        if ($matrix[0][$j] == 0) {
            $firstRowZero = true;
            break;
        }
    }
    
    // check first column
    for ($i = 0; $i < $m; $i++) {
        if ($matrix[$i][0] == 0) {
            $firstColZero = true;
            break;
        }
    }
    
    // mark zeros on first row and column
    for ($i = 1; $i < $m; $i++) {
        for ($j = 1; $j < $n; $j++) {
            if ($matrix[$i][$j] == 0) {
                $matrix[$i][0] = 0;
                $matrix[0][$j] = 0;
            }
        }
    }
    
    // set zeros based on marks
    for ($i = 1; $i < $m; $i++) {
        for ($j = 1; $j < $n; $j++) {
            if ($matrix[$i][0] == 0 || $matrix[0][$j] == 0) {
                $matrix[$i][$j] = 0;
            }
        }
    }
    
    // set first row to zero
    if ($firstRowZero) {
        for ($j = 0; $j < $n; $j++) {
            $matrix[0][$j] = 0;
        }
    }
    
    // set first column to zero
    if ($firstColZero) {
        for ($i = 0; $i < $m; $i++) {
            $matrix[$i][0] = 0;
        }
    }
    
    return $matrix;
}
সমস্যা ১৫৯: Search a 2D Matrix II
php
function searchMatrixII($matrix, $target) {
    if (empty($matrix)) return false;
    
    $row = 0;
    $col = count($matrix[0]) - 1;
    
    while ($row < count($matrix) && $col >= 0) {
        if ($matrix[$row][$col] == $target) {
            return true;
        } elseif ($matrix[$row][$col] > $target) {
            $col--;
        } else {
            $row++;
        }
    }
    
    return false;
}

// উদাহরণ
$matrix = [
    [1,4,7,11,15],
    [2,5,8,12,19],
    [3,6,9,16,22],
    [10,13,14,17,24],
    [18,21,23,26,30]
];
echo searchMatrixII($matrix, 5) ? 'true' : 'false'; // true
সমস্যা ১৬০: Transpose Matrix
php
function transpose($matrix) {
    $m = count($matrix);
    $n = count($matrix[0]);
    
    $result = array_fill(0, $n, array_fill(0, $m, 0));
    
    for ($i = 0; $i < $m; $i++) {
        for ($j = 0; $j < $n; $j++) {
            $result[$j][$i] = $matrix[$i][$j];
        }
    }
    
    return $result;
}

// উদাহরণ
$matrix = [
    [1,2,3],
    [4,5,6]
];
print_r(transpose($matrix));
সমস্যা ১৬১: Matrix Diagonal Sum
php
function diagonalSum($mat) {
    $n = count($mat);
    $sum = 0;
    
    for ($i = 0; $i < $n; $i++) {
        $sum += $mat[$i][$i]; // primary diagonal
        $sum += $mat[$i][$n - 1 - $i]; // secondary diagonal
    }
    
    // middle element counted twice, subtract if n is odd
    if ($n % 2 == 1) {
        $sum -= $mat[floor($n / 2)][floor($n / 2)];
    }
    
    return $sum;
}

// উদাহরণ
$mat = [
    [1,2,3],
    [4,5,6],
    [7,8,9]
];
echo diagonalSum($mat); // 25
সমস্যা ১৬২: Island Perimeter
php
function islandPerimeter($grid) {
    $perimeter = 0;
    $m = count($grid);
    $n = count($grid[0]);
    
    for ($i = 0; $i < $m; $i++) {
        for ($j = 0; $j < $n; $j++) {
            if ($grid[$i][$j] == 1) {
                $perimeter += 4;
                
                // check up
                if ($i > 0 && $grid[$i - 1][$j] == 1) $perimeter -= 2;
                // check left
                if ($j > 0 && $grid[$i][$j - 1] == 1) $perimeter -= 2;
            }
        }
    }
    
    return $perimeter;
}

// উদাহরণ
$grid = [
    [0,1,0,0],
    [1,1,1,0],
    [0,1,0,0],
    [1,1,0,0]
];
echo islandPerimeter($grid); // 16
সমস্যা ১৬৩: Flood Fill
php
function floodFill($image, $sr, $sc, $newColor) {
    $originalColor = $image[$sr][$sc];
    if ($originalColor == $newColor) return $image;
    
    dfsFloodFill($image, $sr, $sc, $originalColor, $newColor);
    return $image;
}

function dfsFloodFill(&$image, $i, $j, $originalColor, $newColor) {
    if ($i < 0 || $i >= count($image) || $j < 0 || $j >= count($image[0]) || 
        $image[$i][$j] != $originalColor) {
        return;
    }
    
    $image[$i][$j] = $newColor;
    
    dfsFloodFill($image, $i + 1, $j, $originalColor, $newColor);
    dfsFloodFill($image, $i - 1, $j, $originalColor, $newColor);
    dfsFloodFill($image, $i, $j + 1, $originalColor, $newColor);
    dfsFloodFill($image, $i, $j - 1, $originalColor, $newColor);
}
সমস্যা ১৬৪: Rotting Oranges
php
function orangesRotting($grid) {
    $m = count($grid);
    $n = count($grid[0]);
    $queue = [];
    $fresh = 0;
    
    for ($i = 0; $i < $m; $i++) {
        for ($j = 0; $j < $n; $j++) {
            if ($grid[$i][$j] == 2) {
                array_push($queue, [$i, $j, 0]);
            } elseif ($grid[$i][$j] == 1) {
                $fresh++;
            }
        }
    }
    
    if ($fresh == 0) return 0;
    
    $dirs = [[1,0], [-1,0], [0,1], [0,-1]];
    $minutes = 0;
    
    while (!empty($queue)) {
        list($x, $y, $time) = array_shift($queue);
        $minutes = max($minutes, $time);
        
        foreach ($dirs as $dir) {
            $nx = $x + $dir[0];
            $ny = $y + $dir[1];
            
            if ($nx >= 0 && $nx < $m && $ny >= 0 && $ny < $n && $grid[$nx][$ny] == 1) {
                $grid[$nx][$ny] = 2;
                $fresh--;
                array_push($queue, [$nx, $ny, $time + 1]);
            }
        }
    }
    
    return $fresh == 0 ? $minutes : -1;
}

// উদাহরণ
$grid = [
    [2,1,1],
    [1,1,0],
    [0,1,1]
];
echo orangesRotting($grid); // 4
সমস্যা ১৬৫: Number of Islands
php
function numIslands($grid) {
    if (empty($grid)) return 0;
    
    $count = 0;
    $m = count($grid);
    $n = count($grid[0]);
    
    for ($i = 0; $i < $m; $i++) {
        for ($j = 0; $j < $n; $j++) {
            if ($grid[$i][$j] == '1') {
                $count++;
                dfsIsland($grid, $i, $j);
            }
        }
    }
    
    return $count;
}

function dfsIsland(&$grid, $i, $j) {
    if ($i < 0 || $i >= count($grid) || $j < 0 || $j >= count($grid[0]) || 
        $grid[$i][$j] != '1') {
        return;
    }
    
    $grid[$i][$j] = '0';
    
    dfsIsland($grid, $i + 1, $j);
    dfsIsland($grid, $i - 1, $j);
    dfsIsland($grid, $i, $j + 1);
    dfsIsland($grid, $i, $j - 1);
}

// উদাহরণ
$grid = [
    ['1','1','1','1','0'],
    ['1','1','0','1','0'],
    ['1','1','0','0','0'],
    ['0','0','0','0','0']
];
echo numIslands($grid); // 1
সমস্যা ১৬৬: Max Area of Island
php
function maxAreaOfIsland($grid) {
    $maxArea = 0;
    $m = count($grid);
    $n = count($grid[0]);
    
    for ($i = 0; $i < $m; $i++) {
        for ($j = 0; $j < $n; $j++) {
            if ($grid[$i][$j] == 1) {
                $area = dfsArea($grid, $i, $j);
                $maxArea = max($maxArea, $area);
            }
        }
    }
    
    return $maxArea;
}

function dfsArea(&$grid, $i, $j) {
    if ($i < 0 || $i >= count($grid) || $j < 0 || $j >= count($grid[0]) || 
        $grid[$i][$j] != 1) {
        return 0;
    }
    
    $grid[$i][$j] = 0;
    
    return 1 + dfsArea($grid, $i + 1, $j) +
               dfsArea($grid, $i - 1, $j) +
               dfsArea($grid, $i, $j + 1) +
               dfsArea($grid, $i, $j - 1);
}
সমস্যা ১৬৭: Surrounded Regions
php
function solve(&$board) {
    if (empty($board)) return;
    
    $m = count($board);
    $n = count($board[0]);
    
    // mark border-connected 'O's
    for ($i = 0; $i < $m; $i++) {
        if ($board[$i][0] == 'O') dfsBorder($board, $i, 0);
        if ($board[$i][$n - 1] == 'O') dfsBorder($board, $i, $n - 1);
    }
    
    for ($j = 0; $j < $n; $j++) {
        if ($board[0][$j] == 'O') dfsBorder($board, 0, $j);
        if ($board[$m - 1][$j] == 'O') dfsBorder($board, $m - 1, $j);
    }
    
    // flip remaining 'O' to 'X' and border-marked to 'O'
    for ($i = 0; $i < $m; $i++) {
        for ($j = 0; $j < $n; $j++) {
            if ($board[$i][$j] == 'O') {
                $board[$i][$j] = 'X';
            } elseif ($board[$i][$j] == '#') {
                $board[$i][$j] = 'O';
            }
        }
    }
    
    return $board;
}

function dfsBorder(&$board, $i, $j) {
    if ($i < 0 || $i >= count($board) || $j < 0 || $j >= count($board[0]) || 
        $board[$i][$j] != 'O') {
        return;
    }
    
    $board[$i][$j] = '#';
    
    dfsBorder($board, $i + 1, $j);
    dfsBorder($board, $i - 1, $j);
    dfsBorder($board, $i, $j + 1);
    dfsBorder($board, $i, $j - 1);
}
সমস্যা ১৬৮: Word Search in Matrix
php
function existWord($board, $word) {
    for ($i = 0; $i < count($board); $i++) {
        for ($j = 0; $j < count($board[0]); $j++) {
            if (dfsWordSearch($board, $word, $i, $j, 0)) {
                return true;
            }
        }
    }
    return false;
}
সমস্যা ১৬৯: Beautiful Arrangement (Backtracking)
php
function countArrangement($n) {
    $visited = array_fill(1, $n, false);
    return backtrackArrangement($n, 1, $visited);
}

function backtrackArrangement($n, $pos, &$visited) {
    if ($pos > $n) return 1;
    
    $count = 0;
    for ($i = 1; $i <= $n; $i++) {
        if (!$visited[$i] && ($i % $pos == 0 || $pos % $i == 0)) {
            $visited[$i] = true;
            $count += backtrackArrangement($n, $pos + 1, $visited);
            $visited[$i] = false;
        }
    }
    
    return $count;
}
সমস্যা ১৭০: Combination Sum IV
php
function combinationSum4($nums, $target) {
    $dp = array_fill(0, $target + 1, 0);
    $dp[0] = 1;
    
    for ($i = 1; $i <= $target; $i++) {
        foreach ($nums as $num) {
            if ($i >= $num) {
                $dp[$i] += $dp[$i - $num];
            }
        }
    }
    
    return $dp[$target];
}
১১. হ্যাশিং (১৭১-১৮০)
সমস্যা ১৭১: Two Sum using Hash Map
php
function twoSumHash($nums, $target) {
    $map = [];
    
    foreach ($nums as $i => $num) {
        $complement = $target - $num;
        
        if (isset($map[$complement])) {
            return [$map[$complement], $i];
        }
        
        $map[$num] = $i;
    }
    
    return [];
}
সমস্যা ১৭২: First Repeating Character
php
function firstRepeatingChar($str) {
    $seen = [];
    
    for ($i = 0; $i < strlen($str); $i++) {
        $char = $str[$i];
        
        if (isset($seen[$char])) {
            return $char;
        }
        
        $seen[$char] = true;
    }
    
    return null;
}

// উদাহরণ
echo firstRepeatingChar("abcdefghija"); // 'a'
সমস্যা ১৭৩: Count Frequency of Elements
php
function countFrequency($arr) {
    $freq = [];
    
    foreach ($arr as $num) {
        $freq[$num] = ($freq[$num] ?? 0) + 1;
    }
    
    return $freq;
}

// উদাহরণ
$arr = [1,2,2,3,3,3,4];
print_r(countFrequency($arr));
সমস্যা ১৭৪: Intersection of Two Arrays
php
function intersection($nums1, $nums2) {
    $set1 = array_flip($nums1);
    $result = [];
    
    foreach ($nums2 as $num) {
        if (isset($set1[$num]) && !in_array($num, $result)) {
            $result[] = $num;
        }
    }
    
    return $result;
}

// উদাহরণ
$nums1 = [1,2,2,1];
$nums2 = [2,2];
print_r(intersection($nums1, $nums2)); // [2]
সমস্যা ১৭৫: Jewels and Stones
php
function numJewelsInStones($jewels, $stones) {
    $jewelSet = array_flip(str_split($jewels));
    $count = 0;
    
    for ($i = 0; $i < strlen($stones); $i++) {
        if (isset($jewelSet[$stones[$i]])) {
            $count++;
        }
    }
    
    return $count;
}

// উদাহরণ
echo numJewelsInStones("aA", "aAAbbbb"); // 3
সমস্যা ১৭৬: Subarray Sum Equals K (with Hash Map)
php
function subarraySumHash($nums, $k) {
    $count = 0;
    $sum = 0;
    $sumMap = [0 => 1];
    
    foreach ($nums as $num) {
        $sum += $num;
        
        if (isset($sumMap[$sum - $k])) {
            $count += $sumMap[$sum - $k];
        }
        
        $sumMap[$sum] = ($sumMap[$sum] ?? 0) + 1;
    }
    
    return $count;
}
সমস্যা ১৭৭: Longest Consecutive Sequence
php
function longestConsecutive($nums) {
    $numSet = array_flip($nums);
    $longest = 0;
    
    foreach ($nums as $num) {
        if (!isset($numSet[$num - 1])) {
            $currentNum = $num;
            $currentStreak = 1;
            
            while (isset($numSet[$currentNum + 1])) {
                $currentNum++;
                $currentStreak++;
            }
            
            $longest = max($longest, $currentStreak);
        }
    }
    
    return $longest;
}

// উদাহরণ
$nums = [100,4,200,1,3,2];
echo longestConsecutive($nums); // 4
সমস্যা ১৭৮: Top K Frequent Elements
php
function topKFrequent($nums, $k) {
    $freq = [];
    
    foreach ($nums as $num) {
        $freq[$num] = ($freq[$num] ?? 0) + 1;
    }
    
    arsort($freq);
    
    return array_slice(array_keys($freq), 0, $k);
}

// উদাহরণ
$nums = [1,1,1,2,2,3];
print_r(topKFrequent($nums, 2)); // [1,2]
সমস্যা ১৭৯: Group Anagrams (with Hash Map)
php
function groupAnagramsHash($strs) {
    $map = [];
    
    foreach ($strs as $str) {
        $chars = str_split($str);
        sort($chars);
        $key = implode('', $chars);
        
        $map[$key][] = $str;
    }
    
    return array_values($map);
}
সমস্যা ১৮০: Isomorphic Strings
php
function isIsomorphic($s, $t) {
    if (strlen($s) != strlen($t)) return false;
    
    $mapST = [];
    $mapTS = [];
    
    for ($i = 0; $i < strlen($s); $i++) {
        $charS = $s[$i];
        $charT = $t[$i];
        
        if (isset($mapST[$charS]) && $mapST[$charS] != $charT) {
            return false;
        }
        
        if (isset($mapTS[$charT]) && $mapTS[$charT] != $charS) {
            return false;
        }
        
        $mapST[$charS] = $charT;
        $mapTS[$charT] = $charS;
    }
    
    return true;
}

// উদাহরণ
echo isIsomorphic("egg", "add") ? 'true' : 'false'; // true
১২. বিট ম্যানিপুলেশন (১৮১-১৯০)
সমস্যা ১৮১: Check if number is power of two
php
function isPowerOfTwo($n) {
    if ($n <= 0) return false;
    return ($n & ($n - 1)) == 0;
}

// উদাহরণ
echo isPowerOfTwo(16) ? 'true' : 'false'; // true
সমস্যা ১৮২: Count Set Bits (Hamming Weight)
php
function countSetBits($n) {
    $count = 0;
    
    while ($n > 0) {
        $count += $n & 1;
        $n >>= 1;
    }
    
    return $count;
}

// উদাহরণ
echo countSetBits(13); // 3 (1101)
সমস্যা ১৮৩: Single Number (Find element appearing once)
php
function singleNumber($nums) {
    $result = 0;
    
    foreach ($nums as $num) {
        $result ^= $num;
    }
    
    return $result;
}

// উদাহরণ
$nums = [4,1,2,1,2];
echo singleNumber($nums); // 4
সমস্যা ১৮৪: Reverse Bits
php
function reverseBits($n) {
    $result = 0;
    
    for ($i = 0; $i < 32; $i++) {
        $result <<= 1;
        $result |= ($n & 1);
        $n >>= 1;
    }
    
    return $result;
}

// উদাহরণ
echo reverseBits(43261596); // 964176192
সমস্যা ১৮৫: Missing Number (using XOR)
php
function missingNumberXOR($nums) {
    $n = count($nums);
    $xor = $n;
    
    for ($i = 0; $i < $n; $i++) {
        $xor ^= $i ^ $nums[$i];
    }
    
    return $xor;
}
সমস্যা ১৮৬: Sum of Two Integers (without + operator)
php
function getSum($a, $b) {
    while ($b != 0) {
        $carry = $a & $b;
        $a = $a ^ $b;
        $b = $carry << 1;
    }
    
    return $a;
}

// উদাহরণ
echo getSum(5, 3); // 8
সমস্যা ১৮৭: Find the Difference
php
function findTheDifference($s, $t) {
    $result = 0;
    
    for ($i = 0; $i < strlen($s); $i++) {
        $result ^= ord($s[$i]);
    }
    
    for ($i = 0; $i < strlen($t); $i++) {
        $result ^= ord($t[$i]);
    }
    
    return chr($result);
}

// উদাহরণ
echo findTheDifference("abcd", "abcde"); // 'e'
সমস্যা ১৮৮: Power of Four
php
function isPowerOfFour($n) {
    if ($n <= 0) return false;
    
    // power of two and the only set bit at odd position
    return ($n & ($n - 1)) == 0 && ($n & 0xAAAAAAAA) == 0;
}
সমস্যা ১৮৯: Binary Watch
php
function readBinaryWatch($turnedOn) {
    $result = [];
    
    for ($h = 0; $h < 12; $h++) {
        for ($m = 0; $m < 60; $m++) {
            if (countSetBits($h) + countSetBits($m) == $turnedOn) {
                $result[] = sprintf("%d:%02d", $h, $m);
            }
        }
    }
    
    return $result;
}
সমস্যা ১৯০: Bitwise AND of Numbers Range
php
function rangeBitwiseAnd($left, $right) {
    $shift = 0;
    
    while ($left < $right) {
        $left >>= 1;
        $right >>= 1;
        $shift++;
    }
    
    return $left << $shift;
}

// উদাহরণ
echo rangeBitwiseAnd(5, 7); // 4
১৩. স্লাইডিং উইন্ডো (১৯১-২০০)
সমস্যা ১৯১: Maximum Average Subarray I
php
function findMaxAverage($nums, $k) {
    $sum = 0;
    
    for ($i = 0; $i < $k; $i++) {
        $sum += $nums[$i];
    }
    
    $maxSum = $sum;
    
    for ($i = $k; $i < count($nums); $i++) {
        $sum = $sum - $nums[$i - $k] + $nums[$i];
        $maxSum = max($maxSum, $sum);
    }
    
    return $maxSum / $k;
}

// উদাহরণ
$nums = [1,12,-5,-6,50,3];
echo findMaxAverage($nums, 4); // 12.75
সমস্যা ১৯২: Minimum Size Subarray Sum
php
function minSubArrayLen($target, $nums) {
    $left = 0;
    $sum = 0;
    $minLen = PHP_INT_MAX;
    
    for ($right = 0; $right < count($nums); $right++) {
        $sum += $nums[$right];
        
        while ($sum >= $target) {
            $minLen = min($minLen, $right - $left + 1);
            $sum -= $nums[$left];
            $left++;
        }
    }
    
    return $minLen == PHP_INT_MAX ? 0 : $minLen;
}

// উদাহরণ
$nums = [2,3,1,2,4,3];
echo minSubArrayLen(7, $nums); // 2
সমস্যা ১৯৩: Longest Substring Without Repeating Characters (Sliding Window)
php
function lengthOfLongestSubstringSliding($s) {
    $charMap = [];
    $left = 0;
    $maxLength = 0;
    
    for ($right = 0; $right < strlen($s); $right++) {
        $char = $s[$right];
        
        if (isset($charMap[$char]) && $charMap[$char] >= $left) {
            $left = $charMap[$char] + 1;
        }
        
        $charMap[$char] = $right;
        $maxLength = max($maxLength, $right - $left + 1);
    }
    
    return $maxLength;
}
সমস্যা ১৯৪: Permutation in String
php
function checkInclusion($s1, $s2) {
    if (strlen($s1) > strlen($s2)) return false;
    
    $count1 = array_fill(0, 26, 0);
    $count2 = array_fill(0, 26, 0);
    
    for ($i = 0; $i < strlen($s1); $i++) {
        $count1[ord($s1[$i]) - ord('a')]++;
        $count2[ord($s2[$i]) - ord('a')]++;
    }
    
    for ($i = 0; $i <= strlen($s2) - strlen($s1); $i++) {
        if ($count1 == $count2) return true;
        
        if ($i < strlen($s2) - strlen($s1)) {
            $count2[ord($s2[$i]) - ord('a')]--;
            $count2[ord($s2[$i + strlen($s1)]) - ord('a')]++;
        }
    }
    
    return false;
}

// উদাহরণ
echo checkInclusion("ab", "eidbaooo") ? 'true' : 'false'; // true
সমস্যা ১৯৫: Find All Anagrams in a String
php
function findAnagrams($s, $p) {
    $result = [];
    if (strlen($s) < strlen($p)) return $result;
    
    $pCount = array_fill(0, 26, 0);
    $sCount = array_fill(0, 26, 0);
    
    for ($i = 0; $i < strlen($p); $i++) {
        $pCount[ord($p[$i]) - ord('a')]++;
        $sCount[ord($s[$i]) - ord('a')]++;
    }
    
    for ($i = 0; $i <= strlen($s) - strlen($p); $i++) {
        if ($pCount == $sCount) {
            $result[] = $i;
        }
        
        if ($i < strlen($s) - strlen($p)) {
            $sCount[ord($s[$i]) - ord('a')]--;
            $sCount[ord($s[$i + strlen($p)]) - ord('a')]++;
        }
    }
    
    return $result;
}

// উদাহরণ
$s = "cbaebabacd";
$p = "abc";
print_r(findAnagrams($s, $p)); // [0,6]
সমস্যা ১৯৬: Max Consecutive Ones III
php
function longestOnes($nums, $k) {
    $left = 0;
    $zeroCount = 0;
    $maxLen = 0;
    
    for ($right = 0; $right < count($nums); $right++) {
        if ($nums[$right] == 0) {
            $zeroCount++;
        }
        
        while ($zeroCount > $k) {
            if ($nums[$left] == 0) {
                $zeroCount--;
            }
            $left++;
        }
        
        $maxLen = max($maxLen, $right - $left + 1);
    }
    
    return $maxLen;
}

// উদাহরণ
$nums = [1,1,1,0,0,0,1,1,1,1,0];
echo longestOnes($nums, 2); // 6
সমস্যা ১৯৭: Fruit Into Baskets
php
function totalFruit($fruits) {
    $basket = [];
    $left = 0;
    $maxFruits = 0;
    
    for ($right = 0; $right < count($fruits); $right++) {
        $fruit = $fruits[$right];
        $basket[$fruit] = ($basket[$fruit] ?? 0) + 1;
        
        while (count($basket) > 2) {
            $leftFruit = $fruits[$left];
            $basket[$leftFruit]--;
            
            if ($basket[$leftFruit] == 0) {
                unset($basket[$leftFruit]);
            }
            
            $left++;
        }
        
        $maxFruits = max($maxFruits, $right - $left + 1);
    }
    
    return $maxFruits;
}

// উদাহরণ
$fruits = [1,2,3,2,2];
echo totalFruit($fruits); // 4
সমস্যা ১৯৮: Longest Repeating Character Replacement
php
function characterReplacement($s, $k) {
    $count = array_fill(0, 26, 0);
    $left = 0;
    $maxCount = 0;
    $maxLength = 0;
    
    for ($right = 0; $right < strlen($s); $right++) {
        $index = ord($s[$right]) - ord('A');
        $count[$index]++;
        $maxCount = max($maxCount, $count[$index]);
        
        while ($right - $left + 1 - $maxCount > $k) {
            $count[ord($s[$left]) - ord('A')]--;
            $left++;
        }
        
        $maxLength = max($maxLength, $right - $left + 1);
    }
    
    return $maxLength;
}

// উদাহরণ
echo characterReplacement("AABABBA", 1); // 4
সমস্যা ১৯৯: Minimum Window Substring (Sliding Window)
php
function minWindowSliding($s, $t) {
    if (empty($s) || empty($t)) return "";
    
    $need = [];
    for ($i = 0; $i < strlen($t); $i++) {
        $need[$t[$i]] = ($need[$t[$i]] ?? 0) + 1;
    }
    
    $have = [];
    $left = 0;
    $minLen = PHP_INT_MAX;
    $minStart = 0;
    $required = count($need);
    $formed = 0;
    
    for ($right = 0; $right < strlen($s); $right++) {
        $char = $s[$right];
        $have[$char] = ($have[$char] ?? 0) + 1;
        
        if (isset($need[$char]) && $have[$char] == $need[$char]) {
            $formed++;
        }
        
        while ($formed == $required && $left <= $right) {
            if ($right - $left + 1 < $minLen) {
                $minLen = $right - $left + 1;
                $minStart = $left;
            }
            
            $leftChar = $s[$left];
            $have[$leftChar]--;
            
            if (isset($need[$leftChar]) && $have[$leftChar] < $need[$leftChar]) {
                $formed--;
            }
            
            $left++;
        }
    }
    
    return $minLen == PHP_INT_MAX ? "" : substr($s, $minStart, $minLen);
}
সমস্যা ২০০: Sliding Window Maximum (Deque)
php
function maxSlidingWindowDeque($nums, $k) {
    if (empty($nums) || $k == 0) return [];
    
    $result = [];
    $deque = []; // indices
    
    for ($i = 0; $i < count($nums); $i++) {
        // remove out of window indices
        while (!empty($deque) && $deque[0] < $i - $k + 1) {
            array_shift($deque);
        }
        
        // remove smaller values from back
        while (!empty($deque) && $nums[end($deque)] < $nums[$i]) {
            array_pop($deque);
        }
        
        array_push($deque, $i);
        
        if ($i >= $k - 1) {
            $result[] = $nums[$deque[0]];
        }
    }
    
    return $result;
}
উপসংহার
এই ২০০টি DSA সমস্যা ও সমাধান PHP-তে বিভিন্ন ধরণের অ্যালগরিদম এবং ডাটা স্ট্রাকচার কভার করে। প্রতিটি সমস্যার সমাধান বুঝে পড়ুন, নিজে নিজে কোড লিখে প্র্যাকটিস করুন, এবং প্রয়োজনে কাস্টমাইজ করে দেখুন।

প্র্যাকটিস করার টিপস:

প্রথমে সমস্যাটি ভালোভাবে বুঝুন

নিজে চেষ্টা করুন সমাধান বের করতে

সমাধান দেখে বুঝুন এবং বিশ্লেষণ করুন

টাইম কমপ্লেক্সিটি এবং স্পেস কমপ্লেক্সিটি বিশ্লেষণ করুন

ভিন্ন ভিন্ন পদ্ধতিতে সমাধান করার চেষ্টা করুন

নিয়মিত প্র্যাকটিস করুন

শুভ কামনা! 🚀

