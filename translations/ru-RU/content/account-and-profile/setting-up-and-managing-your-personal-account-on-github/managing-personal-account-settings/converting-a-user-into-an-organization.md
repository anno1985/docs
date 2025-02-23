---
title: Преобразование пользователя в организацию
redirect_from:
- /articles/what-is-the-difference-between-create-new-organization-and-turn-account-into-an-organization
- /articles/explaining-the-account-transformation-warning
- /articles/converting-a-user-into-an-organization
- /github/setting-up-and-managing-your-github-user-account/converting-a-user-into-an-organization
- /github/setting-up-and-managing-your-github-user-account/managing-user-account-settings/converting-a-user-into-an-organization
- /account-and-profile/setting-up-and-managing-your-github-user-account/managing-user-account-settings/converting-a-user-into-an-organization
intro: Вы можете выполнить преобразование личной учетной записи в организацию Это позволяет предоставлять детализированные разрешения для репозиториев, принадлежащих организации.
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
topics:
- Accounts
shortTitle: User into an organization
ms.openlocfilehash: 641172d82581ad83bd7281fed941171ce6c817b7
ms.sourcegitcommit: 2298858ef68ffb4e79490ddbb9d6a64081dfbc39
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2022
ms.locfileid: "147389396"
---
{% warning %}

**Предупреждение.** Прежде чем выполнять преобразование пользователя в организацию, необходимо учесть следующее.

* Вы **больше не сможете** войти в преобразованную личную учетную запись.
* Вы **больше не сможете** создать или изменить gist, принадлежащие преобразованной личной учетной записи.
* Организацию **невозможно** будет преобразовать обратно в пользователя.
* Ключи SSH, маркеры OAuth, профиль задания, реакции, а также связанные сведения о пользователе **не будут** переданы в организацию. Это относится только к преобразуемой личной учетной записи, но не к участникам совместной работы для личной учетной записи.
* Любые фиксации, сделанные с преобразованной личной учетной записью, **больше не будут связаны** с ней. Сами фиксации **останутся неизменными**.
* Любые существующие комментарии, сделанные преобразованной личной учетной записью, **больше не будут связаны** с ней. Сами комментарии **останутся** неизменными, но будут связаны с пользователем `ghost`.
* Все вилки частных репозиториев, сделанные с помощью преобразованной личной учетной записи, будут удалены.
{% endwarning %}

{% ifversion fpt or ghec or ghes %}
## <a name="keep-your-personal-account-and-create-a-new-organization-manually"></a>Сохранение личной учетной записи и создание новой организации вручную

Если необходимо, чтобы в вашей организации использовалось то же имя, что и для вашей личной учетной записи, или если нужно сохранить данные вашей личной учетной записи без изменений, вместо преобразования личной учетной записи в организацию создайте новую организацию и перенесите в нее репозитории.

1. Чтобы сохранить текущее имя своей личной учетной записи для личного использования, [измените имя этой учетной записи](/articles/changing-your-github-username), придумав новое и интересное название.
2. [Создайте новую организацию](/articles/creating-a-new-organization-from-scratch) с исходным именем своей личной учетной записи.
3. [Перенесите свои репозитории](/articles/transferring-a-repository) в новую учетную запись организации.{% endif %}

## <a name="convert-your-personal-account-into-an-organization-automatically"></a>Автоматическое преобразование личной учетной записи в организацию

Вы также можете преобразовать личную учетную запись непосредственно в организацию. Преобразование учетной записи:
 - Сохраняет репозитории в неизменном виде, и их потом не нужно переносить вручную в другую учетную запись
 - Автоматически приглашает участников совместной работы в команды с разрешениями, эквивалентными тем, что были до {% ifversion fpt or ghec %}. Для личных учетных записей в {% data variables.product.prodname_pro %} выставление счетов автоматически переводится на [оплаченные {% data variables.product.prodname_team %}](/articles/about-billing-for-github-accounts) без необходимости повторного ввода сведений об оплате, корректировки цикла выставления счетов или двойной оплаты в любое время{% endif %}

1. Создайте новую личную учетную запись, которая будет использоваться для входа в GitHub, а также для доступа к организации и репозиториям после преобразования.
2.  [Покиньте все организации](/articles/removing-yourself-from-an-organization), в которые входила преобразуемая личная учетная запись.
{% data reusables.user-settings.access_settings %} {% data reusables.user-settings.organizations %}
5. В разделе "Преобразование учетной записи" щелкните **Преобразовать <username> в организацию**.
    ![Кнопка преобразования организации](/assets/images/help/settings/convert-to-organization.png)
6. Проверьте и подтвердите преобразование в диалоговом окне "Предупреждение о преобразовании учетной записи". Обратите внимание, что сведения в этом окне совпадают с предупреждением в начале этой статьи.
    ![Предупреждение о преобразовании](/assets/images/help/organizations/organization-account-transformation-warning.png)
7. На странице "Преобразование пользователя в организацию" в разделе "Выбор ответственного по организации" выберите вторичную личную учетную запись, созданную в предыдущем разделе, или другого пользователя, которому вы доверяете управление организацией.
    ![Страница "Добавление ответственного по организации"](/assets/images/help/organizations/organization-add-owner.png)
8. Выберите подписку для новой организации и при появлении запроса введите сведения о выставлении счетов.
9. Щелкните **Создать организацию**.
10. Войдите в новую личную учетную запись, созданную на шаге 1, а затем используйте переключатель контекста для получения доступа к новой организации.

{% tip %}

**Совет.** При преобразовании личной учетной записи в организацию мы добавим участников совместной работы в репозиториях, относящихся к учетной записи, в новую организацию в качестве *внешних участников совместной работы*. Затем при желании вы сможете пригласить *внешних участников совместной работы* стать членами новой организации. Дополнительные сведения см. в статье "[Роли в организации](/organizations/managing-peoples-access-to-your-organization-with-roles/roles-in-an-organization#outside-collaborators)".

{% endtip %}

## <a name="further-reading"></a>Дополнительные материалы
- [Настройка команд](/articles/setting-up-teams) {% ifversion fpt or ghec %}- [Приглашение пользователей присоединиться к организации](/articles/inviting-users-to-join-your-organization){% endif %}
- "[Вступление в организацию](/articles/accessing-an-organization)"
