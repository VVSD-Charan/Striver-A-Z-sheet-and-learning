# Execution Context in JavaScript

<li>Everything in JavaScript happens inside an execution context.</li>
<li>JavaScript is a synchronous single threaded language. Single threaded means that only one line of code can be executed at a time. Synchronous single threaded means that one line of code is executed at a time in a specific order.</li>
<li>When we run a javaScript program ,execution context is created.</li<br>

![alt text](<WhatsApp Image 2024-02-29 at 18.34.49_cca1086b.jpg>)

# Example of how execution context works

```

var n = 2;
function square(num)
{
    var ans = num * num;
    return ans;
}

var square2 = square(n);
var square4 = square(4);

```

<li>When we run this program , first of all a global execution context is created.</li>
<li>Execution context is created in two phases.
    <ol>
        <li>Creation / Memory creation phase.</li>
        <li>Code execution phase.</li>
    </ol>
</li>

## Phase 1 :  Memory creation phase
<li>In this phase,JavaScript will allocate space to all variables and functions.</li>
<li>In this phase , JavaScript goes line by line and allocates memory to all variables and functions.</li>
<li>If it encounters a variable , memory is allocated to it and variables are initialized as <strong>undefined</strong> . If it encounters a function , then <strong>entire code of function</strong> will be stored.</li><br><br>

![alt text](<WhatsApp Image 2024-02-29 at 18.50.36_66814c5d.jpg>)


## Phase 2 : Code execution phase

<li>JavaScript again goes line by line to execute code.</li><br>

```
var n = 2;
```

<li>
    After phase 1 , variable n's memory allocation is being done and n was initialized as undefined. Now , in this phase the value of n will be set as 2 from undefined.
</li><br>

   ```
   function square(num)
    {
        var ans = num * num;
        return ans;
    }
   ```

<li>
    These lines of code are neglected by javaScript. Functions are inovked only when they are used.
</li><br>

```
var square2 = square(n);
```

<li>
As function is invoked , an entirely new execution context will be created for  function inside code component. 
</li><br><br>

![WhatsApp Image 2024-02-29 at 23 23 13_e4c4d672](https://github.com/VVSD-Charan/Striver-A-Z-sheet-and-learning/assets/105978561/0bda640e-74eb-422a-8271-ad0edbbac2db)

<li>
The execution context created will be for that piece of code i.e function only. Again both the phases i.e memory creation and code execution phase will be done . The return statement in function returns value of variable in local memory to the place where function was invoked i.e value of 4 will be sent to variable square2 as function was invoked there.
</li><br><br>

![WhatsApp Image 2024-02-29 at 23 52 57_1a832194](https://github.com/VVSD-Charan/Striver-A-Z-sheet-and-learning/assets/105978561/5c8d42e8-20e0-4444-9cd4-4610ec466e66)

<li>
Similarly , the function will be invoked at line
</li><br>

```
var square4 = square(4);
```

<li>
Again , new execution context will be created followed by phases 1 and 2. With this , the execution of entire code will be completed. Whenever execution context is done executing , it will be deleted. <strong> At the end of execution of program , the global execution context will also be deleted. </strong>
</li><br><br>

![WhatsApp Image 2024-02-29 at 23 58 29_aa0581f0](https://github.com/VVSD-Charan/Striver-A-Z-sheet-and-learning/assets/105978561/4d25938c-86a7-47bc-a4c2-6f6edc645b5d)


## How does JavaScript manage such difficult tasks of execution context deletion and creation ?

<li>When a function is invoked , a new execution context is created . And same goes on whenever a function is invoked.</li>
<li><strong>JavaScript maintains a call stack</strong> to perform these operations.</li>
<li>When a function is invoked , a new execution context is created and pushed into stack. When it completes its execution , the execution context will be popped out of stack.</li>
<li>Global execution context always stays at the bottom of the stack.</li>
<li>Global execution context will be the last thing to be deleted from call stack. It will be deleted after entire execution is completed.</li>


