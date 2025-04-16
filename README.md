## Диаграмма классов для задания Практика «Скользящий максимум»
![image](https://github.com/user-attachments/assets/f8f22490-99cc-4bda-a1b0-f580cbd9f04f)

### Описание основных сущностей

#### **1. Класс ParsingTask**
**Назначение**: Обработка и парсинг данных о слайдах и их посещениях.

**Методы**:
- ParseSlideRecords(inputLines)
  - *Вход*: строки файла slides.txt (первая - заголовок)
  - *Выход*: словарь ID слайда → SlideRecord
  - *Особенности*: 
    - Пропускает некорректные строки
    - Ожидает формат: SlideId;SlideType;UnitTitle

- ParseVisitRecords(VisitLines, availableSlides)
  - *Вход*: 
    - строки файла visits.txt (первая - заголовок)
    - словарь существующих слайдов
  - *Выход*: последовательность VisitRecord
  - *Особенности*:
    - Бросает FormatException при ошибках в данных
    - Ожидает формат: UserId;SlideId;Date;Time

- ParseSingleVisit(slidesCatalog, visitLine) (вспомогательный)
  - *Назначение*: парсинг одной строки посещения

#### **2. Класс SlideRecord**
**Назначение**: Хранение метаданных слайда.

**Свойства**:
- SlideId: int - уникальный идентификатор
- SlideType: SlideType - тип слайда
- UnitTitle: string - тема недели

**Конструктор**:
- SlideRecord(id, type, title) - создает запись о слайде

#### **3. Класс VisitRecord**
**Назначение**: Фиксация факта посещения слайда.

**Свойства**:
- UserId: int - идентификатор студента
- SlideId: int - идентификатор слайда
- DateTime: DateTime - дата и время посещения
- SlideType: SlideType - тип посещенного слайда (дублируется для быстрого доступа)

**Конструктор**:
- VisitRecord(userId, slideId, date, type) - создает запись о посещении
