# STRINGS


### FIRST LETTER TO APPEAR TWICE

```c

#include <stdio.h>
#include <string.h>

char firstRepeatedChar(char* s) {
    int indices[26] = {0}; 
    char result = '\0'; 

    int smallestIndexDiff = strlen(s); 

    for (int i = 0; s[i] != '\0'; i++) {
        int index = s[i] - 'a';

        if (indices[index] != 0) { 
            int indexDiff = i - indices[index] + 1;

            if (indexDiff < smallestIndexDiff) {
                smallestIndexDiff = indexDiff;
                result = s[i];
            }
        } else { 
            indices[index] = i + 1; 
        }
    }

    return result;
}

int main() {
    char s1[] = "abccbaacz";
    printf("Output: %c\n", firstRepeatedChar(s1)); // Output: c

    char s2[] = "abcdd";
    printf("Output: %c\n", firstRepeatedChar(s2)); // Output: d

    return 0;
}

```

### REMOVE TRAILING ZER0

```c

#include <stdio.h>
#include <string.h>

char* removeTrailingZeros(char* num) {
    int len = strlen(num);
    while (len > 0 && num[len - 1] == '0') {
        num[len - 1] = '\0';
        len--;
    }
    return num;
}

int main() {
    char num1[] = "51230100";
    printf("Output: %s\n", removeTrailingZeros(num1)); // Output: "512301"

    char num2[] = "123";
    printf("Output: %s\n", removeTrailingZeros(num2)); // Output: "123"

    return 0;
}

```

### ADD TRAILING ZERO

```c
#include <stdio.h>
#include <string.h>

char* addTrailingZeros(char* num, int zeros) {
    int len = strlen(num);
    int newLen = len + zeros;
    for (int i = len; i < newLen; i++) {
        num[i] = '0';
    }
    num[newLen] = '\0';
    return num;
}

int main() {
    char num1[] = "512301";
    int zeros1 = 2;
    printf("Output: %s\n", addTrailingZeros(num1, zeros1)); // Output: "51230100"

    char num2[] = "123";
    int zeros2 = 3;
    printf("Output: %s\n", addTrailingZeros(num2, zeros2)); // Output: "123000"

    return 0;
}
```

### PREFIX COUNTER IN A STRING WITH GIVEN TEXT

```c

#include <stdio.h>
#include <string.h>

int countPrefix(char* words[], int size, char* pref) {
    int count = 0;
    for (int i = 0; i < size; i++) {
        if (strncmp(words[i], pref, strlen(pref)) == 0) {
            count++;
        }
    }
    return count;
}

int main() {
    char* words1[] = {"pay", "attention", "practice", "attend"};
    int size1 = sizeof(words1) / sizeof(words1[0]);
    char* pref1 = "at";
    printf("Output: %d\n", countPrefix(words1, size1, pref1)); // Output: 2

    char* words2[] = {"leetcode", "win", "loops", "success"};
    int size2 = sizeof(words2) / sizeof(words2[0]);
    char* pref2 = "code";
    printf("Output: %d\n", countPrefix(words2, size2, pref2)); // Output: 0

    return 0;
}

```



### REPLACE CHARACTER
```c
i: Reydel
o: R*yd*l
#include <stdio.h>
#include <string.h>

void replaceAll(char *str, char oldChar, char newChar);
int main() {
    char str[100] = "Reydel";
    char oldChar = 'e', newChar = '*';

    printf("String before replacing: %s\n", str);
    replaceAll(str, oldChar, newChar);
    printf("String after replacing '%c' with '%c': %s\n", oldChar, newChar, str);

    return 0;
}
void replaceAll(char *str, char oldChar, char newChar) {
    while (*str != '\0') {
        if (*str == oldChar) {
            *str = newChar;
        }
        str++;
    }
}

```

### REPLACE FIRST / LAST CHARACTER
```C
FIRST

I: REYDEL
O: 4EYDEL

#include <stdio.h>
#include <string.h>

void replaceFirst(char *str, char newChar);

int main() {
    char str[100] = "REYDEL";
    char newChar = '4'; 
    printf("String before replacing: %s\n", str);
    replaceFirst(str, newChar);
    printf("String after replacing first character with '%c': %s\n", newChar, str);
    return 0;
}
void replaceFirst(char *str, char newChar) {
    if (str[0] != '\0') {
        str[0] = newChar;
    }
}

LAST

I: REYDEL
O: REYDE4

void replaceLast(char *str, char newChar) {
    size_t length = strlen(str);
    if (length > 0) {
        str[length - 1] = newChar;
    }
}
```

### REVERSE STRING

```C

int main() {
    char str[101];
    printf("Enter a string: ");
    scanf("%s", str);

    int len = strlen(str);
    for (int i = len - 1; i >= 0; i--) {
        printf("%c", str[i]);
    }
    return 0;
}

```

### PERCENTAGE OF LETTERS IN A STRING

```c
#include <stdio.h>
#include <string.h>

int letterPercentage(char* s, char letter) {
    int count = 0;
    int totalLength = strlen(s);

    for (int i = 0; i < totalLength; i++) {
        if (s[i] == letter) {
            count++;
        }
    }

    if (totalLength == 0) {
        return 0; // Edge case when the string is empty
    }

    return (count * 100) / totalLength; // Calculate the percentage and round down
}

int main() {
    char s1[] = "reyyydyl", letter1 = 'y';
    printf("Output: %d\n", letterPercentage(s1, letter1)); // Output: 33

    char s2[] = "jjjj", letter2 = 'k';
    printf("Output: %d\n", letterPercentage(s2, letter2)); // Output: 0

    return 0;
}

```

### CHECK OF BOTH STRINGS ARE ANAGRAM
```C
#include <stdio.h>
#include <string.h>

int main() {
    char str1[100001] = "DSDA"; 
    char str2[100001] = "DSAD";
    
    int len1 = strlen(str1);
    int len2 = strlen(str2);

    if (len1 != len2) {
        printf("NO\n");
        return 0;
    }
    
    // Sort both strings
    for (int i = 0; i < len1; i++) {
        for (int j = i + 1; j < len1; j++) {
            if (str1[i] > str1[j]) {
                char temp = str1[i];
                str1[i] = str1[j];
                str1[j] = temp;
            }
            if (str2[i] > str2[j]) {
                char temp = str2[i];
                str2[i] = str2[j];
                str2[j] = temp;
            }
        }
    }
    // Check if sorted strings are equal
    for (int i = 0; i < len1; i++) {
        if (str1[i] != str2[i]) {
            printf("NO\n");
            return 0;
        }
    }
    
    printf("YES\n");
    return 0;
}

```

### LONGEST SUBSTRING W/O REPEATING CHARACTERS

