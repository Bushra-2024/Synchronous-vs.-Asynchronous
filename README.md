# Synchronous-vs.-Asynchronous

![image](https://github.com/user-attachments/assets/80f6ae21-7d11-48d0-b9ed-ce9e0374fb75)

## First, look at the picture to better understand synchronization and asynchronous concepts.
![image](https://github.com/user-attachments/assets/d5c1bb4e-071f-4310-bcd9-ad78896f0737)

---
- **Synchronous code** runs line by line, waiting for each line to finish before moving to the next one. It’s like an inline process where the program can't move forward until the current line has been completed.

**Example (Synchronous):**


![image](https://github.com/user-attachments/assets/1906391e-aff3-4f2b-b939-5ae6aaf682fb)


![image](https://github.com/user-attachments/assets/6b7e8941-6484-4533-9774-9f40e5f9f5ad)



- **Asynchronous code** does not wait. It moves to the next line while the async task works in the background. Async code is like a method that runs in the background (with callbacks), and once it finishes, the callback is executed.

**Example (Asynchronous):**


![image](https://github.com/user-attachments/assets/2a11e2ff-6c76-4750-936d-57713cf59412)



In **synchronous** execution, each step waits for the previous one to complete. In **asynchronous** execution, the program continues running while it waits for an operation (like a setTimeout or a network request) to finish. 


**Synchronous Execution Process:**  
1. Executes the first line.  
2. Waits for it to complete before moving to the next line.

**Asynchronous Execution Process:**  
1. Executes the first line.  
2. Moves to the next line without waiting.  
3. The callback of the async task runs once the task completes.

---


### setTimeout

- **`setTimeout()`** is a JavaScript function that lets you delay the execution of some code by a specified amount of time (in milliseconds). 
- It **takes two parameters**:
  - **Logic**: The function to execute after the delay.
  - **Time**: The amount of time (in milliseconds) to wait before executing the logic.

**Example:**
```js
console.log("Start");

setTimeout(() => {
  console.log("This happens after 2 seconds");
}, 2000); // 2000 ms = 2 seconds

console.log("End");
```

- In this example, the `setTimeout()` function waits for 2 seconds before printing "This happens after 2 seconds.
- **`setTimeout()`** is asynchronous because it does not block the execution of other code. As you can see, "End" is printed immediately after "Start," and then, after the specified delay, the message inside `setTimeout` is printed.

- **`setTimeout()`** only executes **once** after the specified delay.

---

### setInterval

- **`setInterval()`** is similar to `setTimeout()` but instead of running once, it executes the provided code repeatedly at the specified interval (every few milliseconds).
  
**Example:**
```js
let timeDisplay = document.createElement("div")
timeDisplay.classList.add("timeDisplay")

document.body.appendChild(timeDisplay);

setInterval(() => {
    const now = new Date();
    timeDisplay.innerHTML = now.toLocaleString()
  }, 1000);
```

- In this case, "This is happening every 1 second" will be printed every 1 second.
  
---

**Asynchronous in JavaScript** can be written in three ways: **Callback**, **Promise**, and **Async/Await**.

### **1. Callback**

- **Asynchronous callbacks** are functions that are passed to another function. The other function starts executing some code in the background, and once that background task finishes, the callback function is called. It’s a way of notifying the program that the task is complete and passing any result (data) back to the original function.

**Example (Callback):**
```js
function fetchData(callback) {
  console.log("Fetching data...");
  
  setTimeout(() => {
    console.log("Data fetched!");
    callback("Here is your data");
  }, 2000);
}

function handleData(data) {
  console.log("Callback received data:", data);
}

fetchData(handleData);
```
**Explanation:**
- The function `fetchData` starts fetching data in the background (simulated with `setTimeout`).
- While it waits, it moves to the next line.
- Once the background task finishes (2 seconds later), it calls the `handleData` function, passing the fetched data to it.

**Output:**
```
Fetching data...
Data fetched!
Callback received data: Here is your data
```

In **Callback** style, the program doesn't stop. It continues to run while waiting for the background task (like fetching data) to finish. Once the background task is complete, the callback function is called to handle the result.



Here’s the refined explanation with the details you've provided:

---

**2. Asynchronous in JavaScript: Callback, Promise, Async/Await**

In JavaScript, there are three main ways to handle asynchronous code: **Callback**, **Promise**, and **Async/Await**.

---

### **Callback**

- **Asynchronous callbacks** are functions that are passed to another function and executed after the background task completes. This allows the program to continue running other code without waiting for the background task to finish.
  
- For example, imagine you’re calling a function to fetch data, but instead of waiting for it to finish, you provide a callback function to be executed once the data is fetched.

**Explanation in Simple Terms:**  
Think of a callback like setting an alarm. You go do other things, and when the time is up, the alarm goes off to let you know it’s done.

**Example (Callback):**
```js
function fetchData(callback) {
  setTimeout(() => {
    console.log("Data fetched!");
    callback();  // Callback called after task finishes
  }, 2000);
}

console.log("Start");
fetchData(() => {
  console.log("Callback executed!");
});
console.log("End");
```

**Output:**
```
Start
End
Data fetched!
Callback executed!
```

---

### **Promise**

- A **Promise** represents a value that will be available in the future. It has three states:  
  - **Pending:** The promise is still waiting for the task to complete.  
  - **Fulfilled:** The task is complete, and the promise has been resolved.  
  - **Rejected:** The task failed, and the promise has been rejected.

- A promise accepts a **callback function** with two parameters: `resolve` (if the task completes successfully) and `reject` (if the task fails).

**Explanation in Simple Terms:**  
A promise is like placing an order at a restaurant. The restaurant tells you the food will be ready soon, but you don’t know when. When the food is ready, they either deliver it (resolved) or say it couldn’t be made (rejected).

**Example (Promise):**
```js
let myPromise = new Promise((resolve, reject) => {
  let success = true;
  
  if (success) {
    resolve("Task completed!");
  } else {
    reject("Task failed.");
  }
});

myPromise
  .then(result => {
    console.log(result);  // Handle success
  })
  .catch(error => {
    console.error(error);  // Handle error
  });
```

**Explanation:**
- **then**: Runs if the promise is fulfilled (resolved).
- **catch**: Handles the error if the promise is rejected.

**Output:**
```
Task completed!
```


### **Key Differences and Simple Explanation:**

- **Callback:** Works by passing a function that will be called when the task is finished.  
- **Promise:** Represents the future value of an operation and has three states—`pending`, `fulfilled`, and `rejected`.  
- **Async/Await:** Makes asynchronous code look like synchronous code, with `await` waiting for promises to resolve.



