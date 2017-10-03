---
title: "何謂 Windows Communication Foundation 列商務配接器 SDK 的 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc690e8f-fd37-44b5-a277-89952e631ae6
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 084201d9680cb8d17c37c2218ebe7622c4cc4495
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-windows-communication-foundation-line-of-business-adapter-sdk"></a>什麼是 Windows Communication Foundation 列商務配接器 SDK 的
功能和元件中的概觀[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。 本主題也說明重要概念，包括中繼資料、 連線管理，以及若要知道，例如繫結和通道的詞彙。

## <a name="features-overview"></a>功能概觀
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]設計用來建置可公開的資料和作業的特定業務系統的配接器開發人員的需求。 所提供的功能部分[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]包括：  
  
-   一致的機制來公開傳輸及資料通訊協定
  
-   WCF 繫結之配接器的公開
  
-   透過 WCF 通道架構的擴充性
  
-   [!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)]
  
-   常見的中繼資料搜尋和瀏覽使用者介面使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]使用設計階段整合[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]
  
 因為[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]延伸 wcf，它也提供下列功能：  
  
-   現有的.NET Framework 通訊技術版本對應轉換
  
-   跨廠商的互通性，包括可靠性、 安全性與交易支援
  
-   明確服務方向
  
## <a name="components-overview"></a>元件概觀
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供一致且可重複的體驗配接器開發人員和配接器取用者透過一組執行階段和設計階段元件、.NET 物件模型，以及支援元件包括：  
  
|元件|Description|  
|---------------|-----------------|  
|[!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)]|提供逐步指南中的建立[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]專案內[!INCLUDE[btsVStudioNet](../../includes/btsvstudionet-md.md)]。|  
|[!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)]|提供建立 Web 專案以裝載在網際網路資訊服務 (IIS) 的配接器的逐步指引。|  
|[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]執行階段系統|支援[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]延伸 WCF 通道架構並提供其他執行階段服務。|  
|[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]物件模型|集合類別、 類型和介面，可以支援一般配接器工作，例如中繼資料正規化、 快取、 連線的管理和集區，和傳訊檢查。|  
|[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]|提供自訂的.NET 應用程式能夠使用配接器開發使用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。|  
|[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]|提供[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]能夠使用配接器開發使用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]。|  

## <a name="sdk-fundamentals"></a>SDK 的基本概念  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] Runtime 時，應用程式開發介面和建立公開資料和作業的特定業務系統的配接器的設計階段工具的集合所組成。 配接器管理配接器取用者和特定業務系統之間的訊息，且可包含的中繼資料、 資料或其他資訊。  
  
### <a name="metadata"></a>中繼資料  
 其中一個配接器以撰寫的區別特性[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]且使用 Windows Communication Foundation (WCF) 服務模型物件模型來實作其中一個中繼資料。 中繼資料描述資料、 作業、 屬性和其他動態特性的系統，並可由配接器取用者來探索、 使用，以及目標系統的互動。  
  
 典型的 WCF 服務程式生命週期包括 WCF 服務開發人員建立及裝載服務。 WCF 服務端點包含位址、 繫結及合約，也稱為 「 A、 B 和 C 的 「 WCF。  位址是服務的位置，而繫結會指定通訊協定和用來與服務通訊的傳輸。  WCF 服務開發人員定義合約使用 WCF System.ServiceModel 物件模型提供 WCF 服務的形式實作，它使用 ServiceHost 裝載。 SvcUtil.exe 和/或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]可用來建置用戶端對應到已發佈的服務中繼資料。 一旦服務啟動並執行，可以針對服務端點位址，以慣用的語言和用戶端實作 WCF 服務的詳細資料與對應的 app.config 檔案中產生 WCF proxy 執行設計階段工具。  
  
 WCF LOB 配接器開發人員，相反地，實作中提供的中繼資料物件模型[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]定義的作業和配接器所支援的類型。 輸出配接器是 WCF 自訂繫結，因為它是裝載同處理序中取用者應用程式。  配接器的電腦上，安裝之後[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]可用來瀏覽和搜尋中繼資料，並因此偏好的語言，以及包含配接器組態詳細資料的 app.config 檔案中產生 WCF proxy。 合約會建立，並藉由查詢可用的特定業務系統中的即時中繼資料產生視 WCF LOB 配接器。  
  
 例如，特定業務系統可能 adjudicate 不同醫療保健宣告類型，而且包含成長的唯一作業、 資料型別、 商務規則和系統的使用者所建立的報表集合。 若這項資訊會公開為靜態的合約，就必須修改，因為新的商務物件新增至系統，或只是提供新的商務物件的存取權。 不過，如果宣告 adjudication 系統內的動態商務物件的相關資訊可瀏覽 （和搜尋），新的物件，例如新驗證規則機構宣告或新的報表會公開，而且可以取用。  
  
### <a name="connection-management"></a>連接管理  
 可以使用的特定業務系統交換資訊之前，配接器必須建立連接。 連接 （消費者） 的介面卡會連結到特定業務系統 （提供者），並控制連接生命週期，包括開啟、 關閉、 中止，與驗證連線的有效性。 根據業務的系統需求，連線可能需要一或多個認證及連線參數，例如伺服器名稱、 預設目錄或連接埠號碼。  
  
 連線的存留期是由連接集區管理。 當配接器，要求新的連接時[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供現有的連接，如果有一個可用; 否則新的連接建立和放入集區，然後提供給配接器。 當配接器與連接完成時，它會放回集區。 連接已閒置超過特定閾值，系統會關閉和移除從集區。  
  
### <a name="windows-communication-foundation"></a>Windows Communication Foundation  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]的延伸[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]、 統一的程式設計模型，用於建置服務導向應用程式的 managed 程式碼。 配接器使用撰寫[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]當成[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]可供任何 WCF 支援的應用程式的繫結。  
  
## <a name="important-terms"></a>重要詞彙  

| | |
|---|---|
| 繫結 | 定義配接器通訊的方式。 建立繫結[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]並定義傳輸、 編碼方式，與其他詳細資料。 繫結中可能有一或多個繫結項目。 |
|通道 | 繫結項目的實作。 通道繫結堆疊在彼此的上方來建立通道堆疊的集合。 |
| message  |  自主的單位的可能包括本文和標頭的幾個部分所組成的資料。|
| 中繼資料 | 說明的作業和可用的資料包括特定業務系統特性。|
| operation (作業) | 函式和特定業務系統所公開的方法。 它們會在資料上運作，且執行有用的活動，例如 adjudicating 宣告、 建立訂單時，或查詢的銷售資料。  |
 
   
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 和 WCF LOB 配接器 SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/using-biztalk-server-and-the-wcf-lob-adapter-sdk.md)   
   [WCF LOB 配接器 SDK 教學課程](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorials-to-learn-the-wcf-lob-adapter-sdk.md)