```C

Example abcabcbb 1: 3
Example bbbbb 2: 1
Example pwwkew 3: 3


#include <stdio.h>
#include <string.h>

int lengthOfLongestSubstring(char *s) {
    int n = strlen(s);
    int longest = 0;
    int start = 0;
    int charIndex[256]; 

    memset(charIndex, -1, sizeof(charIndex));

    for (int end = 0; end < n; end++) {
        if (charIndex[s[end]] != -1) {
            // If the character is found in the substring, update the start index
            start = (start > charIndex[s[end]] + 1) ? start : charIndex[s[end]] + 1;
        }
        // Update the character's index
        charIndex[s[end]] = end;
        // Update the length of the longest substring
        longest = (longest > end - start + 1) ? longest : end - start + 1;
    }

    return longest;
}

int main() {
    char s1[] = "abcabcbb";
    char s2[] = "bbbbb";
    char s3[] = "pwwkew";

    printf("Example 1: %d\n", lengthOfLongestSubstring(s1)); // Output: 3
    printf("Example 2: %d\n", lengthOfLongestSubstring(s2)); // Output: 1
    printf("Example 3: %d\n", lengthOfLongestSubstring(s3)); // Output: 3

    return 0;
}
```


### LONGEST PALINDROMIC SUBSTRING

```C

#include <stdio.h>
#include <string.h>

char* longestPalindrome(char* s) {
    int n = strlen(s);
    int start = 0, maxLength = 1;
    int dp[n][n]; // Create a 2D array to store the results of subproblems

    // Initialize dp[i][i] as true because single characters are palindromes
    for (int i = 0; i < n; ++i)
        dp[i][i] = 1;

    // Check for palindromes of length 2
    for (int i = 0; i < n - 1; ++i) {
        if (s[i] == s[i + 1]) {
            dp[i][i + 1] = 1;
            start = i;
            maxLength = 2;
        }
    }

    // Check for palindromes of length greater than 2
    for (int len = 3; len <= n; ++len) {
        for (int i = 0; i < n - len + 1; ++i) {
            int j = i + len - 1;
            if (s[i] == s[j] && dp[i + 1][j - 1]) {
                dp[i][j] = 1;
                start = i;
                maxLength = len;
            }
        }
    }

    // Allocate memory for the result substring
    char* result = (char*)malloc((maxLength + 1) * sizeof(char));
    strncpy(result, s + start, maxLength);
    result[maxLength] = '\0'; // Null-terminate the string

    return result;
}

int main() {
    char s1[] = "babad";
    char s2[] = "cbbd";

    printf("Example 1: %s\n", longestPalindrome(s1)); // Output: "bab" or "aba"
    printf("Example 2: %s\n", longestPalindrome(s2)); // Output: "bb"

    return 0;
}

```


### STRING TO INTEGER (ATOI)

```C

#include <stdio.h>
#include <ctype.h> 

int myAtoi(char *s) {
    int sign = 1; 
    int result = 0;
    int i = 0;

    while (s[i] == ' ')
        i++;

    if (s[i] == '+' || s[i] == '-') {
        sign = (s[i++] == '-') ? -1 : 1;
    }

    while (isdigit(s[i])) {
        if (result > INT_MAX / 10 || (result == INT_MAX / 10 && s[i] - '0' > INT_MAX % 10)) {
            return (sign == 1) ? INT_MAX : INT_MIN;
        }
        result = result * 10 + (s[i++] - '0');
    }

    return sign * result;
}

int main() {
    char s1[] = "42";
    char s2[] = "   -42";
    char s3[] = "4193 with words";

    printf("Example 1: %d\n", myAtoi(s1)); // Output: 42
    printf("Example 2: %d\n", myAtoi(s2)); // Output: -42
    printf("Example 3: %d\n", myAtoi(s3)); // Output: 4193

    return 0;
}

```


### REGULAR EXPRESSION MATCHING

```C

#include <stdio.h>
#include <stdbool.h>
#include <string.h>

bool isMatch(char *s, char *p) {
    if (*p == '\0') {
        return *s == '\0'; 
    }

    bool firstMatch = (*s != '\0' && (*s == *p || *p == '.'));

    if (*(p + 1) == '*') {
        return (isMatch(s, p + 2) || (firstMatch && isMatch(s + 1, p)));
    } else {
        return firstMatch && isMatch(s + 1, p + 1);
    }
}

int main() {
    char s1[] = "aa";
    char p1[] = "a";

    char s2[] = "aa";
    char p2[] = "a*";

    char s3[] = "ab";
    char p3[] = ".*";

    printf("Example 1: %s\n", isMatch(s1, p1) ? "true" : "false"); // Output: false
    printf("Example 2: %s\n", isMatch(s2, p2) ? "true" : "false"); // Output: true
    printf("Example 3: %s\n", isMatch(s3, p3) ? "true" : "false"); // Output: true

    return 0;
}
```

### INTEGER TO ROMAN TO INTEGER
```C
char* intToRoman(int num) {

    char* symbol[] = {"M", "CM", "D", "CD", "C", "XC", "L", "XL", "X", "IX", "V", "IV", "I"};
    int value[] = {1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1};
    char* result = (char*)malloc(20 * sizeof(char));
    result[0] = '\0'; // Initialize the result string

    for (int i = 0; num != 0; ++i) {

        while (num >= value[i]) {
            strcat(result, symbol[i]);
            num -= value[i];
        }
    }
    return result;
}

int romanToInt(char *s) {
    int values[26];
    values['I' - 'A'] = 1;
    values['V' - 'A'] = 5;
    values['X' - 'A'] = 10;
    values['L' - 'A'] = 50;
    values['C' - 'A'] = 100;
    values['D' - 'A'] = 500;
    values['M' - 'A'] = 1000;

    int result = 0;
    int prevValue = 0;

    for (int i = 0; s[i] != '\0'; ++i) {
        int value = values[s[i] - 'A'];
 
        result += (prevValue < value) ? -prevValue : prevValue;
        prevValue = value;
    }

    result += prevValue;

    return result;
}

```


### LARGEST COMMON PREFIX

```C

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char* longestCommonPrefix(char **strs, int strsSize) {
    if (strsSize == 0) return ""; 

    int len = strlen(strs[0]);
    char* prefix = (char*)malloc((len + 1) * sizeof(char));
    if (prefix == NULL) {
        return NULL;
    }
    strncpy(prefix, strs[0], len); 

    for (int i = 0; i < len; i++) {
        char c = strs[0][i]; 
        for (int j = 1; j < strsSize; j++) {

            if (i == strlen(strs[j]) || strs[j][i] != c) {
                prefix[i] = '\0';
                return prefix;
            }
        }
    }

    return prefix; // 
}

int main() {
    char *strs1[] = {"flower", "flow", "flight"};
    char *strs2[] = {"dog", "racecar", "car"};

    printf("Example 1: %s\n", longestCommonPrefix(strs1, 3)); // Output: "fl"
    printf("Example 2: %s\n", longestCommonPrefix(strs2, 3)); // Output: ""

    return 0;
}

```

