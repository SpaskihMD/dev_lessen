Команда	       Что делает
git init	   Инициализировать репозиторий
git add .	   Добавить файлы для следующего коммита (если в конеце добавить точку то выберет все файлы)
        . - все файлы
        или надо добавить файлы просто пишем путь к файлам
git config --global user.name "Tvoe Imya"   Говорим git кто делает изменения
git commit	   Зафиксировать изменения    git commit -m "сообщение к комиту"
git push	   Отправить коммиты в репозиторий
git pull	   Забрать изменения из репозитория




git config --global user.email "mihail@mail.ru"   -мой email
git config --global user.name "Mihail"            -мое имя
git commit -m "New"
git config --global --list                        -проверка что все сохранилось


команды от GitHub
echo "# dev_lessen" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/SpaskihMD/dev_lessen.git
git push -u origin main