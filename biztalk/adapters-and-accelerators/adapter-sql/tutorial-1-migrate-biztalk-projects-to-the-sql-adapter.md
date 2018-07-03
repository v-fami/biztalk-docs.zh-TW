---
title: 教學課程 1： 將 BizTalk 專案移轉至 SQL 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b4d2dbb-e37c-4d70-831f-3bdac3c28c97
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea64d98404d247a47e8cad8df421c81752fe63e0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013303"
---
# <a name="tutorial-1-migrate-biztalk-projects-to-the-sql-adapter"></a>教學課程 1： 移轉至 SQL 配接器的 BizTalk 專案
舊版的 SQL 配接器隨附於 Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]不同於以 WCF 為基礎[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]在許多方面，包括：  
  
- 建立 BizTalk 專案的設計階段經驗。  
  
- 中繼資料的擷取體驗。  
  
- 結構描述檔案名稱和命名空間。  
  
- 資料類型對應。  
  
- 可以使用配接器執行的作業。  
  
- 在 BizTalk Server 管理主控台中的實體連接埠設定  
  
  移轉 BizTalk 專案建立使用 SQLadapter 舊版的主題會說明這些差異。  
  
  不過，您可以對使用舊版的配接器所建立的 BizTalk 專案中的變更，並讓其使用以 WCF 為基礎[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
  本教學課程會提供指示，您應該對現有的 BizTalk 專案使用舊版的配接器所建立的變更。  
  
> [!NOTE]
>  在本教學課程中，為了保持簡潔，舊版的 SQL 配接器將會被稱為 vPrev SQL 配接器。 同樣地，使用 vPrev SQL 配接器的 BizTalk 專案會被稱為 vPrev BizTalk 專案。  
> 
> [!IMPORTANT]
>  本教學課程提供有關如何移轉 vPrev SQL 配接器 BizTalk 專案的執行基本的插入作業會在 SQL Server 資料庫資料表的指引。 本教學課程並未涵蓋所有可能的案例，從 vPrev SQL 配接器移轉至新的 WCF 式[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 您必須使用本移轉教學課程中，做為基礎，並據此修改要與您現有的專案相關的變更。  
  
## <a name="sample-used-for-the-tutorial"></a>用於本教學課程的範例  
 本教學課程是以示範如何移轉 vPrev BizTalk 專案的範例 (SQL_Migration) 為基礎。 提供了 Microsoft 範例[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]。 如需詳細資訊，請參閱範例。  
  
## <a name="prerequisites"></a>必要條件  
  
-   您必須具有 vPrev BizTalk 專案。 本教學課程包含 SQL Server 資料庫中，執行插入作業的客戶資料表上的 BizTalk 專案。 Customer 資料表具有下列設計：  
  
    |資料行名稱|描述|  
    |-----------------|-----------------|  
    |v_custid|主索引鍵，整數類型，識別欄位|  
    |[屬性]|nchar(10) 類型|  
  
-   您必須擁有執行插入作業使用 vPrev SQL 配接器的 SQL Server 資料庫的要求訊息。 產生使用 vPrev SQL 配接器的插入作業的結構描述必須符合 「 要求 」 訊息。  
  
-   您應已完成中的步驟[之前您開發 BizTalk 應用程式](http://msdn.microsoft.com/library/3539741d-5266-43d4-9b7b-73e82f0ed4f6)。  
  
## <a name="understanding-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>了解 BizTalk 專案使用舊版配接器的建立  
 建立 vPrev BizTalk 專案的關鍵要素是：  
  
-   **BizTalk 協調流程**。 這是簡單的協調流程會挑選要求訊息的檔案位置，傳送要求訊息至 SQL Server 資料庫使用 Wcf-custom 傳送接收連接埠、 接收回應，並將它儲存到另一個檔案的位置。  
  
-   **您想要在 SQL Server 資料庫上執行的作業結構描述**。 本教學課程包含執行插入作業在 Customer 資料表上的 BizTalk 專案。 產生針對 Customer 資料表的結構描述是 InsertCustomerService.xsd。 此結構描述會產生使用 vPrev SQL 配接器。  
  
-   **要求訊息**。 要執行插入作業在 Customer 資料表上的要求訊息。 要求訊息的結構描述符合的插入作業結構描述，因為由舊版的 SQL 配接器顯示。  
  
## <a name="how-to-migrate-a-biztalk-project-created-using-the-previous-version-of-the-adapter"></a>如何移轉 BizTalk 專案可讓您建立使用舊版的配接器  
 本移轉教學課程的目標是要讓您傳送要求訊息，這符合 vPrev SQL 配接器使用 WCF 自訂連接埠，只有處理程序符合以 WCF 為基礎的訊息所產生的結構描述[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 因此，簡單地說，在移轉作業牽涉到設定不符合 WCF 為基礎的處理訊息的 WCF 自訂連接埠[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]的結構描述。  
  
 不過，若要能夠適當地設定 WCF 自訂連接埠，您必須執行下列工作：  
  
- 產生使用 WCF 為基礎的 Customer 資料表的 Insert 作業的中繼資料[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
- 執行插入作業使用 vPrev SQL 配接器的要求訊息來執行插入作業使用以 WCF 為基礎的要求訊息對應[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
- 將使用以 WCF 為基礎所接收的回應訊息對應[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]vPrev SQL 配接器的回應訊息。  
  
- 建立 WCF 自訂 SQL 傳送接收中的連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
- 設定 WCF 自訂連接埠，若要使用的要求和回應的對應。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [步驟 1： 修改 vPrev BizTalk 專案使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/step-1-modify-the-vprev-biztalk-project-using-the-sql-adapter.md)  
  
-   [步驟 2： 設定協調流程中使用 SQL 配接器的 BizTalk Server 管理主控台](../../adapters-and-accelerators/adapter-sql/step-2-configure-the-orchestration-to-use-the-sql-adapter-in-biztalk-server.md)  
  
-   [步驟 3： 測試移轉應用程式使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/step-3-test-the-migrated-application-that-uses-the-sql-adapter.md)  
  
## <a name="see-also"></a>另請參閱  
 [SQL 配接器教學課程](../../adapters-and-accelerators/adapter-sql/sql-adapter-tutorials.md)