---
title: 批次處理 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- batching
- Messaging Engine, batching
- batching, batch size
- batching, about batching
- batching, configuring
- batching, Messaging Engine
ms.assetid: eadc177a-d395-4f99-8dab-aa706fd8ea00
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca31344e60daa88a37c21d0f90b6cf2d2a8aa5a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230886"
---
# <a name="batching"></a>批次處理
*批次處理*是序列化的一組允許進行最佳化，關於資料庫往返的訊息處理。 批次是不可部分完成的工作單位，也就是說，批次不是完全成功就是完全失敗。 若批次中一個作業成功而另一個失敗，則組成批次的所有作業都是無效的，且必須重複執行。  
  
 BizTalk Server 會使用批次處理來進行下列動作：  
  
-   攤銷許多訊息的交易成本。  
  
-   藉由減少資料庫往返內部數目來提高速度。  
  
-   使用 BizTalk Server 非同步 API，以便更有效地利用 BizTalk Server 執行緒集區。  
  
## <a name="applying-batching"></a>套用批次處理  
 批次處理是在接收位置的進階屬性中設定，並會在傳送埠端自動啟用。  
  
## <a name="lowering-the-batch-size"></a>減少批次大小  
 若在下列情況下，您應該降低批次大小：  
  
-   處理大型訊息時  
  
-   當資料庫往返不是您的瓶頸  
  
> [!NOTE]
>  變更時要小心**LargeMessageThreshold**設定。 批次大小乘以平均訊息大小應該小於**LargeMessageThreshold**設定，除非批次大小為 1。  
  
## <a name="see-also"></a>另請參閱  
 [傳訊引擎](../core/the-messaging-engine.md)   
 [批次處理接收訊息處理](../core/batching-messages-for-receive-processing.md)   
 [傳送處理的批次訊息](../core/batching-messages-for-send-processing.md)