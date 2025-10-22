---
title: "Ошибка Invalid signature for profile public key — как исправить?"
description: "Решение ошибки Invalid signature for profile public key при подключении к серверу Minecraft"
weight: 28
---

## Описание проблемы

Если вы сталкиваетесь с ошибкой при попытке подключения к серверу:

```
Invalid signature for profile public key.
Try restarting your game.
agj$a: Missing profile public key.
This server requires secure profiles.
```

Это связано с проверкой безопасных профилей в новых версиях Minecraft. Ниже описано решение!

## Решение

Вам необходимо изменить настройку в файле конфигурации сервера `server.properties`.

### Пошаговая инструкция

1. Откройте панель управления panel.qwer-host.xyz и выберите свой сервер.
2. Перейдите во вкладку **"Файлы"** (Files) и найдите файл `server.properties`.
3. Откройте файл для редактирования.
4. Найдите строку:
   ```properties
   enforce-secure-profile=true
   ```
5. Измените значение на `false`:
   ```properties
   enforce-secure-profile=false
   ```
6. Сохраните файл.
7. Перезагрузите сервер.

После перезагрузки попробуйте войти снова — ошибка должна исчезнуть.

