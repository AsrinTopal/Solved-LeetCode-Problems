# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->

# Approach
Approach
A C++ approach to add two numbers expressed as linked lists, where the digits are kept in reverse order (the 1's digit is at the beginning of the list) and each node in the linked list carries a single number digit.

Nonetheless, you can think about doing the following minor adjustments to better optimize it:

Steer clear of pointless conditional phrases while extracting digits:

As the following example demonstrates, you may simplify the code by extracting the digits straight from the nodes, as opposed to utilizing conditional (ternary) statements to do so:

```
int digit1 = (l1 != nullptr) ? l1->val : 0;
int digit2 = (l2 != nullptr) ? l2->val : 0;our space complexity here, e.g. $$O(n)$$ -->
```
Do not remove the dummy head:
```
delete dummyHead;
```
Deleting the dummy head can be avoided to prevent potential memory issues.
The dummy head node in this code doesn't need to be removed. It's easy to just cross out the line:

Here's the optimized code with these small improvements:

# Code
```
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode* dummyHead = new ListNode(0);
        ListNode* tail = dummyHead;
        int carry = 0;

        while (l1 || l2 || carry) {
            int digit1 = l1 ? l1->val : 0;
            int digit2 = l2 ? l2->val : 0;

            int sum = digit1 + digit2 + carry;
            carry = sum / 10;

            tail->next = new ListNode(sum % 10);
            tail = tail->next;

            if (l1) l1 = l1->next;
            if (l2) l2 = l2->next;
        }

        return dummyHead->next;
    }
};
```