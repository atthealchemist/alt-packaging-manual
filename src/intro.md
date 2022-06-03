# Введение

Начиная делать это руководство, я преследую следующую цель: сделать единый, понятный разработчику/админу/кому угодно, учебник, в современном изложении с учётом всех новшеств на 2022 год.

Причина этому очень проста: начинающему мейнтейнеру достаточно трудно разобраться в куче разрозненных, а порой - устаревших знаний. 
Поэтому я решил просто, доступно и понятно объяснить себе и всем остальным
- что из себя представляет система сборки пакетов в AltLinux
- сравнить её с уже существующими аналогами сборки в других дистрибутивах
- попробовать собрать пакет из исходников `.tar.{gz,bz,xz}`
- попробовать использовать для этого исходники из готовых релиз-веток репозиториев [github.com](https://github.com), [gitlab.com](https://gitlab.com) и других.
- написать своё собственное приложение и так же собрать его в пакет

Этот мануал будет так же выложен в репозиторий, будет обновляться и дополняться по мере его написания.
Каждый может принять участие в его исправлении и дополнении.

По всему мануалу я буду обращаться к читателю на "ты", как бы обращаясь к самому себе и отвечая на собственные вопросы. Надеюсь, тебе будет комфортен такой стиль повествования :)

## Используемые обозначения

Я буду везде стараться показывать процесс выполнения команд. Сами же команды буду описывать так:

<div id="termynal" data-termynal data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input">whoami</span>
    <span class="no-select" data-ty>pushkeen</span>
</div>

Знак доллара перед началом команды означает, что эта команда должна быть запущена от текущего пользователя. Эти команды ты можешь копировать к себе в консоль. Копируя их, не копируй знак доллара и пробел после него в начале команды! Терминал их не распознает!

Процесс выполнения команд будет выглядеть следующим образом:

<div id="termynal" data-termynal  data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[pushkeen@localhost ~] $">whoami</span>
    <span class="no-select" data-ty>pushkeen</span>
</div>

Если вдруг надо выполнить команду из под суперпользователя (aka рута):
<div id="termynal" data-termynal data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[root@localhost /] #">cat /etc/passwd</span>
</div>

Перед запуском таких команд обязательно надо делать
<div id="termynal" data-termynal data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[pushkeen@localhost ~] $">su -</span>
    <span class="no-select" data-ty>Enter password: ********</span>
    <span data-ty="input" data-ty-prompt="[root@localhost] #"></span>
</div>

## Могу я помочь тебе с этим мануалом?
Конечно, можешь! Всё очень просто!

<div id="termynal" data-termynal data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">git clone https://github.com/atthealchemist/alt-packaging-manual.git</span>
    <span data-ty="progress" data-ty-progressPercent="81"></span>
    <span class="no-select" data-ty>Successfully cloned repo @ ./alt-packaging-manual.git</span>
    <span data-ty="input" data-ty-prompt="[~] $">cd ./alt-packaging-manual/</span>
    <span data-ty="input" data-ty-prompt="[~/alt-packaging-manual] $">git checkout -b intro-add-section-credits</span>
    <span class="no-select" data-ty>{...Внёс изменения в файлики...}</span>
    <span data-ty="input" data-ty-prompt="[~/alt-packaging-manual] $">git commit -am "Добавил новую секцию: Благодарности в intro.md"</span>
    <span class="no-select" data-ty>Commited 1 file</span>
    <span data-ty="input" data-ty-prompt="[~/alt-packaging-manual] $">git push origin intro-add-section-credits</span>
    <span class="no-select" data-ty>Successfully pushed to branch 'intro-add-section-credits' on origin</span>
</div>

И создай Pull Request (или Merge Request, что в принципе одно и то же) в master.

Необязательно, но если хочется видеть свои изменения в книге в режиме реального времени:
  - скачай mdBook с [официального сайта](https://github.com/rust-lang/mdBook/releases) и распакуй его в *alt-build-manual*
  - запусти `./mdbook serve`
  - после чего перейди на [localhost:3000](http://localhost:3000) в любом браузере.

  Всё, можешь вносить исправления в markdown-файлики, сохранять их и видеть изменения сразу в браузере.

 

Заранее спасибо за помощь, без тебя было бы труднее! :)
