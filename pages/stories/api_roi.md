---
title: ROI API
keywords: РОИ, Российская общественная инициатива, API РОИ, API документация, технический писатель, технический писатель фриланс, технический писатель удаленно
sidebar: general_sidebar
permalink: api_roi.html
folder: stories
summary: "v 1.0"
---


## Общая информация

- Взаимодействие с платформой осуществляется через REST API.

- API функционирует в режиме чтения данных (GET-запросы).

- Все запросы выполняются только по протоколу HTTPS.

- Ответы на запросы предоставляются в формате JSON.

- No sign up or API key needed.

- Base url <code class="language-plaintext highlighter-rouge">https://www.roi.ru/api/</code>.

## Resources description

### Справочники

Supporting data for structuring and storing initiatives.

#### Initiatives implementation levels

<span class="label label-success" style="font-size: .9em;">GET</span> **/attributes/level**

This endpoint allows you to get values of initiatives implementation levels.

##### Path Parameters

Not used.

##### Example of API call

```bash
curl --location --request GET 'https://www.roi.ru/api/attributes/level'
````

##### Success response (HTTP 200)

<div class="panel panel-default">

<!-- Nav tabs -->
    <ul class="nav nav-tabs" role="tablist">
        <li role="presentation" class="active">
      <a href="#tab-1-id" aria-controls="tab-1-id" role="tab" data-toggle="tab">
                Schema
            </a>
        </li>
        <li role="presentation">
            <a href="#tab-2-id" aria-controls="tab-2-id" role="tab" data-toggle="tab">
                Response
            </a>
        </li>
    </ul>

<!-- Tab panes -->
    <div class="tab-content">
        <div role="tabpanel" class="tab-pane active" id="tab-1-id">
            <div class="container-fluid" markdown="1">    

|-------|--------|---------|
| ***data***  | *array* | *Корневой элемент данных*  |
| **id** | integer | Идентификатор |
| **title** | string | Уровень реализации |

</div> <!-- This close tag must be left aligned. -->
        </div>
        <div role="tabpanel" class="tab-pane" id="tab-2-id">
            <div class="container-fluid" markdown="1">

```json-doc
{
    "data": [
        {
            "id": 1,
            "title": "Федеральный"
        },
        {
            "id": 2,
            "title": "Региональный"
        },
        {
            "id": 3,
            "title": "Муниципальный"
        }
    ]
}
```
</div> <!-- This close tag must be left aligned. -->
        </div>

    </div>
</div>

##### Unauthorized response (HTTP 401)

The request has not been completed because of invalid authentication credentials for the resource.

{% include important.html content="To fix the error, make sure the endpoint is correct and retry the request." %}

***

#### Статусы инициативы

<span class="label label-success" style="font-size: .9em;">GET</span> **/attributes/status**

Получает значения справочника со статусами инициативы.

##### Path Parameters

Not used.

##### Example of API call

```bash
curl --location --request GET 'https://www.roi.ru/api/attributes/status'
````

##### Success response (HTTP 200)

Значения справочника уровней реализации инициатив.

<div class="panel panel-default">

<!-- Nav tabs -->
    <ul class="nav nav-tabs" role="tablist">
        <li role="presentation" class="active">
      <a href="#tab-3-id" aria-controls="tab-3-id" role="tab" data-toggle="tab">
                Schema
            </a>
        </li>
        <li role="presentation">
            <a href="#tab-4-id" aria-controls="tab-4-id" role="tab" data-toggle="tab">
                Response
            </a>
        </li>
    </ul>

<!-- Tab panes -->
    <div class="tab-content">
        <div role="tabpanel" class="tab-pane active" id="tab-3-id">
            <div class="container-fluid" markdown="1">    

|-------|--------|---------|
| ***data***  | *array* | *Корневой элемент данных*  |
| **id** | integer | Идентификатор |
| **title** | string | Статусы инициативы |

</div> <!-- This close tag must be left aligned. -->
        </div>
        <div role="tabpanel" class="tab-pane" id="tab-4-id">
            <div class="container-fluid" markdown="1">

```json-doc
{
    "data": [
        {
            "id": 31,
            "title": "На голосовании"
        },
        {
            "id": 71,
            "title": "В архиве"
        },
        {
            "id": 51,
            "title": "На рассмотрении ЭРГ"
        },
        {
            "id": 61,
            "title": "Решение принято ЭРГ"
        }
    ]
}
```
</div> <!-- This close tag must be left aligned. -->
        </div>

    </div>
</div>

##### Unauthorized response (HTTP 401)

