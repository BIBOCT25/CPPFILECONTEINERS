# CPPFILECONTEINERS

| [📁 **Работа с файлами**](./README.md) | 📦 **Работа с контейнерами** (Вы здесь) |
| :---: | :---: |

### 1. Создание 5×5 вектора
```cpp
#include <iostream>
#include <vector>
#include <iomanip>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");
    
    // Создание 5x5 вектора, заполненного нулями
    vector<vector<int>> vec(5, vector<int>(5, 0));
    
    // Заполнение значениями 1..25
    int counter = 1;
    for (int i = 0; i < 5; i++) {
        for (int j = 0; j < 5; j++) {
            vec[i][j] = counter++;
        }
    }
    
    // Вывод матрицы
    cout << "=== СОЗДАНИЕ МАТРИЦЫ 5x5 (VECTOR) ===" << endl;
    cout << "Размер: " << vec.size() << "x" << vec[0].size() << endl;
    for (int i = 0; i < 5; i++) {
        for (int j = 0; j < 5; j++) {
            cout << setw(4) << vec[i][j];
        }
        cout << endl;
    }
    
    return 0;
}
```

### 2. Увеличение размера до 6×6 и вывод
```cpp
#include <iostream>
#include <vector>
#include <iomanip>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");
    
    // Создаём исходную матрицу 5x5
    vector<vector<int>> vec(5, vector<int>(5));
    int counter = 1;
    for (int i = 0; i < 5; i++) {
        for (int j = 0; j < 5; j++) {
            vec[i][j] = counter++;
        }
    }
    
    cout << "=== ИСХОДНАЯ МАТРИЦА 5x5 ===" << endl;
    for (int i = 0; i < 5; i++) {
        for (int j = 0; j < 5; j++) {
            cout << setw(4) << vec[i][j];
        }
        cout << endl;
    }
    
    // Увеличение до 6x6: добавляем новую строку
    vec.push_back(vector<int>(6, 0));
    
    // Добавляем новый столбец к существующим 5 строкам
    for (int i = 0; i < 5; i++) {
        vec[i].push_back(0);
    }
    
    // Заполняем новые ячейки
    int val = 26;
    for (int j = 0; j < 6; j++) {
        vec[5][j] = val++;  // новая строка
    }
    for (int i = 0; i < 5; i++) {
        vec[i][5] = val++;  // новый столбец
    }
    
    cout << "\n=== ПОСЛЕ УВЕЛИЧЕНИЯ ДО 6x6 ===" << endl;
    cout << "Размер: " << vec.size() << "x" << vec[0].size() << endl;
    for (int i = 0; i < 6; i++) {
        for (int j = 0; j < 6; j++) {
            cout << setw(4) << vec[i][j];
        }
        cout << endl;
    }
    
    return 0;
}
```

### 3. Увеличение до 7×7 и вывод (перед уменьшением)
```cpp
#include <iostream>
#include <vector>
#include <iomanip>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");
    
    // Создаём матрицу 6x6 (после предыдущего шага)
    vector<vector<int>> vec(6, vector<int>(6));
    int counter = 1;
    for (int i = 0; i < 6; i++) {
        for (int j = 0; j < 6; j++) {
            vec[i][j] = counter++;
        }
    }
    
    cout << "=== ИСХОДНАЯ МАТРИЦА 6x6 ===" << endl;
    for (int i = 0; i < 6; i++) {
        for (int j = 0; j < 6; j++) {
            cout << setw(4) << vec[i][j];
        }
        cout << endl;
    }
    
    // Увеличение до 7x7
    vec.push_back(vector<int>(7, 0));  // новая строка
    for (int i = 0; i < 6; i++) {
        vec[i].push_back(0);           // новый столбец
    }
    
    // Заполняем новые ячейки
    int val = 37;
    for (int j = 0; j < 7; j++) {
        vec[6][j] = val++;
    }
    for (int i = 0; i < 6; i++) {
        vec[i][6] = val++;
    }
    
    cout << "\n=== ПОСЛЕ УВЕЛИЧЕНИЯ ДО 7x7 (ПЕРЕД УМЕНЬШЕНИЕМ) ===" << endl;
    cout << "Размер: " << vec.size() << "x" << vec[0].size() << endl;
    for (int i = 0; i < 7; i++) {
        for (int j = 0; j < 7; j++) {
            cout << setw(4) << vec[i][j];
        }
        cout << endl;
    }
    
    return 0;
}
```

### 4. Уменьшение до 6×6 и вывод
```cpp
#include <iostream>
#include <vector>
#include <iomanip>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");
    
    // Создаём матрицу 7x7
    vector<vector<int>> vec(7, vector<int>(7));
    int counter = 1;
    for (int i = 0; i < 7; i++) {
        for (int j = 0; j < 7; j++) {
            vec[i][j] = counter++;
        }
    }
    
    cout << "=== ИСХОДНАЯ МАТРИЦА 7x7 ===" << endl;
    for (int i = 0; i < 7; i++) {
        for (int j = 0; j < 7; j++) {
            cout << setw(4) << vec[i][j];
        }
        cout << endl;
    }
    
    // Уменьшение до 6x6
    vec.pop_back();  // удаляем последнюю строку
    for (int i = 0; i < 6; i++) {
        vec[i].pop_back();  // удаляем последний столбец в каждой строке
    }
    
    cout << "\n=== ПОСЛЕ УМЕНЬШЕНИЯ ДО 6x6 ===" << endl;
    cout << "Размер: " << vec.size() << "x" << vec[0].size() << endl;
    for (int i = 0; i < 6; i++) {
        for (int j = 0; j < 6; j++) {
            cout << setw(4) << vec[i][j];
        }
        cout << endl;
    }
    
    return 0;
}
```

### 5. Уменьшение до 5×5 и вывод
```cpp
#include <iostream>
#include <vector>
#include <iomanip>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");
    
    // Создаём матрицу 6x6
    vector<vector<int>> vec(6, vector<int>(6));
    int counter = 1;
    for (int i = 0; i < 6; i++) {
        for (int j = 0; j < 6; j++) {
            vec[i][j] = counter++;
        }
    }
    
    cout << "=== ИСХОДНАЯ МАТРИЦА 6x6 ===" << endl;
    for (int i = 0; i < 6; i++) {
        for (int j = 0; j < 6; j++) {
            cout << setw(4) << vec[i][j];
        }
        cout << endl;
    }
    
    // Уменьшение до 5x5
    vec.pop_back();  // удаляем последнюю строку
    for (int i = 0; i < 5; i++) {
        vec[i].pop_back();  // удаляем последний столбец
    }
    
    cout << "\n=== ПОСЛЕ УМЕНЬШЕНИЯ ДО 5x5 ===" << endl;
    cout << "Размер: " << vec.size() << "x" << vec[0].size() << endl;
    for (int i = 0; i < 5; i++) {
        for (int j = 0; j < 5; j++) {
            cout << setw(4) << vec[i][j];
        }
        cout << endl;
    }
    
    return 0;
}
```

### 6. Уменьшение до 4×4 и вывод
```cpp
#include <iostream>
#include <vector>
#include <iomanip>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");
    
    // Создаём матрицу 5x5
    vector<vector<int>> vec(5, vector<int>(5));
    int counter = 1;
    for (int i = 0; i < 5; i++) {
        for (int j = 0; j < 5; j++) {
            vec[i][j] = counter++;
        }
    }
    
    cout << "=== ИСХОДНАЯ МАТРИЦА 5x5 ===" << endl;
    for (int i = 0; i < 5; i++) {
        for (int j = 0; j < 5; j++) {
            cout << setw(4) << vec[i][j];
        }
        cout << endl;
    }
    
    // Уменьшение до 4x4
    vec.pop_back();  // удаляем последнюю строку
    for (int i = 0; i < 4; i++) {
        vec[i].pop_back();  // удаляем последний столбец
    }
    
    cout << "\n=== ПОСЛЕ УМЕНЬШЕНИЯ ДО 4x4 ===" << endl;
    cout << "Размер: " << vec.size() << "x" << vec[0].size() << endl;
    for (int i = 0; i < 4; i++) {
        for (int j = 0; j < 4; j++) {
            cout << setw(4) << vec[i][j];
        }
        cout << endl;
    }
    
    return 0;
}
```

