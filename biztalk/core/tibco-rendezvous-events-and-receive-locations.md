---
title: "TIBCO Rendezvous 事件與接收位置 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: receive locations, life cycle
ms.assetid: 3576af82-4723-4efc-961e-40b1150cf13d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e9278687ff212fc2368eca138780417d7c052824
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tibco-rendezvous-events-and-receive-locations"></a>TIBCO Rendezvous 事件與接收位置
所有 TIBCO Rendezvous 系統均可傳送訊息給它們選擇的主體名稱。 概念*事件*是訊息的其他 TIBCO Rendezvous 程式產生。  
  
 下列步驟說明接收位置的生命週期：  
  
1.  接收位置已建立。  
  
2.  接收位置已和主控件建立關聯。  
  
3.  接收位置已繫結到協調流程。  
  
4.  接收位置已啟用。  
  
5.  接收位置收到訊息。  
  
> [!IMPORTANT]
>  每個接收位置都必須有一個唯一的名稱。 在同一個 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 部署中，不能有兩個相同名稱的接收位置。  
  
> [!IMPORTANT]
>  建議您在接收位置的放置位置中設定強式存取控制清單 (ACL)。 例如，您必須在檔案接收位置拾取訊息的目錄中設定強式 ACL，讓只有經過授權的使用者可以在此位置放置訊息。  
  
## <a name="see-also"></a>另請參閱  
 [建立 TIBCO Rendezvous 接收處理常式](../core/creating-tibco-rendezvous-receive-handlers.md)