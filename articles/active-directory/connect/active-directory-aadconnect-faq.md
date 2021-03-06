---
title: 'Azure Active Directory Connect: FAQ | Microsoft Docs'
description: このページでは、Azure AD Connect についてよく寄せられる質問を紹介します。
services: active-directory
documentationcenter: ''
author: billmath
manager: mtillman
ms.assetid: 4e47a087-ebcd-4b63-9574-0c31907a39a3
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 05/09/2018
ms.author: billmath
ms.openlocfilehash: 46a9bf47b4998c4d5be47f67556fbdb3ba7b71db
ms.sourcegitcommit: d28bba5fd49049ec7492e88f2519d7f42184e3a8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/11/2018
ms.locfileid: "34054096"
---
# <a name="frequently-asked-questions-for-azure-active-directory-connect"></a>Azure Active Directory Connect についてよく寄せられる質問

## <a name="general-installation"></a>一般的なインストール
**Q: Azure AD のグローバル管理者が 2FA を有効化している場合、インストールを実行できますか。**  
2016 年 2 月以降のビルドでは、これがサポートされています。

**Q: Azure AD Connect を無人インストールする方法はありますか。**  
インストール ウィザードを使用して Azure AD Connect をインストールする場合にのみサポートされます。 サイレント モードでの無人インストールはサポートされていません。

**Q: ドメインに接続できないフォレストがあります。Azure AD Connect をインストールにはどうすればよいですか。**  
2016 年 2 月以降のビルドでは、これがサポートされています。

**Q: AD DS の正常性エージェントはサーバー コアで稼働しますか。**  
はい。 エージェントをインストールした後、次の PowerShell コマンドレットを使って登録プロセスを実行できます。 

`Register-AzureADConnectHealthADDSAgent -Credentials $cred`

**Q: AADConnect では、2 つのドメインから Azure AD への同期がサポートされていますか。**</br>
はい、これはサポートされています。 [複数のドメイン](active-directory-aadconnect-multiple-domains.md)に関するページをご覧ください
 
**Q: Azure AD Connect では同じ Active Directory ドメインに対する複数のコネクタの使用はサポートされていますか。**</br> いいえ、これはサポートされていません 

## <a name="network"></a>ネットワーク
**Q: ファイアウォールやネットワーク デバイスなど、ネットワーク上で接続を開ける最大時間を制限するものがあります。Azure AD Connect を使用する場合、クライアント側のタイムアウトしきい値はどのくらいにすればいいでしょうか。**  
すべてのネットワーク ソフトウェアや物理デバイスなど、接続を開ける最大時間を制限するものは、Azure AD Connect クライアントがインストールされているサーバーと Azure Active Directory 間の接続に対して少なくとも 5 分 (300 秒) のしきい値を使用する必要があります。 これは、以前リリースされたすべての Microsoft Identity 同期ツールにも適用されます。

**Q: SLD (シングル ラベル ドメイン) はサポートされていますか。**  
いいえ、Azure AD Connect は、SLD を使用するオンプレミスのフォレスト/ドメインはサポートしていません。

**Q: 切り離された AD ドメインを持つフォレストはサポートされますか。**  
いいえ、Azure AD Connect は、切り離された名前空間を持つオンプレミスのフォレストはサポートしていません。

**Q: 「ドット形式」の NetBios 名はサポートされていますか。**  
いいえ、Azure AD Connect では、NetBios 名にピリオド (.) が含まれているオンプレミスのフォレスト/ドメインはサポートしていません。

**Q: 純粋な IPv6 環境はサポートされますか。**  
いいえ、Azure AD Connect は、純粋な IPv6 環境はサポートしていません。

## <a name="federation"></a>フェデレーション
**Q: Office 365 の証明書を更新するように求める電子メールを受け取った場合はどうすればいいですか。**  
[証明書の更新](active-directory-aadconnect-o365-certs.md) に関する記事に記載されているガイダンスに従って、証明書を更新してください。

**Q: O365 証明書利用者の "証明書利用者の自動更新" を設定しました。トークン署名証明書が自動的にロールオーバーされるときに、何か必要な操作はありますか。**  
[証明書の更新](active-directory-aadconnect-o365-certs.md)に関する記事に記載されているガイダンスに従ってください。

