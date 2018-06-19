---
title: 支援使用輪詢進行傳入呼叫 |Microsoft 文件
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
ms.openlocfilehash: a8533ce2829fec956819b311fd6b8f99479f40d6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217398"
---
# <a name="support-for-inbound-calls-using-polling"></a>使用輪詢進行傳入呼叫時的支援
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]可讓用戶端程式來接收通知他們 Oracle E-business Suite 中的資料變更的 Oracle E-business Suite 中的訊息。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]接收 「 輪詢基礎 」 的訊息，其中指定的 SQL 陳述式、 預存程序、 函數或程序在封裝中，而執行配接器支援擷取資料，並提供用戶端定期的結果時間。  
  
> [!NOTE]
>  您也可以設定應用程式內容中輪詢作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 它，才能設定輪詢作業的應用程式內容，如果介面資料表或檢視介面上執行作業。 應用程式內容，以及如何設定它的相關資訊，請參閱[設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)。  
  
 使用一般輪詢作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]牽涉到下列：  
  
1.  配接器用戶端必須指定`Polling`為中的輸入作業**InboundOperationType**繫結屬性。 這個繫結屬性的預設值是**輪詢**。  
  
2.  配接器用戶端必須指定 SELECT 陳述式**PolledDataAvailableStatement**繫結屬性來判斷是否有資料可用來輪詢。 第一個傳回的結果集上執行此陳述式的第一個資料列的第一個資料行包含正整數值，如果有可用日期進行輪詢。  
  
3.  配接器用戶端必須指定輪詢間隔**PollingInterval**內容繫結至定義陳述式中指定的秒數間隔**PolledDataAvailableStatement**執行繫結屬性。 在每個輪詢間隔結束時，輪詢的資料可用陳述式會執行，而且會傳回結果集。  
  
4.  配接器用戶端必須指定 SELECT 陳述式或預存程序**PollingInput**繫結屬性。 如果您想要輪詢的資料表或檢視，您必須指定這個繫結屬性的 SELECT 陳述式。 如果您想要輪詢使用預存程序，您必須指定這個繫結屬性的整個要求訊息。  
  
     中的陳述式**PollingInput**繫結屬性不會執行沒有資料可用於輪詢，取決於**PolledDataAvailableStatement**步驟 2 中的繫結屬性。  
  
5.  配接器用戶端必須指定動作中的輪詢作業**PollingAction**繫結屬性。 針對特定作業的輪詢動作會從使用配接器服務增益集所使用的作業產生的中繼資料來決定。  
  
6.  配接器用戶端可以使用**PollWhileDataFound**內容繫結至忽略的輪詢間隔，並持續輪詢資料，以及可用時。  
  
    > [!IMPORTANT]
    >  如果您設定的值**PollWhileDataFound**繫結屬性設定為 True，配接器用戶端持續輪詢資料從 Oracle 和程序中開啟和關閉連接到 Oracle 資料庫在迴圈中。 因為 ODP.NET 開啟連線的速度大於關閉的連線，連線一段時間後可能會耗盡，並擲回例外狀況。 為因應措施，請確定值**UseOracleConnectionPool**設為 True，和適當的值中有提及**IncrPoolSize**內容繫結至控制連接數目您可以開啟配接器用戶端。  
  
7.  配接器用戶端可以指定後輪詢陳述式，Oracle 的 PL/SQL 區塊，如**PostPollStatement**繫結屬性。 這個繫結屬性中指定陳述式中指定的陳述式之後**PollingInput**執行繫結屬性。  
  
    > [!NOTE]
    >  執行陳述式中指定的配接器**PollingInput**和**PostPollStatement**繫結在交易中的屬性。 如需中的交易[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]，請參閱[配接器處理交易的運作方式？](https://msdn.microsoft.com/library/dd788428.aspx)。  
  
 配接器會抑制來自 Oracle E-business Suite 的任何空白輪詢回應。  
  
 下圖提供資訊中的輪詢工作流程[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 輪詢工作流程的兩個案例說明：  
  
1.  當值**PollWhileDataFound**設為"False"（預設值）。  
  
2.  當值**PollWhileDataFound**設為"True"。  
  
 ![輪詢案例 &#40;PollWhileDataFound &#61;False &#41;] (../../adapters-and-accelerators/adapter-oracle-ebs/media/e5f00f4c-cc76-4e8b-9991-b4471f9d4865.gif "e5f00f4c-cc76-4e8b-9991-b4471f9d4865") ![輪詢案例 &#40;PollWhileDataFound &#61;True &#41;] (../../adapters-and-accelerators/adapter-oracle-ebs/media/ebecf64c-a770-4525-9c75-62fdb71e1fb1.gif "ebecf64c-a770-4525-9c75-62fdb71e1fb1")  
  
## <a name="differences-between-polling-and-notification"></a>通知輪詢之間的差異  
 雖然輪詢通知都是這兩個輸入的作業，且配接器用戶端通知有關 Oracle 資料庫中的資料變更下, 表列出這兩者之間的一些差異。 下列差異，可協助您決定在針對作業，視您的需求而定：  
  
|輪詢|通知|  
|-------------|------------------|  
|支援的所有 Oracle 資料庫版本都支援輪詢[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。|10.2 和更新版本的 Oracle 資料庫版本才支援通知。|  
|您可以設定輪詢間隔，以檢查適用於定期輪詢資料，或立即一樣，當有可用的資料。 **提示：** 輪詢可讓您更佳的輸送量持續發生資料變更並不想為每項變更，並發生時加以通知。 相反地，您可以指定您要在其後發生是因為最後一個變更通知的所有變更的通知輪詢間隔。|資料變更通知是一律在瞬間完成。|  
|輪詢配接器所起始。 若要驗證是否資料適用於輪詢，並以起始輪詢執行輪詢陳述式，如果某些資料可用於輪詢 SQL 陳述式執行配接器。|通知是由 Oracle 資料庫啟動。 只在配接器發出的通知陳述式會指示資料庫在陳述式的結果集變更的情況下起始通知。 通知是 Oracle 資料庫的功能。|  
|您可以使用輪詢陳述式來讀取或更新的 Oracle 資料庫中的資料。|您可以使用通知陳述式只讀取 Oracle 資料庫中的資料。|  
|輪詢會通知您有關已變更的實際資料。|通知會告知中插入，例如資料的變更類型的相關更新和刪除。|  
  
 如需詳細資訊：  
  
-   繫結屬性與輪詢，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。  
  
-   輪詢基礎使用接收訊息[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，請參閱[輪詢 Oracle E-business Suite 使用 BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-biztalk-server.md)。  
  
## <a name="see-also"></a>另請參閱  
 [哪些作業可以是執行使用配接器？](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)