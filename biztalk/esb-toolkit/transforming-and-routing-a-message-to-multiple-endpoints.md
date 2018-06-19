---
title: 轉換，並將訊息路由傳送至多個端點 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 544db12c-95fc-4321-b397-ec9e7410e37d
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c0fc2b3b9893607f760c564d03fc6090a7f1ea0
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26010239"
---
# <a name="transforming-and-routing-a-message-to-multiple-endpoints"></a>轉換，並將訊息路由傳送至多個端點
在此使用案例中，ESB 執行轉換，透過路線 Web 服務上手提交的訊息。 動態解析查閱決定對應名稱，並將轉換輸入的訊息。 此外，路線指定 n 個行程服務會以動態方式解析並，它會將訊息路由傳送已轉換的目標端點。 所有作業都發生在傳訊層，如圖 1 所示。  
  
 ![轉換多個端點](../esb-toolkit/media/ch3-transformingmultipleendpoints.gif "Ch3 TransformingMultipleEndpoints")  
  
 **圖 1**  
  
 **轉換，並將訊息路由傳送至多個端點**  
  
 動態解析 」 範例隨附[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]示範這個使用案例。 它會顯示如何使用 ESB 管線元件，特別是，ESB 分派解譯器元件，以動態解析端點位置、 設定路由的屬性，並解析以及執行 BizTalk Server 對應，則在訊息層級，而不使用協調流程。 它也示範單向和雙向的訊息模式。  
  
 如需詳細資訊，請參閱[安裝及執行動態解析範例](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)和[安裝及執行多個 Web 服務範例](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md)。