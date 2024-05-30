### **Настройка окружения для работы со смарт контрактами**

- Установить npm
(sudo apt install npm || sudo brew install npm)
- Существуют разные фреймворки для создания, тестирования и развертывания смарт контрактов на Ethereum <**Hardhat**, **Truffle, Embark, Brownie (Для Python)>**

---

**Нам необходимо использовать Locklift поэтому установим его:**

```bash
npm install --save-dev locklift
```

**Установка Node JS (В конце команды я использую Bash так у меня стоит fish)**

- Есть конфликт который я нашел при установке Node через nvm. думаю это свзяанно с тем что я использую fish так как ошибка указывала на это. Поэтому будем устанавливать Node через fnm.

```bash
curl -fsSL https://fnm.vercel.app/install | bash
```

**Инициализируем проект:**

```bash
npx locklift init -f
```

**Build проекта:**

```bash
npx locklift build
```

**Начнем c определения контракта:**

- Smart Contract - это алгоритм который следит за условиями соблюдения сделки в блокчейне. То есть каждый контракт состоит из кода содержащего определенные условия при выполнении которых будет достигнут заранее известный результат. 
(К примеру я пропишу в контракте что за 7 USDT я получу 1 TON)

**Установка Evernode Simple Emulator** 

- Evernode Simple Emulator (SE) — это локальный экземпляр платформы Evernode, который разработчик может запустить на своем компьютере одним щелчком мыши для локального тестирования приложений.

```bash
npm install -g everdev
```

Необходимо иметь Docker чтоб выполнить команду так как на данный момент Evernode SE существует только в Docker образе

```bash
everdev se start

everdev se stop
```

Тестирование выполняем по иструкции которое находится в гитхабе

```bash
npx locklift test --network local
```

Так же по условию задания необходимо использовать locklift-deploy

```bash
npm install --save-dev locklift @broxus/locklift-deploy
```

---

### **Проблемы и ошибки**

- Ошибка сборки проекта была связанна с конфиг файлом locklift.config.ts в самом файле указал неправльно <externalContractsArttifacts> решил путем добавления библтотек после этого проект стал нормально собираться и работать
- В файле market.test.ts я добавил деплой Market контракта и Collection ошибки были с адресами owner так как не было понятно как их нужно добавить в контракт нужные типы параметров компилятор постоянно ругался на передоваемы типы. Так же есть файл deplou.test.ts там я просто тестировал деплой контрактов и смотрел как это все происходит.
- Ошибка при деплое контракта Market была в неправильных параметров которые были переданны контракту решилось все путем присвоения toString()
- Ошибка при тестировании: Accept tokens and mint NFTs так и не успел решить эту ошибку так как потратил кучу времени чтоб понять какие типы параметров должны быть не всегда понятно где все это смотреть

## Итог:

Задача была выполнена не полностью. Я бы даже сказал сильно не полность. :( так как было много вопросов и мало времени чтоб найти на них ответы чтоб была какая-то ясность. Только под конец срока я начал нормально понимать что и как передается за исключением типов данных которые иногда было не понятно от куда берутся.