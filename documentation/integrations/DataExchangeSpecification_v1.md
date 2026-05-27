# Data Exchange Specification v1

---

## Change Notes

Версия 1.0.0

- Добавено съобщение E001
- Добавено съобщение E003
- Добавено съобщение E004
- Добавено съобщение E005
- Добавено съобщение E006
- Добавено съобщение E007
- Добавено съобщение E008
- Добавено съобщение E009
- Добавено съобщение E011
- Добавено съобщение E013
- Добавено съобщение E015
- Добавено съобщение E016
- Добавено съобщение E017
- Добавено съобщение E018
- Добавено съобщение E096
- Добавено съобщение E098
- Добавено условие CDX01
- Добавено условие CDX02
- Добавено условие CDX03
- Добавено условие CDX04
- Добавено условие CDX05
- Добавено условие CDX06
- Добавено условие CDX07
- Добавено условие CDX08
- Добавено условие CDX09
- Добавено правило RL001
- Добавено правило RL002
- Добавено правило RL003
- Добавено правило RL004
- Добавено правило RL005

---

## Съобщения

| Съобщение                                                                                                | Име  | Класификация | Адрес | Тип            | Налично в Release** | Изпращач    | Получател   |
| -------------------------------------------------------------------------------------------------------- | ---- | ------------ | ----- | -------------- | ------------------- | ----------- | ----------- |
| Заявка за извършване на проверка на доход на домакинство (отговор E096 или E098)                         | E001 |              |       | Request        | 1.11                | ИСДПЕБУКСЕЕ | НАП         |
| Резултат от проверка на доход на домакинство (отговор E096 или E098)                                     | E003 |              |       | Request        | 1.11                | НАП         | ИСДПЕБУКСЕЕ |
| Заявка за проверка на домакинство                                                                        | E005 |              |       | Request        |                     | ИСДПЕБУКСЕЕ | ГРАО, МВР   |
| Резултат от проверка на домакинство                                                                      | E006 |              |       | Resonse        |                     | ГРАО, МВР   | ИСДПЕБУКСЕЕ |
| Заявка за проверка на енергийни характеристики на жилище                                                 | E007 |              |       | Request        |                     | ИСДПЕБУКСЕЕ | АУЕР        |
| Резултат от проверка на енергийни характеристики на жилище                                               | E008 |              |       | Response       |                     | АУЕР        | ИСДПЕБУКСЕЕ |
| Заявка за проверка за отпуснато помощно средство/медицинско изделие от НЗОК                              | E009 |              |       | Request        |                     | ИСДПЕБУКСЕЕ | НЗОК        |
| Резултат от проверка за отпуснато помощно средство/медицинско изделие от НЗОК                            | E010 |              |       | Response       |                     | НЗОК        | ИСДПЕБУКСЕЕ |
| Заявка за проверка на титуляр на партида (отговор E096 или E098)                                         | E011 |              |       | Request        |                     | ИСДПЕБУКСЕЕ | ОЕМ         |
| Резултат от заявка за проверка на титуляр на партида (отговор E096 или E098)                             | E013 |              |       | Request        |                     | ОЕМ         | ИСДПЕБУКСЕЕ |
| Заявка за удостоверяване / прекратяване на статут                                                        | E015 |              |       | Request        |                     | ИСДПЕБУКСЕЕ | ОЕМ         |
| Потвърждение за удостоверен / прекратен статут                                                           | E016 |              |       | Response       |                     | ОЕМ         | ИСДПЕБУКСЕЕ |
| Заявка за промяна на титуляр                                                                             | E017 |              |       | Request        |                     | ОЕМ         | ИСДПЕБУКСЕЕ |
| Потвърждение за промяна на титуляр                                                                       | E018 |              |       | Response       |                     | ИСДПЕБУКСЕЕ | ОЕМ         |
| Успешно получаване на заявка (използва се за потвърждение на получаване на заявка при асинхронен процес) | Е096 |              |       | ОК Response    |                     | Всички      | Всички      |
| Грешка при обработка на заявка                                                                           | E098 |              |       | Error Response |                     | Всички      | Всички      |

---

## E001 Заявка за извършване на проверка на доход на домакинство (отговор E096 или E098)

| Name                           | R/C/O | Cardinality | Data types       | Constraint                     | Fixed Value | Rules | Conditions | Code Lists | Field Name / Tag | Description                                                                                                         |
| ------------------------------ | ----- | ----------- | ---------------- | ------------------------------ | ----------- | ----- | ---------- | ---------- | ---------------- | ------------------------------------------------------------------------------------------------------------------- |
| Header                         | R     | 1..1        |                  |                                |             |       |            |            | header           | Системна информация за съобщението                                                                                  |
| Type of sender                 | R     | 1..1        | Codeable Concept |                                |             |       |            | CL001      | sender           | Тип изпращач на съобщението                                                                                         |
| Sender Information System Name | R     | 1..1        | String           | min=1, max=255, chars=an       |             |       |            |            | senderISName     | Име и версия на информационната система, изпратила съобщението                                                      |
| Type of recipient              | R     | 1..1        | Codeable Concept |                                |             |       |            | CL001      | recipient        | Тип на получател на съобщението                                                                                     |
| Message ID                     | R     | 1..1        | UUID             | min=36, max=36                 |             |       |            |            | messageId        | Уникален идентификатор на съобщението - трябва да бъде ново UUID генерирано към момента на изпращане на съобщението |
| Type of message                | R     | 1..1        | String           | min=4, max=4, chars=an         |             |       |            |            | messageType      | Тип на съобщението                                                                                                  |
| Preparation Timestamp          | R     | 1..1        | Date and Time    | YYYY-MM-DDhh:mm:ss[+\\|-]hh:mm |             |       |            |            | createdOn        | Дата и час на изготвяне на съобщението по ISO 8601 в локално време с часова зона                                    |
| Contents                       | R     | 1..1        |                  |                                |             |       |            |            | contents         | Съдържание на съобщението                                                                                           |
| Household Members              | R     | 1..n        |                  |                                |             |       |            |            | householdMembers | Лица от домакинството                                                                                               |
| Identifier Type                | R     | 1..1        | Codeable Concept |                                |             |       |            | CL002      | identifierType   | Вид идентификатор                                                                                                   |
| Identifier                     | R     | 1..1        | String           |                                |             | RL001 |            |            | identifier       | ЕГН/ЛНЧ/ЛН                                                                                                          |
| Year                           | R     | 1..1        | Integer          | YYYY (календарна година)       |             |       |            |            | year             | Календарна година                                                                                                   |
| Has Declaration                | R     | 1..1        | Boolean          |                                |             |       |            |            | hasDeclaration   | Има подадена декларация по чл. 50 от ЗДДФЛ                                                                          |
| Non Taxable Income             | R     | 1..1        | Decimal          |                                |             |       |            |            | nonTaxableIncome | Необлагаеми доходи по чл. 13 от ЗДДФЛ                                                                               |
| Energy Expense                 | R     | 1..1        |                  |                                |             |       |            |            | energyExpense    | Данни за разходите за енергия                                                                                       |
| Year                           | R     | 1..1        | Integer          | YYYY (календарна година)       |             |       |            |            | year             | Календарна година                                                                                                   |
| Amount                         | R     | 1..1        | Decimal          |                                |             |       |            |            | amount           | Стойност на годишен разход за енергия                                                                               |

