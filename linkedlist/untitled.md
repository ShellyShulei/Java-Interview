# 234. Palindrome Linked List

Given a singly linked list, determine if it is a palindrome.

**Example 1:**

```text
Input: 1->2
Output: false
```

**Example 2:**

```text
Input: 1->2->2->1
Output: true
```

```text
class Solution {
    public boolean isPalindrome(ListNode head) {
        if (head == null || head.next == null) {
            return true;
        }
        ListNode mid = findmid(head);
        ListNode right = mid.next;
        mid.next = null;
        ListNode newHead = reverse(right);
        return check(head, newHead);
    }
    private ListNode findmid(ListNode head) {
        ListNode slow = head;
        ListNode fast = head;
        while (fast.next != null && fast.next.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }
        return slow;
    }
    private ListNode reverse (ListNode head) {
        if (head == null || head.next == null) {
            return head;
        }
        ListNode prev = null;
        while (head != null) {
            ListNode next = head.next;
            head.next = prev;
            prev = head;
            head = next;
        }
        return prev;
    }
    private boolean check (ListNode head, ListNode newHead) {
        if (head == null && newHead != null) {
            return false;
        }
        if (head != null && newHead == null) {
            return false;
        }
        while (head != null && newHead != null) {
            if (head.val != newHead.val) {
                return false;
            }
            head = head.next;
            newHead = newHead.next;
        }
        return true;
    }
}
```

{% hint style="info" %}
Time: O\(n\)    Space: O\(1\)

First, we find the middle node to seperate the list into two parts, reverse the right part. Then, check if they have the same value one by one.
{% endhint %}



