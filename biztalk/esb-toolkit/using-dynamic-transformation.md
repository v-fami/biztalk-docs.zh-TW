---
title: 使用動態轉換 |Microsoft 文件
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
ms.openlocfilehash: 1d7f6bc57d009e558188950d9bcb0387f808f835
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295406"
---
# <a name="using-dynamic-transformation"></a>使用動態轉換
## <a name="overview"></a>概觀  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]支援三種機制，用於動態轉換：  
  
-   做為協調流程實作動態轉換代理程式  
  
-   動態轉換包含在核心 Web 服務的 Web 服務  
  
-   ESB 管線元件所執行的轉換  
  
 本節著重於實作為協調流程轉換代理程式。 如需轉換 Web 服務的資訊，請參閱[使用 BizTalk ESB 工具組 Web 服務](../esb-toolkit/using-the-biztalk-esb-toolkit-web-services.md)。 ESB 發送器管線元件的相關資訊，請參閱[使用管線支援元件](../esb-toolkit/using-the-pipeline-support-components.md)。  
  
## <a name="how-it-works"></a>運作方式  
 轉換傳遞代理程式是訂閱訊息的協調流程其中**名稱**屬性的目前**ServiceInstance**路線中的項目是**Microsoft.Practices.ESB.Services.Transform**。 代理程式會執行下列一系列的作業：  
  
1.  接收不具型別的的訊息 (System.Xml.XmlDocument)。  
  
2.  如果對應的名稱可為靜態值路線，代理程式會嘗試使用解析程式管理員在對應的名稱解析。  
  
3.  它會套用適當的對應到輸入的來源訊息。  
  
4.  它會將對應輸出發佈到 BizTalk Messagebox 資料庫中。  
  
## <a name="how-to-configure-dynamic-transformation"></a>如何設定動態轉換  
 如需如何設定動態轉換使用路線設計工具的詳細資訊，請參閱[旅使用路線設計師建立](../esb-toolkit/creating-itineraries-using-itinerary-designer.md)。  
  
## <a name="dynamic-transformation-errors"></a>動態轉換錯誤  
 動態轉換機制將會建立，並在下列情況下發行 ESB 錯誤訊息：  
  
-   無法判斷解析程式元件，其對應至套用。  
  
-   不提供指定的對應 （例如，您指定不正確的地圖類型或在 BizTalk Server 2009 尚未部署的對應）。  
  
-   在對應期間發生失敗 （例如，來源文件不是正確的來源型別或外部組件中的自訂函式不會部署至 BizTalk 對應參考）。  
  
-   在 just-in-time (JIT) 解析的地圖類型期間，發生例外狀況。  
  
-   沒有任何訂閱者有輸出訊息。  
  
-   發生任何系統例外狀況。  
  
 它是開發人員必須負責提供用來填入例外狀況訊息，並建立回應的例外狀況處理常式的內容資訊。 某些資料會自動使用，而且泛型處理常式將會收取例外狀況訊息沒有目標處理常式是否指定或可用。 如需動態轉換例外狀況處理的詳細資訊，請參閱[使用 ESB 例外狀況管理](../esb-toolkit/using-esb-exception-management.md)。