The request has not been completed because of invalid authentication credentials for the resource.

{% include important.html content="To fix the error, make sure the endpoint is correct and retry the request." %}

***

### Инициативы

Предложения граждан России по вопросам социально-экономического развития страны, совершенствования государственного и муниципального управления.

#### Инициативы в статусе “На голосовании”

<span class="label label-success" style="font-size: .9em;">GET</span> **/petitions/poll**

Получает список инициатив в статусе «На голосовании».

##### Path Parameters

Not used.

##### Example of API call

```bash
curl --location --request GET 'https://www.roi.ru/api/petitions/poll'
````

##### Success response (HTTP 200)

<div class="panel panel-default">

<!-- Nav tabs -->
    <ul class="nav nav-tabs" role="tablist">
        <li role="presentation" class="active">
      <a href="#tab-5-id" aria-controls="tab-5-id" role="tab" data-toggle="tab">
                Schema
            </a>
        </li>
        <li role="presentation">
            <a href="#tab-6-id" aria-controls="tab-6-id" role="tab" data-toggle="tab">
                Response
            </a>
        </li>
    </ul>

<!-- Tab panes -->
    <div class="tab-content">
        <div role="tabpanel" class="tab-pane active" id="tab-5-id">
            <div class="container-fluid" markdown="1">    

|-------|--------|---------|
| ***data***  | *array* | *Корневой элемент данных*  |
| **id** | integer | Идентификатор |
| **title** | string | Наименование инициативы |
| ***geo***  | *object* | *Информация о местоположении* |
| **geo.area**  | string | Федеральный округ |
| **geo.region**  | string | Регион |
| **geo.municipality**  | string | Муниципалитет |
| ***level***  | *object* | *Уровень инициативы*  |
| **level.id**  | integer | Идентификатор уровня |
| **level.title**  | string | Наименование уровня | 
| ***status***  | *object* | *Статус инициативы*  |
| **status.id**  | integer | Идентификатор статуса |
| **status.title** | string | Наименование статуса 


</div> <!-- This close tag must be left aligned. -->
        </div>
        <div role="tabpanel" class="tab-pane" id="tab-6-id">
            <div class="container-fluid" markdown="1">

```json-doc
{
    "data": [
        {
            "id": 24104,
            "title": "Ввести понятие «Самозанятость», дать возможность работать без документов",
            "geo": {
                "area": "Уральский федеральный округ",
                "region": "Тюменская область без автономных округов"
            },
            "level": {
                "id": 1,
                "title": "Федеральный"
            },
            "status": {
                "id": 31,
                "title": "На голосовании"
            }
        },
        {
            "id": 24241,
            "title": "Установить ограждения на тротуарах перед пешеходными переходами",
            "geo": {
                "area": "Южный федеральный округ",
                "region": "Краснодарский край"
            },
            "level": {
                "id": 1,
                "title": "Федеральный"
            },
            "status": {
                "id": 31,
                "title": "На голосовании"
            }
        },
        {
            "id": 25439,
            "title": "Увеличить в 5 раз штраф и ввести приоритетную эвакуацию за нарушение правил остановки или стоянки в местах, отведенных для остановки или стоянки транспортных средств инвалидов",
            "geo": {
                "area": "Центральный федеральный округ",
                "region": "г. Москва"
            },
            "level": {
                "id": 1,
                "title": "Федеральный"
            },
            "status": {
                "id": 31,
                "title": "На голосовании"
            }
        },

...

        {
            "id": 84330,
            "title": "Запретить вырубку деревьев и строительство нового жилого дома в центре г.Нижневартовска ХМАО-Югры, а также рассмотреть вопрос о реконструкции существующего сквера на данной территории квартал Б",
            "geo": {
                "area": "Уральский федеральный округ",
                "region": "Ханты-Мансийский автономный округ - Югра",
                "municipality": "Городской округ город Нижневартовск"
            },
            "level": {
                "id": 3,
                "title": "Муниципальный"
            },
            "status": {
                "id": 31,
                "title": "На голосовании"
            }
        }
    ]
}
```
</div> <!-- This close tag must be left aligned. -->
        </div>

    </div>
</div>

##### Unauthorized response (HTTP 401)

The request has not been completed because of invalid authentication credentials for the resource.

{% include important.html content="To fix the error, make sure the endpoint is correct and retry the request." %}

***

#### Инициативы в статусе “Решение принято”

<span class="label label-success" style="font-size: .9em;">GET</span> **/petitions/complete**

Получает список инициатив в статусе «Решение принято».

##### Path Parameters

Not used.

##### Example of API call

```bash
curl --location --request GET 'https://www.roi.ru/api/petitions/complete'
````

