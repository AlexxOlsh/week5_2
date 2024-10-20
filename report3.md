# Управление пользователями и группами в Linux

В Linux система управления пользователями и группами играет ключевую роль в обеспечении безопасности и организации доступа к ресурсам системы.

### Создание пользователей и групп

**adduser <имя_пользователя>:** Создает нового пользователя с заданным именем.
- Пример: `adduser newuser` создаст пользователя с именем newuser.

**groupadd <имя_группы>:** Создает новую группу.
- Пример: `groupadd developers` создаст группу с именем developers.


### Настройка пользователей

**usermod:** Изменяет параметры существующего пользователя.

- **-a -G <группа>:** Добавляет пользователя в группу.
- **-d <каталог>:** Устанавливает домашний каталог.
- **-l <новое_имя>:** Переименовывает пользователя.
- **-p <пароль>:** Устанавливает новый пароль.

- Пример: `usermod -a -G sudo newuser` добавит пользователя newuser в группу sudo.


### Настройка групп

**groupmod:** Изменяет параметры существующей группы.
- **-n <новое_имя>:** Переименовывает группу.
- Пример: `groupmod -n admins developers` переименует группу developers в admins.


### Права доступа к файлам и каталогам

**chmod <права> <файл>:** Изменяет права доступа к файлу.
- Права задаются в восьмеричном формате (например, 755).
- Пример: `chmod 755 script.sh` дает владельцу все права, группе чтения и выполнения, а остальным - только чтение.

**chown <пользователь>:<группа> <файл>:** Изменяет владельца и группу файла.
- Пример: `chown root:root /etc/shadow` сделает пользователя root владельцем и членом группы root для файла /etc/shadow.

 
### Чтение прав доступа

**ls -l:** Выводит подробную информацию о файле, включая права доступа.
- Первые 10 символов строки представляют собой права доступа:
    - Первые три символа - права владельца (r - чтение, w - запись, x - выполнение).
    - Следующие три символа - права группы.
    - Последние три символа - права для всех остальных пользователей.
  
- Пример: `-rw-r--r--` означает, что владелец имеет права на чтение и запись, группа и остальные пользователи - только на чтение.

### Расширенные возможности

**sudo:** Позволяет выполнять команды от имени другого пользователя (обычно root).
- Пример: `sudo apt update` обновит список пакетов с правами суперпользователя.
**visudo:** Безопасный редактор файла /etc/sudoers, который определяет, какие пользователи могут использовать команду sudo.

### Пример сценария

    `Bash
    ###### Создать группу для разработчиков
    groupadd developers
    
    ###### Создать пользователя и добавить его в группу разработчиков
    adduser newdev
    usermod -a -G developers newdev
    
    ###### Создать каталог для проектов и дать группе разработчиков права на запись
    mkdir /var/projects
    chown root:developers /var/projects
    chmod 775 /var/projects
    
    ###### Разрешить пользователю newdev использовать sudo для обновления системы
    visudo  # Добавить строку: newdev ALL=(ALL) ALL`