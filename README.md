# Клуб Теха Лекций

Репозиторий с исходниками .tex конспектов лекций, читаемых в МФТИ.  

- Сами .pdf конспекты можно найти в [Google Drive](https://drive.google.com/drive/folders/1CQQHfA5_bgEhP6T0iH9Xp6xDz7D5lbIU?usp=sharing) в разделе Lectures  
- Группа ВК [vk.com/mipt_ltc](https://vk.com/mipt_ltc)


**Конспекты текущего семестра**

- 2 сем. Матан (наука) — 7 лек. 🔥
- 4 сем. Гармонический анализ — 4 лек. 
- 4 сем. Теория колец и полей — 6 лек. 🔥
- 4 сем. Базы данных (md) — 2 лек. 
- 4 сем. Введение в АД (md) — 4 лек. 🔥
- 4 сем. Мера и интеграл Лебега (наука) — 6 лек. 🔥
- 4 сем. АМВ (наука) — 6 лек. 🔥
- 4 сем. Вычислительные методы алгебры (наука) — 5 лек. 🔥
- 4 сем. Физика — 1 лек.
- 6 сем. Случайные процессы — 3 лек. 

---

## Инструкция по вкладыванию лекции 

0. Напишите в лс группы Ваш ник на гите с подписью "дайте права writer”

1. Идете на Google Drive, и смотрите есть ли там уже папка с таким же предметом, который Вы будете создавать (если название на русском, напишите нам, оно должно быть в латинице). Если его там нет, или Вам оно не нравится — пишите в сообщество и согласуете название для папки.

2. Подготовка, Вы клонируете репозиторий 

   ```$ git clone https://github.com/MIPT-Group/Lectures_Tex_Club```  

   и создаете ветку своего предмета. Ветка **ДОЛЖНА** называться в таком формате:   
   ```l/5/Subj_Name/2020_Lecturer``` , где  

   - `l` — сокращение от lecture  

   - `5` — номер семестра   

   - `Subj_Name` — название предмета (**ОБЯЗАТЕЛЬНО** без пробелов, в латинской раскладке и в таком формате) так же папка будет называться на google drive   

   - `2020_Lecturer` — текущий год и Фамилия лектора, тоже **ОБЯЗАТЕЛЬНО** в латинской раскладке  

     Note:  

     - Пример создания ветки:  
       ```$ git checkout -b l/3/Probability_and_Measure_Theory/2020_Ehrlich```  

     - Чтобы удалить ветку нужно вернуться в master и написать:   
       ```git branch --delete branch_name```,   
       если ветка была не смежена и удаление не прошло — добавьте ```-D```  
       Да, это немного длинно, но это нужно чтобы CI система компилировала только определенную папку, а не весь репозиторий.  

     - To rename a local and remote branch in git

       - Checkout to your local branch and rename it.
       
         ```$ git checkout old-name && git branch -m new-name``` 

       - Delete the old-name remote branch and push the new-name local branch.
       
         ```$ git push origin :old-name new-name``` 
         
       - Reset the upstream branch for the new-name local branch.
       
         ```$ git push origin -u new-name``` 

     - To rename dir
     
       `$ git mv old-name/ new-name`

   После этого в переходите в эту ветку и создаете в ней директорию с лекцией на пути `Lectures/3_Semester/Subj_Name/2020_Lecturer/main.tex` (главный файл **ДОЛЖЕН** называться `main.tex`)   
   (Такие ограничения  (**ДОЛЖЕН** и **ОБЯЗАТЕЛЬНО**) нужны для работы  CI системы автоматической компиляции и подгрузки конспектов на диск.)

3. ```$ git add```  

4. После этого техаетете в этой  директории, используя что Вам нравится (TexStudio/Texpad/Vim/…) и с очередным обновлением (```$ git add .``` )заливаете изменения в эту ветку  

5. Проверяете что не добавлили лишний мусор командой ```$ git status``` (если добавили, то его можно убрать из под контроля гита командой ```$ git restore --staged <file>``` )

6. Теперь коммитите изменения  ```$ git commit -m “add 5th lecture”```  

7. После этого, как все будет готово и конспект проверен –– можете сделать pul request в master (например, на сайте GitHub)    

   - Не забудьте проверить, что что код компилируется без ошибок (errors), иначе Ваш пул не одобрят          
   - Загружать нужно только .tex файлы и, возможно, картинки, не должно быть файлов типа main.pdf или main.toc (они автоматически будут игнориться благодаря .gitignore) 

 8. После этого админ проверяет, что все хорошо, и одобряет pul  

---

### Возможные проблемы с Git

1. Все названия, вроде `branch_name`,  можно оборачивать в  кавычки `“branch_name”,` если в них есть командные символы, вроде &.

2. Если merge будет ругаться на какие-то несостыковки, можно попробовать исправить ошибку, притянув изменения. А именно: Вы делаете пул изменений в master 

      ```$ git pull``` 
      
      А далее переходите обратно в ветку и обновляете ее   

      ```
        $ git checkout branch_name
        $ git pull -r origin master
      ```

      и дальше делаете push. 
      
      ```$ git push origin branch_name```


 ### Возможные причины поломки Actions:

 1. Не используйте `\include`, только `\input`  
 2. Если у вас есть изображения формата .pdf, их нужно добавлять используя суффикс -f (поскольку .pdf файлы игноряться .gitignore)   
   
    `$ git add -f images/picture.pdf`
         
    PS: Нигде больше нельзя использовать аргумент -f  
    PPS: Но не делайте `$ git add -f .`, так Вы добавите и main.pdf  
 3. Используйте только латиницу для названий всех файлов и папок (в том числе изображений).

В случае проблем хорошей идеей будет клонировать репозиторий в другую папку и в ней попробовать скомпилировать код через  

`$ pdflatex main.tex`

или запустить его в другом компиляторе (texstudio/vimtex...) и посмотреть, есть ли ошибки. Если ошибок нет, то можно проверить log actions, и, используя google, попробовать их решить, и, если этот товарищ не помог, то в лс группы.  
