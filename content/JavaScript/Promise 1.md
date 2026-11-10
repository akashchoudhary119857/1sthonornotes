Let's turn this into an easy-to-follow note with visuals to make it more engaging. 
Means a type of statement which we had passed on 
### Stages of a Promise

A promise in JavaScript can be in one of three states, similar to real-life scenarios:

1. **Pending:** The initial state, neither fulfilled nor rejected (waiting stage).
    
2. **Fulfilled:** The operation completed successfully (resolved).
    
3. **Rejected:** The operation failed (rejected).
    

### Syntax to Create a Promise

To create a promise, use the following syntax:

javascript

```
let prom = new Promise(function(resolve, reject){
  if(condition){
    resolve("Success!");
  } else {
    reject("Failure!");
  }
});
```

### Handling Promise Outcomes

Use the `then` method to handle fulfillment and the `catch` method to handle rejection:

javascript

```
let onFulfill = (result) => {
  console.log(result);
}

let onReject = (error) => {
  console.log(error);
}

prom.then(onFulfill);
prom.catch(onReject);
```

You can pass custom messages to the `resolve` and `reject` functions, which will be processed by the callback methods:

- **Resolved:** Outputs "Success!" if the condition is met.
    
- **Rejected:** Outputs "Failure!" if the condition is not met.
    

This structure allows your code to handle asynchronous operations more gracefully and efficiently.

Lets understand with an example:
```
<script>
  let complete = true;
  let prom = new Promise(function(resolve, reject){
  console.log("waiting");
  if(complete){
  resolve("I am done....");
  }
  else{
  reject("I an quit.........");
  }
  });
  console.log(prom);
</script>
```
Changes this to a function:
<script>
function prom(complete){
return new Promise( function (resolve, reject){
 if(complete){
  resolve("I am done....");
  }
  else{
  reject("I an quit.........");
  }
});
}
console.log(prom(true/false));
</script>
now introducing our call backs for some automation process of promises which really makes our coding behavior more adaptive

