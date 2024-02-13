### ***反转链表算法***
```cpp
   ListNode* reverseList(ListNode* head) {
        ListNode* prev = NULL; // prev : 指向反转好节点的最后一个节点
        ListNode* curr = head;    //指向反转链表的第一个节点
        while(curr != NULL){
            ListNode* next = curr->next; 
            curr->next = prev;
            prev = curr;
            curr = next;
        }
        return prev;
    }
```