### LETTER IN COM IN PHONE NO.

```C

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char map[10][5] = {"", "", "abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"};

void search(int cidx, char** res, char* restmp, int* returnSize, int len, char* digits) {
    if (cidx == len) {
        restmp[cidx] = '\0';
        char* tmp = (char*) malloc((len+1) * sizeof(char));
        strncpy(tmp, restmp, len+1);
        res[(*returnSize)++] = tmp;
    } else {
        char* substring = map[digits[cidx] - '0'];
        for (int i = 0; i < strlen(substring); i++) {
            restmp[cidx] = substring[i];
            search(cidx+1, res, restmp, returnSize, len, digits);
        }
    }
}

char** letterCombinations(char* digits, int* returnSize) {
    int len = strlen(digits);
    *returnSize = 0;
    if (len == 0) return NULL;
    int size = 1;
    for (int i = 0; i < len; i++) {
        size *= strlen(map[digits[i] - '0']);
    }
    char** res = (char**) malloc(size * sizeof(char*));
    char* restmp = (char*) malloc((len+1) * sizeof(char));
    search(0, res, restmp, returnSize, len, digits);
	free(restmp);
    return res;
}

int main() {
    char digits[] = "23";
    int returnSize;
    char** result = letterCombinations(digits, &returnSize);
    
    // Print the result
    printf("[");
    for (int i = 0; i < returnSize; i++) {
        printf("%s%s", result[i], (i == returnSize - 1) ? "" : ",");
        free(result[i]); 
    }
    printf("]\n");
    
    free(result); // [ad,ae,af,bd,be,bf,cd,ce,cf]

    return 0;
}

```

### CHECK VALID PARENTHESIS

```C
bool isValid(char* s) {
    char stack[10000];
    int top = -1; // Initialize stack top

    for (int i = 0; s[i] != '\0'; i++) {
        if (s[i] == '(' || s[i] == '[' || s[i] == '{') {
            stack[++top] = s[i]; // Push opening symbols onto stack
        } else {
            // Check if stack is empty or closing symbol does not match top of stack
            if (top == -1 || (s[i] == ')' && stack[top] != '(') || (s[i] == ']' && stack[top] != '[') || (s[i] == '}' && stack[top] != '{')) {
                return false;
            }
            top--; // Pop matching opening symbol from stack
        }
    }

    // If stack is empty, all symbols were matched
    return top == -1;
}

char s1[] = "()"; // Output: true
char s2[] = "()[]{}"; // Output: true
char s3[] = "(]"; // Output: FALSE

// example call 
printf("Example 1: %s\n", isValid(s1) ? "true" : "false"); 


```

### FIND INDEX OF THE FIRST OCCURENCE STRING

```C
#include <stdio.h>
#include <string.h>

int strStr(char *haystack, char *needle) {

    if (needle[0] == '\0')
        return 0;

    char *result = strstr(haystack, needle);

    if (result == NULL)
        return -1;

    return result - haystack;
}

int main() {
    char haystack1[] = "sadbutsad";
    char needle1[] = "sad";

    char haystack2[] = "letleetcode";
    char needle2[] = "leet";

    int index1 = strStr(haystack1, needle1);
    int index2 = strStr(haystack2, needle2);

    printf("Example 1: %d\n", index1); // Output: 0
    printf("Example 2: %d\n", index2); // Output: -1

    return 0;
}

```

### DEFANGING AN IP ADDRESS

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char *defangIPaddr(char *address) {
    // Calculate the length of the defanged IP address
    int len = strlen(address);
    int defangedLen = len + 6; // Each '.' is replaced by "[.]"

    // Allocate memory for the defanged IP address
    char *defangedAddress = (char *)malloc(defangedLen + 1); // Plus 1 for the null terminator

    // Iterate through the characters of the original IP address
    int j = 0;
    for (int i = 0; i < len; i++) {
        if (address[i] == '.') {
            // If the current character is a '.', replace it with "[.]" in the defanged address
            defangedAddress[j++] = '[';
            defangedAddress[j++] = '.';
            defangedAddress[j++] = ']';
        } else {
            // Otherwise, copy the character as is
            defangedAddress[j++] = address[i];
        }
    }

    defangedAddress[j] = '\0';

    return defangedAddress;
}

int main() {
    char *address1 = "1.1.1.1";
    char *address2 = "255.100.50.0";

    char *defanged1 = defangIPaddr(address1);
    char *defanged2 = defangIPaddr(address2);

    printf("Example 1: %s\n", defanged1); // Output: "1[.]1[.]1[.]1"
    printf("Example 2: %s\n", defanged2); // Output: "255[.]100[.]50[.]0"


    return 0;
}

```

### FINAL VALUE OF VARIABLE AFTER PERFORMING OPERATIONS

```C
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int finalValueAfterOperations(char **operations, int operationsSize) {
    int X = 0; // Initial value of X

    for (int i = 0; i < operationsSize; i++) {
        if (strcmp(operations[i], "++X") == 0 || strcmp(operations[i], "X++") == 0) {
            X++;
        } else if (strcmp(operations[i], "--X") == 0 || strcmp(operations[i], "X--") == 0) {
            X--;
        }
    }

    return X;
}

int main() {
    char *operations1[] = {"--X", "X++", "X++"};
    int size1 = sizeof(operations1) / sizeof(operations1[0]);
    printf("Example 1: %d\n", finalValueAfterOperations(operations1, size1)); // Output: 1

    return 0;
}

```


### JEWELS AND STONE

```c

#include <stdio.h>
#include <string.h>

int numJewelsInStones(char *jewels, char *stones) {
    int jewelsCount[128] = {0}; 
    
    // Count the occurrences of each stone type
    for (int i = 0; i < strlen(stones); i++) {
        jewelsCount[stones[i]]++;
    }
    
    int totalJewels = 0;
    
    // Count the occurrences of each stone type that is also present in the jewels
    for (int i = 0; i < strlen(jewels); i++) {
        totalJewels += jewelsCount[jewels[i]];
    }
    
    return totalJewels;
}

int main() {
    char *jewels1 = "aA";
    char *stones1 = "aAAbbbb";
    printf("Example 1: %d\n", numJewelsInStones(jewels1, stones1)); // Output: 3

    char *jewels2 = "z";
    char *stones2 = "ZZ";
    printf("Example 2: %d\n", numJewelsInStones(jewels2, stones2)); // Output: 0

    return 0;
}

