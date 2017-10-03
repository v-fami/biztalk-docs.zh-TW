---
title: "教學課程 4： 建立使用 BizTalk Server 2013 的混合式應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a9de95f-7d2c-437d-be5b-0062592f32c6
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5c11b163f34a1320052de585c7ddfc79afb03db4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013"></a>教學課程 4： 建立使用 BizTalk Server 2013 的混合式應用程式
本節提供的逐步解說說明如何建立與 [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)] 及 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 有關的混合式應用程式。  
  
## <a name="business-scenario"></a>商務案例  
 Northwind 是一家透過合作夥伴 (Contoso 即為其中一個合作夥伴) 以一般檔案 EDI 訊息的形式接收銷售訂單的企業。 Northwind 想要設定一個可執行下列作業的端對端應用程式：  
  
-   **管理 EDI 訊息處理**– 應用程式的這個模組必須驗證從 Contoso 接收的訊息是否符合標準 EDI 訊息格式。 這個模組還必須產生所有必要的通知，以確認訊息處理成功。  
  
-   **使用商務邏輯來處理資料**– 一旦成功驗證並處理 EDI 訊息，Northwind 就必須執行訊息根據商務邏輯，以便進一步處理。 例如，若所接收訊息中的訂單數量超過指定的數量，則會將資料存放在 SQL Server 資料庫中。 否則，資料會傳送至共用檔案位置。  
  
 為了實現這個狀況，Northwind 決定設定一個混合式應用程式，以便在雲端進行 EDI 訊息處理，並同時在內部部署中進行商務邏輯驅動的資料處理。 Northwind 使用下列項目來設定此混合式應用程式：  
  
-   **[!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)]**-Azure BizTalk 入口網站提供[!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)]可讓客戶可設定交易夥伴和 EDI 協議[!INCLUDE[winazure](../includes/winazure-md.md)]。 Northwind 使用 [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)] – 2012 年 4 月發行，用於建立及部署協議，以便處理內送 EDI 訊息、根據 X12 840 銷售訂單結構描述進行驗證、將訊息轉換為 Northwind 所需的結構描述，再將訊息傳送至服務匯流排佇列。 所以，若要開發混合式應用程式，應將資料從服務匯流排佇列傳送至內部部署的應用程式。  
  
-   **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**– Service Bus 在新的介面卡 (**Sb-messaging**) 適用於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可讓應用程式接收來自服務匯流排實體，例如佇列、 主題的訊息，依此類推到[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 做為一部分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式中，Northwind 使用協調流程決定接收的銷售訂單中要求的數量是否超過 100。 如果數量大於 100，要將訊息插入至呼叫的 SQL Server 資料庫資料表**SalesOrder**。 如果數量少於 100，則會將訊息傳送至共用檔案位置。  
  
     為了將訊息插入 SQL Server 資料庫資料表中，Northwind 使用 [!INCLUDE[adaptersql](../includes/adaptersql-md.md)] 中提供的 [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。  
  
### <a name="end-to-end-message-flow"></a>端點對端點訊息流程  
 這就是訊息通過混合式應用程式的方式：  
  
1.  Contoso 會將 X12 銷售訂單訊息傳送至已在雲端部署 EDI 協議的端點。  
  
2.  訊息透過 EDI 協議處理成功之後，就會傳送至服務匯流排佇列。  
  
3.  SB-Messaging 接收配接器會使用服務匯流排佇列中的訊息，並將在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中部署的協調流程具現化，以根據訂單數量將訊息傳送至不同的目的地。  
  
4.  如果訂購數量大於 100，協調流程會插入訊息**SalesOrder**資料表。 如果訂購數量少於或等於 100，則會將訊息寫入至共用檔案位置。  
  
## <a name="set-up-your-computer"></a>設定電腦  
 本教學課程要求您執行四項主要活動。 下表列出各項活動與其軟體需求：  
  
|活動|必要軟體|  
|--------------|-----------------------|  
|建立 EDI 協議所需的 EDI 成品|本教學課程與 [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)] 一起建立 – 2012 年 4 月發行的版本以及 X12 840 銷售訂單結構描述。 這些可以從下載[http://go.microsoft.com/fwlink/p/?LinkId=235057](http://go.microsoft.com/fwlink/p/?LinkId=235057)。|  
|建立和部署 EDI 協議|因為 EDI 協議是部署在 Azure，您只需要 Web 瀏覽器 (如 Internet Explorer) 就能登入 Azure BizTalk Portal。|  
|建置、部署及設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式|如果您想要佈建[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦上的 Azure VM，請遵循指示[http://msdn.microsoft.com/library/azure/jj248689.aspx](http://msdn.microsoft.com/library/azure/jj248689.aspx)。|  
|將測試訊息傳送到 EDI 協議端點|您可以使用 [!INCLUDE[appfabricintegration](../includes/appfabricintegration-md.md)] 隨附的範例套件中提供的 MessageSender 工具。 您可以下載範例套件的[http://go.microsoft.com/fwlink/p/?LinkId=235057](http://go.microsoft.com/fwlink/p/?LinkId=235057)。|  
  
 您可以選擇在相同或不同電腦上安裝這些項目。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [（適用於 Azure) 的步驟 1： 建立 EDI 專案](../core/step-1-for-azure-create-the-edi-project.md)  
  
-   [（適用於 Azure) 的步驟 2： 建立 EDI 協議](../core/step-2-for-azure-create-an-edi-agreement.md)  
  
-   [（適用於 Azure) 的步驟 3： 建立服務匯流排佇列](../core/step-3-for-azure-create-a-service-bus-queue.md)  
  
-   [步驟 4 （內部部署）： 建立 SQL Server 資料表](../core/step-4-on-premises-create-the-sql-server-table.md)  
  
-   [步驟 5 （內部部署）： 產生插入訊息插入至 SalesOrder 資料表的結構描述](../core/step-5-generate-the-schema-for-inserting-a-message-into-salesorder-table.md)  
  
-   [步驟 6 （內部部署）： 建立轉換，將訊息從佇列插入結構描述對應](../core/step-6-map-the-message-from-the-queue-to-the-insert-schema.md)  
  
-   [步驟 7 （內部部署）： 建立協調流程](../core/step-7-on-premises-create-an-orchestration.md)  
  
-   [步驟 8 （在內部部署）： 設定 BizTalk Server 應用程式](../core/step-8-on-premises-configure-the-biztalk-server-application.md)  
  
-   [步驟 9： 測試方案](../core/step-9-test-the-solution.md)