# Design Linked List

## **Code**

```java
/**
 * Your MyLinkedList object will be instantiated and called as such:
 * MyLinkedList obj = new MyLinkedList();
 * int param_1 = obj.get(index);
 * obj.addAtHead(val);
 * obj.addAtTail(val);
 * obj.addAtIndex(index,val);
 * obj.deleteAtIndex(index);
 */
class MyLinkedList {

    class Node {
        int val;
        Node next;
        public Node(int val) {
            this.val = val;
            this.next = null;
        }
    }

    private Node head;
    private int size;

    /** 
     * Initialize your data structure here. 
     */
    public MyLinkedList() {
        this.size = 0;
    }

    /** 
     * Get the value of the index-th node in the linked list. 
     * If the index is invalid, return -1. 
     */
    public int get(int index) {
        if (index > this.size - 1 || index < 0) {
            return -1;
        }
        if (this.head == null) {
            return -1;
        }
        Node curr = this.head;
        for (int i = 0; i < index; i++) {
            curr = curr.next;
        }
        return curr.val;
    }

    /** 
     * Add a node of value val before the first element of the linked list. 
     * After the insertion, 
     * the new node will be the first node of the linked list. 
     */
    public void addAtHead(int val) {
        Node node = new Node(val);
        node.next = this.head;
        this.head = node;
        this.size++;
    }

    /** 
     * Append a node of value val to the last element of the linked list. 
     */
    public void addAtTail(int val) {
        Node node = new Node(val);
        if (this.head == null) {
            this.head = node;
        } else {
            Node curr = this.head;
            while (curr.next != null) {
                curr = curr.next;
            }
            curr.next = node;
        }
        this.size++;
    }

    /** 
     * Add a node of value val before the index-th node in the linked list. 
     * If index equals to the length of linked list, 
     * the node will be appended to the end of linked list. 
     * If index is greater than the length, the node will not be inserted. 
     */
    public void addAtIndex(int index, int val) {
        if (index < 0 || index > this.size) {
            return;
        }
        if (index == 0) {
            this.addAtHead(val);
        } else {
            Node curr = this.head;
            for (int i = 0; i < index - 1; i++) {
                curr = curr.next;
            }
            Node node = new Node(val);
            node.next = curr.next;
            curr.next = node;
            this.size++;
        }
    }

    /** 
     * Delete the index-th node in the linked list, if the index is valid. 
     */
    public void deleteAtIndex(int index) {
        if (index < 0 || index >= this.size) {
            return;
        }
        Node curr = this.head;
        if (index == 0) {
            this.head = curr.next;
        } else {
            for (int i = 0; i < index - 1; i++) {
                curr = curr.next;
            }
            curr.next = curr.next.next;
        }
        this.size--;
    }
}

```

