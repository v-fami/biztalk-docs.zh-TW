---
title: "Oracle 資料庫配接器範例 |Microsoft 文件"
description: "可以使用 BizTalk Server、 WCF 服務模型時，與 WCF 通道模型的 oracle DB WCF 配接器範例"
ms.custom: 
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 744f19ce-3126-4745-92dd-4f68443180fc
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5bfef9fcfce65d8aede1cd905a53469c565977f
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="samples-for-the-oracle-database-adapter"></a>適用於 Oracle 資料庫配接器範例
範例如[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]分類成：  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 範例  
  
-   WCF 服務模型範例  
  
-   WCF 通道模型範例  

  
這些範例位於[BizTalk Adapter Pack 2010: Oracle 資料庫配接器範例](https://www.microsoft.com/download/details.aspx?id=4675)。 建立資料表和封裝範例中所使用的 SQL 指令碼會包含項目。 

> [!NOTE]
> [!INCLUDE[files-need-updated](../../includes/files-need-updated.md)]
  
下列清單描述的範例。
  
## <a name="biztalk-server-samples"></a>BizTalk Server 範例
  
|範例目錄名稱|Description|  
|---------------------------|-----------------|  
|Func_RecordTypes|示範如何使用記錄型別參數和傳回值中函數和程序使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。|  
|Func_RefCursor|示範如何使用函數和程序使用中的 REF CURSOR 參數[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。|  
|InvokeFunction|示範如何叫用 Oracle 資料庫使用中的函式[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。|  
|InvokeOverloadedProc|示範如何使用多載函式和 Oracle 資料庫中的程序叫用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。|  
|Operate_BFILE|示範如何使用 Oracle 程序中使用 Oracle BFILE 類型[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。|  
|Operate_LOB|示範如何執行 ReadLOB 和 UpdateLOB 作業在資料表上使用的 LOB 資料類型[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。|  
|PollingQuery|示範如何設定輪詢查詢，並接收結果使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。|  
|SelectAccTable|示範如何執行 select 查詢 Oracle 資料庫資料表使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。|  
|SqlExec|示範如何執行參數化的查詢使用 SQLEXECUTE 操作 Oracle 資料庫使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。|  
  
## <a name="wcf-service-model-samples"></a>WCF 服務模型範例  
  
|範例目錄名稱|Description|  
|---------------------------|-----------------|  
|OracleBfileTypeSM|示範如何在 Oracle 程序中發生的 Oracle 資料表和做為參數的基本 SQL 作業中使用 Oracle BFILE 型別。|  
|OracleOverloadsSM|示範如何叫用多載函式和封裝中的程序。|  
|OraclePollingSM|示範如何設定輪詢查詢，而且接收的結果。|  
|OracleRecordTypesSM|示範如何使用記錄型別參數和傳回值，函式和程序中。|  
|OracleRefCursorsSM|示範如何使用函數和程序中的 REF CURSOR 參數|  
|OracleTransactedDmlSM|示範如何使用 WCF 服務模型的交易中執行的 Oracle 資料庫上的作業。|  
  
## <a name="wcf-channel-model-samples"></a>WCF 通道模型範例  
  
|範例目錄名稱|Description|  
|---------------------------|-----------------|  
|OraclePollingCM|示範如何設定輪詢查詢，而且接收的結果。|  
|OracleStreamingDemo|示範如何執行端對端使用 UpdateLOB 和資料表的 Select 作業的 LOB 資料的資料流|  
|OracleTransactedDmlCM|示範如何使用 WCF 通道模型的交易中執行的 Oracle 資料庫上的作業。|  
  

## <a name="see-also"></a>另請參閱  
[開發您的 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)