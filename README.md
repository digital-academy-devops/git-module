# Модуль 2. Git

Целью данного модуля является знакомство с базовыми процессами использования Git и [GitHub](https://github.com), а также с некоторыми стандартными форматами данных и утилитами. 

В ходе выполнения этого практического задания, мы рассмотрим:
- Создание репозитория
- Создание и объединение веток
- Создание запроса на объединение (pull request)
- Разрешение конфликта
- Добавление и удаление тэгов
- Создание релиза
- `.gitignore` и стандартные файлы метаданных GitHub (`README`, `CODEOWNERS`)
- Добавление pre-commit хука
- Изучение синтаксиса Markdown
- Изучение форматов представления данных YAML и JSON, а также утилит для работы с ними
- Изучение стандартных средств автоматизации на примере Makefile

## Предварительная настройка

1. [Установите клиент Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) на свой компьютер. 
   
    Как упоминалось ранее, для выполнения практических заданий предпочтительней использовать Unix-подобную операционную систему (Linux, MacOS X), т.к., в подавляющем большинстве случаев, именно они используются в реальной практике работы DevOps-инженеров. 
    Если сейчас ваша основная ОС - Windows, рекомендуется использовать один из следующих вариантов:
      - Использовать [GitBash](https://gitforwindows.org)
        
        Для установки дополнительных утилит для использования их в GitBach, воспользуйтесь [Scoop](https://scoop.sh/) (необходим [PowerShell](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.)).
      - [установить виртуальную машину](https://ubuntu.com/tutorials/how-to-run-ubuntu-desktop-on-a-virtual-machine-using-virtualbox#1-overview) с Ubuntu в Virtual box.
1. Выполните шаги для минимальной конфигурации клиента Git.
1. Создайте нового пользователя [GitHub](https://github.com) или используйте уже имеющийся у вас аккаунт.
    
    > **На заметку**
    >
    > При регистрации GitHub, требует указать уникальный email. Если вы хотите зарегистрировать несколько учетных записей Github на один email (например завести отдельный аккаунт для выполнения заданий этого курса), вы можете использовать следующие особенности **некоторых** популярных email серверов/сервисов, в частности Gmail:
    > - Суффиксы после `+` в адресах игнорируются при доставке писем, таким образом все следующие адреса будут доствлены на `user@gmail.com`:
    >   - user+1@gmail.com
    >   - user+suffix@gmail.com
    >   - user+some+longer+suffix@gmail.com
    >   - user+some-longer-suffix-with-dashes@gmail.com
    > - Символ `.` не учитывается при формировании адреса назначения. Т.е. `first.last@gmail.com` будет интерпретировано как `firstlast@gmail.com`.
1. Создайте новый private репозиторий .
1. Добавьте пользователя [@digital-academy-devops](https://github.com/digital-academy-devops) в список соавторов - `Settings / Collaborators / Add People`.

## Задание

В качестве "кода" для данного задания, предлагаю описать при помощи YAML ваше резюме. 
В будущем, возможно, будет полезным поддерживать эту информацию в актуальном состоянии и, на её основе, анализировать собственный прогресс а также иметь возможность быстро сгенерировать готовое резюме для отправки работодателям.

1. Для созданного GitHub репозитория, инициализируйте локальный репозиторий любым удобным способом.
1. Для работы над первым релизом создайте набор задач для первого релиза (вкладка `Issues`) с кратким описанием задачи и минимально необходимыми деталями по реализации, например:
   - Добавление шаблона YAML файла с резюме с готовой структурой
   - Наполнение файла текущей актуальной информацией
   - Добавление описания репозитория и т.д.
1. Cоздайте ветки для первоначального набора задач
1. Поэтапно выполняйте задачи и объединяйте изменения в основную ветку разработки через Pull request (см. [Помощь](#помощь))
1. Создайте первый релиз
1. Создайте набор задач по автоматизации:
   - Проверки корректности формата файла резюме 
   - Поиска и группировки данных резюме, например: 
     - "Вывод всех навыков с уровнем владения medium"
     - "Вывод всех программ на которых я прохожу обучение в данный момент" и т.п.
   - Конвертации YAML в JSON, при этом JSON не должен попадать под контроль версий и добавляться в репозиторий.
    
    
### Рекомендации
- Для работы используйте любой удобный текстовый редактор или IDE. 
  
  Если IDE поддерживает работу с Git, можете использовать её, но помните, что история изменений основной ветки должна сохраняться в чистоте от лишних коммитов. Это не означает что вы должны реже сохранять изменения в локальном репозитории, а совсем наоброт!
  
  Перед объединением, используйте механизмы группировки коммитов в feature ветках.
- Документируйте код при помощи комментариев.
- Документируйте репозиторий в целом при помощи [Markdown](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax). В качестве примера, используйте [исходники данного файла](https://github.com/digital-academy-devops/git-module/blob/main/README.md?plain=1).
- Для реализации автоматизации, используйте [yq](https://mikefarah.gitbook.io/yq/) или [jq](https://stedolan.github.io/jq/) для работы с данными и [Bash-скрипты](https://www.redhat.com/sysadmin/learn-bash-scripting), [Taskfile](https://taskfile.dev) или [make](https://www.gnu.org/software/make/) ([tutorial](https://www.opensourceforu.com/2012/06/gnu-make-in-detail-for-beginners/)) для автоматизации повторяющихся действий.
- Для автоматической валидации используйте [pre-commit framework](https://pre-commit.com).
- Если вы хотите в дальнейшем иметь возможноть сгенерировать на основе YAML документ резюме, например в PDF или HTML, изучите готовые open-source для решения этой задачи. 
  
  [Например](https://www.google.com/search?q=yaml+cv):
  - https://github.com/haath/yaml-cv
  - https://github.com/notsag/yaml-resume

  Либо напишите собственный код способный сделать это ;) 
  
  В случае, если вы решите использовать готовые решения, для экономии времени, описывайте резюме используя структуру сразу подходящую для выбранного готового решения.

### Помощь
Для получения комментариев к вашему коду, создавайте `Pull request`/`Pull request Draft` для ваших изменений и добавляйте [@digital-academy-devops](https://github.com/digital-academy-devops) в ревьюверы. Если вы уверены в верности выбранных решений, можете применять Pull request без ожидания подтверждения, в дальнейшем они будут отсмотрены и, при необходимости, прокомментированы.
