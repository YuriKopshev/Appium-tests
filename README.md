# Домашняя работа к занятию «2.4. Appium. Кроссплатформенная мобильная автоматизация тестирования»


---

## Задача 1. Настройка окружения для работы с Appium

1. Установлен [Node.js](https://nodejs.org/en/download/).
2. Через терминал установил **appium** и **appium-Doctor**, используя менеджер пакетов npm.
```bash
npm install -g appium
npm install -g appium-doctor
```
3. Запустил appium-doctor, выполнив в терминале команду, и проверил, каких компонентов не хватает для автоматизации Android.
```bash
appium-doctor --android
```

4. Убедился, что в блоке **necessary** возле всех пунктов стоят зелёные галочки. 

5. Установил последнюю версию [Appium Inspector](https://github.com/appium/appium-inspector/releases).

6. Запустил в терминале appium-сервер.
```bash
appium
```


7. Запустил эмулятор.

8. Собрал [приложение из лекции 2.2](https://github.com/netology-code/mqa-homeworks/tree/main/2.2%20UI%20Automator/sample) и запомнил путь к apk-файлу.

9. Подключился к устройству через Appium Inspector. В значении параметра *app* необходимо указать путь к apk-файлу.
```json
{
  "platformName": "Android",
  "deviceName": "Some name",
  "app": "<путь_к_apk_файлу>"
}

```

Или вот так(предварительно установив приложение через apk файл на эмулятор!!!):

```json
{
  "platformName": "Android",
  "appium:deviceName": "Samsung",
  "appium:appPackage": "ru.netology.testing.uiautomator",
  "appium:appActivity": "ru.netology.testing.uiautomator.MainActivity"
}

```


## Задача 2. Автоматизация тестирования на Appium

Порядок запуска тестов:

1. Включаем эмулятор с установленным [приложением](https://github.com/netology-code/mqa-homeworks/tree/main/2.2%20UI%20Automator/sample) 
2. Запускаем appium server
```bash
appium
```
3. Проверяем что устройство видит ПК:
```bash
adb devices
```
4. Вписываем имя устройства или эмулятора в код теста:

   `desiredCapabilities.setCapability(MobileCapabilityType.DEVICE_NAME, "Pixel 6 API 30");`

Где это можно посмотреть:
   Имя устройства (найти для реального устройства можно в “Настройки” — “О телефоне”, а для виртуального “Tools” — “AVD Manager” — поле “Name”)

5. Запускаем тесты