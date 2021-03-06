# vba-check-customers-and-vendors - проверка контрагентов

Файл `Проверка контрагентов.xlsm` позволяет проверить за раз большое кол-во контрагентов.

Скорость проверки: около 250 контрагентов в минуту.

Файл будет полезен финансовым аудиторам: например, вы выгружаете контрагентов из книги покупок / продаж и полученные ИНН разом «прогоняете» через макрос.

## Как начать пользоваться макросом

1. Скачиваем zip архив [`Проверка контрагентов.zip`](https://github.com/akzhar/vba-check-customers-and-vendors/raw/main/%D0%9F%D1%80%D0%BE%D0%B2%D0%B5%D1%80%D0%BA%D0%B0%20%D0%BA%D0%BE%D0%BD%D1%82%D1%80%D0%B0%D0%B3%D0%B5%D0%BD%D1%82%D0%BE%D0%B2.zip) и распаковываем его

3. Регистрируемся на [DaData.ru](https://dadata.ru/api/#registration_popup), получаем `API_KEY` (строку, состоящую из набора латинских букв и цифр)

4. Вставляем полученный `API_KEY` в файл `api key.txt`

2. Открываем файл `Проверка контрагентов.xlsm`

3. Если при открытии файла появится окно `Предупреждение системы безопасности`, разрешите запуск макросов, нажав кнопку `Включить содержимое`

<img src="https://raw.githubusercontent.com/akzhar/vba-check-customers-and-vendors/main/demo/1.png" alt="Включить содержимое" title="Включить содержимое" width="75%"/>

4. Выполняем настройку, описанную на странице `Инструкция` (делается всего 1 раз)
 
## Как выполнять проверку

1. Заполняем столбец `Критерий поиска` на листе `Проверка контрагентов` (это может быть что-то из списка на скриншоте ниже, например, ИНН контрагентов)

<img src="https://raw.githubusercontent.com/akzhar/vba-check-customers-and-vendors/main/demo/2.jpg" alt="Варианты критерия поиска" title="Варианты критерия поиска" width="75%"/>

2. Нажимаем кнопку `Начать поиск`

3. По каждому контрагенту макрос загрузит следующие данные:

      - ИНН юр. лица
      - Наименование юр. лица
      - ОКВЭД (код и наименование основного вида деятельности)
      - Статус (Действующая / В процессе ликвидации / Ликвидирована)
      - Дата регистрации юр. лица
      - Дата ликвидации юр. лица
      - ФИО генерального директора
      - ССЧ (среднесписочная численность сотрудников, данные на начало года, как обновлять - см. на странице `Инструкция`)

<img src="https://raw.githubusercontent.com/akzhar/vba-check-customers-and-vendors/main/demo/demo.gif" alt="demo" title="demo" width="100%"/>

## Варианты использования полученной из макроса информации

1. Выявить контрагентов, руководители которых являются сотрудниками (например, управленческий персонал, члены совета директоров и пр.) аудируемой компании (связанные стороны)

2. Получить данные о дебиторах, которые находятся в стадии ликвидации (резерв по сомнительным долгам)

3. Получить данные о кредиторах, которые ликвидированы, но отражены в составе кредиторской задолженности

4. Получить данные о ССЧ контрагента (среднесписочной численности сотрудников) для оценки возможности оказания услуг/выполнения работ.

    - Например, если ССЧ = 1 человек, а контрагент оказывает транспортные услуги в несопоставимых с численностью сотрудников объемах (мошенничество)

5. По контрагентам, численность которых равна 1, проверить фактически оказываемые для аудируемого лица услуги и основной вид деятельности контрагента (мошенничество)

6. По контрагентам, руководители в которых являются сотрудниками аудируемой организации, оценить могла ли проверяемая компания своими силами выполнить работы без привлечения сторонней организации.

    - Например, начальник IT-отдела аудируемой компании одновременно является руководителем компании-поставщика, ССЧ которой равна 1 человек. Компания-поставщик оказывает услуги по настройке серверов, поддержке 1С и т.д. для аудируемой компании (расходы по налогу на прибыль, вычеты по НДС). В ходе проверки мы видим, что аудируемая компания обладает необходимыми ресурсами для выполнения данных работ самостоятельно без привлечения сторонней организации: начальник ИТ-отдела может выполнять работы по настройке серверов самостоятельно в рамках трудового договора с аудируемой компанией без привлечения сторонней организации, в которой он же выполняет все работы (мошенничество).

### Источники данных	

- Все кроме ССЧ: https://dadata.ru/api/suggest/party
- Расшифровка ОКВЭД: https://dadata.ru/api/suggest/okved2
- ССЧ: https://nalog.ru/opendata


