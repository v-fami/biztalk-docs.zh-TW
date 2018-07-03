---
title: 無法註冊位址的外掛式的接收器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 313b436a-d7c5-4b46-bfe3-bbad0d8efe42
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e33aa3e48cd92b3d190289c1d65bf3a3bb7c7907
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986615"
---
# <a name="failed-to-register-isolated-receiver-for-address"></a>無法註冊位址的外掛式的接收器
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                         |
|-----------------|---------------------------------------------------------------------------------------------------------|
|  產品名稱   |           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]            |
| 產品版本 |                       [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                        |
|    事件識別碼     |                                                    0                                                    |
|  事件來源   |                                                    0                                                    |
|    元件    |                                                    0                                                    |
|  符號名稱  |                                                    0                                                    |
|  訊息文字   | 無法註冊位址的外掛式的接收器 」{0}"; 接收位置不存在或已停用。 |
  
## <a name="explanation"></a>說明  
 此錯誤表示已發行的外掛式的 WCF 接收位置找不到對應的接收位置。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列動作： 在 BizTalk 管理主控台中，請確定該接收位置屬性所指定 receiveLocationName Web.config 檔案中 BizTalk WCF 服務發佈精靈產生存在，而且是已啟動。  
  
 如需有關建立接收位置，請參閱下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  
  
-   [利用外掛式 WCF 接收配接器發佈 WCF 服務](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)  
  
-   [如何設定 Wcf-basichttp 接收位置](http://msdn.microsoft.com/library/43f18e5d-ba28-453c-b8ce-5bcdc6f27fdd)  
  
-   [如何設定 Wcf-wshttp 接收位置](../core/how-to-configure-a-wcf-wshttp-receive-location.md)  
  
-   [如何設定 Wcf-customisolated 接收位置](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [逐步解說：使用 WCF-BasicHttp 配接器發佈 WCF 服務](../core/walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter.md)