### 7. Изменение значений элементов циклом for
```cpp
#include <iostream>
#include <vector>
#include <iomanip>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");
    
    // Создаём матрицу 4x4 с начальными значениями
    vector<vector<int>> vec(4, vector<int>(4));
    int counter = 1;
    for (int i = 0; i < 4; i++) {
        for (int j = 0; j < 4; j++) {
            vec[i][j] = counter++;
        }
    }
    
    cout << "=== ИСХОДНАЯ МАТРИЦА 4x4 ===" << endl;
    for (int i = 0; i < 4; i++) {
        for (int j = 0; j < 4; j++) {
            cout << setw(4) << vec[i][j];
        }
        cout << endl;
    }
    
    // Изменение всех элементов циклом for (умножаем на 10)
    for (int i = 0; i < 4; i++) {
        for (int j = 0; j < 4; j++) {
            vec[i][j] = vec[i][j] * 10;
        }
    }
    
    cout << "\n=== ПОСЛЕ УМНОЖЕНИЯ ВСЕХ ЭЛЕМЕНТОВ НА 10 ===" << endl;
    for (int i = 0; i < 4; i++) {
        for (int j = 0; j < 4; j++) {
            cout << setw(4) << vec[i][j];
        }
        cout << endl;
    }
    
    // Изменение элементов по условию (чётные обнуляем)
    for (int i = 0; i < 4; i++) {
        for (int j = 0; j < 4; j++) {
            if (vec[i][j] % 20 == 0) {
                vec[i][j] = 0;
            }
        }
    }
    
    cout << "\n=== ПОСЛЕ ОБНУЛЕНИЯ ЧЁТНЫХ (кратных 20) ===" << endl;
    for (int i = 0; i < 4; i++) {
        for (int j = 0; j < 4; j++) {
            cout << setw(4) << vec[i][j];
        }
        cout << endl;
    }
    
    // Заполнение новыми значениями по формуле
    for (int i = 0; i < 4; i++) {
        for (int j = 0; j < 4; j++) {
            vec[i][j] = (i + 1) * 100 + (j + 1);  // строка*100 + столбец
        }
    }
    
    cout << "\n=== НОВЫЕ ЗНАЧЕНИЯ ПО ФОРМУЛЕ (строка*100 + столбец) ===" << endl;
    for (int i = 0; i < 4; i++) {
        for (int j = 0; j < 4; j++) {
            cout << setw(4) << vec[i][j];
        }
        cout << endl;
    }
    
    return 0;
}
```

### 8. То же самое с std::deque
```cpp
#include <iostream>
#include <deque>
#include <iomanip>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");
    
    // Создание 5x5 deque
    deque<deque<int>> dq(5, deque<int>(5));
    int counter = 1;
    for (int i = 0; i < 5; i++) {
        for (int j = 0; j < 5; j++) {
            dq[i][j] = counter++;
        }
    }
    
    cout << "=== DEQUE 5x5 ===" << endl;
    for (const auto& row : dq) {
        for (int val : row) {
            cout << setw(4) << val;
        }
        cout << endl;
    }
    
    // Увеличение до 6x6
    dq.push_back(deque<int>(6, 0));
    for (int i = 0; i < 5; i++) {
        dq[i].push_back(0);
    }
    int val = 26;
    for (int j = 0; j < 6; j++) dq[5][j] = val++;
    for (int i = 0; i < 5; i++) dq[i][5] = val++;
    
    cout << "\n=== DEQUE 6x6 ===" << endl;
    for (const auto& row : dq) {
        for (int v : row) cout << setw(4) << v;
        cout << endl;
    }
    
    // Уменьшение до 4x4
    dq.pop_back(); dq.pop_back();
    for (int i = 0; i < 4; i++) {
        dq[i].pop_back(); dq[i].pop_back();
    }
    
    cout << "\n=== DEQUE 4x4 ===" << endl;
    for (const auto& row : dq) {
        for (int v : row) cout << setw(4) << v;
        cout << endl;
    }
    
    // Изменение значений
    for (int i = 0; i < 4; i++) {
        for (int j = 0; j < 4; j++) {
            dq[i][j] = dq[i][j] * 10;
        }
    }
    
    cout << "\n=== DEQUE 4x4 (x10) ===" << endl;
    for (const auto& row : dq) {
        for (int v : row) cout << setw(4) << v;
        cout << endl;
    }
    
    return 0;
}
```

### 9. То же самое с std::list
```cpp
#include <iostream>
#include <list>
#include <iomanip>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");
    
    // Создание 5x5 list
    list<list<int>> lst;
    int counter = 1;
    for (int i = 0; i < 5; i++) {
        list<int> row;
        for (int j = 0; j < 5; j++) {
            row.push_back(counter++);
        }
        lst.push_back(row);
    }
    
    cout << "=== LIST 5x5 ===" << endl;
    for (const auto& row : lst) {
        for (int val : row) {
            cout << setw(4) << val;
        }
        cout << endl;
    }
    
    // Увеличение до 6x6
    list<int> newRow(6, 0);
    lst.push_back(newRow);
    int val = 26;
    auto lastRow = lst.end(); --lastRow;
    for (auto& cell : *lastRow) cell = val++;
    for (auto it = lst.begin(); it != lastRow; ++it) {
        it->push_back(val++);
    }
    (*lastRow).push_back(val);
    // Корректировка: заполним правильно
    val = 26;
    for (auto& cell : *lastRow) cell = val++;
    val = 32;
    for (auto it = lst.begin(); it != lastRow; ++it) {
        it->push_back(val++);
    }
    
    cout << "\n=== LIST 6x6 ===" << endl;
    for (const auto& row : lst) {
        for (int v : row) cout << setw(4) << v;
        cout << endl;
    }
    
    // Уменьшение до 4x4
    lst.pop_back(); lst.pop_back();
    for (auto& row : lst) {
        row.pop_back(); row.pop_back();
    }
    
    cout << "\n=== LIST 4x4 ===" << endl;
    for (const auto& row : lst) {
        for (int v : row) cout << setw(4) << v;
        cout << endl;
    }
    
    // Изменение значений
    for (auto& row : lst) {
        for (auto& cell : row) {
            cell = cell * 10;
        }
    }
    
    cout << "\n=== LIST 4x4 (x10) ===" << endl;
    for (const auto& row : lst) {
        for (int v : row) cout << setw(4) << v;
        cout << endl;
    }
    
    return 0;
}
```

### 10. Простой статический 2D массив
```cpp
#include <iostream>
#include <iomanip>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");
    
    // Простой статический массив 5x5
    int arr[5][5];
    
    // Заполнение
    int counter = 1;
    for (int i = 0; i < 5; i++) {
        for (int j = 0; j < 5; j++) {
            arr[i][j] = counter++;
        }
    }
    
    cout << "=== ПРОСТОЙ МАССИВ 5x5 ===" << endl;
    for (int i = 0; i < 5; i++) {
        for (int j = 0; j < 5; j++) {
            cout << setw(4) << arr[i][j];
        }
        cout << endl;
    }
    
    // Изменение значений циклом for
    for (int i = 0; i < 5; i++) {
        for (int j = 0; j < 5; j++) {
            arr[i][j] = arr[i][j] * 10;
        }
    }
    
    cout << "\n=== МАССИВ 5x5 (x10) ===" << endl;
    for (int i = 0; i < 5; i++) {
        for (int j = 0; j < 5; j++) {
            cout << setw(4) << arr[i][j];
        }
        cout << endl;
    }
    
    cout << "\nПРИМЕЧАНИЕ: Статический массив нельзя увеличить/уменьшить!" << endl;
    cout << "Размер фиксирован на этапе компиляции: 5x5" << endl;
    
    return 0;
}
```

### 11. Динамический 2D массив (с изменением размера вручную)
```cpp
#include <iostream>
#include <iomanip>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");
    
    int rows = 5, cols = 5;
    
    // Выделение памяти под динамический массив 5x5
    int** arr = new int*[rows];
    for (int i = 0; i < rows; i++) {
        arr[i] = new int[cols];
    }
    
    // Заполнение
    int counter = 1;
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            arr[i][j] = counter++;
        }
    }
    
    cout << "=== ДИНАМИЧЕСКИЙ МАССИВ 5x5 ===" << endl;
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            cout << setw(4) << arr[i][j];
        }
        cout << endl;
    }
    
    // "Увеличение" до 6x6 (создаём новый массив и копируем)
    int newRows = 6, newCols = 6;
    int** newArr = new int*[newRows];
    for (int i = 0; i < newRows; i++) {
        newArr[i] = new int[newCols];
    }
    
    // Копируем старые значения
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            newArr[i][j] = arr[i][j];
        }
    }
    // Заполняем новые ячейки
    int val = 26;
    for (int j = 0; j < newCols; j++) newArr[5][j] = val++;
    for (int i = 0; i < rows; i++) newArr[i][5] = val++;
    
    // Удаляем старый массив
    for (int i = 0; i < rows; i++) delete[] arr[i];
    delete[] arr;
    
    arr = newArr;
    rows = newRows;
    cols = newCols;
    
    cout << "\n=== ДИНАМИЧЕСКИЙ МАССИВ 6x6 ===" << endl;
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            cout << setw(4) << arr[i][j];
        }
        cout << endl;
    }
    
    // Изменение значений
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            arr[i][j] = arr[i][j] * 10;
        }
    }
    
    cout << "\n=== ДИНАМИЧЕСКИЙ МАССИВ 6x6 (x10) ===" << endl;
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            cout << setw(4) << arr[i][j];
        }
        cout << endl;
    }
    
    // Освобождение памяти
    for (int i = 0; i < rows; i++) delete[] arr[i];
    delete[] arr;
    
    return 0;
}
```

