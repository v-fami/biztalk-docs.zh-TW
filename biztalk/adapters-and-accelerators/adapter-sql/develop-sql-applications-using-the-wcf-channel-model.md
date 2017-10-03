---
title: "開發 SQL 應用程式使用 WCF 通道模型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11df5cc2-b532-45a8-9055-d05f4704a6e5
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b503b0766a4848e05c9361fb151196ee43afd81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="develop-sql-applications-using-the-wcf-channel-model"></a>開發 SQL 應用程式使用 WCF 通道模型
您可以使用[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]使用通道模型[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]直接透過使用 SQL Server 繫結建立通道執行個體傳送 XML 訊息。  
  
 使用 WCF 通道模型，透過使用強型別類別和方法的 WCF 服務模型會公開的其中一個優點是通道模型提供更細微的控制，透過您在 SQL database 執行的作業。 此控制項是來自事實，在 WCF 通道模型中，您直接控制您透過通道傳送訊息的內容。  
  
 在某些情況下，控制此額外層級可能有所助益。 例如，當您執行更新作業的資料表上使用 WCF 通道模型，您可以藉由略過您傳遞的訊息中的更新範本的資料行選擇性地更新目標資料列中的資料行。 所需的唯一資料行是那些與"nillable = false 」 在 WSDL 中。 所公開的 update 方法[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]用戶端會使用範本，其中包含每個資料行中的資料表結構描述的強型別記錄參數。  
  
 本主題中的各節說明如何執行作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]使用 WCF 通道模型。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [SQL 配接器的 WCF 通道模型概觀](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-channel-model-with-the-sql-adapter.md)  
  
-   [建立使用 SQL 配接器的通道](../../adapters-and-accelerators/adapter-sql/create-a-channel-using-the-sql-adapter.md)  
  
-   [在使用 WCF 通道模型的 SQL 執行插入作業的資料表](../../adapters-and-accelerators/adapter-sql/run-an-insert-operation-on-a-table-in-sql-using-the-wcf-channel-model.md)  
  
-   [從 SQL Server 接收輪詢基礎資料變更的訊息，使用 WCF 通道模型](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-a-wcf-channel.md)  
  
## <a name="see-also"></a>另請參閱  
[開發 SQL 應用程式](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)