---

## E003 Резултат от проверка на доход на домакинство (отговор E096 или E098)

| Name                           | R/C/O | Cardinality | Data types       | Constraint                     | Fixed Value | Rules | Conditions | Code Lists | Field Name / Tag  | Description                                                                      |
| ------------------------------ | ----- | ----------- | ---------------- | ------------------------------ | ----------- | ----- | ---------- | ---------- | ----------------- | -------------------------------------------------------------------------------- |
| Header                         | R     | 1..1        | ---              |                                |             |       |            |            | header            | Системна информация за съобщението                                               |
| Type of sender                 | R     | 1..1        | Codeable Concept |                                |             |       |            | CL001      | sender            | Тип изпращач на съобщението                                                      |
| Sender Information System Name | R     | 1..1        | String           | min=1, max=255, chars=an       |             |       |            |            | senderISName      | Име и версия на информационната система, изпратила съобщението                   |
| Type of recipient              | R     | 1..1        | Codeable Concept |                                |             |       |            | CL001      | recipient         | Тип на получател на съобщението                                                  |
| Message ID                     | R     | 1..1        | UUID             | min=36, max=36                 |             |       |            |            | messageId         | Уникален идентификатор на текущото съобщение                                     |
| Type of message                | R     | 1..1        | String           | min=4, max=4, chars=an         |             |       |            |            | messageType       | Тип на съобщението                                                               |
| Preparation Timestamp          | R     | 1..1        | Date and Time    | YYYY-MM-DDhh:mm:ss[+\\|-]hh:mm |             |       |            |            | createdOn         | Дата и час на изготвяне на съобщението по ISO 8601 в локално време с часова зона |
| Contents                       | R     | 1..1        | ---              |                                |             |       |            |            | contents          | Съдържание на съобщението                                                        |
| Operation Id                | R     | 1..1        | UUID             | min=36, max=36                 |             |       |            |            | operationId       | Идентификатор на операция                                                        |
| Result Code                 | R     | 1..1        | Codeable Concept |                                |             | RL003 |            | CL006      | resultCode        | Код на резултата от проверката                                                   |
| Result Description          | O     | 0..1        | String           | min=0, max=500                 |             |       |            |            | resultDescription | Допълнително пояснение към резултата от проверката                               |

---

## E005 Заявка за проверка на домакинство

| Name                           | R/C/O | Cardinality | Data types       | Constraint                     | Fixed Value | Rules | Conditions | Code Lists | Field Name / Tag | Description                                                                                                         |
| ------------------------------ | ----- | ----------- | ---------------- | ------------------------------ | ----------- | ----- | ---------- | ---------- | ---------------- | ------------------------------------------------------------------------------------------------------------------- |
| Header                         | R     | 1..1        |                  |                                |             |       |            |            | header           | Системна информация за съобщението                                                                                  |
| Type of sender                 | R     | 1..1        | Codeable Concept |                                |             |       |            | CL001      | sender           | Тип изпращач на съобщението                                                                                         |
| Sender Information System Name | R     | 1..1        | String           | min=1, max=255, chars=an       |             |       |            |            | senderISName     | Име и версия на информационната система, изпратила съобщението                                                      |
| Type of recipient              | R     | 1..1        | Codeable Concept |                                |             |       |            | CL001      | recipient        | Тип на получател на съобщението                                                                                     |
| Message ID                     | R     | 1..1        | UUID             | min=36, max=36                 |             |       |            |            | messageId        | Уникален идентификатор на съобщението - трябва да бъде ново UUID генерирано към момента на изпращане на съобщението |
| Type of message                | R     | 1..1        | String           | min=4, max=4, chars=an         |             |       |            |            | messageType      | Тип на съобщението                                                                                                  |
| Preparation Timestamp          | R     | 1..1        | Date and Time    | YYYY-MM-DDhh:mm:ss[+\\|-]hh:mm |             |       |            |            | createdOn        | Дата и час на изготвяне на съобщението по ISO 8601 в локално време с часова зона                                    |
| Contents                       | R     | 1..1        |                  |                                |             |       |            |            | contents         | Съдържание на съобщението                                                                                           |
| Household Members              | R     | 1..n        |                  |                                |             |       |            |            | householdMembers | Лица от домакинството                                                                                               |
| Identifier Type                | R     | 1..1        | Codeable Concept |                                |             | RL002 |            | CL002      | identifierType   | Вид идентификатор                                                                                                   |
| Identifier                     | R     | 1..1        | String           |                                |             | RL001 |            |            | identifier       | ЕГН / ЛНЧ                                                                                                           |

---

## E006 Резултат от проверка на домакинство

| Name                           | R/C/O | Cardinality | Data types       | Constraint                      | Fixed Value | Rules | Conditions | Code Lists | Field Name / Tag | Description                                                                      |
| ------------------------------ | ----- | ----------- | ---------------- | ------------------------------- | ----------- | ----- | ---------- | ---------- | ---------------- | -------------------------------------------------------------------------------- |
| Header                         | R     | 1..1        | ---              |                                 |             |       |            |            | header           | Системна информация за съобщението                                               |
| Type of sender                 | R     | 1..1        | Codeable Concept |                                 |             |       |            | CL001      | sender           | Тип изпращач на съобщението                                                      |
| Sender Information System Name | R     | 1..1        | String           | min=1, max=255, chars=an        |             |       |            |            | senderISName     | Име и версия на информационната система, изпратила съобщението                   |
| Type of recipient              | R     | 1..1        | Codeable Concept |                                 |             |       |            | CL001      | recipient        | Тип на получател на съобщението                                                  |
| Message ID                     | R     | 1..1        | UUID             | min=36, max=36                  |             |       |            |            | messageId        | Уникален идентификатор на текущото съобщение                                     |
| Type of message                | R     | 1..1        | String           | min=4, max=4, chars=an          |             |       |            |            | messageType      | Тип на съобщението                                                               |
| Preparation Timestamp          | R     | 1..1        | Date and Time    | YYYY-MM-DDhh:mm:ss[+\\|-]hh:mm  |             |       |            |            | createdOn        | Дата и час на изготвяне на съобщението по ISO 8601 в локално време с часова зона |
| Contents                       | R     | 1..1        | ---              |                                 |             |       |            |            | contents         | Съдържание на съобщението                                                        |
| Household Members              | R     | 1..n        |                  |                                 |             |       |            |            | householdMembers | Лица от домакинството                                                            |
| Identifier Type                | R     | 1..1        | Codeable Concept |                                 |             | RL002 |            | CL002      | identifierType   | Вид идентификатор                                                                |
| Identifier                     | R     | 1..1        | String           |                                 |             | RL001 |            |            | identifier       | ЕГН                                                                              |
| Is Deceased                    | R     | 1..1        | Boolean          |                                 |             |       |            |            | isDeceased       | Дали лицето е починало                                                           |
| Current Address             | R     | 1..1        |                  |                                 |             |       |            |            | currentAddress   | Настоящ адрес на лицето                                                          |
| Country                     | R     | 1..1        | String           | ISO 3166-1 alpha-2 country code |             |       |            |            | country          | Държава по настоящ адрес                                                         |
| EKATTE                      | C     | 1..1        | String           | min=5, max=5, chars=n           |             |       | CDX02      |            | ekatte           | Код по ЕКАТТЕ на населено място по настоящ адрес на лицето                       |
| Localization unit           | O     | 1..1        | String           | min=0, max=255, chars=an        |             |       |            |            | localizationUnit | Име на локализационна единица по настоящ адрес на лицето                         |
| Number                      | O     | 1..1        | String           | min=0, max=5, chars=an          |             |       |            |            | number           | Номер на блок / локализационна единица по настоящ адрес на лицето                |
| Entrance                    | O     | 1..1        | String           | min=0, max=5, chars=an          |             |       |            |            | entrance         | Вход по настоящ адрес на лицето                                                  |
| Floor                       | O     | 1..1        | String           | min=0, max=5, chars=an          |             |       |            |            | floor            | Етаж по настоящ адрес на лицето                                                  |
| Appartment                  | O     | 1..1        | String           | min=0, max=5, chars=an          |             |       |            |            | appartment       | Апартамент по настоящ адрес на лицето                                            |

