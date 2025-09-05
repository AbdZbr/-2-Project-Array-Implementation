#include <iostream>
using namespace std;

struct Element {
    int row;
    int col;
    int value;
};

class SparseMatrix {
private:
    Element* elements;
    int maxSize;
    int count;
    int rows;
    int cols;

public:
    SparseMatrix(int r, int c, int size) {
        rows = r;
        cols = c;
        maxSize = size;
        count = 0;
        elements = new Element[maxSize];
    }

    ~SparseMatrix() {
        delete[] elements;
    }

    void insert(int r, int c, int val) {
        if (val == 0) return;
        if (count >= maxSize) {
            cout << "Array full, cannot insert more elements.\n";
            return;
        }
        elements[count].row = r;
        elements[count].col = c;
        elements[count].value = val;
        count++;
    }

    void display() {
        int k = 0;
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                if (k < count && elements[k].row == i && elements[k].col == j)
                    cout << elements[k++].value << " ";
                else
                    cout << "0 ";
            }
            cout << endl;
        }
    }

    SparseMatrix add(SparseMatrix& other) {
        if (rows != other.rows || cols != other.cols) {
            cout << "Matrix dimensions do not match!\n";
            return SparseMatrix(0, 0, 0);
        }

        SparseMatrix result(rows, cols, maxSize + other.maxSize);

        int i = 0, j = 0;
        while (i < count && j < other.count) {
            if (elements[i].row < other.elements[j].row ||
               (elements[i].row == other.elements[j].row && elements[i].col < other.elements[j].col)) {
                result.insert(elements[i].row, elements[i].col, elements[i].value);
                i++;
            } else if (elements[i].row == other.elements[j].row && elements[i].col == other.elements[j].col) {
                result.insert(elements[i].row, elements[i].col, elements[i].value + other.elements[j].value);
                i++; j++;
            } else {
                result.insert(other.elements[j].row, other.elements[j].col, other.elements[j].value);
                j++;
            }
        }

        while (i < count) result.insert(elements[i].row, elements[i].col, elements[i].value), i++;
        while (j < other.count) result.insert(other.elements[j].row, other.elements[j].col, other.elements[j].value), j++;

        return result;
    }
};

int main() {
    SparseMatrix mat1(3, 3, 5);
    mat1.insert(0, 0, 1);
    mat1.insert(0, 2, 2);
    mat1.insert(1, 1, 3);

    cout << "Matrix 1:" << endl;
    mat1.display();

    SparseMatrix mat2(3, 3, 5);
    mat2.insert(0, 0, 4);
    mat2.insert(0, 1, 5);
    mat2.insert(1, 1, 6);

    cout << "\nMatrix 2:" << endl;
    mat2.display();

    SparseMatrix sum = mat1.add(mat2);
    cout << "\nSum of Matrix 1 and Matrix 2:" << endl;
    sum.display();

    return 0;
}
