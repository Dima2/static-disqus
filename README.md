#Disqus comments for static blogs

Insert discuss comments in static pages so users and search engines could see them even if disqus is down.

#Readme RU

Идея в том что каждый раз перед заливкой моего блога на сервер, выполняется скрипт [get_disqus_comments.py](https://github.com/Dima2/static-disqus/blob/master/blogofile/_controllers/comments.py) который добавляет новые комменты в файл threads.json.
 
Потом кастомный контролер для движка Вlogofile [comments.py](https://github.com/dima2/static-disqus/blob/master/blogofile/_controllers/comments.py) выстраивает их, вычисляет порядок и сдвиг (для древовидной структуры) и раскладывает их в dict readyPosts[id_поста]=[отсортированные_комменты] .
 
Когда по шаблону собираются комменты для поста [comments.mako](https://github.com/Dima2/static-disqus/blob/master/blogofile/_templates/comments.mako) они достаются из dict'а и выводятся с стилем.
 
В конце страницы добавляется javascript, который в случае если у посетителя включен javascript, не заблочен Disqus и сам disqus доступен, заменяет вышеупомянутый блок с комментами стандартным виджетом комментов Disqus.
