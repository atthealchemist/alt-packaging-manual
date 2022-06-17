## Настройка APT для работы с локальным репозиторием Hasher

Создаём в конфиге репозиториев Hasher файл `apt.list` со следующим содержимым.
<div id="termynal" data-termynal data-ty-title="nano ~/.hasher/repo/x86_64/apt.list" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty>
        <p>rpm file:///ALT/Sisyphus noarch classic</p>
        <p>rpm file:///ALT/Sisyphus x86_64-i586 classic</p>
        <p>rpm file:///ALT/Sisyphus x86_64 classic</p>
    </span>
</div>

Добавляем в `/etc/fstab` запись вида
<div id="termynal" data-termynal data-ty-title="nano /etc/fstab" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty>
        <p>10.88.5.62:/ftppool/all/pub/distributions/ALTLinux      /ALT    nfs     ro,noexec,nolock,nosuid,nodev,hard,intr,rsize=8192,wsize=8192 0 0</p>
    </span>
</div>

И создаём каталог /ALT/ для хранения зеркала репозитория AltLinux у нас на машине
<div id="termynal" data-termynal data-ty-title="bash" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">sudo mkdir -p /ALT/</span>
</div>

После чего добавляем файл `pkgpriorities` со следующим содержанием:
<div id="termynal" data-termynal data-ty-title="nano ~/.hasher/repo/x86_64/pkgpriorities" data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty>
        <p>Important:</p>
        <p>&nbsp;&nbsp;basesystem</p>
        <p>Required:</p>
        <p>&nbsp;&nbsp;apt</p>
        <p>Standard:</p>
        <p>&nbsp;&nbsp;gnome-screensaver</p>
        <p>&nbsp;&nbsp;kernel-doc</p>
        <p>&nbsp;&nbsp;libpam0</p>
        <p>&nbsp;&nbsp;libpam0-devel</p>
        <p>&nbsp;&nbsp;maxima-bin-gcl</p>
        <p>&nbsp;&nbsp;metacity-gnome</p>
        <p>&nbsp;&nbsp;postfix</p>
        <p>&nbsp;&nbsp;python-dev</p>
        <p>&nbsp;&nbsp;python-modules-tkinter</p>
        <p>&nbsp;&nbsp;xscreensaver-hacks</p>
    </span>
</div>

И переходим к следующему шагу.