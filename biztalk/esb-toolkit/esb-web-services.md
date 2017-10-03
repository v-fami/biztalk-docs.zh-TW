---
title: "ESB Web 服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c122ecdd-344a-4f76-9c73-bf692d479c09
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94e6f59770e14e14ed9599d0c26bae187f340e59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="esb-web-services"></a>ESB Web 服務
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含下列 Web 服務：  
  
-   **路線上手 Web 服務。**這些服務會接受外部的訊息，並提交訊息以供處理。 內容的行程包含中繼資料和處理指示，說明要執行哪些服務。 路由服務會定義的端點的訊息應路由，雖然轉換服務指定轉換訊息的方式。 這些服務支援單向和雙向 （要求-回應） 處理。ASMX 和 Windows Communication Foundation (WCF) 實作所提供。 行程上手 Web 服務不是訊息類型特有的因此可接受任何訊息類型。  
  
-   **解析程式的 Web 服務。**此服務可讓外部應用程式呼叫 Microsoft ESB 解析程式架構，來查閱 ESB 端點解析程式 Framework 所支援的解析機制為基礎。 服務也提供 ASMX 和 WCF 實作。  
  
-   **轉換的 Web 服務。**此服務可讓執行 Microsoft BizTalk Server 對應訊息方塊的持續性，不會以 BizTalk Server 為基礎的應用程式的對應執行擴充的 BizTalk Server 功能的額外負荷。 服務提供 ASMX 和 WCF 實作。  
  
-   **例外狀況處理的 Web 服務。**這項服務會接受來自外部來源的例外狀況訊息，並使用錯誤處理器管線的路由會正規化、 追蹤和例外狀況訊息發佈至 ESB 管理入口網站。 服務提供 ASMX 和 WCF 實作。  
  
-   **UDDI Web 服務。**此服務可讓應用程式和使用者查閱根據服務名稱、 商業提供者或商務分類的端點; 它也可讓應用程式和使用者管理商務提供者服務和分類儲存在UDDI 儲存機制。 這是 ESB 管理入口網站和協力廠商提供者所使用的基礎結構服務。  
  
-   **BizTalk 作業 Web 服務。**此 ASMX 為基礎的服務會顯示有關 BizTalk Server 主控件、 協調流程、 應用程式和狀態，讓使用者和第三方，以輕鬆地查詢應用程式與主機的狀態，不論內的電腦上的位置BizTalk Server 群組。 查詢可以包含訊息狀態和流程、 變更狀態、 目前的服務執行個體和訊息詳細資料。 也可以更新服務的接收位置。 這是 ESB 管理入口網站和協力廠商提供者所使用的基礎結構服務。  
  
 如需有關 Web 服務的一部分[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，請參閱[使用 BizTalk ESB 工具組 Web 服務](../esb-toolkit/using-the-biztalk-esb-toolkit-web-services.md)。