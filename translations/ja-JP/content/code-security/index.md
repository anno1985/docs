---
title: コードセキュリティ
shortTitle: Code security
intro: 'コードベースからシークレットや脆弱性を排除{% ifversion not ghae %}し、ソフトウェアサプライチェーンを管理{% endif %}する機能で、{% data variables.product.prodname_dotcom %}ワークフローにセキュリティを組み込んでください。'
introLinks:
  overview: /code-security/getting-started/github-security-features
featuredLinks:
  guides:
    - /code-security/getting-started/securing-your-repository
    - /code-security/getting-started/securing-your-organization
    - '{% ifversion fpt or ghec %}/code-security/repository-security-advisories/creating-a-repository-security-advisory{% endif %}'
    - '{% ifversion ghes or ghae %}/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/setting-up-code-scanning-for-a-repository{% endif%}'
  guideCards:
    - '{% ifversion fpt or ghec or ghes > 3.2 %}/code-security/supply-chain-security/managing-vulnerabilities-in-your-projects-dependencies/configuring-dependabot-security-updates{% endif %}'
    - '{% ifversion fpt or ghec or ghes > 3.2 %}/code-security/supply-chain-security/keeping-your-dependencies-updated-automatically/enabling-and-disabling-dependabot-version-updates{% endif %}'
    - '{% ifversion fpt or ghec or ghes > 3.2 %}/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/setting-up-code-scanning-for-a-repository{% endif %}'
    - '{% ifversion ghes < 3.3 %}/code-security/supply-chain-security/understanding-your-software-supply-chain/exploring-the-dependencies-of-a-repository{% endif %}'
    - '{% ifversion ghes < 3.3 %}/code-security/supply-chain-security/managing-vulnerabilities-in-your-projects-dependencies/configuring-notifications-for-vulnerable-dependencies{% endif %}'
    - '{% ifversion ghes < 3.3 or ghae %}/code-security/secret-scanning/configuring-secret-scanning-for-your-repositories{% endif %}'
    - '{% ifversion ghae %}/code-security/code-scanning/integrating-with-code-scanning/uploading-a-sarif-file-to-github{% endif %}'
    - '{% ifversion ghae %}/code-security/code-scanning/using-codeql-code-scanning-with-your-existing-ci-system{% endif %}'
    - /code-security/supply-chain-security/end-to-end-supply-chain/end-to-end-supply-chain-overview
  popular:
    - '{% ifversion ghes %}/admin/release-notes{% endif %}'
    - /code-security/supply-chain-security/managing-vulnerabilities-in-your-projects-dependencies/about-alerts-for-vulnerable-dependencies
    - /code-security/security-advisories/guidance-on-reporting-and-writing/about-coordinated-disclosure-of-security-vulnerabilities
    - /code-security/supply-chain-security/keeping-your-dependencies-updated-automatically/keeping-your-actions-up-to-date-with-dependabot
    - /code-security/supply-chain-security/keeping-your-dependencies-updated-automatically/configuration-options-for-dependency-updates
    - /code-security/supply-chain-security/keeping-your-dependencies-updated-automatically/managing-encrypted-secrets-for-dependabot
    - '{% ifversion ghae %}/code-security/secret-scanning/about-secret-scanning{% endif %}'
    - /code-security/supply-chain-security/managing-vulnerabilities-in-your-projects-dependencies/troubleshooting-the-detection-of-vulnerable-dependencies
    - '{% ifversion ghes < 3.3 or ghae %}/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/configuring-the-codeql-workflow-for-compiled-languages{% endif %}'
    - '{% ifversion ghes < 3.3 or ghae %}/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/troubleshooting-the-codeql-workflow{% endif %}'
    - '{% ifversion ghes < 3.3 or ghae %}/code-security/code-scanning/automatically-scanning-your-code-for-vulnerabilities-and-errors/running-codeql-code-scanning-in-a-container{% endif %}'
changelog:
  label: security-and-compliance
  versions:
    fpt: '*'
    ghec: '*'
examples_source: data/product-examples/code-security/code-examples.yml
layout: product-landing
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
topics:
  - Repositories
  - Dependencies
  - Vulnerabilities
children:
  - /getting-started
  - /adopting-github-advanced-security-at-scale
  - /secret-scanning
  - /code-scanning
  - /security-advisories
  - /supply-chain-security
  - /dependabot
  - /security-overview
  - /guides
ms.openlocfilehash: 0f6dbbec6243c8785016fb903a77fe9c7326b7d9
ms.sourcegitcommit: e8c012864f13f9146e53fcb0699e2928c949ffa8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2022
ms.locfileid: '148159262'
---

