## 문제
https://leetcode.com/problems/remove-nth-node-from-end-of-list/description/

## 알고리즘
Linked List

## 풀이
```n = 2```라면 뒤에서부터 2번째의 값을 연결 리스트에서 제거해야 한다.
시간복잡도가 덜 드는 풀이방법이 있는데 내 머리로 그 방법을 떠올릴 수 없을 거 같아서 아래 방법으로 풀었다.

## 코드
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {

        // node를 다룰때에는 항상 파라미터로 받은 node를 다른 변수에 담아서 조작해야 한다.
        ListNode node = head;
        ListNode[] nodeList = new ListNode[30];
        int index = 0;

        while(node != null) {
            nodeList[index++] = node;
            node = node.next;
        }

        // 배열의 크기가 하나면 무조건 제거 (n은 1부터 가능하기 때문)
        if(index == 1) {
            return null;
        } else if(index-n == 0) {   // 배열의 크기와 n을 뺀 값이 0이 제거할 노드가
            return head.next;
        } else {    // 위 경우가 아니면 제거해야할 전 node 에서 next 값을 next.next 값으로 변경하여 해당 값을 지워준다. 
            node = nodeList[index-n-1];
            node.next = node.next.next;
        }

        return head;
    }
}
```