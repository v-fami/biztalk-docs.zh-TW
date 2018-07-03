---
title: BizTalk Adapter for Oracle 資料庫的架構概觀 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapter, and WCF
- architecture of the Oracle Database adapter
- ODAC
- Oracle Data Access Components
- endpoint
- adapter, architecture
- endpoint address
- ODP.NET
- Oracle Data Provider for .NET
- architecture
ms.assetid: cc59beb5-327a-4b00-a45c-82cc9d505167
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 292bb6504c1c7d8604f18f153e35f6d8e5980017
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014559"
---
# <a name="architecture-overview-of-the-biztalk-adapter-for-oracle-database"></a>BizTalk Adapter for Oracle 資料庫的架構概觀
描述的架構[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]。 

了解[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]架構可協助您：  
  
- 了解之間的關聯性[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]而[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]。  
  
- 因此，您可以更妥善地保護您的方案中的資料，請了解安全性界限。  
  
- 了解[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]繫結屬性。  
  
- 疑難排解安裝問題。  
  
本主題描述使用的端對端解決方案的架構[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]來操作 Oracle 資料庫，也描述的內部架構和[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
 
## <a name="adapter-architecture-overview"></a>配接器架構概觀
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。 這個繫結包含單一的自訂傳輸繫結項目，以便與 Oracle 資料庫進行通訊。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]包裝[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]執行階段，而且會公開給應用程式可以透過[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道架構。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與 Oracle 資料提供者所提供的 Oracle 資料庫通訊.NET (ODP.NET) 和 Oracle 用戶端，也就是組件的 Oracle 資料存取元件 (ODAC) 的 Windows。  
  
 下圖顯示使用開發的解決方案的端對端架構[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
 ![Oracle 資料庫配接器架構圖](../../adapters-and-accelerators/adapter-oracle-database/media/bts-oracledb-architecturec.gif "bts_OracleDB_Architecturec")  
  
## <a name="consuming-the-adapter"></a>使用配接器  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]公開 （expose) 將 Oracle 資料庫視為[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務用戶端應用程式。 若要執行作業及存取 Oracle 資料庫上的資料，用戶端應用程式會交換使用的 SOAP 訊息[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]透過[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道。 上圖顯示四種方式，在其中[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]可取用。 其中包括：  
  
- 透過[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型的應用程式。 A[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型應用程式執行的 Oracle 資料庫上的作業，使用[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型來交換 SOAP 訊息直接與[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 如需開發解決方案的詳細資訊[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]利用[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型，請參閱[開發的 Oracle 資料庫應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)。  
  
- 透過[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型的應用程式。 A[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型的應用程式上呼叫方法[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]用戶端執行的 Oracle 資料庫上的作業。 A[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]用戶端模型所公開之作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]為.NET 方法。 您可以使用[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]或 WCF ServiceModel Metadata Utility Tool (svcutil.exe) 來建立[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]用戶端類別所公開的中繼資料從[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 如需詳細資訊[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型和[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[開發 Oracle 資料庫應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)。  
  
- 透過 BizTalk 接收位置或傳送埠設定為使用 Microsoft BizTalk Wcf-custom 配接器。 Wcf-custom 配接器可讓您使用[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]擴充性功能。 使用 Wcf-custom 配接器中，您可以選取和設定 Oracle DB 繫結和行為的接收位置或傳送埠。 如需有關如何使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案，請參閱[開發 BizTalk 應用程式](../../core/develop-your-biztalk-applications.md)。  
  
- 透過 IIS 裝載的 Web 服務。 在此案例中，使用標準 WCF Http 繫結在 IIS 中裝載 WCF 服務 proxy 產生使用配接器。 這會在服務合約公開為 Web 服務的外部使用者。 IIS 會自動裝載配接器在執行階段，它反而會與 Oracle 資料庫通訊。  
  
  [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]和 ODAC 一律裝載同處理序的應用程式或取用配接器的服務。  
  
## <a name="oracle-database-adapter-and-wcf"></a>Oracle 資料庫配接器和 WCF  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] 提供程式設計模型，根據用戶端與服務之間的通道上的 SOAP 訊息交換。 通訊的用戶端和服務所公開的端點之間傳送這些訊息。 端點所組成：  
  
- *端點位址*，以指定訊息接收到的位置  
  
- A*繫結*，指定用來交換訊息的通訊協定  
  
- A*合約*，指定端點所公開的作業和資料類型。  
  
  繫結是由堆疊在彼此的上層定義與端點交換訊息的方式的一或多個繫結項目所組成。 最少的傳輸和編碼用來與端點交換訊息，必須指定繫結。 端點之間交換訊息是透過通道堆疊所組成的一或多個通道。 每個通道是其中一個繫結項目，設定端點的繫結中的具象實作。 [WCF 文件](http://go.microsoft.com/fwlink/?LinkID=196850)包含更多詳細資料，關於[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]，和[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]程式設計模型。  
  
  [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]公開[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]自訂繫結，Oracle DB 繫結 (**Microsoft.Adapters.OracleDB.OracleDBBinding**)。 根據預設，此繫結包含單一的自訂傳輸繫結項目，Oracle DB 配接器繫結項目 (**Microsoft.Adapters.OracleDB.OracleDBAdapter**)，可使用的 Oracle 資料庫的作業。  
  
  **Microsoft.Adapters.OracleDB.OracleDBBinding** （Oracle DB 繫結） 和**Microsoft.Adapters.OracleDB.OracleDBAdapter** （Oracle DB 配接器繫結項目） 是公用的類別，也會公開至組態系統。 因為 Oracle DB 配接器繫結項目公開的您可以建置自己的自訂[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]繫結的擴充功能的支援[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 例如，您可以實作自訂繫結，以支援企業單一登入 (SSO)，在[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道或服務模型方案。 彙總的資料庫作業為單一多功能的作業，或執行自訂的應用程式所實作的作業和作業上的 Oracle 資料庫之間的結構描述轉換是執行此動作的原因。  
  
  [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]建置的上方[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]之上執行和[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]執行階段。 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供軟體架構和工具的基礎結構[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會使用提供給使用者和配接器用戶端的一組豐富的功能。  

## <a name="oracle-database-adapter-and-wcf-lob-adapter-sdk"></a>Oracle 資料庫配接器和 WCF LOB 配接器 SDK
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]會實作一組核心元件，利用所提供的功能[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]和.NET (ODP.NET) 時，提供透過 Oracle 資料提供者與 Oracle 資料庫的連線能力。  
  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]做為透過此軟體層[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]介面[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]。 ODP.NET 做為透過此層[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與 Oracle 資料庫的介面。 
 
下圖顯示的內部元件之間的關聯性[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]， [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，和 T。  
  
 ![Oracle 資料庫配接器內部架構](../../adapters-and-accelerators/adapter-oracle-database/media/fa730561-9db7-40d1-bfcd-bc4eb119eea8.gif "fa730561-9db7-40d1-bfcd-bc4eb119eea8")  
 
   
## <a name="odpnet"></a>ODP.NET  
 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]與透過 ODP.NET 和 Oracle 用戶端之 Oracle 資料庫連接。 這兩個元件都一部分 Oracle 資料存取元件 (ODAC)。  
  
 ODP.NET 實作 Oracle 資料庫與 ADO.NET 介面一致的資料提供者。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]運作的 Oracle 資料庫上使用 ODP.NET 所公開的類別。  
  
 Oracle 用戶端提供連線到 Oracle 資料庫。 您連接到 Oracle 資料庫所提供的連線 URI 以[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 您可以指定連線 URI，有兩種：  
  
- **使用 tnsnames.ora**。 這種方法，連線配接器用戶端所提供的 URI 會包含只 tnsnames.ora 檔案中指定的網路服務名稱。 配接器會從 net 的服務名稱項目，在檔案中擷取連接參數，例如伺服器名稱、 服務名稱、 連接埠號碼 」 等。 若要使用這種方法，執行 Oracle 用戶端的電腦，必須設定為包含 tnsnames.ora 檔案中的 net 的服務名稱的 Oracle 資料庫中。  
  
- **不使用 tnsnames.ora**。 在此方法中，配接器用戶端會指定連線參數，直接在 連線 URI 中。 這不需要網路的服務名稱會出現在用戶端電腦上的 tnsnames.ora 檔案。 這種方法甚至不需要存在於用戶端電腦上的 tnsnames.ora 檔案。  
  
  如需連線 URI 的詳細資訊，請參閱[建立 Oracle 資料庫的連接](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md)。
  
## <a name="next"></a>下一個
[保護您的 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/secure-your-oracle-database-applications.md)