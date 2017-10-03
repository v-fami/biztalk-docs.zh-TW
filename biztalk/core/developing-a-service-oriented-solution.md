---
title: "開發服務導向解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tutorials, developing
- service solution tutorial, background information
- service solution tutorial, developing
- developing, tutorials
- developing, service solution tutorial
ms.assetid: 7979a05c-7fd3-4476-a623-55de8abdc493
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d8e33baa51a551d0f1f851410fda696abc96983
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="developing-a-service-oriented-solution"></a>開發服務導向解決方案
服務導向解決方案示範 Woodgrove Bank 的信用帳務系統。 關於帳戶的資訊取自三種舊有系統：提供信用額度的 SAP 系統，執行於大型主機上的暫止交易系統，以及使用 MQSeries 的付款追蹤系統。 結餘檢查要求透過 Web 服務或「互動式語音應答」(IVR) 系統執行。 如需有關案例的詳細資訊，請參閱[瞭解服務導向解決方案](../core/understanding-the-service-oriented-solution.md)。  
  
 此《開發人員手冊》提供一種方法，用來建置 Woodgrove Bank 實例的服務導向架構解決方案。 本手冊從考慮符合產業標準模式的可行解決方案著手。 ＜服務導向方案模式＞一節會開始將該模式轉譯成 BizTalk 應用程式的適當成品。 下一節的＜服務導向方案元件＞，則會摘要介紹應用程式的各個部分及其關聯。 ＜實作重點＞一節則會討論為符合實例準則所需執行的特殊工作，例如使用「企業單一登入」。 ＜配合 BAM 監控服務導向方案＞一節，則說明該方案如何使用 BAM API 來追蹤要求和結果的進度。 ＜版本管理服務導向方案＞和＜擴充服務導向方案＞等節內容，則會介紹擴充或修改方案的方法。 參考章節會列出解決方案中的檔案，並提供訊息的參考。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [模式在服務導向解決方案](../core/patterns-in-the-service-oriented-solution.md)  
  
-   [元件的服務導向解決方案](../core/components-of-the-service-oriented-solution.md)  
  
-   [實作會反白顯示的服務導向解決方案](../core/implementation-highlights-of-the-service-oriented-solution.md)  
  
-   [監控服務導向 BAM 解決方案](../core/monitoring-the-service-oriented-solution-with-bam.md)  
  
-   [版本控制服務導向解決方案](../core/versioning-the-service-oriented-solution.md)  
  
-   [擴充服務導向解決方案](../core/scaling-the-service-oriented-solution.md)  
  
-   [服務導向解決方案參考](../core/service-oriented-solution-reference.md)