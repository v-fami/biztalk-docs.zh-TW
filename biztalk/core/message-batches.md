---
title: "訊息批次 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f893d16-2670-4463-9a89-6f5be912a045
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25866ac076d77eae13d2ab5378a7582f584b6670
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-batches"></a>訊息批次
需要同時處理配接器的訊息群組時，您應該批次處理這些訊息，以最佳化效能。 就程式設計來說，訊息批次是具有關聯作業的訊息集合。 將批次中的訊息分組，而不個別提交每個訊息，您可以最佳化使用資源和處理工作。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用批次處理，以：  
  
-   攤銷許多訊息的交易成本。  
  
-   藉由減少資料庫往返內部數目來提高速度。  
  
-   以非同步方式處理訊息，以便更有效地使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行緒集區。  
  
 批次是不可部分完成的工作單位。 也就是說，其中的所有作業不是全部成功就是全部失敗。 如果批次內其中一個作業成功而另一個失敗，則組成批次的所有作業都是無效的，而且必須重新提交這些訊息。 這表示，為了回應失敗的批次，配接器必須執行三項作業：  
  
-   判斷哪些訊息失敗。  
  
-   決定失敗訊息的處理方式。  
  
-   重新提交未失敗的訊息。