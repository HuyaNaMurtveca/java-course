# Bookmarks Manager :paperclip:

## Условие

Създайте приложение за удобно съхранение и организиране на линкове (*bookmarks*).

### Сървър

Предоставя следните функционалности на клиента:
- регистриране и вход с потребителско име и парола
- добавяне на нови bookmarks
- премахване на bookmarks
- групиране на bookmarks
- търсене на bookmarks по заглавие или ключова дума

:bulb: Bookmark-ите на потребителите трябва да се съхраняват във файлове на сървъра.

:bulb: Всеки добавен bookmark трябва да има *заглавие*. То трябва да отговаря на съдържанието на **<title\>** таг-а от `html`-а на страницата.

:bulb: При добавяне на нов bookmark, сървърът трябва да `extract`-не ключовите думи от страницата, за да могат потребителите да търсят по тях.

- Ключовите думи са най-използваните думи в страницата. Погрижете се предварително да премахнете пунктуационни знаци, специални символи, `stopwords` и т.н.
- Опитайте се да сведете думите до техните корени, използвайки някой [`stemming`](https://en.wikipedia.org/wiki/Stemming) алгоритъм. Най-простият от тях, който можете да използвате, е `Suffix-stripping algorithm`:
> - if the word ends in 'ed', remove the 'ed'
> - if the word ends in 'ing', remove the 'ing'
> - if the word ends in 'ly', remove the 'ly'

- За лесно `parse`-ване на `html`, може да използвате библиотеката [JSoup](https://jsoup.org/).

### Клиент

Клиентът трябва да има `command line interface` със следните команди:


#### Регистриране
```bash
register <username> <password>
```
Регистрира нов потребител в приложението с име и парола

#### Вход
```bash
login <username> <password>
```

#### Създаване на нова група за съхранение на bookmarks
```bash
new-group <group-name>
```

#### Добавяне на нов bookmark в група
```bash
add-to <group-name> <bookmark> {--shorten}
```
Добавя bookmark в конкретна група. Aко опцията `--shorten` е налична, сървърът трябва да съкрати оригиналния bookmark, използвайки API-то на [Bitly](https://dev.bitly.com/api-reference), документирано [тук](https://dev.bitly.com). 

#### Премахване на bookmark от група
```bash
remove-from <group-name> <bookmark>
```

#### List-ване на всички bookmarks
```bash
list - извежда списък с всички линкове на потребителя
```

#### List-ване на всички bookmarks от група
```bash
list --group-name <group-name> - извежда списък с всички линкове от дадената група
```

#### Търсене на bookmarks по тагове
```bash
search --tags <tag> [<tag> ...]
```
#### Търсене на bookmarks по заглавие
```bash
search --title <title> - връща всички линкове, в чиито заглавия се среща <title>
```

#### Изчистване на невалидни линкове
```bash
cleanup - премахва всички bookmarks, чиито линкове вече не са валидни (т.е при /GET на bookmark-a се връща статус код 404 Not Found)
```

#### Добавяне на bookmarks от Chrome
```bash
import-from-chrome - добавя всички bookmarks от Google Chrome
```

`Google Chrome` съхранява вашите `bookmarks` на файловата система в `json` формат. Файлът с `bookmarks` се намира в различни директории в зависимост от операционната система:
- **Windows** - `AppData\Local\Google\Chrome\User Data\Default`
- **Linux** - `~/.config/google-chrome/Default/`
- **MacOS** - `/Users/<Your UserName>/Library/Application\ Support/Google/Chrome`

## Submission

Качете `.zip` архив на познатите папки `src`, `test` и `resources` (опционално, ако имате допълнителни файлове, които не са .java) в sapera.org.
Там няма да има автоматизирани тестове.
Проектът ви трябва да е качен в грейдъра не по-късно от 18:00 в деня преди датата на защитата.

Успех!