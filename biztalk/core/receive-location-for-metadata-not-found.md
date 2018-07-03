---
title: 找不到的中繼資料的接收位置 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3c397fb5-f400-4cff-85b9-5bf0d2069557
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d4ae137cc48d5df142c2917b0d40fd2bc95e36dd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011591"
---
# <a name="receive-location-for-metadata-not-found"></a>找不到的中繼資料的接收位置
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                       |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                          [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                           |
| 產品版本 |                                      [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                       |
|    事件識別碼     |                                                                   0                                                                   |
|  事件來源   |                                                                   0                                                                   |
|    元件    |                                                                   0                                                                   |
|  符號名稱  |                                                                   0                                                                   |
|  訊息文字   | 接收位置"{0}「 找不到的中繼資料。 （請檢查 Web.config 中的接收位置對應，並確認 接收位置存在）。 |
  
## <a name="explanation"></a>說明  
 此錯誤表示已發行的外掛式的 WCF 接收位置找不到對應的接收位置的中繼資料。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列動作： 在 BizTalk 管理主控台中，請確定該接收位置屬性所指定 receiveLocationName Web.config 檔案中 BizTalk WCF 發佈精靈產生存在，且已啟動。  
  
 如需有關接收位置，請參閱下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  
  
-   [發佈 WCF 服務](../core/publishing-wcf-services.md)  
  
-   [如何設定 Wcf-basichttp 接收位置](http://msdn.microsoft.com/library/43f18e5d-ba28-453c-b8ce-5bcdc6f27fdd)  
  
-   [如何設定 Wcf-wshttp 接收位置](../core/how-to-configure-a-wcf-wshttp-receive-location.md)  
  
-   [如何設定 Wcf-customisolated 接收位置](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [逐步解說：使用 WCF-NetMsmq 配接器發佈 WCF 服務](../core/walkthrough-publishing-wcf-services-with-the-wcf-netmsmq-adapter.md)