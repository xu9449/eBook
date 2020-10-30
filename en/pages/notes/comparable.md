i. Nature Order:
```java
PriorityQueue < Integer> minHeap = new PriorityQueue<Integer>();
```
ii. Custom Class
```java
PriorityQueue<Cell> minHeap = new PriorityQueue<Cell>();
class Cell implements Comparable<Cell> {
	….
	@Override
	public int compareTo(Cell another) {
		if(this.value == another.value) {
			return 0;
		}
		return this.value < another.value ? -1 ; 1;
	}
```
iii. Extra Comparator object to compare the elements
```java
class MyComparator implements Comparator<Cell>{
@Override
	public int compare(Cell c1, Cell c2) {
		…
	}
}
```
iv. Collections,reverseOrder()

```java
	PriorityQueue<Integer> pQueue = new PriorityQueue<Integer>(1000, new Comparator<Integer>() {  
	    
	                public int compare(Integer w1, Integer w2) {                         
	                    return w1.compareTo(w2);  
	                }      
	            });  
```
