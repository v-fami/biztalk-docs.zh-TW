---
title: 規劃效能 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 267a8bc6-a0ab-4335-bc04-c22d5a56792f
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fac21f0b483ac3cbaec64c48b524a17422cb146
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22302998"
---
# <a name="planning-for-performance"></a>規劃效能
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]是應用程式平台。 它不只伺服器產品或只在開發人員的產品。 它是用來建立商務程序管理系統，來整合企業應用程式，來將工作流程，自動化應用程式平台，而且若要啟用服務導向架構。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]是取決於許多其他軟體元件。 BizTalk 應用程式平台通常包含數個下列軟體元件： Windows Server 作業系統，SQL Server [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，IIS （選擇性） 外部系統的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]互動，以及非 Microsoft 配接器和元件。  
  
 由於原本就複雜的本質之故[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境中，有許多考量進行規劃效能時。 有數個適用於所有的預設設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境並有其他考量和方法可用來最佳化特定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]架構。  
  
 本主題提供所有效能都最佳化時，您應該套用的預設設定的總覽[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。 它也提供建議的測試和最佳化[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專為特定案例的環境。  
  
## <a name="settings-that-you-should-apply-to-all-biztalk-server-environments"></a>您應該將它套用到所有的 BizTalk Server 環境的設定  
 [操作的整備檢查清單](../technical-guides/operational-readiness-checklists.md)區段本指南包含採用任何 BizTalk 方案之前應檢視的項目清單。 此檢查清單包含可以的效能有重大影響的動作項目您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]運用 BizTalk 解決方案的特定本質不論環境。  
  
## <a name="considerations-for-testing-and-optimizing-a-biztalk-solution"></a>測試和最佳化 BizTalk 方案的考量  
 不同的 BizTalk 解決方案可能有些大相逕庭效能準則。 例如，建置周圍執行協調流程的 BizTalk 解決方案必須比著重於接收、 轉換及對應一般檔案文件的 BizTalk 解決方案的不同的效能設定檔。 協調流程已取得焦點的解決方案可能需要大量的 CPU，或可能會呼叫自訂元件時的一般檔案轉換及對應已取得焦點的方案可能更多的記憶體密集受益最佳化。  
  
 配接器和管線用來接收和傳送的文件中和 out[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可能也會影響深遠的 BizTalk 方案的效能。 此方案所需的文件追蹤的層級將也會大幅影響效能。 許多但內容不同的效能設定檔可能在不同的 BizTalk 方案中，因為它是關鍵，則測試 BizTalk 方案來測量最大持續性效能和最大持續性追蹤效能。  
  
 決定之後的最大持續性效能和最大持續性追蹤的 BizTalk 解決方案的效能，有特定的步驟，您可以運用 BizTalk 方案中移除的瓶頸。 如需詳細資訊，請參閱[BizTalk Server 2009 效能指南](http://go.microsoft.com/fwlink/?LinkID=150492)(http://go.microsoft.com/fwlink/?LinkID=150492)。  
  
## <a name="see-also"></a>另請參閱  
 [規劃 BizTalk Server 層](../technical-guides/planning-the-biztalk-server-tier.md)