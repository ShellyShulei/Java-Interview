# 剑指 Offer 38. 字符串的排列

输入一个字符串，打印出该字符串中字符的所有排列。

你可以以任意顺序返回这个字符串数组，但里面不能有重复元素。

示例:

输入：s = "abc" 输出：\["abc","acb","bac","bca","cab","cba"\]

{% hint style="info" %}
要用set去重
{% endhint %}

```text
class Solution {
    public String[] permutation(String s) {
        char[] arr = s.toCharArray();
        List<String> result = new ArrayList<>();
        helper(arr, 0, result);
        return result.toArray(new String[result.size()]);
    }

    private void helper( char[] arr, int index, List<String> result) {
        if (index == arr.length) {
            result.add(new String(arr));
            return;
        }
        Set<Character> used = new HashSet<Character>();
        for (int i = index; i < arr.length; i++) {
        if (used.add(arr[i])) {
            swap(arr, i , index);
            helper(arr, index+1, result);
            swap(arr, i, index);
         }
        }
    }

    private void swap(char[] arr, int i, int j) {
        char tmp = arr[i];
        arr[i] = arr[j];
        arr[j] = tmp;
    }
}
```





