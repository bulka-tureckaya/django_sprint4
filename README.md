# Blogicum

>Blogicum - это блоговая платформа на базе Django, которая позволяет пользователям создавать и публиковать свои собственные блоги, а так же комментировать их. Она предоставляет простой и интуитивно понятный интерфейс для управления записями, категориями и статическими страницами.

## Что было добавлено к предыдущей версии

Вот перечень задач, которые нужно было выполнить:

### • Кастомные страницы для ошибок.
Подключите к проекту и настройте кастомные страницы для ошибок 403 CSRF,

404 и 500. Шаблоны для этих страниц находятся в директории templates/pages/.

### • Работа с пользователями.

  Подключены к проекту пользователи:
  
1. Подключено к проекту пути для работы с пользователями из django.contrib.auth.urls.

2. Переопределены шаблоны для каждой подключённой страницы.

3. Создана страница auth/registration/ с формой для регистрации пользователей.

4. Создана страница пользователя profile/<username>/. На ней должны отображаться:

   a. информация о пользователе (доступна всем посетителям),

   b. публикации пользователя (доступны всем посетителям),

   c. ссылка на страницу редактирования профиля для изменения имени, фамилии, логина и адреса электронной почты (доступна только залогиненному пользователю — хозяину аккаунта),

   d. ссылка на страницу изменения пароля (доступна только залогиненному пользователю — хозяину аккаунта).

Переопределять встроенную модель пользователя не требуется.

### • Пагинация.

Подключена к проекту пагинация и настроен вывод не более 10 публикаций
  
  - на главную страницу,
  
  - на страницу пользователя,
  
  - на страницу категории.

### • Изображения к постам.

Добавил возможность прикреплять изображение к публикациям проекта. Если изображение добавлено, то оно должно отображаться в публикациях на
  
  - главной странице,
  
  - странице пользователя,
  
  - странице категории,
  
  - отдельной странице публикации.

### • Добавление новых публикаций.

У зарегистрированных пользователей должна быть возможность самостоятельно публиковать посты. Создал страницу для публикации новых записей posts/create/:

1. Страница добавления публикации должна быть доступна только авторизованным пользователям.

2. После валидации формы и добавления новой публикации пользователь должен быть перенаправлен на свою страницу profile/<username>/.

3. Новые категории и местоположения может создавать только администратор сайта через панель администратора.

4. Указав дату публикации «в будущем», можно создавать отложенные посты. Они должны стать доступны всем посетителям с момента, указанного в поле «Дата». Отложенные публикации должны быть доступны автору сразу же после отправки; автор должен видеть на своей странице все свои публикации, включая отложенные и снятые с публикации администратором.

### • Редактирование публикаций.

Добавил страницу редактирования публикации с адресом posts/<post_id>/edit/.
  
  - Права на редактирование должны быть только у автора публикации. Остальные пользователи должны перенаправляться на страницу просмотра поста.
  
  - Для страницы редактирования поста должен применяться тот же HTML-шаблон, что и для страницы создания нового поста: blog/create.html.
  
  - После окончания редактирования пользователь должен переадресовываться на страницу отредактированной публикации.

### • Комментарии к публикациям.

Создал систему комментирования записей. На странице поста под текстом записи должна выводиться форма для отправки комментария, а ниже — список комментариев.

1. Комментарии должны быть отсортированы по времени их публикации, «от старых к новым».

2. Комментировать публикации могут только авторизованные пользователи.

3. Авторы комментариев должны иметь возможность отредактировать собственные комментарии.

4. Для каждой публикации на
  
  - главной странице,
  
  - странице пользователя,
  
  - странице категории

нужно выводить количество комментариев.

5. Адрес для добавления комментария posts/<post_id>/comment/

6. Адрес для редактирования комментария posts/<post_id>/edit_comment/<comment_id>/

### • Удаление публикаций и комментариев.

Авторизованные пользователи должны иметь возможность удалять собственные публикации и комментарии. Перед удалением материала должна открываться подтверждающая страница, содержащая публикацию или комментарий. Для подтверждающей страницы не надо создавать отдельные 
шаблоны; для этого необходимо переиспользовать существующие шаблоны, необходимая логика в них уже присутствует.
  
  - Адрес для удаления публикации posts/<post_id>/delete/
  
  - Адрес для удаления комментария posts/<post_id>/delete_comment/<comment_id>/

### • Новые статичные страницы.

Обновите механизм создания и изменения статичных страниц в проекте, используя CBV. Адреса уже существующих статичных страниц не должны измениться.


Предыдущая версия https://github.com/SHURSHALO/Blogicum_sprint3
## Установка
1. Клонируйте репозиторий на свою локальную машину:
```
git clone git@github.com:SHURSHALO/Blogicum_FINAL_sprint4.git
```
2. Перейдите в директорию проекта:
```
cd Blogicum_FINAL_sprint4
```
3. Создайте и активируйте виртуальное окружение (опционально):
```
py -3.9 -m venv venv
```
```
source venv/Scripts/activate
```

4. Установите необходимые зависимости:
```
pip install -r requirements.txt
```
5. Примените миграции базы данных:
```
cd blogicum
```
```
python manage.py migrate
```
6. Создайте суперпользователя:
```
python manage.py createsuperuser
```
### Запуск
```
python manage.py runserver
```
Откройте веб-браузер и перейдите по адресу http://localhost:8000/, чтобы получить доступ к приложению Blogicum.

Админка доступна по адресу http://127.0.0.1:8000/admin/