### 12. Демонстрация всех методов вектора (capacity, resize, reserve и т.д.)
```cpp
#include <iostream>
#include <vector>
#include <iomanip>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");
    
    vector<vector<int>> vec;
    
    cout << "=== ДЕМОНСТРАЦИЯ МЕТОДОВ VECTOR ===" << endl;
    
    // reserve
    vec.reserve(5);
    cout << "После reserve(5): size=" << vec.size() 
         << ", capacity=" << vec.capacity() << endl;
    
    // resize
    vec.resize(5, vector<int>(5, 0));
    cout << "После resize(5, vector<int>(5,0)): size=" << vec.size() 
         << ", capacity=" << vec.capacity() << endl;
    
    // Заполнение
    int counter = 1;
    for (int i = 0; i < 5; i++) {
        for (int j = 0; j < 5; j++) {
            vec[i][j] = counter++;
        }
    }
    
    cout << "\nСодержимое 5x5:" << endl;
    for (const auto& row : vec) {
        for (int val : row) cout << setw(4) << val;
        cout << endl;
    }
    
    // at()
    cout << "\nvec.at(2).at(2) = " << vec.at(2).at(2) << endl;
    
    // front() и back()
    cout << "vec.front()[0] = " << vec.front()[0] << endl;
    cout << "vec.back()[4] = " << vec.back()[4] << endl;
    
    // data()
    cout << "vec.data() = " << vec.data() << endl;
    
    // empty()
    cout << "vec.empty() = " << (vec.empty() ? "true" : "false") << endl;
    
    // max_size()
    cout << "vec.max_size() = " << vec.max_size() << endl;
    
    // clear
    vec.clear();
    cout << "\nПосле clear(): size=" << vec.size() 
         << ", capacity=" << vec.capacity() 
         << ", empty=" << (vec.empty() ? "true" : "false") << endl;
    
    // shrink_to_fit
    vec.shrink_to_fit();
    cout << "После shrink_to_fit(): capacity=" << vec.capacity() << endl;
    
    return 0;
}
```

### 13. std::array
```cpp
#include <iostream>
#include <array>
#include <iomanip>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");
    
    // Создание 5x5 через array (размер фиксирован!)
    array<array<int, 5>, 5> arr;
    
    // Заполнение
    int counter = 1;
    for (int i = 0; i < 5; i++) {
        for (int j = 0; j < 5; j++) {
            arr[i][j] = counter++;
        }
    }
    
    cout << "=== std::array 5x5 ===" << endl;
    cout << "Размер: " << arr.size() << "x" << arr[0].size() << endl;
    for (const auto& row : arr) {
        for (int val : row) {
            cout << setw(4) << val;
        }
        cout << endl;
    }
    
    // Методы
    cout << "\nМетоды array:" << endl;
    cout << "size(): " << arr.size() << endl;
    cout << "max_size(): " << arr.max_size() << endl;
    cout << "empty(): " << (arr.empty() ? "true" : "false") << endl;
    cout << "front()[0][0]: " << arr.front()[0] << endl;
    cout << "back()[4][4]: " << arr.back()[4] << endl;
    cout << "at(2).at(2): " << arr.at(2).at(2) << endl;
    cout << "data(): " << arr.data() << endl;
    
    // Изменение значений циклом for
    for (int i = 0; i < 5; i++) {
        for (int j = 0; j < 5; j++) {
            arr[i][j] = arr[i][j] * 10;
        }
    }
    
    cout << "\n=== ПОСЛЕ УМНОЖЕНИЯ НА 10 ===" << endl;
    for (const auto& row : arr) {
        for (int val : row) {
            cout << setw(4) << val;
        }
        cout << endl;
    }
    
    // Заполнение через fill
    arr[0].fill(999);
    cout << "\n=== После fill(999) первой строки ===" << endl;
    for (const auto& row : arr) {
        for (int val : row) {
            cout << setw(4) << val;
        }
        cout << endl;
    }
    
    // swap двух строк
    arr[0].swap(arr[4]);
    cout << "\n=== После swap строк 0 и 4 ===" << endl;
    for (const auto& row : arr) {
        for (int val : row) {
            cout << setw(4) << val;
        }
        cout << endl;
    }
    
    // Итераторы
    cout << "\nИтераторы (первая строка):" << endl;
    for (auto it = arr[0].begin(); it != arr[0].end(); ++it) {
        cout << *it << " ";
    }
    cout << endl;
    
    // Обратные итераторы
    cout << "Обратные итераторы (последняя строка):" << endl;
    for (auto it = arr[4].rbegin(); it != arr[4].rend(); ++it) {
        cout << *it << " ";
    }
    cout << endl;
    
    cout << "\nПРИМЕЧАНИЕ: std::array имеет ФИКСИРОВАННЫЙ размер!" << endl;
    cout << "Нельзя изменить 5x5 -> 6x6 или 4x4." << endl;
    
    return 0;
}
```

### 14. std::forward_list
```cpp
#include <iostream>
#include <forward_list>
#include <iomanip>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");
    
    // Создание односвязного списка (только вперёд!)
    forward_list<int> flist;
    
    cout << "=== std::forward_list (ОДНОСВЯЗНЫЙ СПИСОК) ===" << endl;
    
    // Добавление элементов в начало
    for (int i = 5; i >= 1; i--) {
        flist.push_front(i * 10);
    }
    
    cout << "После push_front (5 элементов):" << endl;
    for (int val : flist) {
        cout << setw(4) << val;
    }
    cout << endl;
    
    // Методы
    cout << "\nМетоды forward_list:" << endl;
    cout << "empty(): " << (flist.empty() ? "true" : "false") << endl;
    cout << "front(): " << flist.front() << endl;
    // max_size(), resize(), reverse(), sort(), merge(), unique(), remove(), remove_if()
    
    // Вставка после первого элемента
    auto it = flist.begin();
    flist.insert_after(it, 999);
    
    cout << "\nПосле insert_after(первого элемента, 999):" << endl;
    for (int val : flist) {
        cout << setw(4) << val;
    }
    cout << endl;
    
    // emplace_after
    it = flist.begin();
    flist.emplace_after(it, 777);
    
    cout << "\nПосле emplace_after(первого элемента, 777):" << endl;
    for (int val : flist) {
        cout << setw(4) << val;
    }
    cout << endl;
    
    // Удаление после первого элемента
    it = flist.begin();
    flist.erase_after(it);
    
    cout << "\nПосле erase_after(первого элемента):" << endl;
    for (int val : flist) {
        cout << setw(4) << val;
    }
    cout << endl;
    
    // Изменение значений
    for (int& val : flist) {
        val = val * 2;
    }
    
    cout << "\nПосле умножения всех элементов на 2:" << endl;
    for (int val : flist) {
        cout << setw(4) << val;
    }
    cout << endl;
    
    // sort
    flist.sort();
    cout << "\nПосле sort():" << endl;
    for (int val : flist) {
        cout << setw(4) << val;
    }
    cout << endl;
    
    // reverse
    flist.reverse();
    cout << "\nПосле reverse():" << endl;
    for (int val : flist) {
        cout << setw(4) << val;
    }
    cout << endl;
    
    // unique (удаляет дубликаты подряд)
    flist.push_front(20);
    flist.push_front(20);
    cout << "\nПосле добавления дубликатов 20,20 в начало:" << endl;
    for (int val : flist) {
        cout << setw(4) << val;
    }
    cout << endl;
    flist.unique();
    cout << "После unique():" << endl;
    for (int val : flist) {
        cout << setw(4) << val;
    }
    cout << endl;
    
    // remove
    flist.remove(40);
    cout << "\nПосле remove(40):" << endl;
    for (int val : flist) {
        cout << setw(4) << val;
    }
    cout << endl;
    
    // remove_if (удалить всё > 50)
    flist.remove_if([](int n) { return n > 50; });
    cout << "\nПосле remove_if(>50):" << endl;
    for (int val : flist) {
        cout << setw(4) << val;
    }
    cout << endl;
    
    // clear
    flist.clear();
    cout << "\nПосле clear(): empty=" << (flist.empty() ? "true" : "false") << endl;
    
    // resize
    flist.resize(5, 100);
    cout << "После resize(5, 100):" << endl;
    for (int val : flist) {
        cout << setw(4) << val;
    }
    cout << endl;
    
    // assign
    flist.assign({1, 2, 3, 4, 5});
    cout << "\nПосле assign({1,2,3,4,5}):" << endl;
    for (int val : flist) {
        cout << setw(4) << val;
    }
    cout << endl;
    
    cout << "\nПРИМЕЧАНИЕ: forward_list не имеет:" << endl;
    cout << "- push_back() / pop_back()" << endl;
    cout << "- size() (для эффективности)" << endl;
    cout << "- произвольного доступа по индексу" << endl;
    cout << "- двунаправленных итераторов" << endl;
    
    return 0;
}
```

