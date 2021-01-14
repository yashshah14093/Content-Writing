Hello Readers,

Everyone of you would have taken a ride in public transport buses🚌 or trains🚝. You might have observed that the person of old age are given priority over others.

![Public Transport](https://i.imgur.com/QQeCWil.jpeg)

Now let's say you have the responsibility of distribution of seats among people based on age which you already know, How will you do this task using programming?

> arrayOfAge = [9,4,6,8,5]

> numberOfSeats = 3

Alright, you might have guessed it correctly. Just Sort the array and pick 3 people with maximum age.

What's the time complexity of this approach? ***O(n.log(n))***

But, Let's say there are m stops for the bus and at each stop one people acquiring the seat leaves and another person enteres the bus. To whom do you allot the seat? Will you do sorting again and again for each stop and allot the seat to the person with maximum age? Let's first analyze this approach...

Sorting for each stop will take ***O(n.log(n))*** time and doing it m times. So, the total time-complexity will be ***O(m.n.log(n))***.

Now, We want to optimize the algorithm. Here comes our Data-Structure Priority-Queue or Heap.

You might be wondering🤔, What's special in this data-structure?

The above algorithm could be solved in just ***O(m.log(n))***, Isn't it is much better than before😀?

Now Let's understand Priority Queue and how can it optimise our problem?

# Priority Queue (HEAP)

In priority queue, an element with the highest priority served first than the rest of the elements. Basically, the elements are arranged in this data-structure based on priority. Priority could be of any type eg. maximum value, minimum value etc. 

So, Think🤔 about how can we prioritise people in the example above?

Hoping you already got it, We can prioritise people based on age i.e. the person with the maximum age🧓 should be given seat first.

<br>
Heap satisfies the following properties:

1. Tree of a heap is a complete binary tree i.e. Height is always ***O(logn)***.
2. Heap follows the order of elements internally. E.g. In a Max-Heap, parent's value is greater than equal to that of its children.

In heap, the children of an element at index **'i'** are at positions (2*i + 1) and (2*i + 2) as its binary tree is completely balanced. 

