## Установка системы управления виртуализацией `vagrant`

[`Vagrant`](https://www.vagrantup.com) является удобной оболочкой по управлению виртуальными машинами.
В качестве бэкэнда может использовать самые разные системы виртуализации в том числе и [`VirualBox`](../virtualbox/README.md).
`Vagrant` позовляет легко создавать/удалять, запускать/останавливать/сохранять виртуальные машины с гостевыми опреационными
системами с возможностью создавать их из огромного количества уже подготовленных образов содержащих как образы общего назначения,
например, чистые дистрибутивы различных операционных систем, так и специализированные образы содержацие операционные сисемы
в которые установлен и сконфигурирован определённый набор софта для решения конкретных задач. Например, можно скачать вируальный
образ с Ubuntu Linux в котором уже будет установлен и сконфигурирован `docker`.

1. Установить `vagrant` можно с официального [сайта](https://www.vagrantup.com). На этом сайте есть три кнопки-ссылки.
   * `Get Started`
     Здесь очень доходчиво написано как установить и пользоваться `vagrant`'ом. Дока у `vagrant`'просто отменная
     и подойдет даже для неискушённых пользователей.
   * `Download` Здесь можно перейти к дистрибутивам.
   * `Find Boxes` Это ссылка на сайт с обширным репозиторием образов (`box`'ов).
2. **Важно!** Если вашей основной операционной системой, куда вы устанавливаете `vagrant` является `MS Windows`,
то необходимо что бы у вас в системе была установлена версия `PowerShell` не ниже `5.1`. Все используемые сейчас версии `OS Windows` содержат `PowerShell`,
но только самые последние версии `MS Windows` содержат версию `PowerShell` минимально необходимую `vagrant`'у.
Если не проапгрейдить `PowerShell` до версии `5.1`, то будете получать вот [такую](https://github.com/hashicorp/vagrant/issues/8783) ошибку.
Исталлятор`PowerShell` с самой последней версией подходящей для вашей версии `MS Windows` можно получить [здесь](https://docs.microsoft.com/en-us/powershell/scripting/setup/installing-windows-powershell?view=powershell-6). `PowerShell` можно проапгрейдить и после установки `vagrant`.


### Использование `vagrant`.

Рекумендую прочитать [мануал](https://www.vagrantup.com/intro/getting-started/index.html) (очень хорошо и доходчиво написан).

Все действия нужно выполнять в консоли `Windows`.

*При запуске почти всех команд утилиты `vagrant` необходимо что бы текущим каталогом был каталог с нужным `Vagrantfile`. Это не касается команды `global-status`, которую можно запускать из любого каталога. О том что такое `Vagrantfile` и откуда он берётся чуть ниже.*

Создайте отдельный пустой каталог, в коатором будут находится управляющие файлы для вновь создаваемой виртуальной машины и прейдите внего.
```bat
> mkdir my_first_linux
> cd my_first_linux 
```
Например, мы хотим получить виртуальную машину последней версией `Ubuntu linux`. Сначала инициализируем конфигурационный файл (т.н. `Vagrantfile`):
```bat
> vagrant init ubuntu/xenial64
```
После этого в каталоге появится файл с именем `Vagrantfile`, с настройками по умолчанию. Перед созданием виртуальной машины этот файл можно
подкорректировать под свои нужды, но в большинстве случаев значиния по умолчанию подойдут.

Запускаем виртуальную машину:
```bat
> vagrant up
```
Сначала образ будет доволно продолжительное время закачиваться из общего репозитория `vagrant`'а (следующие запуски будут происходить быстрее,
т.к. нужный образ уже будет на вашей машине). Затем закаченный образ (в терминах `vagrant` образ называетися `box`) будет использован для запуска новой виртуальной машины.
На консоль набросает довольно много сообщений. Потом управление вернётся в консоль.

Если всё прошло хорошо, то вы имеете на своей машине запущенный экземпляр гостевой ОС (в данном случае `Ubuntu linux`). Посмотреть список запущенных
гостевых хостов (`box`'ов) можно воспользовавшись такой коммандной:
```bat
> vagrant global-status
```

Всегда можно получить доходчивую справку по ключам и командам утилиты:
```bat
> vagrant --help
Usage: vagrant [options] <command> [<args>]

    -v, --version                    Print the version and exit.
    -h, --help                       Print this help.

Common commands:
     box             manages boxes: installation, removal, etc.
     destroy         stops and deletes all traces of the vagrant machine
     global-status   outputs status Vagrant environments for this user
     halt            stops the vagrant machine
     help            shows the help for a subcommand
     init            initializes a new Vagrant environment by creating a Vagrantfile
     login           log in to HashiCorp's Vagrant Cloud
     package         packages a running vagrant environment into a box
     plugin          manages plugins: install, uninstall, update, etc.
     port            displays information about guest port mappings
     powershell      connects to machine via powershell remoting
     provision       provisions the vagrant machine
     push            deploys code in this environment to a configured destination
     rdp             connects to machine via RDP
     reload          restarts vagrant machine, loads new Vagrantfile configuration
     resume          resume a suspended vagrant machine
     snapshot        manages snapshots: saving, restoring, etc.
     ssh             connects to machine via SSH
     ssh-config      outputs OpenSSH valid configuration to connect to the machine
     status          outputs status of the vagrant machine
     suspend         suspends the machine
     up              starts and provisions the vagrant environment
     version         prints current and latest Vagrant version

For help on any individual command run `vagrant COMMAND -h`

Additional subcommands are available, but are either more advanced
or not commonly used. To see all subcommands, run the command `vagrant list-commands`.
```

Дальше настало время залогиниться к вновь созданному гостевому хосту:
```bat
> vagrant ssh
```

После этого вы оказываетесь на консоли гостевой операционной системы. В случае образа `ubuntu/xenial64` вы будете заллогинены как пользователь `vagrant`.
У пользователя будут права выполнять команды от имени администратора (`root`). Например что-бы переключиться на пользователя `root` можно выполнить вот такую команду:
```sh
vagrant$ sudo su - root
root#
```
Теперь можно делать с гостевой системой всё что захочется - вы `root`.

Что-бы выйти из гостевой системы, в коносли можно выполнить комадну `exit`: первый раз вы снова превратитьесь в пользователся `vagrant`, а во второй раз выйдите из системы и снова окажетесь в консоли `Windows`.

Залогиниться к гостевой системе можно несколько раз одновременно. Т.е. можно иметь несколько сессий работы с системой. Для этого надо запустить несколько окон с консолью `Windows` перейти в каждом из них в каталог с нужным `Vagrantfile` и там выполнить команду `vagrant ssh` как описано выше.

Что бы остановить запущенную гостевую систему (что равносильно выключению виртуального компьютера, на котором она запущена) нужно перейти в каталог с `Vagrantfile` и выполнить команду:
```bat
> vagrant halt
```
Можно заставить гостевую машину заснуть и настоящий компьютер:
```bat
> vagrant suspend
```
Что бы запустить остановленную/заснувшую машину нужно вомпользоваться той-же командой, что и при первом старте:
```bar
> vargant up
```
Если какая то виртуальная машина бошьше не нужна, то её можно удалить:
```bar
> vargant destroy
```

*Еще раз упомяну, что при запуске команды `vagrant` необходимо что бы текущим каталогом был каталог с нужным `Vagrantfile`. Это не касается команды `global-status`, которую можно запускать из любого каталога.*