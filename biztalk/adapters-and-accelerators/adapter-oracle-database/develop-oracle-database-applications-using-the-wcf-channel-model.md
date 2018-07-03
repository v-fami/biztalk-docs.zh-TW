---
title: 開發使用 WCF 通道模型的 Oracle 資料庫應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF channel model, streaming
- channel programming, streaming
- WCF channel model, performing operations
- developing applications, by using the WCF channel model
- streaming, using the WCF channel model
- WCF channel model, developingn applications
- channel programming, performing operations
ms.assetid: cb6bf5fd-ff90-44bd-a9dd-03b00f12a78d
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4990ebb9e9aad612a82af42b3d186643da1e91ab
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002727"
---
# <a name="develop-oracle-database-applications-using-the-wcf-channel-model"></a>開發使用 WCF 通道模型的 Oracle 資料庫應用程式
您可以使用[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]通道模型使用[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]直接透過使用 Oracle DB 繫結建立通道執行個體傳送 XML 訊息。  
  
 透過使用強型別類別與 WCF 服務模型會公開的方法中使用 WCF 通道模型的優點之一是通道模型提供更精密地控制您的 Oracle 資料庫執行的作業。 為什麼？ WCF 通道模型中您可以直接控制您透過通道傳送訊息的內容。  
  
 在某些情況下，此額外控制層級能帶來好處。 比方說，當您使用 WCF 通道模型來執行資料表的更新作業時，您可以藉由略過資料行，從您傳遞的訊息中的更新範本選擇性地更新目標資料列中的資料行。 所公開的 update 方法[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]用戶端會使用範本，其中每個資料行包含資料表的結構描述中的強型別記錄參數。 如果資料行"nillable = false"的 WSDL，就必須更新使用 WCF 服務模型。  
  
 透過 WCF 服務模型的 WCF 通道模型提供的另一個主要優點是以端對端串流 Oracle 大型物件 (LOB) 資料類型的更完整支援。 使用 WCF 通道模型中，您可以執行端對端串流：  
  
- 若要更新資料表中的 LOB 資料行，或使用 UpdateLOB 作業檢視。  
  
- 在外和 IN，OUT 參數包含 LOB 程序和函式所傳回的資料。  
  
- SQLEXECUTE 作業的結果中包含的 LOB 資料。  
  
- LOB 資料行上，會傳回 POLLINGSTMT 作業。  
  
- 在 選取資料表或檢視表上作業所傳回的 LOB 資料行。  
  
  這是因為 WCF 通道模型中您直接控制如何於外寄訊息提供訊息內文和訊息本文，對傳入訊息的處理方式。  
  
  相反地，WCF 服務模型只提供：  
  
- 端對端的一項操作，ReadLOB 作業的 LOB 資料串流。  
  
- 若要更新 LOB 資料，以資料流處理方式的 Oracle 資料庫上沒有功能。  
  
  本主題中的各節說明如何執行作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用 WCF 通道模型。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用 Oracle 資料庫配接器的 WCF 通道模型概觀](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-channel-model-with-the-oracle-database-adapter.md) 
  
-   [建立通道，使用 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md) 
  
-   [使用 WCF 通道模型之 Oracle 資料庫上叫用作業](../../adapters-and-accelerators/adapter-oracle-database/invoke-operations-on-the-oracle-database-using-the-wcf-channel-model.md)  
  
-   [使用 WCF 通道模型的 Oracle 資料庫中執行 SQLEXECUTE 作業](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md)  
  
-   [在使用 WCF 通道模型的 Oracle 資料庫執行插入作業](../../adapters-and-accelerators/adapter-oracle-database/run-an-insert-operation-in-oracle-database-using-the-wcf-channel-model.md)  
  
-   [叫用使用 WCF 通道模型的 Oracle 資料庫中的函式](../../adapters-and-accelerators/adapter-oracle-database/invoke-a-function-in-oracle-database-using-the-wcf-channel-model.md)  
  
-   [使用 WCF 通道模型的 Oracle 資料庫中接收以輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-db-using-a-wcf-channel.md)  
  
-   [串流處理 Oracle 資料庫 LOB 資料類型使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md)