##### Success response (HTTP 200)

<div class="panel panel-default">

<!-- Nav tabs -->
    <ul class="nav nav-tabs" role="tablist">
        <li role="presentation" class="active">
      <a href="#tab-7-id" aria-controls="tab-7-id" role="tab" data-toggle="tab">
                Schema
            </a>
        </li>
        <li role="presentation">
            <a href="#tab-8-id" aria-controls="tab-8-id" role="tab" data-toggle="tab">
                Response
            </a>
        </li>
    </ul>

<!-- Tab panes -->
    <div class="tab-content">
        <div role="tabpanel" class="tab-pane active" id="tab-7-id">
            <div class="container-fluid" markdown="1">    

|-------|--------|---------|
| ***data***  | *array* | *Корневой элемент данных*  |
| **id** | integer | Идентификатор |
| **title** | string | Наименование инициативы |
| ***geo***  | *object* | *Информация о местоположении* |
| **geo.area**  | string | Федеральный округ |
| **geo.region**  | string | Регион |
| **geo.municipality**  | string | Муниципалитет |
| ***level***  | *object* | *Уровень инициативы*  |
| **level.id**  | integer | Идентификатор уровня |
| **level.title**  | string | Наименование уровня | 
| ***status***  | *object* | *Статус инициативы*  |
| **status.id**  | integer | Идентификатор статуса |
| **status.title** | string | Наименование статуса 
| ***result***  | *object* | *Информация о решении по инициативе*  |
| **result.id**  | integer | Идентификатор решения |
| **result.title**  | string | Наименование решения |


</div> <!-- This close tag must be left aligned. -->
        </div>
        <div role="tabpanel" class="tab-pane" id="tab-8-id">
            <div class="container-fluid" markdown="1">

```json-doc
{
    "data": [
        {
            "id": 309,
            "title": "Вернуть минимально допустимый уровень содержание алкоголя в крови водителя",
            "geo": {
                "area": "Центральный федеральный округ",
                "region": "Московская область"
            },
            "level": {
                "id": 1,
                "title": "Федеральный"
            },
            "status": {
                "id": 61,
                "title": "Решение принято ЭРГ"
            },
            "result": {
                "id": 1,
                "title": "Данная инициатива реализована"
            }
        },
        {
            "id": 401,
            "title": "Сохранять номер мобильного телефона при переходе от одного оператора связи к другому.",
            "geo": {
                "area": "Центральный федеральный округ",
                "region": "Владимирская область"
            },
            "level": {
                "id": 1,
                "title": "Федеральный"
            },
            "status": {
                "id": 61,
                "title": "Решение принято ЭРГ"
            },
            "result": {
                "id": 1,
                "title": "Данная инициатива реализована"
            }
        }
...
        {
            "id": 66369,
            "title": "5 шагов: как поддержать граждан России и её экономику",
            "geo": {
                "area": "Центральный федеральный округ",
                "region": "г. Москва",
                "municipality": "Северное"
            },
            "level": {
                "id": 1,
                "title": "Федеральный"
            },
            "status": {
                "id": 61,
                "title": "Решение принято ЭРГ"
            },
            "result": {
                "id": 0,
                "title": ""
            }
        }
    ]
}
```
</div> <!-- This close tag must be left aligned. -->
        </div>

    </div>
</div>

##### Unauthorized response (HTTP 401)

The request has not been completed because of invalid authentication credentials for the resource.

{% include important.html content="To fix the error, make sure the endpoint is correct and retry the request." %}

***

#### Инициативы в статусе “В архиве”

<span class="label label-success" style="font-size: .9em;">GET</span> **/petitions/archive**

Получает список инициатив в статусе «В архиве».

##### Path Parameters

Not used.

##### Example of API call

