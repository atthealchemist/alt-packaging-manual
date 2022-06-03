# Глава 1. Установка и настройка всего необходимого мейнтейнеру проекта.

В первую очередь тебе нужно:
- получить доступ к инфраструктуре git.alt
    - создать SSH и GPG ключи
    - завести аккаунт в [AltLinux Wiki](https://altlinux.org)
    - выбрать себе ментора и отправить ему свой публичный SSH ключ
    - оформить заявку на вступление в AltLinux Team

Теперь подробнее остановимся на каждом шаге.

## Создание ключей

Для большей наглядности далее происходящего, представим, что ты - Александр Сергеевич Пушкин, и ты решил присоединиться к команде мейнтейнеров AltLinux. 

### SSH ключ
SSH ключ нужен для предоставления доступа тебе и идентификации твоей работы в инфраструктуре [git.alt]().

Создать его очень просто:
```bash
$ ssh-keygen -t ED25519 -b 4096
```

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
[pushkeen@localhost ~]$ ssh-keygen -t ed25519 -b 4096

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

[pushkeen@localhost ~]$ 
```

### GPG-ключ

Этот ключ - идентификация тебя в репозиториях и почтовых сообщениях, поэтому отнесись к нему с особой внимательностью.

Создаётся просто, одной командой
```bash
$ gpg --gen-key
```

Подробный процесс создания GPG-ключа:
```bash
[pushkeen@localhost ~]$ gpg --gen-key
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

[pushkeen@localhost ~]$ 
```

После чего экспортируй свой новоиспечённый GPG-ключ в файл следующей командой:
```bash
$ gpg --armor --export pushkeen@altlinux.org > ~/gpg-keys/pushkeen_git_alt_gpg_key.pub
```

## Завести аккаунт в AltLinux Wiki

Это необязательный шаг, однако если тебе есть что сказать и ты можешь помочь в пополнении базы знаний по AltLinux - можешь зарегистрироваться по [этой ссылке](https://www.altlinux.org/%D0%A1%D0%BB%D1%83%D0%B6%D0%B5%D0%B1%D0%BD%D0%B0%D1%8F:%D0%97%D0%B0%D0%BF%D1%80%D0%BE%D1%81%D0%B8%D1%82%D1%8C_%D1%83%D1%87%D1%91%D1%82%D0%BD%D1%83%D1%8E_%D0%B7%D0%B0%D0%BF%D0%B8%D1%81%D1%8C)


## Выбрать себе ментора и отправить ему публичный ключ

Для этого тебе скорее всего понадобится войти в [Telegram-чат](http://telegram.me/alt_linux). Однако есть и другие возможности связаться с менторами AltLinux Team, например [IRC](https://www.altlinux.org/IRC-%D0%BA%D0%B0%D0%BD%D0%B0%D0%BB%D1%8B_ALT_Linux) и [mailing-lists]() (списки рассылки).

Для принятия тебя в Team и предоставления тебе доступа к инфраструктуре ментору нужна следующая информация:

- псевдоним (имя пользователя), которые ты сам можешь придумать. Должен начинаться с буквы, содержать только строчные буквы и цифры, быть не короче трёх символов. 

    Псевдоним — это, фактически, твоё второе имя в команде. Так тебя будут называть в глаза и за глаза, по нему на тебя будут ссылаться. Поэтому псевдоним лучше выбирать короткий, запоминающийся и не отягощённый мусором. 

    Допустим, ты выбрал свой псевдоним - ***pushkeen***. Запомни его, теперь он будет тебя связывать с множеством ресурсов сразу, поменять его не так просто, людям память тоже не перепишешь.

- твой будущий желаемый адрес почты, на который будет производиться пересылка всей информации о состоянии пакетов, новых багов и т.д. 

    С учётом выбора твоего псевдонима, твой адрес будет - ***pushkeen@altlinux.org***;

- SSH-ключ (ED25519 или RSA >= 4096bit), который мы с тобой создали раньше. 

    Этот ключ будет использоваться для SSH-доступа на ресурсы Sisyphus (git.alt и другие). Отправляй ментору только публичную часть ключа! (файл с расширением .pub);

- GPG-ключ (RSA >= 4096bit). 

    В ключе должны быть твои настоящие(!) имя и фамилия в формате "Александр Пушкин" и твоего пользовательского идентификатора (aka логина) для всей инфраструктуры вида ***pushkeen@altlinux.org***. Отправляй ментору только публичную часть ключа! 
    
    **Пожалуйста, помни, этот ключ будет использоваться для подписи пакетов и для удостоверения твоей личности в почте! Не присваивай свои заслуги какому-нибудь несуществующему Spyro The Dragon или  Hiroyuki Sawano!**

## Оформление заявки на вступление в AltLinux Team

Чтобы оформить заявку, тебе нужно создать баг здесь - [Bugzilla](https://bugzilla.altlinux.org/enter_bug.cgi).

Оформи баг следующим образом:
- В первом списке выбираешь *Team Accounts*, дальше в выпадающем списке под второй красной звёздочкой сверху выбираешь *Join*
- В описании бага (большом текстовом поле) вводишь следующее:
    - псевдоним (имя пользователя) нового участника;
    - адрес пересылки почты;
    - имя своего ментора (с его согласия, конечно же);
    - несколько слов о том, чем ты хочешь заниматься в ALT Linux Team («собрать для начала такой-то пакет, а потом, если получится, ещё пакеты из такой-то области», «просто помочь со сборкой чего-нибудь», «научиться собирать пакеты», «у вас тут хотелка висит» и т. п.);
- добавляй e-mail ментора в поле CC («Подписка»), чтобы он смог должным образом подтвердить своё менторство;
- Нажимай на кнопку "Создать баг" ("Submit bug" в английской версии), после чего смело добавляй во вложения следующие файлы (по файлу во вложение):
    - публичный SSH-ключ (тот самый `~/ssh-keys/pushkeen_git_alt_ssh_key.pub`)
    - публичный GPG-ключ (тот самый `~/gpg-keys/pushkeen_git_alt_gpg_key.pub`)

Когда тебе придёт оповещение от ментора о том, что заявка принята, поздравляю, ты справился с первым этапом! Теперь тебя ждёт увлекательная дорога к сборке своего первого пакета, полная проб и ошибок, результаты которой навсегда останутся в памяти сообщества AltLinux Team.

## Установка всего необходимого

Для начала нам надо установить все пакеты, с помощью которых мы будем производить конфигурацию и сборку других пакетов. Вот такая вот логика.
```bash
$ sudo apt-get install build-environment gear git
```

### Конфигурация Git

После чего конфигурируем git для подписания своих коммитов.
```bash
$ git config --global user.name 'Alexander Pushkin'
$ git config --global user.email 'pushkeen@altlinux.org'
$ git config --global user.signingkey 'DEADBEEF'
```

Уже предвосхищаю твой вопрос - "где посмотреть `user.signingkey`"? 
Всё просто, следующей командой:
```bash
$ gpg --list-keys | grep -B 1 'Alexander Pushkin'
```

Ну и как всегда, наглядное представление того, как это будет выглядеть:
```bash
[pushkeen@localhost ~]$ gpg --list-keys | grep -B 1 'Alexander Pushkin'
pub   4096R/DEADBEEF 2022-06-03  # <-- DEADBEEF - наш подписной ключик
uid                  Alexander Pushkin (pushkeen gpg key) <pushkeen@altlinux.org>
```

В конечном итоге твой `git config --global --list` должен выглядеть вот так:
```bash
[pushkeen@localhost ~]$ git config --global --list
user.signingkey=DEADBEEF
user.name=Alexander Pushkin
user.email=pushkeen@altlinux.org

[pushkeen@localhost ~]$ 
```

### Конфигурация `.rpmmacros`

Создай файл `.rpmmacros` в домашнем каталоге следующей командой:

```bash
$ nano ~/.rpmmacros
```

И добавь в него следующие строчки:
```bash
%packager Alexander Pushkin <pushkeen@altlinux.org>
%_gpg_name BFFDEB200AAC53999992BA3D10EEDE37DEADBEEF
```

После чего нажимай комбинацию клавиш `Ctrl+O` (да, это английская О, не ноль) для сохранения файла.

### Конфигурация Hasher

Для того, чтобы пользоваться Hasher, надо добавить в него нашего пользователя - *pushkeen*.
```bash
[root@localhost /]# hasher-useradd pushkeen
Adding user pushkeen to group pushkeen_a
Adding user pushkeen to group pushkeen_b
Adding user pushkeen to group hashman
```

Не забудь выйти из под рута командой `exit`.

Для простейшей конфигурации Hasher создай каталог `~/.hasher`:
```bash
mkdir -p ~/.hasher
```
И создай внутри него файл `~/.hasher/config` командой
```bash
$ nano ~/.hasher/config
```
Добавь в него следующие строчки:
```bash
USER=pushkeen
workdir="/tmp/.private/pushkeen/"
target=x86_64
packager="`rpm --eval %packager`"
apt_config="$HOME/.hasher/apt.conf"
mount=/dev/pts,/proc
```
После чего нажимай комбинацию клавиш `Ctrl+O` (да, это английская О, не ноль) для сохранения файла.

Если ты хочешь собирать пакеты для 32-битной архитектуры, меняй `target=x86_64` в строчках выше на `target=i586`.
Полный список поддерживаемых архитектур можно найти [здесь]()

