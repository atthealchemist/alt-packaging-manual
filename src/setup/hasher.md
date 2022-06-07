## Конфигурация Hasher

Для того, чтобы пользоваться Hasher, надо добавить в него нашего пользователя - *pushkeen*.
<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[root@localhost /] #">hasher-useradd pushkeen</span>
    <span class="no-select" data-ty>
        <p>Adding user pushkeen to group pushkeen_a</p>
        <p>Adding user pushkeen to group pushkeen_b</p>
        <p>Adding user pushkeen to group hashman</p>
    </span>
    <span data-ty="input" data-ty-prompt="[root@localhost /] #">exit</span>
    <span data-ty="input" data-ty-prompt="[pushkeen@localhost ~] $"></span>
</div>

Не забудь выйти из под рута командой `exit` и перелогиниться, чтобы новые группы применились к твоему пользователю.

Немного подробнее о созданных группах:
- Группа *pushkeen_a (admin)* - псевдо-root для получения полных прав в среде сборки пакета.
- Группа *pushkeen_b (builder)* - группа-сборщик пакета. То есть те, кто состоят в этой группе, имеют право собирать пакеты в Hasher.
- Группа *hashman* - пользователь, под которым запускается Hasher.

Для простейшей конфигурации Hasher создай каталоги `~/.hasher` - где будут лежать настройки непосредственно для Hasher и `~/repo/` - где будет локальный репозиторий, куда Hasher будет собирать твои пакеты:
<div id="termynal" data-termynal data-ty-title="bash"  data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">mkdir -p ~/{.hasher,repo,}</span>
</div>

И создай внутри него файл `~/.hasher/config` командой
<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">nano ~/.hasher/config</span>
</div>

Добавь в него следующие строчки:
<div id="termynal" data-termynal data-ty-title="nano" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty>
        <p>USER=pushkeen</p>
        <p>workdir="/tmp/.private/pushkeen/"</p>
        <p>target=x86_64</p>
        <p>packager="`rpm --eval %packager`"</p>
        <p>apt_config="$HOME/.hasher/apt.conf"</p>
        <p>def_repo="$HOME/repo"</p>
        <p>mount=/dev/pts,/proc</p>
    </span>
</div>
После чего нажимай комбинацию клавиш <kbd>Ctrl</kbd> + <kbd>O</kbd> (да, это английская О, не ноль) для сохранения файла.

Если ты хочешь собирать пакеты для 32-битной архитектуры, меняй `target=x86_64` в строчках выше на `target=i586`.

Полный список поддерживаемых архитектур можно найти [здесь](https://www.altlinux.org/Ports)

После всего этого (мы же хотим проверять и устанавливать наш свежесобранный пакет как из репозитория, не так ли?)
мы создаём файл `/etc/apt/sources.list.d/hasher_repo`
<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">sudo nano /etc/apt/sources.list.d/hasher_repo</span>
</div>
со следующим содержимым:

<div id="termynal" data-termynal data-ty-title="nano" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty>
        <p>rpm file:/home/pushkeen/repo x86_64 hasher</p>
    </span>
</div>

После чего делаем 
<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">sudo apt-get update</span>
</div>
чтобы синхронизироваться с нашим локальным репозиторием.