```


### FIND WORDS CONTAINER CHARACTER

```C

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int* findOccurrences(char** words, int wordsSize, char x, int* returnSize) {
    int* result = (int*)malloc(wordsSize * sizeof(int));
    *returnSize = 0; /

    for (int i = 0; i < wordsSize; i++) {
        for (int j = 0; j < strlen(words[i]); j++) {
            if (words[i][j] == x) {
                result[(*returnSize)++] = i;
                break;
            }
        }
    }

    if (*returnSize == 0) {
        free(result);
        return NULL;
    }
    result = (int*)realloc(result, (*returnSize) * sizeof(int));
    return result;
}

int main() {
    char* words1[] = {"leet", "man", "code"};
    char x1 = 'e';
    int returnSize1;
    
    int wordsLength = sizeof(words1) / sizeof(words1[0]);

    
    int* result1 = findOccurrences(words1, wordsLength, x1, &returnSize1);
    printf("[");
    for (int i = 0; i < returnSize1; i++) {
        printf("%d%s", result1[i], (i == returnSize1 - 1) ? "" : ",");
    }
    printf("]\n");
    free(result1); // [0, 2]
    
    return 0;
    
}

```

### GOAL PARSER 

```C

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char *interpret(char *command) {
    int len = strlen(command);
    char *result = (char *)malloc((len + 1) * sizeof(char));
    int index = 0;

    for (int i = 0; i < len; i++) {
        if (command[i] == 'G') {
            result[index++] = 'G';
        } else if (command[i] == '(' && command[i + 1] == ')') {
            result[index++] = 'o';
            i++; // Skip ')' as well
        } else if (command[i] == '(' && command[i + 1] == 'a' && command[i + 2] == 'l' && command[i + 3] == ')') {
            result[index++] = 'a';
            result[index++] = 'l';
            i += 3; // Skip 'a', 'l', and ')'
        }
    }

    result[index] = '\0'; 

    return result;
}

int main() {
    char *command1 = "G()(al)";
    printf("Example 1: %s\n", interpret(command1)); // Output: "Goal"

    char *command2 = "G()()()()(al)";
    printf("Example 2: %s\n", interpret(command2)); // Output: "Gooooal"

    char *command3 = "(al)G(al)()()G";
    printf("Example 3: %s\n", interpret(command3)); // Output: "alGalooG"

    return 0;
}


```

### LARGEST WORD FOUND IN SENTENCE

```C

#include <stdio.h>
#include <string.h>

int countWords(char *sentence) {
    int count = 0;
    int isWord = 0;

    for (int i = 0; i < strlen(sentence); i++) {

        if (sentence[i] != ' ' && (i == 0 || sentence[i - 1] == ' ')) {
            isWord = 1; 
            count++; 
        } else if (sentence[i] == ' ') {
            isWord = 0; 
        }
    }

    return count;
}

int maxWords(char **sentences, int sentencesSize) {
    int maxCount = 0;


    for (int i = 0; i < sentencesSize; i++) {
        int count = countWords(sentences[i]);  
        if (count > maxCount) {
            maxCount = count; 
        }
    }

    return maxCount;
}

int main() {
    char *sentences1[] = {"alice and bob love leetcode", "i think so too", "this is great thanks very much"};
    printf("Example 1: %d\n", maxWords(sentences1, 3)); // Output: 6

    char *sentences2[] = {"please wait", "continue to fight", "continue to win"};
    printf("Example 2: %d\n", maxWords(sentences2, 3)); // Output: 3

    return 0;
}

```

### SPLIT STRING IN BALANCED STRING

```c

#include <stdio.h>

int balancedStringSplit(char *s) {
    int balance = 0; // Initialize balance count
    int count = 0; 

    for (int i = 0; s[i] != '\0'; i++) {
        if (s[i] == 'L') {
            balance++; 
        } else {
            balance--; 
        }

        if (balance == 0) {
            count++; 
        }
    }

    return count;
}

int main() {
    char s1[] = "RLRRLLRLRL";
    printf("Example 1: %d\n", balancedStringSplit(s1)); // Output: 4

    char s2[] = "RLRRRLLRLL";
    printf("Example 2: %d\n", balancedStringSplit(s2)); // Output: 2

    char s3[] = "LLLLRRRR";
    printf("Example 3: %d\n", balancedStringSplit(s3)); // Output: 1

    return 0;
}
```


### CHECK IF TWO STRING ARRAYS ARE EQUIVALENT

```c

#include <stdio.h>
#include <stdbool.h>
#include <string.h>

bool arrayStringsAreEqual(char **word1, int word1Size, char **word2, int word2Size) {
    char str1[1000] = ""; 
    char str2[1000] = "";

    for (int i = 0; i < word1Size; i++) {
        strcat(str1, word1[i]);
    }
    for (int i = 0; i < word2Size; i++) {
        strcat(str2, word2[i]);
    }
    return strcmp(str1, str2) == 0;
}

int main() {
    // Test cases
    char *word1_1[] = {"ab", "c"};
    char *word2_1[] = {"a", "bc"};
    printf("Example 1: %s\n", arrayStringsAreEqual(word1_1, 2, word2_1, 2) ? "true" : "false"); // Output: true

    char *word1_2[] = {"a", "cb"};
    char *word2_2[] = {"ab", "c"};
    printf("Example 2: %s\n", arrayStringsAreEqual(word1_2, 2, word2_2, 2) ? "true" : "false"); // Output: false

    return 0;
}
```


### Count Items Matching a Rule

```c

#include <stdio.h>
#include <string.h>

int countMatches(char ***items, int itemsSize, int *itemsColSize, char *ruleKey, char *ruleValue) {
    int count = 0;

    for (int i = 0; i < itemsSize; i++) {
        if (strcmp(ruleKey, "type") == 0 && strcmp(items[i][0], ruleValue) == 0) {
            count++;
        } else if (strcmp(ruleKey, "color") == 0 && strcmp(items[i][1], ruleValue) == 0) {
            count++;
        } else if (strcmp(ruleKey, "name") == 0 && strcmp(items[i][2], ruleValue) == 0) {
            count++;
        }
    }

    return count;
}

int main() {
    // Test cases
    char *items_1[][3] = {{"phone","blue","pixel"}, {"computer","silver","lenovo"}, {"phone","gold","iphone"}};
    char ruleKey_1[] = "color";
    char ruleValue_1[] = "silver";
    printf("Example 1: %d\n", countMatches(items_1, 3, (int[]){3, 3, 3}, ruleKey_1, ruleValue_1)); // Output: 1

    char *items_2[][3] = {{"phone","blue","pixel"}, {"computer","silver","phone"}, {"phone","gold","iphone"}};
    char ruleKey_2[] = "type";
    char ruleValue_2[] = "phone";
    printf("Example 2: %d\n", countMatches(items_2, 3, (int[]){3, 3, 3}, ruleKey_2, ruleValue_2)); // Output: 2

    return 0;
}

