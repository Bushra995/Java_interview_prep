# Java String Practice - Quick Revision

This file is a quick revision guide for common Java string-based practice methods.

---

## 1. Reverse a String

### Method
```java
static String reverse(String name){
    StringBuilder sb = new StringBuilder();
    for(int i = name.length() - 1; i >= 0; i--){
        sb.append(name.charAt(i));
    }
    return sb.toString();
}
```

### Example
```java
System.out.println(reverse("ANAB"));
```

### Output
```text
BANA
```

### Notes
- Starts from the last character and appends each character to `StringBuilder`.
- Efficient compared to repeated string concatenation.

---

## 2. Check Palindrome

> Note: Your method is named `isAnagram`, but the logic actually checks whether the string is a **palindrome**, not an anagram.

### Method
```java
static boolean isAnagram(String name){
    boolean istrue = false;
    if(name.equalsIgnoreCase(reverse(name))){
        istrue = true;
    } else {
        istrue = false;
    }
    return istrue;
}
```

### Example
```java
System.out.println(isAnagram("madam"));
System.out.println(isAnagram("hello"));
```

### Output
```text
true
false
```

### Notes
- A palindrome reads the same forward and backward.
- Better method name would be `isPalindrome`.

---

## 3. Count Vowels and Consonants

### Method
```java
static void check_vowel_constant(String name){
    char[] c = name.toCharArray();
    int total_vowels = 0;
    int total_constants = 0;

    for(int i = 0; i < c.length; i++){
        if(c[i] >= 'a' && c[i] <= 'z'){
            if("aeiou".contains(String.valueOf(c[i]))){
                total_vowels++;
            } else {
                total_constants++;
            }
        }
    }
    System.out.printf("Vowels %d and constants %d%n", total_vowels, total_constants);
}
```

### Example
```java
check_vowel_constant("education");
```

### Output
```text
Vowels 5 and constants 4
```

### Notes
- Only lowercase letters are counted.
- Uppercase letters are ignored in current logic.
- `constants` should be renamed to `consonants`.

---

## 4. Find Repeated and Non-Repeated Characters

### Method
```java
static void nonrep_char_find(String name){
    char[] c = name.toCharArray();
    StringBuilder nonrepetitive_string = new StringBuilder();
    StringBuilder repetitive_string = new StringBuilder();

    for(int i = 0; i < name.length(); i++){
        if(name.indexOf(name.charAt(i)) == name.lastIndexOf(name.charAt(i))){
            nonrepetitive_string.append(name.charAt(i));
        } else {
            if(repetitive_string.indexOf(String.valueOf(name.charAt(i))) == -1) {
                repetitive_string.append(name.charAt(i));
            }
        }
    }
    System.out.println("repeptive string " + repetitive_string);
    System.out.println("non rep string" + nonrepetitive_string);
}
```

### Example
```java
nonrep_char_find("programming");
```

### Possible Output
```text
repeptive string rgm
non rep stringpoain
```

### Notes
- Characters appearing once go to non-repetitive string.
- Repeated characters are added only once to repetitive string.

---

## 5. Remove Duplicate Characters

### Method
```java
static void remove_duplicated(String input){
    StringBuilder sb = new StringBuilder();
    for(int i = 0; i < input.length(); i++){
        if(sb.indexOf(String.valueOf(input.charAt(i))) == -1){
            sb.append(input.charAt(i));
        }
    }
    System.out.println(sb);
}
```

### Example
```java
remove_duplicated("aaaaaaaaaabbbbbbbbbbcccccccd");
```

### Output
```text
abcd
```

### Notes
- Preserves first occurrence of each character.
- Useful for quick duplicate removal without collections.

---

## 6. Character Frequency Count

### Method
```java
static void charfreqCount(String ch){
    HashMap<Character, Integer> map = new HashMap<>();
    StringBuilder seenchar = new StringBuilder();
    for(int i = 0; i < ch.length(); i++){
        if(seenchar.indexOf(String.valueOf(ch.charAt(i))) == -1) {
            seenchar.append(ch.charAt(i));

            int counteach = 0;
            for (int j = 0; j < ch.length(); j++) {
                if (ch.charAt(i) == ch.charAt(j)) {
                    counteach++;
                }
            }
            seenchar.append(counteach);
            map.put(ch.charAt(i), counteach);
        }
    }
    System.out.println(seenchar);
    for(HashMap.Entry<Character, Integer> entry : map.entrySet()){
        System.out.println("char" + entry.getKey() + "count: " + entry.getValue());
    }
}
```

### Example
```java
charfreqCount("aabbbcc");
```

### Output
```text
a2b3c2
chara count: 2
charb count: 3
charc count: 2
```

### Notes
- Uses nested loops, so time complexity is higher.
- Stores frequency in a `HashMap`.

---

# Sample `main()` for Quick Practice

```java
public static void main(String[] args) {
    System.out.println("Reverse: " + reverse("ANAB"));

    System.out.println("Is Palindrome: " + isAnagram("madam"));

    check_vowel_constant("education");

    nonrep_char_find("programming");

    remove_duplicated("aaaaaaaaaabbbbbbbbbbcccccccd");

    charfreqCount("aabbbcc");
}
```

---

# Important Corrections to Remember

## Rename Suggestions
- `isAnagram` → `isPalindrome`
- `check_vowel_constant` → `checkVowelConsonant`
- `nonrep_char_find` → `findRepeatedAndNonRepeatedChars`
- `remove_duplicated` → `removeDuplicates`
- `charfreqCount` → `charFreqCount`

## Spelling Fixes
- `constants` → `consonants`
- `repeptive` → `repetitive`

---

# Quick Interview Revision Points

- **StringBuilder** is useful for mutable string operations.
- **Palindrome** check can be done by comparing original with reversed string.
- **Duplicate removal** can be done using `StringBuilder`, `Set`, or `Map`.
- **Character frequency** can be solved using:
  - nested loops
  - `HashMap<Character, Integer>`
- **Repeated/non-repeated characters** often use:
  - `indexOf()`
  - `lastIndexOf()`

---

# Summary Table

| Method | Purpose |
|--------|---------|
| `reverse()` | Reverse a string |
| `isAnagram()` | Checks palindrome logic |
| `check_vowel_constant()` | Count vowels and consonants |
| `nonrep_char_find()` | Find repeated and non-repeated chars |
| `remove_duplicated()` | Remove duplicate chars |
| `charfreqCount()` | Count character frequencies |

---

If you want, I can also generate:
1. a **cleaned-up improved Java version** of this class, or
2. a **shorter 1-page interview revision markdown** version.
