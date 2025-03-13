# CourseWork_4sem [Novak Ksenia 353504]

## Content sharing web application with adaptive recommendation system
People naturally seek out connection and interaction with others, and this tendency is a fundamental aspect of human nature. In the digital age, where interactions often happen through screens, content sharing platforms serve as vital conduits for communication. These platforms enable users to express themselves, share their thoughts, ideas, and creativity, thus contributing to the development of a more dynamic and varied information landscape.




## Functional requirements
1. Authorization via mail, the ability to log in through other services 
2. User profile, text description field
3. Creating a note with the ability to add a hashtag(s)
4. Creating comments to your own or other people's posts, the "like" function, reposts to your page
5. A feed of recommendations based on user preferences, subscriptions, and used/viewed hashtags.




# Content Sharing Web Application with Adaptive Recommendation System

## Описание проекта

Данное веб-приложение служит платформой для обмена контентом, где пользователи могут делиться своими мыслями, идеями и творческими работами. Приложение предлагает возможности для создания и управления профилями пользователей, публикации заметок с хештегами, комментирования постов и получения рекомендаций на основе интересов пользователей.

## Функциональные требования

1. **Аутентификация через электронную почту** и возможность входа через сторонние сервисы.
2. **Профиль пользователя** с текстовым полем описания.
3. **Создание заметки** с возможностью добавления хештегов.
4. **Создание комментариев** к своим и чужим постам, функция "лайка", репосты на своей странице.
5. **Лента рекомендаций** на основе предпочтений пользователей, подписок и используемых/просмотренных хештегов.

## Модели данных

### 1. Модель пользователя (User)

**Цель:** Управление авторизацией и хранение информации о пользователях.

**Поля:**
- `userId` (String): Уникальный идентификатор пользователя.
- `username` (String): Имя пользователя.
- `email` (String): Адрес электронной почты для аутентификации.
- `passwordHash` (String): Хеш пароля для обеспечения безопасности.
- `profilePicture` (String): URL к изображению профиля.
- `bio` (String): Текстовое описание пользователя.
- `createdAt` (Date): Дата регистрации.
- `updatedAt` (Date): Дата последнего обновления профиля.
- `authProvider` (String): Сервис, через который пользователь регистрировался (например, Google, Facebook).

**Методы:**
- `register()`: Регистрация нового пользователя через email или внешний сервис.
- `login()`: Вход пользователя в приложение через email или внешний сервис.
- `editProfile()`: Изменение информации профиля.
- `deleteAccount()`: Удаление учетной записи.

### 2. Модель поста (Post)

**Цель:** Хранение записей, которые создают пользователи, и управление ими.

**Поля:**
- `postId` (String): Уникальный идентификатор поста.
- `title` (String): Заголовок поста.
- `content` (String): Основное содержание поста.
- `createdAt` (Date): Дата создания поста.
- `updatedAt` (Date): Дата последнего обновления поста.
- `userId` (String): Идентификатор пользователя, создавшего пост.
- `hashtags` (Array of Strings): Список хештегов, связанных с постом.

**Методы:**
- `createPost()`: Создание нового поста с хештегами.
- `editPost()`: Редактирование существующего поста.
- `deletePost()`: Удаление поста.
- `getPost()`: Получение информации о посте.
- `likePost()`: Добавление функции "лайк" к посту.
- `repost()`: Репост поста на своей странице.

### 3. Модель комментария (Comment)

**Цель:** Хранение комментариев к постам и их управление.

**Поля:**
- `commentId` (String): Уникальный идентификатор комментария.
- `content` (String): Содержание комментария.
- `createdAt` (Date): Дата создания комментария.
- `userId` (String): Идентификатор пользователя, который написал комментарий.
- `postId` (String): Идентификатор поста, к которому относится комментарий.

**Методы:**
- `addComment()`: Добавление нового комментария к посту.
- `editComment()`: Редактирование существующего комментария.
- `deleteComment()`: Удаление комментария.
- `getCommentsByPost()`: Получение всех комментариев для конкретного поста.

### 4. Модель рекомендаций (Recommendation)

**Цель:** Генерация рекомендаций для пользователей на основе их взаимодействий и интересов.

**Поля:**
- `recommendationId` (String): Уникальный идентификатор рекомендации.
- `userId` (String): Идентификатор пользователя, для которого предназначена рекомендация.
- `postId` (String): Идентификатор рекомендованного поста.
- `reason` (String): Описание причины рекомендации (например, на основе просмотренных хештегов или подписок
