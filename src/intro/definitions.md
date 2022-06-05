## Используемые обозначения

Я буду везде стараться показывать процесс выполнения команд. Сами же команды буду описывать так:

<div id="termynal" data-termynal data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">whoami</span>
</div>

Знак доллара перед началом команды означает, что эта команда должна быть запущена от текущего пользователя. Эти команды ты можешь копировать к себе в консоль. Копируя их, не копируй знак доллара и пробел после него в начале команды! Терминал их не распознает!

Процесс выполнения команд будет выглядеть следующим образом:
<div id="termynal" data-termynal data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">whoami</span>
    <span class="no-select" data-ty>pushkeen</span>
</div>

Если вдруг надо выполнить команду из под суперпользователя (aka рута):
<div id="termynal" data-termynal data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[/] #">cat /etc/passwd</span>
</div>

Перед запуском таких команд обязательно надо делать
<div id="termynal" data-termynal data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">su -</span>
    <span class="no-select" data-ty>Enter password: ********</span>
    <span data-ty="input" data-ty-prompt="[/] #"></span>
</div>