---
title: BizTalk Adapter for Siebel eBusiness 應用程式的架構概觀 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture of Siebel adapter
- Siebel COM Data Control
- adapters, architecture
ms.assetid: b048937f-207b-4c64-8837-7bfeecedfa03
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b77d1da9261ae4a532e8b56be0f4172350f800e7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981439"
---
# <a name="architecture-overview-of-the-biztalk-adapter-for-siebel-ebusiness-applications"></a>BizTalk Adapter for Siebel eBusiness 應用程式的架構概觀
描述使用的端對端解決方案的架構[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]若要在 Siebel 系統中，與內部架構上運作[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
 了解[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]架構可協助您：  
  
- 了解之間的關聯性[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]而[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]。  
  
- 因此，您可以在您的解決方案來改善資料安全性，請了解安全性界限。  
  
- 了解[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]繫結屬性。  
  
- 疑難排解安裝問題。  

## <a name="adapter-architecture-overview"></a>配接器架構概觀
[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]建置的上方[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]之上執行和[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]執行階段。 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供軟體架構和工具的基礎結構[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]採用提供給使用者和配接器用戶端的一組豐富的功能。  
  
 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]是 WCF 自訂繫結。 這個繫結包含單一的自訂傳輸繫結項目，可讓與 Siebel 系統的通訊。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]包裝[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]執行階段，而且會公開給應用程式可以透過[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道架構。  
  
## <a name="siebel-com-data-control"></a>Siebel COM 資料控制項  
 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]與 Siebel 系統透過 Siebel COM 資料控制項程式庫 (sstchca.dll) 和 Microsoft.Adapters.Siebel.SiebelBusinessObjectInterface.dll 程式庫連線。 Siebel COM 資料控制項是 Siebel Web 用戶端元件。 
  
 Siebel COM 資料控制項介面可讓外部用戶端等[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]來連接及通訊與 Siebel 應用程式物件管理員 Siebel 企業伺服器上。 Siebel 物件管理員和 Siebel 企業伺服器，以及其他連接參數中指定[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]連線 URI。 如需連線 URI 的詳細資訊，請參閱[建立 Siebel 系統連接 URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md)。  
  
 下圖顯示使用開發的解決方案的端對端架構[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。  
  
 ![Siebel 端&#45;到&#45;結束架構](../../adapters-and-accelerators/adapter-siebel/media/1ae1955e-b7d7-44a0-80c1-1e835edab356.gif "1ae1955e-b7d7-44a0-80c1-1e835edab356")  
  
## <a name="consuming-the-adapter"></a>使用配接器  
 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]會公開與 Siebel 系統[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務用戶端應用程式。 若要執行作業及存取 Siebel 系統上的資料，用戶端應用程式交換使用的 SOAP 訊息[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]透過[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道。 上圖顯示四種方式，在其中[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]可取用。  
  
- 透過[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型的應用程式。 A[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型應用程式使用執行 Siebel 系統上的作業[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型來交換 SOAP 訊息直接與[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。 如需開發解決方案的詳細資訊[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]利用[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型，請參閱[開發 SQL 應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)。  
  
- 透過[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型的應用程式。 A[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型的應用程式上呼叫方法[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]Siebel 系統上執行作業的用戶端。 A[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]用戶端模型所公開之作業[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]為.NET 方法。 您可以使用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]或 ServiceModel Metadata Utility Tool (svcutil.exe) 來建立[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]用戶端類別所公開的中繼資料從[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。 如需詳細資訊[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型和[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，請參閱[開發 SQL 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)。  
  
- 透過 BizTalk 接收位置或傳送埠設定為使用 Microsoft BizTalk Wcf-custom 配接器。 Wcf-custom 配接器可讓您使用[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]擴充性功能。 使用 Wcf-custom 配接器中，您可以選取和設定 Siebel 繫結和行為的接收位置或傳送埠。 BizTalk 交易支援 BizTalk 分層通道繫結項目，可以藉由在 Siebel 繫結上設定繫結屬性載入。 如需有關如何使用[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案，請參閱[開發 BizTalk 應用程式](../../core/develop-your-biztalk-applications.md)。
  
- 透過 IIS 裝載的 Web 服務。 在此案例中，使用標準 WCF Http 繫結在 IIS 中裝載 WCF 服務 proxy 產生使用配接器。 這會在服務合約公開為 Web 服務的外部使用者。 IIS 自動裝載在執行階段，其中，反過來與 Siebel 系統的配接器。  
  
  [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]和 Siebel COM 資料控制項程式庫永遠是裝載同處理序的應用程式或取用配接器的服務。  
  
## <a name="siebel-adapter-and-wcf"></a>Siebel 配接器和 WCF  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] 提供程式設計模型，根據用戶端與服務之間的通道上的 SOAP 訊息交換。 通訊的用戶端和服務所公開的端點之間傳送這些訊息。 端點所組成：  
  
- *端點位址*，以指定訊息接收到的位置。  
  
- A*繫結*，指定用來交換訊息的通訊協定。  
  
- A*合約*，指定端點所公開的作業和資料類型。  
  
  繫結是由堆疊在彼此的上層定義與端點交換訊息的方式的一或多個繫結項目所組成。 最少的傳輸和編碼用來與端點交換訊息，必須指定繫結。 端點之間交換訊息是透過通道堆疊所組成的一或多個通道。 每個通道是其中一個繫結中設定端點的繫結元素的具象實作。 [WCF 文件](http://go.microsoft.com/fwlink/?LinkID=196850)包含更多詳細資料，關於[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]，和[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]程式設計模型。  
  
  [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]公開[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]自訂繫結，Siebel 繫結 (**Microsoft.Adapters.Siebel.SiebelBinding**)。 根據預設，此繫結包含單一的自訂傳輸繫結項目，Siebel 配接器繫結項目 (**Microsoft.Adapters.Siebel.SiebelAdapter**)，可使用 Siebel 系統上的作業。 使用時[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]具有[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您可以設定**EnableBizTalkCompatibilityMode**載入自訂繫結項目屬性繫結 — BizTalk 分層通道繫結項目 — 之上 Siebel 配接器繫結項目。 BizTalk 分層通道繫結項目在內部實作[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]，不會公開外部 Siebel 繫結。  
  
  **Microsoft.Adapters.Siebel.SiebelBinding** （Siebel 繫結） 和**Microsoft.Adapters.Siebel.SiebelAdapter** （Siebel 配接器繫結項目） 是公用的類別，也會公開至組態系統。 Siebel 配接器繫結項目公開的因為您可以建置自己的自訂[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]繫結的擴充功能的支援[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。 例如，您可以實作自訂繫結，以支援企業單一登入 (SSO)，在[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道或服務的程式設計模型。 執行此動作的原因包括為：  
  
- 彙總成單一的多功能作業的資料庫作業。  
  
- 執行結構描述轉換的自訂應用程式所實作的作業與 Siebel 系統上的作業。  

## <a name="siebel-adapter-and-wcf-lob-adapter-sdk"></a>Siebel 配接器和 WCF LOB 配接器 SDK

[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]會實作一組核心元件的：  
  
- 利用所提供的功能[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]。  
  
- 連接至 Siebel 系統透過 Siebel COM 資料控制項程式庫 (sstchca.dll) 提供。  
  
  [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是透過此軟體層[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]wcf; 介面Siebel COM 資料控制項是透過此層級[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]與 Siebel 系統的介面。 下圖顯示的內部元件之間的關聯性[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]之間以及這些元件與 Siebel COM 資料控制項。  
  
  ![Siebel 配接器內部架構](../../adapters-and-accelerators/adapter-siebel/media/e4accea7-86b2-4f2a-937a-edff7e1100ec.gif "e4accea7-86b2-4f2a-937a-edff7e1100ec")
   
## <a name="see-also"></a>另請參閱  
 [保護您的 Siebel 應用程式](../../adapters-and-accelerators/adapter-siebel/secure-your-siebel-applications.md)  
 [了解 BizTalk Adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/understand-biztalk-adapter-for-siebel-ebusiness-applications.md)