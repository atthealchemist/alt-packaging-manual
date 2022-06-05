# Конфигурация git

Сначала конфигурируем git для подписания своих коммитов.

<div id="termynal" data-termynal  data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">git config --global user.name 'Alexander Pushkin'</span>
    <span data-ty="input" data-ty-prompt="[~] $">$ git config --global user.email 'pushkeen@altlinux.org'</span>
    <span data-ty="input" data-ty-prompt="[~] $">git config --global user.signingkey 'DEADBEEF'</span>
</div>

Уже предвосхищаю твой вопрос - "где посмотреть `user.signingkey`"? 
Всё просто, следующей командой:
```bash
$ gpg --list-keys | grep -B 1 'Alexander Pushkin'
```

Ну и как всегда, наглядное представление того, как это будет выглядеть:
```bash
[pushkeen@localhost ~]$ gpg --list-keys | grep -B 1 'Alexander Pushkin'
pub   4096R/DEADBEEF 2022-06-03  # <-- DEADBEEF - наш подписной ключик
uid                  Alexander Pushkin (pushkeen gpg key) <pushkeen@altlinux.org>
```

В конечном итоге твой `git config --global --list` должен выглядеть вот так:
```bash
[pushkeen@localhost ~]$ git config --global --list
user.signingkey=DEADBEEF
user.name=Alexander Pushkin
user.email=pushkeen@altlinux.org

[pushkeen@localhost ~]$ 
```