---

## E007 Заявка за проверка на енергийни характеристики на жилище

| Name                           | R/C/O | Cardinality | Data types       | Constraint                      | Fixed Value | Rules | Conditions | Code Lists | Field Name / Tag  | Description                                                                      |
| ------------------------------ | ----- | ----------- | ---------------- | ------------------------------- | ----------- | ----- | ---------- | ---------- | ----------------- | -------------------------------------------------------------------------------- |
| Header                         | R     | 1..1        | ---              |                                 |             |       |            |            | header            | Системна информация за съобщението                                               |
| Type of sender                 | R     | 1..1        | Codeable Concept |                                 |             |       |            | CL001      | sender            | Тип изпращач на съобщението                                                      |
| Sender Information System Name | R     | 1..1        | String           | min=1, max=255, chars=an        |             |       |            |            | senderISName      | Име и версия на информационната система, изпратила съобщението                   |
| Type of recipient              | R     | 1..1        | Codeable Concept |                                 |             |       |            | CL001      | recipient         | Тип на получател на съобщението                                                  |
| Message ID                     | R     | 1..1        | UUID             | min=36, max=36                  |             |       |            |            | messageId         | Уникален идентификатор на текущото съобщение                                     |
| Type of message                | R     | 1..1        | String           | min=4, max=4, chars=an          |             |       |            |            | messageType       | Тип на съобщението                                                               |
| Preparation Timestamp          | R     | 1..1        | Date and Time    | YYYY-MM-DDhh:mm:ss[+\\|-]hh:mm  |             |       |            |            | createdOn         | Дата и час на изготвяне на съобщението по ISO 8601 в локално време с часова зона |
| Contents                       | R     | 1..1        | ---              |                                 |             |       |            |            | contents          | Съдържание на съобщението                                                        |
| Building Type               | R     | 1..1        | Codeable Concept |                                 |             |       |            | CL003      | buildingType      | Тип на сградата                                                                  |
| Certificate Number          | O     | 1..1        | String           | min=0, max=50, chars=an         |             |       |            |            | certificateNumber | Номер на сертификат за енергийни характеристики                                  |
| Address                        | R     | 1..1        |                  |                                 |             |       |            |            | Address           | Адрес                                                                            |
| Country                        | R     | 1..1        | String           | ISO 3166-1 alpha-2 country code |             |       |            |            | country           | Държава                                                                          |
| EKATTE                         | C     | 1..1        | String           | min=5, max=5, chars=n           |             |       | CDX02      |            | ekatte            | Код по ЕКАТТЕ на населено място                                                  |
| Localization unit              | O     | 1..1        | String           | min=0, max=255, chars=an        |             |       |            |            | localizationUnit  | Име на локализационна единица                                                    |
| Number                         | O     | 1..1        | String           | min=0, max=5, chars=an          |             |       |            |            | number            | Номер на блок / локализационна единица                                           |
| Entrance                       | O     | 1..1        | String           | min=0, max=5, chars=an          |             |       |            |            | entrance          | Вход                                                                             |
| Floor                          | O     | 1..1        | String           | min=0, max=5, chars=an          |             |       |            |            | floor             | Етаж                                                                             |
| Appartment                     | O     | 1..1        | String           | min=0, max=5, chars=an          |             |       |            |            | appartment        | Апартамент                                                                       |

---

## E008 Резултат от проверка на енергийни характеристики на жилище

| Name                           | R/C/O | Cardinality | Data types       | Constraint                     | Fixed Value | Rules | Conditions | Code Lists | Field Name / Tag | Description                                                                            |
| ------------------------------ | ----- | ----------- | ---------------- | ------------------------------ | ----------- | ----- | ---------- | ---------- | ---------------- | -------------------------------------------------------------------------------------- |
| Header                         | R     | 1..1        | ---              |                                |             |       |            |            | header           | Системна информация за съобщението                                                     |
| Type of sender                 | R     | 1..1        | Codeable Concept |                                |             |       |            | CL001      | sender           | Тип изпращач на съобщението                                                            |
| Sender Information System Name | R     | 1..1        | String           | min=1, max=255, chars=an       |             |       |            |            | senderISName     | Име и версия на информационната система, изпратила съобщението                         |
| Type of recipient              | R     | 1..1        | Codeable Concept |                                |             |       |            | CL001      | recipient        | Тип на получател на съобщението                                                        |
| Message ID                     | R     | 1..1        | UUID             | min=36, max=36                 |             |       |            |            | messageId        | Уникален идентификатор на текущото съобщение                                           |
| Type of message                | R     | 1..1        | String           | min=4, max=4, chars=an         |             |       |            |            | messageType      | Тип на съобщението                                                                     |
| Preparation Timestamp          | R     | 1..1        | Date and Time    | YYYY-MM-DDhh:mm:ss[+\\|-]hh:mm |             |       |            |            | createdOn        | Дата и час на изготвяне на съобщението по ISO 8601 в локално време с часова зона       |
| Contents                       | R     | 1..1        | ---              |                                |             |       |            |            | contents         | Съдържание на съобщението                                                              |
| Value Calculated            | R     | 1..1        | Boolean          |                                |             |       |            |            | valueCalculated  | Изчислена е стойност за специфичния годишен разход на първична енергия на единица площ |
| Value                       | C     | 1..1        | Decimal          |                                |             |       | CDX03      |            | value            | Стойност за специфичния годишен разход на първична енергия на единица площ             |

---

## E009 Заявка за проверка за отпуснато помощно средство/медицинско изделие от НЗОК

