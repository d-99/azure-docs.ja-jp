---
title: Azure Portal で Batch アカウントを作成する | Microsoft Docs
description: Azure ポータルで、クラウド内で大規模な並列ワークロードを実行する Azure Batch アカウントを作成する方法について説明します
services: batch
documentationcenter: ''
author: dlepow
manager: jeconnoc
editor: ''
ms.assetid: 3fbae545-245f-4c66-aee2-e25d7d5d36db
ms.service: batch
ms.workload: big-compute
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: get-started-article
ms.date: 05/15/2018
ms.author: danlep
ms.custom: H1Hack27Feb2017
ms.openlocfilehash: 83d97d9ed9c51d59500115c4ee3896d471024999
ms.sourcegitcommit: b6319f1a87d9316122f96769aab0d92b46a6879a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2018
ms.locfileid: "34359759"
---
# <a name="create-a-batch-account-with-the-azure-portal"></a>Azure Portal で Batch アカウントを作成する

> [!div class="op_single_selector"]
> * [Azure Portal](batch-account-create-portal.md)
> * [Batch Management .NET](batch-management-dotnet.md)
>
>

[Azure Portal][azure_portal] で Azure Batch アカウントを作成し、自分のコンピューティング シナリオに適したアカウント プロパティを選ぶ方法について説明します。 アクセス キーやアカウント URL のような重要なアカウント プロパティを確認できる場所を紹介します。

Batch アカウントとシナリオの背景情報については、[機能の概要](batch-api-basics.md)に関するページを参照してください。

## <a name="create-a-batch-account"></a>Batch アカウントを作成する

[!INCLUDE [batch-account-mode-include](../../includes/batch-account-mode-include.md)]

1. [Azure Portal][azure_portal] にサインインします。

2. **[新規]**  >  **[Compute]**  >  **[Batch サービス]** の順にクリックします。

    ![Marketplace での Batch][marketplace_portal]

