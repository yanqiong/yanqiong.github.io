---
layout: post
title:  "快速排序"
date:   2016-4-29 14:00:00 +0800
categories: web css scss
---

```
function quickSort(items, left, right) {

    var index;

    if (items.length > 1) {

        left = typeof left != "number" ? 0 : left;
        right = typeof right != "number" ? items.length - 1 : right;

        index = partition(items, left, right);

        if (left < index - 1) {
            quickSort(items, left, index - 1);
        }

        if (index < right) {
            quickSort(items, index, right);
        }

    }

    return items;
}

// first call
var result = quickSort(items);
```


```
var sort = function() {
    var quickSort = function(arr) {
        var left = [];
        var right = [];

        if (!$.isArray(arr)) {
            return "input is not an array";
        }

        if (arr.length <= 1) return arr;

        var pivot = arr[0];
        arr.shift();
        for (var i = 0; i < arr.length; i++) {
            arr[i] <= pivot ? left.push(arr[i]) : right.push(arr[i]);
        }
        return $.merge($.merge(quickSort(left), $.makeArray(pivot)), quickSort(right));
    };

    return {
        quickSort: quickSort
    };
}();
```

```
Array.prototype.quick_sort = function() {
	var len = this.length;
	if (len <= 1)
		return this.slice(0);
	var left = [];
	var right = [];
	var mid = [this[0]];
	for (var i = 1; i < len; i++)
		if (this[i] < mid[0])
			left.push(this[i]);
		else
			right.push(this[i]);
	return left.quick_sort().concat(mid.concat(right.quick_sort()));
};
```