```


### TRUNCATE OR BASAWASAN BASE SA GIVEN INDEX

```C

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char *truncateSentence(char *s, int k) {
    int len = strlen(s);
    int wordCount = 0;

    // Count the number of words in the sentence
    for (int i = 0; i < len; i++) {
        if (s[i] == ' ')
            wordCount++;
    }
    wordCount++; // Count the last word

    // If the word count is less than or equal to k, return the original sentence
    if (wordCount <= k)
        return s;

    // Extract the first k words
    char *result = (char *)malloc((len + 1) * sizeof(char));
    if (result == NULL) {
        // Memory allocation failed
        return NULL;
    }
    int wordIndex = 0;
    int resultIndex = 0;
    for (int i = 0; i < len && wordIndex < k; i++) {
        if (s[i] == ' ') {
            result[resultIndex++] = ' ';
            wordIndex++;
        } else {
            result[resultIndex++] = s[i];
        }
    }
    result[resultIndex] = '\0'; // Null-terminate the result string

    return result;
}

int main() {
    // Test cases
    char s1[] = "Hello how are you Contestant";
    int k1 = 4;
    printf("Example 1: %s\n", truncateSentence(s1, k1)); // Output: "Hello how are you"

    char s3[] = "chopper is not a tanuki";
    int k3 = 5;
    printf("Example 3: %s\n", truncateSentence(s3, k3)); // Output: "chopper is not a tanuki"

    return 0;
}

```


### SHUFFLE STRING BASED ON INDEX

```C

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char *restoreString(char *s, int *indices, int indicesSize) {
    int len = strlen(s);
    char *result = (char *)malloc((len + 1) * sizeof(char)); 
    if (result == NULL) {
        return NULL;
    }

    for (int i = 0; i < len; i++) {
        result[indices[i]] = s[i];
    }
    result[len] = '\0'; 

    return result;
}

int main() {
    // Test cases
    char s1[] = "codeleet";
    int indices1[] = {4, 5, 6, 7, 0, 2, 1, 3};
    int indicesSize1 = sizeof(indices1) / sizeof(indices1[0]);
    printf("Example 1: %s\n", restoreString(s1, indices1, indicesSize1)); // Output: "leetcode"

    char s2[] = "abc";
    int indices2[] = {1, 0, 2};
    int indicesSize2 = sizeof(indices2) / sizeof(indices2[0]);
    printf("Example 2: %s\n", restoreString(s2, indices2, indicesSize2)); // Output: "bac"

    return 0;
}

```

### FIND THE FIRST PALINDROME IN ARRAY

```C

#include <stdio.h>
#include <stdbool.h>
#include <string.h>

bool isPalindrome(char *str) {
    int len = strlen(str);
    for (int i = 0; i < len / 2; i++) {
        if (str[i] != str[len - i - 1]) {
            return false;
        }
    }
    return true;
}

char *firstPalindrome(char **words, int wordsSize) {
    for (int i = 0; i < wordsSize; i++) {
        if (isPalindrome(words[i])) {
            return words[i];
        }
    }
    return "";
}

int main() {
    char *words1[] = {"abc", "car", "ada", "racecar", "cool"};
    int wordsSize1 = sizeof(words1) / sizeof(words1[0]);
    printf("Example 1: %s\n", firstPalindrome(words1, wordsSize1)); // Output: "ada"

    char *words2[] = {"notapalindrome", "racecar"};
    int wordsSize2 = sizeof(words2) / sizeof(words2[0]);
    printf("Example 2: %s\n", firstPalindrome(words2, wordsSize2)); // Output: "racecar"

    char *words3[] = {"def", "ghi"};
    int wordsSize3 = sizeof(words3) / sizeof(words3[0]);
    printf("Example 3: %s\n", firstPalindrome(words3, wordsSize3)); // Output: ""

    return 0;
}

```

### STRING TO LOWER CASE

```c

#include <stdio.h>
#include <ctype.h>

void toLowerCase(char *s) {
    while (*s != '\0') {
        *s = tolower(*s); 
        s++; 
    }
}

int main() {
    // Test cases
    char s1[] = "Hello";
    toLowerCase(s1);
    printf("Example 1: %s\n", s1); // Output: "hello"

    char s2[] = "here";
    toLowerCase(s2);
    printf("Example 2: %s\n", s2); // Output: "here"

    char s3[] = "LOVELY";
    toLowerCase(s3);
    printf("Example 3: %s\n", s3); // Output: "lovely"

    return 0;
}
```


### MAXIMUM ODD BINARY

```c

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char *maximumOddNumber(char *s) {
    int n = strlen(s);

    // Find the rightmost '1' in the string
    int idx = -1;
    for (int i = n - 1; i >= 0; i--) {
        if (s[i] == '1') {
            idx = i;
            break;
        }
    }

    // If no '1's found, return the original string
    if (idx == -1) {
        return s;
    }

    // Sort the remaining bits in decreasing order
    for (int i = 0; i < idx; i++) {
        for (int j = i + 1; j < idx; j++) {
            if (s[i] < s[j]) {
                char temp = s[i];
                s[i] = s[j];
                s[j] = temp;
            }
        }
    }

    return s;
}

int main() {
    char s1[] = "010";
    printf("Example 1: %s\n", maximumOddNumber(s1)); // Output: "001"

    char s2[] = "0101";
    printf("Example 2: %s\n", maximumOddNumber(s2)); // Output: "1001"

    return 0;
}

```

### CHECK IF PANGRAM IF GOT ALL THE ALPHABETS

```c
#include <stdio.h>
#include <stdbool.h>
#include <string.h>

bool checkIfPangram(char *sentence) {
    bool seen[26] = {false}; 
    
    for (int i = 0; sentence[i] != '\0'; i++) {
        if (sentence[i] >= 'a' && sentence[i] <= 'z') {
            seen[sentence[i] - 'a'] = true;
        }
    }
    
    for (int i = 0; i < 26; i++) {
        if (!seen[i]) {
            return false; // If any flag is false, return false
        }
    }
    
    return true; // If all flags are true, return true
}

int main() {
    // Test cases
    char sentence1[] = "thequickbrownfoxjumpsoverthelazydog";
    printf("Example 1: %s\n", checkIfPangram(sentence1) ? "true" : "false"); // Output: true
    
    char sentence2[] = "abcdefghijklmnopqrstuvwxyz";
    printf("Example 2: %s\n", checkIfPangram(sentence2) ? "true" : "false"); // Output: false
    
    return 0;
}

```

### FAULTY KEYBOARD

```C
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

void reverse(char* s, int idx) {
    int l = 0, r = idx;
    while (l < r) {
        char t = s[l];
        s[l] = s[r];
        s[r] = t;
        l++;
        r--;
    }
}