3. **[新しい Batch アカウント]** 設定を入力します。 次の詳細を確認してください。

    ![Batch アカウントを作成する][account_portal]

    a.[サインオン URL] ボックスに、次のパターンを使用して、ユーザーが RightScale アプリケーションへのサインオンに使用する URL を入力します。 **[アカウント名]**: 選択する名前は、アカウントが作成される Azure リージョン内で一意である必要があります (下の **[場所]** を参照)。 アカウント名に含めることができるのは、英小文字と数字のみで、文字数は 3 ～ 24 文字にする必要があります。

    b. **サブスクリプション**: Batch アカウントを作成するサブスクリプション。 サブスクリプションが 1 つのみの場合は、既定でそのサブスクリプションが選択されます。

    c. **リソース グループ**: 新しい Batch アカウント用の既存のリソース グループを選択します。必要に応じて、新しく作成することもできます。

    d. **場所**: Batch アカウントを作成する Azure リージョン。 サブスクリプションとリソース グループでサポートされているリージョンのみがオプションとして表示されます。

    e. **ストレージ アカウント** (省略可能): Batch アカウントに関連付ける Azure ストレージ アカウント。 ほとんどの Batch アカウントでこれをお勧めします。 Batch のストレージ アカウント オプションについては、[Batch 機能の概要](batch-api-basics.md#azure-storage-account)に関するページをご覧ください。 ポータルで、既存のストレージ アカウントを選択するか、必要に応じて新しいストレージ アカウントを作成します。

      ![ストレージ アカウントの作成][storage_account]

    f. **プール割り当てモード**: ほとんどのシナリオで、既定の **[Batch サービス]** をそのまま使用してください。

4. **[作成]** をクリックしてアカウントを作成します。



## <a name="view-batch-account-properties"></a>Batch アカウントのプロパティを表示する
アカウントが作成されたら、そのアカウントをクリックして設定とプロパティにアクセスします。 左側のメニューを使用すると、アカウントの設定およびプロパティすべてにアクセスできます。

![Azure Portal の [Batch アカウント] ブレード][account_blade]

* **Batch アカウントの名前、URL、およびキー**: [Batch API](batch-apis-tools.md#azure-accounts-for-batch-development) を使用してアプリケーションを開発する場合は、Batch リソースにアクセスするためにアカウント URL およびキーが必要になります  (Batch では Azure Active Directory 認証もサポートされます)。

    Batch アカウント アクセス情報を表示するには、**[キー]** をクリックします。

    ![Batch account keys in Azure portal][account_keys]

* Batch アカウントに関連付けられているストレージ アカウントの名前とキーを表示するには、**[ストレージ アカウント]** をクリックします。

* Batch アカウントに適用されるリソース クォータを表示するには、**[クォータ]** をクリックします。 詳細については、「[Batch サービスのクォータと制限](batch-quota-limit.md)」を参照してください。


## <a name="additional-configuration-for-user-subscription-mode"></a>ユーザー サブスクリプション モードのための追加構成

ユーザー サブスクリプション モードで Batch アカウントを作成することを選択した場合は、アカウントを作成する前に別途、次の手順を実行してください。

### <a name="allow-azure-batch-to-access-the-subscription-one-time-operation"></a>Azure Batch によるサブスクリプションへのアクセスを許可する (1 回限りの操作)
ユーザー サブスクリプション モードで Batch アカウントを初めて作成する場合は、Batch にサブスクリプションを登録する必要があります  (既に実行済みの場合は、次のセクションに移ってください)。

1. [Azure Portal][azure_portal] にサインインします。

2. **[その他のサービス]** > **[サブスクリプション]** の順にクリックし、Batch アカウントに使用するサブスクリプションをクリックします。

3. **[サブスクリプション]** ページで、**[アクセス制御 (IAM)]** > **[追加]** の順にクリックします。

    ![サブスクリプションのアクセスの制御][subscription_access]

4. **[アクセス許可の追加]** ページで、**[共同作成者]** ロールを選択し、Batch API を探します。 API が見つかるまで、次の各文字列を検索します。
    1. **MicrosoftAzureBatch**。
    2. **Microsoft Azure Batch**。 新しい Azure AD テナントでは、この名前が使用される場合があります。
    3. **ddbf3205-c6bd-46ae-8127-60eb93363864** は Batch API の ID です。 

5. Batch API を見つけたら選択して、**[保存]** をクリックします。

    ![Batch のアクセス許可を追加する][add_permission]

### <a name="create-a-key-vault"></a>Key Vault を作成します
ユーザー サブスクリプション モードでは、作成する Batch アカウントと同じリソース グループに属する Azure キー コンテナーが必要です。 Batch を[利用でき](https://azure.microsoft.com/regions/services/)、お使いのサブスクリプションでサポートされているリージョンにそのリソース グループが属していることを確認してください。

1. [Azure portal][azure_portal] で、**[新規]** > **[セキュリティ]** > **[Key Vault]** の順にクリックします。

2. **[Key Vault の作成]** ページで、キー コンテナーの名前を入力し、Batch アカウント用のリージョンでリソース グループを作成します。 残りの設定については既定値のままにして、**[作成]** をクリックします。

ユーザー サブスクリプション モードで Batch アカウントを作成しているときに、キー コンテナーのリソース グループを使用して、**ユーザー サブスクリプション**をプール割り当てモードとして指定し、キー コンテナーを選択します。

## <a name="other-batch-account-management-options"></a>その他の Batch アカウント管理オプション
Azure portal を利用する方法に加えて、次のようなツールを使用して Batch アカウントを作成および管理できます。

* [Batch PowerShell コマンドレット](batch-powershell-cmdlets-get-started.md)
* [Azure CLI](batch-cli-get-started.md)
* [Batch Management .NET](batch-management-dotnet.md)

## <a name="next-steps"></a>次の手順
* Batch サービスの概念と機能の詳細については、[Batch 機能の概要](batch-api-basics.md)に関するページを参照してください。 この記事では、プール、コンピューティング ノード、ジョブ、タスクなど、主要な Batch リソースについて説明するほか、大規模なコンピューティング ワークロード向けのこのサービスの機能の概要について説明します。
* [Batch .NET クライアント ライブラリ](batch-dotnet-get-started.md)または [Python](batch-python-tutorial.md) を使用した Batch 対応アプリケーションの開発に関する基本事項を確認してください。 これらの入門記事では、Batch サービスを使用して複数のコンピューティング ノードでワークロードを実行する実用アプリケーションの開発手順を説明しています。また、Azure Storage を使用してワークロード ファイルのステージングと取得を行う方法についても取り上げています。

[azure_portal]: https://portal.azure.com
[batch_pricing]: https://azure.microsoft.com/pricing/details/batch/

[marketplace_portal]: ./media/batch-account-create-portal/marketplace-batch.png
[account_blade]: ./media/batch-account-create-portal/batch_blade.png
[account_portal]: ./media/batch-account-create-portal/batch-account-portal.png
[account_keys]: ./media/batch-account-create-portal/batch-account-keys.png
[account_url]: ./media/batch-account-create-portal/account_url.png
[storage_account]: ./media/batch-account-create-portal/storage_account.png
[subscription_access]: ./media/batch-account-create-portal/subscription_iam.png
[add_permission]: ./media/batch-account-create-portal/add_permission.png

