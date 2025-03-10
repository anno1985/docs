---
title: Управление параметрами проверки кода для вашей команды
intro: 'Вы можете снизить шум для команды, ограничив уведомления, когда ваша команда получает запрос на проверку запроса на вытягивание.'
redirect_from:
  - /github/setting-up-and-managing-organizations-and-teams/managing-code-review-assignment-for-your-team
  - /organizations/organizing-members-into-teams/managing-code-review-assignment-for-your-team
product: '{% data reusables.gated-features.code-review-assignment %}'
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
topics:
  - Organizations
  - Teams
shortTitle: Code review settings
permissions: Team maintainers and organization owners can configure code review settings.
ms.openlocfilehash: eb4711251f7bebc9088ae711ba8a36dc60acba56
ms.sourcegitcommit: f638d569cd4f0dd6d0fb967818267992c0499110
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2022
ms.locfileid: '148108829'
---
## Сведения о параметрах проверки кода

{% ifversion only-notify-requested-members %} Чтобы снизить шум для вашей команды и уточнить индивидуальную ответственность за проверки запросов на вытягивание, можно настроить параметры проверки кода.

- Уведомления для команды
- Автоматические назначения

## Сведения об уведомлениях для команды

Если вы решили уведомлять только определенных участников команды, отключите отправку уведомлений всей команде, когда ей поступает запрос на проверку запроса на вытягивание, если конкретному участнику этой команды также отправляется соответствующий запрос на проверку. Это особенно полезно, если репозиторий настроен так, что команды выступают в качестве владельцев кода, но участники репозитория зачастую знают конкретного человека, который будет проверять запрос на вытягивание. Дополнительные сведения см. в разделе [Сведения о владельцах кода](/github/creating-cloning-and-archiving-repositories/about-code-owners).

## Сведения об автоматическом назначении
{% endif %}

Если включено автоматическое назначение, каждый раз, когда команде поступает запрос на проверку запроса на вытягивание команда удаляется из списка рецензентов, а вместо всей команды рецензентами назначаются указанные участники команды. Задания проверки кода позволяют решить, отправляется ли уведомление всей команде или только определенным ее участникам, когда команде поступает запрос на проверку.

Когда владельцам кода автоматически поступает запрос на проверку, команда по-прежнему удаляется из списка рецензентов и заменяется отдельными пользователями, если только не настроено правило защиты ветви, согласно которому проверку должны выполнять владельцы кода. Если используется такое правило защиты ветви, запрос команде не удастся удалить, поэтому в дополнение появятся индивидуальные запросы.

### Алгоритмы маршрутизации

При назначении проверки кода рецензенты автоматически выбираются и назначаются на основе одного из двух возможных алгоритмов. 

При использовании алгоритма циклического перебора рецензенты выбираются на основе того, кто получил последний запрос на проверку, перебирая всех членов команды независимо от количества необработанных проверок, которое у них в настоящее время имеются. 

При использовании алгоритма распределения нагрузки рецензенты выбираются на основе общего числа последних запросов на проверку каждого участника и учитывается количество необработанных проверок для каждого члена. Алгоритм распределения нагрузки пытается убедиться, что каждый участник команды проверяет одинаковое количество запросов на вытягивание в любой 30-дневный период.

Для проверки не выбираются участники команды, статус которых "Занят". Если все участники команды заняты, запрос на вытягивание останется назначенным самой команде. Дополнительные сведения о статусах пользователей см. в разделе [Указание статуса](/account-and-profile/setting-up-and-managing-your-github-profile/customizing-your-profile/personalizing-your-profile#setting-a-status).

{% ifversion only-notify-requested-members %}
## Настройка уведомлений для команды

{% данных reusables.profile.access_org %} {% данных для повторного использования.user-settings.access_org %} {% данных reusables.organizations.specific_team %} {% данных reusables.organizations.team_settings %} {% ifversion fpt или ghec или ghes > 3.4 или ghae > 3,4 %}
1. На боковой панели слева нажмите **{% octicon "code-review" aria-label="The code-review icon" %} Проверка кода**.
{% else %}
1. На боковой панели слева нажмите **Проверка кода**
![Кнопка проверки кода](/assets/images/help/teams/review-button.png) {% endif %}
1. Выберите **Уведомить только запрошенных участников команды.** 
![Уведомления для команды проверки кода](/assets/images/help/teams/review-assignment-notifications.png)
1. Нажмите кнопку **Сохранить изменения**.
{% endif %}

## Настройка автоматического назначения
{% данных reusables.profile.access_org %} {% данных для повторного использования.user-settings.access_org %} {% данных reusables.organizations.specific_team %} {% данных reusables.organizations.team_settings %} {% ifversion fpt или ghec или ghes > 3.4 или ghae > 3,4 %}
1. На боковой панели слева нажмите **{% octicon "code-review" aria-label="The code-review icon" %} Проверка кода**.
{% else %}
1. На боковой панели слева нажмите **Проверка кода**
![Кнопка проверки кода](/assets/images/help/teams/review-button.png) {% endif %}
1. Выберите **Включить автоматическое назначение**.
![Кнопка автоматического назначения](/assets/images/help/teams/review-assignment-enable.png)
1. В разделе "Сколько участников команды следует назначить для проверки?" используйте раскрывающееся меню и выберите рецензентов, которые будут назначены каждому запросу на вытягивание.
![Раскрывающийся список для выбора количества рецензентов](/assets/images/help/teams/review-assignment-number.png)
1. В разделе "Алгоритм маршрутизации" используйте раскрывающееся меню и выберите нужный алгоритм. Дополнительные сведения см. в разделе [Алгоритмы маршрутизации](#routing-algorithms)".
![Раскрывающийся список для выбора алгоритма маршрутизации](/assets/images/help/teams/review-assignment-algorithm.png)
1. При необходимости, чтобы всегда пропускать определенных участников команды, выберите **Никогда не назначать определенных участников команды**. Затем выберите одного или нескольких участников команды, которых необходимо всегда пропускать.
![Флажок "Никогда не назначать определенных участников команды" и раскрывающееся меню](/assets/images/help/teams/review-assignment-skip-members.png) {% ifversion ghes < 3.4 %}
1. При необходимости, чтобы уведомить только участников команды, выбранных путем назначения проверки кода для каждого запроса на проверку на вытягивание, в разделе "Уведомления" выберите **Если назначаются участники команды, не уведомлять всю команду**.
{%- endif %} {% ifversion fpt или ghec или ghes или ghae > 3,3 %}
1. При необходимости, чтобы включить участников дочерних команд в качестве потенциальных рецензентов при назначении запросов, выберите **Участники дочерней команды**.
1. Кроме того, для подсчета всех участников, которые уже были запрошены, от общего числа назначенных участников, выберите **Подсчет существующих запросов**.
1. При необходимости, чтобы удалить запрос на проверку для команды при назначении участников команды, выберите **Запрос на проверку для команды**.
{%- endif %}
1. Нажмите кнопку **Сохранить изменения**.

## Отключение автоматического назначения
{% data reusables.profile.access_org %} {% data reusables.user-settings.access_org %} {% data reusables.organizations.specific_team %} {% data reusables.organizations.team_settings %}
1. Нажмите **Включить автоматическое назначение**, чтобы снять флажок.
![Кнопка назначения проверки кода](/assets/images/help/teams/review-assignment-enable.png)
1. Нажмите кнопку **Сохранить изменения**.