### 15. std::set
```cpp
#include <iostream>
#include <set>
#include <iomanip>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");
    
    set<int> s;
    
    cout << "=== std::set (МНОЖЕСТВО - уникальные, отсортированные) ===" << endl;
    
    // Вставка элементов
    s.insert(50);
    s.insert(30);
    s.insert(70);
    s.insert(30);  // дубликат - не добавится!
    s.insert(10);
    s.insert(90);
    s.insert(50);  // ещё дубликат
    s.insert(40);
    
    cout << "После вставки {50,30,70,30,10,90,50,40}:" << endl;
    for (int val : s) {
        cout << setw(4) << val;
    }
    cout << endl;
    cout << "Размер: " << s.size() << " (дубликаты 30 и 50 не добавлены)" << endl;
    
    // Методы
    cout << "\nМетоды set:" << endl;
    cout << "size(): " << s.size() << endl;
    cout << "max_size(): " << s.max_size() << endl;
    cout << "empty(): " << (s.empty() ? "true" : "false") << endl;
    
    // find
    auto it = s.find(30);
    if (it != s.end()) {
        cout << "find(30): найден = " << *it << endl;
    }
    
    it = s.find(100);
    cout << "find(100): " << (it != s.end() ? "найден" : "не найден") << endl;
    
    // count (всегда 0 или 1)
    cout << "count(30): " << s.count(30) << endl;
    cout << "count(100): " << s.count(100) << endl;
    
    // lower_bound / upper_bound
    cout << "lower_bound(30): " << *s.lower_bound(30) << endl;
    cout << "upper_bound(30): " << *s.upper_bound(30) << endl;
    
    // equal_range
    auto range = s.equal_range(30);
    cout << "equal_range(30): " << *range.first << " - " << *range.second << endl;
    
    // emplace
    s.emplace(60);
    cout << "\nПосле emplace(60): ";
    for (int val : s) cout << val << " ";
    cout << endl;
    
    // emplace_hint
    s.emplace_hint(s.begin(), 20);
    cout << "После emplace_hint(20): ";
    for (int val : s) cout << val << " ";
    cout << endl;
    
    // Удаление
    s.erase(40);
    cout << "\nПосле erase(40): ";
    for (int val : s) cout << val << " ";
    cout << endl;
    
    // Удаление по итератору
    it = s.find(60);
    if (it != s.end()) s.erase(it);
    cout << "После erase(find(60)): ";
    for (int val : s) cout << val << " ";
    cout << endl;
    
    // Удаление диапазона
    auto start = s.find(30);
    auto end = s.find(70);
    s.erase(start, end);
    cout << "После erase(30, 70): ";
    for (int val : s) cout << val << " ";
    cout << endl;
    
    // clear
    s.clear();
    cout << "\nПосле clear(): size=" << s.size() << endl;
    
    // insert из initializer_list
    s.insert({5, 3, 1, 4, 2});
    cout << "После insert({5,3,1,4,2}): ";
    for (int val : s) cout << val << " ";
    cout << endl;
    
    // key_comp / value_comp
    auto comp = s.key_comp();
    cout << "\nКомпаратор: 1 < 5 = " << (comp(1, 5) ? "true" : "false") << endl;
    
    cout << "\nХАРАКТЕРИСТИКИ set:" << endl;
    cout << "- Хранит только уникальные элементы" << endl;
    cout << "- Автоматически сортирует (по умолчанию по возрастанию)" << endl;
    cout << "- Поиск, вставка, удаление: O(log n)" << endl;
    cout << "- Нельзя изменить элемент (только удалить и вставить новый)" << endl;
    
    return 0;
}
```

### 16. std::multiset
```cpp
#include <iostream>
#include <set>
#include <iomanip>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");
    
    multiset<int> ms;
    
    cout << "=== std::multiset (МУЛЬТИМНОЖЕСТВО - дубликаты разрешены) ===" << endl;
    
    // Вставка (дубликаты сохраняются!)
    ms.insert(30);
    ms.insert(10);
    ms.insert(50);
    ms.insert(30);  // дубликат СОХРАНЯЕТСЯ!
    ms.insert(30);  // ещё один
    ms.insert(20);
    ms.insert(50);  // дубликат
    
    cout << "После вставки {30,10,50,30,30,20,50}:" << endl;
    for (int val : ms) {
        cout << setw(4) << val;
    }
    cout << endl;
    cout << "Размер: " << ms.size() << endl;
    
    // count (может быть > 1)
    cout << "\ncount(30): " << ms.count(30) << " (три элемента)" << endl;
    cout << "count(10): " << ms.count(10) << " (один элемент)" << endl;
    cout << "count(100): " << ms.count(100) << " (нет элементов)" << endl;
    
    // find возвращает первый найденный
    auto it = ms.find(30);
    cout << "find(30): " << *it << endl;
    
    // equal_range
    auto range = ms.equal_range(30);
    cout << "\nequal_range(30):" << endl;
    for (auto it = range.first; it != range.second; ++it) {
        cout << *it << " ";
    }
    cout << endl;
    
    // lower_bound / upper_bound
    cout << "lower_bound(30): " << *ms.lower_bound(30) << endl;
    cout << "upper_bound(30): " << *ms.upper_bound(30) << endl;
    
    // Удаление по значению (удаляет ВСЕ вхождения!)
    ms.erase(30);
    cout << "\nПосле erase(30) - удаляет ВСЕ тройки:" << endl;
    for (int val : ms) {
        cout << setw(4) << val;
    }
    cout << endl;
    
    // Удаление одного элемента по итератору
    ms.insert(50);
    ms.insert(50);
    cout << "\nПосле добавления ещё двух 50:" << endl;
    for (int val : ms) cout << setw(4) << val;
    cout << endl;
    
    it = ms.find(50);
    if (it != ms.end()) ms.erase(it);  // удаляет только один!
    cout << "После erase(find(50)) - удаляет только ОДИН:" << endl;
    for (int val : ms) cout << setw(4) << val;
    cout << endl;
    
    // emplace
    ms.emplace(25);
    ms.emplace(25);
    cout << "\nПосле двух emplace(25):" << endl;
    for (int val : ms) cout << setw(4) << val;
    cout << endl;
    
    // Изменение всех элементов (только через удаление и вставку)
    cout << "\nИзменение: multiset не позволяет менять элементы на месте!" << endl;
    cout << "Нужно: стереть старый, вставить новый." << endl;
    
    // Пример: заменить все 50 на 55
    while (ms.find(50) != ms.end()) {
        ms.erase(ms.find(50));
        ms.insert(55);
    }
    cout << "После замены всех 50 на 55:" << endl;
    for (int val : ms) cout << setw(4) << val;
    cout << endl;
    
    cout << "\nХАРАКТЕРИСТИКИ multiset:" << endl;
    cout << "- Допускает дубликаты" << endl;
    cout << "- Автоматически сортирует" << endl;
    cout << "- erase(значение) удаляет ВСЕ вхождения" << endl;
    cout << "- erase(итератор) удаляет только ОДИН элемент" << endl;
    
    return 0;
}
```

