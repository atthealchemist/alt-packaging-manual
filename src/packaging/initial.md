## С чего начинается пакет?

Каждый пакет начинается с инициализации в нём пустого git репозитория. Или "реинициализации" существующего.

Реинициализация, если можно так выразиться, представляет собой удаление старого репозитория и создание нового.
<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">rm -r .git/</span>
    <span data-ty="input" data-ty-prompt="[~] $">git init</span>
    <span class="no-select" data-ty>Initialized empty repository @ ./mitmproxy</span>
</div>

После чего создаём два файла, которые собственно и отличают наш пакет от простых исходников.
- `.gear/rules` - файл с правилами для сборки этого пакета Hasher'ом.
- `{PACKAGE_NAME}.spec` - описание пакета.

<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">mkdir -p .gear/ && touch .gear/rules</span>
    <span data-ty="input" data-ty-prompt="[~] $">touch {PACKAGE_NAME}.spec</span>
</div>

О них дальше и пойдёт речь.

### Файл `.gear/rules` - правила Hasher для сборки конкретного пакета

Этот файл (плюс несколько вспомогательных) описывают правила сборки содержимого git-репозитория в пакет формата `pkg.tar` (source tarball) или `src.rpm` (srpm). `pkg.tar` (или в простонародье "тарболл") - это основанный на tar формат для хранения пакета с исходным кодом, аналогичный src.rpm, но не требующий запуска `rpmbuild` для создания. Hasher умеет собирать пакеты в формате `pkg.tar`.

В этом файле описаны правила для Hasher, а именно:
- откуда и что она будет собирать
- куда она запишет готовый пакет
- ... (дополнить)

В простых случаях этот файл обычно выглядит так:

```bash
[pushkeen@localhost mitmproxy-package]$ cat .gear/rules
tar.gz: targetTag:mitmproxy-src
```
<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">cat .gear/rules</span>
    <span class="no-select" data-ty>tar.gz: targetTag:mitmproxy-src</span>
</div>

В этой единственной строчке мы указываем:
- что для конкретной версии приложения (targetTag) в пакете (пусть она будет 8.0.0)
- мы берём наши исходники из каталога `mitmproxy-src`
- и мы пакуем их в архив `mitmproxy-src-8.0.0.tar.gz`

### Файл `mitmproxy.spec` - спецификация (от слова Specification - spec) нашего пакета

Заглянем внутрь файла `mitmproxy.spec`.
Что нам важно здесь знать?

```yaml
# Макросом define мы можем создать т.н. переменные, которые сможем
# использовать дальше по всему конкретному spec-файлу
%define program_name mitmproxy

# Название нашего пакета, такое, под каким мы будем устанавливать его из репозиториев
# $ sudo apt-get install mitmproxy
Name: mitmproxy
# Версия нашего пакета
Version: 8.0.0
# Версия сборки нами нашего пакета. Т.е, сколько раз этот пакет собирался и изменялся.
Release: alt1

# Короткое описание пакета
Summary: An interactive TLS-capable intercepting HTTP proxy for penetration testers and software developers. 
# Лицензия пакетируемой нами программы. В данном случае mitmproxy публикуется 
# под MIT лицензией.
License: MIT
# Категория приложений, к которой относится наш пакет
Group: Networking/Other

# Адрес сайта нашей программы
# Здесь может быть так же адрес сайта с документацией программы 
# или адрес репозитория с программой
Url: https://mitmproxy.org/
# Тот, кто собирает пакет с этой программой 
# (мы как раз ранее заводили GPG ключ именно для этого)
Packager: Alexander Pushkin <pushkeen@altlinux.org>
# Архитектура пакета
# Т.к. в данном случае у нас программа написана на Python 3, она по сути является 
# мультиплатформенной и не привязана к какой-то конкретной архитектуре
BuildArch: noarch
# Путь к архиву с исходниками нашего пакета. Из него будет собираться srpm - 
# специальный пакет, содержащий в себе только исходные тексты нашей программы.
Source: %name-%version.tar.gz

# Основные зависимости, требуемые для сборки пакета.
BuildRequires(pre): rpm-build-python3

# Расширенное описание пакета
%description
mitmproxy is an interactive, SSL/TLS-capable intercepting proxy with a console interface for HTTP/1, HTTP/2, and WebSockets.

mitmdump is the command-line version of mitmproxy. Think tcpdump for HTTP.

mitmweb is a web-based interface for mitmproxy.

# Дальше начинается описание сборочных стадий

# Определение стадии подготовки
%prep

# Определение стадии установки
%setup

# Определение стадии сборки
%build

# Вызов макроса для сборки python3 пакета
%python3_build

# Определение стадии установки
%install

# Вызов макроса для установки python3 пакета в систему
%python3_install

# Определение стадии описания файлов, входящих в пакет
%files
%python3_sitelibdir/%program_name/
%python3_sitelibdir/*.egg-info

# Список изменений пакета.
# Ведётся разработчиками, чтобы указывать особенности конкретных сборок.
# Например, если был применён какой-то особый патч или интегрирован дополнительный модуль.
%changelog
* Fri Jun 3 2022 Alexander Pushkin <pushkeen@altlinux.org> 8.0.0-alt1
Initial build
```
