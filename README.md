# Проект: CI (Continuous Integration) с GitHub Actions

Този проект използва GitHub Actions, за да осигури автоматично build-ване и тестване на Node.js приложението при всяка промяна в `main` бранча и при всяка Pull Request към него.

## Съдържание
1. [Обща информация](#обща-информация)
2. [Работа с CI](#работа-с-ci)
3. [Заключение](#заключение)

---

## Обща информация

- **Платформа**: [GitHub Actions](https://docs.github.com/en/actions)  
- **Цел**:  
  - Автоматично да билдва приложението.  
  - Изпълнява тестове при всеки push към `main` и при Pull Request-и към `main`.  
  - Качва резултатите от тестовете като артефакт за преглед в GitHub.

---

## Какво се случва във всяка стъпка

1. **Checkout** (`actions/checkout@v4`):  
   Клонира репото в CI средата (Ubuntu машина).

2. **Use Node.js** (`actions/setup-node@v4`):  
   Настройва конкретна версия на Node.js (в момента е с примерен `node-version: 20`).

3. **Install program dependencies**:  
   Инсталира всички npm пакети от `package.json`.

4. **Start the App**:  
   Стартира приложението във фонов режим (`npm run start &`), за да може да е достъпно по време на тестовете.

5. **Run integration tests**:  
   Изпълнява тестовете и записва изхода в `test-output.log`.

6. **Upload test output**:  
   Качва `test-output.log` като артефакт в GitHub Actions, така че да може да се свали и разгледа по-късно.

---

## Работа с CI

### Промяна в кода
- При всяко `push` към `main` или `pull_request` към `main`, GitHub Actions автоматично стартира Workflow-а „Build and Test“.

### Преглеждане на резултатите
1. Отидете в таба “Actions” на вашето репо в GitHub.  
2. Изберете последния (или желания) Workflow Run, за да видите детайлните логове.

### Сваляне на артефакти
1. При завършил Build/Test, отворете съответния Run.  
2. В секцията “Artifacts” ще откриете `test-results` (съдържащ `test-output.log`), който може да се изтегли.

## Заключение
Тази конфигурация за CI (Continuous Integration) осигурява бърза обратна връзка относно качеството на кода, като автоматично билдва и тества Node.js приложението при всяка промяна в main.

За повече информация относно GitHub Actions, посетете официалната документация. Ако имате нужда от помощ при настройката или добавянето на нови стъпки, можете да се обърнете към общността на GitHub или да прегледате Node.js документацията за конкретни команди и добри практики при разработка.

Успех и приятно тестване!

