# Кастомный твиттер

Возможность добавлять, изменять, удалять посты. Посты хранятся в localStoge в виде JSON строки. При клике на пост можно перейти на его страницу. Там есть возможность просмотра полной инормации по посту и возможность редактирования поста, добавлять или удалять комментарии. 



Использовала 
* [Библиотеку компонентов](https://vuetifyjs.com/en)
* [Библиотеку иконок](https://pictogrammers.com/library/mdi/icon)
* [Библиотеку для уведомлений](https://github.com/Maronato/vue-toastification)


Основная страница с постами 

![image](https://github.com/povar0305/custom-twitter/assets/73982948/cf4ef4f7-8845-4877-bdf5-8aaf879a0525)


При добавлении поста появляется уведомление. Для уведомлений использовала [библиотеку](https://github.com/Maronato/vue-toastification)

![image](https://github.com/povar0305/custom-twitter/assets/73982948/a70a4d3b-0dfb-4588-bd7e-cdd16f8fd7e2)


Отображение постов с комментариями 

![image](https://github.com/povar0305/custom-twitter/assets/73982948/d60e6664-52e3-4b2c-9016-eb01ef9c4a52)


Удаление постов 

![image](https://github.com/povar0305/custom-twitter/assets/73982948/2b16de9f-00c7-492c-935b-f16392a0acf4)

Редактирование поста 

![image](https://github.com/povar0305/custom-twitter/assets/73982948/1f6f1751-528e-49c9-8582-b39fc0bc6155)
![image](https://github.com/povar0305/custom-twitter/assets/73982948/4f0f1e52-5ab6-4937-8f74-3644c387a8cc)



Страница отдельного поста 

![image](https://github.com/povar0305/custom-twitter/assets/73982948/89c9c493-a498-460f-ba0e-e709e8931e12)


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

