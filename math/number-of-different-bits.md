# Number Of Different Bits

{% hint style="info" %}
exclusive or 两个位不同则变为1

数1的个数就行
{% endhint %}

```text
public class Solution {
  public int diffBits(int a, int b) {
    // after exclusive or, only the bits where
    //a and b are different will be 1
    a ^= b;
    int count = 0;
    //In java, notice that we are using logical right shift >>>
    //and a!= 0 as the terminal condition
    while (a != 0) {
      count += a & 1;
      a >>>= 1;
    }
    return count;
  }
}
```



