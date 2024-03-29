---
title: 輪詢和 SQL 配接器在 BizTalk TypedPolling 作業的訊息結構描述 |Microsoft 文件
description: 輪詢和 TypedPolling 訊息 SQL 配接器在 BizTalk 配接器組件 (BAP) 中使用的結構
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1e900307-2c9c-493b-81c9-67af3e143eeb
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0cd6a281bfca73e74f23ce25bb9fa08761a07789
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25964860"
---
# <a name="message-schemas-for-the-polling-and-typedpolling-operations"></a>輪詢和 TypedPolling 作業的訊息結構描述
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]輪詢和 TypedPolling 介面的輸入來輪詢查詢的結果集傳回至配接器的用戶端操作。  
  
 設定繫結屬性設定輪詢和 TypedPolling 作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 如需有關這些繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。 您設定**PollingStatement**內容繫結至指定的 SQL 陳述式 (SELECT 或 EXEC\<預存程序\>) 的輪詢查詢。 為您的程式碼在輪詢作業中，資料和強型別 TypedPolling 作業中的資料，則會傳回此查詢的結果集。 結果集的結構取決於中繼資料配接器可呈現為指定的查詢。  
  
## <a name="polling-message-structure"></a>輪詢訊息結構 
  
**作業**:`Polling`

**XML 訊息**:  
```xml
<?xml version="1.0" encoding="utf-8" ?>
  <Polling xmlns="http://schemas.microsoft.com/Sql/2008/05/Polling">
    <PolledData>
      <DataSet xmlns="http://schemas.datacontract.org/2004/07/System.Data">
        <any>[Value]</any>
        <any>[Value]</any>
        …
        </DataSet>
    </PolledData>
 </Polling>
```

**描述**: SQL Server 傳送到配接器用戶端的傳入的訊息。  


## <a name="typedpolling-message-structure"></a>TypedPolling 訊息結構 

**作業**:`TypedPolling`

**XML 訊息**:  
```xml
<?xml version="1.0" encoding="utf-8" ?>
  <TypedPollingResultSet xmlns="http://schemas.microsoft.com/Sql/2008/05/TypedPolling">
    <COLUMN1>[Value]</Column1>
    <COLUMN2>[Value]</Column2>
    …
  </TypedPollingResultSet>
```

**描述**： 強型別輸入的訊息到配接器用戶端傳送的 SQL Server。
  
## <a name="message-action-for-the-polling-and-typedpolling-operations"></a>輪詢和 TypedPolling 作業的訊息動作  
 訊息動作:  
  
-   輪詢作業正在 「 輪詢 」。  
  
-   TypedPolling 作業為"TypedPolling。 」  
  
