---
title: BizTalk Adapter for SQL Server 的架構概觀 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d31eb73f-b73e-4cd3-8b62-207b806175ee
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 841f07bfb8c027ab2bfc1b98e23b225af42b449c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225246"
---
# <a name="architecture-overview-of-biztalk-adapter-for-sql-server"></a>BizTalk Adapter for SQL Server 的架構概觀
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。 此繫結包含單一的自訂傳輸繫結項目，能夠啟用與 SQL Server 資料庫通訊。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]包裝[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]執行階段，而且會公開給應用程式可以透過[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道架構。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與透過 ADO.NET 的 SQL Server 資料庫通訊。  


 下圖顯示使用開發解決方案的端對端架構[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
 ![](../../adapters-and-accelerators/adapter-sql/media/05e2a88c-a3cc-42a7-9c06-cfdb7c071e70.gif "05e2a88c-a3cc-42a7-9c06-cfdb7c071e70")  

  
## <a name="consuming-the-adapter"></a>使用配接器  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]公開 （expose) SQL Server 資料庫，作為[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務用戶端應用程式。 若要執行作業及存取 SQL Server 資料庫上的資料，用戶端應用程式交換的 SOAP 訊息[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]透過[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道。 上圖顯示四種方式在其中[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可以取用。  
  
-   **透過[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型應用程式**。 A[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型應用程式使用執行 SQL Server 資料庫上的作業[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型交換 SOAP 訊息直接與[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 請參閱[開發 SQL 應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)。
  
-   **透過[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型應用程式**。 A[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型應用程式上呼叫的方法[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]用戶端上的 SQL Server 資料庫執行作業。 A[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]用戶端模型所公開的作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]做為.NET 方法。 您可以使用[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]或 WCF ServiceModel Metadata Utility Tool (svcutil.exe) 來建立[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]所公開的中繼資料從用戶端類別[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  請參閱[開發 SQL 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)。
  
-   **透過 BizTalk 接收位置或傳送埠設定為使用 Microsoft BizTalk Wcf-custom 配接器**。 Wcf-custom 配接器可讓您使用[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]擴充性功能。 您可以使用 Wcf-custom 配接器選取和設定的 SQL DB 繫結和行為的接收位置或傳送埠。 如需有關如何使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案，請參閱[開發 BizTalk Server 應用程式](../../core/developing-biztalk-server-applications.md)。 
  
-   **透過 IIS 裝載的 Web 服務**。 在此案例中，使用配接器所產生的 WCF 服務 proxy 會裝載於 IIS 使用的標準 WCF Http 繫結。 這樣會在服務合約公開為 Web 服務給外部使用者。 IIS 自動裝載配接器在執行階段，其亦會與 SQL Server 資料庫通訊。  
  
## <a name="the-sql-adapter-and-wcf"></a>SQL 配接器和 WCF  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]提供程式設計模型，根據 SOAP 訊息交換，透過用戶端和服務之間的通道。 通訊的用戶端和服務所公開的端點之間傳送這些訊息。 端點所組成：  
  
-   *端點位址*，指定接收訊息的位置。  
  
-   A*繫結*，以指定用來交換訊息的通訊協定。  
  
-   A*合約*，指定端點所公開的作業和資料類型。  
  
 繫結堆疊在彼此的上方來定義與端點交換訊息的方式的一或多個繫結項目所組成。 最少的傳輸和編碼，可用來與端點交換訊息，必須指定繫結。 端點之間交換訊息會透過所組成的一個或多個通道的通道堆疊。 每個通道是其中一個繫結項目設定之端點的繫結中的具象實作。 

[WCF 文件](http://go.microsoft.com/fwlink/?LinkID=196850)包含更多詳細資料，關於[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]，而[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]程式設計模型。  
  
 [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]公開[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]自訂繫結，SQL DB 繫結 (**Microsoft.Adapters.SQLDB.SQLDBBinding**)。 根據預設，此繫結包含單一的自訂傳輸繫結項目，SQL DB 配接器繫結項目 (**Microsoft.Adapters.SQLDB.SQLDBAdapter**)，可讓 SQL Server 資料庫上的作業。  
  
 **Microsoft.Adapters.SQLDB.SQLDBBinding** （SQL DB 繫結） 和**Microsoft.Adapters.SQLDB.SQLDBAdapter** （SQL DB 配接器繫結項目） 都是公用的類別，也會公開至組態系統。 公開 SQL DB 配接器繫結項目，因為您可以建立自己的自訂[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]能夠擴充功能的繫結[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 例如，您可以實作自訂繫結以支援企業單一登入 (SSO) 中[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道或服務模型方案。 執行此動作的原因就是彙總資料庫作業為單一的多功能作業或執行自訂的應用程式所實作的作業和作業上的 SQL Server 資料庫之間的結構描述轉換。  
  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]建置最上層的[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，並執行最上層的[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]執行階段。 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]軟體架構和工具，基礎結構提供[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會使用提供給使用者和配接器用戶端的一組豐富的功能。  

## <a name="sql-adapter-and-the-wcf-lob-adapter-sdk"></a>SQL 配接器和 WCF LOB 配接器 SDK
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]實作運用功能所提供的核心元件的一組[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]並提供透過 ADO.NET 的 SQL Server 資料庫的連接。  
  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]做為透過此軟體層[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]介面[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)];ADO.NET 可做為透過此圖層[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與 SQL Server 資料庫的介面。 下圖顯示的內部元件之間的關聯性[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]之間以及這些元件和 ADO.NET。  
  
 ![](../../adapters-and-accelerators/adapter-sql/media/0b15e33b-7f59-4228-bb50-0455f7ed3d85.gif "0b15e33b-7f59-4228-bb50-0455f7ed3d85")  
 
   
## <a name="adonet"></a>ADO.NET  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與透過 ADO.NET 的 SQL Server 資料庫連接。 ADO.NET 提供一致的存取資料來源，例如 SQL Server，並加速擷取、 處理和修改資料來源中的資料。 深入了解[ADO.NET](https://msdn.microsoft.com/library/e80y5yhx.aspx)。
  
 SQL 用戶端提供的 SQL Server 資料庫的連接能力。 您連接到 SQL Server 資料庫所提供的連線 URI 以[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 此連線的 URI 包含 SQL Server 安裝所在電腦的名稱和資料庫的名稱。 如需連線 URI 的詳細資訊，請參閱[建立 SQL Server 的連接](../../adapters-and-accelerators/adapter-sql/create-a-connection-to-sql-server.md)。  
  
## <a name="see-also"></a>另請參閱  

 [瞭解 BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)