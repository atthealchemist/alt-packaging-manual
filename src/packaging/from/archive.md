## Из архивов исходников (.tar.gz, .zip...)

Самый простой способ. В зависимости от формата архива, распаковываем его
- для tar.gz - `tar xzvpf {SOURCES_DIR}.tar.gz`
- для zip - `unzip -x {SOURCES_DIR}.zip`

После чего имя папки с исходниками ({SOURCES_DIR}) устанавливаем в `.gear/rules`
<div id="termynal" data-termynal data-ty-title="nano .gear/rules" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty>
        <p>tar.gz: targetTag:{SOURCES_DIR}</p>
    </span>
</div>
