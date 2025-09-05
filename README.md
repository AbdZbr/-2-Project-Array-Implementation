# -2-Project-Array-Implementation

Data Structure
Each non-zero element is stored in a struct Element with row, col, and value. The SparseMatrix class contains a dynamic array of Elements and keeps track of the total rows, columns, maximum allowed non-zero elements, and the current count.

Insertion
The insert method adds only non-zero values to the array. It ignores zeros to maintain sparsity and prevents overflow if the array is full.

Display
The display method prints the full matrix. It loops through all row and column indices and prints a value if a non-zero element exists; otherwise, it prints 0.

Addition of Matrices
The add method sums two sparse matrices by iterating through their non-zero elements in order. Elements in the same position are summed, while remaining elements are added as-is.

Challenges & Learning Points
Aligning non-zero elements for addition was tricky initially, especially when elements existed in only one matrix. Using while-loops with careful row and column comparisons solved this. I also learned the importance of dynamic memory management and indexing for efficient sparse matrix operations.
