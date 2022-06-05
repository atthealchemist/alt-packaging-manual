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

<!-- Используемые обозначения -->
{{#include definitions.md}}

<!-- Могу ли я помочь тебе с этим мануалом? -->
{{#include help.md}}