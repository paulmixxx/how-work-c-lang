# How work C language

## Теория

https://ru.wikipedia.org/wiki/Си_(язык_программирования)


### Исходный код

Передаем инструкции непосредственно процессору или делаем системные вызовы ОС

* https://learn.microsoft.com/en-us/windows-hardware/drivers/debugger/x64-architecture
* https://linasm.sourceforge.net/docs/instructions/index.php
* https://www.felixcloutier.com/x86/
* https://manpages.ubuntu.com/manpages/lunar/ru/man2/syscalls.2.html
* https://filippo.io/linux-syscall-table/
* https://gist.github.com/yamnikov-oleg/454f48c3c45b735631f2


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


## ДЗ

Сделать `strace` популярных команд: `ls`, `ping`, `nslookup`, `curl`, `id`, `w`
