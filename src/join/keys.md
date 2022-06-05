## Создание ключей
### SSH ключ
SSH ключ нужен для предоставления доступа тебе и идентификации твоей работы в инфраструктуре [Gitery](https://gitery.altlinux.org) и [Gyle](https://gyle.altlinux.org).

Создать его очень просто:
<div id="termynal" data-termynal  data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">ssh-keygen -t ED25519 -b 4096</span>
</div>

Сейчас я объясню, что это за параметры:
- ключ `-t` отвечает за схему (тип) шифрования. 
В данном случае выбрана схема [ED25519](https://ru.wikipedia.org/wiki/EdDSA#Ed25519).
- ключ `-b` отвечает за размер ключа (в битах). 
То есть за то, насколько взломоустойчивый будет твой ключ. 
*4096* в данном случае более чем достаточно, но можно поставить и больше. 
Стоит учесть, что **не рекомендуется ставить размер меньше 2048**, 
т.к. такие ключи достаточно просто "предугадать" потенциальному злоумышленнику.

Подробный процесс создания ключа:
```bash
[~] $ ssh-keygen -t ed25519 -b 4096

Generating public/private ed25519 key pair.
Enter file in which to save the key (/home/pushkeen/.ssh/id_ed25519):  # можешь нажать Enter или задать свой путь до файла ключа. Например, я хочу сохранить ключ с названием "pushkeen_git_alt_ssh_key" в каталоге ~/ssh-keys/, я введу ~/ssh-keys/pushkeen_git_alt_ssh_key
Enter passphrase (empty for no passphrase):  # здесь ты можешь ввести пароль, который будет всегда спрашиваться при использовании твоего ключа. Enter - не создавать пароль
Enter same passphrase again:  # повтори пароль, который создал на шаге выше
Your identification has been saved in /home/pushkeen/.ssh/id_ed25519  # этот ключ ты никогда никому ни при каких обстоятельствах не передаёшь
Your public key has been saved in /home/pushkeen/.ssh/id_ed25519.pub  # этот ключ ты отправишь ментору, чтобы он смог дать тебе доступ к инфраструктуре git.alt
The key fingerprint is:
SHA256:30e5DDKZtrQpQeABoDAWGjJ3JeoGjee3XudfclkGnYU pushkeen@localhost.localdomain
The key randomart image is:
+---[ED25519 256]--+
|o o O*++..        |
|.G C =E           |
|+. * +.+o.        |
| o * +.*..        |
| . + o +.B        |
| .   o o..        |
|      o ...       |
|       .oo.*      |
|        .=N.      |
+----[SHA256]------+

[~] $ 
```

### GPG-ключ

Этот ключ - идентификация тебя в репозиториях и почтовых сообщениях, поэтому отнесись к нему с особой внимательностью.

Создаётся просто, одной командой
<div id="termynal" data-termynal  data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">gpg --gen-key</span>
</div>


Подробный процесс создания GPG-ключа:
```bash
[~] $ gpg --gen-key
gpg (GnuPG) 1.4.23; Copyright (C) 2015 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Please select what kind of key you want:
   (1) RSA and RSA (default)
   (2) DSA and Elgamal
   (3) DSA (sign only)
   (4) RSA (sign only)
Your selection? 1  # Выбирай значение по умолчанию
RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (2048) 4096  # Всё в точности как с SSH ключом - больше - лучше.
Requested keysize is 4096 bits
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0)  # Как долго будет действителен твой ключ. Ставь 0, чтобы сделать его вечным.
Key does not expire at all
Is this correct? (y/N) y  # Подтверждай свои изменения английской буковкой "y"

You need a user ID to identify your key; the software constructs the user ID
from the Real Name, Comment and Email Address in this form:
    "Heinrich Heine (Der Dichter) <heinrichh@duesseldorf.de>"

Real name: Alexander Pushkin  # Вводи свои реальные имя и фамилию
Email address: pushkeen@altlinux.org  # Вводи свой почтовый адрес в доменной зоне altlinux.org
Comment: pushkeen gpg key  # Можешь оставить комментарий для себя, зачем был создан этот ключ
You selected this USER-ID:
    "Alexander Pushkin (pushkeen gpg key) <pushkeen@altlinux.org>"

Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? o  # Соглашайся с изменениями и создавай ключ
You need a Passphrase to protect your secret key.

Enter passphrase:  # вводи пароль
Repeat passphrase:  # повтори его

We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
+++++
....+++++
We need to generate a lot of random bytes. It is a good idea to perform
some other action (type on the keyboard, move the mouse, utilize the
disks) during the prime generation; this gives the random number
generator a better chance to gain enough entropy.
.+++++
.+++++
gpg: key DEADBEEF marked as ultimately trusted
public and secret key created and signed.

gpg: checking the trustdb
gpg: 3 marginal(s) needed, 1 complete(s) needed, PGP trust model
gpg: depth: 0  valid:   2  signed:   0  trust: 0-, 0q, 0n, 0m, 0f, 2u
pub   4096R/DEADBEEF 2022-06-03
      Key fingerprint = 3FF0 DEAB BEEB 5397 9992  DEAF BEEE DEAD BEEF 0803
uid                  Alexander Pushkin (pushkeen gpg key) <pushkeen@altlinux.org>
sub   4096R/DEADB0AB 2022-06-03

[~] $ 
```

После чего экспортируй свой новоиспечённый GPG-ключ в файл следующей командой:
<div id="termynal" data-termynal  data-ty-typeDelay="40" data-ty-lineDelay="700">
    <span data-ty="input" data-ty-prompt="[~] $">gpg --armor --export pushkeen@altlinux.org > ~/gpg-keys/pushkeen_git_alt_gpg_key.pub</span>
</div>
