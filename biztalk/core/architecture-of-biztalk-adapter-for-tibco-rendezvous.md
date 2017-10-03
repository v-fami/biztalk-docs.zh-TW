---
title: "BizTalk Adapter for TIBCO Rendezvous 的架構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- passing messages
- architecture
- message passing
- messages, passing
ms.assetid: 174d6ceb-8e1d-4c93-827d-8155cfe47836
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 801f92453ffc85d83d57c1caa5c89ec618b96ed0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="architecture-of-biztalk-adapter-for-tibco-rendezvous"></a>BizTalk Adapter for TIBCO Rendezvous 的架構
Microsoft BizTalk Adapter for TIBCO Rendezvous 提供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 與 TIBCO Rendezvous 之間的雙向連線。 此配接器同時使用 TIBCO Rendezvous API 與 BizTalk 配接器架構 API 來提供緊密整合。  
  
 TIBCO Rendezvous 軟體產品可為企業應用程式整合 (EAI) 提供訊息匯流排。 TIBCO 可提供 C、C++、Java、Visual Basic 與 Microsoft .NET Framework 的訊息 API 以在 Microsoft Office Excel 工作表與其他自選的應用程式上接收資料摘要。  
  
## <a name="message-passing"></a>訊息傳遞  
 訊息傳遞的基本概念相當簡單：  
  
-   訊息包含單一主旨，這個主旨是由以句點分隔的多個項目所組成。 訊息會傳送至單一 Rendezvous 精靈 (但最後會廣播到其他精靈中)。  
  
-   待命程式會向精靈宣告感興趣之主旨 (使用基本萬用字元功能)，這時如果兩個精靈彼此「互連」或是事實上為同一個精靈時，就會將具有相符主旨的訊息傳遞給該待命程式。 如需詳細資訊，請參閱中的訊息[BizTalk Adapter for TIBCO Rendezvous 中的訊息](../core/messages-in-biztalk-adapter-for-tibco-rendezvous.md)。  
  
 下圖說明 BizTalk Adapter for TIBCO Rendezvous 的架構。  
  
 ![](../core/media/tibcorend-arch.gif "TibcoRend_Arch")  
  
## <a name="see-also"></a>另請參閱  
 [使用者入門](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)   
 [規劃與架構](../core/planning-and-architecture15.md)