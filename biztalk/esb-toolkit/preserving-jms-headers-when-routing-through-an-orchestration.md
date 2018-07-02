---
title: 透過協調流程路由時保留 JMS 標頭 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d9a59ff3-0cbf-499f-92b2-cf5b808d8b3f
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 142bd0d2e5ff86362fe3c3ffa7ef8ec256202708
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979711"
---
# <a name="preserving-jms-headers-when-routing-through-an-orchestration"></a>透過協調流程路由時保留 JMS 標頭
在此使用案例中，元件隨附[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]擷取內送訊息的 Java 訊息服務 (JMS) 標頭，然後重新加以建構外寄訊息。 這示範 JMS 訊息標頭保留及從協調流程內的標頭內容的存取 圖 1 所示。  
  
 ![保留 JMS](../esb-toolkit/media/ch3-preservingjms.gif "Ch3 PreservingJMS")  
  
 **圖 1**  
  
 **保留 JMS 標頭資訊，在 ESB 協調流程和處理**  
  
 JMS MQRFH2 元件範例隨附[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]示範這個使用案例，並包含下列三個部分：  
  
- 第 1 部分示範失真標頭保留從 IBM WebSphere MQ，透過 ESB 和 BizTalk Server，再回到 IBM WebSphere MQ 會傳送的訊息。  
  
- 第 2 部分示範如何在 ESB 協調流程中的程式碼可以存取 MQRFH2 標頭屬性。 在此情況下，指令碼會修改 JMS 標頭屬性，以指定目的地佇列名稱。  
  
- 第 3 部分示範大量載入的佇列訊息，並顯示應用程式將訊息路由至訊息內容中指定的目的地佇列的方式。  
  
  如需詳細資訊，請參閱 <<c0> [ 安裝和執行 JMS MQRFH2 元件範例](../esb-toolkit/installing-and-running-the-jms-mqrfh2-component-sample.md)。