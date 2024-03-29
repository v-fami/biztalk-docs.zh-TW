---
title: SQL 配接器範例 |Microsoft Docs
description: 可以使用 BizTalk Server、 WCF 服務模型，與 WCF 通道模型的 SQL WCF 配接器範例
ms.custom: ''
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2438696-bc51-46df-81ca-00c17a52736e
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f7ff1e686fd8de344c4de4513fbda84003c69a8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982631"
---
# <a name="samples-for-the-sql-adapter"></a>SQL 配接器的範例

範例[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]會分類為：  
  
- [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 範例  
  
- WCF 服務模型範例  
  
- WCF 通道模型範例  
  
這些範例位於[BizTalk Adapter Pack 2010: SQL 配接器範例](https://www.microsoft.com/download/details.aspx?id=22455)。 建立物件的 SQL 指令碼使用在範例中，例如資料庫資料表，而包含程序。 

> [!NOTE]
> [!INCLUDE[files-need-updated](../../includes/files-need-updated.md)]
  
下列清單描述的範例。
  
## <a name="biztalk-server-samples"></a>BizTalk Server 範例  
  
|  範例目錄名稱  |                                                                                          描述                                                                                          |
|-------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ExecuteStoredProcedure  |      示範如何叫用使用配接器使用的 SQL Server 資料庫中的預存程序[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。      |
|       SelectTable       |  示範如何執行 SQL Server 資料庫資料表使用的介面卡上的選取作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  |
|   CompositeOperations   |    示範如何執行複合作業使用的介面卡在 SQL Server 資料庫上[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。    |
|      TypedPolling       |   示範如何使用配接器使用 SQL Server 資料庫上執行強型別輪詢[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。   |
|   FILESTREAMOperation   | 示範如何執行 SQL Server 2008 資料庫使用的介面卡上的 FILESTREAM 作業[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 |
| IncrementalNotification | 示範如何從 SQL Server 資料庫使用的配接器接收累加通知[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 |
| Employee_PurchaseOrder  |                  範例根據[教學課程 2： 員工-訂單程序使用 SQL 配接器](tutorial-2-employee-purchase-order-process-using-the-sql-adapter.md)。                  |
  
## <a name="wcf-service-model-samples"></a>WCF 服務模型範例   
  
|範例目錄名稱|描述|  
|---------------------------|-----------------|  
|EmployeeBasicOps|示範如何執行 Insert、 Select、 Update 和刪除使用配接器在 SQL Server 資料庫上的作業。|  
|ExecuteReader|示範如何叫用 ExecuteReader 作業上使用配接器的 SQL Server 資料庫。|  
|Execute_StoredProc|示範如何叫用使用配接器的 SQL Server 資料庫中的預存程序。|  
|Execute_TypedStoredProcedure|示範如何叫用強型別的預存程序中使用配接器的 SQL Server 資料庫。|  
|Records_FILESTREAM_Op|示範如何更新使用配接器的 SQL Server 資料庫資料表中的 FILESTREAM 資料。|  
|ScalarFunction_ServiceModel|示範如何叫用使用配接器的 SQL Server 資料庫中的純量函式。|  
|TableFunction_ServiceModel|示範如何叫用中使用配接器的 SQL Server 資料庫的資料表值函式。|  
|Polling_ServiceModel|示範如何從 SQL Server 資料庫，使用配接器接收以輪詢為基礎的資料變更訊息。|  
|TypedPolling_ServiceModel|示範如何從 SQL Server 資料庫，使用配接器接收強型別輪詢為基礎的資料變更訊息。|  
|Notification_ServiceModel|示範如何從 SQL Server 資料庫，使用配接器接收查詢通知。|  
  
## <a name="wcf-channel-model-samples"></a>WCF 通道模型範例 
  
|範例目錄名稱|描述|  
|---------------------------|-----------------|  
|EmployeeInsertOp|示範如何執行插入作業上使用配接器的 SQL Server 資料庫。|  
|Polling_ChannelModel|示範如何從 SQL Server 資料庫，使用配接器接收以輪詢為基礎的資料變更訊息。|  
  
## <a name="see-also"></a>另請參閱  
[開發 SQL 應用程式](develop-your-sql-applications.md)