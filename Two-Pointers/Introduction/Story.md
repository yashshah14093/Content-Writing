# Two Pointers Method

Hello👋 Readers,

Before introducing you to the Two Pointers Approach, I would first like you to find the maximum length chain of fruits from the chain of fruits given below.

![](https://i.imgur.com/kTU4Z3s.jpg)

--------------------------------
🎯 What's your approach?🧐
-------------------------------

### Approach-1

**Step-1**: Select a fruit and find how far a chain can grow such that no fruit could repeat.

**Step-2**: Perform Step-2 for each of the fruit in the chain. 

**Step-3**: Select the maximum length out of those.

------------------------------------------------------
🎯 What's the time-complexity of the above approach?

📝 **O(N^2)** 

--------------------------------------------------------

🎯 Think🤔 about how can we optimise out approach?

📝 Farthest index remains the same until the we iterate over the first occurence of the repeating element.

![](https://i.imgur.com/ozQIt9a.jpg)

Observe the Table below:

![](https://i.imgur.com/C7xuRij.jpg)

---------------------------------------------------------

By having a look on the table, you will observe that the result of the farthest index remains same until the first index of repeating element can be overtaken.

To implement the above observation, We can use Two-Pointers Method which we are going to discuss.

