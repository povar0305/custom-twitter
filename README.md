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

![image](https://github.com/povar0305/custom-twitter/assets/73982948/140c4f85-8eaa-4d40-a028-a937f31da8c8)


Удаление комментариев

![image](https://github.com/povar0305/custom-twitter/assets/73982948/6cf0974f-e755-4a72-afef-fc0f927ec620)
![image](https://github.com/povar0305/custom-twitter/assets/73982948/9f8cdb1d-3eaa-4d54-9d92-fb4a85494c3c)




## Валидация форм 


### Запись
* заголовок (обязательное поле, максимальная длина 50 символов)
* краткое описание (обязательное поле, максимальная длина 100 символов)
* полное описание (максимальная длина 255 символов)
![image](https://github.com/povar0305/custom-twitter/assets/73982948/a679b481-7742-4c54-8c92-6c4117272ffb)
![image](https://github.com/povar0305/custom-twitter/assets/73982948/2ecef39b-357f-4e85-a7bd-12a6ebaea700)


### Комментарий
* имя комментатора (обязательное поле, максимальная длина 50 символов)
* email комментатора (проверка на валидность email, максимальная длина 50 символов)
* текст комментария (обязательное поле, максимальная длина 255 символов
![image](https://github.com/povar0305/custom-twitter/assets/73982948/6d6c11a9-3baf-4952-8bbe-ff9db4651d01)
![image](https://github.com/povar0305/custom-twitter/assets/73982948/8adb2a8d-5f0f-48e7-91d1-f0c56eddd04c)


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