### 17. std::map
```cpp
#include <iostream>
#include <map>
#include <iomanip>
#include <string>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");
    
    map<string, int> m;
    
    cout << "=== std::map (СЛОВАРЬ - ключ:значение, отсортирован) ===" << endl;
    
    // Вставка разными способами
    m["Иванов"] = 85;
    m["Петров"] = 92;
    m.insert({"Сидоров", 78});
    m.insert(pair<string, int>("Козлов", 95));
    m.emplace("Фёдоров", 88);
    
    // Попытка дубликата ключа
    m["Иванов"] = 90;  // перезапишет значение!
    
    cout << "Содержимое словаря:" << endl;
    cout << setw(15) << "Фамилия" << " | " << "Балл" << endl;
    cout << string(25, '-') << endl;
    for (const auto& [key, value] : m) {
        cout << setw(15) << key << " | " << value << endl;
    }
    
    // Методы
    cout << "\nМетоды map:" << endl;
    cout << "size(): " << m.size() << endl;
    cout << "max_size(): " << m.max_size() << endl;
    cout << "empty(): " << (m.empty() ? "true" : "false") << endl;
    
    // Доступ по ключу
    cout << "m[\"Иванов\"]: " << m["Иванов"] << endl;
    cout << "m.at(\"Петров\"): " << m.at("Петров") << endl;
    
    // Проверка существования ключа
    cout << "count(\"Сидоров\"): " << m.count("Сидоров") << endl;
    cout << "count(\"Неизвестный\"): " << m.count("Неизвестный") << endl;
    
    // find
    auto it = m.find("Козлов");
    if (it != m.end()) {
        cout << "find(\"Козлов\"): " << it->first << " = " << it->second << endl;
    }
    
    // contains (C++20)
    // cout << "contains(\"Фёдоров\"): " << m.contains("Фёдоров") << endl;
    
    // lower_bound / upper_bound
    it = m.lower_bound("К");
    cout << "lower_bound(\"К\"): " << it->first << " = " << it->second << endl;
    it = m.upper_bound("К");
    cout << "upper_bound(\"К\"): " << it->first << " = " << it->second << endl;
    
    // insert_or_assign (C++17)
    m.insert_or_assign("Иванов", 100);
    cout << "\nПосле insert_or_assign(\"Иванов\", 100):" << endl;
    for (const auto& [key, value] : m) {
        cout << setw(15) << key << " | " << value << endl;
    }
    
    // try_emplace (не перезаписывает существующий)
    auto [iter, inserted] = m.try_emplace("Петров", 50);
    cout << "\ntry_emplace(\"Петров\", 50): вставлен=" << (inserted ? "да" : "нет") << endl;
    cout << "Значение осталось: " << iter->second << endl;
    
    // Удаление
    m.erase("Сидоров");
    cout << "\nПосле erase(\"Сидоров\"):" << endl;
    for (const auto& [key, value] : m) {
        cout << setw(15) << key << " | " << value << endl;
    }
    
    // Изменение значений циклом
    cout << "\nУвеличение всех баллов на 5:" << endl;
    for (auto& [key, value] : m) {
        value += 5;
    }
    for (const auto& [key, value] : m) {
        cout << setw(15) << key << " | " << value << endl;
    }
    
    // extract (C++17) - извлечение узла
    auto node = m.extract("Козлов");
    if (!node.empty()) {
        node.key() = "Козловский";  // меняем ключ
        m.insert(move(node));
    }
    cout << "\nПосле extract и смены ключа Козлов->Козловский:" << endl;
    for (const auto& [key, value] : m) {
        cout << setw(15) << key << " | " << value << endl;
    }
    
    // clear
    m.clear();
    cout << "\nПосле clear(): size=" << m.size() << endl;
    
    cout << "\nХАРАКТЕРИСТИКИ map:" << endl;
    cout << "- Хранит пары ключ:значение" << endl;
    cout << "- Ключи уникальны и отсортированы" << endl;
    cout << "- Доступ по ключу: O(log n)" << endl;
    cout << "- operator[] создаёт элемент если ключа нет" << endl;
    
    return 0;
}
```

### 18. std::multimap
```cpp
#include <iostream>
#include <map>
#include <string>
#include <iomanip>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");
    
    multimap<string, int> mm;
    
    cout << "=== std::multimap (МУЛЬТИСЛОВАРЬ - дубликаты ключей разрешены) ===" << endl;
    
    // Вставка (дубликаты ключей разрешены!)
    mm.insert({"Иванов", 85});
    mm.insert({"Петров", 92});
    mm.insert({"Иванов", 78});  // дубликат ключа!
    mm.insert({"Иванов", 95});  // ещё один
    mm.emplace("Сидоров", 88);
    mm.insert({"Петров", 73});
    
    cout << "Содержимое (ключи могут повторяться):" << endl;
    cout << setw(15) << "Фамилия" << " | " << "Балл" << endl;
    cout << string(25, '-') << endl;
    for (const auto& [key, value] : mm) {
        cout << setw(15) << key << " | " << value << endl;
    }
    cout << "Размер: " << mm.size() << endl;
    
    // count (может быть > 1)
    cout << "\ncount(\"Иванов\"): " << mm.count("Иванов") << endl;
    cout << "count(\"Петров\"): " << mm.count("Петров") << endl;
    cout << "count(\"Неизвестный\"): " << mm.count("Неизвестный") << endl;
    
    // find возвращает первый найденный
    auto it = mm.find("Иванов");
    cout << "find(\"Иванов\"): " << it->first << " = " << it->second << endl;
    
    // equal_range
    auto range = mm.equal_range("Иванов");
    cout << "\nequal_range(\"Иванов\"):" << endl;
    for (auto it = range.first; it != range.second; ++it) {
        cout << "  " << it->first << " = " << it->second << endl;
    }
    
    // lower_bound / upper_bound
    cout << "\nlower_bound(\"Иванов\"): " << mm.lower_bound("Иванов")->second << endl;
    auto ub = mm.upper_bound("Иванов");
    if (ub != mm.end()) {
        cout << "upper_bound(\"Иванов\"): " << ub->first << " = " << ub->second << endl;
    }
    
    // Удаление по ключу (удаляет ВСЕ вхождения!)
    mm.erase("Иванов");
    cout << "\nПосле erase(\"Иванов\") - удаляет ВСЕ:" << endl;
    for (const auto& [key, value] : mm) {
        cout << setw(15) << key << " | " << value << endl;
    }
    
    // Удаление одного элемента по итератору
    mm.insert({"Петров", 100});
    mm.insert({"Петров", 100});
    cout << "\nПосле добавления ещё двух Петров:" << endl;
    for (const auto& [key, value] : mm) {
        cout << setw(15) << key << " | " << value << endl;
    }
    
    it = mm.find("Петров");
    if (it != mm.end()) mm.erase(it);  // удаляет только один
    cout << "\nПосле erase(find(\"Петров\")) - удалён только ОДИН:" << endl;
    for (const auto& [key, value] : mm) {
        cout << setw(15) << key << " | " << value << endl;
    }
    
    // Изменение значений
    cout << "\nУвеличение всех баллов на 5:" << endl;
    for (auto& [key, value] : mm) {
        value += 5;
    }
    for (const auto& [key, value] : mm) {
        cout << setw(15) << key << " | " << value << endl;
    }
    
    // extract (C++17)
    cout << "\nextract и изменение ключа:" << endl;
    auto node = mm.extract("Сидоров");
    if (!node.empty()) {
        node.key() = "Сидоренко";
        mm.insert(move(node));
    }
    for (const auto& [key, value] : mm) {
        cout << setw(15) << key << " | " << value << endl;
    }
    
    cout << "\nХАРАКТЕРИСТИКИ multimap:" << endl;
    cout << "- Допускает дубликаты ключей" << endl;
    cout << "- Нет operator[] (какой из дубликатов вернуть?)" << endl;
    cout << "- Нет at()" << endl;
    cout << "- erase(ключ) удаляет ВСЕ вхождения" << endl;
    cout << "- erase(итератор) удаляет только ОДИН элемент" << endl;
    
    return 0;
}
```

