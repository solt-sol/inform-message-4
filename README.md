# inform-message-4
Измененная функция once_done:

```
async def once_done(sink: discord.sinks, channel: discord.TextChannel, *args):
    recorded_users = [
        f"<@{user_id}>"
        for user_id, audio in sink.audio_data.items()
    ]
    text = "Сними коментарий через 2 строчки вниз"
    await sink.vc.disconnect() 
    files = [(audio.file, f"{user_id}.{sink.encoding}") for user_id, audio in sink.audio_data.items()]
    print(files)
    a = files[0]
    files.append(discord.File(a[0], a[1]))
    text = client.speech(a[0], {'Content-Type': 'audio/wav'})
    print(text)
    #await channel.send(text, files=files)  
```

Вывод:

```
Bot - Online..
Старт в канале '1'
Запись начата в канале '1'
Стоп в канале '1'
Стоп записи в канале '1'
[(<_io.BytesIO object at 0x00000127B462A660>, '791309916266692619.wav')]
{'entities': {}, 'intents': [], 'text': '', 'traits': {}}
```
