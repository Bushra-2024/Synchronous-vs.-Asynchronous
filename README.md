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



- In **synchronous** execution, each step waits for the previous one to complete. In **asynchronous** execution, the program continues running while it waits for an operation (like a setTimeout or a network request) to finish. 


**Synchronous Execution Process:**  
1. Executes the first line.  
2. Waits for it to complete before moving to the next line.

**Asynchronous Execution Process:**  
1. Executes the first line.  
2. Moves to the next line without waiting.  
3. The callback of the async task runs once the task completes.

---

