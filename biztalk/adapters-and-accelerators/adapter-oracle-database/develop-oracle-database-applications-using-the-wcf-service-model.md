---
title: "開發 Oracle 資料庫應用程式使用 WCF 服務模型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performing operations, by using the WCF service model
- developing applications, by using the WCF service model
- WCF service model, using to develop applications
ms.assetid: 3f2c60b2-4835-492d-8c3c-ed35d3e4c517
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 548ca256d4395aefd67681229e9669ef2afcc2f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="develop-oracle-database-applications-using-the-wcf-service-model"></a>開發使用 WCF 服務模型的 Oracle 資料庫應用程式
最低層級，[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]提供程式設計的模型中的用戶端叫用作業服務藉由在用戶端與服務端點之間建立的通道上交換 SOAP 訊息。 此模型中，稱為 WCF 通道模型，公開資料型別和方法，可讓您直接在 WCF 通道架構上運作。 WCF 通道模型會將您提供直接控制您所建立之 SOAP 訊息的內容以及方式這兩個應用程式和[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]取用這些; 不過，建立格式正確的 SOAP 訊息，透過通道傳送，並驗證傳回回覆訊息可以是詳細的精確的工作。  
  
 基於這個理由，[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]提供其他呼叫 WCF 服務模型的程式設計模型。 WCF 服務模型牽涉到使用目標服務上叫用作業，或從用戶端接收作業的 proxy 類別。  
  
-   用來叫用作業的目標服務上的 proxy 類別會呼叫 WCF 用戶端類別。 這個類別會建立具有強型別參數的.NET 方法為服務所公開的作業。 藉由使用 WCF 服務模型，您可以叫用所公開的作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]為 WCF 用戶端上的.NET 方法。 WCF 用戶端的詳細資訊，請參閱 < WCF 用戶端概觀 >，網址[http://go.microsoft.com/fwlink/?LinkId=91458](http://go.microsoft.com/fwlink/?LinkId=91458)。  
  
-   在 WCF 服務模型中，服務所公開的服務合約介面所表示。 此受管理的程式碼的表示方式的服務合約呼叫 WCF 服務合約。 WCF 服務合約的模型做為其強型別參數的方法作業。 從用戶端接收作業，您會實作 WCF 服務，從這個介面的類別。 然後，您就可以裝載在此類別的執行個體**system.servicemodel.servicehost 內**啟用用戶端來叫用您的程式碼的作業。 您可以使用 WCF 服務模型和以 POLLINGSTMT 作業目標的 WCF 服務合約，接收有關 Oracle 資料庫使用輪詢作業的結果[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
 您使用工具來產生 WCF 用戶端類別或 WCF 服務合約，以及相關聯的協助程式程式碼取自服務中繼資料，[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]公開。 您可以使用下列工具之一：  
  
-   ServiceModel Metadata Utility Tool (svcutil.exe)，隨附 WCF  
  
-   [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，隨附[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]  
  
 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]與整合[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]設計經驗，以及顯示標準的 Microsoft Windows 介面提供強大瀏覽和搜尋功能，對配接器所公開的作業。 如需如何產生 WCF 用戶端或 WCF 服務合約的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 Oracle 資料庫方案成品](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)。  
  
 它會呈現的模型.NET 程式設計人員熟悉且可透過通道隱藏基礎 SOAP 訊息交換的複雜性，因為 WCF 服務模型通常是最佳選擇程式設計為開發解決方案[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 不過，有一些的案例中的 WCF 通道模型可能是較好的選擇。 例如，WCF 服務模型只支援 ReadLOB 作業資料流。 這是因為序列化和還原序列化之 XML 表示的 SOAP 訊息中的物件與用來代表服務模型中的.NET 類型之間涉及讀入記憶體中的整個訊息。 （ReadLOB 運算的結果是此規則的例外狀況）。  
  
 WCF 通道模型上的所有作業資料流的 XML 節點層級和資料層的資料流上的 ReadLOB 和 UpdateLOB 作業提供支援。 如果您正在處理查詢，傳回大型結果集，或嘗試更新資料表中的 LOB 欄位，WCF 通道模型可能是較好的選擇。 如需有關如何使用 WCF 通道模型的詳細資訊，請參閱[開發 Oracle 資料庫應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)。  
  
 本節中的主題包含資訊、 程序和範例，以協助您建立及使用 WCF 服務模型來開發應用程式使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [與 Oracle 資料庫配接器的 WCF 服務模型概觀](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-service-model-with-the-oracle-database-adapter.md)  
  
-   [中繼資料和 WCF 服務模型，與 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/metadata-and-the-wcf-service-model-with-oracle-database.md)  
  
-   [為 Oracle 資料庫方案成品產生 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md)  
  
-   [設定 Oracle 資料庫的用戶端繫結](../../adapters-and-accelerators/adapter-oracle-database/configure-a-client-binding-for-the-oracle-database.md)  
  
-   [使用 WCF 服務模型執行基本 Insert、 Update、 Delete 和 Select 作業](../../adapters-and-accelerators/adapter-oracle-database/insert-update-delete-select-operations-in-oracle-db-using-a-wcf-service.md)  
  
-   [使用 WCF 服務模型來完成資料表的作業與 Oracle 資料庫中的大型資料類型](../../adapters-and-accelerators/adapter-oracle-database/run-operations-on-tables-with-large-data-types-in-oracle-db-using-a-wcf-service.md)  
  
-   [使用 WCF 服務模型叫用函式和 Oracle 資料庫中的程序](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md)  
  
-   [使用 WCF 服務模型的 Oracle 資料庫中執行的作業使用 REF CURSOR](../../adapters-and-accelerators/adapter-oracle-database/run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model.md)  
  
-   [使用 WCF 服務模型的 Oracle 資料庫中執行的作業使用的記錄類型](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md)  
  
-   [執行 SQLEXECUTE 操作 Oracle 資料庫中，使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md)  
  
-   [Oracle 資料庫中接收輪詢基礎資料變更的訊息，使用 WCF 服務模型](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-db-using-a-wcf-service.md)  
  
-   [使用 WCF 服務模型接收的 Oracle 資料庫變更通知](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-using-the-wcf-service-model1.md)