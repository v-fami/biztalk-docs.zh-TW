---
title: BizTalk Adapter for SQL Server 的架構概觀 |Microsoft Docs
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
ms.openlocfilehash: 37b5a21380b3883967e4478940ee7abbee6760c2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995487"
---
# <a name="architecture-overview-of-biztalk-adapter-for-sql-server"></a>BizTalk Adapter for SQL Server 的架構概觀
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。 這個繫結包含單一的自訂傳輸繫結項目，以便與 SQL Server 資料庫進行通訊。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]包裝[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]執行階段，而且會公開給應用程式可以透過[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道架構。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與透過 ADO.NET 的 SQL Server 資料庫通訊。  


 下圖顯示使用開發的解決方案的端對端架構[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
 ![](../../adapters-and-accelerators/adapter-sql/media/05e2a88c-a3cc-42a7-9c06-cfdb7c071e70.gif "05e2a88c-a3cc-42a7-9c06-cfdb7c071e70")  

  
## <a name="consuming-the-adapter"></a>使用配接器  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]公開 （expose) SQL Server 資料庫，作為[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務用戶端應用程式。 若要執行的作業，並存取 SQL Server 資料庫上的資料，用戶端應用程式會交換使用的 SOAP 訊息[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]透過[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道。 上圖顯示四種方式，在其中[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可取用。  
  
- **透過[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型的應用程式**。 A[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型應用程式使用執行 SQL Server 資料庫上的作業[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型來交換 SOAP 訊息直接與[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 請參閱[開發 SQL 應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)。
  
- **透過[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型的應用程式**。 A[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型的應用程式上呼叫方法[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]用戶端上的 SQL Server 資料庫執行作業。 A[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]用戶端模型所公開之作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]為.NET 方法。 您可以使用[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]或 WCF ServiceModel Metadata Utility Tool (svcutil.exe) 來建立[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]用戶端類別所公開的中繼資料從[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  請參閱[開發 SQL 應用程式使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)。
  
- **透過 BizTalk 接收位置或傳送埠設定為使用 Microsoft BizTalk Wcf-custom 配接器**。 Wcf-custom 配接器可讓您使用[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]擴充性功能。 使用 Wcf-custom 配接器中，您可以選取和設定 SQL DB 繫結和行為的接收位置或傳送埠。 如需有關如何使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案，請參閱[開發 BizTalk Server 應用程式](../../core/developing-biztalk-server-applications.md)。 
  
- **透過 IIS 裝載的 Web 服務**。 在此案例中，使用標準 WCF Http 繫結在 IIS 中裝載 WCF 服務 proxy 產生使用配接器。 這會在服務合約公開為 Web 服務的外部使用者。 IIS 自動裝載在執行階段，其接著會與 SQL Server 資料庫通訊的配接器。  
  
## <a name="the-sql-adapter-and-wcf"></a>SQL 配接器和 WCF  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] 提供程式設計模型，根據用戶端與服務之間的通道上的 SOAP 訊息交換。 通訊的用戶端和服務所公開的端點之間傳送這些訊息。 端點所組成：  
  
- *端點位址*，以指定訊息接收到的位置。  
  
- A*繫結*，指定用來交換訊息的通訊協定。  
  
- A*合約*，指定端點所公開的作業和資料類型。  
  
  繫結是由堆疊在彼此的上層定義與端點交換訊息的方式的一或多個繫結項目所組成。 最少的傳輸和編碼用來與端點交換訊息，必須指定繫結。 端點之間交換訊息是透過通道堆疊所組成的一或多個通道。 每個通道是其中一個繫結項目，設定端點的繫結中的具象實作。 

[WCF 文件](http://go.microsoft.com/fwlink/?LinkID=196850)包含更多詳細資料，關於[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]，和[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]程式設計模型。  
  
 [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]公開[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]自訂繫結，SQL DB 繫結 (**Microsoft.Adapters.SQLDB.SQLDBBinding**)。 根據預設，此繫結包含單一的自訂傳輸繫結項目，SQL DB 配接器繫結項目 (**Microsoft.Adapters.SQLDB.SQLDBAdapter**)，可讓 SQL Server 資料庫上的作業。  
  
 **Microsoft.Adapters.SQLDB.SQLDBBinding** （SQL DB 繫結） 和**Microsoft.Adapters.SQLDB.SQLDBAdapter** （SQL DB 配接器繫結項目） 是公用的類別，也會公開至組態系統。 SQL DB 配接器繫結項目公開的因為您可以建置自己的自訂[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]繫結的擴充功能的支援[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 例如，您可以實作自訂繫結，以支援企業單一登入 (SSO)，在[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道或服務模型方案。 彙總的資料庫作業為單一多功能的作業，或執行自訂的應用程式所實作的作業和作業上的 SQL Server 資料庫之間的結構描述轉換是執行此動作的原因。  
  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]之上的[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，並執行最上層的[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]執行階段。 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]提供軟體架構和工具的基礎結構[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]會使用提供給使用者和配接器用戶端的一組豐富的功能。  

## <a name="sql-adapter-and-the-wcf-lob-adapter-sdk"></a>SQL 配接器和 WCF LOB 配接器 SDK
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]會實作一組核心元件，利用所提供的功能[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]，並提供透過 ADO.NET 的 SQL Server 資料庫的連線。  
  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]做為透過此軟體層[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]介面[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)];ADO.NET 可做為透過此層[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與 SQL Server 資料庫的介面。 下圖顯示的內部元件之間的關聯性[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]和這些元件與 ADO.NET 之間。  
  
 ![](../../adapters-and-accelerators/adapter-sql/media/0b15e33b-7f59-4228-bb50-0455f7ed3d85.gif "0b15e33b-7f59-4228-bb50-0455f7ed3d85")  
 
   
## <a name="adonet"></a>ADO.NET  
 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與透過 ADO.NET 的 SQL Server 資料庫連線。 ADO.NET 提供一致的方式存取資料來源，例如 SQL Server，並加速擷取、 處理及修改資料來源中的資料。 深入了解[ADO.NET](https://msdn.microsoft.com/library/e80y5yhx.aspx)。
  
 SQL 用戶端提供連線到 SQL Server 資料庫。 您連接到 SQL Server 資料庫所提供的連線 URI 以[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 此連線的 URI 包含 SQL Server 安裝所在電腦的名稱和資料庫的名稱。 如需連線 URI 的詳細資訊，請參閱[建立 SQL Server 的連接](../../adapters-and-accelerators/adapter-sql/create-a-connection-to-sql-server.md)。  
  
## <a name="see-also"></a>另請參閱  

 [了解 BizTalk Adapter for SQL Server](../../adapters-and-accelerators/adapter-sql/understand-biztalk-adapter-for-sql-server.md)