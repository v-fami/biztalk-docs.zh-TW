---
title: "瞭解 BizTalk Adapter for Siebel eBusiness 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapter features
- features of Siebel adapters
- adapters, features
- adapter, overview
ms.assetid: 3249fb74-9ca1-4b81-971d-5151a2e354fe
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1ad8aecf0faa0a9a0117feaf91e5fa91203fa63f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="understand-biztalk-adapter-for-siebel-ebusiness-applications"></a>瞭解 BizTalk Adapter for Siebel eBusiness 應用程式
[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]啟用服務導向程式設計的存取，以便與外部系統互動。 配接器用戶端提供下列優點：  
  
-   **一致的設計階段經驗**。 配接器會提供瀏覽、 搜尋和擷取的 LOB 成品的中繼資料的一般和使用者易記的設計階段經驗。  
  
-   **各種程式設計選項**。 配接器會提供選擇的程式設計模型包括 Windows Communication Foundation (WCF) 通道模型，WCF 服務模型中，ADO.NET 中，Web 服務，或 BizTalk 支援模型。  
  
-   **跨 Lob 統一經驗**。 標準化使用 WCF 配接器和[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，因此提供一致的體驗的任何 LOB 系統的存取。  
  
 如所述，配接器會建立最上層的[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]。 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供通用的基礎建置各種 BizTalk Server 和 Microsoft Office 等用戶端應用程式可以取用的整合配接器。 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]對齊由公開為 Windows Communication Foundation (WCF) 通道整合配接器的 Microsoft 服務策略配接器的策略。 如需有關[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，請參閱[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]文件。 連同安裝文件[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]通常下\<安裝磁碟機 >: \Program Files\\[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]\Documents。  
  
 若要執行 Siebel 系統上的作業，配接器用戶端必須存取 Siebel 系統所公開的商務服務。 Siebel 應用程式公開資料做為商務元件和商務物件。 Siebel*商務元件*是將一或多個資料表的資料行成單一結構相關聯的邏輯實體。 Siebel*商務物件*實作商務模型繫結在一起的一組相互關聯的商務元件。 與[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]，配接器用戶端可以在 Siebel 商務物件和商業元件介面。  
  
 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]也包含[!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)])。 [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] Siebel 系統的 ADO 介面提供延伸的 ADO.NET 介面。  
  
 本章節將討論的功能[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]和[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [BizTalk Adapter for Siebel eBusiness 應用程式中的概觀](../../adapters-and-accelerators/adapter-siebel/overview-of-biztalk-adapter-for-siebel-ebusiness-applications.md)  
  
-   [Siebel 配接器中的主要功能](../../adapters-and-accelerators/adapter-siebel/key-features-in-the-siebel-adapter.md) 
  
-   [BizTalk adapter for Siebel eBusiness 應用程式的限制](../../adapters-and-accelerators/adapter-siebel/limitations-of-biztalk-adapter-for-siebel-ebusiness-applications.md)  
  
-   [有關 Siebel 的資料提供者](../../adapters-and-accelerators/adapter-siebel/about-the-data-provider-for-siebel.md)