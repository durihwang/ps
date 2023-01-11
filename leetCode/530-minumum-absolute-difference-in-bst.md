## 문제
https://leetcode.com/problems/minimum-absolute-difference-in-bst/

## 알고리즘
이진검색트리(BST)

## 풀이
이진 검색 트리에서 각 노드 값의 차이가 가장 작은 것을 구하는 문제이다.

가장 처음 노드가 아니면 이전 값과 현재 노드 값을 비교해서 차이가 가장 작은 것을 갱신해주면 된다.

하지만 문제에 보면 노드 값이 0이나 null도 들어가 있다.

맨 처음 노드를 판별할 때 0이나 null로 판단할게 아니라 check 변수를 하나 만들어서 판단해주자.

## 코드
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {

    int min;
    int prev;
    boolean check;

    public int getMinimumDifference(TreeNode root) {
        
        min = Integer.MAX_VALUE;
        check = false;
        inOrder(root);
        return min;
    }

    public void inOrder(TreeNode root) {
        
        if(root == null) {
            return;
        }

        inOrder(root.left);
        // 최소값 처리
        if(!check){
            check = true;// 맨 처음에는 이전 값이 없으므로 check 배열을 true로 변경
            // 노드 값이 0이나 null도 들어갈 수 있기 때문에 prev 값이 0이거나 null인 경우를 맨 처음 노드라고 생각하면 안된다.
            // 가장 안전하게 check 변수를 만들어서 최초 여부를 체크하는 것이 가장 좋다.
        } else {
            min = Math.min(min, root.val-prev);// 맨 처음 노드가 아니라면 현재 값에서 prev 값을 뺀 최소값을 계속 갱신
        }

        // 이전 노드 값 저장
        prev = root.val;
        //System.out.println(root.val);
        
        inOrder(root.right);
    }
}
```