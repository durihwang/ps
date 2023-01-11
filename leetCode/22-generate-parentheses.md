## 문제
https://leetcode.com/problems/generate-parentheses/description/

## 알고리즘
백트래킹

## 풀이
n이 주어지면 n만큼 해당하는 쌍이 맞는 괄호의 경우를 리턴하는 문제이다.

## 코드
```java
class Solution {
    public List<String> generateParenthesis(int n) {

        List<String> resultList = new ArrayList<>();
        recursive(n, resultList, 0, 0, "");
        return resultList;
    }

    public void recursive(int n, List<String> resultList, int left, int right, String str) {

        // 조건 처리
        if(left == n && right == n) {
            resultList.add(str);
        }

        // 재귀
        if(left < n) {
            recursive(n, resultList, left+1, right, str + "("); // 왼쪽 괄호는 n보다 작은 경우에 무조건 넣을 수 있다.
        }
        if(left > right) {
            recursive(n, resultList, left, right+1, str + ")"); // 오른쪽 괄호는 왼쪽 괄호와 쌍이 맞아야 하기 때문에 왼쪽 괄호보다 항상 작은 경우에만 넣을 수 있다.
        }
    }
}
```