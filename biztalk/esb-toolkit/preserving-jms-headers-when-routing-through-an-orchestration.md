---
title: 透過協調流程路由時保留 JMS 標頭 |Microsoft 文件
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
ms.openlocfilehash: 362f41919a050b08bdba9c70c7771698ab71ce33
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22294670"
---
# <a name="preserving-jms-headers-when-routing-through-an-orchestration"></a>保留 JMS 標頭時透過協調流程路由
在此使用情況下，元件隨附[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]從內送訊息中擷取 Java 訊息服務 (JMS) 標頭，並再重新加以建構外寄訊息中。 這示範了 JMS 訊息標頭的保留和存取中的標頭內容，在協調流程，如圖 1 所示。  
  
 ![保留 JMS](../esb-toolkit/media/ch3-preservingjms.gif "Ch3 PreservingJMS")  
  
 **圖 1**  
  
 **保留 JMS ESB 協調流程和處理整個的標頭資訊**  
  
 隨附的 「 JMS MQRFH2 元件 」 範例[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]示範這個使用案例，並包含下列三個部分：  
  
-   第 1 部分示範失真標頭的保留，因為訊息是從 IBM WebSphere MQ，透過 ESB 和 BizTalk Server，然後再回到 IBM WebSphere MQ。  
  
-   第 2 部分會示範如何在 ESB 協調流程中的程式碼可以存取 MQRFH2 標頭屬性。 在此情況下，指令碼會修改 JMS 標頭屬性，以指定的目的地佇列的名稱。  
  
-   第 3 部分示範大量載入的佇列訊息，並顯示如何應用程式將訊息路由傳送至訊息內容中指定的目的地佇列。  
  
 如需詳細資訊，請參閱[安裝和執行 JMS MQRFH2 元件範例](../esb-toolkit/installing-and-running-the-jms-mqrfh2-component-sample.md)。