### 19. std::unordered_set
```cpp
#include <iostream>
#include <unordered_set>
#include <iomanip>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");
    
    unordered_set<int> us;
    
    cout << "=== std::unordered_set (ХЕШ-МНОЖЕСТВО - уникальные, не отсортированы) ===" << endl;
    
    // Вставка
    us.insert(50);
    us.insert(30);
    us.insert(70);
    us.insert(30);  // дубликат - не добавится
    us.insert(10);
    us.insert(90);
    us.emplace(40);
    
    cout << "После вставки {50,30,70,30,10,90,40}:" << endl;
    for (int val : us) {
        cout << setw(4) << val;
    }
    cout << endl;
    cout << "Порядок НЕ отсортирован (зависит от хеша)!" << endl;
    
    // Методы
    cout << "\nМетоды unordered_set:" << endl;
    cout << "size(): " << us.size() << endl;
    cout << "max_size(): " << us.max_size() << endl;
    cout << "empty(): " << (us.empty() ? "true" : "false") << endl;
    
    // bucket_count, bucket_size, bucket
    cout << "bucket_count(): " << us.bucket_count() << endl;
    for (size_t i = 0; i < us.bucket_count(); i++) {
        if (us.bucket_size(i) > 0) {
            cout << "  bucket[" << i << "] size = " << us.bucket_size(i) << ": ";
            for (auto it = us.begin(i); it != us.end(i); ++it) {
                cout << *it << " ";
            }
            cout << endl;
        }
    }
    
    // load_factor
    cout << "load_factor(): " << us.load_factor() << endl;
    cout << "max_load_factor(): " << us.max_load_factor() << endl;
    
    // rehash и reserve
    us.rehash(20);
    cout << "\nПосле rehash(20): bucket_count=" << us.bucket_count() << endl;
    us.reserve(50);
    cout << "После reserve(50): bucket_count=" << us.bucket_count() << endl;
    
    // find
    auto it = us.find(30);
    if (it != us.end()) cout << "find(30): найден = " << *it << endl;
    
    // count
    cout << "count(30): " << us.count(30) << endl;
    cout << "count(100): " << us.count(100) << endl;
    
    // equal_range
    auto range = us.equal_range(30);
    cout << "equal_range(30): ";
    for (auto it = range.first; it != range.second; ++it) {
        cout << *it << " ";
    }
    cout << endl;
    
    // Удаление
    us.erase(40);
    cout << "\nПосле erase(40): ";
    for (int val : us) cout << val << " ";
    cout << endl;
    
    // Изменение НЕВОЗМОЖНО (только удалить и вставить)
    cout << "\nИзменение: нельзя модифицировать элементы!" << endl;
    cout << "Нужно стереть и вставить новый." << endl;
    
    // clear
    us.clear();
    cout << "После clear(): size=" << us.size() << endl;
    
    cout << "\nХАРАКТЕРИСТИКИ unordered_set:" << endl;
    cout << "- Уникальные элементы" << endl;
    cout << "- Порядок не определён (зависит от хеша)" << endl;
    cout << "- В среднем O(1) для вставки/поиска/удаления" << endl;
    cout << "- В худшем случае O(n)" << endl;
    
    // Сравнение с set
    cout << "\nСРАВНЕНИЕ set vs unordered_set:" << endl;
    cout << "set:       отсортирован, O(log n), больше памяти на указатели дерева" << endl;
    cout << "unordered: не отсортирован, O(1) в среднем, больше памяти на хеш-таблицу" << endl;
    
    return 0;
}
```

### 20. std::unordered_multiset
```cpp
#include <iostream>
#include <unordered_set>
#include <iomanip>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");
    
    unordered_multiset<int> ums;
    
    cout << "=== std::unordered_multiset (ХЕШ-МУЛЬТИМНОЖЕСТВО) ===" << endl;
    
    // Вставка (дубликаты разрешены)
    ums.insert(30);
    ums.insert(10);
    ums.insert(50);
    ums.insert(30);  // дубликат СОХРАНЯЕТСЯ
    ums.insert(30);  // ещё
    ums.insert(20);
    ums.emplace(50);
    
    cout << "После вставки {30,10,50,30,30,20,50}:" << endl;
    for (int val : ums) {
        cout << setw(4) << val;
    }
    cout << endl;
    cout << "Размер: " << ums.size() << endl;
    
    // count
    cout << "\ncount(30): " << ums.count(30) << " (три штуки)" << endl;
    cout << "count(10): " << ums.count(10) << endl;
    
    // equal_range
    auto range = ums.equal_range(30);
    cout << "equal_range(30): ";
    for (auto it = range.first; it != range.second; ++it) {
        cout << *it << " ";
    }
    cout << endl;
    
    // Удаление по значению (удаляет ВСЕ!)
    ums.erase(30);
    cout << "\nПосле erase(30) - удаляет ВСЕ 30:" << endl;
    for (int val : ums) cout << setw(4) << val;
    cout << endl;
    
    // Удаление одного по итератору
    auto it = ums.find(50);
    if (it != ums.end()) ums.erase(it);
    cout << "После erase(find(50)) - удалён только ОДИН 50:" << endl;
    for (int val : ums) cout << setw(4) << val;
    cout << endl;
    
    // bucket информация
    cout << "\nbucket_count: " << ums.bucket_count() << endl;
    cout << "load_factor: " << ums.load_factor() << endl;
    
    // rehash
    ums.rehash(30);
    cout << "После rehash(30): bucket_count=" << ums.bucket_count() << endl;
    
    // clear
    ums.clear();
    cout << "\nПосле clear(): size=" << ums.size() << endl;
    
    cout << "\nХАРАКТЕРИСТИКИ unordered_multiset:" << endl;
    cout << "- Допускает дубликаты" << endl;
    cout << "- Порядок не определён" << endl;
    cout << "- O(1) в среднем для операций" << endl;
    
    return 0;
}
```

### 21. std::unordered_map
```cpp
#include <iostream>
#include <unordered_map>
#include <string>
#include <iomanip>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");
    
    unordered_map<string, int> um;
    
    cout << "=== std::unordered_map (ХЕШ-СЛОВАРЬ) ===" << endl;
    
    // Вставка
    um["Иванов"] = 85;
    um["Петров"] = 92;
    um.insert({"Сидоров", 78});
    um.emplace("Козлов", 95);
    
    // Дубликат перезаписывает
    um["Иванов"] = 90;
    
    cout << "Содержимое (порядок не определён):" << endl;
    cout << setw(15) << "Фамилия" << " | " << "Балл" << endl;
    cout << string(25, '-') << endl;
    for (const auto& [key, value] : um) {
        cout << setw(15) << key << " | " << value << endl;
    }
    
    // Методы
    cout << "\nМетоды unordered_map:" << endl;
    cout << "size(): " << um.size() << endl;
    cout << "bucket_count(): " << um.bucket_count() << endl;
    cout << "load_factor(): " << um.load_factor() << endl;
    
    // Доступ
    cout << "um[\"Иванов\"]: " << um["Иванов"] << endl;
    cout << "um.at(\"Петров\"): " << um.at("Петров") << endl;
    
    // count / find / contains
    cout << "count(\"Козлов\"): " << um.count("Козлов") << endl;
    auto it = um.find("Сидоров");
    if (it != um.end()) {
        cout << "find(\"Сидоров\"): " << it->second << endl;
    }
    
    // bucket
    cout << "\nРаспределение по bucket:" << endl;
    for (size_t i = 0; i < um.bucket_count(); i++) {
        if (um.bucket_size(i) > 0) {
            cout << "  bucket[" << i << "]: ";
            for (auto it = um.begin(i); it != um.end(i); ++it) {
                cout << it->first << "=" << it->second << " ";
            }
            cout << endl;
        }
    }
    
    // rehash / reserve
    um.rehash(20);
    cout << "\nПосле rehash(20): bucket_count=" << um.bucket_count() << endl;
    um.reserve(50);
    cout << "После reserve(50): bucket_count=" << um.bucket_count() << endl;
    
    // insert_or_assign
    um.insert_or_assign("Иванов", 100);
    cout << "\nПосле insert_or_assign(\"Иванов\", 100):" << endl;
    for (const auto& [key, value] : um) {
        cout << setw(15) << key << " | " << value << endl;
    }
    
    // try_emplace
    auto [iter, inserted] = um.try_emplace("Петров", 50);
    cout << "\ntry_emplace(\"Петров\", 50): вставлен=" << (inserted ? "да" : "нет") << endl;
    
    // Удаление
    um.erase("Сидоров");
    cout << "\nПосле erase(\"Сидоров\"):" << endl;
    for (const auto& [key, value] : um) {
        cout << setw(15) << key << " | " << value << endl;
    }
    
    // Изменение всех значений
    cout << "\nУвеличение всех баллов на 5:" << endl;
    for (auto& [key, value] : um) {
        value += 5;
    }
    for (const auto& [key, value] : um) {
        cout << setw(15) << key << " | " << value << endl;
    }
    
    // extract
    auto node = um.extract("Козлов");
    if (!node.empty()) {
        node.key() = "Козловский";
        um.insert(move(node));
    }
    cout << "\nПосле extract и смены ключа:" << endl;
    for (const auto& [key, value] : um) {
        cout << setw(15) << key << " | " << value << endl;
    }
    
    cout << "\nХАРАКТЕРИСТИКИ unordered_map:" << endl;
    cout << "- Ключи уникальны, порядок не определён" << endl;
    cout << "- O(1) в среднем для доступа/вставки/удаления" << endl;
    cout << "- operator[] создаёт элемент если ключа нет" << endl;
    
    return 0;
}
```

