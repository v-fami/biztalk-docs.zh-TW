---
title: 開發 BizTalk Server 中的 Oracle 資料庫應用程式 |Microsoft Docs
description: 建立 Oracle DB 應用程式使用 WCF，或在 BizTalk Server 與 BizTalk 配接器組件 (BAP)
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d4a685b2-ac17-4949-bc77-001f56450847
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5f83d335f92798a8d1b2c4c2c32cb20e23ffe26
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36977663"
---
# <a name="develop-your-oracle-database-applications"></a>開發您的 Oracle 資料庫應用程式

## <a name="overview"></a>概觀
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。 用戶端應用程式可以取用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]到 Oracle 資料庫成品上叫用作業。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]可取用：  
  
- 中的實體連接埠繫結透過[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案。  
  
- 藉由叫用方法的執行個體上[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]用戶端 proxy。  
  
- 為裝載[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務。  
  
- 透過通道執行個體使用的程式碼中傳送 SOAP 訊息[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型。  

## <a name="biztalk-vs-wcf-service-vs-wcf-channel"></a>BizTalk 與 WCF 服務與 WCF 通道  
 下表中：  
  
- 列出可對 Oracle 資料庫使用的不同作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。  
  
- 提供的連結，其中包含執行工作使用所選的方法的相關資訊的主題 ([!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，WCF 服務模型或 WCF 通道模型)。  
  
|工作|BizTalk Server|WCF 服務模型|WCF 通道模型|  
|----------|--------------------|-----------------------|-----------------------|  
|基本 Insert、 Update、 Delete 與資料表和檢視表的 Select 作業|[插入、 更新、 刪除或選取 使用 BizTalk Server 與 Oracle 資料庫的作業](../../adapters-and-accelerators/adapter-oracle-database/insert-update-delete-select-operations-using-biztalk-server-with-oracle-db.md)|[插入、 更新、 刪除或選取 使用 WCF 服務模型的 Oracle 資料庫中的 作業](../../adapters-and-accelerators/adapter-oracle-database/insert-update-delete-select-operations-in-oracle-db-using-a-wcf-service.md)|[在使用 WCF 通道模型的 Oracle 資料庫執行插入作業](../../adapters-and-accelerators/adapter-oracle-database/run-an-insert-operation-in-oracle-database-using-the-wcf-channel-model.md)|  
|資料表和檢視表包含 LOB 資料的作業|[具有 Oracle 資料庫中的大型物件資料類型的資料表執行作業](../../adapters-and-accelerators/adapter-oracle-database/run-operations-on-tables-with-large-object-data-types-in-oracle-database.md)|[完成使用 WCF 服務模型的 Oracle 資料庫中的大型資料類型的資料表作業](../../adapters-and-accelerators/adapter-oracle-database/run-operations-on-tables-with-large-data-types-in-oracle-db-using-a-wcf-service.md)||  
|函式和預存程序作業|[叫用函式，並使用 BizTalk Server 的 Oracle 資料庫中的程序](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-biztalk-server.md)|[叫用函式，並使用 WCF 服務模型的 Oracle 資料庫中的程序](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md)|[叫用使用 WCF 通道模型的 Oracle 資料庫中的函式](../../adapters-and-accelerators/adapter-oracle-database/invoke-a-function-in-oracle-database-using-the-wcf-channel-model.md)|  
|叫用多載函式和程序|[叫用多載函式，並使用 BizTalk Server 的 Oracle 資料庫中的程序](../../adapters-and-accelerators/adapter-oracle-database/run-overloaded-functions-and-procedures-in-oracle-database-using-biztalk-server.md)|[叫用函式，並使用 WCF 服務模型的 Oracle 資料庫中的程序](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md)||  
|函式和程序與 REF CURSOR 參數的作業|[叫用函式和程序與使用 BizTalk Server 的 Oracle 資料庫中的 REF CURSOR](../../adapters-and-accelerators/adapter-oracle-database/run-functions-and-procedures-with-ref-cursors-in-oracle-db-using-biztalk-server.md)|[使用 WCF 服務模型的 Oracle 資料庫中執行的作業使用 REF CURSOR](../../adapters-and-accelerators/adapter-oracle-database/run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model.md)||  
|函式和程序的作業記錄類型|[叫用函式和程序與使用 BizTalk Server 的 Oracle 資料庫中的記錄類型](../../adapters-and-accelerators/adapter-oracle-database/run-functions-and-procedures-with-record-types-in-oracle-db-with-biztalk-server.md)|[使用 WCF 服務模型的 Oracle 資料庫中執行作業使用的記錄類型](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md)||  
|資料表和檢視上的作業對具有 BFILE 資料類型|[具有 BFILE 資料類型，使用 BizTalk Server 的 Oracle 資料庫中的資料表執行作業](../../adapters-and-accelerators/adapter-oracle-database/run-operations-on-tables-with-bfile-data-types-in-oracle-db-using-biztalk.md)|||  
|SQLEXECUTE 作業|[使用 BizTalk Server 的 Oracle 資料庫中執行 SQLEXECUTE 作業](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-biztalk-server.md)|[使用 WCF 服務模型的 Oracle 資料庫中執行 SQLEXECUTE 作業](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md)|[使用 WCF 通道模型的 Oracle 資料庫中執行 SQLEXECUTE 作業](../../adapters-and-accelerators/adapter-oracle-database/run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model.md)|  
|接收以輪詢為基礎的資料變更訊息|[使用 BizTalk Server 輪詢 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/poll-oracle-database-using-biztalk-server.md)|[使用 WCF 服務模型的 Oracle 資料庫中接收以輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-db-using-a-wcf-service.md)|[使用 WCF 通道模型的 Oracle 資料庫中接收以輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-db-using-a-wcf-channel.md)|  
|執行的 Oracle 資料庫上的複合作業|[執行複合作業上使用 BizTalk Server 的 Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md)|||  
|接收資料庫變更通知|[接收使用 BizTalk Server 的 Oracle 資料庫變更通知](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-using-biztalk-server.md)|[接收使用 WCF 服務 Model1 Oracle 資料庫變更通知](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-using-the-wcf-service-model1.md)||  
  

  
## <a name="next-steps"></a>後續的步驟
 在本節中的主題提供資訊、 程序和範例，以協助您開發應用程式，使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]在這兩[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]程式設計解決方案。 
  
-   [建立 Oracle 資料庫的連線](../../adapters-and-accelerators/adapter-oracle-database/create-a-connection-to-the-oracle-database.md)
  
-   [取得 Visual Studio 中的 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md) 
  
-   [設定 Oracle 資料庫繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md)
  
-   [Oracle 資料庫配接器中的資料流處理大型物件資料類型](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md)
  
-   [在 Oracle 資料庫配接器接收以輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md)
  
-   [開發 BizTalk Server 應用程式](../../core/developing-biztalk-server-applications.md)
  
-   [開發使用 WCF 服務模型的 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)  
  
-   [開發使用 WCF 通道模型的 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)  
  
-   [從 Oracle 資料庫，以程式設計方式取得中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-programmatically-from-the-oracle-database.md)  
  
-   [搭配使用 SharePoint 與 Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/use-the-oracle-database-adapter-with-sharepoint.md)
  
-   [配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)  
  
-   [設定與 Oracle 資料庫的交易隔離等級和交易等待時間](../../adapters-and-accelerators/adapter-oracle-database/configure-transaction-isolation-level-and-transaction-timeout-with-oracle-db.md)

- [使用 svcutil.exe](use-the-servicemodel-metadata-utility-with-the-oracle-db-adapter-in-biztalk.md)