---
title: 什麼是商務配接器 SDK 的 Windows Communication Foundation 一行 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc690e8f-fd37-44b5-a277-89952e631ae6
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ada608dbac8071af182c26af02c8f47b43e6cca
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011983"
---
# <a name="what-is-the-windows-communication-foundation-line-of-business-adapter-sdk"></a>什麼是商務配接器 SDK 的 Windows Communication Foundation 一行
功能和元件概觀[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 本主題也說明重要概念，包括中繼資料、 連線管理和了解，例如繫結和通道的詞彙。

## <a name="features-overview"></a>功能概觀
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]用意是要滿足開發人員建置公開 （expose） 的資料和作業的特定業務系統的配接器的需求。 所提供的功能的一些[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]包括：  
  
- 一致的機制來公開傳輸及資料通訊協定
  
- 配接器為 WCF 繫結的曝光率
  
- 透過 WCF 通道架構的擴充性
  
- [!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)]
  
- 常見的中繼資料搜尋和瀏覽使用者介面使用 [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]
  
- [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 使用設計階段整合 [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]
  
  因為[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是延伸 wcf，因此它也提供下列功能：  
  
- 現有的.NET Framework 通訊技術的版本對應轉換
  
- 跨廠商互動性，包括可靠性、 安全性和交易的支援
  
- 明確的服務導向
  
## <a name="components-overview"></a>元件概觀
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供一致且可重複使用經驗，配接器開發人員和配接器取用者透過一組執行階段和設計階段元件、.NET 物件模型，以及支援元件包括：  
  

|                                        元件                                        |                                                                                                       描述                                                                                                        |
|-----------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|        [!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)]        |         提供逐步指示，建立[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]專案內[!INCLUDE[btsVStudioNet](../../includes/btsvstudionet-md.md)]。         |
|            [!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)]            |                                                   提供建立 Web 專案來裝載在網際網路資訊服務 (IIS) 中的配接器的逐步指引。                                                    |
| [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] 執行階段系統 |                          支援[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]藉由擴充 WCF 通道架構，並提供其他執行階段服務。                           |
|  [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] 物件模型   |                  類別、 類型和支援一般配接器工作，例如中繼資料正規化、 快取、 連線的管理和共用，以及訊息檢查介面的集合。                  |
|     [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]     |                               提供自訂的.NET 應用程式能夠使用配接器開發使用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。                                |
|    [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]    | 可讓[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]能夠使用配接器開發使用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 |

## <a name="sdk-fundamentals"></a>SDK 的基本概念  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]包含執行階段時，Api，以及建立公開 （expose） 資料和作業，從特定業務系統的配接器的設計階段工具的集合。 配接器管理配接器取用者與特定業務系統之間的訊息，而且可以包含的中繼資料、 資料或其他資訊。  

### <a name="metadata"></a>中繼資料  
 其中一個配接器與寫入的區別特性[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，而且其中一個使用 Windows Communication Foundation (WCF) 服務模型物件模型來實作中繼資料。 中繼資料描述資料、 作業、 屬性和系統的其他動態特性，並可由配接器取用者來探索、 取用，並與其互動的目標系統。  

 典型的 WCF 服務程式設計生命週期包括 WCF 服務開發人員建立和裝載服務。 WCF 服務端點所組成的位址、 繫結和合約，也稱為 「 A、 B 和 C 的 「 WCF。  位址是服務的位置，而繫結指定通訊協定和用來與服務通訊的傳輸。  WCF 服務開發人員定義合約，使用 WCF System.ServiceModel 物件模型，提供它的實作 WCF 服務的形式和裝載使用 ServiceHost。 SvcUtil.exe 和/或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]可用來建置用戶端並對應至已發佈的服務中繼資料。 一旦服務啟動並執行，可以執行設計階段工具，對服務端點位址，以產生 WCF proxy，慣用的語言和對應的 WCF 服務的詳細資料的用戶端實作的 app.config 檔案中。  

 WCF LOB 配接器開發人員，相反地，實作中提供的中繼資料物件模型[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]來定義的作業和配接器支援的類型。 輸出配接器是 WCF 自訂繫結，因為它是裝載同處理序在取用者應用程式中。  配接器的電腦上，安裝之後[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]可用瀏覽和搜尋中繼資料，並因此產生 WCF proxy，以偏好的語言，以及包含配接器的組態詳細資料的 app.config 檔案。 合約會建立，並藉由查詢可用的特定業務系統中的即時中繼資料產生 WCF LOB 配接器依需求。  

 例如，特定業務系統可能 adjudicate 不同類型的醫療保健的宣告，並可能包含集結了各種唯一的作業、 資料型別、 商務規則和系統的使用者所建立的報表。 如果這項資訊會公開為靜態的合約，它就必須修改為新的商務物件新增至系統，或只是提供新的商務物件的存取權。 不過，如果宣告 adjudication 系統內動態商務物件的相關資訊可瀏覽 （和搜尋），新的物件，例如新的驗證規則，機構的宣告或新的報表會公開，而且可以取用。  

### <a name="connection-management"></a>連接管理  
 可以與特定業務系統交換資訊之前，配接器必須建立連線。 連接的特定業務系統 （提供者） 的連結配接器 （取用者），並控制連接生命週期，包括開啟、 關閉、 中止，及驗證連線有效。 根據特定業務系統的需求，連線可能需要一或多個認證及連線參數，例如伺服器名稱、 預設目錄或連接埠號碼。  

 連接的存留期是由連接集區管理。 配接器，要求新的連接時[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供現有的連接，如果有一個為可用，否則為，新的連接會建立並放入集區和則提供給配接器。 配接器完成時進行連線，它會放回集區。 已閒置超過特定臨界值的連接會關閉，並從集區中移除。  

### <a name="windows-communication-foundation"></a>Windows Communication Foundation  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]的延伸[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]，統一的程式設計模型，用於建置服務導向應用程式與 managed 程式碼。 使用所撰寫的介面卡[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]當成[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]可供任何 WCF 功能的應用程式的繫結。  

## <a name="important-terms"></a>重要詞彙  

|           |                                                                                                                                                                                                                                                         |
|-----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  繫結  | 定義配接器通訊的方式。 繫結藉由[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]並定義傳輸、 編碼及其他詳細資料。 繫結中，可能會有一或多個繫結項目。 |
|  通道  |                                                          繫結項目的實作。 通道繫結堆疊彼此的上方來建立通道堆疊的集合。                                                           |
|  message  |                                                                              獨立的數個部分包括本文和標頭可能包含的資料單位。                                                                              |
| 中繼資料  |                                                                   描述的作業和可用的資料包括特定業務系統的特性。                                                                    |
| operation (作業) |                             函式和特定業務系統所公開的方法。 它們在資料上運作，並執行有用的活動，例如 adjudicating 宣告、 建立訂單，或查詢的銷售資料。                              |
   
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 和 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/using-biztalk-server-and-the-wcf-lob-adapter-sdk.md)   
   [WCF LOB 配接器 SDK 教學課程](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorials-to-learn-the-wcf-lob-adapter-sdk.md)