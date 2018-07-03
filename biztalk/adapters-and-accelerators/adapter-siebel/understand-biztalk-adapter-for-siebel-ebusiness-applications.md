---
title: 了解 BizTalk Adapter for Siebel eBusiness Application |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapter features
- features of Siebel adapters
- adapters, features
- adapter, overview
ms.assetid: 3249fb74-9ca1-4b81-971d-5151a2e354fe
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 788db9ba048141256cfaa3cc5017fa48bd6ec7de
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999231"
---
# <a name="understand-biztalk-adapter-for-siebel-ebusiness-applications"></a>了解 BizTalk Adapter for Siebel eBusiness 應用程式
[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]啟用服務導向程式設計的存取，以便與外部系統進行互動。 配接器用戶端提供下列優點：  
  
- **一致的設計階段經驗**。 配接器會提供瀏覽、 搜尋和擷取中繼資料的 LOB 成品的一般和方便使用的設計階段體驗。  
  
- **各種程式設計選項**。 配接器會提供各種程式設計模型，包括 Windows Communication Foundation (WCF) 通道模型中，WCF 服務模型中，ADO.NET 中，Web 服務，或 BizTalk 支援的模型。  
  
- **統一的體驗，跨 Lob**。 使用 WCF 配接器將標準化和[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，因此提供一致的體驗的任何 LOB 系統的存取。  
  
  如前所述，配接器是以 WCF LOB 配接器 SDK 為基礎。 WCF LOB 配接器 SDK 建置可取用各種不同的用戶端應用程式，例如 BizTalk Server 和 Microsoft Office 的整合配接器提供的通用基礎。 WCF LOB 配接器 SDK 公開為 Windows Communication Foundation (WCF) 通道的整合配接器會將對齊配接器策略，Microsoft 服務策略。 如需有關 WCF LOB 配接器 SDK 的詳細資訊，請參閱 < [WCF LOB 配接器 SDK 文件](../../adapters-and-accelerators/wcf-lob-adapter-sdk/microsoft-wcf-line-of-business-adapter-sdk-documentation.md)。
  
  若要執行 Siebel 系統上的作業，配接器用戶端必須存取 Siebel 系統所公開的商務服務。 Siebel 應用程式公開資料做為商務元件和商務物件。 Siebel*商務元件*是將一個或多個資料表的資料行成單一結構相關聯的邏輯實體。 Siebel*商務物件*緊密結合在一起的一組相互關聯的商務元件實作的商務模型。 使用[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]，配接器用戶端可能會出現 Siebel 商務物件和商務元件。  
  
  [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]也包含[!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)])。 [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]藉由擴充 ADO.NET 介面提供 Siebel 系統的 ADO 介面。  
  
  本章節將討論的功能[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]而[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [BizTalk Adapter for Siebel eBusiness Applications 概觀](../../adapters-and-accelerators/adapter-siebel/overview-of-biztalk-adapter-for-siebel-ebusiness-applications.md)  
  
-   [Siebel 配接器中的主要功能](../../adapters-and-accelerators/adapter-siebel/key-features-in-the-siebel-adapter.md) 
  
-   [BizTalk Adapter for Siebel eBusiness Applications 的限制](../../adapters-and-accelerators/adapter-siebel/limitations-of-biztalk-adapter-for-siebel-ebusiness-applications.md)  
  
-   [關於 Data Provider for Siebel](../../adapters-and-accelerators/adapter-siebel/about-the-data-provider-for-siebel.md)