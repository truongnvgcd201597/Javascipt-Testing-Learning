### Example 1:
```
export function findMaxI(numberList) {
    if(!Array.isArray(numberList) || numberList.length === 0) return undefined;
    let max = numberList[0];
    for (const highCheck in numberList) {
        if (numberList[highCheck] > max) max = numberList[highCheck];
    }
    return max;
}
console.log(findMaxI([1,2,3,4,6,7,10]));
```
