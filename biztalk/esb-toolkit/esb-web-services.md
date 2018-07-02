---
title: ESB Web 服務 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c122ecdd-344a-4f76-9c73-bf692d479c09
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe1b2f6bc30982ea05717fd8e151997e2a3f90a2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973359"
---
# <a name="esb-web-services"></a>ESB Web 服務
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含下列 Web 服務：  
  
- <strong>路線入口 Web 服務。</strong>這些服務會接受外部的訊息，並提交訊息以進行處理。 路線的內容會包含描述要執行哪些服務的中繼資料和處理指示。 路由服務定義的訊息應該路由傳送，而轉換服務可讓您指定應如何轉換訊息的端點。 這些服務支援單向和雙向 （要求-回應） 處理;ASMX 和 Windows Communication Foundation (WCF) 實作提供。 路線入口 Web 服務不是訊息類型特有的因此可接受任何訊息類型。  
  
- <strong>解析程式 Web 服務。</strong>這項服務可讓外部應用程式呼叫 Microsoft ESB 解析程式架構，來查閱 ESB 解析程式 Framework 所支援的解析機制為基礎的端點。 此服務也提供 ASMX 和 WCF 實作。  
  
- <strong>轉換 Web 服務。</strong>這項服務可讓執行 Microsoft BizTalk Server 對應，無需使用 Messagebox 持續性、 擴充 BizTalk Server 的功能不會以 BizTalk Server 為基礎的應用程式的對應執行的額外負荷。 服務提供了 ASMX 和 WCF 實作。  
  
- <strong>例外狀況處理的 Web 服務。</strong>這項服務會接受來自外部來源的例外狀況訊息，並使用錯誤處理器管線的路由會標準化、 追蹤及例外狀況訊息發佈至 ESB 管理入口網站。 服務提供了 ASMX 和 WCF 實作。  
  
- <strong>UDDI Web 服務。</strong>此服務可讓應用程式和使用者查閱的服務名稱、 商業提供者或商業類別目錄為基礎的端點; 它也可讓應用程式和使用者，來操作商業提供者，而服務和分類儲存在UDDI 存放庫。 這是用的 ESB 管理入口網站與協力廠商提供者的基礎結構服務。  
  
- <strong>BizTalk 作業 Web 服務。</strong>此 ASMX 為基礎的服務會顯示有關 BizTalk Server 主控件、 協調流程、 應用程式和狀態，讓使用者和協力廠商，以輕鬆地查詢應用程式與主機的狀態，不論內的電腦上的位置BizTalk Server 群組中。 查詢可以包含訊息狀態和流程、 狀態變更、 目前的服務執行個體和訊息詳細資料。 服務也可以更新接收位置。 這是用的 ESB 管理入口網站與協力廠商提供者的基礎結構服務。  
  
  如需有關 Web 服務的一部分[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，請參閱 <<c2> [ 使用 BizTalk ESB 工具組 Web 服務](../esb-toolkit/using-the-biztalk-esb-toolkit-web-services.md)。