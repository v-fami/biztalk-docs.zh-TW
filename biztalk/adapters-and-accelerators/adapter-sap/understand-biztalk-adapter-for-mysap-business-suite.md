---
title: 了解 BizTalk Adapter for mySAP Business Suite |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapter features
- adapters, features
- .NET Framework Data Provider for mySAP Business Suite
- Data Provider for SAP
- features of SAP adapter
- adapters, about SAP ADO Provider
ms.assetid: 136ca828-2724-454b-9d4d-a491d45e1eda
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 709833ecec71a98e0e09d2cd660b68bf5b647d8b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985607"
---
# <a name="understand-biztalk-adapter-for-mysap-business-suite"></a>了解 BizTalk Adapter for mySAP Business Suite
[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]啟用服務導向程式設計的存取，以便與外部系統進行互動。 配接器用戶端提供下列優點：  
  
- **一致的設計階段經驗**。 配接器會提供瀏覽、 搜尋和擷取中繼資料的 LOB 成品的一般和方便使用的設計階段體驗。  
  
- **各種程式設計選項**。 配接器提供選擇的程式設計模型包括 Windows Communication Foundation (WCF) 通道模型、 WCF 服務模型、 ADO.NET、 web 服務或 BizTalk 支援模型。  
  
- **統一的體驗，跨 Lob**。 使用 WCF 配接器將標準化和[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，因此提供一致的體驗的任何 LOB 系統的存取。  
  
  如前所述，配接器是以 WCF LOB 配接器 SDK 為基礎。 WCF LOB 配接器 SDK 建置可取用各種不同的用戶端應用程式，例如 BizTalk Server 和 Microsoft Office 的整合配接器提供的通用基礎。 WCF LOB 配接器 SDK 公開為 Windows Communication Foundation (WCF) 通道的整合配接器會將對齊配接器策略，Microsoft 服務策略。 如需有關 WCF LOB 配接器 SDK 的詳細資訊，請參閱 < [WCF LOB 配接器 SDK 文件](../../adapters-and-accelerators/wcf-lob-adapter-sdk/microsoft-wcf-line-of-business-adapter-sdk-documentation.md)。
  
  若要執行 SAP 系統上的作業，配接器用戶端必須存取相關的遠端函式呼叫 (Rfc)、 商務應用程式發展介面 (Bapi) 和 Idoc （或中繼文件）。 SAP R/3 系統會將 Rfc、 Bapi 和 Idoc 公開商務整合。 Rfc 是實作特定的商務邏輯的遠端函式模組。 可以叫用此邏輯，從外部的應用程式，例如 BizTalk Server 或.NET 應用程式。 Bapi 是 SAP 商務物件，接著會透過標準的 RFC 介面公開的介面方法。 Idoc 是抽象電子資料交換 (EDI) 的通訊層，SAP 和非 SAP 系統之間進行通訊的機制。 使用[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]，您可以存取的 Rfc、 Bapi 和 Idoc 公開的 SAP 系統。  
  
  [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]也包含[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]，可讓 SAP 系統的 ADO 介面。  
  
  此區段會列出的功能[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]而[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [BizTalk adapter for mySAP Business Suite 的架構概觀](../../adapters-and-accelerators/adapter-sap/architecture-overview-of-the-biztalk-adapter-for-mysap-business-suite.md)  
  
-   [SAP 配接器中的主要功能](../../adapters-and-accelerators/adapter-sap/key-features-in-the-sap-adapter.md)  
  
-   [BizTalk Adapter for mySAP Business Suite 的限制](../../adapters-and-accelerators/adapter-sap/limitations-of-biztalk-adapter-for-mysap-business-suite.md)  
  
-   [關於 .NET Framework Data Provider for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/about-the-net-framework-data-provider-for-mysap-business-suite.md)  
  
## <a name="see-also"></a>另請參閱  
[開始使用 BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/get-started-with-the-biztalk-adapter-for-mysap-business-suite.md)