---
title: "對應階段 （可復原交換處理） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 544d85c7-bc47-46c1-8990-82b48a8f2f23
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20b3e45cf337702457dc8e5986db54df6bea5e5d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="mapping-phase-recoverable-interchange-processing"></a>對應階段 (可復原交換處理)
根據預設，當交換中的訊息在接收埠的對應階段失敗時，整個交換就會暫停。 您可以藉由新增名為的屬性來變更此行為**BTS。SuspendMessageOnMapFailure**至訊息內容，而藉由設定內容屬性的值`True`從管線元件。 當此屬性設定為 `True` 時，「結束點管理員」會將對應期間失敗的訊息放到擱置佇列，並繼續處理交換中的其餘訊息。  
  
 下列程式碼中設定的值**SuspendMessageOnFailure**屬性設定為 True。  
  
```  
  
public IBaseMessage Execute(IPipelineContext pc, IBaseMessage inmsg)  
{  
    bool bSuspend = true;  
    inmsg.Context.Write("SuspendMessageOnMappingFailure", "http://schemas.microsoft.com/BizTalk/2003/system-properties", bSuspend);   
    …  
}  
  
```