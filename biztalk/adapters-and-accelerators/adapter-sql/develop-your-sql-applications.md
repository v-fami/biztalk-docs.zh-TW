---
title: "開發 BizTalk Server 中的 SQL 應用程式 |Microsoft 文件"
description: "建立 SQL 配接器應用程式使用 WCF，或在 BizTalk Server 與 BizTalk 配接器組件 (BAP)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fac4b5b0-2980-4784-a081-e795654292ed
caps.latest.revision: "39"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e5be1f01a9d8180dea60f508cba1c4ff7c0964f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="develop-your-sql-applications"></a>開發 SQL 應用程式

## <a name="overview"></a>概觀
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]繫結。 用戶端應用程式可以取用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]至 SQL Server 成品上叫用作業。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可以取用：  
  
-   中的實體連接埠繫結透過[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]方案。  
  
-   藉由叫用用戶端 proxy 的執行個體上的方法。  
  
-   為託管的 WCF 服務。  
  
-   傳送 SOAP 訊息中使用 WCF 通道模型的程式碼是通道執行個體。  

## <a name="biztalk-vs-wcf-service-vs-wcf-channel"></a>BizTalk 與 WCF 服務與 WCF 通道    
 下表：  
  
-   列出可以在 SQL Server 執行的不同作業使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
-   提供的主題包含執行工作，使用所選的方法的相關資訊的連結 ([!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，WCF 服務模型時，WCF 通道模型)。  
  
|工作|BizTalk Server|WCF 服務模型|WCF 通道模型|  
|----------|--------------------|-----------------------|-----------------------|  
|執行基本 Insert、 Update、 Delete，然後選取資料表和檢視表上的作業|[插入、 更新、 刪除或選取 使用 SQL 配接器的 BizTalk Server 作業](insert-update-delete-or-select-using-the-sql-adapter-in-biztalk-server.md)|[插入、 更新、 刪除或選取介面資料表和檢視表使用 WCF 服務模型的作業](../../adapters-and-accelerators/adapter-oracle-ebs/insert-update-delete-select-on-interface-tables-and-views-with-a-wcf-service.md)|[在使用 WCF 通道模型的 SQL 執行插入作業的資料表](run-an-insert-operation-on-a-table-in-sql-using-the-wcf-channel-model.md)|  
|資料表和大型資料的檢視上執行的作業類型資料行<br /><br /> （也包括使用配接器的 FILESTREAM 作業的相關資訊）|[資料表和檢視表包含使用 SQL 配接器的大型資料類型的作業](supported-operations-on-tables-and-views-with-large-data-types-with-sql-adapter.md)|[使用 SQL 使用 WCF 服務模型中的大型資料類型執行資料表和檢視表上的作業](read-or-update-tables-and-views-with-large-data-types-in-sql-with-a-wcf-service.md)|-|  
|執行預存程序|[使用 BizTalk Server 的 SQL Server 中執行預存程序](execute-stored-procedures-in-sql-server-using-biztalk-server.md)|[叫用預存程序，在 SQL 中使用 WCF 服務模型](invoke-stored-procedures-in-sql-using-the-wcf-service-model.md)|-|  
|具有單一參數的預存程序執行而不需使用 BizTalk 協調流程|[使用 BizTalk Server 的 SQL Server 中執行具有單一 XML 參數的預存程序](execute-stored-procedures-with-a-single-xml-parameter-in-sql-using-biztalk.md)|-|-|  
|執行包含 FOR XML 子句中定義的預存程序|[執行預存程序在使用 BizTalk Server 的 SQL Server 中具有 FOR XML 子句](execute-stored-procedures-having-a-for-xml-clause-in-sql-server-using-biztalk.md)|-|-|  
|執行 SQL Server 上的複合作業|[執行複合操作 SQL Server 上使用 BizTalk Server](run-composite-operations-on-sql-server-using-biztalk-server.md)|-|-|  
|叫用 SQL Server 中的純量函式|[叫用使用 BizTalk Server 的 SQL Server 中的純量函式](invoke-scalar-functions-in-sql-server-using-biztalk-server.md)|[使用 WCF 服務模型來叫用 SQL Server 中的純量函式](invoke-scalar-functions-in-sql-server-by-using-the-wcf-service-model.md)|-|  
|叫用 SQL Server 中的資料表值函式|[叫用使用 BizTalk Server 的 SQL Server 中的資料表值函式](invoke-table-valued-functions-in-sql-server-using-biztalk-server.md)|[使用 WCF 服務模型來叫用 SQL Server 中的資料表值函式](invoke-table-valued-functions-in-sql-server-by-using-the-wcf-service-model.md)|-|  
|執行**ExecuteReader**， **ExecuteScalar**，或**ExecuteNonQuery**作業|[ExecuteReader、 ExecuteScalar 或使用 BizTalk Server 的 SQL 中的 ExecuteNonQuery 作業](executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md)|[ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery SQL 使用 WCF 服務模型中的作業](executereader-executescalar-executenonquery-in-sql-using-wcf-service-model.md)|-|  
|接收訊息以輪詢為基礎的資料變更|[與 BizTalk Server 使用 SQL 配接器的輪詢 SQL Server](poll-sql-server-using-the-sql-adapter-with-biztalk-server.md)|[搭配 WCF 服務模型中使用 SQL 配接器的輪詢 SQL Server](poll-sql-server-using-the-sql-adapter-with-wcf-service-model.md)|[從 SQL Server 接收輪詢基礎資料變更的訊息，使用 WCF 通道模型](receive-polling-based-data-changed-messages-from-sql-server-using-a-wcf-channel.md)|  
|接收 SQL Server 通知|[接收使用 BizTalk Server 的 SQL 查詢通知](receive-sql-query-notifications-using-biztalk-server.md)|[使用 WCF 服務模型的 sql 接收查詢通知](receive-query-notifications-from-sql-using-the-wcf-service-model.md)|-|  

## <a name="next-steps"></a>後續的步驟  
 本節中的主題提供資訊、 程序和範例，以協助您開發應用程式取用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和.NET 程式設計方案。 

- [建立 SQL Server 的連接](create-a-connection-to-sql-server.md)
- [取得 Visual Studio 中的 SQL Server 作業的中繼資料](get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)
- [中繼資料節點識別碼](metadata-node-ids2.md)
- [使用繫結屬性](read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)
- [必要條件： 設定 MSDTC](configure-msdtc-on-sql-server-and-adapter-client.md)
- [開發 BizTalk 應用程式使用 SQL 配接器](develop-biztalk-applications-using-the-sql-adapter.md)
- [開發應用程式使用 WCF 服務模型](develop-sql-applications-using-the-wcf-service-model.md)
- [開發應用程式使用 WCF 通道模型](develop-sql-applications-using-the-wcf-channel-model.md)
- [範例](samples-for-the-sql-adapter.md)
- [設定交易隔離等級和交易逾時](configure-transaction-isolation-level-and-transaction-timeout-with-sql.md)
  