## <a name="environment"></a>環境
**Q: Azure AD Connect のインストール後のサーバー名の変更はサポートされていますか。**  
いいえ。 サーバー名を変更すると、同期エンジンが SQL データベースに接続できなくなり、サービスを開始できなくなります。

## <a name="identity-data"></a>ID データ
**Q: Azure AD の UPN (userPrincipalName) 属性がオンプレミスの UPN と一致しません。なぜでしょうか。**  
次の記事を参照してください。

* [Office 365、Azure、Intune におけるユーザー名が、オンプレミスの UPN または代替ログイン ID と一致しない](https://support.microsoft.com/en-us/kb/2523192)
* [異なるフェデレーション ドメインを使用するようにユーザー アカウントの UPN を変更した後、Azure Active Directory 同期ツールによって変更が同期されない](https://support.microsoft.com/en-us/kb/2669550)

また、「 [Azure AD Connect 同期サービスの機能](active-directory-aadconnectsyncservice-features.md)」に記載された手順に従って、同期エンジンによる userPrincipalName の更新が許可されるように Azure AD を構成することもできます。

**Q: オンプレミスの AD グループ/連絡先オブジェクトと既存の Azure AD グループ/連絡先オブジェクトとのあいまい一致はサポートされていますか。**  
はい、これは proxyAddress に基づきます。  メールが有効でないグループに対して、あいまい一致はサポートされていません。

**Q: 既存の Azure AD グループ/連絡先オブジェクトに対して手動で設定された ImmutableId 属性とオンプレミスの AD グループ/連絡先オブジェクトとの完全一致はサポートされていますか。**  
いいえ。現在これはサポートされていません。

## <a name="custom-configuration"></a>カスタム構成
**Q: Azure AD Connect 用の PowerShell コマンドレットのドキュメントはどこにありますか。**  
このサイトに記載されているコマンドレットを除き、Azure AD Connect で使用されている PowerShell コマンドレットは、ユーザーによる使用をサポートしていません。

***Q:* Synchronization Service Manager** の [サーバーのエクスポート/インポート] を使用して、サーバー間で構成を移動できますか。  
いいえ。 このオプションはすべての構成設定を取得しないため、使用すべきではありません。 代わりに、2 台目のサーバーでウィザードを使用して基本構成を作成し、同期ルール エディターを使用して PowerShell スクリプトを生成し、サーバー間でカスタム ルールを移動してください。 「[スウィング移行](active-directory-aadconnect-upgrade-previous-version.md#swing-migration)」を参照してください。

**Q: Azure サインイン ページではパスワードがキャッシュされますか。また、パスワード入力要素のオートコンプリート属性を "false" に設定することで、これを防ぐことはできますか。**</br>
現在、オートコンプリート タグを含め、パスワード入力フィールドの HTML 属性を変更することはできません。 現在、パスワード フィールドに属性を追加できるようカスタム Javascript を許可する機能の開発に取り組んでいます。 この機能は、2017 年後半に提供される予定です。

**Q: Azure サインイン ページでは、以前正常にサインインしたユーザーのユーザー名が表示されますか。また、この動作は無効にできますか。**</br>
現在、サインイン ページの HTML 属性を変更することはできません。 現在、パスワード フィールドに属性を追加できるようカスタム Javascript を許可する機能の開発に取り組んでいます。 この機能は、2017 年後半に提供される予定です。

**Q: 同時セッションを防ぐ方法はありますか。**</br>
いいえ。

## <a name="auto-upgrade"></a>自動アップグレード

**Q: 自動アップグレードを使用した場合の利点と結果について教えてください。**</br>
Microsoft では、すべてのお客様に対し、Azure AD Connect インストールの自動アップグレードを有効にするようお勧めしています。 自動アップグレードの利点は、常に最新の修正プログラムを適用できることです (Azure AD Connect で確認された脆弱性に対応するセキュリティ更新プログラムなど)。 アップグレード プロセスは簡単で、新しいバージョンがリリースされ次第、自動的に実行されます。 Microsoft では、自動アップグレードを通じて、Azure AD Connect を使用する何千件ものお客様に新リリースを提供しています。

自動アップグレード プロセスではまず最初に、インストールが自動アップグレードに適合しているかどうかが確立されます (ルールへのカスタム変更や、特定の環境的要因などがないか確認されます)。 適合している場合は、アップグレードが実行され、その後テストが実行されます。 テストの結果、アップグレードが失敗していた場合は、旧バージョンが自動的に復元されます。

環境のサイズによっては、処理に数時間かかる場合もあります。アップグレード中は、Windows Server AD と Azure AD の間の同期は行われません。

**Q: 自動アップグレードが動作しなくなっているため、新しいバージョンをインストールする必要があるという内容の電子メールが送られてきました。なぜそうしなければならないのですか。**</br>
昨年リリースされた Azure AD Connect のバージョンでは、特定の状況において、自動アップグレード機能がサーバー上で無効になることがあります。 この問題は、先月末にリリースされた Azure AD Connect バージョン 1.1.750.0 で修正されました。 この問題の影響を受けた可能性があるお客様には、Azure AD Connect の最新バージョンに手動でアップグレードして、問題を回避していただく必要があります。 手動でアップグレードするには、AADConnect.msi ファイルの最新バージョンをダウンロードし、実行する必要があります。
 
-  現在のバージョンが 1.1.750.0 よりも古い場合は、最新のバージョンにアップグレードする必要があります ([こちらからダウンロードできます](https://www.microsoft.com/en-us/download/details.aspx?id=47594))。
- Azure AD Connect のバージョンが 1.1.750.0 以降である場合は、自動アップグレードの問題を回避するための措置は必要ありません。ご使用のバージョンに、この問題の修正プログラムが既に含まれています。 

**Q: 最新バージョンにアップグレードして、自動アップグレードを再度有効にするよう求める内容の電子メールが送られてきました。使用しているのは 1.1.654.0 です。アップグレードする必要はありますか。** </br>    
はい、1.1.750 以降のバージョンにアップグレードして、自動アップグレードを再度有効にする必要があります。 新しいバージョンへのアップグレード方法については、こちらのリンクで説明しています

**Q: 最新バージョンにアップグレードして、自動アップグレードを再度有効にするよう求める内容の電子メールが送られてきました。PowerShell を使用して自動アップグレードを有効にしたのですが、最新バージョンをインストールする必要があるのでしょうか。**</br>    
はい、1.1.750.0 以降のバージョンにアップグレードする必要があります。 PowerShell を使用して自動アップグレード サービスを有効にした場合、1.1.750 より前のバージョンで見つかった自動アップグレードの問題は回避されません

**Q: 新しいバージョンにアップグレードする必要があるのですが、Azure AD Connect を誰がインストールしたのかわからないため、ユーザー名とパスワードがわかりません。これらの情報は必要ですか。**</br>
最初に使用されたユーザー名とパスワードがわからなくても、Azure AD Connect はアップグレードできます。グローバル管理者ロールが割り当てられた任意の Azure AD アカウントを使用できます。

**Q: 現在使用している Azure AD Connect のバージョンはどうすれば確認できますか。**</br>   
サーバーにインストールされている Azure AD Connect のバージョンを確認するには、コントロール パネルに移動し、[プログラム] > [プログラムと機能] で、インストールされている Microsoft Azure AD Connect のバージョンを調べてください。

![version](media/active-directory-aadconnect-faq/faq1.png)

**Q: AADConnect を最新バージョンにアップグレードする方法について教えてください。**</br>    
新しいバージョンへのアップグレード方法については、[こちらの記事](active-directory-aadconnect-upgrade-previous-version.md)で説明しています。 

**Q: 昨年、AADConnect を最新バージョンにアップグレードしたのですが、再度アップグレードする必要があるのでしょうか。**</br> Azure AD Connect チームではサービスを頻繁に更新しているため、バグの修正、セキュリティ更新プログラム、および新機能をご利用いただくには、サーバーを常に最新のバージョンで更新することが重要です。 自動アップグレードを有効にしておけば、ソフトウェアのバージョンは自動的に更新されます。 Azure AD Connect のバージョン リリース履歴は、こちらの[リンク](active-directory-aadconnect-version-history.md)から確認できます。

**Q: アップグレードにかかる時間と、ユーザーへの影響について教えてください。**</br>    
アップグレードに必要な時間は、テナントのサイズによって異なります。大規模な組織の場合は、夜間や週末に行うことをお勧めします。 なお、アップグレード中は同期アクティビティは実行されません。

**Q: AADConnect のアップグレードは行ったと思うのですが、Office ポータルにはまだ DirSync と表示されます。なぜでしょうか。**</br>    
Office チームでは、Office ポータルに現在の製品名が反映されるようにするべく取り組んでいます。現状では、ご使用の同期ツールは反映されません。

**Q: 自動アップグレードの状況を確認したところ、「中断」と表示されています。なぜ中断されているのでしょうか。自分で有効化する必要があるのでしょうか。**</br>     
以前のバージョンでは、特定の状況において、自動アップグレードの状態が「中断」に設定されたままになるというバグが確認されています。 手動で有効にすることも技術的には可能ですが、複雑な手順が必要になるため、最新バージョンの Azure AD Connect をインストールすることをお勧めします

**Q: 私の会社では変更管理の要件が厳しく設定されているため、変更がプッシュアウトされるタイミングを制御したいのですが、自動アップグレードが起動されるタイミングを制御することはできますか。**</br> いいえ、現在のところ、そのような機能はありません。Microsoft では、今後のリリースでこれを導入するかどうか検討しているところです。

**Q: 自動アップグレードが失敗した場合、電子メールによる通知は送られてきますか。アップグレードが成功したかどうかを確認する方法について教えてください。**</br>     
アップグレードの結果に関する通知はありません。これについては、将来のリリースで導入するかどうか検討しているところです。

**自動アップグレードのプッシュ アウト予定に関するタイム ラインは公表されていますか。**</br>    
自動アップグレードは、新しいバージョンのリリース プロセスにおける最初のステップです。そのため、新しいバージョンが発生した際には、必ず自動アップグレードがプッシュされます。 Azure AD Connect の新バージョンについては、[Azure AD のロードマップ](../../active-directory/whats-new.md)に関するページで事前に発表されます。

**Q: 自動アップグレードでは、AAD Connect Health もアップグレードされますか。**</br>   はい、自動アップグレードでは、AAD Connect Health もアップグレードされます

**Q: ステージング モードの AAD Connect サーバーも自動アップグレードされますか。**</br>   
いいえ、ステージング モードの Azure AD Connect サーバーは自動アップグレードされません。

**Q: 自動アップグレードが失敗し、AAD Connect サーバーが起動しない場合には、どうすればよいのでしょうか。**</br>   
まれに、アップグレードの実行後、Azure AD Connect サービスが開始されないことがあります。 そのような場合は、サーバーを再起動してください。通常はこれで問題が解決します。 それでも Azure AD Connect サービスが開始されない場合は、サポート チケットを発行してください。 方法については、こちらの[リンク](https://blogs.technet.microsoft.com/praveenkumar/2013/07/17/how-to-create-service-requests-to-contact-office-365-support/)で説明しています。 

**Q: Azure AD Connect を新しいバージョンにアップグレードする際のリスクがよくわかりません。アップグレードについて電話で説明を受けることはできますか。**</br>
Azure AD Connect の新バージョンへのアップグレードについてヘルプが必要な場合は、サポート チケットを発行してください。方法については、こちらの[リンク](https://blogs.technet.microsoft.com/praveenkumar/2013/07/17/how-to-create-service-requests-to-contact-office-365-support/)で説明しています。

## <a name="troubleshooting"></a>トラブルシューティング
**Q: Azure AD Connect に関するヘルプを参照する方法を教えてください。**

[Microsoft サポート技術情報 (KB) の検索](https://www.microsoft.com/en-us/Search/result.aspx?q=azure%20active%20directory%20connect&form=mssupport)

* Azure AD Connect のサポートに関する一般的な破損時補償の技術的な解決策について、Microsoft サポート技術情報 (KB) を検索してください。

[Microsoft Azure Active Directory フォーラム](https://social.msdn.microsoft.com/Forums/azure/en-US/home?forum=WindowsAzureAD)

* このコミュニティで技術的な質問と回答を検索して参照したり、 [こちら](https://social.msdn.microsoft.com/Forums/azure/en-US/newthread?category=windowsazureplatform&forum=WindowsAzureAD&prof=required)をクリックして独自の質問を行ったりできます。

[Azure AD のサポートを受ける方法](https://docs.microsoft.com/azure/active-directory/active-directory-troubleshooting-support-howto)

* このリンクを使用して、Azure Portal からサポートを受けることができます。

