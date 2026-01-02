# Stream APIs
## Intermediate Functions

- filter(Predicate)
- distinct()
- limit(long n)
- skip(long n)
- map(Function)
- flatMap(Function)
- sorted()
- peek(Consumer)

---

## Terminal Functions**

- forEach(Consumer)
- reduce(BinaryOperator)
- findFirst()
- findAny()
- count()
- min(Comparator)
- max(Comparator)
- sum() (primitive streams)
- average() (primitive streams)
- anyMatch(Predicate)
- allMatch(Predicate)
- noneMatch(Predicate)
- collect(Collector)
    - Common collectors:
        - Collectors.toList()
        - Collectors.toSet()
        - Collectors.toMap()
        - Collectors.groupingBy()
        - Collectors.partitioningBy()
        - Collectors.joining()
        - Collectors.counting()

---

# DSA

### HashMap Operations

Frequency Count
```java
map.put(key, map.getOrDefault(key, 0) + 1);
```
Compare Two HashMaps
```java
map1.equals(map2);
```

⸻

### Arrays

Return Multiple Values (as Array)
```java
return new int[]{val1, val2};
```
Convert HashMap Values to List of Lists
```java
return new ArrayList<>(map.values());
```
Compare Two Arrays
```java
Arrays.equals(arr1, arr2);
```

⸻

### 2D Matrix (Array)

Dimensions
```java
int rows = matrix.length;
int cols = matrix[i].length;
```
Access / Assign Element
```java
matrix[i][j] = element;
```
Traversal Pattern
```java
for (int i = 0; i < rows; i++) {
    for (int j = 0; j < cols; j++) {
        // matrix[i][j]
    }
}
```

⸻

### String & Character Conversions

String → Character Array
```java
char[] chars = str.toCharArray();
```
Character Array → String
```java
String str = new String(charArray);
```
int[] → String
```java
String str = Arrays.toString(intArray);
```
Character at Index
```java
str.charAt(i);
```
Convert Character to Lowercase
```java
Character.toLowerCase(str.charAt(i));
```

⸻

### String → Integer Conversions

Single Digit Character → int
```java
int num = Integer.parseInt(String.valueOf(str.charAt(i)));
```
⚠️ Integer.parseInt(str.charAt(i)) is invalid because char ≠ String.

Substring → int
```java
int num = Integer.parseInt(str.substring(i, j));
```

⸻

### Switch Statement
```java
switch (token) {
    case "+":
        // logic
        break;
    case "-":
        // logic
        break;
}
```

⸻

### Math Utilities

Ceiling Division
```java
(int) Math.ceil((double) pile / val);
```
👉 Used when partial division still counts as full (e.g., Koko Eating Bananas).

⸻

### Binary Search (Safe Mid Calculation)
```java
int mid = left + (right - left) / 2;
```
✔ Prevents integer overflow
✔ Standard interview-approved formula

⸻
