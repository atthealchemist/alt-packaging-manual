Для публикации пакета в репозиторий Sisyphus нам нужно создать репозиторий нашего пакета в репозитории Sisyphus
следующей командой
<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">ssh git.alt init-db packages/mitmproxy</span>
    <span class="no-select" data-ty>Successfully initialized mitmproxy repo at git.alt:pushkeen/packages/mitmproxy.git</span>
</div>

Создаём тег с версией пакета, который мы публикуем
<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">gear-create-tag -u "Alexander Pushkin &lt;pushkeen@altlinux.org&gt;"</span>
</div>

После чего делаем 
<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">git push --all --tags git.alt:packages/mitmproxy</span>
    <span class="no-select" data-ty>Pushing sources with tags @ git.alt:packages/mitmproxy... SUCCESS!</span>
</div>
для загрузки всего пакета в репозиторий Sisyphus.

Создаём в сборочнице задание на сборку пакета mitmproxy с версией 8.0.0-alt1

<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">ssh git.alt build mitmproxy 8.0.0-alt1</span>
    <span class="no-select" data-ty>Created task #101 of mitmproxy package build by pushkeen@</span>
</div>

После чего статус задачи в сборочнице можно посмотреть командой

<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">ssh git.alt task ls</span>
    <span class="no-select" data-ty>Task #101 (mitmproxy) status: PENDING</span>
</div>

Когда на почту придёт уведомление об успешной (или неудачной) сборке - поздравляю. Мы наконец-то дошли до конца и научились сами паковать приложения в пакеты!