---
title: Async/Await 
subTitle: How to Make a Promise the right way
category: "nodejs"
cover: trumpphoto1.jpg
---

Async/await is a better, and currently the best way to write promises in Javascript, thus very useful when writing Node JS apps.

![unsplash.com](./trumpphoto1.jpg)

### What is a Promise
A promise in Javascript is well, an actual promise that program will execute a function or a method after some other function or method is executed. For example: Parents make a promise to their child that they will buy him a toy if he get a good grade from a test.

The Promise has 3 states:
1. **Pending**: Time from when the promise was made to the time it is fulfilled
2. **Resolved**: Child Gets the promised toy
3. **Rejected**: Child got a bad grade so, no toy

```javascript
const parentsPromise = {
    toy: 'Lego'
}
const goodGrade = true;

const newToyAs = async () => { //Make a Promise
   try{ //Pending
       const grade = await console.log(goodGrade); //Resolved 
       const toy = await console.log(parentsPromise.toy); //Resolved 
    }  
    catch(e){ //If Bad Grade - Rejected
        const bad = new Error('Grade is lower then expected');
        console.log(bad);
}
}
newToyAs() //Prints True and Lego in the console, Parents have bought him a toy.
```

Let’s look at the real world example shall we?

The real world example will be a call to external currency exchange api [fixer.io](https://fixer.io/) using 3rd party library [axios](https://www.npmjs.com/package/axios) for the job.

```javascript
const axios = require('axios');

const getExchangeRate = async (from, to) => { //Promise
    try{
    const response = await axios.get('http://data.fixer.io/api/latest?access_key=5ff2c9aab39f450a57b1033e48f95da5'); 
    
      console.log(response.data.rates[to]); //Resolved
    }
    catch (e){ //Rejected
        throw new Error(`Unable to get country from: ${from} and ${to}`);
        
    }
}

getExchangeRate('EUR', 'USD'); //1.196596
```

Promises are one of the key concepts of building APIs and knowing promises will certainly make your life easier, also, healthier.

Thanks for reading. I hope Promises are a bit simpler to you now.

Feel free to comment and say your feelings about this article.
