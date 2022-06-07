## Предварительная сборка пакета в Hasher

После того, как мы создали наш пакет, нужно проверить - а работает ли он? А корректно устанавливается? А смогут ли им пользоваться *другие пользователи*?

Для того, чтобы максимально упростить жизнь мэйнтейнерам (и им сочувствующим), была создана утилита `hsh`.
В итоге сборка пакета превратилась в использование всего одной команды:

<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">gear -v --hasher -- hsh --lazy</span>
    <span class="no-select" data-ty>Building package mitmproxy... <span class="danger">FAILED!</span></span>
</div>

Возникают ошибки - правим, запускаем повторную сборку в том же окружении Hasher:
<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">gear -v --hasher -- hsh --rebuild</span>
    <span class="no-select" data-ty>Building package mitmproxy... <span class="success">SUCCESS!</span></span>
</div>

Повторять процедуру до полной сборки пакета без ошибок.

Когда мы собрали его, запускаем 
<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">buildreq mitmproxy.spec</span>
    <span class="no-select" data-ty>Adding next requirements to mitmproxy.spec:</span>
    <span class="no-select" data-ty>+ python3</span>
    <span class="no-select" data-ty>+ python3-module-requests</span>
    <span class="no-select" data-ty>+ python3-module-six</span>
</div>

И ждём, пока он подтянет все требуемые зависимости для сборки и корректной работы пакета.
После чего добавляем изменённый спек в git командой
<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">git commit --amend -a</span>
</div>
