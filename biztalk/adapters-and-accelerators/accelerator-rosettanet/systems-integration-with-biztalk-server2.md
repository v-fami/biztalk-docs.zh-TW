---
title: 與 BizTalk Server 的系統整合 |Microsoft Docs
description: BizTalk Server 包含整合使用 XML 的訊息、 自動化商務程序使用對應和協調流程，以及處理使用不同的通訊協定，例如 FTP、 HTTP、 SMTP、 SOAP 和 SQL 系統的能力。
ms.custom: ''
ms.date: 06/08/2018
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ba3dda1-efdb-4a2b-bb3a-825d76696f15
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85dd0ce3143373428a810a4e24b3c8b4f679cc14
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969415"
---
# <a name="systems-integration-with-biztalk-server"></a>與 BizTalk Server 的系統整合
BizTalk Server 正在使用的整合伺服器[發佈和訂閱架構](../../core/publish-and-subscribe-architecture.md)。 它專為 eBusiness 應用所[使用配接器](../../core/using-adapters.md)來接收和傳送訊息，實作[透過協調流程的商務程序](../../core/defining-business-processes.md)，並包含[管理和追蹤](../../core/management-and-tracking-architecture.md)這些不同的組件。 BizTalk Server 也包含[交易夥伴管理](../../core/trading-partner-management-using-biztalk-server.md)適用於企業對企業訊息[高可用性](../../core/planning-for-high-availability3.md)若要大幅延長執行時間，一個開發平台[建立您自己元件](../../core/developing-custom-components.md)，管理主控台[管理您的成品](../../core/operational-and-administrative-tasks-in-your-biztalk-environment.md)，和商務活動監控管理[彙總、 警示和設定檔](../../core/using-business-activity-monitoring.md)。 此技術堆疊提供許多功能，可以用來開發、實作、操作和維護您的解決方案。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 提供下列整合服務，您可以使用與 Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]。 如需詳細資訊[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]integration services，請參閱 < [BizTalk Accelerator for RosettaNet ](microsoft-biztalk-accelerator-for-rosettanet-documentation.md)。
  
## <a name="message-integration"></a>訊息整合  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 會透過自動化訊息交換，整合不同的實體 (部門、商務夥伴和廠商)。 它將 XML 當做一般的溝通通訊協定使用。 並使用 XML 結構描述定義 (XSD) 結構描述來描述和驗證訊息，另外也利用 XSL 轉換 (XSLT) 將資料從一個訊息轉換到另一個。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 整合引擎會將訊息從一個位置傳送到另一個位置。 它的特色是發行者/訂閱者模型，可讓一個部門發佈文件，讓另一個部門訂閱該文件。 訂閱的部門可以在發佈的部門不知情的情形下訂閱訊息。 如此一來，即可有效地處理交易夥伴組織，透過彈性的中樞-支點安排方式取代點對點通訊。  
  
## <a name="business-process-automation"></a>商務程序自動化  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 使用所謂協調流程的程序對應，在單一程序中連結一組獨特、相關的動作，藉此自動化並整合商務程序。 透過建立協調流程，可以根據資料交換及分析來連結步驟，諸如訊息接收、訊息傳送、決策、迴圈及其他作業。 有了協調流程，就可以建立會在事件發生時自動執行的商務程序。  
  
 使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您可以動態變更根據商務規則的程序。 這種做法讓您可以依照商務的考量，彈性地變更協調流程程序中採取的措施。 例如，針對超過特定上限金額的訂單，限制其核准程序。  
  
  
## <a name="integration-of-heterogeneous-systems"></a>異質系統的整合  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 能夠整合異質環境中的 IT 系統，在這類環境中，系統以不同的溝通通訊協定傳送資料。 執行的方式是使用配接器透過不同的通訊協定連線至系統。 它支援使用 File、FTP、HTTP、SMTP、SOAP 和 SQL 配接器。 您可以透過「BizTalk 配接器架構」(BizTalk Adapter Framework) 建立自訂的配接器。 如需詳細資訊，請參閱 <<c0> [ 建立自訂配接器](../../core/developing-custom-adapters.md)。
  
## <a name="role-based-tools"></a>以角色為基礎的工具  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 是開發和執行環境中開發人員、 IT 專業人員和商務專業人員共同作業以建立、 實作、 操作、 維護及自訂系統。 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 每個角色提供自訂其使用的工具。  
  
 如需詳細資訊，請參閱 <<c0> [ 以角色為基礎的產品](../../adapters-and-accelerators/accelerator-rosettanet/a-role-based-product2.md)，並[解 RosettaNet 加速器](../../adapters-and-accelerators/accelerator-rosettanet/learn-the-rosettanet-accelerator-and-the-biztalk-tools-available.md)。
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何解決商務需求](../../adapters-and-accelerators/accelerator-rosettanet/how-biztalk-server-solves-the-business-need1.md)   
 [BizTalk Accelerator for RosettaNet 在 BizTalk Server 中新增的項目](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md)
