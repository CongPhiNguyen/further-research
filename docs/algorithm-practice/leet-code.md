# Leetocode solution

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
