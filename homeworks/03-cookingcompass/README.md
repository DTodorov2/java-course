# Домашно 3

`Краен срок: 20.01.2024, 23:59`

Задачата ни този път цели упражняване на познанията ни за HTTP, REST и JSON.

За разлика от предните задачи, този път няма да има автоматични референтни тестове, готови интерфейси, които да имплементирате или фиксирана от нас структура на проекта - имате цялата свобода, що се отнася до дизайна, имплементацията и тестването.

## **Cooking Compass** :spaghetti:

Създайте Java клиент, който предоставя възможност за търсене на рецепти за готвене по различни критерии.

[REST API](https://developer.edamam.com/edamam-docs-recipe-api)-то, което ще използваме за намиране на рецепти, е публично, има безплатен план и работи с application ID и application key като средство за автентикация, които може да вземете след регистрация. След приключване на работата по заданието, по желание можете да изтриете регистрацията си чрез изпращане на имейл до Edamam.

При регистрация, изберете план "Recipe Search API - Developer".

Необходимият ви endpoint e `/api/recipes/v2`, документиран [тук](https://developer.edamam.com/edamam-docs-recipe-api).

Безплатният план на API-то [има свои лимити](https://developer.edamam.com/edamam-recipe-api) - можете да правите **до 10 заявки на минута**, **до 10000 заявки на месец** и **се връщат до 100 резултата на заявка**, поради което ще се наложи да обмислите и оптимизирате използването му, докато разработвате и тествате.

### Дизайн

Както казва чичото на Спайдърмен: "With Great Power Comes Great Responsibility".
Този път, вие определяте абстракциите, които ще използвате. Използвайте възможността да приложите **design patterns**, като задачата предразполага в това отношение и съответно ще получите бонус.

### Функционалност

Критериите, по които трябва да можем да търсим рецепти, са:

- ключови думи
- за кое хранене от деня е подходящо ястието (закуска/обяд/...)
- за какъв режим на хранене е подходящо (alcohol-free/gluten-free/...)

Уверете се, че клиентът поддържа търсене по различни комбинации от гореизброените параметри, като трябва да се поддържа подаване и на множество стойности за даден параметър.

#### Резултати

От върнатите от API-то резултати, клиентът трябва да изчита като минимум следните полета за всяка готварска рецепта: `label`, `dietLabels`, `healthLabels`, `totalWeight`, `cuisineType`, `mealType`, `dishType`, `ingredientLines`.

#### Странициране

Когато едно API може да върне голям брой резултати, обикновено (от performance съображения) то не го прави на един път, а използва т.нар. *странициране* - връща резултатите на части (страници), като първо извличаме първа страница, после втора и т.н.

Вътрешната имплементация на вашия Java клиент трябва да взима резултатите от поне две страници - вие решавате колко страници и по колко резултата максимум да вземете - единствено трябва да се съобразите с лимитите на безплатната версия на API-то.

:warning: **Важно:** Имайте предвид ограниченията на безплатния план на API-то при имплементиране и тестване на тази част от задачата.

#### Error handling

При изпращане на заявка към сървъра, обработката ѝ не винаги е успешна. Когато нещо се обърка, сървърът връща подходящ статус код и съобщение, които следва да обработвате. Моделирайте тази функционалност с помощта на custom checked exceptions.

### Тестване

:warning: Няма да бъдат приемани и оценявани решения без тестове!

Сами отговаряте за цялостното тестване на решението си, ние пък ще оценяваме колко добре сте се справили с това.
Целете се към висок code coverage, както и покрийте всички възможни сценарии, които вашият Java клиент поддържа, включително такива, които могат да ви се сторят тривиални.
За постигане на висок code coverage, може да се наложи да използвате Mockito.

### ✒️ Бележки 

:exclamation: Няма да се приемат решения, използващи библиотеки, фреймуърци и API-та, които не сме изучавали в курса и не са изрично упоменати в условието. За тази задача, знанията от курса са ви напълно достатъчни.

### **Предаване**

За да предадете решението си, архивирайте в **zip** архив **src** и **test** директориите на проекта и го качете в съответния assignment в грейдъра.

### **Оценяване**

Решението може да ви донесе до 100 точки, като ще бъде оценявано за:

* функционална пълнота и коректност, и за автоматични тестове с добър code coverage (50% от оценката). Решения без автоматични тестове няма да бъдат приемани и оценявани
* добър обектно-ориентиран дизайн, спазване на правилата за чист код и подбиране на оптимални за задачата структури от данни (50% от оценката)
* подходящото използване на design patterns може да ви донесе бонус точки

### Желаем ви успех! :four_leaf_clover: 