## Используемые обозначения

Я буду везде стараться показывать процесс выполнения команд. Сами же команды буду описывать так:

<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">whoami</span>
</div>

Жёлто-оранжевым показан непосредственно ввод команды (*whoami*) - то, что вы по идее будете вводить (кстати, его можно копировать!). Белым - результат её выполнения.


Знак доллара перед началом команды означает, что эта команда должна быть запущена от текущего пользователя. Эти команды ты можешь копировать к себе в консоль. Копируя их, не копируй знак доллара и пробел после него в начале команды! Терминал их не распознает!

Процесс выполнения команд будет выглядеть следующим образом:
<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">whoami</span>
    <span class="no-select" data-ty>pushkeen</span>
</div>

**Результат выполнения команд в нарисованном терминале в документации не всегда будет совпадать с оригинальным, здесь он упрощён для наглядности процесса!**

Если вдруг надо выполнить команду из под суперпользователя (aka рута):
<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[/] #">cat /etc/passwd</span>
</div>

Перед запуском таких команд обязательно надо делать
<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">su -</span>
    <span class="no-select" data-ty>Enter password: ********</span>
    <span data-ty="input" data-ty-prompt="[/] #"></span>
</div>

Так же есть команды, которые подразумевают собой заполнение файлов. Они выглядят так:
<div id="termynal" data-termynal data-ty-title="nano ~/.bashrc" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty>
        <p>alias xx="exit"</p>
        <p>alias purr="git pull --rebase"</p>
    </span>
</div>

Хоть в названии терминала и написано nano, по сути здесь может быть использован любой установленный текстовый редактор, например vim или vscode.

Если я попрошу сделать так
<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">cleanup_spec {PACKAGE_NAME}.spec</span>
</div>

Вместо `{PACKAGE_NAME}` вы подставляете название того пакета, которое хотите собрать. Я буду показывать на примере `mitmproxy`.
То есть в вашем случае (вернее моём) реальная команда будет выглядеть так:
<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">cleanup_spec mitmproxy.spec</span>
</div>

Это правило распространяется как на команды, так и на содержимое файлов.