| Name                           | R/C/O | Cardinality | Data types       | Constraint                     | Fixed Value | Rules | Conditions | Code Lists | Field Name / Tag | Description                                                                                                         |
| ------------------------------ | ----- | ----------- | ---------------- | ------------------------------ | ----------- | ----- | ---------- | ---------- | ---------------- | ------------------------------------------------------------------------------------------------------------------- |
| Header                         | R     | 1..1        |                  |                                |             |       |            |            | header           | Системна информация за съобщението                                                                                  |
| Type of sender                 | R     | 1..1        | Codeable Concept |                                |             |       |            | CL001      | sender           | Тип изпращач на съобщението                                                                                         |
| Sender Information System Name | R     | 1..1        | String           | min=1, max=255, chars=an       |             |       |            |            | senderISName     | Име и версия на информационната система, изпратила съобщението                                                      |
| Type of recipient              | R     | 1..1        | Codeable Concept |                                |             |       |            | CL001      | recipient        | Тип на получател на съобщението                                                                                     |
| Message ID                     | R     | 1..1        | UUID             | min=36, max=36                 |             |       |            |            | messageId        | Уникален идентификатор на съобщението - трябва да бъде ново UUID генерирано към момента на изпращане на съобщението |
| Type of message                | R     | 1..1        | String           | min=4, max=4, chars=an         |             |       |            |            | messageType      | Тип на съобщението                                                                                                  |
| Preparation Timestamp          | R     | 1..1        | Date and Time    | YYYY-MM-DDhh:mm:ss[+\\|-]hh:mm |             |       |            |            | createdOn        | Дата и час на изготвяне на съобщението по ISO 8601 в локално време с часова зона                                    |
| Contents                       | R     | 1..1        |                  |                                |             |       |            |            | contents         | Съдържание на съобщението                                                                                           |
| Identifier Type             | R     | 1..1        | Codeable Concept |                                |             |       |            | CL002      | identifierType   | Вид идентификатор                                                                                                   |
| Identifier                  | R     | 1..1        | String           |                                |             | RL001 |            |            | identifier       | ЕГН/ЛНЧ/ЛН                                                                                                          |
| Aids                        | O     | 1..n        | Codeable Concept |                                |             |       |            | CL004      | aids             | Помощни средства                                                                                                    |
| Medical devices             | C     | 1..n        | Codeable Concept |                                |             |       | CDX04      | CL005      | medicalDevices   | Медицински изделия                                                                                                  |

---

## E010 Резултат от проверка за отпуснато помощно средство/медицинско изделие от НЗОК

| Name                           | R/C/O | Cardinality | Data types       | Constraint                     | Fixed Value | Rules | Conditions | Code Lists | Field Name / Tag  | Description                                                                                                         |
| ------------------------------ | ----- | ----------- | ---------------- | ------------------------------ | ----------- | ----- | ---------- | ---------- | ----------------- | ------------------------------------------------------------------------------------------------------------------- |
| Header                         | R     | 1..1        |                  |                                |             |       |            |            | header            | Системна информация за съобщението                                                                                  |
| Type of sender                 | R     | 1..1        | Codeable Concept |                                |             |       |            | CL001      | sender            | Тип изпращач на съобщението                                                                                         |
| Sender Information System Name | R     | 1..1        | String           | min=1, max=255, chars=an       |             |       |            |            | senderISName      | Име и версия на информационната система, изпратила съобщението                                                      |
| Type of recipient              | R     | 1..1        | Codeable Concept |                                |             |       |            | CL001      | recipient         | Тип на получател на съобщението                                                                                     |
| Message ID                     | R     | 1..1        | UUID             | min=36, max=36                 |             |       |            |            | messageId         | Уникален идентификатор на съобщението - трябва да бъде ново UUID генерирано към момента на изпращане на съобщението |
| Type of message                | R     | 1..1        | String           | min=4, max=4, chars=an         |             |       |            |            | messageType       | Тип на съобщението                                                                                                  |
| Preparation Timestamp          | R     | 1..1        | Date and Time    | YYYY-MM-DDhh:mm:ss[+\\|-]hh:mm |             |       |            |            | createdOn         | Дата и час на изготвяне на съобщението по ISO 8601 в локално време с часова зона                                    |
| Contents                       | R     | 1..1        |                  |                                |             |       |            |            | contents          | Съдържание на съобщението                                                                                           |
| Identifier Type             | R     | 1..1        | Codeable Concept |                                |             |       |            | CL002      | identifierType    | Вид идентификатор                                                                                                   |
| Identifier                  | R     | 1..1        | String           |                                |             | RL001 |            |            | identifier        | ЕГН/ЛНЧ/ЛН                                                                                                          |
| Aids                           | C     | 1..n        |                  |                                |             |       | CDX05      |            | aids              | Помощни средства                                                                                                    |
| Aid Code                       | R     | 1..1        | Codeable Concept |                                |             |       |            | CL004      | aidCode           | Код на помощното средство                                                                                           |
| Is Provided                    | R     | 1..1        | Boolean          |                                |             |       |            |            | isProvided        | Дали помощното средство е отпуснато                                                                                 |
| Medical Devices                | C     | 1..n        |                  |                                |             |       | CDX06      |            | medicalDevices    | Медицински изделия                                                                                                  |
| Medical Device Code            | R     | 1..1        | Codeable Concept |                                |             |       |            | CL005      | medicalDeviceCode | Код на медицинското изделие                                                                                         |
| Is Provided                    | R     | 1..1        | Boolean          |                                |             |       |            |            | isProvided        | Дали медицинското изделие е отпуснато                                                                               |

---

## E011 Заявка за проверка на титуляр на партида (отговор E096 или E098)

