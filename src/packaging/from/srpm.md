## Из исходников уже кем-то собранных пакетов в других пакетных репозиториях (Fedora, Debian, etc.)

На самом деле всё проще, чем кажется.

### Если у нас есть готовый SRPM пакет
Допустим мы нашли уже готовый srpm пакет `mitmproxy` в репозиториях Mageia Linux.
Выкачиваем его оттуда и открываем консоль в том месте, куда мы его скачали.

Затем берём утилиту `gear-srpmimport` и натравливаем её на наш .src.rpm файлик.

<div id="termynal" data-termynal  data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">gear-srpmimport mitmproxy-8.0.0-mga9.src.rpm</span>
    <span class="no-select" data-ty>Extracting to ./mitmproxy... ok!</span>
</div>

Вносим изменения в .spec-файл, предварительно его почистив от всего ненужного

<div id="termynal" data-termynal  data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">cleanup_spec mitmproxy.spec</span>
</div>

После чего уже непосредственно запускаем пробную сборку gear:
```bash
gear 
    \ -v
    \ --hasher
    \ --
    \ hsh
    \ --lazy
```

Возникают ошибки - правим, запускаем повторную сборку в том же окружении Hasher:
```bash
gear 
    \ -v
    \ --hasher
    \ --
    \ hsh
    \ --rebuild
```

Повторять процедуру до полной сборки пакета без ошибок.

Когда мы собрали его, запускаем 
```bash
buildreq mitmproxy.spec
```

И ждём, пока он подтянет все build requirements.
После чего добавляем изменённый спек в git командой
```bash
git commit --amend -a
```

### Debian/Ubuntu way
В Debian-based дистрибутивах исходники пакетов просто пакуются в тарболлы вида `<package_name>.orig.tar.gz`.

Метаданные хранятся в `<package_name>.dsc`
Дополнительные скрипты для сборки конкретного пакета, патчи и прочее лежат в `<package_name>.debian.tar.xz`.