## Из архивов исходников (.tar.gz, .zip...)

Самый простой способ. В зависимости от формата архива, распаковываем его
- для tar.gz - `tar xzvpf <sources_dir>.tar.gz`
- для zip - `unzip -x <sources_dir>.zip`

После чего имя папки с исходниками устанавливаем в `.gear/rules`
```
tar.gz: targetTag:<sources_dir>
```
