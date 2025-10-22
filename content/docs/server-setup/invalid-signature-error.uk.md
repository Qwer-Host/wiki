---
title: "Помилка Invalid signature for profile public key — як виправити?"
description: "Рішення помилки Invalid signature for profile public key при підключенні до сервера Minecraft"
weight: 28
---

## Опис проблеми

Якщо ви стикаєтеся з помилкою при спробі підключення до сервера:

```
Invalid signature for profile public key.
Try restarting your game.
agj$a: Missing profile public key.
This server requires secure profiles.
```

Це пов'язано з перевіркою безпечних профілів у нових версіях Minecraft. Нижче описано рішення!

## Рішення

Вам необхідно змінити налаштування у файлі конфігурації сервера `server.properties`.

### Покрокова інструкція

1. Відкрийте панель керування panel.qwer-host.xyz і виберіть свій сервер.
2. Перейдіть у вкладку **"Файли"** (Files) і знайдіть файл `server.properties`.
3. Відкрийте файл для редагування.
4. Знайдіть рядок:
   ```properties
   enforce-secure-profile=true
   ```
5. Змініть значення на `false`:
   ```properties
   enforce-secure-profile=false
   ```
6. Збережіть файл.
7. Перезавантажте сервер.

Після перезавантаження спробуйте увійти знову — помилка має зникнути.
