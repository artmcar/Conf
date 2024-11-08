# Задание 1
## Вывести отсортированный в алфавитном порядке список имен пользователей в файле passwd (вам понадобится grep)

```
grep '^[^:]' /etc/passwd | cut -d: -f1 | sort
```

![11](https://github.com/user-attachments/assets/c5baf9a9-f72a-4560-9b64-63602b2d0e3e)


# Задание 2
## Вывести данные /etc/protocols в отформатированном и отсортированном порядке для 5 наибольших портов

```
cat /etc/protocols | awk '{print $2, $1}' | sort -nr | head -n5
```

![12](https://github.com/user-attachments/assets/d6c0f442-d1db-4763-86ee-85d28a932884)



# Задание 3

```
#!/bin/bash
if [ -z "$1" ]; then
  echo "Использовать: $0 \"Текст для баннера\""
  exit 1
fi
text="$1"
length=${#text}
banner_length=$((length + 4))
printf '+%s+\n' "$(printf '%*s' "$banner_length" '' | tr ' ' '-')"
printf '| %s |\n' "$text"
printf '+%s+\n' "$(printf '%*s' "$banner_length" '' | tr ' ' '-')"
```

![13](https://github.com/user-attachments/assets/016d547b-fdac-40f4-8ee4-fcddfc497ddf)



# Задание 4
## Написать программу для вывода всех идентификаторов (по правилам C/C++ или Java) в файле (без повторений)

```
grep -oE '\b[A-Za-z_][A-Za-z0-9_]*\b' main.cpp | sort -u
```
![14](https://github.com/user-attachments/assets/c0df7bc4-e295-4612-9d04-d3ae735039a2)


# Задание 5
## Написать программу для регистрации пользовательской команды (правильные права доступа и копирование в /usr/local/bin).

```
#!/bin/bash

file=$1

chmod 755 "./$file"

sudo cp "$file" /usr/local/bin/
```

# Задание 6
## Написать программу для проверки наличия комментария в первой строке файлов с расширением c, js и py.


```
#!/bin/bash
for file in *.{c,js,py}; do
  if [ -f "$file" ]; then
    first_line=$(head -n 1 "$file")
    if [[ "$first_line" == /* ]] || [[ "$first_line" == \#* ]] || [[ "$first_line" == "//"* ]]; then
      echo "$file: комментарий найден в первой строке."
    else
      echo "$file: комментарий не найден."
    fi
  fi
done
```
![16](https://github.com/user-attachments/assets/c4b5a8fe-ea33-4300-838b-1eb4f0bced2c)



# Задание 7
## Написать программу для нахождения файлов-дубликатов (имеющих 1 или более копий содержимого) по заданному пути (и подкаталогам)

```
#!/bin/bash
if [ "$#" -ne 1 ]; then
    echo "Использовать: $0 <директория>"
    exit 1
fi

directory="$1"
if [ ! -d "$directory" ]; then
    echo "Ошибка: директория '$directory' не найдена"
    exit 1
fi

find "$directory" -type f -exec md5sum {} + | sort | awk '{
    if ($1 in seen) {
        print "Дубликат: " $2 " <--> " seen[$1];
    } else {
        seen[$1] = $2;
    }
}'
```
![17](https://github.com/user-attachments/assets/fa3a878d-a770-4025-ae20-a521f5defa6b)


# Задание 8
## Написать программу, которая находит все файлы в данном каталоге с расширением, указанным в качестве аргумента и архивирует все эти файлы в архив tar.

```
#!/bin/bash
    if [ -z "$1" ] || [ -z "$2" ]; then
        echo "укажите путь и расширение"
        exit 1
    fi
    search_path="$1"
    extension="$2"
    archive_name="archive.tar"
    if [ ! -d "$search_path" ]; then
        echo "путь $search_path не существует или не является директорией"
        exit 1
    fi
    echo "файл с расширением $extension из $search_path архивирован в $archive_name..."
    find "$search_path" -type f -name "*.$extension" | tar -cvf "$archive_name" -T -
```
![18](https://github.com/user-attachments/assets/a82edac2-b174-40c0-886d-0a3206b216cc)



# Задание 9
## Написать программу, которая заменяет в файле последовательности из 4 пробелов на символ табуляции. Входной и выходной файлы задаются аргументами.

```
#!/bin/bash

if [ "$#" -ne 2 ]; then
    echo "Использовать: $0 <входной файл> <выходной файл>"
    exit 1
fi

input_file="$1"
output_file="$2"

if [ ! -f "$input_file" ]; then
    echo "Ошибка: входной файл '$input_file' не найден"
    exit 1
fi

if sed 's/    /\t/g' "$input_file" > "$output_file"; then
    echo "Операция успешна. Выходной файл: $output_file"
else
    echo "Ошибка при обработке файла"
    exit 1
fi
```

![19](https://github.com/user-attachments/assets/3b601276-205d-49b9-a518-f2f0efafb733)



# Задание 10
## Написать программу, которая выводит названия всех пустых текстовых файлов в указанной директории. Директория передается в программу параметром.


```
#!/bin/bash

if [ "$#" -ne 1 ]; then
    echo "Использовать: $0 <директория>"
    exit 1
fi

directory="$1"

if [ ! -d "$directory" ]; then
    echo "Ошибка: директория '$directory' не найдена"
    exit 1
fi

find "$directory" -type f -name "*.txt" -empty -print
```
![110](https://github.com/user-attachments/assets/25db33ab-efa6-498e-894a-a845a1e58176)




