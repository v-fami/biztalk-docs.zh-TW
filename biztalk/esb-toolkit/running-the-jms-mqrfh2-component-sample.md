---
title: "執行 JMS MQRFH2 元件範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 44f4b48c-398a-4ec1-a033-1fc4a76a305c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4fcea4bca324f73ee37b63e78673140eae250692
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-jms-mqrfh2-component-sample"></a>執行 JMS MQRFH2 元件範例
JMS MQRFH2 元件 」 範例包含三個部分：  
  
-   [執行 JMS MQRFH2 標頭保留範例](../esb-toolkit/running-the-jms-mqrfh2-header-preservation-sample.md)。 因為訊息是從 IBM WebSphere MQ，透過 ESB 和 Microsoft BizTalk Server，然後再回到 IBM WebSphere MQ 這個部分會示範失真標頭的保留。  
  
-   [從協調流程 」 範例執行標頭屬性存取](../esb-toolkit/running-the-header-property-access-from-an-orchestration-sample.md)。 此組件會示範如何 ESB 協調流程內的程式碼可以存取 MQRFH2 標頭屬性。 在此情況下，程式碼會使用標頭屬性來指定目的地佇列名稱。  
  
-   [執行大量載入以內容為基礎的路由範例](../esb-toolkit/running-the-bulk-load-content-based-routing-sample.md)。 此部分示範如何在大量載入的佇列訊息，並顯示如何應用程式將訊息路由傳送至訊息內容中指定的目的地佇列。