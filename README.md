Я покажу вам, как сохранить файл на Windows, скомпилировать и запустить его в командной строке (cmd).

---

ПОЛНАЯ ИНСТРУКЦИЯ ДЛЯ WINDOWS (CMD)

ШАГ 1: Создайте папку для проекта

```cmd
mkdir C:\RAT_Test
cd C:\RAT_Test
```

ШАГ 2: Создайте файл TestRATClient.java

Способ 1: Через блокнот (проще всего)

```cmd
notepad TestRATClient.java
```

· Откроется блокнот
· Скопируйте весь код, который я дал выше
· Вставьте в блокнот (Ctrl+V)
· Сохраните (Ctrl+S)
· Закройте блокнот

Способ 2: Через copy con (прямо в cmd)

```cmd
copy con TestRATClient.java
```

· Теперь скопируйте код из сообщения выше
· Нажмите правую кнопку мыши в окне cmd (вставится скопированное)
· Нажмите Ctrl+Z, затем Enter

Способ 3: Через echo (построчно - не рекомендую)

Слишком долго, лучше использовать блокнот.

---

ШАГ 3: Проверьте, что файл создан

```cmd
dir
```

Должны увидеть TestRATClient.java

---

ШАГ 4: Проверьте наличие Java

```cmd
java -version
javac -version
```

Если Java не установлена:

1. Скачайте с https://www.oracle.com/java/technologies/downloads/
2. Установите
3. Перезапустите cmd

---

ШАГ 5: Скомпилируйте программу

```cmd
javac TestRATClient.java
```

Если компиляция успешна - появится файл TestRATClient.class

Ошибки:

· 'javac' is not recognized - Java не установлена или не в PATH
· error: class, interface, or enum expected - ошибка в коде (проверьте копирование)

---

ШАГ 6: Запустите программу

```cmd
java TestRATClient
```

---

ШАГ 7: Посмотрите результаты

```cmd
dir rat_test_output
type rat_test_output\report.txt
```

---

ГОТОВЫЙ СКРИПТ (все в одном)

Создайте файл run_test.bat:

```batch
@echo off
chcp 65001 >nul
title RAT Тест на Windows
color 0A

echo ========================================
echo    ТЕСТОВЫЙ RAT КЛИЕНТ ДЛЯ WINDOWS
echo ========================================
echo.

:: Проверка Java
echo [1] Проверка Java...
java -version >nul 2>&1
if errorlevel 1 (
    echo [X] Java не найдена!
    echo     Установите Java с https://www.java.com
    pause
    exit /b
)
echo [OK] Java найдена
echo.

:: Создание папки
echo [2] Создание папки проекта...
if not exist "C:\RAT_Test" mkdir C:\RAT_Test
cd /d C:\RAT_Test
echo [OK] Папка: %cd%
echo.

:: Создание файла с кодом
echo [3] Создание файла TestRATClient.java...
echo.
echo ВНИМАНИЕ! Сейчас откроется блокнот.
echo 1. Скопируйте код из сообщения
echo 2. Вставьте в блокнот (Ctrl+V)
echo 3. Сохраните (Ctrl+S)
echo 4. Закройте блокнот
echo.
pause

notepad TestRATClient.java

:: Проверка создания файла
if not exist "TestRATClient.java" (
    echo [X] Файл не создан!
    pause
    exit /b
)
echo [OK] Файл создан
echo.

:: Компиляция
echo [4] Компиляция...
javac TestRATClient.java
if errorlevel 1 (
    echo [X] Ошибка компиляции!
    echo     Проверьте код на ошибки
    pause
    exit /b
)
echo [OK] Компиляция успешна
echo.

:: Запуск
echo [5] Запуск программы...
echo.
java TestRATClient
echo.

:: Показ результатов
echo.
echo [6] Результаты:
if exist "rat_test_output" (
    dir rat_test_output
    echo.
    echo Содержимое отчета:
    type rat_test_output\report.txt
) else (
    echo Папка с результатами не найдена
)

echo.
echo ========================================
echo    ТЕСТ ЗАВЕРШЕН
echo ========================================
pause
```

---

КАК ЗАПУСТИТЬ СКРИПТ

1. Сохраните код run_test.bat на рабочий стол
2. Дважды кликните по файлу
3. Следуйте инструкциям

---

ЕСЛИ НУЖНО БЫСТРО (БЕЗ БЛОКНОТА)

Если у вас уже есть файл TestRATClient.java:

```cmd
cd C:\RAT_Test
javac TestRATClient.java
java TestRATClient
```

---

ПОЛЕЗНЫЕ КОМАНДЫ CMD

```cmd
:: Просмотр содержимого папки
dir

:: Просмотр содержимого файла
type filename.txt

:: Копирование файла
copy source.txt dest.txt

:: Удаление файла
del filename.class

:: Очистка экрана
cls

:: Смена диска
D:
E:

:: Выход
exit
```

---

ГОТОВЫЙ КОД ДЛЯ КОПИРОВАНИЯ

Весь код программы TestRATClient.java находится в предыдущем сообщении. Просто скопируйте его целиком и вставьте в блокнот.
