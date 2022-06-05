## Структура пакета

Прежде чем пытаться что-то начать собирать, нужно понять структуру пакетов в AltLinux.

Разные разработчики делают разные структуры, но в целом у всех всё выглядит примерно так:
```
.
└── mitmproxy-package
    ├── .git
    ├── .gear
    │   └── *rules
    ├── *mitmproxy.spec
    └── mitmproxy-src  # исходники самой программы, которую ты собираешься опакетить
        ├── CHANGELOG.md
        ├── codecov.yml
        ├── CONTRIBUTING.md
        ├── docs
        ├── examples
        ├── .gitattributes
        ├── .github
        ├── .gitignore
        ├── LICENSE
        ├── MANIFEST.in
        ├── mitmproxy
        ├── README.md
        ├── release
        ├── SECURITY.md
        ├── setup.cfg
        ├── setup.py
        ├── test
        ├── tox.ini
        └── web
```

Звёздочками (*) я обозначил файлы, которые используются Hasher при сборке пакета.