```bash
curl --location --request GET 'https://www.roi.ru/api/petitions/archive'
````

##### Success response (HTTP 200)

<div class="panel panel-default">

<!-- Nav tabs -->
    <ul class="nav nav-tabs" role="tablist">
        <li role="presentation" class="active">
      <a href="#tab-9-id" aria-controls="tab-9-id" role="tab" data-toggle="tab">
                Schema
            </a>
        </li>
        <li role="presentation">
            <a href="#tab-10-id" aria-controls="tab-10-id" role="tab" data-toggle="tab">
                Response
            </a>
        </li>
    </ul>

<!-- Tab panes -->
    <div class="tab-content">
        <div role="tabpanel" class="tab-pane active" id="tab-9-id">
            <div class="container-fluid" markdown="1">    

|-------|--------|---------|
| ***data***  | *array* | *Корневой элемент данных*  |
| **id** | integer | Идентификатор |
| **title** | string | Наименование инициативы |
| ***geo***  | *object* | *Информация о местоположении* |
| **geo.area**  | string | Федеральный округ |
| **geo.region**  | string | Регион |
| **geo.municipality**  | string | Муниципалитет |
| ***level***  | *object* | *Уровень инициативы*  |
| **level.id**  | integer | Идентификатор уровня |
| **level.title**  | string | Наименование уровня | 
| ***status***  | *object* | *Статус инициативы*  |
| **status.id**  | integer | Идентификатор статуса |
| **status.title** | string | Наименование статуса |

</div> <!-- This close tag must be left aligned. -->
        </div>
        <div role="tabpanel" class="tab-pane" id="tab-10-id">
            <div class="container-fluid" markdown="1">

```json-doc
{
    "data": [
        {
            "id": 310,
            "title": "Возврат системы перехода на «зимнее» время",
            "geo": {
                "area": "Центральный федеральный округ",
                "region": "г. Москва"
            },
            "level": {
                "id": 1,
                "title": "Федеральный"
            },
            "status": {
                "id": 71,
                "title": "В архиве"
            }
        },
        {
            "id": 330,
            "title": "Наделить собственников недвижимости избирательным правом на муниципальном уровне по месту ее нахождения",
            "geo": {
                "area": "Центральный федеральный округ",
                "region": "г. Москва"
            },
            "level": {
                "id": 1,
                "title": "Федеральный"
            },
            "status": {
                "id": 71,
                "title": "В архиве"
            }
        },
        {
            "id": 331,
            "title": "Упрощенный порядок развертывания сетей БШПД в сельских населенных пунктах и малых городах",
            "geo": {
                "area": "Центральный федеральный округ",
                "region": "г. Москва"
            },
            "level": {
                "id": 1,
                "title": "Федеральный"
            },
            "status": {
                "id": 71,
                "title": "В архиве"
            }
        },
...
        {
            "id": 68517,
            "title": "Создать атласы конструкторских решений по всем отраслям промышленности",
            "geo": {
                "area": "Центральный федеральный округ",
                "region": "г. Москва",
                "municipality": "Муниципальный район Светлогорский"
            },
            "level": {
                "id": 1,
                "title": "Федеральный"
            },
            "status": {
                "id": 71,
                "title": "В архиве"
            }
        }
    ]
}
```
</div> <!-- This close tag must be left aligned. -->
        </div>

    </div>
</div>

##### Unauthorized response (HTTP 401)

The request has not been completed because of invalid authentication credentials for the resource.

{% include important.html content="To fix the error, make sure the endpoint is correct and retry the request." %}

***

#### Initiative

<span class="label label-success" style="font-size: .9em;">GET</span> **/petition/{id}**

Получает информацию по интересующей инициативе.

##### Path Parameters

**id** <span style="color: #848484; font-weight: 400; text-transform: lowercase;">(required)</span> - Initiative ID.

##### Example of API call

{% include note.html content="Example based on Initiative ID 1016 - *Мой дом - моя крепость!*" %}

```bash
curl --location --request GET 'https://www.roi.ru/api/petition/1016'
````

##### Success response (HTTP 200)

<div class="panel panel-default">

<!-- Nav tabs -->
    <ul class="nav nav-tabs" role="tablist">
        <li role="presentation" class="active">
      <a href="#tab-11-id" aria-controls="tab-11-id" role="tab" data-toggle="tab">
                Schema
            </a>
        </li>
        <li role="presentation">
            <a href="#tab-12-id" aria-controls="tab-12-id" role="tab" data-toggle="tab">
                Response
            </a>
        </li>
    </ul>

<!-- Tab panes -->
    <div class="tab-content">
        <div role="tabpanel" class="tab-pane active" id="tab-11-id">
            <div class="container-fluid" markdown="1">    