| Name                           | R/C/O | Cardinality | Data types       | Constraint                      | Fixed Value | Rules | Conditions | Code Lists | Field Name / Tag       | Description                                                                                                         |
| ------------------------------ | ----- | ----------- | ---------------- | ------------------------------- | ----------- | ----- | ---------- | ---------- | ---------------------- | ------------------------------------------------------------------------------------------------------------------- |
| Header                         | R     | 1..1        |                  |                                 |             |       |            |            | header                 | Системна информация за съобщението                                                                                  |
| Type of sender                 | R     | 1..1        | Codeable Concept |                                 |             |       |            | CL001      | sender                 | Тип изпращач на съобщението                                                                                         |
| Sender Information System Name | R     | 1..1        | String           | min=1, max=255, chars=an        |             |       |            |            | senderISName           | Име и версия на информационната система, изпратила съобщението                                                      |
| Type of recipient              | R     | 1..1        | Codeable Concept |                                 |             |       |            | CL001      | recipient              | Тип на получател на съобщението                                                                                     |
| Message ID                     | R     | 1..1        | UUID             | min=36, max=36                  |             |       |            |            | messageId              | Уникален идентификатор на съобщението - трябва да бъде ново UUID генерирано към момента на изпращане на съобщението |
| Type of message                | R     | 1..1        | String           | min=4, max=4, chars=an          |             |       |            |            | messageType            | Тип на съобщението                                                                                                  |
| Preparation Timestamp          | R     | 1..1        | Date and Time    | YYYY-MM-DDhh:mm:ss[+\\|-]hh:mm  |             |       |            |            | createdOn              | Дата и час на изготвяне на съобщението по ISO 8601 в локално време с часова зона                                    |
| Contents                       | R     | 1..1        |                  |                                 |             |       |            |            | contents               | Съдържание на съобщението                                                                                           |
| Address                        | R     | 1..1        |                  |                                 |             |       |            |            | Address                | Адрес                                                                                                               |
| Country                        | R     | 1..1        | String           | ISO 3166-1 alpha-2 country code |             |       |            |            | country                | Държава                                                                                                             |
| EKATTE                         | C     | 1..1        | String           | min=5, max=5, chars=n           |             |       | CDX02      |            | ekatte                 | Код по ЕКАТТЕ на населено място                                                                                     |
| Localization unit              | O     | 1..1        | String           | min=0, max=255, chars=an        |             |       |            |            | localizationUnit       | Име на локализационна единица                                                                                       |
| Number                         | O     | 1..1        | String           | min=0, max=5, chars=an          |             |       |            |            | number                 | Номер на блок / локализационна единица                                                                              |
| Entrance                       | O     | 1..1        | String           | min=0, max=5, chars=an          |             |       |            |            | entrance               | Вход                                                                                                                |
| Floor                          | O     | 1..1        | String           | min=0, max=5, chars=an          |             |       |            |            | floor                  | Етаж                                                                                                                |
| Appartment                     | O     | 1..1        | String           | min=0, max=5, chars=an          |             |       |            |            | appartment             | Апартамент                                                                                                          |
| Owner                          | R     | 1..1        |                  |                                 |             |       |            |            | owner                  | Титуляр на партида                                                                                                  |
| Identifier Type                | R     | 1..1        | Codeable Concept |                                 |             |       |            | CL002      | identifierType         | Вид идентификатор                                                                                                   |
| Identifier                     | R     | 1..1        | String           |                                 |             | RL001 |            |            | identifier             | ЕГН/ЛНЧ/ЛН                                                                                                          |
| First Name                     | R     | 1..1        | String           | min=0, max=50, chars=a          |             |       |            |            | firstName              | Собствено име                                                                                                       |
| Last Name                      | R     | 1..1        | String           | min=0, max=50, chars=a          |             |       |            |            | lastName               | Фамилия                                                                                                             |
| Point Of Measurement           | R     | 1..1        |                  |                                 |             |       |            |            | measurementPoint       | Данни за измервателна точка                                                                                         |
| Measurement Point Number       | O     | 0..1        | String           | min=0, max=50, chars=an         |             |       |            |            | measurementPointNumber | Номер на измервателна точка                                                                                         |
| Client Number                  | O     | 0..1        | String           | min=0, max=50, chars=an         |             |       |            |            | clientNumber           | Клиентски номер                                                                                                     |
| Subscriber Number              | O     | 0..1        | String           | min=0, max=50, chars=an         |             |       |            |            | subscriberNumber       | Абонатен номер                                                                                                      |

---

## E013 Резултат от заявка за проверка на титуляр на партида (отговор E096 или E098)

| Name                           | R/C/O | Cardinality | Data types       | Constraint                      | Fixed Value | Rules | Conditions | Code Lists | Field Name / Tag       | Description                                                                                                         |
| ------------------------------ | ----- | ----------- | ---------------- | ------------------------------- | ----------- | ----- | ---------- | ---------- | ---------------------- | ------------------------------------------------------------------------------------------------------------------- |
| Header                         | R     | 1..1        |                  |                                 |             |       |            |            | header                 | Системна информация за съобщението                                                                                  |
| Type of sender                 | R     | 1..1        | Codeable Concept |                                 |             |       |            | CL001      | sender                 | Тип изпращач на съобщението                                                                                         |
| Sender Information System Name | R     | 1..1        | String           | min=1, max=255, chars=an        |             |       |            |            | senderISName           | Име и версия на информационната система, изпратила съобщението                                                      |
| Type of recipient              | R     | 1..1        | Codeable Concept |                                 |             |       |            | CL001      | recipient              | Тип на получател на съобщението                                                                                     |
| Message ID                     | R     | 1..1        | UUID             | min=36, max=36                  |             |       |            |            | messageId              | Уникален идентификатор на съобщението - трябва да бъде ново UUID генерирано към момента на изпращане на съобщението |
| Type of message                | R     | 1..1        | String           | min=4, max=4, chars=an          |             |       |            |            | messageType            | Тип на съобщението                                                                                                  |
| Preparation Timestamp          | R     | 1..1        | Date and Time    | YYYY-MM-DDhh:mm:ss[+\\|-]hh:mm  |             |       |            |            | createdOn              | Дата и час на изготвяне на съобщението по ISO 8601 в локално време с часова зона                                    |
| Contents                       | R     | 1..1        |                  |                                 |             |       |            |            | contents               | Съдържание на съобщението                                                                                           |
| Operation Id                | R     | 1..1        | UUID             | min=36, max=36                  |             |       |            |            | operationId            | Идентификатор на операция                                                                                           |
| Result Code                 | R     | 1..1        | Codeable Concept |                                 |             | RL004 |            | CL006      | resultCode             | Код на резултата от проверката                                                                                      |
| Result Description          | O     | 0..1        | String           | min=0, max=500                  |             |       |            |            | resultDescription      | Допълнително пояснение към резултата от проверката                                                                  |
| Address                        | C     | 1..1        |                  |                                 |             |       | CDX08      |            | Address                | Адрес                                                                                                               |
| Country                        | R     | 1..1        | String           | ISO 3166-1 alpha-2 country code |             |       |            |            | country                | Държава                                                                                                             |
| EKATTE                         | C     | 1..1        | String           | min=5, max=5, chars=n           |             |       | CDX02      |            | ekatte                 | Код по ЕКАТТЕ на населено място                                                                                     |
| Localization unit              | O     | 1..1        | String           | min=0, max=255, chars=an        |             |       |            |            | localizationUnit       | Име на локализационна единица                                                                                       |
| Number                         | O     | 1..1        | String           | min=0, max=5, chars=an          |             |       |            |            | number                 | Номер на блок / локализационна единица                                                                              |
| Entrance                       | O     | 1..1        | String           | min=0, max=5, chars=an          |             |       |            |            | entrance               | Вход                                                                                                                |
| Floor                          | O     | 1..1        | String           | min=0, max=5, chars=an          |             |       |            |            | floor                  | Етаж                                                                                                                |
| Appartment                     | O     | 1..1        | String           | min=0, max=5, chars=an          |             |       |            |            | appartment             | Апартамент                                                                                                          |
| Owner                          | C     | 1..1        |                  |                                 |             |       | CDX08      |            | owner                  | Титуляр на партида                                                                                                  |
| Identifier Type                | R     | 1..1        | Codeable Concept |                                 |             |       |            | CL002      | identifierType         | Вид идентификатор                                                                                                   |
| Identifier                     | R     | 1..1        | String           |                                 |             | RL001 |            |            | identifier             | ЕГН/ЛНЧ/ЛН                                                                                                          |
| First Name                     | R     | 1..1        | String           | min=0, max=50, chars=a          |             |       |            |            | firstName              | Собствено име                                                                                                       |
| Last Name                      | R     | 1..1        | String           | min=0, max=50, chars=a          |             |       |            |            | lastName               | Фамилия                                                                                                             |
| Point Of Measurement           | C     | 1..1        |                  |                                 |             |       | CDX08      |            | measurementPoint       | Данни за измервателна точка                                                                                         |
| Measurement Point Number       | C     | 0..1        | String           | min=0, max=50, chars=an         |             |       | CDX09      |            | measurementPointNumber | Номер на измервателна точка                                                                                         |
| Client Number                  | C     | 0..1        | String           | min=0, max=50, chars=an         |             |       | CDX09      |            | clientNumber           | Клиентски номер                                                                                                     |
| Subscriber Number              | C     | 0..1        | String           | min=0, max=50, chars=an         |             |       | CDX09      |            | subscriberNumber       | Абонатен номер                                                                                                      |
| GPS Data                       | O     | 1..1        |                  | ISO 6709                        |             |       | CDX08      |            | gpsData                | Географски координати на електромера или обекта                                                                     |
| Latitude                       | O     | 0..1        | Decimal Degrees  | ±DD.DDDDD                       |             |       |            |            | latitude               | Географска ширина                                                                                                   |
| Longitude                      | O     | 0..1        | Decimal Degrees  | ±DD.DDDDD                       |             |       |            |            | longitude              | Географска дължина                                                                                                  |

