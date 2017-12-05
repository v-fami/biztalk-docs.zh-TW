---
title: "路由和處理行程基礎 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8354538-e45c-487d-a380-59f497ea060f
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7600408837ed2ef40e11bc179bf0739fb15c5a61
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="itinerary-based-routing-and-processing"></a>行程為基礎的路由和處理
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]實作路由名單模式，透過使用自訂管線元件。 訊息中繼資料和其他因素，可用來判斷適當的路由名單，也稱為路線，要用於每個訊息。 此路由 slip 可以執行訊息轉換、 叫用協調流程服務，並定義訊息路由傳送 BizTalk Server 將會執行的步驟、 有效地減少從核心 BizTalk Server 引擎的訊息處理指示。  
  
 如需有關行程的處理方式的詳細資訊，請參閱[重要案例及開發工作](../esb-toolkit/key-scenarios-and-development-tasks.md)。