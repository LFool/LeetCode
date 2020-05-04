# Min Stack

## Description

Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

* push\(x\) -- Push element x onto stack.
* pop\(\) -- Removes the element on top of the stack.
* top\(\) -- Get the top element.
* getMin\(\) -- Retrieve the minimum element in the stack.

**Example 1:**

```text
Input
["MinStack","push","push","push","getMin","pop","top","getMin"]
[[],[-2],[0],[-3],[],[],[],[]]

Output
[null,null,null,null,-3,null,0,-2]

Explanation
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin(); // return -3
minStack.pop();
minStack.top();    // return 0
minStack.getMin(); // return -2
```

**Constraints:**

* Methods `pop`, `top` and `getMin` operations will always be called on **non-empty** stacks.

## **Code**

```java
class MinStack {
    
    int[] elementData;
    int[] minData;
    int capacity;
    int size;
    int top;

    /** initialize your data structure here. */
    public MinStack() {
        elementData = new int[10];
        minData = new int[10];
        Arrays.fill(minData, Integer.MAX_VALUE);
        capacity = 10;
        size = 0;
        top = 0;
    }
    
    public void push(int x) {
        if (capacity - size - 1 <= 0) {
            grow();
        }
        elementData[++top] = x;
        size++;
        minData[top] = Math.min(minData[top - 1], x);
    }
    
    public void pop() {
        top--;
        size--;
    }
    
    public int top() {
        return elementData[top];
    }
    
    public int getMin() {
        return minData[top];
    }
    
    public void grow() {
        int newCapacity = capacity + (capacity >> 1);
        capacity = newCapacity;
        elementData = Arrays.copyOf(elementData, newCapacity);
        minData = Arrays.copyOf(minData, newCapacity);
    }
}

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack obj = new MinStack();
 * obj.push(x);
 * obj.pop();
 * int param_3 = obj.top();
 * int param_4 = obj.getMin();
 */
```

