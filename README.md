## Легенда
Как вы уже видели, некоторые проекты требуют для своей работы совместимости с текущей поддерживаемой версией языка. Но при этом есть большое желание использовать новейшие возможности ES. И для этого есть специальный инструмент, который позволяет осуществлять компиляцию кода на ES6+ в поддерживаемые на данный момент возможности - Babel. Поэтому вы приняли следующее решение: писать всё на новейшей версии языка и с помощью Babel обеспечить себе наибольшее количество пользователей.

## Описание
Ваша задача подключить Babel к проекту и настроить сборку с его использованием.

1. Установите Babel (npm install --save-dev @babel/core @babel/cli @babel/preset-env).

2. Установите CoreJS (npm install core-js@3).

3. Настройте скрипт запуска build для сборки с помощью npm. Для этого в секции scripts файла package.json пропишите:

        {
            ...
            "scripts": {
                ...
                "build": "babel src -d dist"
                ...
            }
        }

4. Создайте конфиг .babelrc и пропишите @babel/preset-env:
        {
        "presets": [
            [
            "@babel/preset-env",
            {
                "useBuiltIns": "usage",
                "corejs": 3
            }
            ]
        ]
        }
5. Создайте файл src/app.js со следующим содержимым:
    const characters = [
    {name: 'мечник', health: 10},
    {name: 'маг', health: 100},
    {name: 'маг', health: 0},
    {name: 'лучник', health: 0},
    ];

    const alive = characters.filter(item => item.health > 0);
Удостоверьтесь, что проект собирается, если в консоли запустить команду npm run build, и в каталоге dist формируется преобразованный Babel код.

Добавьте каталог dist в .gitignore.