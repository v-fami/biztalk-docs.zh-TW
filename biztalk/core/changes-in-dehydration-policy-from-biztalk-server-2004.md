---
title: "從 BizTalk Server 2004 的凍結原則變更 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c760bffe-5f64-4eb2-bc23-89d7c9310f39
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9daf93fd6c925e5412aef3f4e985dd966f576eee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="changes-in-dehydration-policy-from-biztalk-server-2004"></a>BizTalk Server 2004 中的凍結原則變更
[!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] 中的 BizTalk Server 凍結原則已經變更，與 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 不同。 以下透過決定 [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] 中凍結狀況的布林值 (true = 凍結)，摘要說明 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 與 [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] 的差異。  
  
```  
Dehydrate = (WaitingHistory == -1 OR WaitingHistory > TestThreshold)  
```  
  
 凍結原則[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]次要如此已變更。 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]一律會凍結在接收/延遲/接聽 如果等待時間超過 2 ***MaxThreshold**。