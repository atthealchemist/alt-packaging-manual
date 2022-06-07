## Конфигурация SSH

Для настройки инфраструктуры git.alt нужно прописать в `~/.ssh/config` следующие строки:
<div id="termynal" data-termynal data-ty-title="nano ~/.ssh/config" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty>
        <p># Репозиторий</p>
        <p>Host git.alt  # Здесь может быть любой удобный тебе алиас</p>
        <p>&nbsp;&nbsp;&nbsp;&nbsp;HostName gitery.altlinux.org</p>
        <p>&nbsp;&nbsp;&nbsp;&nbsp;User alt_USERNAME  # Где USERNAME - твой псевдоним, зарегистрированный ранее, т.е. pushkeen</p>
        <p>&nbsp;&nbsp;&nbsp;&nbsp;Port 222</p>
        <p></p>
    </span> 
    <span data-ty>
        <p># Сборочница</p>
        <p>Host gyle.alt  # Здесь может быть любой удобный тебе алиас</p>
        <p>&nbsp;&nbsp;&nbsp;&nbsp;HostName gyle.altlinux.org</p>
        <p>&nbsp;&nbsp;&nbsp;&nbsp;User alt_USERNAME  # Где USERNAME> - твой псевдоним, зарегистрированный ранее, т.е. pushkeen</p>
        <p>&nbsp;&nbsp;&nbsp;&nbsp;Port 222</p>
        <p></p>
    </span>
</div>

Список доступных команд каждого сервиса выдаётся при ssh-логине с командой help:
<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">ssh git.alt help</span>
    <span class="no-select" data-ty>...</span>
    <span data-ty="input" data-ty-prompt="[~] $">ssh gyle.alt help</span>
    <span class="no-select" data-ty>...</span>
</div>

Более подробная информация обо всех используемых командах находится [здесь](https://www.altlinux.org/Git.alt/Справочник)