### 22. std::unordered_multimap
```cpp
#include <iostream>
#include <unordered_map>
#include <string>
#include <iomanip>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");
    
    unordered_multimap<string, int> umm;
    
    cout << "=== std::unordered_multimap (ХЕШ-МУЛЬТИСЛОВАРЬ) ===" << endl;
    
    // Вставка (дубликаты ключей разрешены)
    umm.insert({"Иванов", 85});
    umm.insert({"Петров", 92});
    umm.insert({"Иванов", 78});
    umm.insert({"Иванов", 95});
    umm.emplace("Сидоров", 88);
    umm.insert({"Петров", 73});
    
    cout << "Содержимое (ключи могут повторяться):" << endl;
    cout << setw(15) << "Фамилия" << " | " << "Балл" << endl;
    cout << string(25, '-') << endl;
    for (const auto& [key, value] : umm) {
        cout << setw(15) << key << " | " << value << endl;
    }
    cout << "Размер: " << umm.size() << endl;
    
    // count
    cout << "\ncount(\"Иванов\"): " << umm.count("Иванов") << endl;
    
    // equal_range
    auto range = umm.equal_range("Иванов");
    cout << "equal_range(\"Иванов\"):" << endl;
    for (auto it = range.first; it != range.second; ++it) {
        cout << "  " << it->first << " = " << it->second << endl;
    }
    
    // find
    auto it = umm.find("Петров");
    cout << "find(\"Петров\"): " << it->second << endl;
    
    // bucket
    cout << "\nbucket_count: " << umm.bucket_count() << endl;
    cout << "load_factor: " << umm.load_factor() << endl;
    
    // Удаление по ключу (ВСЕ!)
    umm.erase("Иванов");
    cout << "\nПосле erase(\"Иванов\") - удаляет ВСЕ:" << endl;
    for (const auto& [key, value] : umm) {
        cout << setw(15) << key << " | " << value << endl;
    }
    
    // Изменение значений
    cout << "\nУвеличение всех баллов на 5:" << endl;
    for (auto& [key, value] : umm) {
        value += 5;
    }
    for (const auto& [key, value] : umm) {
        cout << setw(15) << key << " | " << value << endl;
    }
    
    cout << "\nХАРАКТЕРИСТИКИ unordered_multimap:" << endl;
    cout << "- Допускает дубликаты ключей" << endl;
    cout << "- Нет operator[] и at()" << endl;
    cout << "- O(1) в среднем для операций" << endl;
    cout << "- Порядок не определён" << endl;
    
    return 0;
}
```

### 23. std::stack
```cpp
#include <iostream>
#include <stack>
#include <vector>
#include <list>
#include <deque>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");
    
    cout << "=== std::stack (СТЕК - LIFO - Last In, First Out) ===" << endl;
    
    // По умолчанию stack использует deque
    stack<int> s;
    
    // push
    cout << "push: 10, 20, 30, 40, 50" << endl;
    s.push(10);
    s.push(20);
    s.push(30);
    s.push(40);
    s.push(50);
    
    // Методы
    cout << "\nМетоды stack:" << endl;
    cout << "size(): " << s.size() << endl;
    cout << "empty(): " << (s.empty() ? "true" : "false") << endl;
    cout << "top(): " << s.top() << " (последний добавленный)" << endl;
    
    // pop
    cout << "\npop (удаление с вершины):" << endl;
    while (!s.empty()) {
        cout << "  top = " << s.top() << ", pop!" << endl;
        s.pop();
    }
    cout << "После всех pop: empty=" << (s.empty() ? "true" : "false") << endl;
    
    // emplace
    s.emplace(100);
    cout << "\nПосле emplace(100): top=" << s.top() << endl;
    
    // swap
    stack<int> s2;
    s2.push(999);
    s.swap(s2);
    cout << "После swap: s.top()=" << s.top() << ", s2.top()=" << s2.top() << endl;
    
    // Стек на основе вектора
    cout << "\n--- Стек на основе vector ---" << endl;
    stack<int, vector<int>> sVec;
    sVec.push(1);
    sVec.push(2);
    sVec.push(3);
    cout << "sVec.size()=" << sVec.size() << ", top=" << sVec.top() << endl;
    
    // Стек на основе list
    cout << "\n--- Стек на основе list ---" << endl;
    stack<int, list<int>> sList;
    sList.push(100);
    sList.push(200);
    cout << "sList.size()=" << sList.size() << ", top=" << sList.top() << endl;
    
    cout << "\nХАРАКТЕРИСТИКИ stack:" << endl;
    cout << "- LIFO: последний вошёл - первый вышел" << endl;
    cout << "- Доступ только к верхнему элементу (top)" << endl;
    cout << "- Нет итераторов" << endl;
    cout << "- По умолчанию основан на deque" << endl;
    cout << "- Можно указать vector или list как базовый контейнер" << endl;
    cout << "- Операции: push, pop, top, emplace, size, empty, swap" << endl;
    
    return 0;
}
```

### 24. std::queue
```cpp
#include <iostream>
#include <queue>
#include <list>
#include <deque>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");
    
    cout << "=== std::queue (ОЧЕРЕДЬ - FIFO - First In, First Out) ===" << endl;
    
    // По умолчанию queue использует deque
    queue<int> q;
    
    // push
    cout << "push: 10, 20, 30, 40, 50" << endl;
    q.push(10);
    q.push(20);
    q.push(30);
    q.push(40);
    q.push(50);
    
    // Методы
    cout << "\nМетоды queue:" << endl;
    cout << "size(): " << q.size() << endl;
    cout << "empty(): " << (q.empty() ? "true" : "false") << endl;
    cout << "front(): " << q.front() << " (первый добавленный)" << endl;
    cout << "back(): " << q.back() << " (последний добавленный)" << endl;
    
    // pop
    cout << "\npop (удаление из начала):" << endl;
    while (!q.empty()) {
        cout << "  front = " << q.front() << ", back = " << q.back() << ", pop!" << endl;
        q.pop();
    }
    cout << "После всех pop: empty=" << (q.empty() ? "true" : "false") << endl;
    
    // emplace
    q.emplace(100);
    q.emplace(200);
    cout << "\nПосле emplace(100,200): front=" << q.front() << ", back=" << q.back() << endl;
    
    // swap
    queue<int> q2;
    q2.push(999);
    q.swap(q2);
    cout << "После swap: q.front()=" << q.front() << ", q2.front()=" << q2.front() << endl;
    
    // Очередь на основе list
    cout << "\n--- Очередь на основе list ---" << endl;
    queue<int, list<int>> qList;
    qList.push(1);
    qList.push(2);
    qList.push(3);
    cout << "qList: front=" << qList.front() << ", back=" << qList.back() << ", size=" << qList.size() << endl;
    
    cout << "\nХАРАКТЕРИСТИКИ queue:" << endl;
    cout << "- FIFO: первый вошёл - первый вышел" << endl;
    cout << "- Доступ к front (начало) и back (конец)" << endl;
    cout << "- Нет итераторов" << endl;
    cout << "- По умолчанию основана на deque" << endl;
    cout << "- Можно указать list как базовый контейнер (vector нельзя - нет pop_front)" << endl;
    cout << "- Операции: push, pop, front, back, emplace, size, empty, swap" << endl;
    
    return 0;
}
```

### 25. std::priority_queue
```cpp
#include <iostream>
#include <queue>
#include <vector>
#include <functional>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");
    
    cout << "=== std::priority_queue (ОЧЕРЕДЬ С ПРИОРИТЕТОМ) ===" << endl;
    
    // По умолчанию: максимальный элемент имеет высший приоритет (max-heap)
    priority_queue<int> pq;
    
    // push
    cout << "push: 30, 10, 50, 20, 40" << endl;
    pq.push(30);
    pq.push(10);
    pq.push(50);
    pq.push(20);
    pq.push(40);
    
    // Методы
    cout << "\nМетоды priority_queue:" << endl;
    cout << "size(): " << pq.size() << endl;
    cout << "empty(): " << (pq.empty() ? "true" : "false") << endl;
    cout << "top(): " << pq.top() << " (максимальный элемент)" << endl;
    
    // pop (удаляет максимальный)
    cout << "\npop (удаление максимального):" << endl;
    while (!pq.empty()) {
        cout << "  top = " << pq.top() << ", pop!" << endl;
        pq.pop();
    }
    
    // Минимальный элемент имеет приоритет (min-heap)
    cout << "\n--- priority_queue с greater (min-heap) ---" << endl;
    priority_queue<int, vector<int>, greater<int>> pqMin;
    pqMin.push(30);
    pqMin.push(10);
    pqMin.push(50);
    pqMin.push(20);
    pqMin.push(40);
    
    cout << "Извлечение (минимальные первыми):" << endl;
    while (!pqMin.empty()) {
        cout << "  " << pqMin.top();
        pqMin.pop();
    }
    cout << endl;
    
    // С пользовательским компаратором
    cout << "\n--- Пользовательский компаратор (чётные приоритетнее) ---" << endl;
    auto comp = [](int a, int b) {
        // Чётные числа имеют больший приоритет
        bool aEven = (a % 2 == 0);
        bool bEven = (b % 2 == 0);
        if (aEven && !bEven) return false;  // a приоритетнее
        if (!aEven && bEven) return true;   // b приоритетнее
        return a < b;  // среди одинаковой чётности - большее приоритетнее
    };
    
    priority_queue<int, vector<int>, decltype(comp)> pqCustom(comp);
    pqCustom.push(1);
    pqCustom.push(2);
    pqCustom.push(3);
    pqCustom.push(4);
    pqCustom.push(5);
    pqCustom.push(6);
    
    cout << "Извлечение (чётные первыми, затем большие):" << endl;
    while (!pqCustom.empty()) {
        cout << "  " << pqCustom.top();
        pqCustom.pop();
    }
    cout << endl;
    
    // emplace
    cout << "\nemplace:" << endl;
    priority_queue<int> pq3;
    pq3.emplace(100);
    pq3.emplace(50);
    cout << "После emplace(100,50): top=" << pq3.top() << endl;
    
    // swap
    priority_queue<int> pq4;
    pq4.push(999);
    pq3.swap(pq4);
    cout << "После swap: pq3.top()=" << pq3.top() << ", pq4.top()=" << pq4.top() << endl;
    
    // priority_queue для пар (сортировка по первому элементу)
    cout << "\n--- priority_queue с парами ---" << endl;
    priority_queue<pair<int, string>> pqPairs;
    pqPairs.push({3, "третий"});
    pqPairs.push({1, "первый"});
    pqPairs.push({2, "второй"});
    
    cout << "Извлечение пар (по убыванию первого элемента):" << endl;
    while (!pqPairs.empty()) {
        cout << "  {" << pqPairs.top().first << ", " << pqPairs.top().second << "}" << endl;
        pqPairs.pop();
    }
    
    cout << "\nХАРАКТЕРИСТИКИ priority_queue:" << endl;
    cout << "- Элементы извлекаются по приоритету" << endl;
    cout << "- По умолчанию: максимальный элемент первым (max-heap)" << endl;
    cout << "- Можно задать компаратор для изменения приоритета" << endl;
    cout << "- Нет итераторов" << endl;
    cout << "- Доступ только к top()" << endl;
    cout << "- Операции: push, pop, top, emplace, size, empty, swap" << endl;
    
    return 0;
}
```