---

## E015 Заявка за удостоверяване / прекратяване на статут

| Name                           | R/C/O | Cardinality | Data types       | Constraint                     | Fixed Value | Rules | Conditions | Code Lists | Field Name / Tag       | Description                                                                                                         |
| ------------------------------ | ----- | ----------- | ---------------- | ------------------------------ | ----------- | ----- | ---------- | ---------- | ---------------------- | ------------------------------------------------------------------------------------------------------------------- |
| Header                         | R     | 1..1        |                  |                                |             |       |            |            | header                 | Системна информация за съобщението                                                                                  |
| Type of sender                 | R     | 1..1        | Codeable Concept |                                |             |       |            | CL001      | sender                 | Тип изпращач на съобщението                                                                                         |
| Sender Information System Name | R     | 1..1        | String           | min=1, max=255, chars=an       |             |       |            |            | senderISName           | Име и версия на информационната система, изпратила съобщението                                                      |
| Type of recipient              | R     | 1..1        | Codeable Concept |                                |             |       |            | CL001      | recipient              | Тип на получател на съобщението                                                                                     |
| Message ID                     | R     | 1..1        | UUID             | min=36, max=36                 |             |       |            |            | messageId              | Уникален идентификатор на съобщението - трябва да бъде ново UUID генерирано към момента на изпращане на съобщението |
| Type of message                | R     | 1..1        | String           | min=4, max=4, chars=an         |             |       |            |            | messageType            | Тип на съобщението                                                                                                  |
| Preparation Timestamp          | R     | 1..1        | Date and Time    | YYYY-MM-DDhh:mm:ss[+\\|-]hh:mm |             |       |            |            | createdOn              | Дата и час на изготвяне на съобщението по ISO 8601 в локално време с часова зона                                    |
| Contents                       | R     | 1..1        |                  |                                |             |       |            |            | contents               | Съдържание на съобщението                                                                                           |
| Certificate number          | R     | 1..1        | String           | min=16, max=16, chars=n        |             |       |            |            | certificateNumber      | Номер на удостоверение                                                                                              |
| Certificate date            | R     | 1..1        | Date             | YYYY-MM-DD                     |             |       |            |            | certificateDate        | Дата на удостоверение                                                                                               |
| Validity date               | R     | 1..1        | Date             | YYYY-MM-DD                     |             |       |            |            | validityDate           | Дата на валидност на удостоверение                                                                                  |
| Status                      | R     | 1..1        | Codeable Concept |                                |             |       |            | CL007      | status                 | Статут на клиент                                                                                                    |
| Status state                | R     | 1..1        | Codeable Concept |                                |             |       |            | CL008      | statusState            | Състояние на статут                                                                                                 |
| Status reason               | O     | 1..1        | String           | min=0, max=255, chars=an       |             |       |            |            | statusReason           | Причина за удостоверяване / отнемане на статут                                                                      |
| Owner                          | R     | 1..1        |                  |                                |             |       |            |            | owner                  | Титуляр на партида                                                                                                  |
| Identifier Type                | R     | 1..1        | Codeable Concept |                                |             |       |            | CL002      | identifierType         | Вид идентификатор                                                                                                   |
| Identifier                     | R     | 1..1        | String           |                                |             | RL001 |            |            | identifier             | ЕГН/ЛНЧ/ЛН                                                                                                          |
| First Name                     | R     | 1..1        | String           | min=0, max=50, chars=a         |             |       |            |            | firstName              | Собствено име                                                                                                       |
| Last Name                      | R     | 1..1        | String           | min=0, max=50, chars=a         |             |       |            |            | lastName               | Фамилия                                                                                                             |
| Point Of Measurement           | R     | 1..1        |                  |                                |             |       |            |            | measurementPoint       | Данни за измервателна точка                                                                                         |
| Measurement Point Number       | O     | 0..1        | String           | min=0, max=50, chars=an        |             |       |            |            | measurementPointNumber | Номер на измервателна точка                                                                                         |
| Client Number                  | O     | 0..1        | String           | min=0, max=50, chars=an        |             |       |            |            | clientNumber           | Клиентски номер                                                                                                     |
| Subscriber Number              | O     | 0..1        | String           | min=0, max=50, chars=an        |             |       |            |            | subscriberNumber       | Абонатен номер                                                                                                      |

---

## E016 Потвърждение за удостоверен / прекратен статут

| Name                           | R/C/O | Cardinality | Data types       | Constraint                     | Fixed Value | Rules | Conditions | Code Lists | Field Name / Tag  | Description                                                                      |
| ------------------------------ | ----- | ----------- | ---------------- | ------------------------------ | ----------- | ----- | ---------- | ---------- | ----------------- | -------------------------------------------------------------------------------- |
| Header                         | R     | 1..1        | ---              |                                |             |       |            |            | header            | Системна информация за съобщението                                               |
| Type of sender                 | R     | 1..1        | Codeable Concept |                                |             |       |            | CL001      | sender            | Тип изпращач на съобщението                                                      |
| Sender Information System Name | R     | 1..1        | String           | min=1, max=255, chars=an       |             |       |            |            | senderISName      | Име и версия на информационната система, изпратила съобщението                   |
| Type of recipient              | R     | 1..1        | Codeable Concept |                                |             |       |            | CL001      | recipient         | Тип на получател на съобщението                                                  |
| Message ID                     | R     | 1..1        | UUID             | min=36, max=36                 |             |       |            |            | messageId         | Уникален идентификатор на текущото съобщение                                     |
| Type of message                | R     | 1..1        | String           | min=4, max=4, chars=an         |             |       |            |            | messageType       | Тип на съобщението                                                               |
| Preparation Timestamp          | R     | 1..1        | Date and Time    | YYYY-MM-DDhh:mm:ss[+\\|-]hh:mm |             |       |            |            | createdOn         | Дата и час на изготвяне на съобщението по ISO 8601 в локално време с часова зона |
| Contents                       | R     | 1..1        | ---              |                                |             |       |            |            | contents          | Съдържание на съобщението                                                        |
| Certificate number          | R     | 1..1        | String           | min=16, max=16, chars=n        |             |       |            |            | certificateNumber | Номер на удостоверение                                                           |
| Status                      | R     | 1..1        | Codeable Concept |                                |             |       |            | CL007      | status            | Статут на клиент                                                                 |
| Result Code                 | R     | 1..1        | Codeable Concept |                                |             | RL004 |            | CL006      | resultCode        | Код на резултата от проверката                                                   |
| Result Description          | O     | 0..1        | String           | min=0, max=500                 |             |       |            |            | resultDescription | Допълнително пояснение към резултата от проверката                               |

