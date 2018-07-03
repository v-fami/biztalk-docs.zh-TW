---
title: 使用動態轉換 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1e4aac7-242a-41b6-8df4-4881371f44d1
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ccb83c4dc90a513367d2c914dc546eb0fd931d67
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006133"
---
# <a name="using-dynamic-transformation"></a>使用動態轉換
## <a name="overview"></a>概觀  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]動態轉換支援三種機制：  
  
- 實作為協調流程的動態轉換代理程式  
  
- 動態轉換隨附的核心 Web 服務的 Web 服務  
  
- ESB 管線元件所執行的轉換  
  
  本節著重於實作為協調流程轉換代理程式。 如需轉換 Web 服務的資訊，請參閱[使用 BizTalk ESB 工具組 Web 服務](../esb-toolkit/using-the-biztalk-esb-toolkit-web-services.md)。 ESB 發送器管線元件的相關資訊，請參閱[使用管線支援元件](../esb-toolkit/using-the-pipeline-support-components.md)。  
  
## <a name="how-it-works"></a>運作方式  
 轉換傳遞代理程式是訂閱訊息的協調流程所在**名稱**屬性的目前**ServiceInstance**路線中的項目是**Microsoft.Practices.ESB.Services.Transform**。 代理程式會執行下列一連串作業：  
  
1.  接收不具型別的的訊息 (System.Xml.XmlDocument)。  
  
2.  是否可為路線中的靜態值對應的名稱，代理程式會嘗試解析對應使用解析程式管理員的名稱。  
  
3.  它適用於適當的對應輸入的來源訊息。  
  
4.  它會將對應輸出發佈到 BizTalk Messagebox 資料庫中。  
  
## <a name="how-to-configure-dynamic-transformation"></a>如何設定動態轉換  
 如需如何設定使用路線設計工具的動態轉換的詳細資訊，請參閱[建立路線使用路線設計工具](../esb-toolkit/creating-itineraries-using-itinerary-designer.md)。  
  
## <a name="dynamic-transformation-errors"></a>動態轉換錯誤  
 動態轉換機制會建立，並在下列情況下發行 ESB 錯誤訊息：  
  
- 解析程式元件無法判斷其對應至套用。  
  
- 指定的對應不提供 （例如，您指定了不正確的對應型別或尚未部署在 BizTalk Server 2009 對應）。  
  
- 在對應期間發生失敗 （例如，來源文件不是正確的來源型別或外部組件中的自訂函式未部署到 BizTalk 對應參考）。  
  
- 在 just-in-time (JIT) 解析的地圖類型期間，發生例外狀況。  
  
- 沒有任何訂閱者存在於輸出訊息。  
  
- 系統中的任何例外狀況，就會發生。  
  
  它是開發人員必須負責提供用來填入的例外狀況訊息，並建立處理常式來回應例外狀況的內容資訊。 某些資料會自動提供，以及泛型處理常式將會挑選例外狀況訊息沒有目標處理常式是否指定或可用。 如需有關處理動態轉換例外狀況的詳細資訊，請參閱[使用 ESB 例外狀況管理](../esb-toolkit/using-esb-exception-management.md)。