## Конфигурация `.rpmmacros`
Создай файл `.rpmmacros` в домашнем каталоге следующей командой:

<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">nano ~/.rpmmacros</span>
</div>

И добавь в него следующие строчки:
<div id="termynal" data-termynal data-ty-title="nano" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty>
        <p>%packager Alexander Pushkin <pushkeen@altlinux.org></p>
        <p>%_gpg_name BFFDEB200AAC53999992BA3D10EEDE37DEADBEEF</p>
    </span>
</div>

После чего нажимай комбинацию клавиш <kbd>Ctrl</kbd>+<kbd>O</kbd> (да, это английская О, не ноль) для сохранения файла.
