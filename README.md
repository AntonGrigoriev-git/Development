# backend and frontend

## Настройка проекта

1. Клонируйте репозиторий:
```
git clone https://github.com/ваш_репозиторий.git
```

2. Перейдите в директорию проекта, где находится `manage.py`:
```
cd ProjectFlow
```

3. Создайте виртуальное окружение:
- **Windows**:
```
python -m venv venv
```
- **macOS и Linux**:
```
python3 -m venv venv
```

4. Активируйте виртуальное окружение:
- **Windows**:
```
.\venv\Scripts\Activate
```
- **macOS и Linux**:
```
source venv/bin/activate
```

5. Убедитесь, что у вас установлен Python и pip. Установите зависимости:
```
pip install -r requirements.txt
```

6. Создайте базу данных и выполните миграции:
```
python manage.py migrate
```

7. Убедитесь, что у вас установлен Node.js и npm. Установите зависимости для фронтенда:
```
cd frontend # Перейдите в директорию с Vue.js приложением
npm install
```

8. Запустите оба сервера (Django и Vue.js) с помощью команды:
```
npm run start
```