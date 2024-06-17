## Создайте пару представлений в вашем первом приложении:
### главная
### о себе
```
class MainPageView(TemplateView):
    template_name = 'myapp/index.html'

    def get_context_data(self, **kwargs):
        contex = super().get_context_data(**kwargs)
        contex['name'] = 'Слукин Иван'
        contex['email'] = 'vania@gmail.com'
        contex['phone'] = '+79140735611'
        logger.info(f'посещение страницы index в: {datetime.now()}')
        return contex


class AboutView(TemplateView):
    template_name = 'myapp/about.html'

    def get_context_data(self, **kwargs):
        contex = super().get_context_data(**kwargs)
        contex['name'] = 'Слукин Иван'
        contex['email'] = 'vania@gmail.com'
        contex['phone'] = '+79140735611'
        logger.info(f'посещение страницы about в: {datetime.now()}')
        return contex
```
### Внутри каждого представления должна быть переменная html — многострочный текст с HTML-вёрсткой и данными о вашем первом Django-сайте и о вас.

```
def index(request):
    html = """
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Мой первый Django-сайт</title>
        <style>
            body {
                font-family: Arial, sans-serif;
                line-height: 1.5;
                margin: 0;
                padding: 20px;
            }
            
            h1 {
                color: #333;
            }
            
            p {
                color: #777;
            }
        </style>
    </head>
    <body>
        <h1>Добро пожаловать на мой первый Django-сайт!</h1>
    
        <h2>О сайте</h2>
        <p>Этот сайт разработан с использованием Django, фреймворка для создания веб-приложений на Python.</p>
    
        <h2>Обо мне</h2>
        <p>Привет, меня зовут Иван. Я являюсь начинающим веб-разработчиком. Мои навыки включают HTML, CSS, Python.</p>
    
        <footer>
            <p>Свяжитесь со мной: vanya@gmail.com | +79140735611</p>
        </footer>
    </body>
    </html>
    """
    logger.info(f'посещение страницы index в: {datetime.now()}')
    return HttpResponse(html)
```