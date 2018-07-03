---
title: 開發使用 WCF 服務模型的 Oracle 資料庫應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performing operations, by using the WCF service model
- developing applications, by using the WCF service model
- WCF service model, using to develop applications
ms.assetid: 3f2c60b2-4835-492d-8c3c-ed35d3e4c517
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cc677e0bcb8159bb750a91c9e1ea4aa0b5fbf2d5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999935"
---
# <a name="develop-oracle-database-applications-using-the-wcf-service-model"></a>開發使用 WCF 服務模型的 Oracle 資料庫應用程式
在最低層級，[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]呈現所在的用戶端來叫用服務上的作業在用戶端與服務端點之間建立的通道上交換的 SOAP 訊息的程式設計模型。 此模型中，稱為 WCF 通道模型中，會公開資料型別和方法，讓您直接在 WCF 通道架構上運作。 WCF 通道模型會將您提供了兩個應用程式和您所建立的 SOAP 訊息的內容上的直接控制和[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]取用這些; 不過，建立格式正確的 SOAP 訊息，透過通道傳送和驗證傳回回覆訊息可以是詳細的確切的工作。  
  
 基於這個理由，[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]提供另一個呼叫 WCF 服務模型的程式設計模型。 WCF 服務模型牽涉到使用 proxy 類別叫用目標服務上的作業，或從用戶端接收作業。  
  
- 用來叫用作業的目標服務上的 proxy 類別呼叫的 WCF 用戶端類別。 此類別的模型做為強型別參數使用的.NET 方法的服務所公開的作業。 藉由使用 WCF 服務模型，您可以叫用所公開之作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]做為 WCF 用戶端上的.NET 方法。 如需有關 WCF 用戶端的詳細資訊，請查看 < WCF 用戶端概觀 > [ http://go.microsoft.com/fwlink/?LinkId=91458 ](http://go.microsoft.com/fwlink/?LinkId=91458)。  
  
- 在 WCF 服務模型中，服務所公開的服務合約被以介面而定。 Managed 程式碼的這個表示法的服務合約呼叫 WCF 服務合約。 WCF 服務合約會模型化為具有強型別參數的方法的作業。 若要接收從用戶端的作業，您會實作類別時，WCF 服務，從這個介面。 然後，您就可以裝載在此類別的執行個體**System.ServiceModel.ServiceHost**来讓用戶端來叫用您的程式碼的作業。 使用 WCF 服務模型和以 POLLINGSTMT 作業為目標的 WCF 服務合約，您可以接收的 Oracle 資料庫使用的輪詢作業結果[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
  您使用工具來產生 WCF 用戶端類別或 WCF 服務合約和相關聯協助程式程式碼，從服務中繼資料，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]公開 （expose)。 您可以使用下列工具：  
  
- ServiceModel Metadata Utility Tool (svcutil.exe)，隨附於 WCF  
  
- [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，隨附 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]  
  
  [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]與整合[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]設計體驗並提供標準的 Microsoft Windows 介面，提供功能強大的瀏覽和搜尋功能，對配接器所公開的作業。 如需如何產生 WCF 用戶端或 WCF 服務合約的詳細資訊，請參閱[產生的 Oracle 資料庫解決方案成品的 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)。  
  
  由於它會呈現的模型.NET 程式設計人員所熟悉且可透過通道會隱藏基礎 SOAP 訊息交換的複雜性，WCF 服務模型通常是最佳的選擇，以開發適用於程式設計解決方案[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 不過，有的案例中的 WCF 通道模型可能是較好的選擇。 例如，WCF 服務模型只支援 ReadLOB 作業串流。 這是因為序列化和還原序列化 SOAP 訊息中的物件的 XML 表示法與用來表示服務模型中的.NET 類型之間需要讀取整個訊息載入記憶體。 （ReadLOB 作業的結果是此規則的例外狀況）。  
  
  WCF 通道模型 XML 節點層級資料流處理的所有作業和資料層的資料都流 ReadLOB 和 UpdateLOB 作業提供支援。 如果您正在處理查詢會傳回大型結果集，或嘗試更新資料表中的 LOB 欄位，WCF 通道模型可能是較好的選擇。 如需使用 WCF 通道模型的詳細資訊，請參閱[開發 Oracle 資料庫應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)。  
  
  在本節中的主題包含的資訊、 程序和範例，以協助您建立及使用 WCF 服務模型開發應用程式，使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [Oracle 資料庫配接器使用 WCF 服務模型的概觀](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-service-model-with-the-oracle-database-adapter.md)  
  
-   [中繼資料和 WCF 服務模型與 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/metadata-and-the-wcf-service-model-with-oracle-database.md)  
  
-   [為 Oracle 資料庫方案成品產生 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)  
  
-   [設定用戶端繫結的 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/configure-a-client-binding-for-the-oracle-database.md)  
  
-   [使用 WCF 服務模型執行基本 Insert、 Update、 Delete 和 Select 作業](../../adapters-and-accelerators/adapter-oracle-database/insert-update-delete-select-operations-in-oracle-db-using-a-wcf-service.md)  
  
-   [使用 WCF 服務模型來完成 Oracle 資料庫中的大型資料類型的資料表作業](../../adapters-and-accelerators/adapter-oracle-database/run-operations-on-tables-with-large-data-types-in-oracle-db-using-a-wcf-service.md)  
  
-   [叫用函式和使用 WCF 服務模型的 Oracle 資料庫中的程序](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md)  
  
-   [使用 WCF 服務模型的 Oracle 資料庫中執行的作業使用 REF CURSOR](../../adapters-and-accelerators/adapter-oracle-database/run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model.md)  
  
-   [使用 WCF 服務模型的 Oracle 資料庫中執行作業使用的記錄類型](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md)  
  
-   [使用 WCF 服務模型，Oracle 資料庫中執行 SQLEXECUTE 作業](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md)  
  
-   [接收以輪詢為基礎的資料變更訊息中使用 WCF 服務模型的 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-db-using-a-wcf-service.md)  
  
-   [使用 WCF 服務模型接收的 Oracle 資料庫變更通知](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-using-the-wcf-service-model1.md)