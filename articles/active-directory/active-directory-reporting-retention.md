---
title: Azure Active Directory レポートの保持ポリシー | Microsoft Docs
description: Azure Active Directory でのレポート データの保持ポリシー
services: active-directory
documentationcenter: ''
author: rolyon
manager: mtillman
editor: ''
ms.assetid: 183e53b0-0647-42e7-8abe-3e9ff424de12
ms.service: active-directory
ms.devlang: ''
ms.topic: article
ms.tgt_pltfrm: ''
ms.workload: identity
ms.component: compliance-reports
ms.date: 05/10/2018
ms.author: rolyon
ms.reviewer: dhanyahk
ms.openlocfilehash: fac160d2d5916097afcbb9825bb82a52789e4a89
ms.sourcegitcommit: 266fe4c2216c0420e415d733cd3abbf94994533d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34589197"
---
# <a name="azure-active-directory-report-retention-policies"></a>Azure Active Directory レポートの保持ポリシー


このトピックでは、最も一般的な質問に対する回答を、Azure Active Directory のさまざまなアクティビティ レポートのデータ保持と一緒に説明します。 

### <a name="q-how-can-you-get-the-collection-of-activity-data-started"></a>Q: アクティビティ データの収集を開始するにはどうすればよいか

**A:**

| Azure AD のエディション | コレクションの開始 |
| :--              | :--   |
| Azure AD Premium P1 <br /> Azure AD Premium P2 | サブスクリプションにサインアップしたとき |
| Azure AD Free | [Azure Active Directory ブレード](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview)を初めて開いたとき、または [Reporting API](https://aka.ms/aadreports) を初めて使用したとき  |

---
### <a name="q-when-is-your-activity-data-available-in-the-azure-portal"></a>Q: Azure portal でアクティビティ データを使用できるようになるのはいつか

**A:**

- **すぐに** - Azure Portal で既にレポートを操作している場合
- **2 時間以内** - Azure Portal でレポートを有効にしていない場合

---

### <a name="q-how-can-you-get-the-collection-of-security-signals-started"></a>Q: セキュリティ シグナルの収集を開始するにはどうすればよいか  

**A:** セキュリティ シグナルの場合、収集プロセスは Identity Protection センターを使用することを選択した時点から開始されます。 


---

### <a name="q-for-how-long-is-the-collected-data-stored"></a>Q: 収集されたデータはどのくらい保存されるのか

**A:**

**アクティビティ レポート**    

| レポート                 | Azure AD Free | Azure AD Premium P1 | Azure AD Premium P2 |
| :--                    | :--           | :--                 | :--                 |
| ディレクトリ監査        | 7 日        | 30 日             | 30 日             |
| サインイン アクティビティ       | 該当なし           | 30 日             | 30 日             |
| Azure MFA の使用状況        | 30 日       | 30 日             | 30 日             |

**セキュリティ シグナル**

| レポート         | Azure AD Free | Azure AD Premium P1 | Azure AD Premium P2 |
| :--            | :--           | :--                 | :--                 |
| リスクのあるユーザー  | 7 日        | 30 日             | 90 日間             |
| リスクの高いサインイン | 7 日        | 30 日             | 90 日間             |

---
