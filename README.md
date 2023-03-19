# Report--lab1
## 1. Скачайте библиотеку boost с помощью утилиты wget. Адрес для скачивания https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz

```
$ wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
```
![VirtualBox_kali-linux-2023 1-virtualbox-amd64_19_03_2023_13_08_55](https://user-images.githubusercontent.com/128289395/226183524-5c8c13aa-1d4c-4ebe-a76f-ffc5b7059cb2.png)


## 2.Разархивируйте скаченный файл в директорию ~/boost_1_69_0

```
$ tar -xvf boost_1_69_0.tar.gz
```
![VirtualBox_kali-linux-2023 1-virtualbox-amd64_19_03_2023_16_49_46](https://user-images.githubusercontent.com/128289395/226183538-e2942f79-74c8-47e0-a22f-b2dcbca7f423.png)


дальше работаем в ~/boost_1_69_0

## 3. Подсчитайте количество файлов в директории ~/boost_1_69_0 не включая вложенные директории

```
$ ls -l | grep "^-" | wc -l
```

## 4. Подсчитайте количество файлов в директории ~/boost_1_69_0 включая вложенные директории.

```
$ ls -l -R | wc -l
```
![VirtualBox_kali-linux-2023 1-virtualbox-amd64_19_03_2023_16_51_50](https://user-images.githubusercontent.com/128289395/226183567-a9c16d31-edbb-4fe6-9a08-32e3b82efc06.png)


## 5. Подсчитайте количество заголовочных файлов, файлов с расширением .cpp, сколько остальных файлов (не заголовочных и не .cpp).

```
$ ls -l -R | grep -c *.hpp
$ ls -l -R | grep -c *.cpp
$ ls -l -R | grep -v *.hpp | grep -v *.cpp | grep -v 'итого' | wc -l
```

![VirtualBox_kali-linux-2023 1-virtualbox-amd64_19_03_2023_16_53_11](https://user-images.githubusercontent.com/128289395/226183581-5dbba33e-8acb-46bb-a646-56dcb9774c5a.png)


## 6.Найдите полный пусть до файла any.hpp внутри библиотеки boost.

```
$ find $PWD -type f -name any.hpp
```
![VirtualBox_kali-linux-2023 1-virtualbox-amd64_19_03_2023_16_54_05](https://user-images.githubusercontent.com/128289395/226183591-c9ab8199-9f9a-43bf-bf2d-64dc9e041d5e.png)


## 7. Выведите в консоль все файлы, где упоминается последовательность boost::asio

```
$ grep -R -l "boost::asio"
```
![VirtualBox_kali-linux-2023 1-virtualbox-amd64_19_03_2023_16_54_42](https://user-images.githubusercontent.com/128289395/226183593-77d9f745-5f68-4d3f-b89f-04ce3bb0e769.png)


## 8. Скомпилирутйе boost. Можно воспользоваться инструкцией или ссылкой.

```
$ ./bootstrap.sh --prefix=boost_output
$ ./b2 install
```

![VirtualBox_kali-linux-2023 1-virtualbox-amd64_19_03_2023_16_55_42](https://user-images.githubusercontent.com/128289395/226183607-67df29cc-9014-4c7f-b480-a79f75fe7966.png)

## 9. Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию ~/boost-libs.

```
$ mv ~/boost_1_69_0/boost_output/lib ~/boost-libs
```

![VirtualBox_kali-linux-2023 1-virtualbox-amd64_19_03_2023_17_21_34](https://user-images.githubusercontent.com/128289395/226183631-4423f4eb-d044-47e2-9f89-6ff462ed7320.png)

## 10. Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.

```
$ du -h -a
```
![VirtualBox_kali-linux-2023 1-virtualbox-amd64_19_03_2023_17_22_17](https://user-images.githubusercontent.com/128289395/226183657-d87f02da-fcf5-4bfa-86f8-f030a471794d.png)


## 11. Найдите топ10 самых "тяжёлых"

```
$ du -h -a | sort -r -h | head -n 10
```
![VirtualBox_kali-linux-2023 1-virtualbox-amd64_19_03_2023_17_22_41](https://user-images.githubusercontent.com/128289395/226183677-9c90327c-ec4e-4ad3-8d9a-abc750cf0121.png)
