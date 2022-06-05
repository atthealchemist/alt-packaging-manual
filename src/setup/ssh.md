## Конфигурация SSH

Для настройки инфраструктуры git.alt нужно прописать в `~/.ssh/config` следующие строки:
```bash
# Репозиторий
Host git.alt  # Здесь может быть любой удобный тебе алиас
  HostName gitery.altlinux.org
  User alt_<USERNAME>  # Где <USERNAME> - твой псевдоним, зарегистрированный ранее, т.е. pushkeen
  Port 222 

# Сборочница
Host gyle.alt  # Здесь может быть любой удобный тебе алиас
  HostName gyle.altlinux.org
  User alt_USERNAME  # Где <USERNAME> - твой псевдоним, зарегистрированный ранее, т.е. pushkeen
  Port 222
```

Список доступных команд каждого сервиса выдаётся при ssh-логине с командой help:
```bash
$ ssh git.alt help
```

```bash
$ ssh gyle.alt help
```

Более подробная информация обо всех используемых командах находится [здесь](https://www.altlinux.org/Git.alt/Справочник)