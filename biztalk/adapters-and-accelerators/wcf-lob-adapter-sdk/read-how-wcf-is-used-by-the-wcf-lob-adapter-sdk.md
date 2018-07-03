---
title: 讀取 WCF 如何使用 WCF LOB 配接器 SDK |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 183dd134-7273-4767-bad0-c42ae125985e
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8991590d97d70fc0e2090f11f05f8882b0ca3396
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004711"
---
# <a name="read-how-wcf-is-used-by-the-wcf-lob-adapter-sdk"></a>讀取 WCF 如何使用 WCF LOB 配接器 SDK
[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]擴充[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道架構，並相依於[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]runtime 能夠提供基本的傳訊服務，才能公開配接器功能，並交換資訊。 
  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供的架構來撰寫配接器，呈現在[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]，以及它們與一般配接器的項目，例如中繼資料和連接共用互補的。 它也包含支援工具，來增強的體驗，例如[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].NET 應用程式及[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]for[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式和[!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)]。  
  
 它負責[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]公開 （expose） 服務給取用端應用程式，來管理不同的端點之間的訊息流程，並提供自訂、 SDK 和工具的各種設定及監視訊息流程。 比方說，開發人員可以自訂行為[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]藉由擴充其通道使用的自訂訊息處理常式。  
  
 之間的關聯性[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]下列的高階架構圖所示。  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/asdk-wcf.gif "ASDK_WCF")  
  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]建置的上方[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]做為擴充[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型。 它提供了特定領域和簡化的物件模型和工具組，可建置配接器，為自訂[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道。 使用所建置的配接器[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]當成自訂[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]繫結。  
  
 下圖顯示使用指定的配接器繫結的輸出訊息交換。  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/58609452-d09e-4dbd-b470-c92a29977858.gif "58609452-d09e-4dbd-b470-c92a29977858")  
  
 下圖顯示使用指定的配接器繫結的輸入的訊息交換。  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/b62d5040-7e40-4edd-ac7b-69768131c51b.gif "b62d5040-7e40-4edd-ac7b-69768131c51b")  
  
 如需詳細資訊[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型，請參閱[通道模型概觀](https://msdn.microsoft.com/library/ms729840.aspx)。  
  
## <a name="wcf-services-and-the-wcf-lob-adapter-sdk"></a>WCF 服務和 WCF LOB 配接器 SDK  
 開發一般時[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務，第一個步驟是建立共用與外界說明如何與服務通訊的服務合約。 此合約基本上會指定集合與存取服務所提供的作業所需的訊息的結構。  
  
 此合約會公開為服務時，一旦[Service Model Metadata Utility Tool (Svcutil.exe)](https://msdn.microsoft.com/library/aa347733.aspx)可用來建立[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]取用它的用戶端。 合約會提供一組靜態資訊的作業和不可以變更的訊息。 
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/a410af83-ee3b-46d0-9afd-d32970f5ba0a.gif "a410af83-ee3b-46d0-9afd-d32970f5ba0a")  
  
 相反地，配接器使用來建置[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供一組動態的集合的作業和特定業務系統中所提供的資料相關的中繼資料。 特定業務系統通常會有太多作業需要在一個合約中描述，並可能會有新作業加入至回應新商務需求。  
  
 例如，特定業務系統可能會提供帳戶管理作業。 找出需要簡化的新客戶帳戶建立程序之後, 該公司會更新特定業務系統，以包含新的作業。 使用所建置的配接器[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]公開這項作業，它提供給用戶端的中繼資料中。  
  
 在設計階段， [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]-根據配接器會產生的合約，以動態方式以符合特定業務系統的需求。  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/2f4d896a-14d9-43f4-8cdc-f816c5eab46d.gif "2f4d896a-14d9-43f4-8cdc-f816c5eab46d")  
  
 提供 ASDK[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]和[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]工具配接器取用者在設計階段產生動態的合約。  
  
 在執行階段，當訊息流動到配接器使用寫入時[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，配接器通常必須採取一連串的動作上接收訊息。 這些動作包括：  
  
- 查閱相關的訊息中繼資料  
  
- 開啟訊息  
  
- 解譯的訊息  
  
- 特定業務系統中呼叫適當的函式  
  
  如果是[!INCLUDE[nextref_btsWinCommFoundation_md](../../includes/nextref-btswincommfoundation-md.md)]服務，訊息只是通過而不需透過中繼資料解析。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for Oracle Database 與 WCF LOB 配接器 SDK](../adapter-oracle-database/architecture-overview-of-the-biztalk-adapter-for-oracle-database.md)