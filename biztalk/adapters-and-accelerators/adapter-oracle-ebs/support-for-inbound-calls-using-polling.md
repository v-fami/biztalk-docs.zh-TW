---
title: 使用輪詢進行傳入呼叫支援 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ae02a93a-808f-4774-a2c4-efdf39a4d49a
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 868e56730f21235e3f73f6ab91a463ea4589bafd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984663"
---
# <a name="support-for-inbound-calls-using-polling"></a>使用輪詢進行傳入呼叫支援
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]可讓用戶端程式，以接收來自 Oracle E-business Suite，Oracle E-business Suite 中的資料變更的通知訊息。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]接收 「 以輪詢為基礎 」 的訊息，其中指定的 SQL 陳述式、 預存程序、 函數或程序在封裝中，而執行配接器的支援擷取資料，並提供給用戶端的結果，定期的時間。  

> [!NOTE]
>  您也可以設定應用程式內容中輪詢作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 它，才能設定輪詢作業的應用程式內容，如果在介面資料表或介面檢視上執行作業。 應用程式內容，以及如何將它設定的相關資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  

 典型的輪詢作業使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]牽涉到下列：  

1. 配接器用戶端必須指定`Polling`中輸入作業**InboundOperationType**繫結屬性。 這個繫結屬性的預設值是**輪詢**。  

2. 配接器用戶端必須指定的 SELECT 陳述式**PolledDataAvailableStatement**繫結屬性，以判斷是否有資料可供輪詢。 第一個傳回的結果集上執行此陳述式的第一個資料列的第一個資料行包含整數值，如果有可用日期進行輪詢。  

3. 配接器用戶端必須指定輪詢間隔**PollingInterval**繫結屬性來定義以秒為單位的陳述式中指定的間隔**PolledDataAvailableStatement**執行繫結屬性。 在每個輪詢間隔結束時，輪詢的資料提供陳述式會執行，而且會傳回結果集。  

4. 配接器用戶端必須指定 SELECT 陳述式或預存程序**PollingInput**繫結屬性。 如果您想要輪詢的資料表或檢視，您必須指定這個繫結屬性的 SELECT 陳述式。 如果您想要使用預存程序進行輪詢，您必須指定這個繫結屬性的整個要求訊息。  

    中的陳述式**PollingInput**繫結屬性只有當沒有資料可供輪詢，取決於執行**PolledDataAvailableStatement**步驟 2 中的繫結屬性。  

5. 配接器用戶端必須指定在輪詢作業動作**PollingAction**繫結屬性。 輪詢動作特定的作業是從 取用配接器服務增益集所使用的作業產生的中繼資料來決定。  

6. 配接器用戶端可以使用**PollWhileDataFound**忽略輪詢間隔，並持續輪詢資料，當有可用的屬性繫結。  

   > [!IMPORTANT]
   >  如果您設定的值**PollWhileDataFound**繫結屬性設為 True，配接器用戶端持續輪詢資料從 Oracle 和程序中開啟及關閉連線到 Oracle 資料庫在迴圈中。 因為 ODP.NET 開啟連線的速率大於連線正在關閉，連線會耗盡段時間之後，並擲回例外狀況。 因應之道，請確定值**UseOracleConnectionPool**設定為 True，和適當的值所述**IncrPoolSize**繫結屬性，即可控制連線的數目可以開啟配接器用戶端。  

7. 配接器用戶端可以指定後輪詢陳述式，Oracle 的 PL/SQL 區塊中，如**PostPollStatement**繫結屬性。 這個繫結屬性中指定的陳述式中指定的陳述式之後執行**PollingInput**屬性繫結會執行。  

   > [!NOTE]
   >  執行陳述式中指定的配接器**PollingInput**並**PostPollStatement**繫結在交易中的屬性。 如需中的交易[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱 <<c2> [ 配接器處理交易的運作方式？](https://msdn.microsoft.com/library/dd788428.aspx)。  

   配接器會隱藏來自 Oracle E-business Suite 的任何空白的輪詢回應。  

   下圖提供資訊中的輪詢工作流程[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 說明的輪詢工作流程的兩個案例：  

8. 當 windows 7 **PollWhileDataFound**設為"False"（預設值）。  

9. 當 windows 7 **PollWhileDataFound**設為"True"。  

   ![輪詢案例&#40;PollWhileDataFound&#61;False&#41;](../../adapters-and-accelerators/adapter-oracle-ebs/media/e5f00f4c-cc76-4e8b-9991-b4471f9d4865.gif "e5f00f4c-cc76-4e8b-9991-b4471f9d4865") ![輪詢案例&#40;PollWhileDataFound &#61; True&#41; ] (../../adapters-and-accelerators/adapter-oracle-ebs/media/ebecf64c-a770-4525-9c75-62fdb71e1fb1.gif "ebecf64c-a770-4525-9c75-62fdb71e1fb1")  

## <a name="differences-between-polling-and-notification"></a>輪詢和通知之間的差異  
 輪詢和通知都是這兩個輸入的作業，而且有關 Oracle 資料庫中的資料變更通知配接器用戶端，但下表列出兩者之間的一些差異。 下列差異將協助您決定的作業，視您的需求而定：  


|                                                                                                                                                                                                                                                      輪詢                                                                                                                                                                                                                                                      |                                                                                                                              通知                                                                                                                               |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                                                                                                                                   支援的所有 Oracle 資料庫版本都支援輪詢[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。                                                                                                                                                                    |                                                                                               10.2 和更新版本的 Oracle 資料庫版本只支援通知。                                                                                               |
| 您可以設定輪詢間隔，以檢查適用於定期輪詢資料，或立即一樣，當有可用的資料。 **提示：** 輪詢可讓您更佳的輸送量的資料變更會持續發生，並不想為每項變更並發生時收到通知。 相反地，您可以指定之後，您想要的上次變更通知，因為發生錯誤的所有變更的通知的輪詢間隔。 |                                                                                                          資料變更通知是一律在瞬間完成。                                                                                                          |
|                                                                                                                                         輪詢配接器所起始。 若要驗證是否可供輪詢，資料，並藉由執行輪詢陳述式，如果某些資料已可供輪詢起始輪詢 SQL 陳述式執行配接器。                                                                                                                                         | 通知是由 Oracle 資料庫啟動。 只在配接器發出的通知陳述式會指示要起始通知，萬一沒有陳述式的結果集變更的資料庫。 通知是 Oracle 資料庫的功能。 |
|                                                                                                                                                                                                                 您可以使用輪詢陳述式來讀取或更新的 Oracle 資料庫中的資料。                                                                                                                                                                                                                  |                                                                                             您可以使用 notification 陳述式只讀取 Oracle 資料庫中的資料。                                                                                             |
|                                                                                                                                                                                                                            輪詢會告知您已變更的實際資料。                                                                                                                                                                                                                            |                                                                                   通知只會通知的類型變更的資料，例如 Insert、 Update 和 Delete。                                                                                    |

 如需詳細資訊：  

- 繫結屬性與輪詢，請參閱[了解 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  

- 接收以輪詢為基礎的訊息，使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱 <<c2> [ 輪詢 Oracle E-business Suite 使用 BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-biztalk-server.md)。  

## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)