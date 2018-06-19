---
title: 訊息結構描述的輪詢 Operations2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- POLLINGSTMT operation, message actions for
- POLLINGSTMT operation, message structure for
ms.assetid: b82edcc2-9437-4c7b-ba2b-7b966fff3f15
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: beb28e7b769c16f1798023adb8b30c3e636a3407
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214598"
---
# <a name="message-schemas-for-the-polling-operations"></a>輪詢作業的訊息結構描述
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現輪詢根據 Oracle 資料庫上的目標物件與相關的各種輸入的作業。 若要輪詢資料表和檢視表，而每個預存程序、 函數和已封裝的程序和函式公開為輸入進行輪詢作業，會顯示單一 POLLINGSTMT 作業。  
  
 您可以指定**PollingId**中連接來限定 POLLINGSTMT 作業的命名空間 URI 的查詢字串參數。 設定此參數只限定的命名空間 POLLINGSTMT 作業。它不會變更訊息動作。 如需 Oracle 資料庫配接器連線 URI 的詳細資訊，請參閱[建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。  
  
 設定繫結屬性設定輪詢作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 如需有關這些繫結屬性的詳細資訊，請參閱[閱讀有關 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。 您設定**PollingStatement**內容繫結至指定的 SQL 陳述式、 預存程序、 函式或在封裝中的輪詢查詢的程序。 此查詢的結果集傳回做為資料輪詢作業中的程式碼時。  
  
## <a name="message-structure-for-the-polling-operations"></a>輪詢作業的訊息結構  
 下表顯示各種輪詢作業的 XML 訊息結構。  
  
|作業|目標物件|XML 訊息|Description|  
|---------------|-------------------|-----------------|-----------------|  
|POLLINGSTMT|-資料表<br /><br /> 對檢視|`<?xml version="1.0" encoding="utf-8" ?>  <POLLINGSTMT xmlns="[VERSION]/POLLINGSTMT[POLLING_ID]">   <POLLINGSTMTRECORD>     <POLLINGSTMTRECORD>       <FIELD1_NAME>val1</FIELD1_NAME>        <FIELD2_NAME>val2</FIELD2_NAME>       …     </POLLINGSTMTRECORD>      …    </POLLINGSTMTRECORD> </POLLINGSTMT>`|結果集包含在 POLLINGSTMTRECORD 類型的結構取決於中繼資料配接器提供諸如 SQL SELECT 查詢。<br /><br /> POLLINGSTMT 作業的命名空間是由 PollingId 參數，在 連線 URI 中所決定。|  
|[CustomPollingOperation]|-預存程序<br /><br /> 函式<br /><br /> -套件|**預存程序**<br /><br /> `<?xml version="1.0" encoding="utf-8" ?>  <[CustomPollingOperation] xmlns="[Version]/[SCHEMA]/PollingProcedure">    <[CustomPollingOperation]Result>      <PRM1>[Value]</PRM1>      <PRM2>[Value]</PRM2>      …    </[CustomPollingOperation]Result> </[CustomPollingOperation]>`<br /><br /> **函數**<br /><br /> `<?xml version="1.0" encoding="utf-8" ?> <[CustomPollingOperation] xmlns="[Version]/[Schema]/PollingFunction">    <[CustomPollingOperation]Result>      <COL1>[Value]</COL1]>      <COL2>[Value]</COL2>      …    </[CustomPollingOperation]Result> </[CustomPollingOperation]>`<br /><br /> **套件**<br /><br /> `<?xml version="1.0" encoding="utf-8" ?>  <[CustomPollingOperation] xmlns="[Version]/[Schema]/PollingPackage/[PACKAGE_NAME]/">    <[CustomPollingOperation]Result>[Value]</[CustomPollingOperation]Result> </[CustomPollingOperation]>`|輪詢作業中的結果集的結構取決於目標物件中的項目中的資料類型。|  
  
 [版本] = http://Microsoft.LobServices.OracleDB/2007/03。  
  
 [CustomPollingOperation] = 與預存程序、 函數或封裝的程序或函式名稱公開為輸入的輪詢作業相同。  
  
 [Schema] = Oracle 結構描述名稱。 例如，SCOTT。  
  
## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)