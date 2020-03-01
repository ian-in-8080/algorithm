## Reverse List

### thoughts

- use node PREV to serve as new head 
- PREV starts with null => the old head attach to null as the end node
- use node NEXT to back up the nodes => head jump to NEXT

```
public ListNode reverseList(LisNode head) {
  ListNode NewHead = null;
  
  while(head != null) {
    ListNode next = head.next;
    head.next = newHead;
    newHead = head;
    head = head.next;
    }
  
  return newHead;
}
```

## Reverse List in range



## Add two number

- two number in linkedlist representation
- each node is a digit
- in reverse order

```
Input: 7->1->6->null, 5->9->2->null
Output: 2->1->9->null	
Explanation: 617 + 295 = 912, 912 to list:  2->1->9->null
```

### Thoughts
- add digits in each node starting from the head
- if two list run out -> whether carry one?
- if one of the list run out -> whether carry one?

```
public ListNode addLists(ListNode l1, ListNode l2) {
if (l1 == null && l2 == null) return null;
        if (l1 == null) return l2;
        if (l2 == null) return l1;
        
        ListNode dummy = new ListNode(-1);
        ListNode tail = dummy;
        int carry = 0;
        while (l1 != null && l2 != null) {
            int digit = l1.val + l2.val + carry;
            carry = digit / 10;
            tail.next = new ListNode(digit % 10);
            tail = tail.next;
            l1 = l1.next;
            l2 = l2.next;
        }
        
        while (l1 != null) {
            int digit = l1.val + carry;
            carry = digit / 10;
            tail.next = new ListNode(digit % 10);
            tail = tail.next;
            l1 = l1.next;
        }
        
        while (l2 != null) {
            int digit = l2.val + increment;
            increment = digit / 10;
            tail.next = new ListNode(digit % 10);
            tail = tail.next;
            l2 = l2.next;
        }
        
        if (carry != 0) {
            tail.next = new ListNode(carry);
        }
        
        return dummy.next;
    }

```

## Add 2 number 2

- two number in linkedlist representation
- forward order
- sum two linkedlist and present the number in forward linkedList

```
Input: 6->1->7   2->9->5
Output: 9->1->2
```

### thoughts

-  convert list to num => sum nums => convert num back to list (not apply when num getting large than limit of long)
- reverse two lists => add two list 
- use stacks

```
public ListNode addLists2(ListNode l1, ListNode l2) {
        // write your code here
        long num1 = nodeToNum(l1);
        long num2 = nodeToNum(l2);
        System.out.println(num1 + num2);
        return numToNode(num1 + num2);
        
    }
    
    private ListNode numToNode(long num) {
        ListNode head = null;
        ListNode temp = null;
        if (num == 0) return new ListNode(0);
        while (num > 0) {
            int digit = (int) (num % 10);
            head = new ListNode(digit);
            head.next = temp;
            temp = head;
            num /= 10;
        }  
        
        return head;
    }
    
    private long nodeToNum(ListNode node) {
        if (node == null) return 0;
        long theNum = 0;
        while (node != null) {
            theNum += node.val;
            if (node.next == null) {
                break;
            }
            else {
                theNum *= 10;
            }
            node = node.next;
        }
        
        return theNum;
    }
```
