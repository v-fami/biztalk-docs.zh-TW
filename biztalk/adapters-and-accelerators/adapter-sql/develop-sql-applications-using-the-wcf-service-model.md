---
title: 開發 SQL 應用程式使用 WCF 服務模型 |Microsoft Docs
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
ms.openlocfilehash: afeb8d7aac2dd2a29f60c89cf54c86ef2e4519df
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983975"
---
# <a name="develop-sql-applications-using-the-wcf-service-model"></a>開發 SQL 應用程式使用 WCF 服務模型
[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] 提供做為替代程式設計模型的 WCF 通道呼叫 WCF 服務模型的程式設計模型。  
  
 WCF 服務模型會使用熟悉的.NET 架構來隱藏在通道上交換的 SOAP 訊息複雜性。 服務模型會完成這個簡化的讀入記憶體中的整個 SOAP 訊息，再將資訊複製到.NET 資料結構。 載入記憶體中的長訊息，不過，可能不適合某些應用程式。 在這些情況下，開發人員應該使用的 WCF 通道模型。 如需使用 WCF 通道模型的詳細資訊，請參閱[開發 SQL 應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)。  
  
 在最低層級，[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]呈現所在的用戶端來叫用服務上的作業在用戶端與服務端點之間建立的通道上交換的 SOAP 訊息的 WCF 通道模型。 WCF 通道模型會公開資料型別和方法，讓您直接在 WCF 通道架構上運作。 WCF 通道模型會將您提供了兩個應用程式和您所建立的 SOAP 訊息的內容上的直接控制和[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]取用它們。 不過，建立格式正確的 SOAP 訊息，透過通道傳送和驗證傳回回覆訊息可以是詳細的確切的工作。  
  
 WCF 服務模型會使用 proxy 類別，來叫用目標服務上的作業，或從用戶端接收作業。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]公開為 WCF 服務，您可以在其叫用作業的 SQL Server 資料庫。  
  
- 用來叫用作業的目標服務上的 proxy 類別呼叫的 WCF 用戶端類別。 此類別的模型做為強型別參數使用的.NET 方法的服務所公開的作業。 藉由使用 WCF 服務模型，您可以叫用所公開之作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]做為 WCF 用戶端上的.NET 方法。 如需有關 WCF 用戶端的詳細資訊，請參閱 < [WCF Client Overview](https://msdn.microsoft.com/library/ms735103.aspx)。
  
  您可以使用下列工具來產生 WCF 用戶端類別和相關聯協助程式程式碼，從服務中繼資料，[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]公開 （expose):  
  
- **ServiceModel Metadata Utility Tool (svcutil.exe)**，隨附 WCF。  
  
- **[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]** ，其中隨附[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]，並與整合[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]設計經驗。 此工具會提供標準的 Microsoft Windows 介面，提供功能強大的瀏覽和搜尋功能，對配接器所公開的作業。 如需如何產生 WCF 用戶端應用程式的詳細資訊，請參閱[產生的 SQL Server 成品的 WCF 用戶端或 WCF 服務合約](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)。  
  
   在本節中的主題包含的資訊、 程序和範例，以協助您建立及使用 WCF 服務模型開發應用程式，使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [SQL 配接器的 WCF 服務模型概觀](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-service-model-with-the-sql-adapter.md)  
  
-   [中繼資料和 SQL 配接器使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sql/metadata-and-the-wcf-service-model-with-the-sql-adapter.md)  
  
-   [產生 WCF 用戶端或 SQL Server 成品的 WCF 服務合約](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md)  
  
-   [設定 SQL 配接器的用戶端繫結](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md)  
  
-   [插入、 更新、 刪除或選取在介面資料表和檢視使用 WCF 服務模型的作業](../../adapters-and-accelerators/adapter-oracle-ebs/insert-update-delete-select-on-interface-tables-and-views-with-a-wcf-service.md)  
  
-   [具有大型的資料型別在 SQL 中使用 WCF 服務模型的資料表和檢視表執行作業](../../adapters-and-accelerators/adapter-sql/read-or-update-tables-and-views-with-large-data-types-in-sql-with-a-wcf-service.md)  
  
-   [叫用預存程序，在 SQL 中使用 WCF 服務模型](../../adapters-and-accelerators/adapter-sql/invoke-stored-procedures-in-sql-using-the-wcf-service-model.md)  
  
-   [使用 WCF 服務模型叫用 SQL Server 中的純量函式](../../adapters-and-accelerators/adapter-sql/invoke-scalar-functions-in-sql-server-by-using-the-wcf-service-model.md)  
  
-   [使用 WCF 服務模型叫用 SQL Server 中的資料表值函式](../../adapters-and-accelerators/adapter-sql/invoke-table-valued-functions-in-sql-server-by-using-the-wcf-service-model.md)  
  
-   [在 SQL 中使用 WCF 服務模型的 ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-executenonquery-in-sql-using-wcf-service-model.md)  
  
-   [使用 WCF 服務模型中的 SQL 配接器的輪詢 SQL Server](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-wcf-service-model.md)  
  
-   [從使用 WCF 服務模型的 SQL 接收查詢通知](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-from-sql-using-the-wcf-service-model.md)  
  
## <a name="see-also"></a>另請參閱  
[開發 SQL 應用程式](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)