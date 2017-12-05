---
title: "瞭解 BizTalk Adapter for mySAP Business Suite |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapter features
- adapters, features
- .NET Framework Data Provider for mySAP Business Suite
- Data Provider for SAP
- features of SAP adapter
- adapters, about SAP ADO Provider
ms.assetid: 136ca828-2724-454b-9d4d-a491d45e1eda
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5d04c435208e316c343ac7b307943e0f91b8af7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="understand-biztalk-adapter-for-mysap-business-suite"></a>瞭解 BizTalk Adapter for mySAP Business Suite
[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]啟用服務導向程式設計的存取，以便與外部系統互動。 配接器用戶端提供下列優點：  
  
-   **一致的設計階段經驗**。 配接器會提供瀏覽、 搜尋和擷取的 LOB 成品的中繼資料的一般和使用者易記的設計階段經驗。  
  
-   **各種程式設計選項**。 配接器提供的程式設計模型包括 Windows Communication Foundation (WCF) 通道模型、 WCF 服務模型、 ADO.NET、 web 服務或 BizTalk 支援模型的選擇。  
  
-   **跨 Lob 統一經驗**。 標準化使用 WCF 配接器和[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，因此提供一致的體驗的任何 LOB 系統的存取。  
  
 如所述，配接器會建立最上層的[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]。 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供通用的基礎建置各種 BizTalk Server 和 Microsoft Office 等用戶端應用程式可以取用的整合配接器。 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]對齊由公開為 Windows Communication Foundation (WCF) 通道整合配接器的 Microsoft 服務策略配接器的策略。 如需有關[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，請參閱[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]文件。 連同安裝文件[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]通常下\<安裝磁碟機\>: \Program Files\\[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]\Documents。  
  
 若要執行的 SAP 系統上的作業，配接器用戶端必須存取相關的遠端函式呼叫 (Rfc)、 商務應用程式發展介面 (Bapi)，和 Idoc （或中繼文件）。 SAP / 3 系統公開 Rfc、 Bapi，與 Idoc 適用於商務整合。 Rfc 是實作特定的商務邏輯的遠端函式模組。 可以叫用這個邏輯，例如 BizTalk Server 外部應用程式或.NET 應用程式。 Bapi 是 SAP 商務物件，又公開會透過標準的 RFC 介面方法的介面。 Idoc 是抽象的電子資料交換 (EDI) 通訊層的 SAP 和非 SAP 系統之間進行通訊的機制。 與[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]、 您可以存取的 Rfc Bapi，和 SAP 系統所公開的 Idoc。  
  
 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]也包含[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]，這樣會提供 SAP 系統的 ADO 介面。  
  
 此區段會列出的功能[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]和[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [BizTalk adapter for mySAP Business Suite 的架構概觀](../../adapters-and-accelerators/adapter-sap/architecture-overview-of-the-biztalk-adapter-for-mysap-business-suite.md)  
  
-   [SAP 配接器中的主要功能](../../adapters-and-accelerators/adapter-sap/key-features-in-the-sap-adapter.md)  
  
-   [BizTalk Adapter for mySAP Business Suite 的限制](../../adapters-and-accelerators/adapter-sap/limitations-of-biztalk-adapter-for-mysap-business-suite.md)  
  
-   [關於 .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)  
  
## <a name="see-also"></a>請參閱  
[開始使用 BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/get-started-with-the-biztalk-adapter-for-mysap-business-suite.md)