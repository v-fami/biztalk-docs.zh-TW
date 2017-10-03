---
title: "接收位置位址找不到 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 637f3925-06ff-47b2-99db-f85e829ee318
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b1242ffc77976fb2ffcc469752d13a6f6366d7a1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="receive-location-for-address-not-found"></a>接收位置位址找不到
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|接收位置位址"{0}"找不到。 (BizTalk 接收位置可能會停用。)|  
  
## <a name="explanation"></a>說明  
 此錯誤表示已發行的外掛式的 WCF 接收位置找不到對應的接收位置。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列動作： 在 BizTalk 管理主控台中，確定該接收位置屬性所指定 receiveLocationName Web.config 檔案中 BizTalk WCF 發佈精靈產生存在且已啟動。  
  
 如需有關建立接收位置，請參閱下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [發佈 WCF 服務，利用外掛式 WCF 接收配接器](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)  
  
-   [如何設定 Wcf-basichttp 接收位置](http://msdn.microsoft.com/library/43f18e5d-ba28-453c-b8ce-5bcdc6f27fdd)  
  
-   [如何設定 Wcf-wshttp 接收位置](../core/how-to-configure-a-wcf-wshttp-receive-location.md)  
  
-   [如何設定 Wcf-customisolated 接收位置](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [逐步解說： 使用發佈 WCF 服務 Wcf-basichttp 配接器](../core/walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter.md)