char* finalString(char* s) {
    int len = strlen(s), ans_idx = 0;
    char* ans = (char*) calloc(len+1, sizeof(char));
    for (int i = 0; i < len; i++) {
        if (i > 0 && s[i] == 'i') {
            reverse(ans, ans_idx-1);
            continue;
        }
        ans[ans_idx++] = s[i];
    }
    return ans;
}

int main() {
    
    char *result = finalString("string");
    printf("output: %s", result); // rtsng
    return 0;
}
```

### REVERSE STRING STILL IN ORDER

```C
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char* reverseWords(char* s) {
    int start = 0;
    int end = 0;
    int len = strlen(s);
    char* ret = malloc((len + 1) * sizeof(char)); 
    if (ret == NULL) {
        printf("Memory allocation failed!\n");
        exit(EXIT_FAILURE);
    }

    while (s[end] != '\0') {
        if (s[end] == ' ') {
            int left = start;
            int right = end - 1;
            while (left < right) {
                char temp = s[left];
                s[left] = s[right];
                s[right] = temp;
                left++;
                right--;
            }
            start = end + 1; 
        }
        end++;
    }

    int left = start;
    int right = end - 1;
    while (left < right) {
        char temp = s[left];
        s[left] = s[right];
        s[right] = temp;
        left++;
        right--;
    }

    strcpy(ret, s);

    return ret;
}

int main() {
    char param_1[] = "Hello World!";
    char* ret = reverseWords(param_1);
    printf("%s\n", ret); // olleH !dlroW
    free(ret); 
    return 0;
}

```

### Count the Number of Consistent Strings

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int countConsistentStrings(char * allowed, char ** words, int size){
    int s = 0 , ans = 0;
    for(int i = 0 ; allowed[i] ; i++){
        s |= 1<<(allowed[i]-'a');
    }
    for(int i = 0 ; i < size ; i++){
        int c = 0;
        for(int j = 0 ; words[i][j] ; j++){
            c |= 1<<(words[i][j]-'a');
        }
        if(s == (c|s)) ans++;
    }
    return ans;
}

int main() {
    char allowed[] = "abc";
    char *words[] = {"a","b","c","ab","ac","bc","abc"};
    int size = sizeof(words) / sizeof(words[0]);
    int consistentCount = countConsistentStrings(allowed, words, size);
    printf("Number of consistent strings: %d\n", consistentCount); // Number of consistent strings: 7
    return 0;
}
```

### SORTING THE SENTENCE

```c

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

struct Word {
    char word[20];
    int position;
};

int compare(const void *a, const void *b) {
    struct Word *wordA = (struct Word *)a;
    struct Word *wordB = (struct Word *)b;
    return wordA->position - wordB->position;
}

char* reconstruct_sentence(char* s) {
    char* token = strtok(s, " ");
    struct Word words[9];
    int count = 0;

    while (token != NULL) {
        sscanf(token, "%[^0-9]%d", words[count].word, &words[count].position);
        count++;
        token = strtok(NULL, " ");
    }

    qsort(words, count, sizeof(struct Word), compare);

    char* original_sentence = malloc(100 * sizeof(char));
    strcpy(original_sentence, words[0].word);
    for (int i = 1; i < count; i++) {
        strcat(original_sentence, " ");
        strcat(original_sentence, words[i].word);
    }

    return original_sentence;
}

int main() {
    char s1[] = "is2 sentence4 This1 a3";
    char s2[] = "Myself2 Me1 I4 and3";

    printf("%s\n", reconstruct_sentence(s1)); // Output: "This is a sentence"
    printf("%s\n", reconstruct_sentence(s2)); // Output: "Me Myself and I"

    return 0;
}

```

### CHECK IF A STRING IS ACRONYM OF THE WORD

```C

#include <stdio.h>
#include <stdbool.h>
#include <string.h>

bool isAcronym(char ** words, int wordsSize, char * s){
    for(int i = 0 ; i < wordsSize ; i++)
    {
        if(!*s)
            return false;
        if(words[i][0] == *s)
            *s++;
    }
    return !*s;
}

int main() {
    char *words1[] = {"alice", "bob", "charlie"};
    char s1[] = "abc";
    int arrayLength = sizeof(words1) / sizeof(words1[0]); 
    printf("Example 1: %s\n", isAcronym(words1, arrayLength, s1) ? "true" : "false"); // Output: true
    return 0;
}

```

### Remove Outermost Parentheses

```c

#include <stdio.h>
#include <string.h>
#include <stdlib.h>

char *removeOuterParentheses(char *s) {
    int n = strlen(s);
    char *result = (char *)malloc((n + 1) * sizeof(char)); // Allocate memory for the result string
    int counter = 0;
    int resultIndex = 0;

    // Iterate through each character in the string
    for (int i = 0; i < n; i++) {
        // For every '(', increment the counter
        if (s[i] == '(' && counter++ > 0) {
            result[resultIndex++] = '('; // Add '(' to the result string
        }
        // For every ')', decrement the counter
        if (s[i] == ')' && --counter > 0) {
            result[resultIndex++] = ')'; // Add ')' to the result string
        }
    }

    result[resultIndex] = '\0'; // Null-terminate the result string
    return result;
}

int main() {
    char s1[] = "(()())(())";
    printf("Example 1: %s\n", removeOuterParentheses(s1)); // Output: "()()()"

    char s2[] = "(()())(())(()(()))";
    printf("Example 2: %s\n", removeOuterParentheses(s2)); // Output: "()()()()(())"

    char s3[] = "()()";
    printf("Example 3: %s\n", removeOuterParentheses(s3)); // Output: ""

    return 0;
}

```

### COUNT ASTERISK

```c

#include <stdio.h>
#include <string.h>

int countAsterisks(char *s) {
    int count = 0;
    int insideBars = 0; // Flag to track if we are inside '|' characters

    // Iterate through each character in the string
    for (int i = 0; s[i] != '\0'; i++) {
        if (s[i] == '|') {
            insideBars = !insideBars; // Toggle the insideBars flag when encountering '|'
        } else if (s[i] == '*' && !insideBars) {
            count++; // Increment the count if '*' is encountered outside '|'
        }
    }

    return count;
}

int main() {
    char s1[] = "l|*e*et|c**o|*de|";
    printf("Example 1: %d\n", countAsterisks(s1)); // Output: 2

    char s2[] = "iamprogrammer";
    printf("Example 2: %d\n", countAsterisks(s2)); // Output: 0

    char s3[] = "yo|uar|e**|b|e***au|tifu|l";
    printf("Example 3: %d\n", countAsterisks(s3)); // Output: 5

    return 0;
}

```


### MAKE SMALLEST PALINDROME

