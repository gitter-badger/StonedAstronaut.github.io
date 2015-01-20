title: Приветствую на своем блоге
date: 2015-01-20
published: True

Привет.

Этот блог я написал по видео урокам tuts+. Для написания использовался язык python3.4, микрофреймворк flask 0.9, для заготовок статей - markdown, для генерации статических страниц - Frozen-Flask, для подстветки синтаксиса кода на страницах блога - Pygments.

Пример кода:

    :::python
    @app.route('/')
    def index():
       return render_template('index.html', posts=blog.posts)