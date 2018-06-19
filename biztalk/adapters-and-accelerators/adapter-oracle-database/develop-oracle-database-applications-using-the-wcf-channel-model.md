---
title: 開發 Oracle 資料庫應用程式使用 WCF 通道模型 |Microsoft 文件
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
ms.openlocfilehash: 77fb9b6ca1fc70a55b59c6708450b8d94a01eff8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214982"
---
# <a name="develop-oracle-database-applications-using-the-wcf-channel-model"></a>開發 Oracle 資料庫應用程式使用 WCF 通道模型
您可以使用[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]使用通道模型[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]直接透過使用 Oracle 資料庫繫結建立通道執行個體傳送 XML 訊息。  
  
 使用 WCF 通道模型，透過使用強型別類別和方法的 WCF 服務模型會公開的其中一個優點是通道模型提供更細微的控制，透過您的 Oracle 資料庫執行的作業。 為什麼？ WCF 通道模型中直接控制您透過通道傳送訊息的內容。  
  
 在某些情況下，控制此額外層級可能有所助益。 例如，當您執行更新作業的資料表上使用 WCF 通道模型，您可以藉由略過您傳遞的訊息中的更新範本的資料行選擇性地更新目標資料列中的資料行。 所公開的 update 方法[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]用戶端會使用範本，其中包含每個資料行中的資料表結構描述的強型別記錄參數。 如果資料行"nillable = false 」 在 WSDL，就必須更新使用 WCF 服務模型。  
  
 WCF 通道模型提供的 WCF 服務模型透過另一個主要優點是更廣泛支援端對端的資料流的 Oracle 大型物件 (LOB) 資料類型。 使用 WCF 通道模型中，您可以執行端對端資料流：  
  
-   若要更新資料表中的 LOB 資料行或檢視使用 UpdateLOB 作業。  
  
-   在和 IN，OUT 參數包含 LOB 程序和函數所傳回的資料。  
  
-   SQLEXECUTE 運算的結果中包含的 LOB 資料。  
  
-   上傳回 POLLINGSTMT 作業中的 LOB 資料行。  
  
-   上傳回的資料表或檢視表上的選取作業的 LOB 資料行。  
  
 這是因為 WCF 通道模型中您直接控制如何於外寄訊息提供訊息內文和您要如何處理內送訊息的訊息本文。  
  
 相反地，WCF 服務模型只會提供：  
  
-   端對端的一項操作，ReadLOB 作業的 LOB 資料串流。  
  
-   若要更新 LOB 資料，以資料流處理方式的 Oracle 資料庫上沒有功能。  
  
 本主題中的各節說明如何執行作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用 WCF 通道模型。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用 Oracle 資料庫配接器的 WCF 通道模型概觀](../../adapters-and-accelerators/adapter-oracle-database/overview-of-the-wcf-channel-model-with-the-oracle-database-adapter.md) 
  
-   [建立通道使用 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md) 
  
-   [使用 WCF 通道模型之 Oracle 資料庫上叫用作業](../../adapters-and-accelerators/adapter-oracle-database/invoke-operations-on-the-oracle-database-using-the-wcf-channel-model.md)  
  
-   [使用 WCF 通道模型的 Oracle 資料庫中執行 SQLEXECUTE 操作](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md)  
  
-   [在使用 WCF 通道模型的 Oracle 資料庫執行插入作業](../../adapters-and-accelerators/adapter-oracle-database/run-an-insert-operation-in-oracle-database-using-the-wcf-channel-model.md)  
  
-   [叫用使用 WCF 通道模型的 Oracle 資料庫中的函式](../../adapters-and-accelerators/adapter-oracle-database/invoke-a-function-in-oracle-database-using-the-wcf-channel-model.md)  
  
-   [使用 WCF 通道模型的 Oracle 資料庫中收到輪詢基礎資料變更的訊息](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-db-using-a-wcf-channel.md)  
  
-   [資料流處理的 Oracle 資料庫 LOB 資料類型使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md)