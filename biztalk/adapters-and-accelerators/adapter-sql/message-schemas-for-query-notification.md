---
title: "使用 SQL 配接器在 BizTalk 中查詢通知訊息結構描述 |Microsoft 文件"
description: "使用 SQL 配接器從 SQL Server 資料庫中 BizTalk 接收查詢通知"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5183655-64d4-4767-a923-0a575e3708cd
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c78c817470bd8acd41f44204653c41e9012d154
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-query-notification"></a>查詢通知的訊息結構描述
[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]呈現從 SQL Server 資料庫接收查詢通知的通知作業。  
  
 設定繫結屬性設定通知作業[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 如需通知相關的繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for SQL Server 配接器繫結屬性](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md)。 您設定**NotificationStatement**內容繫結至指定的 SQL 陳述式 (SELECT 或 EXEC\<預存程序 >) 的查詢通知。 此查詢的結果集傳回做為強型別資料通知作業中的程式碼時。  
  
## <a name="message-structure-for-the-notification-operation"></a>通知作業的訊息結構  
 下表顯示通知作業的 XML 訊息結構。  

**作業**:`Notification`

**XML 訊息**:  
```xml
<?xml version="1.0" encoding="utf-8" ?>
  <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification">
    <Info>Value</Info>
    <Source>Value</Source>
    <Type>Value</Type>
 </Notification>
```

**描述**： 這是 SQL Server 傳送到配接器用戶端的傳入的訊息。 在訊息：

- `<Info>`標記指出通知的原因。 例如，這個標記中的 「 插入 」 值表示已在一或多個通知的陳述式中參考的資料表中插入資料。
- `<Source>`標記表示的通知來源。 例如，這個標記中的 「 資料 」 值表示參考的物件中的資料的變更。 同樣地，這個標記中的 「 物件 」 值表示參考物件的變更。
- `<Type>`標記表示的資料變更類型。 查詢通知訊息有兩種類型： 變更和訂閱。 A 的 「 變更 」 中的值`<Type>`標記表示查詢的結果已變更，而在 「 訂閱 」 值`<Type>`標記表示的訂用帳戶要求失敗。

  
## <a name="message-action-for-the-notification-operation"></a>通知作業的訊息動作  
 通知作業的訊息動作是 「 通知 」。  
  