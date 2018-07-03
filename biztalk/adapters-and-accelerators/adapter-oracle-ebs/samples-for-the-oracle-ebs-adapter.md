---
title: Oracle EBS 配接器範例 |Microsoft Docs
description: 可以使用 BizTalk Server、 WCF 服務模型，與 WCF 通道模型的 oracle 企業 Business Suite WCF 配接器範例
ms.custom: ''
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 12f19f13-3b01-40d6-b12c-811f99841040
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4fdffd6d24ce18c38c45a086ea0f6376241d21d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000885"
---
# <a name="samples-for-the-oracle-ebs-adapter"></a>適用於 Oracle EBS 配接器範例
範例[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]會分類為：  
  
- [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 範例  
  
- WCF 服務模型範例  
  
- WCF 通道模型範例  
  
- Microsoft Office SharePoint Server 的範例  
  
  這些範例位於[BizTalk Adapter Pack 2010: Oracle E-business Suite 配接器範例](https://www.microsoft.com/download/details.aspx?id=6464)。 建立介面資料表、 同時執行的程式、 資料表和封裝範例中所使用的 SQL 指令碼會包含項目。 
  
> [!NOTE]
> [!INCLUDE[files-need-updated](../../includes/files-need-updated.md)]
  
 下列清單描述的範例。 
  
## <a name="biztalk-server-samples"></a>BizTalk Server 範例  
  
|    範例目錄名稱     |                                                                                                                                                                        描述                                                                                                                                                                        |
|------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     InterfaceTableInsert     |                                                                                   示範如何將記錄插入介面資料表中使用 Oracle E-business Suite [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。                                                                                    |
|      ConcurrentProgram       |                                                                                       示範如何叫用並行程式中使用 Oracle E-business Suite [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。                                                                                       |
|          RequestSet          |                                                                                          示範如何叫用要求中使用 Oracle E-business Suite 設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。                                                                                           |
|      MsgContextProperty      | 示範如何使用訊息內容屬性所公開[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]來設定要在 Oracle E-business Suite 使用成品上執行作業的應用程式內容[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 |
| OracleEBS_CompositeOperation |                                                                                      示範如何執行複合作業中使用 Oracle E-business Suite [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。                                                                                       |
|   OracleNotifyIncremental    |                                                                                   示範如何使用 Oracle 時，收到 「 增量 」 的查詢通知訊息[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。                                                                                    |
| PollingUsingSelectStatement  |                                                                            示範如何設定使用 SELECT 陳述式在有輪詢查詢，並接收結果使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。                                                                            |
|    PollingUsingStoredProc    |                                                                            示範如何設定使用預存程序在有輪詢查詢，並接收結果使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。                                                                            |
  
## <a name="wcf-service-model-sasamplesmples"></a>WCF 服務模型 Sasamplesmples  
  
|範例目錄名稱|描述|  
|---------------------------|-----------------|  
|ConcProgram_ServiceModel|示範如何叫用使用配接器的 Oracle E-business Suite 中的並行程式。|  
|ExecuteReader|示範如何叫用 ExecuteReader 作業上使用配接器的 Oracle E-business Suite。|  
|Interface_Table_Ops|示範如何使用配接器的 Oracle E-business Suite 在介面資料表上執行作業。|  
|LargeDataTypes_ServiceModel|示範如何使用配接器的 Oracle E-business Suite 中執行具有大型資料類型之資料行的資料表上的作業。|  
|Notification_ServiceModel|示範如何從 Oracle E-business Suite 使用配接器後面的資料庫會收到通知。|  
|SelectPolling_ServiceModel|示範如何使用輪詢 Oracle E-business Suite 使用配接器中的介面資料表的 SELECT 陳述式。|  
|StoredProcPolling_ServiceModel|示範如何使用預存程序來輪詢使用配接器的 Oracle E-business Suite 中的資料表。|  
  
## <a name="wcf-channel-model-samples"></a>WCF 通道模型範例  
  
|範例目錄名稱|描述|  
|---------------------------|-----------------|  
|InsertOperation|示範如何執行插入作業在介面資料表上使用配接器的 Oracle E-business Suite 中。|  
|SelectPolling_ChannelModel|示範如何使用輪詢 Oracle E-business Suite 使用配接器中的介面資料表的 SELECT 陳述式。|  
  
## <a name="microsoft-office-sharepoint-server-samples"></a>Microsoft Office SharePoint Server 的範例  
  
| 範例目錄名稱 |                                                                                                                                                                  描述                                                                                                                                                                   |
|-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      MOSS_Sample      | 示範如何使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]Oracle E-business Suite 的成品，從建立 Windows Communication Foundation (WCF) 服務，然後使用 在 Microsoft Office SharePoint Server 使用商務資料清單 Web 組件中顯示資料的 WCF 服務。 |
  
## <a name="see-also"></a>另請參閱  
[開發您的 Oracle E-business Suite 應用程式](../../adapters-and-accelerators/adapter-oracle-ebs/develop-your-oracle-e-business-suite-applications.md)