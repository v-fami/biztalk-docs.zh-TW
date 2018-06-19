---
title: 分散-集中模式實作多個 Web 服務引動過程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 912512a4-9649-40df-bb82-b8f4b85c8ca6
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2682418922c17fd4c6fbe8a6bffbac51051f7841
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26010655"
---
# <a name="implementing-the-scatter-gather-pattern-for-multiple-web-service-invocations"></a>分散-集中模式實作多個 Web 服務引動過程
在此使用案例中，訊息會包含指定多個 BizTalk Server 應該存取的外部服務路線服務步驟。 它使用動態解析來判斷服務位置並傳回的資料轉換對應的端點和任何選用的 BizTalk 服務。 此服務的協調流程會執行轉換和引動過程，和所有服務引動過程會以非同步方式都發生。 所有服務引動過程都完成之後，路線服務彙總成單一的回應訊息的回應，並將訊息傳送至用戶端透過動態指派的端點。 圖 1 說明此使用案例。  
  
 ![實作散佈收集模式](../esb-toolkit/media/ch3-implementingscatter.gif "Ch3 ImplementingScatter")  
  
 **圖 1**  
  
 **實作多個 Web 服務引動過程的分散-集中模式**  
  
 分散-集中範例隨附[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]示範這個使用案例。  
  
 如需詳細資訊，請參閱[安裝及執行分散-集中範例](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md)。