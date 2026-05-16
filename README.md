# Справочник по C++

<table>
  <tr>
    <td align="center" width="50%"><b>📁 Работа с файлами (Вы здесь)</b></td>
    <td align="center" width="50%"><a href="./Conteiner_readme.md"><b>📦 Работа с контейнерами</b></a></td>
  </tr>
</table>

# 30 мини-примеров работы с файлами на C++ с комментариями на русском:

## ЗАПИСЬ В ФАЙЛ
### 1. Простая запись в текстовый файл

```cpp
#include <fstream>
int main() {
    std::ofstream f("test.txt");
    f << "Привет, мир!";
    f.close();
}
```

### 2. Запись с проверкой открытия

```cpp
#include <fstream>
#include <iostream>
int main() {
    std::ofstream f("data.txt");
    if (f.is_open()) {
        f << 42 << " " << 3.14;
        f.close();
    } else std::cout << "Ошибка!";
}
```

### 3. Дозапись в конец файла (append)

```cpp
#include <fstream>
int main() {
    std::ofstream f("log.txt", std::ios::app);
    f << "Новая строка\n";
    f.close();
}
```

### 4. Запись массива чисел

```cpp
#include <fstream>
int main() {
    std::ofstream f("nums.txt");
    int arr[] = {1, 2, 3, 4, 5};
    for (int x : arr) f << x << " ";
    f.close();
}
```

### 5. Запись с форматированием

```cpp
#include <fstream>
#include <iomanip>
int main() {
    std::ofstream f("format.txt");
    f << std::setw(10) << "Имя" << std::setw(5) << "Возраст\n";
    f << std::setw(10) << "Анна" << std::setw(5) << 25;
    f.close();
}
```

## ЧТЕНИЕ ИЗ ФАЙЛА
### 6. Чтение всего файла построчно

```cpp
#include <fstream>
#include <iostream>
#include <string>
int main() {
    std::ifstream f("test.txt");
    std::string line;
    while (getline(f, line)) std::cout << line << "\n";
    f.close();
}
```

### 7. Чтение чисел из файла

```cpp
#include <fstream>
#include <iostream>
int main() {
    std::ifstream f("nums.txt");
    int x;
    while (f >> x) std::cout << x << " ";
    f.close();
}
```

### 8. Чтение по одному символу

```cpp
#include <fstream>
#include <iostream>
int main() {
    std::ifstream f("test.txt");
    char ch;
    while (f.get(ch)) std::cout << ch;
    f.close();
}
```

### 9. Чтение фиксированного количества байт

```cpp
#include <fstream>
#include <iostream>
int main() {
    std::ifstream f("data.txt");
    char buf[100];
    f.read(buf, 100);
    std::cout << "Прочитано: " << f.gcount() << " байт";
    f.close();
}
```

### 10. Проверка существования файла

```cpp
#include <fstream>
#include <iostream>
int main() {
    std::ifstream f("unknown.txt");
    if (f) std::cout << "Файл существует";
    else std::cout << "Файл не найден";
}
```

## БИНАРНЫЕ ФАЙЛЫ
### 11. Запись в бинарный файл

```cpp
#include <fstream>
int main() {
    int x = 12345;
    std::ofstream f("bin.dat", std::ios::binary);
    f.write((char*)&x, sizeof(x));
    f.close();
}
```

### 12. Чтение из бинарного файла

```cpp
#include <fstream>
#include <iostream>
int main() {
    int x;
    std::ifstream f("bin.dat", std::ios::binary);
    f.read((char*)&x, sizeof(x));
    std::cout << x;
    f.close();
}
```

### 13. Запись структуры в бинарный файл

```cpp
#include <fstream>
struct Point { int x, y; };
int main() {
    Point p{10, 20};
    std::ofstream f("point.bin", std::ios::binary);
    f.write((char*)&p, sizeof(p));
    f.close();
}
```

### 14. Чтение структуры из бинарного файла

```cpp
#include <fstream>
#include <iostream>
struct Point { int x, y; };
int main() {
    Point p;
    std::ifstream f("point.bin", std::ios::binary);
    f.read((char*)&p, sizeof(p));
    std::cout << p.x << ", " << p.y;
    f.close();
}
```

### 15. Запись вектора чисел в бинарный файл

