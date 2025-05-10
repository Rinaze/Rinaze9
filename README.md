## Диаграмма классов для задания Практика «Чтение файла»
![image](https://github.com/user-attachments/assets/1bfda2e9-17f0-44eb-b75f-e7280d32b50c)


### Описание основных сущностей

#### 1. **ParsingTask**

**Назначение:**  
Служебный класс для парсинга (разбора) строковых данных в объекты предметной области.

**Основные методы:**
- ParseSlideRecords(IEnumerable lines):  
  Преобразует коллекцию строк в коллекцию объектов SlideRecord и возвращает их как словарь по идентификатору слайда.
- ParseVisitRecords(IEnumerable lines, IDictionary slides):  
  Преобразует коллекцию строк в коллекцию объектов VisitRecord, используя информацию о слайдах.
- ParseLineSlide(string line):  
  Преобразует одну строку в объект SlideRecord.
- ParseLineVisit(IDictionary slides, string line):  
  Преобразует одну строку в объект `VisitRecord`, используя информацию о слайдах.

#### 2. **SlideRecord**

**Назначение:**  
Описывает отдельный слайд курса.

**Поля:**
- int SlideId:  
  Уникальный идентификатор слайда.
- SlideType Type:  
  Тип слайда (например, упражнение, теория, тест).
- string Title:  
  Название слайда.

**Конструктор:**  
- SlideRecord(int slideId, SlideType type, string title):  
  Создаёт новый объект с указанными параметрами.

#### 3. **VisitRecord**

**Назначение:**  
Описывает факт посещения пользователем слайда.

**Поля:**
- int UserId:  
  Идентификатор пользователя.
- int SlideId:  
  Идентификатор слайда.
- DateTime DateTime:  
  Время посещения.
- SlideType SlideType:  
  Тип слайда, который был посещён.

**Конструктор:**  
- VisitRecord(int userId, int slideId, DateTime dateTime, SlideType slideType):  
  Создаёт новый объект с указанными параметрами.

#### 4. **SlideType**

**Назначение:**  
Перечисление, определяющее типы слайдов.

**Возможные значения:**
- Exercise - упражнение
- Quiz - тест/викторина
- Theory - теоретический материал
