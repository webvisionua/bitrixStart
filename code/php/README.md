<a name="top"></a>
# Правила оформления PHP-кода

### Соблюдение стандартов

В случае, если форматирование кода не оговорено в этом разделе — код следует форматировать в соответсвии с PSR-2

- В качестве отступов в коде используется табуляция.
- Открывающая фигурная скобра находится в той же строке.
- Закрывающая фигурная скобка находится на новой строке.


### Комментирование кода

Комментирование кода PHP — его неотъемлимая часть!

При комментировании кода следует использовать [PHPDoc](http://phpdoc.org/) комментарии.

Для однострочных поясняющих комментариев в коде можно использовать обычные комментарии, начинающиеся с `// `.


### Переменные

Основное правило именования переменных — имя должно быть таким, чтобы не требовался комментарий для объяснения назначения переменной.

### Префиксы
В именах переменных используются следующие префиксы:
- **ar** — для массивов
- **db** — для CDBResult
- **b** — для булевых переменных, если из имени не очевидно. Перфикс обязателен, если булевое значение используется там, где обычно хранится строковое **Y/N**.

Пример:
```php
$arUserList = array();
$dbRes      = CIBlockElement::GetByID($id);
$bActive    = false;
```
**Имена переменных не должны начинаться с подчеркивания.**

### Глобальные переменные
Глобальные переменные пишутся ЗАГЛАВНЫМИ буквами с разделением слов знаком подчеркивания. 
```php
global $USER, $APPLICATION, $AR_MESSAGES.
```

***Использование глобальных переменных допускается лишь там, где это абсолютно необходимо. Используйте то, что даёт D7, там, где он это даёт!***

### Локальные переменные
Локальные для скрипта (функции, метода, класса) переменные начинаются всегда с маленькой буквы, слова разделяются капитализацией первого символа (camelCase). 

Данное правило распространяется на аббревиатуры. <br>Т.е. станция BBC пишется `$bbcStation;` `$arBbcStations;`. 

Исключение только одно — ID записывается заглавными. <br>Т.е. `$sectionID`, `$arElementIDs`.
```php
$counter        = 0;
$bElementActive = false;
$lastErrorMsg   = '';
$ID             = $_GET['ID'];
```

### Вспомогательные (временные) переменные
Переменные, используемые в конструкциях FOR... FOREACH, допускается именовать сокращенно, если код блока, в котором они используются, просматривается без прокрутки страницы.
```php
for ($i = 0; $i < count($arRows); $i++) {
	// ...
}
foreach ($arElement as $k => $v) {
	// ...
}
while ($arr = $dbRes->Fetch()) {
	// ...
}
```

### Константы

Имена констант записываются ЗАГЛАВНЫМИ буквами, слова разделяются знаком подчеркивания. В связи с глобальной областью видимости константы необходимо предварять коротким префиксом (по имени модуля, компонента, шаблона).


### Символьные коды Битрикс

Сомвольные коды в битриксе нужны для многих вещей и поэтому следует придерживаться однообразного их наименования.
Символьный код должен быть написан латинскими буквами, без цифр и спецсимволов, и должен отражать суть инфоблока, раздела или элемента.

<table class="table table-bordered">
<tr>
	<th>Где пишем</th>
	<th>Как пишем</th>
</tr>
	<tr>
		<td>В инфоблоках:</td> 
		<td>UPPER_CASE</td>
	</tr>
	<tr>
		<td>В элементах инфоблоков:</td> 
		<td>lower-case</td>
	</tr>
	<tr>
		<td>В разделах:</td> 
		<td>lower-case</td>
	</tr>
	<tr>
		<td>Ключи массивов <b>arParams, arResult</b>:</td> 
		<td>UPPER_CASE</td>
	</tr>
	<tr>
		<td>Ключи массива языковых файлов:</td> 
		<td>UPPER_CASE</td>
	</tr>
</table>



### Именование классов, методов, функций

- Имена классов всегда начинаются с заглавной буквы. Слова отделяются капитализацией первой буквы. (CamelCase)
- Имена методов, функций всегда начинаются с маленькой буквы. Слова отделяются капитализацией первой буквы. (camelCase)

В связи с глобальной областью видимости функций их имена следует начинать с короткого префикса (по имени модуля, компонента, шаблона).



### Оформление управляющих структур
>Общее для управляющих структур правило — логический блок кода выделяется отступом.

Если блок не умещается в один экран, делается отступ минимум в две табуляции. Большой блок кода, относимый к одному логическому элементу, должен отделяться двумя и более пустыми строками и снабжаться открывающим и закрывающим комментариями, поясняющими логику элемента.


### Инструменты для автоформатирования кода, настройка параметров

> 
> 

**[⬆ back to top](#top)**
