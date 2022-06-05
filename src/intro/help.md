## Могу ли я помочь тебе с этим мануалом?
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
  - скачай mdBook с [официального сайта](https://github.com/rust-lang/mdBook/releases) и распакуй его в *alt-packaging-manual* (или сразу скопируй в `/usr/bin/`, как сделал я, чтобы запускать отовсюду)
  - запусти `./mdbook serve`
  - после чего перейди на [localhost:3000](http://localhost:3000) в любом браузере.

  Всё, можешь вносить исправления в markdown-файлики, сохранять их и видеть изменения сразу в браузере.

Заранее спасибо за помощь, без тебя было бы труднее! :)
