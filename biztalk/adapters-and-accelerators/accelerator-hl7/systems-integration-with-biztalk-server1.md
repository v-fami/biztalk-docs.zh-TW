---
title: "利用 BizTalk Server1 系統整合 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- system integration
- BizTalk Server, tools
- business processes, automating
- BTAHL7, BizTalk Server
- BizTalk Server
- BizTalk Server, business process automation
- BizTalk Server, messages
- BizTalk Server, system integration
ms.assetid: 8f66a4fc-186c-415f-a7ed-31f620f0495f
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13eba7a4a799803340d2757bd39c3e5e9844603e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="systems-integration-with-biztalk-server"></a>與 BizTalk Server 進行系統整合
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] 是專為電子商務應用程式設計的整合伺服器。 此系統建置[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsWinSvrNoVersion](../../includes/btswinsvrnoversion-md.md)]系統平台，包括[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]Windows Server 2008， [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]，和[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)]，並利用的功能[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[vs2012](../../includes/vs2012-md.md)]. 此技術堆疊提供許多功能，可以用來開發、實作、操作和維護您的解決方案。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]提供下列整合服務可讓您搭配[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)])。 如需有關 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 整合服務的詳細資訊，請參閱「[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] 說明」。  
  
## <a name="message-integration"></a>訊息整合  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]藉由自動化訊息交換，整合不同的實體 （部門、 商務合作夥伴、 廠商、 等等）。 它會使用可延伸標記語言 (XML) 做為一般的通訊協定。 並使用 XML 結構描述定義 (XSD) 結構描述來描述和驗證訊息，另外也利用 XSL 轉換 (XSLT) 將資料從一個訊息轉換到另一個。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 整合引擎會將訊息從一個位置傳送到另一個位置。 它的特色是發行者/訂閱者模型，可讓一個部門發佈文件，讓另一個部門訂閱該文件。 訂閱的部門可以在發佈的部門不知情的情形下訂閱訊息。 如此一來，即可有效地處理交易夥伴組織，透過彈性的中樞-支點安排方式取代點對點通訊。  
  
## <a name="business-process-automation"></a>商務程序自動化  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]自動化並整合商務程序，透過呼叫協調流程的程序對應連結一組獨特、 相關的動作，以單一處理序。 透過建立協調流程，可以根據資料交換及分析來連結步驟，諸如訊息接收、訊息傳送、決策、迴圈及其他作業。 協調流程可讓您建立商務程序，將會在事件發生時自動執行。  
  
 使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您可以動態變更商務規則為基礎的處理序。 這種做法讓您可以依照商務的考量，彈性地變更協調流程程序中採取的措施。 例如，針對超過特定上限金額的訂單，限制其核准程序。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]也可讓您透過 「 人力工作流程服務自動化的協調流程內納入人為操作。  
  
## <a name="integration-of-heterogeneous-systems"></a>異質系統的整合  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 能夠整合異質環境中的 IT 系統，在這類環境中，系統以不同的溝通通訊協定傳送資料。 執行的方式是使用配接器透過不同的通訊協定連線至系統。 它支援檔案、 FTP、 HTTP、 SMTP、 SOAP 和 SQL 配接器的使用。 您可以透過「BizTalk 配接器架構」(BizTalk Adapter Framework) 建立自訂的配接器。  
  
## <a name="role-based-tools"></a>以角色為基礎的工具  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]是開發人員、 IT 專業人員和商務專業人員建立、 實作、 操作、 維護及自訂系統以合作的開發和執行環境。 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]每個角色提供專門針對其使用的工具。  
  
 如需詳細資訊，請參閱[為基礎的角色為基礎的產品](../../adapters-and-accelerators/accelerator-hl7/a-role-based-product1.md)，和[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]幫助。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Accelerator for HL7 新增至 BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/what-biztalk-accelerator-for-hl7-adds-to-biztalk-server.md)