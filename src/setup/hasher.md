# Конфигурация Hasher

Для того, чтобы пользоваться Hasher, надо добавить в него нашего пользователя - *pushkeen*.
<div id="termynal" data-termynal data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[root@localhost /] #">hasher-useradd pushkeen</span>
    <span class="no-select" data-ty>Adding user pushkeen to group pushkeen_a</span>
    <span class="no-select" data-ty>Adding user pushkeen to group pushkeen_b
</span>
    <span class="no-select" data-ty>Adding user pushkeen to group hashman</span>
    <span data-ty="input" data-ty-prompt="[root@localhost /] #">exit</span>
    <span data-ty="input" data-ty-prompt="[pushkeen@localhost ~] $"></span>
</div>

Не забудь выйти из под рута командой `exit и перелогиниться, чтобы новые группы применились к твоему пользователю.

Немного подробнее о созданных группах:
Группа *pushkeen_a* - псевдо-root для получения полных прав в среде сборки пакета.
Группа *pushkeen_b* - группа-сборщик пакета. То есть те, кто состоят в этой группе, имеют право собирать пакеты в Hasher.
Группа *hashman* - пользователь, под которым запускается Hasher.

Для простейшей конфигурации Hasher создай каталог `~/.hasher`:
```bash
$ mkdir -p ~/.hasher
$ mkdir -p ~/repo/
```
И создай внутри него файл `~/.hasher/config` командой
```bash
$ nano ~/.hasher/config
```
Добавь в него следующие строчки:
```bash
USER=pushkeen
workdir="/tmp/.private/pushkeen/"
target=x86_64
packager="`rpm --eval %packager`"
apt_config="$HOME/.hasher/apt.conf"
def_repo="$HOME/repo"
mount=/dev/pts,/proc
```
После чего нажимай комбинацию клавиш <kbd>Ctrl</kbd> + <kbd>O</kbd> (да, это английская О, не ноль) для сохранения файла.

Если ты хочешь собирать пакеты для 32-битной архитектуры, меняй `target=x86_64` в строчках выше на `target=i586`.

Полный список поддерживаемых архитектур можно найти [здесь](https://www.altlinux.org/Ports)

После всего этого (мы же хотим проверять и устанавливать наш свежесобранный пакет как из репозитория, не так ли?)
мы создаём файл `/etc/apt/sources.list.d/hasher_local_build_repo`
со следующим содержимым:
```conf
rpm file:/home/pushkeen/repo x86_64 hasher
```

После чего делаем `sudo apt-get update`, чтобы синхронизироваться с нашим локальным репозиторием.
