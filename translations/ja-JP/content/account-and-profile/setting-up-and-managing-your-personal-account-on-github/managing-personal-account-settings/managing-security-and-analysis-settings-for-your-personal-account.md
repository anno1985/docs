---
title: 個人アカウントのセキュリティと分析設定を管理する
intro: '{% data variables.product.prodname_dotcom %} 上のプロジェクトのコードをセキュリティ保護し分析する機能を管理できます。'
versions:
  fpt: '*'
  ghec: '*'
  ghes: '*'
topics:
  - Accounts
redirect_from:
  - /github/setting-up-and-managing-your-github-user-account/managing-security-and-analysis-settings-for-your-user-account
  - /github/setting-up-and-managing-your-github-user-account/managing-user-account-settings/managing-security-and-analysis-settings-for-your-user-account
  - /account-and-profile/setting-up-and-managing-your-github-user-account/managing-user-account-settings/managing-security-and-analysis-settings-for-your-user-account
shortTitle: Manage security & analysis
ms.openlocfilehash: 22ff867691f79360db54f0fe85f5e988c71536a3
ms.sourcegitcommit: f638d569cd4f0dd6d0fb967818267992c0499110
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2022
ms.locfileid: '148108953'
---
## セキュリティおよび分析設定の管理について

{% data variables.product.prodname_dotcom %} を使用してリポジトリを保護できます。 このトピックでは、既存または新規のすべてのリポジトリのセキュリティおよび分析機能を管理する方法について説明します。

個々のリポジトリのセキュリティおよび分析機能は引き続き管理できます。 詳細については、「[リポジトリのセキュリティと分析の設定を管理する](/github/administering-a-repository/managing-security-and-analysis-settings-for-your-repository)」を参照してください。

自分の個人アカウントに対するすべてのアクティビティのセキュリティ ログを確認することもできます。 詳細については、「[セキュリティ ログの確認](/authentication/keeping-your-account-and-data-secure/reviewing-your-security-log)」を参照してください。

{% data reusables.security.some-security-and-analysis-features-are-enabled-by-default %}

{% data reusables.security.security-and-analysis-features-enable-read-only %}

リポジトリレベル セキュリティの概要については、「[リポジトリをセキュリティで保護する](/code-security/getting-started/securing-your-repository)」を参照してください。

## 既存のリポジトリに対して機能を有効または無効にする

{% data reusables.user-settings.access_settings %} {% data reusables.user-settings.security-analysis %}
3. [Code security and analysis] の下で機能の右にある **[Disable all]** または **[Enable all]** をクリックします。
  {% ifversion ghes %}![[セキュリティと分析の構成] 機能の [すべて有効にする] または [すべて無効にする] ボタン](/assets/images/enterprise/3.3/settings/security-and-analysis-disable-or-enable-all.png){% else %}![[セキュリティと分析の構成] 機能の [すべて有効にする] または [すべて無効にする] ボタン](/assets/images/help/settings/security-and-analysis-disable-or-enable-all.png){% endif %}
6. オプションで、自分が所有する新しいリポジトリに対して機能を既定で有効にできます。
  {% ifversion ghes %}![新しいリポジトリの [既定で有効化] オプション](/assets/images/enterprise/3.3/settings/security-and-analysis-enable-by-default-in-modal.png){% else %}![新しいリポジトリの [既定で有効化] オプション](/assets/images/help/settings/security-and-analysis-enable-by-default-in-modal.png){% endif %}
7. **[Disable FEATURE]** または **[Enable FEATURE]** をクリックし、所有するすべてのリポジトリに対してこの機能を無効または有効にします。
  {% ifversion ghes %}![機能を無効または有効にするボタン](/assets/images/enterprise/3.3/settings/security-and-analysis-enable-dependency-graph.png){% else %}![機能を無効または有効にするボタン](/assets/images/help/settings/security-and-analysis-enable-dependency-graph.png){% endif %}

{% data reusables.security.displayed-information %}

## 既存のリポジトリに対して機能を有効または無効にする

{% data reusables.user-settings.access_settings %} {% data reusables.user-settings.security-analysis %}
3. 機能の右側にある [Code security and analysis] で、所有する新しいリポジトリに対して既定で機能を有効または無効にします
  {% ifversion ghes %}![新しいリポジトリの機能を有効または無効にするチェックボックス](/assets/images/enterprise/3.3/settings/security-and-analysis-enable-or-disable-feature-checkbox.png){% else %}![新しいリポジトリの機能を有効または無効にするチェックボックス](/assets/images/help/settings/security-and-analysis-enable-or-disable-feature-checkbox.png){% endif %}

## 参考資料

- "[依存関係グラフについて](/github/visualizing-repository-data-with-graphs/about-the-dependency-graph)"
- "[{% data variables.product.prodname_dependabot_alerts %} について](/code-security/supply-chain-security/about-alerts-for-vulnerable-dependencies)"
- "[依存関係を自動的に更新する](/code-security/supply-chain-security/keeping-your-dependencies-updated-automatically)"
