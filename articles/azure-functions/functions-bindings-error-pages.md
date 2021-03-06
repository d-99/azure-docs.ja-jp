---
title: Azure Functions のエラー処理に関するガイダンス | Microsoft Docs
description: 関数の実行時に発生するエラーの処理に関する一般的なガイダンスと、バインド固有のエラーのトピックへのリンクを提供します。
services: functions
cloud: ''
documentationcenter: ''
author: ggailey777
manager: cfowler
ms.assetid: ''
ms.service: functions
ms.workload: na
ms.tgt_pltfrm: multiple
ms.devlang: multiple
ms.topic: article
ms.date: 02/01/2018
ms.author: glenga; cfowler
ms.openlocfilehash: 82cdc62b3070811186583fdf1ce5e6ce421ebc34
ms.sourcegitcommit: 059dae3d8a0e716adc95ad2296843a45745a415d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
ms.locfileid: "29133699"
---
# <a name="azure-functions-error-handling"></a>Azure Functions のエラー処理

このトピックでは、関数の実行時に発生するエラーの処理に関する一般的なガイダンスを提供します。 さらに、発生する可能性があるバインド固有のエラーについて説明されているトピックへのリンクを提供します。 

## <a name="handing-errors-in-functions"></a>関数のエラーの処理
[!INCLUDE [bindings errors intro](../../includes/functions-bindings-errors-intro.md)]

 
## <a name="binding-error-codes"></a>エラー コードのバインド

Azure サービスと統合する際、基盤となるサービスの API からのエラーが発生する場合があります。 これらのサービスのエラー コード ドキュメントへのリンクは、次のトリガーおよびバインド リファレンス トピックの「**例外とリターン コード**」セクションで見つかります。

+ [Azure Cosmos DB](functions-bindings-cosmosdb.md#exceptions-and-return-codes)

+ [Blob Storage](functions-bindings-storage-blob.md#exceptions-and-return-codes)

+ [Event Hubs](functions-bindings-event-hubs.md#exceptions-and-return-codes)

+ [Notification Hubs](functions-bindings-notification-hubs.md#exceptions-and-return-codes)

+ [Queue Storage](functions-bindings-storage-queue.md#exceptions-and-return-codes)

+ [Service Bus](functions-bindings-service-bus.md#exceptions-and-return-codes)

+ [Table Storage](functions-bindings-storage-table.md#exceptions-and-return-codes)
