---
title: Azure Reserved Instances の割引を理解する - Azure Billing | Microsoft Docs
description: Azure Reserved VM Instance の割引が、実行中の仮想マシンにどのように適用されるのかを説明します。
services: billing
documentationcenter: ''
author: yashesvi
manager: yashar
editor: ''
ms.service: billing
ms.devlang: na
ms.topic: conceptual
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 05/09/2018
ms.author: yashar
ms.openlocfilehash: a0800bafc3d6b858387e28a3b75bc7b3a6bfe6e8
ms.sourcegitcommit: 688a394c4901590bbcf5351f9afdf9e8f0c89505
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/18/2018
ms.locfileid: "34301415"
---
# <a name="understand-how-the-reserved-instance-discount-is-applied"></a>予約インスタンスの割引の適用方法について
Azure Reserved VM Instance を購入すると、予約インスタンスの属性や数量に合致する仮想マシンに対して Azure Reserved Instances の割引が自動的に適用されます。 予約インスタンスは、ご利用の仮想マシンのインフラストラクチャ コストに充当されます。 以下の表は、予約インスタンスを購入した後の仮想マシンのコストを示しています。 ストレージとネットワークについては、すべての場合において通常料金が適用されます。

| 仮想マシンのタイプ  | 予約インスタンスの料金 |    
|-----------------------|--------------------------------------------|
|Linux VM (追加ソフトウェアなし) | 予約インスタンスは、ご利用の VM インフラストラクチャ コストに充当されます。|
|Linux VM + ソフトウェア料金 (例: Red Hat) | 予約インスタンスは、インフラストラクチャ コストに充当されます。 追加ソフトウェアについては課金の対象となります。|
|Windows VM (追加ソフトウェアなし) |予約インスタンスは、インフラストラクチャ コストに充当されます。 Windows ソフトウェアについては課金の対象となります。|
|Windows VM + 追加ソフトウェア (例: SQL Server) | 予約インスタンスは、インフラストラクチャ コストに充当されます。 Windows ソフトウェアや追加ソフトウェアについては課金の対象となります。|
|Windows VM + [Azure ハイブリッド特典](https://docs.microsoft.com/azure/virtual-machines/windows/hybrid-use-benefit-licensing) | 予約インスタンスは、インフラストラクチャ コストに充当されます。 Windows ソフトウェアの料金には、Azure ハイブリッド特典が適用されます。 その他のソフトウェアについては、別途課金の対象となります。| 

## <a name="application-of-reserved-instance-discount-to-non-windows-vms"></a>非 Windows VM への予約インスタンスの割引の適用
 予約インスタンスの割引は、実行中の VM インスタンスに 1 時間単位で適用されます。 購入済みの予約インスタンスによる仮想マシンの前払いは、実行中の VM によって生成された使用量と照合され、予約インスタンスの割引が適用されます。 実行時間が 1 時間に満たない可能性のある VM の場合、予約インスタンスは、同時に実行されている VM を含め、予約インスタンスを使用していない他の VM から満たされます。 1 時間の最後には、その時間の VM の予約インスタンスの適用がロックされます。 VM の実行が 1 時間に満たない場合、またはその時間内の同時実行 VM が予約インスタンスの時間を満たさない場合、その時間の予約インスタンスは十分に活用されていません。 以下のグラフは、課金対象の VM 使用量に予約インスタンスを適用した例を示しています。 この例は、単一の予約インスタンス購入で、合致する VM インスタンスが 2 つあることを前提としています。

![適用済みの 1 つの予約インスタンスと合致する 2 つの VM インスタンスのスクリーンショット](media/billing-reserved-vm-instance-application/billing-reserved-vm-instance-application.png)

1.  予約インスタンスのラインを超える使用量には、通常の従量課金制の料金が適用されます。 予約インスタンスのラインを下回る使用量については、予約インスタンス購入分として前払い済みであるため課金されません。
2.  Hour 1 では、インスタンス 1 の実行時間が 0.75 時間、インスタンス 2 の実行時間が 0.5 時間です。 Hour 1 の合計使用量は 1.25 時間となります。 残りの 0.25 時間については従量課金制の料金が発生します。
3.  Hour 2 と Hour 3 では、どちらのインスタンスも実行時間はそれぞれ 1 時間です。 一方のインスタンスには予約インスタンス購入分が充当されますが、もう一方には従量課金制の料金が発生します。
4.  Hour 4 では、インスタンス 1 の実行時間が 0.5 時間、インスタンス 2 の実行時間が 1 時間です。 インスタンス 1 は予約インスタンス購入分で全額充当されます。またインスタンス 2 の 0.5 時間も充当されます。 残りの 0.5 時間については従量課金制の料金が発生します。

予約インスタンスの適用を課金の使用状況レポートの観点から理解し、把握するには、[予約インスタンスの使用量の概要](https://go.microsoft.com/fwlink/?linkid=862757)に関するページを参照してください。

## <a name="application-of-reserved-instance-discount-to-windows-vms"></a>Windows VM への予約インスタンスの割引の適用
Windows VM インスタンスの実行中は、インフラストラクチャ コストに予約インスタンスが適用されて充当されます。 VM インフラストラクチャ コストに対する予約インスタンスの適用は、Windows VM の場合も非 Windows VM の場合も変わりません。 Windows ソフトウェアには別途、vCPU 単位の料金が発生します。 [予約インスタンスに伴う Windows ソフトウェアのコスト](https://go.microsoft.com/fwlink/?linkid=862756)に関するページを参照してください。 [Windows Server 向け Azure ハイブリッド特典] (https://docs.microsoft.com/azure/virtual-machines/windows/hybrid-use-benefit-licensing) で Windows のライセンス コストを賄うことができます。

## <a name="next-steps"></a>次の手順
予約インスタンスの詳細については、次の記事を参照してください。

- [Azure Reserved Instances で仮想マシンのコストを削減する](billing-save-compute-costs-reservations.md)
- [予約インスタンスによる仮想マシンの前払い](../virtual-machines/windows/prepay-reserved-vm-instances.md)
- [予約インスタンスの管理](billing-manage-reserved-vm-instance.md)
- [予約インスタンスの割引の適用方法について](billing-understand-vm-reservation-charges.md)
- 
  [従量課金制サブスクリプションの予約インスタンス使用量について](billing-understand-reserved-instance-usage.md)
- [エンタープライズ加入契約の予約インスタンス使用量について](billing-understand-reserved-instance-usage-ea.md)
- [CSP サブスクリプションの占有インスタンス使用量について](https://docs.microsoft.com/partner-center/azure-reservations)
- [予約インスタンスに含まれない Windows ソフトウェアのコスト](billing-reserved-instance-windows-software-costs.md)


## <a name="need-help-contact-support"></a>お困りの際は、 サポートにお問い合せください

まだ他に質問がある場合は、問題を迅速に解決できるよう [サポートにお問い合わせ](https://portal.azure.com/?#blade/Microsoft_Azure_Support/HelpAndSupportBlade) ください。
