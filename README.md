# Кастомный твиттер

Возможность добавлять, изменять, удалять посты. Посты хранятся в localStoge в виде JSON строки. При клике на пост можно перейти на его страницу. Там есть возможность просмотра полной инормации по посту и возможность редактирования поста, добавлять или удалять комментарии. 



Использовала 
* [Библиотеку компонентов](https://vuetifyjs.com/en)
* [Библиотеку иконок](https://pictogrammers.com/library/mdi/icon)
* [Библиотеку для уведомлений](https://github.com/Maronato/vue-toastification)


Основная страница с постами 

![image](https://github.com/povar0305/custom-twitter/assets/73982948/cf4ef4f7-8845-4877-bdf5-8aaf879a0525)


При добавлении поста появляется уведомление. Для уведомлений использовала [библиотеку](https://github.com/Maronato/vue-toastification)

![image](https://github.com/povar0305/custom-twitter/assets/73982948/9acbbc42-47e3-41fa-8a66-9d5a07c5b64e)


Отображение постов с комментариями 

![image](https://github.com/povar0305/custom-twitter/assets/73982948/23b14ce8-23e9-4bdd-b5c7-c4b96e8dec62)


Удаление постов 

![image](https://github.com/povar0305/custom-twitter/assets/73982948/be243054-53c6-40d2-8c55-6f158a50475a)


Страница отдельного поста 

![image](https://github.com/povar0305/custom-twitter/assets/73982948/7c4528a8-4c54-4034-a5ca-027e8a86130d)


Редактирование поста 

![image](https://github.com/povar0305/custom-twitter/assets/73982948/f3fadeee-cb51-4558-a6d5-81893ddb1c5d)
![image](https://github.com/povar0305/custom-twitter/assets/73982948/db551e9b-039c-4047-b499-fb80d3acf2f2)
![image](https://github.com/povar0305/custom-twitter/assets/73982948/44eeeeeb-3adb-4c85-8799-fbc616d772fb)


Добавление комментариев 

![image](https://github.com/povar0305/custom-twitter/assets/73982948/51811886-c747-40f7-a0cd-f4627e6943fa)
![image](https://github.com/povar0305/custom-twitter/assets/73982948/5f6ddeec-1982-4632-ab8a-ab1135c8b2bc)


Удаление комментариев

![image](https://github.com/povar0305/custom-twitter/assets/73982948/17bae51b-8e30-465d-b94d-802bf0fc7c36)
![image](https://github.com/povar0305/custom-twitter/assets/73982948/c13ebaf2-1f38-4eda-9a2d-60592d71a984)




## Валидация форм 


### Запись
* заголовок (обязательное поле, максимальная длина 50 символов)
* краткое описание (обязательное поле, максимальная длина 100 символов)
* полное описание (максимальная длина 255 символов)
![image](https://github.com/povar0305/custom-twitter/assets/73982948/b756290d-c537-4824-85c2-581a462bed4b)
![image](https://github.com/povar0305/custom-twitter/assets/73982948/e445753d-9dc1-46dc-bf49-65471e144b30)


### Комментарий
* имя комментатора (обязательное поле, максимальная длина 50 символов)
* email комментатора (проверка на валидность email, максимальная длина 50 символов)
* текст комментария (обязательное поле, максимальная длина 255 символов
![image](https://github.com/povar0305/custom-twitter/assets/73982948/812e8110-fb09-4c5e-8ccd-26b06673e8c3)
![image](https://github.com/povar0305/custom-twitter/assets/73982948/9026cfaa-c99c-45e2-98f1-8ff4b1d1abde)


### Особенности 
* даты хранить в формате YYYY-MM-DD, а при отображении показывать в формате DD.MM.YYYY
* приложение должно корректно отображаться и работать в последних версиях Google Chrome, Firefox, Edge.	


## Настройки

Установка:

```bash
# npm
npm install

```

## Настройки разработки

Поднятие сервера для разработки `http://localhost:3000`:

```bash
# npm
npm run dev

```

## Построение продакшена

```bash
# npm
npm run build

```

Билд проекта
```bash
# npm
npm run preview

```

[Более подробная документация](https://nuxt.com/docs/getting-started/deployment)

