# C Piscine - C07

![42 Badge](https://img.shields.io/badge/42-C_Piscine-brightgreen)
![C Badge](https://img.shields.io/badge/Language-C-blue)
![Status Badge](https://img.shields.io/badge/Status-Completed-success)

## What I Learned

Through this C07 module of the 42 Piscine, I developed crucial skills in dynamic memory management and advanced string manipulation:

- **Dynamic memory allocation** - Mastered malloc() usage for creating flexible data structures
- **Memory management** - Learned proper allocation, usage, and deallocation patterns to prevent leaks
- **String duplication and manipulation** - Implemented efficient string copying and concatenation algorithms
- **Array generation** - Created dynamic integer arrays with specified ranges and properties
- **Base conversion algorithms** - Developed number base conversion between arbitrary bases
- **String parsing and splitting** - Built robust string tokenization with custom delimiters
- **Pointer manipulation** - Advanced pointer arithmetic and double pointer usage
- **Error handling** - Implemented comprehensive input validation and edge case management
- **Algorithm optimization** - Balanced performance with memory efficiency in complex operations
- **Modular programming** - Created reusable functions with clear interfaces and responsibilities

This module reinforced my understanding of low-level memory operations and advanced C programming concepts essential for systems programming.

## About the Project

C07 focuses on dynamic memory allocation and advanced string/array manipulation. This module introduces malloc() and teaches proper memory management through increasingly complex exercises that build upon each other.

## Implementation Details

The module consists of 6 exercises demonstrating progressive complexity in memory management:

### Exercise 00: ft_strdup
**Purpose:** String duplication with dynamic allocation
```c
char *ft_strdup(char *src);
```
- Replicates the behavior of the standard `strdup()` function
- Allocates memory for a new string and copies the source
- Returns a pointer to the newly allocated duplicate string
- Handles memory allocation failure gracefully

**Key Learning:** Basic malloc usage and string copying patterns

### Exercise 01: ft_range
**Purpose:** Dynamic integer array generation
```c
int *ft_range(int min, int max);
```
- Creates an array containing all integers from min (inclusive) to max (exclusive)
- Dynamically allocates memory based on the range size
- Returns NULL if min >= max (invalid range)
- Demonstrates array allocation and population in one function

**Key Learning:** Array allocation and range validation

### Exercise 02: ft_ultimate_range
**Purpose:** Enhanced range function with size return
```c
int ft_ultimate_range(int **range, int min, int max);
```
- Allocates and populates an integer array like ft_range
- Uses double pointer to modify the caller's pointer
- Returns the size of the created array (-1 on allocation failure)
- Sets range to NULL and returns 0 for invalid ranges

**Key Learning:** Double pointer manipulation and function return semantics

### Exercise 03: ft_strjoin
**Purpose:** String array concatenation with separator
```c
char *ft_strjoin(int size, char **strs, char *sep);
```
- Concatenates an array of strings with a specified separator
- Calculates total required memory before allocation
- Handles empty arrays by returning an empty but freeable string
- Efficiently manages memory for variable-length result strings

**Key Learning:** Complex string manipulation and memory calculation

### Exercise 04: ft_convert_base
**Purpose:** Number base conversion between arbitrary bases
```c
char *ft_convert_base(char *nbr, char *base_from, char *base_to);
```
- Converts numbers between any valid bases (binary, octal, decimal, hex, etc.)
- Validates base strings for duplicates and forbidden characters
- Handles negative numbers and whitespace like ft_atoi_base
- Returns dynamically allocated string representation

**Key Learning:** Algorithm design and base arithmetic implementation

### Exercise 05: ft_split
**Purpose:** String tokenization with custom delimiters
```c
char **ft_split(char *str, char *charset);
```
- Splits a string into an array of substrings using multiple delimiters
- Any character in charset acts as a separator
- Returns NULL-terminated array of dynamically allocated strings
- Skips empty tokens and handles consecutive separators

**Key Learning:** Complex parsing algorithms and multi-level memory allocation

## Technical Challenges Overcome

- **Memory leak prevention** - Ensuring all allocated memory is properly freed on error paths
- **Efficient memory calculation** - Pre-calculating exact memory requirements to avoid reallocation
- **Edge case handling** - Managing NULL inputs, empty strings, and invalid parameters
- **Multi-level allocation** - Managing arrays of pointers to allocated strings (ft_split)
- **Base validation** - Implementing robust checks for valid number base representations
- **Parser state management** - Tracking parsing state in complex string processing functions

## Memory Management Patterns

Each exercise demonstrates different memory management patterns:

1. **Simple allocation** (ft_strdup): Allocate, populate, return
2. **Size-based allocation** (ft_range): Calculate size, allocate array
3. **Indirect allocation** (ft_ultimate_range): Modify caller's pointer via double pointer
4. **Pre-calculated allocation** (ft_strjoin): Calculate total size before single allocation
5. **Complex validation** (ft_convert_base): Validate inputs before processing
6. **Multi-level allocation** (ft_split): Allocate array of pointers, then individual strings

## Usage Examples

```c
#include <stdio.h>
#include <stdlib.h>

// Example usage of implemented functions
int main(void)
{
    // ft_strdup example
    char *original = "Hello, 42!";
    char *duplicate = ft_strdup(original);
    printf("Original: %s\nDuplicate: %s\n", original, duplicate);
    free(duplicate);
    
    // ft_range example
    int *range = ft_range(5, 10);
    for (int i = 0; i < 5; i++)
        printf("%d ", range[i]); // Prints: 5 6 7 8 9
    free(range);
    
    // ft_strjoin example
    char *strs[] = {"Hello", "42", "School"};
    char *joined = ft_strjoin(3, strs, " - ");
    printf("%s\n", joined); // Prints: Hello - 42 - School
    free(joined);
    
    // ft_split example
    char **tokens = ft_split("one,two;three,four", ",;");
    for (int i = 0; tokens[i]; i++)
    {
        printf("Token %d: %s\n", i, tokens[i]);
        free(tokens[i]);
    }
    free(tokens);
    
    return (0);
}
```

## Compilation

```bash
# Compile individual exercises
cc -Wall -Wextra -Werror ft_strdup.c -o test_strdup

# Compile with test main (uncomment main function in source)
cc -Wall -Wextra -Werror ft_range.c -o test_range

# For ft_convert_base (multiple files)
cc -Wall -Wextra -Werror ft_convert_base.c ft_convert_base2.c -o test_convert
```

## Project Structure

```
C07/
├── ex00/ft_strdup.c           # String duplication
├── ex01/ft_range.c            # Integer range generation
├── ex02/ft_ultimate_range.c   # Enhanced range with size return
├── ex03/ft_strjoin.c          # String array concatenation
├── ex04/                      # Base conversion system
│   ├── ft_convert_base.c      # Main conversion logic
│   └── ft_convert_base2.c     # Helper functions
└── ex05/ft_split.c            # String tokenization
```

## Key Takeaways

This module taught me that effective memory management requires:
- **Planning before allocation** - Understanding exact memory requirements
- **Defensive programming** - Validating all inputs and handling edge cases
- **Clean error handling** - Ensuring no memory leaks even when errors occur
- **Algorithm efficiency** - Minimizing allocations while maintaining functionality
- **Code modularity** - Breaking complex problems into manageable helper functions

These skills are fundamental for any C programmer and essential for systems-level development where memory management is critical.

---

*This project was completed as part of the 42 School C Piscine, demonstrating proficiency in dynamic memory allocation, string manipulation, and advanced C programming concepts.*
