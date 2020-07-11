# 面试题 08.09. 括号

Implement an algorithm to print all valid \(e.g., properly opened and closed\) combinations of n pairs of parentheses.

Note: The result set should not contain duplicated subsets.

For example, given n = 3, the result should be:

\[ "\(\(\(\)\)\)", "\(\(\)\(\)\)", "\(\(\)\)\(\)", "\(\)\(\(\)\)", "\(\)\(\)\(\)" \]

```text
class Solution {
    public List<String> generateParenthesis(int n) {
        List<String> result = new ArrayList<>();
        StringBuilder sb = new StringBuilder(2*n);
        helper(n,n, sb, result);
        return result;
    }
    private void helper (int l, int r, StringBuilder sb, List<String> result) {
        if (l == 0 && r == 0) {
            result.add(new String(sb));
            return;
        }

        if (l >0) {
            sb.append('(');
            helper(l-1, r, sb, result);
            sb.deleteCharAt(sb.length()-1);
        }
        if (r > l) {
            sb.append(')');
            helper(l, r-1, sb, result);
             sb.deleteCharAt(sb.length()-1);
        }
    }
}
```



