# How work C language

## Теория

https://ru.wikipedia.org/wiki/Си_(язык_программирования)


### Исходный код

Передаем инструкции непосредственно процессору или делаем системные вызовы ОС в виде языковых конструкций или вызова функций и библиотек.

* https://learn.microsoft.com/en-us/windows-hardware/drivers/debugger/x64-architecture
* https://linasm.sourceforge.net/docs/instructions/index.php
* https://www.felixcloutier.com/x86/
* https://manpages.ubuntu.com/manpages/lunar/ru/man2/syscalls.2.html
* https://filippo.io/linux-syscall-table/
* https://gist.github.com/paulmixxx/e031042117d58c4d8a2f3e66b67178f3


### Компиляция

Исходный код => Объектный файл => Исполняемый файл

1. Препроцессинг
2. Компиляция
3. Компоновка/Линковка/Сборка

* https://foxford.ru/wiki/informatika/etapy-kompilyatsii
* https://www.studytonight.com/c/c-compilation-process.php
* https://ru.wikipedia.org/wiki/Исходный_код
* https://ru.wikipedia.org/wiki/Объектный_модуль
* https://ru.wikipedia.org/wiki/Исполняемый_файл


### Исполнение

* Просим ОС вызвать Исполняемый файл через командный интерпретатор
  * Системные вызовы
    * Инструкции архитектуры

* https://ru.wikipedia.org/wiki/Интерпретатор_командной_строки
* https://ru.wikipedia.org/wiki/Оболочка_операционной_системы
* https://ru.wikipedia.org/wiki/Интерфейс_командной_строки


## Практика

Создаем файл `HelloWorld.c`:

```C
// Simple C program to display "Hello World"

// Header file for input output functions
#include <stdio.h>

// main function -
// where the execution of program begins
int main()
{

	// prints hello world
	printf("Hello World");

	return 0;
}

```

Компилируем:

```bash
gcc -o helloworld HelloWorld.c
```

Посмотрим тип файла:

```bash
file helloworld
```

Запускаем:

```bash
./helloworld
```

Заглянем под капот:

Связь с динамическими библиотеками
```bash
ldd a.out
man libc
man ld.so
```

Вызов библиотечных функций
```bash
ltrace -f ./a.out
man puts
```

Вызов системных функций

```bash
strace ./helloworld
```

Видим системные вызовы ОС. Посмотрим некоторые:

```bash
man 2 execve
man 2 access
man 2 newfstatat
man 2 write
```

Попробуем вызвать для bash:

```bash
strace bash
```

Остановить:

CTRL + D

Системные вызовы:
* [execve (2)](https://www.opennet.ru/cgi-bin/opennet/man.cgi?topic=execve&category=2)
* [access (2)](https://www.opennet.ru/man.shtml?topic=access&category=2&russian=0)
* [newfstatat (2)](https://man.archlinux.org/man/newfstatat.2.en)
* [write (2)](https://www.opennet.ru/man.shtml?topic=write&category=2&russian=0)

https://www.geeksforgeeks.org/c-hello-world-program/

## ДЗ

Сделать `strace` популярных команд: `ls`, `ping`, `nslookup`, `curl`, `id`, `w`
