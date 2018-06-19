---
title: 開發 SQL 應用程式使用 WCF 服務模型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d3ecfd6f-9144-4e41-a4b8-0c768a6ac254
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 645b783ad23d79b4f6be177f6d38287e62abab1a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223206"
---
# <a name="develop-sql-applications-using-the-wcf-service-model"></a>開發 SQL 應用程式使用 WCF 服務模型
[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]提供程式設計模型的 WCF 通道的替代方式為呼叫 WCF 服務模型程式設計模型。  
  
 WCF 服務模型會使用熟悉的.NET 開發架構，隱藏的通道上交換 SOAP 訊息複雜性。 服務模型可完成此簡化作業由讀入記憶體中的整個 SOAP 訊息，然後再將資訊複製到.NET 資料結構。 長訊息載入記憶體，不過，可能不適合某些應用程式。 在這些情況下，開發人員應該使用 WCF 通道模型。 如需有關如何使用 WCF 通道模型的詳細資訊，請參閱[開發 SQL 應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)。  
  
 最低層級，[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]呈現在其中用戶端叫用作業服務藉由在用戶端與服務端點之間建立的通道上交換 SOAP 訊息的 WCF 通道模型。 WCF 通道模型公開資料型別和方法，可讓您直接在 WCF 通道架構上運作。 WCF 通道模型會將您提供直接控制您所建立之 SOAP 訊息的內容以及方式這兩個應用程式和[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]取用。 不過，建立格式正確透過通道傳送的 SOAP 訊息並驗證傳回回覆訊息可以是詳細的精確的工作。  
  
 WCF 服務模型會使用 proxy 類別，來叫用目標服務上的作業，或從用戶端接收作業。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]公開為 WCF 服務，您可以在其叫用作業的 SQL Server 資料庫。  
  
-   用來叫用作業的目標服務上的 proxy 類別，稱為 WCF 用戶端類別。 這個類別會建立具有強型別參數的.NET 方法為服務所公開的作業。 藉由使用 WCF 服務模型，您可以叫用所公開的作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]為 WCF 用戶端上的.NET 方法。 如需 WCF 用戶端的詳細資訊，請參閱[WCF 用戶端概觀](https://msdn.microsoft.com/library/ms735103.aspx)。
  
 您可以使用下列工具來產生 WCF 用戶端類別，以及相關聯的協助程式程式碼取自服務中繼資料，[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]公開：  
  
-   **ServiceModel Metadata Utility Tool (svcutil.exe)**，隨附 WCF。  
  
-   **[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]** ，隨附[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]以及與整合[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]設計經驗。 此工具會顯示標準 Microsoft Windows 介面提供強大瀏覽和搜尋功能，對配接器會公開的作業。 如需如何產生 WCF 用戶端應用程式的詳細資訊，請參閱[產生 WCF 用戶端或 WCF 服務合約的 SQL Server 成品](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。  
  
     本節中的主題包含資訊、 程序和範例，以協助您建立及使用 WCF 服務模型來開發應用程式使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [SQL 配接器的 WCF 服務模型概觀](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-service-model-with-the-sql-adapter.md)  
  
-   [中繼資料和 SQL 配接器之 WCF 服務模型](../../adapters-and-accelerators/adapter-sql/metadata-and-the-wcf-service-model-with-the-sql-adapter.md)  
  
-   [SQL Server 成品產生 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)  
  
-   [設定 SQL 配接器的用戶端繫結](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md)  
  
-   [插入、 更新、 刪除或選取介面資料表和檢視表使用 WCF 服務模型的作業](../../adapters-and-accelerators/adapter-oracle-ebs/insert-update-delete-select-on-interface-tables-and-views-with-a-wcf-service.md)  
  
-   [使用 SQL 使用 WCF 服務模型中的大型資料類型執行資料表和檢視表上的作業](../../adapters-and-accelerators/adapter-sql/read-or-update-tables-and-views-with-large-data-types-in-sql-with-a-wcf-service.md)  
  
-   [叫用預存程序，在 SQL 中使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sql/invoke-stored-procedures-in-sql-using-the-wcf-service-model.md)  
  
-   [使用 WCF 服務模型來叫用 SQL Server 中的純量函式](../../adapters-and-accelerators/adapter-sql/invoke-scalar-functions-in-sql-server-by-using-the-wcf-service-model.md)  
  
-   [使用 WCF 服務模型來叫用 SQL Server 中的資料表值函式](../../adapters-and-accelerators/adapter-sql/invoke-table-valued-functions-in-sql-server-by-using-the-wcf-service-model.md)  
  
-   [ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery SQL 使用 WCF 服務模型中的作業](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-executenonquery-in-sql-using-wcf-service-model.md)  
  
-   [搭配 WCF 服務模型中使用 SQL 配接器的輪詢 SQL Server](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-wcf-service-model.md)  
  
-   [使用 WCF 服務模型的 sql 接收查詢通知](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-from-sql-using-the-wcf-service-model.md)  
  
## <a name="see-also"></a>另請參閱  
[開發 SQL 應用程式](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)