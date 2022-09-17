# Leetcode solution

## Leetcode 387(Ez)

```js
var firstUniqChar = function (s) {
  for (const [index, c] of s.split("").entries()) {
    if (s.indexOf(c) === s.lastIndexOf(c)) {
      return index;
    }
  }
  return -1;
};
```

## Leetcode 2351(Ez)

```js
var repeatedCharacter = function (s) {
  let s1 = new Set();
  for (const c of s) {
    if (s1.has(c)) return c;
    else s1.add(c);
  }
};
```

## Leetcode 540(Medium)

```js
var singleNonDuplicate = function (nums) {
  let res = 0;
  for (const num of nums) {
    res ^= num;
  }
  return res;
};
```

## Leetcode 2255(Ez)

```js
var countPrefixes = function (words, s) {
  let res = 0;
  for (const word of words) {
    if (s.indexOf(word) === 0) res++;
  }
  return res;
};
```

## Leetcode 2357

```js
var minimumOperations = function (nums) {
  let s = new Set();
  for (const num of nums) {
    s.add(num);
  }
  return s.size > 0 ? (s.has(0) ? s.size - 1 : s.size) : 0;
};
```

## Leetcode 1122(Ez)

```js
var relativeSortArray = function (arr1, arr2) {
  let searchObject = {};
  for (let i = 0; i < arr2.length; i++) {
    searchObject[arr2[i]] = i;
  }
  arr1.sort((a, b) => {
    if (searchObject[a] !== undefined && searchObject[b] !== undefined)
      return searchObject[a] - searchObject[b];
    else if (searchObject[a]) return -1;
    else if (searchObject[b]) return 1;
    else return a - b;
  });
  return arr1;
};
```

## Leetcode 151(Medium)

```js
var reverseWords = function (s) {
  return s
    .trim()
    .split(" ")
    .filter((value) => value !== "")
    .reverse()
    .join(" ");
};
```

## Leetcode 292(Ez)

```js
var canWinNim = function (n) {
  return n % 4 !== 0;
};
```

## Leetcode 1512(Ez)

```js
var numIdenticalPairs = function (nums) {
  let objectCount = {};
  for (const num of nums) {
    if (objectCount[num] !== undefined) {
      objectCount[num]++;
    } else objectCount[num] = 1;
  }
  let res = 0;
  let vals = Object.values(objectCount);
  for (let i = 0; i < vals.length; i++) {
    res += (vals[i] * (vals[i] - 1)) / 2;
  }
  return res;
};
```

## Leetcode 2053 (Ez)

- Faster than 5%, bị lặp ở những giá trị bằng nhau vẫn thực hiện tìm index

```js
let arrHandle = arr.filter(
  (value) => arr.indexOf(value) === arr.lastIndexOf(value)
);
console.log(arrHandle);
return arrHandle.length >= k ? arrHandle[k - 1] : "";
```

- Object count faster. Faster than 70%

```js
var kthDistinct = function (arr, k) {
  let objectCount = {};
  for (let i = 0; i < arr.length; i++) {
    if (!objectCount[arr[i]]) objectCount[arr[i]] = 1;
    else objectCount[arr[i]] = 2;
  }
  let index = k;
  console.log("objectCount", objectCount);
  for (let key of Object.keys(objectCount)) {
    if (objectCount[key] == 1) {
      index--;
    }
    if (index == 0) return key;
  }
  return "";
};
```

## Leetcode 2085

```js
let renderObjectCount = (arr) => {
  let objectCount = {};
  for (let i = 0; i < arr.length; i++) {
    if (!objectCount[arr[i]]) objectCount[arr[i]] = 1;
    else objectCount[arr[i]] = 2;
  }
  return objectCount;
};

var countWords = function (words1, words2) {
  let res = 0;

  let o1 = renderObjectCount(words1);
  let o2 = renderObjectCount(words2);

  for (let key of Object.keys(o1)) {
    if (o1[key] === 1 && o2[key] === 1) {
      res++;
    }
  }

  return res;
};
```

## Leetcode 884

- Faster than 15%

```js
var uncommonFromSentences = function (s1, s2) {
  let compoundArr = [...s1.split(" "), ...s2.split(" ")];
  let objectCount = {};
  for (let i = 0; i < compoundArr.length; i++) {
    if (!objectCount[compoundArr[i]]) objectCount[compoundArr[i]] = 1;
    else objectCount[compoundArr[i]] = 2;
  }
  return compoundArr.filter((val) => objectCount[val] === 1);
};
```
