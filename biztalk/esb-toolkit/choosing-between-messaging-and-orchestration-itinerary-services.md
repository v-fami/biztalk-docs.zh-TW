---
title: 選擇傳訊和協調流程路線服務 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 694f929a-c830-4906-8e97-4fbd50e70133
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f98f48cc93e973b7170c854590359029a60ebf57
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26009807"
---
# <a name="choosing-between-messaging-and-orchestration-itinerary-services"></a>選擇傳訊和協調流程路線服務
路線服務可以設定為在傳訊子系統或 BizTalk Server 協調流程子系統中發生。 這些 ESB 路線傳訊服務設定來處理訊息，而且可能會在 BizTalk Server 管線 （上手或匝道） 中執行。 此選項可讓開發人員定義完全在管線中將執行服務。 當然，設定為協調流程子系統中的程序服務將會執行 BizTalk 協調流程中。  
  
## <a name="esb-itinerary-messaging-services"></a>ESB 路線訊息服務  
 BizTalk Server 管線中處理訊息時，使用 ESB 路線訊息服務會降低訊息延遲。 藉由實作單一管線背對背式服務，很可能轉換訊息多次，並將訊息路由至其端點，與單一持續性到 Messagebox 資料庫。 此外，訊息為基礎的處理，就可以解決協調流程處理的其他資源成本。 一般而言，訊息為基礎的處理較大量的資源，並提供處理比協調流程為基礎的處理速度。 在管線中，ESB 發送器和 ESB 發送器解譯管線元件所提供[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]做為訊息攔截器，並執行以傳訊為基礎的路線服務、 它是否路由、 轉換或自訂服務。 如需有關如何設定這些元件的詳細資訊，請參閱[ESB 發送器元件](../esb-toolkit/the-esb-dispatcher-component.md)和[ESB 發送器解譯元件](../esb-toolkit/the-esb-dispatcher-disassemble-component.md)。  
  
## <a name="esb-itinerary-orchestration-services"></a>ESB 路線的協調流程服務  
 如果動態路由，必須發生在協調流程之後或之間，使用路線服務協調流程為基礎的處理。 根據預設，協調流程為基礎的服務會接收的訊息，以 XML 文件。 路由協調流程會使用解析程式管理員，嘗試解決路線中識別的端點。 配接器管理員會使用回應從解析程式管理員要將端點詳細資料升級至訊息內容，並發佈訊息至 Messagebox 資料庫，使用直接繫結邏輯連接埠。 此時，一般 BizTalk 路由，而使用訊息的升級的屬性設定動態傳送埠。  
  
 內含的路線服務的協調流程會提供很好的起點建立自訂協調流程路線服務。 如需有關如何建立自訂的路線服務的詳細資訊，請參閱[修改和擴充 BizTalk ESB Toolkit](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md)。