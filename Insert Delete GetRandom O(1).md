# January-16

## 380. Insert Delete GetRandom O(1).

```java
class RandomizedSet {
   int random;
   ArrayList<Integer>list;
   Set<Integer>set;
    public RandomizedSet() {
        set=new HashSet<>();
        list=new ArrayList<>();
        random=0;
    }
    public boolean insert(int val) {
        if(set.contains(val))return false;
        set.add(val);
        return true;
    }
    public boolean remove(int val) {
        if(!set.isEmpty()&&set.contains(val))
        {
            set.remove(val);
            return true;
        }return false;
    }
    public int getRandom() {
        list=new ArrayList<>(set);
        random=(int)(Math.random()*list.size());
        return list.get(random);
    }
}

/**
 * Your RandomizedSet object will be instantiated and called as such:
 * RandomizedSet obj = new RandomizedSet();
 * boolean param_1 = obj.insert(val);
 * boolean param_2 = obj.remove(val);
 * int param_3 = obj.getRandom();
 */
