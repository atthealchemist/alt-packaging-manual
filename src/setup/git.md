## Конфигурация git

Сначала конфигурируем git для подписания своих коммитов.

<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">git config --global user.name 'Alexander Pushkin'</span>
    <span data-ty="input" data-ty-prompt="[~] $">git config --global user.email 'pushkeen@altlinux.org'</span>
    <span data-ty="input" data-ty-prompt="[~] $">git config --global user.signingkey 'DEADBEEF'</span>
</div>

Уже предвосхищаю твой вопрос - "где посмотреть `user.signingkey`"? 
Всё просто, следующей командой:
<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">gpg --list-keys | grep -B 1 'Alexander Pushkin'</span>
</div>

Ну и как всегда, наглядное представление того, как это будет выглядеть:
<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">gpg --list-keys | grep -B 1 'Alexander Pushkin'</span>
    <span class="no-select" data-ty>
        <p>pub   4096R/DEADBEEF 2022-06-03  # <-- DEADBEEF - наш подписной ключик</p>
        <p>uid                  Alexander Pushkin (pushkeen gpg key) <pushkeen@altlinux.org></p>
    </span>
</div>

В конечном итоге твой `git config --global --list` должен выглядеть вот так:
<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">git config --global --list</span>
    <span class="no-select" data-ty>
        <p>user.signingkey=DEADBEEF</p>
        <p>user.name=Alexander Pushkin</p>
        <p>user.email=pushkeen@altlinux.org</p>
    </span>
</div>