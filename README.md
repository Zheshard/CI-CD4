# Урок 4. Troubleshooting (диагностика и решение проблем в CI/CD)

### Задание: Сделать локальный шаблон CI и отдельный репозиторий с шаблонами, подключить их к своему основному репозиторию через include

Создаем файл .gitlab-ci.yml в корне основного репозитория.

Локальный шаблон CI:

      include:
         - local_ci_templates.yml

Создаем файл local_ci_templates.yml и определяем в нем шаблоны для нашего CI.

      #local_ci_templates.yml

      variables:
         CI_TEST: "Testing local CI template"

      stages:
         - build
         - test

      build:
         stage: build
         script:
            - echo "Building the project"

      test:
         stage: test
         script:
            - echo "$CI_TEST"

В файл .gitlab-ci.yml добавим строку для подключения шаблонов из отдельного репозитория.

      #Основной .gitlab-ci.yml

      include:
         - project: 'your-repo-group/your-repo-with-templates'
         file: 'local_ci_templates.yml'