---

## E017 Заявка за промяна на титуляр

| Name                           | R/C/O | Cardinality | Data types       | Constraint                     | Fixed Value | Rules | Conditions | Code Lists | Field Name / Tag       | Description                                                                                                         |
| ------------------------------ | ----- | ----------- | ---------------- | ------------------------------ | ----------- | ----- | ---------- | ---------- | ---------------------- | ------------------------------------------------------------------------------------------------------------------- |
| Header                         | R     | 1..1        |                  |                                |             |       |            |            | header                 | Системна информация за съобщението                                                                                  |
| Type of sender                 | R     | 1..1        | Codeable Concept |                                |             |       |            | CL001      | sender                 | Тип изпращач на съобщението                                                                                         |
| Sender Information System Name | R     | 1..1        | String           | min=1, max=255, chars=an       |             |       |            |            | senderISName           | Име и версия на информационната система, изпратила съобщението                                                      |
| Type of recipient              | R     | 1..1        | Codeable Concept |                                |             |       |            | CL001      | recipient              | Тип на получател на съобщението                                                                                     |
| Message ID                     | R     | 1..1        | UUID             | min=36, max=36                 |             |       |            |            | messageId              | Уникален идентификатор на съобщението - трябва да бъде ново UUID генерирано към момента на изпращане на съобщението |
| Type of message                | R     | 1..1        | String           | min=4, max=4, chars=an         |             |       |            |            | messageType            | Тип на съобщението                                                                                                  |
| Preparation Timestamp          | R     | 1..1        | Date and Time    | YYYY-MM-DDhh:mm:ss[+\\|-]hh:mm |             |       |            |            | createdOn              | Дата и час на изготвяне на съобщението по ISO 8601 в локално време с часова зона                                    |
| Contents                       | R     | 1..1        |                  |                                |             |       |            |            | contents               | Съдържание на съобщението                                                                                           |
| New Owner                      | R     | 1..1        |                  |                                |             |       |            |            | newOwner               | Нов титуляр на партида                                                                                              |
| Identifier Type                | R     | 1..1        | Codeable Concept |                                |             |       |            | CL002      | identifierType         | Вид идентификатор                                                                                                   |
| Identifier                     | R     | 1..1        | String           |                                |             | RL001 |            |            | identifier             | ЕГН/ЛНЧ/ЛН                                                                                                          |
| First Name                     | R     | 1..1        | String           | min=0, max=50, chars=a         |             |       |            |            | firstName              | Собствено име                                                                                                       |
| Last Name                      | R     | 1..1        | String           | min=0, max=50, chars=a         |             |       |            |            | lastName               | Фамилия                                                                                                             |
| Point Of Measurement           | R     | 1..1        |                  |                                |             |       |            |            | measurementPoint       | Данни за измервателна точка                                                                                         |
| Measurement Point Number       | O     | 0..1        | String           | min=0, max=50, chars=an        |             |       |            |            | measurementPointNumber | Номер на измервателна точка                                                                                         |
| Client Number                  | O     | 0..1        | String           | min=0, max=50, chars=an        |             |       |            |            | clientNumber           | Клиентски номер                                                                                                     |
| Subscriber Number              | O     | 0..1        | String           | min=0, max=50, chars=an        |             |       |            |            | subscriberNumber       | Абонатен номер                                                                                                      |

---

## E018 Потвърждение за промяна на титуляр

| Name                           | R/C/O | Cardinality | Data types       | Constraint                     | Fixed Value | Rules | Conditions | Code Lists | Field Name / Tag       | Description                                                                      |
| ------------------------------ | ----- | ----------- | ---------------- | ------------------------------ | ----------- | ----- | ---------- | ---------- | ---------------------- | -------------------------------------------------------------------------------- |
| Header                         | R     | 1..1        | ---              |                                |             |       |            |            | header                 | Системна информация за съобщението                                               |
| Type of sender                 | R     | 1..1        | Codeable Concept |                                |             |       |            | CL001      | sender                 | Тип изпращач на съобщението                                                      |
| Sender Information System Name | R     | 1..1        | String           | min=1, max=255, chars=an       |             |       |            |            | senderISName           | Име и версия на информационната система, изпратила съобщението                   |
| Type of recipient              | R     | 1..1        | Codeable Concept |                                |             |       |            | CL001      | recipient              | Тип на получател на съобщението                                                  |
| Message ID                     | R     | 1..1        | UUID             | min=36, max=36                 |             |       |            |            | messageId              | Уникален идентификатор на текущото съобщение                                     |
| Type of message                | R     | 1..1        | String           | min=4, max=4, chars=an         |             |       |            |            | messageType            | Тип на съобщението                                                               |
| Preparation Timestamp          | R     | 1..1        | Date and Time    | YYYY-MM-DDhh:mm:ss[+\\|-]hh:mm |             |       |            |            | createdOn              | Дата и час на изготвяне на съобщението по ISO 8601 в локално време с часова зона |
| Contents                       | R     | 1..1        | ---              |                                |             |       |            |            | contents               | Съдържание на съобщението                                                        |
| Result Code                 | R     | 1..1        | Codeable Concept |                                |             | RL005 |            | CL006      | resultCode             | Код на резултата от проверката                                                   |
| Result Description          | O     | 0..1        | String           | min=0, max=500                 |             |       |            |            | resultDescription      | Допълнително пояснение към резултата от проверката                               |
| Point Of Measurement           | R     | 1..1        |                  |                                |             |       |            |            | measurementPoint       | Данни за измервателна точка                                                      |
| Measurement Point Number       | O     | 0..1        | String           | min=0, max=50, chars=an        |             |       |            |            | measurementPointNumber | Номер на измервателна точка                                                      |
| Client Number                  | O     | 0..1        | String           | min=0, max=50, chars=an        |             |       |            |            | clientNumber           | Клиентски номер                                                                  |
| Subscriber Number              | O     | 0..1        | String           | min=0, max=50, chars=an        |             |       |            |            | subscriberNumber       | Абонатен номер                                                                   |

---

## E096 Успешно получаване на заявка (използва се за потвърждение на получаване на заявка при асинхронен процес)

