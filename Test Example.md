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
#### Test:
```
import { traverse } from '@babel/core';
import {findMaxI} from './main.js';

describe('Find Max', () => {
    test('find maximum value in array', () => {
        expect(findMaxI([2, 6, 10, 14])).toBe(14);
    });

    test('should be return undefined when array is empty', () => {
        expect(findMaxI([])).toBe(undefined);
    });
});
```
### Result:
![Test Case Figure](https://scontent.fdad1-1.fna.fbcdn.net/v/t1.15752-9/274223070_541378713914458_492510680962055482_n.png?_nc_cat=103&ccb=1-5&_nc_sid=ae9488&_nc_ohc=M5uVwH6iRBEAX8sP2Sf&_nc_ht=scontent.fdad1-1.fna&oh=03_AVKe4Rd5_6EnFm5JqCOrzSdjNFr0xbnmniLVheArvN1HqA&oe=625AB2A7)
