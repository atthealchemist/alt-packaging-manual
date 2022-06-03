# Руководство по сборке пакетов в AltLinux (книга)

Для помощи в написании:

1. Скачай этот репозиторий к себе следующей командой
```bash
$ git clone https://github.com/atthealchemist/alt-build-manual.git
```
и зайди в него
```bash
$ cd ./alt-build-manual/
```
2. Создай новую веточку, например *intro-add-section-credits*
```bash
$ git checkout -b intro-add-section-credits
```

3. Необязательно, но если хочется видеть свои изменения в книге в режиме реального времени:
  - скачай mdBook с [официального сайта](https://github.com/rust-lang/mdBook/releases) и распакуй его в *alt-build-manual*
  - запусти `./mdbook serve`
  - после чего перейди на [localhost:3000](http://localhost:3000) в любом браузере.

  Всё, можешь вносить исправления в markdown-файлики, сохранять их и видеть изменения сразу в браузере.

После того, как внёс изменения, закоммить их
```bash
$ git commit -am "Добавил новую секцию: Благодарности в intro.md"
```
и запушь эту веточку
```bash
$ git push origin intro-add-section-credits
```
 и создай Pull Request (или Merge Request, что в принципе одно и то же) в master. 

Заранее спасибо за помощь, без тебя было бы труднее! :)