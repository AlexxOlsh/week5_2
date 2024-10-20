# Управление процессами в Linux

## Основные команды для работы с процессами

**ps**

Команда `ps` выводит информацию о процессах, выполняющихся в системе.


**Основные опции:**
- **-a:** Выводит все процессы.
- **-u:** Выводит информацию о пользователях, владеющих процессами.
- **-x:** Выводит процессы, не связанные с терминалом.
- **aux:** Комбинация опций для вывода подробной информации о всех процессах.

Пример:
`Bash
ps aux`

Выведет список всех процессов с подробной информацией о PID, пользователях, времени выполнения и т.д.


**top**

Команда `top` предоставляет динамический, обновляемый список процессов. Это интерактивный инструмент, позволяющий отсортировать процессы по различным критериям (PID, CPU, память и т.д.) и отслеживать их состояние в реальном времени.

**Основные клавиши управления:**
- **q:** Выход из top.
- **k:** Убить процесс.
- **h:** Справка по командам.

Пример:
`Bash
top`


**kill**

Команда `kill` используется для завершения процессов.

**Основные сигналы:**
- **9:** Сигнал TERM, который принудительно завершает процесс.
- **15:** Сигнал INT, который посылает процессу запрос на завершение.

Пример:
`Bash
kill -9 <PID>`

Принудительно завершит процесс с указанным PID.


**htop**

Команда `htop` является более современной и удобной альтернативой `top`. Она предлагает более интуитивный интерфейс, цветное выделение и дополнительные возможности, такие как поиск по процессам, сортировка и группировка.

**Установка:**
`Bash
sudo apt install htop  # Для Ubuntu/Debian
sudo yum install htop    # Для CentOS/RHEL`

**Использование:**
`Bash
htop`

Запустит программу htop.


**Примеры использования**
- **Поиск процесса по имени:**
`Bash
ps aux | grep firefox`

- **Убить процесс с PID 1234:**
`Bash
kill -9 1234`

- **Отсортировать процессы в top по использованию CPU:** В программе top нажать клавишу 1 для сортировки по использованию CPU.