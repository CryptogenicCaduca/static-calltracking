# Установка и конфигурация

### Установка
Сохраните скрипт sipuni-calltracking.js и подключите его на странице.
```html
<script src='/js/sipuni-calltracking.js'></script>
```

### Пример использования
Предположим, нам нужно отследить трафик с Яндекс Директ и двух сайтов: habrahabr.ru и oborot.ru

В HTML добавляем CSS класс ct_phone в элемент, где будет происходить подмена номеров:
```html
<div>Телефон: <span class="ct_phone">+7 888 888-88-88</span></div>
```    

Настраиваем вызов скрипта подмены. 
 * В поле sources задаем правила определения источников трафика. 
 * В поле phones задаем названия источников трафика, и соответсвующие им номера телефонов. 

Вызов этого скрипта должен происходить после HTML элементов содержащих номера телефонов, или в событии готовности DOM модели.
```javascript
<script>
    sipuniCalltracking({
      sources: {
        'ydirect':{'utm_source': 'direct.yandex.ru'},
        'articles':{'ref':/(habrahabr|oborot\.ru)/ig}
      },
      phones: [
        {'src':'articles', 'phone':['+75555555555']},
        {'src':'ydirect', 'phone':['+73333333333']}
      ]
    }, window);
</script>
```
В этом примере предполагается, что ссылки с Яндекс Директ помечены utm метками.

 * [Оглавление](index.md)
 * [Настройка источников трафика](sources.md)
 * [Отображение нескольких телефонов](many-numbers.md)
 * [Подмена контента страницы](subst-content.md)


[![](img/sipuni_logo.png)](http://calltracking.sipuni.com)
 
