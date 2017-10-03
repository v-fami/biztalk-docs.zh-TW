---
title: "讀取 WCF 如何使用 WCF LOB 配接器 SDK |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 183dd134-7273-4767-bad0-c42ae125985e
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb84124213df8cf1bd401ab80db25586f5ca4534
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="read-how-wcf-is-used-by-the-wcf-lob-adapter-sdk"></a>讀取 WCF 如何使用 WCF LOB 配接器 SDK
[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]擴充[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道架構，並相依於[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]runtime 能夠提供基本的訊息服務才能公開配接器功能，並且交換資訊。 
  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供架構，以撰寫配接器，它們在面對[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]，並補充它們，進而與一般配接器的項目，例如中繼資料和連接集區。 它也包含支援工具，例如增強經驗[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].NET 應用程式和[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]如[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式和[!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)]。  
  
 它負責[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]公開服務的取用應用程式，管理不同的端點之間的訊息流程，並提供 SDK 和工具，若要自訂，以設定及監視訊息流程。 例如，開發人員可以自訂行為[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]藉由擴充其通道的自訂訊息處理常式。  
  
 之間的關聯性[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]下列高層級架構圖所示。  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/asdk-wcf.gif "ASDK_WCF")  
  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]建置最上層的[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]做為擴充[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型。 它提供了特定的網域和簡化物件模型和工具集來建置為自訂配接器[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道。 使用所建置的配接器[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]當成自訂[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]繫結。  
  
 下圖顯示使用指定的介面卡繫結的輸出訊息交換。  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/58609452-d09e-4dbd-b470-c92a29977858.gif "58609452-d09e-4dbd-b470-c92a29977858")  
  
 下圖顯示使用指定的介面卡繫結的輸入的訊息交換。  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/b62d5040-7e40-4edd-ac7b-69768131c51b.gif "b62d5040-7e40-4edd-ac7b-69768131c51b")  
  
 如需有關[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型，請參閱[通道模型概觀](https://msdn.microsoft.com/library/ms729840.aspx)。  
  
## <a name="wcf-services-and-the-wcf-lob-adapter-sdk"></a>WCF 服務和 WCF LOB 配接器 SDK  
 當開發一般[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務時，第一個步驟是建立共用與外界描述如何與服務通訊的服務合約。 此合約基本上可指定集合與存取服務所提供的作業所需的訊息結構。  
  
 這個合約會公開為服務時，一旦[Service Model Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx)可以用來建立[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]用戶端，才能加以使用。 合約會提供一組靜態資訊的作業和不可以變更的訊息。 
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/a410af83-ee3b-46d0-9afd-d32970f5ba0a.gif "a410af83-ee3b-46d0-9afd-d32970f5ba0a")  
  
 相反地，配接器使用來建置[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供一組動態集合的作業和可用的特定業務系統內的資料相關的中繼資料。 特定業務系統通常會有太多的作業一個合約中所述，可能會有新作業加入至回應新的商務需求。  
  
 例如，特定業務系統可能會提供帳戶管理作業。 在識別需要簡化的新客戶帳戶的建立作業之後, 公司更新特定業務系統上，以包含新的作業。 使用所建置的配接器[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]公開它提供給用戶端的中繼資料中的這項作業。  
  
 在設計階段[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]-根據配接器會產生以動態方式以符合業務的系統需求的合約。  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/2f4d896a-14d9-43f4-8cdc-f816c5eab46d.gif "2f4d896a-14d9-43f4-8cdc-f816c5eab46d")  
  
 提供 ASDK[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]和[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]配接器取用者在設計階段產生動態合約的工具。  
  
 在執行階段，當訊息傳送到配接器使用撰寫[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，配接器通常必須採取一連串的動作上接收訊息。 這些動作包括：  
  
-   查閱與訊息有關的中繼資料  
  
-   開啟郵件  
  
-   解譯訊息  
  
-   在特定業務系統中呼叫適當的函式  
  
 如果是[!INCLUDE[nextref_btsWinCommFoundation_md](../../includes/nextref-btswincommfoundation-md.md)]服務，訊息直接傳遞不含所透過的中繼資料解析。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for Oracle 資料庫與 WCF LOB 配接器 SDK](../adapter-oracle-database/architecture-overview-of-the-biztalk-adapter-for-oracle-database.md)