```cpp
#include <fstream>
#include <vector>
int main() {
    std::vector<int> v = {1, 2, 3, 4, 5};
    std::ofstream f("vec.bin", std::ios::binary);
    f.write((char*)v.data(), v.size() * sizeof(int));
    f.close();
}
```

## ПОЗИЦИОНИРОВАНИЕ В ФАЙЛЕ
### 16. Узнать текущую позицию

```cpp
#include <fstream>
#include <iostream>
int main() {
    std::ifstream f("test.txt");
    std::cout << "Позиция: " << f.tellg();
    f.close();
}
```

### 17. Переместиться в начало файла

```cpp
#include <fstream>
#include <iostream>
int main() {
    std::ifstream f("test.txt");
    f.seekg(0, std::ios::beg);
    std::cout << "Мы в начале!";
    f.close();
}
```

### 18. Переместиться на 10 байт от начала

```cpp
#include <fstream>
int main() {
    std::ifstream f("test.txt");
    f.seekg(10);
    // чтение начнётся с 10-го байта
    f.close();
}
```

### 19. Переместиться в конец файла

```cpp
#include <fstream>
#include <iostream>
int main() {
    std::ifstream f("test.txt");
    f.seekg(0, std::ios::end);
    std::cout << "Размер файла: " << f.tellg() << " байт";
    f.close();
}
```

### 20. Переместиться на -5 байт от конца

```cpp
#include <fstream>
int main() {
    std::ifstream f("test.txt");
    f.seekg(-5, std::ios::end);
    // чтение последних 5 байт
    f.close();
}
```

## ОБРАБОТКА ОШИБОК И СОСТОЯНИЯ
### 21. Проверка на конец файла

```cpp
#include <fstream>
#include <iostream>
int main() {
    std::ifstream f("test.txt");
    char ch;
    while (!f.eof()) {
        f.get(ch);
        if (!f.eof()) std::cout << ch;
    }
    f.close();
}
```

### 22. Очистка флагов ошибок

```cpp
#include <fstream>
int main() {
    std::ifstream f("test.txt");
    // ... операции ...
    f.clear();  // сброс флагов ошибок
    f.close();
}
```

### 23. Обработка ошибки открытия

```cpp
#include <fstream>
#include <iostream>
int main() {
    std::fstream f;
    f.open("file.txt");
    if (f.fail()) std::cout << "Не удалось открыть!";
    f.close();
}
```

### 24. Использование исключений

```cpp
#include <fstream>
#include <iostream>
int main() {
    std::ifstream f;
    f.exceptions(std::ifstream::failbit);
    try {
        f.open("nofile.txt");
    } catch (std::ifstream::failure& e) {
        std::cout << "Исключение: " << e.what();
    }
}
```

## РАБОТА С FSTREAM (ЧТЕНИЕ + ЗАПИСЬ)
### 25. Открытие файла для чтения и записи

```cpp
#include <fstream>
int main() {
    std::fstream f("data.txt", std::ios::in | std::ios::out);
    f << "Запись";
    f.seekg(0);
    // можно читать
    f.close();
}
```

### 26. Усечение файла при открытии

```cpp
#include <fstream>
int main() {
    std::ofstream f("data.txt", std::ios::trunc);
    // старые данные будут удалены
    f << "Новые данные";
    f.close();
}
```

## УДАЛЕНИЕ И ПЕРЕИМЕНОВАНИЕ
### 27. Удаление файла (C++17)

```cpp
#include <filesystem>
#include <iostream>
int main() {
    if (std::filesystem::remove("old.txt"))
        std::cout << "Файл удалён";
    else std::cout << "Ошибка удаления";
}
```

### 28. Переименование файла

```cpp
#include <cstdio>
int main() {
    rename("old.txt", "new.txt");
}
```

## ПРАКТИЧЕСКИЕ ПРИМЕРЫ
### 29. Копирование текстового файла

```cpp
#include <fstream>
int main() {
    std::ifstream src("source.txt");
    std::ofstream dst("dest.txt");
    dst << src.rdbuf();
    src.close(); dst.close();
}
```

### 30. Подсчёт символов в файле

```cpp
#include <fstream>
#include <iostream>
int main() {
    std::ifstream f("test.txt", std::ios::ate);
    std::cout << "Символов: " << f.tellg();
    f.close();
}
```