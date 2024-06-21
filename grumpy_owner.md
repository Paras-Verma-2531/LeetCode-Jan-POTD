# June-21
## 1052. Grumpy Bookstore Owner
```java
class Solution {

    public int maxSatisfied(int[] customers, int[] grumpy, int minutes) {
        int n = customers.length;
        int unrealizedCustomers = 0;
        //cal the no. of initial unsatisfied customer
        for (int i = 0; i < minutes; i++) {
            unrealizedCustomers += customers[i] * grumpy[i];
        }
        //slide the window and do the same
        int maxUnrealizedCustomers = unrealizedCustomers;
        for (int i = minutes; i < n; i++) {
            unrealizedCustomers += customers[i] * grumpy[i];
            unrealizedCustomers -= customers[i - minutes] * grumpy[i - minutes];
            maxUnrealizedCustomers = Math.max(
                maxUnrealizedCustomers,
                unrealizedCustomers
            );
        }
        //add the satified customers
        int totalCustomers = maxUnrealizedCustomers;
        for (int i = 0; i < customers.length; i++) {
            totalCustomers += customers[i] * (1 - grumpy[i]);
        }
        return totalCustomers;
    }
}