```c

#include <stdio.h>
#include <string.h>

char* makeSmallestPalindrome(char* s) {
    int l = 0, r = strlen(s)-1;
    while (l < r) {
		if (s[l] < s[r]) {
			s[r] = s[l];
		} else {
			s[l] = s[r];
		}
        l++;
        r--;
    }
    return s;
}

int main() {
    char s1[] = "egcfe";
    printf("Example 1: %s\n", makeSmallestPalindrome(s1)); // Output: "efcfe"

    char s2[] = "abcd";
    printf("Example 2: %s\n", makeSmallestPalindrome(s2)); // Output: "abba"

    char s3[] = "seven";
    printf("Example 3: %s\n", makeSmallestPalindrome(s3)); // Output: "neven"

    return 0;
}

```


### REPLACE ALL DIGITS WITH CHARACTERS

```c

#include <stdio.h>
#include <string.h>

char shiftChar(char c, int shift) {
    return c + shift;
}

char* replaceDigits(char* s) {
    int len = strlen(s);
    for (int i = 1; i < len; i+=2) {
        s[i] += s[i-1] - '0';
    }
    return s;
}

int main() {
    char s1[] = "a1c1e1";
    printf("Example 1: %s\n", replaceDigits(s1)); // Output: "abcdef"

    char s2[] = "a1b2c3d4e";
    printf("Example 2: %s\n", replaceDigits(s2)); // Output: "abbdcfdhe"

    return 0;
}

```


### Find Maximum Number of String Pairs

```c

#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int maximumNumberOfStringPairs(char **words, int wordsSize) {
    int pairsCntr = 0;
    int i, j;

    for (i = 0; i < wordsSize; i++) {
        char *reversed_word = malloc(3 * sizeof(char));
        if (reversed_word == NULL) {
            fprintf(stderr, "Memory allocation failed\n");
            exit(1);
        }

        strcpy(reversed_word, words[i]);
        char temp = reversed_word[0];
        reversed_word[0] = reversed_word[1];
        reversed_word[1] = temp;

        for (j = i + 1; j < wordsSize; j++) {
            if (strcmp(reversed_word, words[j]) == 0) {
                pairsCntr++;
            }
        }

        free(reversed_word);
    }

    return pairsCntr;
}


int main() {
    // Example test cases
    char *words1[] = {"cd","ac","dc","ca","zz"};
    int arrayLength = sizeof(words1) / sizeof(words1[0]); 
    int pairs1 = maximumNumberOfStringPairs(words1, arrayLength);
    printf("Pairs in words1: %d\n", pairs1); // Expected output: 2

    char *words2[] = {"ab","ba","cc"};
    int arrayLength2 = sizeof(words2) / sizeof(words2[0]); 
    int pairs2 = maximumNumberOfStringPairs(words2, arrayLength2);
    printf("Pairs in words2: %d\n", pairs2); // Expected output: 1

    return 0;
}

```


### REVERSE PREFIX IN STRING

```c

#include <stdio.h>
#include <string.h>

char *reversePrefix(char *word, char ch) {
    int len = strlen(word);
    for (int i = 0; i < len; i++) {
        if (word[i] == ch) {
            for (int j = 0; j < (i + 1) / 2; j++) {
                char temp = word[j];
                word[j] = word[i - j];
                word[i - j] = temp;
            }
            break;
        }
    }
    return word;
}

int main() {
    char word1[] = "abcdefd";
    char ch1 = 'd';
    printf("Example 1: %s\n", reversePrefix(word1, ch1)); // Output: "dcbaefd"

    char word2[] = "xyxzxe";
    char ch2 = 'z';
    printf("Example 2: %s\n", reversePrefix(word2, ch2)); // Output: "zxyxxe"

    char word3[] = "abcd";
    char ch3 = 'z';
    printf("Example 3: %s\n", reversePrefix(word3, ch3)); // Output: "abcd"

    return 0;
}


```

### RINGS AND RODS

```c

#include <stdio.h>
#include <string.h>

int countPoints(char * rings){
    int i = 0, ans = 0, l = strlen(rings);
    int a[10] = {0};
    
    while(i < l){
        switch(rings[i]){
                case 'R':
                    a[rings[i + 1] - '0'] |= 0b1;
                    break;
                case 'G':
                    a[rings[i + 1] - '0'] |= 0b10;
                    break;
                case 'B':
                    a[rings[i + 1] - '0'] |= 0b100;
                    break;
        }        
        i += 2;
    }
    
    for(i = 0; i < 10; i++){
        if(a[i] == 7)
            ans++;
    }
    
    return ans;
}

int main() {
    char rings1[] = "B0R0G0R9R0B0G0";
    printf("Output: %d\n", countPoints(rings1)); // Output: 1

    char rings2[] = "G4";
    printf("Output: %d\n", countPoints(rings2)); // Output: 0

    char rings3[] = "B0B6G0R6R0R6G9";
    printf("Output: %d\n", countPoints(rings3)); // Output: 1

    return 0;
}

```

### COUNT SUBSTRINGS

```c

#include <stdio.h>
#include <string.h>

int countSubstrings(char **patterns, int patternsSize, char *word) {
    int count = 0;
    int wordLen = strlen(word);

    for (int i = 0; i < patternsSize; i++) {
        char *pattern = patterns[i];
        int patternLen = strlen(pattern);
        
        for (int j = 0; j <= wordLen - patternLen; j++) {
            if (strncmp(word + j, pattern, patternLen) == 0) {
                count++;
                break; // Move to the next pattern
            }
        }
    }

    return count;
}

int main() {
    char *patterns1[] = {"a", "abc", "bc", "d"};
    int patternsSize1 = sizeof(patterns1) / sizeof(patterns1[0]);
    char word1[] = "abc";
    printf("Output: %d\n", countSubstrings(patterns1, patternsSize1, word1)); // Output: 3

    char *patterns2[] = {"a", "b", "c"};
    int patternsSize2 = sizeof(patterns2) / sizeof(patterns2[0]);
    char word2[] = "aaaaabbbbb";
    printf("Output: %d\n", countSubstrings(patterns2, patternsSize2, word2)); // Output: 2

    char *patterns3[] = {"a", "a", "a"};
    int patternsSize3 = sizeof(patterns3) / sizeof(patterns3[0]);
    char word3[] = "ab";
    printf("Output: %d\n", countSubstrings(patterns3, patternsSize3, word3)); // Output: 3

    return 0;
}

```

### INCREASE DECREASING STRING

