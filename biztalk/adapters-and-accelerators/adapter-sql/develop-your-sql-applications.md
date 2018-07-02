---
title: 開發 BizTalk Server 中的 SQL 應用程式 |Microsoft Docs
description: 建立 SQL 配接器應用程式使用 WCF，或在 BizTalk Server 與 BizTalk 配接器組件 (BAP)
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fac4b5b0-2980-4784-a081-e795654292ed
caps.latest.revision: 39
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b003010ae8cb9394dd956a97bd3e05ef855d3e73
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978455"
---
# <a name="develop-your-sql-applications"></a>開發 SQL 應用程式

## <a name="overview"></a>概觀
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]繫結。 用戶端應用程式可以取用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]叫用 SQL Server 成品的作業。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]可取用：  
  
- 中的實體連接埠繫結透過[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案。  
  
- 藉由叫用用戶端 proxy 的執行個體上的方法。  
  
- 為託管的 WCF 服務。  
  
- 透過通道中的執行個體使用的 WCF 通道模型的程式碼中傳送 SOAP 訊息。  

## <a name="biztalk-vs-wcf-service-vs-wcf-channel"></a>BizTalk 與 WCF 服務與 WCF 通道    
 下表中：  
  
- 列出可以在 SQL Server 執行的不同作業使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。  
  
- 提供的連結，其中包含執行工作使用所選的方法的相關資訊的主題 ([!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，WCF 服務模型，WCF 通道模型)。  
  
|工作|BizTalk Server|WCF 服務模型|WCF 通道模型|  
|----------|--------------------|-----------------------|-----------------------|  
|執行基本 Insert、 Update、 Delete，然後選取資料表和檢視表上的作業|[插入、 更新、 刪除或選取 使用 SQL 配接器的 BizTalk Server 作業](insert-update-delete-or-select-using-the-sql-adapter-in-biztalk-server.md)|[插入、 更新、 刪除或選取在介面資料表和檢視使用 WCF 服務模型的作業](../../adapters-and-accelerators/adapter-oracle-ebs/insert-update-delete-select-on-interface-tables-and-views-with-a-wcf-service.md)|[在使用 WCF 通道模型的 SQL 執行插入作業的資料表](run-an-insert-operation-on-a-table-in-sql-using-the-wcf-channel-model.md)|  
|資料表和大型資料的檢視上執行的作業類型資料行<br /><br /> （也包含 FILESTREAM 作業使用配接器的相關資訊）|[資料表和檢視表包含使用 SQL 配接器的大型資料類型的作業](supported-operations-on-tables-and-views-with-large-data-types-with-sql-adapter.md)|[具有大型的資料型別在 SQL 中使用 WCF 服務模型的資料表和檢視表執行作業](read-or-update-tables-and-views-with-large-data-types-in-sql-with-a-wcf-service.md)|-|  
|執行預存程序|[使用 BizTalk Server 的 SQL Server 中執行預存程序](execute-stored-procedures-in-sql-server-using-biztalk-server.md)|[叫用預存程序，在 SQL 中使用 WCF 服務模型](invoke-stored-procedures-in-sql-using-the-wcf-service-model.md)|-|  
|執行具有單一參數的預存程序，而不需使用 BizTalk 協調流程|[使用 BizTalk Server 的 SQL Server 中執行具有單一 XML 參數的預存程序](execute-stored-procedures-with-a-single-xml-parameter-in-sql-using-biztalk.md)|-|-|  
|執行包含在定義中的 FOR XML 子句的預存程序|[執行具有 FOR XML 子句中使用 BizTalk Server 的 SQL Server 中的預存程序](execute-stored-procedures-having-a-for-xml-clause-in-sql-server-using-biztalk.md)|-|-|  
|執行 SQL Server 上的複合作業|[執行 SQL Server 上使用 BizTalk Server 的複合作業](run-composite-operations-on-sql-server-using-biztalk-server.md)|-|-|  
|叫用 SQL Server 中的純量函式|[叫用使用 BizTalk Server 的 SQL Server 中的純量函式](invoke-scalar-functions-in-sql-server-using-biztalk-server.md)|[使用 WCF 服務模型叫用 SQL Server 中的純量函式](invoke-scalar-functions-in-sql-server-by-using-the-wcf-service-model.md)|-|  
|叫用 SQL Server 中的資料表值函式|[叫用使用 BizTalk Server 的 SQL Server 中的資料表值函式](invoke-table-valued-functions-in-sql-server-using-biztalk-server.md)|[使用 WCF 服務模型叫用 SQL Server 中的資料表值函式](invoke-table-valued-functions-in-sql-server-by-using-the-wcf-service-model.md)|-|  
|執行**ExecuteReader**， **ExecuteScalar**，或**ExecuteNonQuery**作業|[ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業中使用 BizTalk Server 的 SQL](executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md)|[在 SQL 中使用 WCF 服務模型的 ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業](executereader-executescalar-executenonquery-in-sql-using-wcf-service-model.md)|-|  
|接收以輪詢為基礎的資料變更訊息|[使用 SQL 配接器與 BizTalk Server 輪詢 SQL Server](poll-sql-server-using-the-sql-adapter-with-biztalk-server.md)|[使用 WCF 服務模型中的 SQL 配接器的輪詢 SQL Server](poll-sql-server-using-the-sql-adapter-with-wcf-service-model.md)|[使用 WCF 通道模型，從 SQL Server 接收以輪詢為基礎的資料變更訊息](receive-polling-based-data-changed-messages-from-sql-server-using-a-wcf-channel.md)|  
|接收的 SQL Server 通知|[接收使用 BizTalk Server 的 SQL 查詢通知](receive-sql-query-notifications-using-biztalk-server.md)|[從使用 WCF 服務模型的 SQL 接收查詢通知](receive-query-notifications-from-sql-using-the-wcf-service-model.md)|-|  

## <a name="next-steps"></a>後續的步驟  
 在本節中的主題提供資訊、 程序和範例，以協助您開發應用程式，使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]在[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和.NET 程式設計解決方案。 

- [建立 SQL Server 的連線](create-a-connection-to-sql-server.md)
- [在 Visual Studio 中取得 SQL Server 作業的中繼資料](get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md)
- [中繼資料節點識別碼](metadata-node-ids2.md)
- [使用繫結屬性](read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)
- [必要條件：設定 MSDTC](configure-msdtc-on-sql-server-and-adapter-client.md)
- [使用 SQL 配接器開發 BizTalk 應用程式](develop-biztalk-applications-using-the-sql-adapter.md)
- [使用 WCF 服務模型開發應用程式](develop-sql-applications-using-the-wcf-service-model.md)
- [使用 WCF 通道模型開發應用程式](develop-sql-applications-using-the-wcf-channel-model.md)
- [範例](samples-for-the-sql-adapter.md)
- [設定交易隔離等級和交易等待時間](configure-transaction-isolation-level-and-transaction-timeout-with-sql.md)
  
