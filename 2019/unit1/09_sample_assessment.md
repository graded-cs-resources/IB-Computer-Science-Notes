---
pagetitle: Unit 1 Sample Test
---

# IB CS Sample Test - Unit 1

Please write your answers in the answer booklet. Carefully label each problem with the problem number so that I can find the answers. You do not need to rewrite the questions.

1. *(2 marks)* Name two examples of computer hardware. 
   
2. *(3 marks)* Name three common native data types in programming languages.

3. *(2 marks)* What does the operator `++` do in code such as `a++`?

4. *(1 mark)* What would be the outcome of the statement `2 * 3 > 4 && 2 + 3 >= 5`?

5. *(2 mark)* Describe what it means for a programming language to be "statically typed" and describe one advantage of static typing.
   
6. *(2 marks)* Recently my son asked me how my car worked. “Well,” I said, “when I push the pedal the engine burns gasoline, making a bunch of tiny explosions that move some rods that make the wheels turn. There’s more to it than that, but that’s all I know.” This explanation is an example of what computer science principle? Briefly explain your answer. 
   
7. *(2 marks)* Outline the relationship between RAM and cache. 
   
8. *(1 mark)* How many bits are in a byte? 
   
9. Programmers who work at a very low level with computer processors might write in a language like the one below:

   ```nasm
   mov   eax,3
   mov   ebx,5
   add   eax,ebx
   int   0x80
   ```

   a. *(1 mark)* This is an example of what type of language?  
   b. *(1 mark)* The command `mov` tells the processor to move a value into a register. What is a CPU register?
   c. *(1 mark)* Moving to registers and adding values are examples of the ___________________ of the processor. 
   
10. *(5 marks)* Construct a complete trace table for the script below for the input values `N = 9` and `T = 14`, showing all variable values and all outputs of the script.

    ```
    J = N + T
    K = J div 2
    loop while K >= N
        Output (K - N)
        K = K - 1
    end loop
    ```

11. *(5 marks)* Construct an algorithm (in pseudocode or typescript-like pseudocode) to loop through the elements of a string array with the name `MONKEYS`, outputting the sentence `Monkey number _____ has the name  _____` for each monkey, as shown in the example below.
   
    ```
    Input: [Napolean, Ricky]
    Output:
      Monkey number 1 has the name Napolean
      Monkey number 2 has the name Ricky
    ```

12. Consider the java method below:
    
    ```java
     public double mystery(double n, boolean b) {
       if (b && n > 10) {
           return n;
       }else {
           return n % 2;
       }
    }
    ```

    1. *(1 mark)* What is the *return type* of this method?

    2. *(1 mark)* What does the operator `%` do?

    3. *(4 marks)* For each method call, write the output. If the method would result in an error, write "error".

       1. `mystery(12.3, true);`

       2. `mystery(87, "false");`

1.  Consider an IB collection of numbers `NUMS = {2, 7, -3, 11, 15, -3}`
    1.  *(4 marks)* Consider the following algorithm

        ```python
        NUMS.resetNext()
        CL = 0
        loop while NUMS.hasNext()
            if NUMS.getNext() = -3 then
                CL = CL + 1
            end if
        end loop
        output CL
        ```

        For this algorithm **copy** and complete the following started trace table:

        | `CL` | `NUMS.hasNext()` | `NUMS.getNext() = -3` | output |
        | ---- | ---------------- | --------------------- | ------ |
        | 0    | `TRUE`           | `FALSE`               |        |
        | ...  | ...              | ...                   | ...    |

    2. *(3 marks)* Construct an algorithm using pseudocode that returns the sum of the elements 