### 26. std::span (C++20)
```cpp
#include <iostream>
#include <span>
#include <vector>
#include <array>
#include <iomanip>
using namespace std;

int main() {
    setlocale(LC_ALL, "Russian");
    
    cout << "=== std::span (C++20 - ПРЕДСТАВЛЕНИЕ НЕПРЕРЫВНОЙ ПАМЯТИ) ===" << endl;
    
    // Создание span из массива
    int arr[] = {10, 20, 30, 40, 50};
    span<int> sp1(arr);
    
    cout << "span из массива arr[5]:" << endl;
    cout << "size(): " << sp1.size() << endl;
    cout << "size_bytes(): " << sp1.size_bytes() << endl;
    cout << "empty(): " << (sp1.empty() ? "true" : "false") << endl;
    
    cout << "Элементы: ";
    for (int val : sp1) {
        cout << val << " ";
    }
    cout << endl;
    
    // Доступ
    cout << "sp1[2]: " << sp1[2] << endl;
    cout << "sp1.front(): " << sp1.front() << endl;
    cout << "sp1.back(): " << sp1.back() << endl;
    cout << "sp1.data(): " << sp1.data() << endl;
    
    // Изменение через span (меняет оригинал!)
    cout << "\nИзменение через span (sp1[0] = 999):" << endl;
    sp1[0] = 999;
    cout << "arr[0] теперь = " << arr[0] << " (оригинал изменился!)" << endl;
    
    // Подпредставление (subspan)
    auto sp2 = sp1.subspan(1, 3);  // с индекса 1, 3 элемента
    cout << "\nsubspan(1, 3): ";
    for (int val : sp2) {
        cout << val << " ";
    }
    cout << endl;
    
    // first / last
    auto spFirst = sp1.first(2);
    cout << "first(2): ";
    for (int val : spFirst) cout << val << " ";
    cout << endl;
    
    auto spLast = sp1.last(2);
    cout << "last(2): ";
    for (int val : spLast) cout << val << " ";
    cout << endl;
    
    // span из вектора
    cout << "\n--- span из вектора ---" << endl;
    vector<int> vec = {1, 2, 3, 4, 5, 6, 7, 8};
    span<int> spVec(vec);
    cout << "span из vector (размер " << spVec.size() << "): ";
    for (int val : spVec) cout << val << " ";
    cout << endl;
    
    // span из array
    cout << "\n--- span из array ---" << endl;
    array<int, 4> arr2 = {100, 200, 300, 400};
    span<int> spArr(arr2);
    cout << "span из array: ";
    for (int val : spArr) cout << val << " ";
    cout << endl;
    
    // Динамический extent
    cout << "\n--- Динамический span ---" << endl;
    int* dynArr = new int[6]{1, 2, 3, 4, 5, 6};
    span<int> spDyn(dynArr, 6);
    cout << "Динамический span (размер " << spDyn.size() << "): ";
    for (int val : spDyn) cout << val << " ";
    cout << endl;
    delete[] dynArr;
    
    // Статический extent
    cout << "\n--- Статический span<5> ---" << endl;
    int arr3[] = {11, 22, 33, 44, 55};
    span<int, 5> spStatic(arr3);
    cout << "Статический span: ";
    for (int val : spStatic) cout << val << " ";
    cout << endl;
    
    // Константный span
    cout << "\n--- Константный span ---" << endl;
    const int constArr[] = {10, 20, 30};
    span<const int> spConst(constArr);
    cout << "span<const int>: ";
    for (int val : spConst) cout << val << " ";
    cout << endl;
    // spConst[0] = 999;  // ОШИБКА КОМПИЛЯЦИИ!
    
    // Изменение значений циклом for
    cout << "\nИзменение через span циклом for:" << endl;
    for (int& val : sp1) {
        val *= 10;
    }
    cout << "После sp1 *= 10: ";
    for (int val : sp1) cout << val << " ";
    cout << endl;
    cout << "Оригинальный массив arr: ";
    for (int val : arr) cout << val << " ";
    cout << endl;
    
    cout << "\nХАРАКТЕРИСТИКИ span:" << endl;
    cout << "- Не владеет данными (лёгкое представление)" << endl;
    cout << "- Может ссылаться на массив, vector, array, C-массив" << endl;
    cout << "- Требует C++20" << endl;
    cout << "- Безопасная альтернатива указателю + размер" << endl;
    cout << "- Может быть динамического или статического размера" << endl;
    cout << "- Изменения через span меняют оригинальные данные" << endl;
    
    return 0;
}
```

## СВОДНАЯ ТАБЛИЦА ВСЕХ РАССМОТРЕННЫХ КОНТЕЙНЕРОВ
| № | Контейнер | Заголовок | Уникальность | Сортировка | Доступ | Вставка/удаление | Память |
|---|---|---|---|---|---|---|---|
| 1 | vector | `<vector>` | Нет | Нет | O(1) | O(n) в середине, O(1) в конце | Непрерывная |
| 2 | deque | `<deque>` | Нет | Нет | O(1) | O(n) в середине, O(1) в начале/конце | Блочная |
| 3 | list | `<list>` | Нет | Нет | O(n) | O(1) везде | Узлы |
| 4 | Статический массив | — | Нет | Нет | O(1) | Нельзя | Непрерывная |
| 5 | Динамический массив | — | Нет | Нет | O(1) | O(n) (копирование) | Непрерывная |
| 6 | array | `<array>` | Нет | Нет | O(1) | Нельзя | Непрерывная |
| 7 | forward_list | `<forward_list>` | Нет | Нет | O(n) | O(1) после итератора | Узлы |
| 8 | set | `<set>` | Да | Да | O(log n) | O(log n) | Дерево |
| 9 | multiset | `<set>` | Нет | Да | O(log n) | O(log n) | Дерево |
| 10 | map | `<map>` | Ключи | Ключи | O(log n) | O(log n) | Дерево |
| 11 | multimap | `<map>` | Нет | Ключи | O(log n) | O(log n) | Дерево |
| 12 | unordered_set | `<unordered_set>` | Да | Нет | O(1) ср. | O(1) ср. | Хеш-таблица |
| 13 | unordered_multiset | `<unordered_set>` | Нет | Нет | O(1) ср. | O(1) ср. | Хеш-таблица |
| 14 | unordered_map | `<unordered_map>` | Ключи | Нет | O(1) ср. | O(1) ср. | Хеш-таблица |
| 15 | unordered_multimap | `<unordered_map>` | Нет | Нет | O(1) ср. | O(1) ср. | Хеш-таблица |
| 16 | stack | `<stack>` | — | — | top | push/pop (LIFO) | Адаптер |
| 17 | queue | `<queue>` | — | — | front/back | push/pop (FIFO) | Адаптер |
| 18 | priority_queue | `<queue>` | — | Приоритет | top | push/pop (max/min) | Адаптер |
| 19 | span (C++20) | `<span>` | — | — | O(1) | Не владеет | Представление |
