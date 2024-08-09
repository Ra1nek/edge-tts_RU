# edge-tts

`edge-tts` — это модуль Python, который позволяет использовать онлайн-сервис преобразования текста в речь Microsoft Edge прямо в вашем коде Python или с помощью команд `edge-tts` или `edge-playback`.

## Установка

Для установки выполните следующую команду:

    $ pip install edge-tts

Если вы хотите использовать только команды `edge-tts` и `edge-playback`, лучше установить через `pipx`:

    $ pipx install edge-tts

## Использование

### Основное использование

Если вы хотите использовать команду `edge-tts`, вы можете просто запустить её с помощью следующей команды:

    $ edge-tts --text "Hello, world!" --write-media hello.mp3 --write-subtitles hello.vtt

Если вы хотите сразу воспроизвести с субтитрами, можно использовать команду `edge-playback`:

    $ edge-playback --text "Hello, world!"

Обратите внимание, что для этого требуется установка командного проигрывателя `mpv`.

Все команды `edge-tts` также работают в `edge-playback`.

### Смена голоса

Если вы хотите изменить язык речи или, в общем, голос, вам нужно сначала проверить доступные голоса с опцией `--list-voices`:

    $ edge-tts --list-voices
    Name: Microsoft Server Speech Text to Speech Voice (af-ZA, AdriNeural)
    ShortName: af-ZA-AdriNeural
    Gender: Female
    Locale: af-ZA

    Name: Microsoft Server Speech Text to Speech Voice (am-ET, MekdesNeural)
    ShortName: am-ET-MekdesNeural
    Gender: Female
    Locale: am-ET

    Name: Microsoft Server Speech Text to Speech Voice (ar-EG, SalmaNeural)
    ShortName: ar-EG-SalmaNeural
    Gender: Female
    Locale: ar-EG

    Name: Microsoft Server Speech Text to Speech Voice (ar-SA, ZariyahNeural)
    ShortName: ar-SA-ZariyahNeural
    Gender: Female
    Locale: ar-SA

    ...

    $ edge-tts --voice ar-EG-SalmaNeural --text "مرحبا كيف حالك؟" --write-media hello_in_arabic.mp3 --write-subtitles hello_in_arabic.vtt

### Пользовательский SSML

Поддержка пользовательского SSML была удалена с версии 5.0.0, так как Microsoft предприняла меры по предотвращению её работы. Вы больше не можете использовать пользовательский SSML.

### Изменение скорости, громкости и высоты тона

Возможно внести небольшие изменения в сгенерированную речь..

    $ edge-tts --rate=-50% --text "Hello, world!" --write-media hello_with_rate_halved.mp3 --write-subtitles hello_with_rate_halved.vtt
    $ edge-tts --volume=-50% --text "Hello, world!" --write-media hello_with_volume_halved.mp3 --write-subtitles hello_with_volume_halved.vtt
    $ edge-tts --pitch=-50Hz --text "Hello, world!" --write-media hello_with_pitch_halved.mp3 --write-subtitles hello_with_pitch_halved.vtt

Кроме того, необходимо использовать `--rate=-50%` вместо `--rate -50%` (обратите внимание на наличие знака равенства), иначе `-50%` будет интерпретировано как очередной аргумент.

### Примечание о команде edge-playback

`edge-playback` — это всего лишь обёртка над `edge-tts`, которая воспроизводит сгенерированную речь. Она принимает те же аргументы, что и опция `edge-tts`.

## Модуль Python

Вы можете использовать модуль `edge-tts` напрямую из Python. Список примеров для применения:

* https://github.com/rany2/edge-tts/tree/master/examples
* https://github.com/rany2/edge-tts/blob/master/src/edge_tts/util.py
* https://github.com/hasscc/hass-edge-tts/blob/main/custom_components/edge_tts/tts.py