|-------|--------|---------|
| ***data***  | *array* | *Корневой элемент данных*  |
| **id** | integer | Идентификатор |
| **code** | string | Номер инициативы |
| **url**  | string | Ссылка на инициативу |
| ***level***  | *object* | *Уровень инициативы*  |
| **level.id**  | integer | Идентификатор уровня |
| **level.title**  | string | Наименование уровня | 
| ***status***  | *object* | *Статус инициативы*  |
| **status.id**  | integer | Идентификатор статуса |
| **status.title** | string | Наименование статуса |
| ***result***  | *object* | *Информация о решении по инициативе*  |
| **result.id**  | integer | Идентификатор решения |
| **result.title**  | string | Наименование решения |
| **title** | string | Наименование инициативы |
| **description** | string | Описание инициативы |
| ***attachment***  | *object* | *Дополнительные материалы*  |
| ***attachment.photo***  | *object* | *Сопроводительные фотографии* |
| **attachment.photo.title**  | string | Наименование фотографии |
| **attachment.photo.url**  | string | Ссылка на фотографию |
| ***attachment.document***  | *object* | *Сопроводительные документы инициативы* |
| **attachment.document.title**  | string | Наименование документа |
| **attachment.document.url**  | string | Ссылка на документ |
| ***decision***  | *object* | *Предлагаемое решение по инициативе*  |
| **decision.text**  | string | Текст предлагаемого решения |
| **prospective** | string | Описание проблемы|
| ***category***  | *object* | *Категория инициативы*  |
| ***category.id***  | integer | Идентификатор категории |
| **category.title**  | string | Наименование категории | 
| ***geo***  | *object* | *Информация о местоположении* |
| **geo.area**  | string | Федеральный округ |
| **geo.region**  | string | Регион |
| **geo.municipality**  | string | Муниципалитет |
| ***date***  | *object* | *Информация о датах инициативы* |
| ***date.poll***  | *object* | *Дата публикации инициативы* |
| **date.poll.begin**  | integer | Дата начала голосования |
| **date.poll.end** | integer | Дата окончания голосования |
| ***vote***  | *object* | *Информация о голосах инициативы* |
| **vote.progress**  | float | Прогресс набора необходимого порога голосов, % |
| **vote.threshold**  | integer | Порог голосов |
| **vote.affirmative**  | integer | Подано голосов «За» инициативу |
| **vote.negative**  | integer | Подано голосов «Против» инициативы | 
| ***authorship***  | *object* | *Другие инициативы на голосовании автора*  |
| **authorship.id**  | integer | Идентификатор другой инициативы на голосовании автора | 


</div> <!-- This close tag must be left aligned. -->
        </div>
        <div role="tabpanel" class="tab-pane" id="tab-12-id">
            <div class="container-fluid" markdown="1">

```json-doc
{
    "data": {
        "id": 1016,
        "code": "77Ф1016",
        "url": "https://www.roi.ru/1016",
        "level": {
            "id": 1,
            "title": "Федеральный"
        },
        "status": {
            "id": 61,
            "title": "Решение принято ЭРГ"
        },
        "result": {
            "id": 0,
            "title": ""
        },
        "title": "Мой дом - моя крепость!",
        "description": "Известны случаи, когда граждане, подвергшиеся нападению в собственном доме и оказавшие злоумышленникам сопротивление, попадают на скамью подсудимых по обвинениям в превышении пределов необходимой самообороны, умышленном причинении вреда здоровью нападавших, или даже убийстве. Даже при благоприятном исходе дела это оборачивается потраченными нервами, временем, деньгами и здоровьем.\r\n\r\nПредлагается внести поправки в федеральные законы, или конституцию, с тем чтобы любые действия, совершённые в собственном доме для защиты имущества, здоровья и жизни близких, собственной жизни и здоровья считались совершёнными в ситуации необходимой самообороны и не выходящими за её пределы(если не будет доказано обратное, и необходимость доказательства лежит на обвиняющей стороне).",
        "decision": [
            {
                "text": "Мой дом - моя крепость!"
            }
        ],
        "prospective": "Устранится \"презумция виновности\" в отношении законопослушных людей, защищающих свои конституционные права и ценности. Люди, защитившие свой дом и семью, смогут продолжать нормально жить вместо того, чтобы заниматься заниматься судебной волокитой, или даже сидеть в тюрьме по сути ни за что.",
        "category": [
            {
                "id": 33,
                "title": "Безопасность"
            },
            {
                "id": 1143,
                "title": "Уголовный кодекс"
            }
        ],
        "geo": {
            "area": "Центральный федеральный округ",
            "region": "г. Москва"
        },
        "date": {
            "poll": {
                "begin": 1366488000,
                "end": 1392889595
            }
        },
        "vote": {
            "progress": 100.45,
            "threshold": 100000,
            "affirmative": 100458,
            "negative": 552
        }
    }
}
```
</div> <!-- This close tag must be left aligned. -->
        </div>

    </div>
</div>

##### Unauthorized response (HTTP 401)

The request has not been completed because of invalid authentication credentials for the resource.

{% include important.html content="To fix the error, make sure the endpoint is correct and retry the request." %}

{% include links.html %}
