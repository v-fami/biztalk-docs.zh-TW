---
title: 規劃效能 |Microsoft Docs
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
ms.openlocfilehash: 452dd1a8a038ab151b98aac8ce6c4f93641f7361
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50752710"
---
# <a name="planning-for-performance"></a>規劃效能
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 是應用程式平台。 它不只是一項伺服器產品或只是開發人員的產品。 它是用來建立商務程序管理系統，以整合企業應用程式，將工作流程，自動化應用程式平台，並啟用服務導向架構。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 是取決於許多其他軟體元件。 BizTalk 應用程式平台通常包含數個下列軟體元件： Windows Server 作業系統，SQL Server [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，IIS （選擇性），外部系統的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]互動，以及非 Microsoft 配接器和元件。  
  
 由於原本就複雜的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境中，有許多考量，進行規劃效能時。 有數個預設設定適用於所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境，但有其他考量和方法，以最佳化特定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]架構。  
  
 本主題概述的所有效能最佳化時，您應該套用的預設設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。 它也提供建議進行測試和最佳化[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專為特定案例的環境。  
  
## <a name="settings-that-you-should-apply-to-all-biztalk-server-environments"></a>您應該將它套用到所有的 BizTalk Server 環境的設定  
 [操作的整備檢查清單](../technical-guides/operational-readiness-checklists.md)一節包含採用任何 BizTalk 方案之前應檢視的項目清單。 這份檢查清單包含可以效能有重大影響的動作項目您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]不論特定性質運用的 BizTalk 解決方案的環境。  
  
## <a name="considerations-for-testing-and-optimizing-a-biztalk-solution"></a>測試和最佳化 BizTalk 解決方案的考量  
 不同的 BizTalk 解決方案可能相當大的不同效能準則。 例如，BizTalk 解決方案，專為執行協調流程必須著重於接收、 轉換和對應一般檔案文件的 BizTalk 解決方案的不同的效能設定檔。 協調流程為主的解決方案可能需要大量的 CPU，或可能呼叫受益於最佳化，雖然一般檔案轉換和對應為主的解決方案可能是較耗記憶體的自訂元件。  
  
 配接器和管線用來接收和傳送文件中和共[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]對於 BizTalk 解決方案的效能也可以有深遠的影響。 此方案所需的文件追蹤的層級將也會大幅影響效能。 由於許多但內容不同的效能設定檔可能在不同的 BizTalk 解決方案中，是十分重要的是您測試 BizTalk 解決方案到測量最大持續性效能和最大持續性追蹤效能。  
  
 決定之後的最大持續性效能和最大持續性追蹤的 BizTalk 方案的效能，有特定的步驟，您可以用來移除 BizTalk 解決方案中的瓶頸。 如需詳細資訊，請參閱 < [BizTalk Server 2009 效能指南](http://go.microsoft.com/fwlink/?LinkID=150492)(http://go.microsoft.com/fwlink/?LinkID=150492)。  
  
## <a name="see-also"></a>另請參閱  
 [規劃 BizTalk Server 層](../technical-guides/planning-the-biztalk-server-tier.md)