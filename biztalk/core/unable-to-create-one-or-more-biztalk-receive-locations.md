---
title: 無法建立一或多個 BizTalk 接收位置 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b564f87b-34ba-400e-9a71-bd66081fc1b8
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b0dfc81876cba51b4dad03a01c2feb935b4fc959
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986399"
---
# <a name="unable-to-create-one-or-more-biztalk-receive-locations"></a>無法建立一或多個 BizTalk 接收位置
## <a name="details"></a>詳細資料  
  
|                 |                                                                                    |
|-----------------|------------------------------------------------------------------------------------|
|  產品名稱   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] |
| 產品版本 |             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]             |
|    事件識別碼     |                                         0                                          |
|  事件來源   |                                         0                                          |
|    元件    |                                         0                                          |
|  符號名稱  |                                         0                                          |
|  訊息文字   |              無法建立一或多個 BizTalk 接收位置。               |
  
## <a name="explanation"></a>說明  
 此錯誤表示 BizTalk WCF 發佈精靈 無法建立接收位置裝載的外掛式的 WCF 配接器。  
  
## <a name="user-action"></a>使用者動作  
 請確定該 BizTalk 執行個體已啟動。  
  
 如需有關建立接收位置，請參閱下列資源[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]文件：  
  
-   [利用外掛式 WCF 接收配接器發佈 WCF 服務](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)  
  
-   [如何設定 Wcf-basichttp 接收位置](http://msdn.microsoft.com/library/43f18e5d-ba28-453c-b8ce-5bcdc6f27fdd)  
  
-   [如何設定 Wcf-wshttp 接收位置](../core/how-to-configure-a-wcf-wshttp-receive-location.md)  
  
-   [如何設定 Wcf-customisolated 接收位置](../core/how-to-configure-a-wcf-customisolated-receive-location.md)  
  
-   [逐步解說：使用 WCF-BasicHttp 配接器發佈 WCF 服務](../core/walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter.md)