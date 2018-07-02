﻿## Установка системы виртуализации `VirtualBox`

`VirtualBox` - это одна из самых популярных систем виртуализации, позволяющая создавать внутри одного компьютера (хоста)
несколько вложенных копьютеров (гостьевых операционных систем). Например, вы работаете на компьютере на котором утсановлена
операционная система `MS Windows`, но вам нужно иметь возможность одновременно (не перезагружая свой компьютер) работать,
например, с Linux или другой версией `MS Windows`. Для этого и используются системы виртуализации.

С недавних пор проект принадлежит компании `Oracle` и является одной из ведущих систем виртуализации на рынке.

1. Получить дистрибутив `VirtualBox` можно на официальном [сайте](https://www.virtualbox.org/) проекта. Скачивайте версию
соответствующую вашей основной операционной системе (не гостевой, гостевые могут быть любыми). 

2. **Важно!** Для того чтобы `VirtualBox` работал правильно, необходимо в BIOS вашего компьютера включить поддержку виртуализации.
   По умолчанию, большинство производителей копьютеров отключают эти опции, хотя их включение не несёт никаких отрицательных эффектов,
   даже если эти возможности не используются.
   Т.к. у разных копьютеров BIOS может быть организован очень по разному, то здесь трудно дать точные рекомендации по тому, как попасть в
   программу настройки BIOS и где там искать эти настройки относящиеся к виртуализации.
   Обычно в саму программу BIOS попадают нажимая определённую комбинацию клавишь на самом начальном этапе загрузки компоютера.
   У разных производителей свои сочетания клавишь. Обычно на экране на несколько секунд выводится инфа о том как попасть в BIOS. Ну или можно
   погуглить по названию своего ноута/производителя и слову `BIOS`. После того как попали в программу настройки BIOS нужно прошерстить все
   настройки ища те, в подписи к которым будет, в той или иной форме, присутствовать слово `virtual`.
   
   Включить виртуализацию в BIOS можно и после установки `VirualBox`а. Часто признаком того, что виртуализация не включена является то,
   что в `VirtualBox` не получается выбрать в качестве гостевой 64 разрядную операционную систему.

Использовать `VirualBox` непостредственно не очень удобно. Для этого гораздо проще использовать [`vagrant`](../vagrant/README.md).
Все настройки так-жу будут осуществляться через `vagrant`, т.ч. никаких дополнительных действий по настройке непосредственно `VirtualBox`
выполнять не надо, если вы будете использовать `vagrant`.

Обычно установка `VirtualBox` на `MS Windows` не вызывает трудностей (кроме упомянутого выше включения поддержки виртуализации в `BIOS`).

