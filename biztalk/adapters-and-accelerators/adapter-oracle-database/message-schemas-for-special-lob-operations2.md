---
title: 訊息結構描述的特殊 LOB Operations2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- LOB data types, message structure of
- LOB data types, message actions for
ms.assetid: 031989d5-3209-41ab-8836-a40539781e74
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 203ffc81b6dc85fcaf7b80ff097bbeb001b747cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214590"
---
# <a name="message-schemas-for-special-lob-operations"></a>特殊 LOB 作業的訊息結構描述
ReadLOB 和 UpdateLOB 作業便會顯示資料表和檢視表包含 LOB 資料行。這是用來儲存 Oracle 大型物件 (LOB) 資料的資料行。 這些作業可讓您讀取或寫入 base64Binary 編碼資料的資料流的形式的 LOB 資料。 它們是在單一資料列的 LOB 資料的單一資料行上運作。  
  
 ReadLOB 和 UpdateLOB 作業和支援的 Oracle LOB 資料類型的概觀，請參閱[資料表和檢視表包含 Oracle 資料庫中的 LOB 資料的作業](../../adapters-and-accelerators/adapter-oracle-database/operations-on-tables-and-views-that-contain-lob-data-in-oracle-database.md)。  
  
## <a name="message-structure-of-lob-data-type-operations"></a>LOB 資料型別作業的訊息結構  
 下表顯示 ReadLOB 和 UpdateLOB 作業要求和回應訊息的結構。 作業的目標資料表中的訊息動作指定，而且也會出現在 目標命名空間。  
  
|作業|XML 訊息|Description|  
|---------------|-----------------|-----------------|  
|ReadLOB|`<ReadLOB xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   <LOB_COLUMN>[COL_NAME]</LOB_COLUMN>   <FILTER>[WHERE_clause]</LOB_COLUMN> </ReadLOB>`|中的 LOB 資料<br /><br /> -LOB_COLUMN 項目，識別資料行，<br /><br /> -資料列符合 where 子句篩選條件的項目中指定<br /><br /> 會傳回。<br /><br /> Where 子句應符合的單一資料列。 如果有一個以上相符的資料列，則會傳回第一個相符的資料列中的 LOB 資料。<br /><br /> **重要**ReadLOB 作業設計來支援 WCF 服務模型中的 LOB 資料的輸入資料流。 您應該使用資料表的 Select 作業讀取 WCF 通道模型中的 LOB 資料或[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]方案。|  
|ReadLOB 回應|`<ReadLOBResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   <ReadLOBResult>     [LOB_DATA]   </ReadLOBResult> </ReadLOBResponse>`|LOB 資料是 base64Binary 編碼資料的資料流的形式傳回。<br /><br /> **重要**配接器所傳回的 WSDL 不符合實際 ReadLOB 回應訊息的配接器使用的結構描述。|  
|UpdateLOB|`<UpdateLOB xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   <LOB_COLUMN>[COL_NAME]</LOB_COLUMN>   <FILTER>[WHERE_clause]</LOB_COLUMN>   <Stream>[LOB_DATA]</Stream> </UpdateLOB>`|中的 LOB 資料<br /><br /> -LOB_COLUMN 項目，識別資料行，<br /><br /> -資料列符合 where 子句篩選條件的項目中指定<br /><br /> 以 base64Binary 編碼資料流中的更新。<br /><br /> Where 子句應符合的單一資料列。 如果有一個以上相符的資料列，會擲回例外狀況。<br /><br /> **請注意**UpdateLOB 作業會取代所有指定的資料行和資料列中的資料。|  
|UpdateLOB 回應|`<UpdateLOBResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]"> </UpdateLOBResponse>`|會傳回空白回應。|  
  
 [版本] = 訊息版本字串。例如，"http://Microsoft.LobServices/OracleDB/2007/03。 」  
  
 [SCHEMA] = 集合的 Oracle 成品。例如，SCOTT。  
  
 [TABLE_NAME] = 資料表，其中包含目標的 LOB 資料行;例如，EMP。  
  
 [COL_NAME] = 目標的 LOB 資料行; 的名稱例如，LOB_FIELD。  
  
 [WHERE_clause] = Oracle 資料庫的 SELECT 陳述式 WHERE 子句，比對單一資料列。例如，識別碼 = 1。  
  
 [LOB_DATA] = base64Binary 類型中的 LOB 資料行資料。  
  
> [!IMPORTANT]
>  ReadLOB 和 UpdateLOB 作業檢視上的訊息結構的相同資料表上會有不同之處在於此作業的命名空間指定的檢視，而不是資料表： `<ReadLOB xmlns ="[VERSION]/[SCHEMA]/``View``/[VIEW_NAME]">`。  
  
## <a name="message-actions-for-lob-data-type-operations"></a>LOB 資料型別作業的訊息動作  
 下表顯示所使用的訊息動作[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]ReadLOB 和 UpdateLOB 作業在資料表上。 [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]來判斷作業的目標資料表中使用的訊息動作中指定的資料表名稱。  
  
|作業|動作|範例|  
|---------------|------------|-------------|  
|ReadLOB|`[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/ReadLOB`|`http:/Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER/ReadLOB`|  
|ReadLOB 回應|`[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/ReadLOB/response`|`http:/Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER/ReadLOB/response`|  
|UpdateLOB|`[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/UpdateLOB`|`http:/Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER/UpdateLOB`|  
|UpdateLOB 回應|`[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/UpdateLOB/response`|`http:/Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER/UpdateLOB/response`|  
  
 [版本] = 訊息版本字串。例如，"http://Microsoft.LobServices.OracleDB/2007/03。 」  
  
 [SCHEMA] = 集合的 Oracle 成品。例如，SCOTT。  
  
 [TABLE_NAME] = 資料表，其中包含目標的 LOB 資料行;例如，客戶。 (SCOTT。CUSTOMER 資料表中會安裝所包含的範例中的 SQL 指令碼）。  
  
> [!IMPORTANT]
>  ReadLOB 和 UpdateLOB 檢視作業的訊息動作是所使用的資料表，類似，不同之處在於動作的作業指定的檢視，而不是資料表： `[VERSION]/[SCHEMA]/View/[VIEW_NAME]/ReadLOB`。  
  
## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)