```c

#include <stdlib.h>
#include <string.h>
#include <stdio.h>

char * sortString(char * s){
    char *result = calloc(strlen(s) + 1, sizeof(char));
    int dp[26] = {0};    
    for(int i = 0;i<strlen(s);i++){
        dp[s[i] - 'a'] += 1;
    }    
    int r_count = 0;
    while(r_count < strlen(s)){         
        for(int i = 0;i<26;i++){
            if (dp[i] > 0){
                result[r_count++] = 'a' + i;                
            }
            dp[i]--;
        }
        for(int i = 25;i>=0;i--){
            if (dp[i] > 0){
                result[r_count++] = 'a' + i;                
            }
            dp[i]--;
        }
    }
    result[strlen(s)] = '\0';
    return result;
}

int main() {
    char s1[] = "aaaabbbbcccc";
    printf("Output: %s\n", sortString(s1)); // Output: "abccbaabccba"

    char s2[] = "rat";
    printf("Output: %s\n", sortString(s2)); // Output: "art"

    return 0;
}

```

### Remove Palindromic Subsequences

```c

#include <stdio.h>
#include <stdbool.h>
#include <string.h>

bool isPalindrome(char* s, int start, int end) {
    while (start < end) {
        if (s[start] != s[end]) {
            return false;
        }
        start++;
        end--;
    }
    return true;
}

int removePalindromeSub(char* s) {
    int n = strlen(s);
    if (n == 0) {
        return 0; // Empty string requires 0 steps
    }
    if (isPalindrome(s, 0, n - 1)) {
        return 1; // If s is already a palindrome, remove it in 1 step
    }
    return 2; // If s is not a palindrome, remove each palindrome subsequence in 1 step
}

int main() {
    char s1[] = "ababa";
    printf("Output: %d\n", removePalindromeSub(s1)); // Output: 1

    char s2[] = "abb";
    printf("Output: %d\n", removePalindromeSub(s2)); // Output: 2

    char s3[] = "baabb";
    printf("Output: %d\n", removePalindromeSub(s3)); // Output: 2

    return 0;
}

```

### Check if Word Equals Summation of Two Words
```c

#include <stdio.h>
#include <stdbool.h>
#include <string.h>

bool isPalindrome(char* s, int start, int end) {
    while (start < end) {
        if (s[start] != s[end]) {
            return false;
        }
        start++;
        end--;
    }
    return true;
}

int removePalindromeSub(char* s) {
    int n = strlen(s);
    if (n == 0) {
        return 0; // Empty string requires 0 steps
    }
    if (isPalindrome(s, 0, n - 1)) {
        return 1; // If s is already a palindrome, remove it in 1 step
    }
    return 2; // If s is not a palindrome, remove each palindrome subsequence in 1 step
}

int main() {
    char s1[] = "ababa";
    printf("Output: %d\n", removePalindromeSub(s1)); // Output: 1

    char s2[] = "abb";
    printf("Output: %d\n", removePalindromeSub(s2)); // Output: 2

    char s3[] = "baabb";
    printf("Output: %d\n", removePalindromeSub(s3)); // Output: 2

    return 0;
}

```


### COUNT VOWELS BASED ON RANGE
```c

#include <stdio.h>F
#include <string.h>

int isVowel(char c) {
    return c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u';
}

int countVowelStrings(char** words, int wordsSize, int left, int right) {
    int count = 0;

    for (int i = left; i <= right; i++) {
        char* word = words[i];
        int length = strlen(word);

        if (isVowel(word[0]) && isVowel(word[length - 1])) {
            count++;
        }
    }

    return count;
}

int main() {
    char* words1[] = {"are", "amy", "u"};
    int left1 = 0, right1 = 2;
    printf("Output: %d\n", countVowelStrings(words1, 3, left1, right1)); // Output: 2

    char* words2[] = {"hey", "aeo", "mu", "ooo", "artro"};
    int left2 = 1, right2 = 4;
    printf("Output: %d\n", countVowelStrings(words2, 5, left2, right2)); // Output: 3

    return 0;
}

```

### IF ALL A APPEARS FIRST BEFORE B

```c
#include <stdio.h>
#include <stdbool.h>
#include <string.h>

bool checkString(char * s){
    int len = strlen(s);
    for(int i = 0; i < len; i++){
        if(s[i] == 'b'){
            for(int j = i+1; j < len; j++){
                if(s[j] == 'a')
                    return false;
            }
        }
    }

    return true;
}
int main() {
    // Test cases
    char s1[] = "aaabbb";
    char s2[] = "abab";
    char s3[] = "bbb";

    printf("Output for s1: %s\n", checkString(s1) ? "true" : "false"); // Expected output: true
    printf("Output for s2: %s\n", checkString(s2) ? "true" : "false"); // Expected output: false
    printf("Output for s3: %s\n", checkString(s3) ? "true" : "false"); // Expected output: true

    return 0;
}
    
```

### COUNT THE NUMBER OF STRINGS THAT STARTS AND ENDS WITH VOWELS

```c

#include <stdio.h>
#include <string.h>

int countVowelStrings(char **words, int wordsSize) {
    int count = 0;

    for (int i = 0; i < wordsSize; i++) {
        char *word = words[i];
        int length = strlen(word);

        if ((word[0] == 'a' || word[0] == 'e' || word[0] == 'i' || word[0] == 'o' || word[0] == 'u') &&
            (word[length - 1] == 'a' || word[length - 1] == 'e' || word[length - 1] == 'i' || word[length - 1] == 'o' || word[length - 1] == 'u')) {
            count++;
        }
    }

    return count;
}

int main() {
    char *words1[] = {"spple", "orange", "elephant", "umbrella"};
    int wordsSize1 = sizeof(words1) / sizeof(words1[0]);
    printf("Output: %d\n", countVowelStrings(words1, wordsSize1)); // Output: 2

    char *words2[] = {"apple", "orange", "elephant", "umbrella", "aardvark"};
    int wordsSize2 = sizeof(words2) / sizeof(words2[0]);
    printf("Output: %d\n", countVowelStrings(words2, wordsSize2)); // Output: 3

    return 0;
}

```

### SHORTEST DISTANCE TO A CHARACTER

```c

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int* shortestToChar(char *s, char c, int* returnSize) {
    int len = strlen(s);
    int* result = (int*)malloc(len * sizeof(int));
    *returnSize = len;

    int lastSeen = -len;

    for (int i = 0; i < len; i++) {
        if (s[i] == c) {
            lastSeen = i;
        }
        result[i] = i - lastSeen;
    }

    lastSeen = 2 * len;

    for (int i = len - 1; i >= 0; i--) {
        if (s[i] == c) {
            lastSeen = i;
        }
        result[i] = (result[i] < lastSeen - i) ? result[i] : (lastSeen - i);
    }

    return result;
}

int main() {
    char s1[] = "loveleetcode";
    char c1 = 'e';
    int returnSize1;
    int* result1 = shortestToChar(s1, c1, &returnSize1);
    printf("Output: [");
    for (int i = 0; i < returnSize1; i++) {
        printf("%d", result1[i]);
        if (i < returnSize1 - 1) {
            printf(",");
        }
    }


    return 0;
}

```

