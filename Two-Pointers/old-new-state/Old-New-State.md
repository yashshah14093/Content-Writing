# Old and New State

- This technique uses Two pointers as variables.
- Pointers stores the intermediate results.
- New results are calculated using those variables.

![](https://i.imgur.com/VNtHKMO.jpg)

### Example:

## Fibonacci Sequence

![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTxl4LXK4WdfFVDyjtTJR1TsuncOUj4c5eReg&usqp=CAU)

- In fibonacci series, next number is the sum of previous two numbers.
- Two pointers(variables) can be used to store the previous two results.
- Next result can be calculated by the sum of those pointers.

      public int fibonacci(int n){

            int prev1 = 1,prev2 = 1;
            int curr = 1;
            for(int index = 3; index <= n; index++){
                curr = prev1 + prev2;
                prev1 = prev2;
                prev2 = curr;
            }

            return curr;
        }
