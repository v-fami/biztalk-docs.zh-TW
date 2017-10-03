---
title: "為路線服務的訂閱者使用傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 898b461c-4d0d-4703-a8ca-7f52f3f15f70
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5213b22c1bdfaa505dbf4b62a03095bcec5a1746
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-a-send-port-as-an-itinerary-service-subscriber"></a>為路線服務的訂閱者使用傳送埠
如需如何為路線服務的訂閱者使用的傳送埠的範例，圖 1 所示動態單向傳送埠拾取訊息符合下列條件的篩選條件：  
  
-   **IsRequestResponse = False**  
  
-   **ServiceName = DynamicTest**  
  
-   **ServiceState = 暫止**  
  
-   **ServiceType = 傳訊**  
  
 ![傳送埠](../esb-toolkit/media/ch4-sendport.gif "第 4 章第傳送埠")  
  
 **圖 1**  
  
 **傳送埠篩選條件的範例**  
  
 您可以使用傳送埠篩選條件運算式來指定它將會從路線上手透過 Messagebox 資料庫拾取的訊息的屬性和值集合。  
  
> [!NOTE]
>  請務必使用特定且盡可能; 已取得焦點的篩選條件否則，會有的挑出非預期的訊息，在高容量環境中可能會造成問題的風險。 系統 Properties.xsd 的結構描述定義的篩選條件屬性的訂用帳戶。