| Name                           | R/C/O | Cardinality | Data types       | Constraint                     | Fixed Value | Rules | Conditions | Code Lists | Field Name / Tag | Description                                                                                  |
| ------------------------------ | ----- | ----------- | ---------------- | ------------------------------ | ----------- | ----- | ---------- | ---------- | ---------------- | -------------------------------------------------------------------------------------------- |
| Header                         | R     | 1..1        |                  |                                |             |       |            |            | header           | Системна информация за съобщението                                                           |
| Type of sender                 | R     | 1..1        | Codeable Concept |                                |             |       |            | CL001      | sender           | Тип изпращач на съобщението                                                                  |
| Sender Information System Name | R     | 1..1        | String           | min=1, max=255, chars=an       |             |       |            |            | senderISName     | Име и версия на информационната система, изпратила съобщението                               |
| Type of recipient              | R     | 1..1        | Codeable Concept |                                |             |       |            | CL001      | recipient        | Тип на получател на съобщението                                                              |
| Message ID                     | R     | 1..1        | UUID             | min=36, max=36                 |             |       |            |            | messageId        | Уникален идентификатор на текущото съобщение                                                 |
| Type of message                | R     | 1..1        | String           | min=4, max=4, chars=an         |             |       |            |            | messageType      | Тип на съобщението                                                                           |
| Preparation Timestamp          | R     | 1..1        | Date and Time    | YYYY-MM-DDhh:mm:ss[+\\|-]hh:mm |             |       |            |            | createdOn        | Дата и час на изготвяне на съобщението по ISO 8601 в локално време с часова зона             |
| Contents                       | R     | 1..1        |                  |                                |             |       |            |            | contents         | Съдържание на съобщението                                                                    |
| Operation Id                | R     | 1..1        | UUID             | min=36, max=36                 |             |       |            |            | operationId      | Идентификатор на операция                                                                    |
| Operation started on           | R     | 1..1        | Date and Time    | YYYY-MM-DDhh:mm:ss[+\\|-]hh:mm |             |       |            |            | startedOn        | Дата и час на започване на асинхронната операция по ISO 8601 в локално време с часова зона   |
| Operation completed on         | C     | 1..1        | Date and Time    | YYYY-MM-DDhh:mm:ss[+\\|-]hh:mm |             |       | CDX07      |            | completedOn      | Дата и час на приключване на асинхронната операция по ISO 8601 в локално време с часова зона |

---

## E098 Грешка при обработка на заявка

| Name                           | R/C/O | Cardinality | Data types       | Constraint                     | Fixed Value | Rules | Conditions | Code Lists | Field Name / Tag | Description                                                                      |
| ------------------------------ | ----- | ----------- | ---------------- | ------------------------------ | ----------- | ----- | ---------- | ---------- | ---------------- | -------------------------------------------------------------------------------- |
| Header                         | R     | 1..1        |                  |                                |             |       |            |            | header           | Системна информация за съобщението                                               |
| Type of sender                 | R     | 1..1        | Codeable Concept |                                |             |       |            | CL001      | sender           | Тип изпращач на съобщението                                                      |
| Sender Information System Name | R     | 1..1        | String           | min=1, max=255, chars=an       |             |       |            |            | senderISName     | Име и версия на информационната система, изпратила съобщението                   |
| Type of recipient              | R     | 1..1        | Codeable Concept |                                |             |       |            | CL001      | recipient        | Тип на получател на съобщението                                                  |
| Message ID                     | R     | 1..1        | UUID             | min=36, max=36                 |             |       |            |            | messageId        | Уникален идентификатор на текущото съобщение                                     |
| Type of message                | R     | 1..1        | String           | min=4, max=4, chars=an         |             |       |            |            | messageType      | Тип на съобщението                                                               |
| Preparation Timestamp          | R     | 1..1        | Date and Time    | YYYY-MM-DDhh:mm:ss[+\\|-]hh:mm |             |       |            |            | createdOn        | Дата и час на изготвяне на съобщението по ISO 8601 в локално време с часова зона |
| Contents                       | R     | 1..1        |                  |                                |             |       |            |            | contents         | Съдържание на съобщението                                                        |
| Errors                         | R     | 1..*        |                  |                                |             |       |            |            | errors           | Специфични данни за грешките                                                     |
| Error type                     | R     | 1..1        | Codeable Concept |                                |             |       |            | CL099      | type             | Специфичен код на грешката                                                       |
| Reason for the error           | O     | 0..1        | String           | min=1, max=255                 |             |       |            |            | reason           | Текст, описващ причината за възникване на грешката                               |
| Description of the error       | O     | 0..1        | String           | max=2000                       |             |       |            |            | description      | Допълнителна информация за грешката, ако има такава необходимост                 |
| Faulty Attribute               | C     | 0..1        | String           | min=1, max=255                 |             |       | CDX01      |            | faultyAttribute  | Системно име на сгрешения параметър, ако това е типа на грешката                 |

---

## Conditions

| Condition ID | Logic |
|---|---|
| CDX01 | IF 'error.type' = 'E002' THEN 'error.faultyAttribute'.required = 'R' ELSE 'error.faultyAttribute' IS null |
| CDX02 | IF 'currentAddress.country' = 'BG' THEN 'currentAddress.ekatte'.required = 'R' ELSE 'currentAddress.ekatte' IS null |
| CDX03 | IF 'valueCalculated' = TRUE THEN 'value'.required = 'R' ELSE 'value' IS null |
| CDX04 | IF 'aids' = IS null THEN 'medicalDevices'.required = 'R' ELSE 'medicalDevices'.required = 'O' |
| CDX05 | IF Request.'aids' = IS NOT null THEN Response.'aids'.required = 'R' ELSE 'aids' IS null |
| CDX06 | IF Request.'medicalDevices' = IS NOT null THEN Response.'medicalDevices'.required = 'R' ELSE 'medicalDevices' IS null |
| CDX07 | IF Asynchronous operation is completed THEN 'completedOn'.required = 'R' ELSE 'completedOn' IS null |
| CDX08 | IF 'resultCode' = DF THEN 'address'.required = 'R' AND 'owner'.required = 'R' AND 'measurementPoint'.required = 'R' ELSE 'address' IS null AND 'owner' IS null AND 'measurementPoint' IS null |
| CDX09 | measurementPointNumber' IS NOT null OR 'clientNumber' IS NOT null OR 'subscriberNumber' IS NOT null |

---

## Rules

| Rule ID | Definition                                                                                                                                                                                                                                                                                                                          | Source | Error Code | Since  |
| ------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ | ---------- | ------ |
| RL001   | Идентификаторът ще бъде проверен в зависимост от неговия тип (посочен в поле identifierType) както следва:  1. за тип 1 (ЕГН) - стандартни проверки за валидност от съответния регистър 2. за тип 2 (ЛНЧ) - стандартни проверки за валидност от съответния регистър  Всички останали типове не подлежат на автоматизирана проверка. | ---    | E002       | v1.0.0 |
| RL002   | Членове на домакинство с тип на идентификатора ЕГН се подават към ГРАО, а с ЛНЧ към МВР                                                                                                                                                                                                                                             | ---    | ---        | v1.0.0 |
| RL003   | Могат да бъдат използвани само стойности от номенклатура CL006 със стойност на полето 'Participant Type' = 2                                                                                                                                                                                                                        | ---    | E002       | v1.0.0 |
| RL004   | Могат да бъдат използвани само стойности от номенклатура CL006 със стойност на полето 'Participant Type' = 8                                                                                                                                                                                                                        | ---    | E002       | v1.0.0 |
| RL005   | Могат да бъдат използвани само стойности от номенклатура CL006 със стойност на полето 'Participant Type' = 1                                                                                                                                                                                                                        | ---    | E002       | v1.0.0 |
