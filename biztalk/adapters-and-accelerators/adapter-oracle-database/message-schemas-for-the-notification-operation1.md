---
title: 訊息結構描述的通知 Operation1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f98d76d0-6084-4de7-b6ff-124202ca92ab
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd0d7513a0a439d34d5bfb4722fec2b9025e676b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214094"
---
# <a name="message-schemas-for-the-notification-operation"></a>通知作業的訊息結構描述
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]介面上接收從 Oracle 資料庫的資料庫變更通知的通知作業。  
  
 設定繫結屬性設定通知作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 如需通知相關的繫結屬性的詳細資訊，請參閱[閱讀有關 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。 您設定**NotificationStatement**內容繫結至指定的查詢通知的 SELECT 陳述式。  
  
## <a name="message-structure-for-the-notification-operation"></a>通知作業的訊息結構  
 下表顯示通知作業的 XML 訊息結構。  
  
|作業|XML 訊息|Description|  
|---------------|-----------------|-----------------|  
|通知|`<?xml version="1.0" encoding="utf-8" ?>  <Notification xmlns="http://Microsoft.LobServices.OracleDB/2007/03/Notification">    <Info>Value</Info>    <Source>Value</Source>    <Type>Value</Type> </Notification>`|這是 Oracle 資料庫傳送到配接器用戶端的傳入的訊息。 在訊息：<br /><br /> -`<Info>`標記指出通知的原因。 例如，這個標記中的 「 插入 」 值表示已在一或多個通知的陳述式中參考的資料表中插入資料。<br /><br /> -`<Source>`標記表示的通知來源。 例如，這個標記中的 「 資料 」 值表示參考的物件中的資料的變更。 同樣地，這個標記中的 「 物件 」 值表示參考物件的變更。<br /><br /> -`<Type>`標記表示的資料變更類型。 例如，「 更新 」 值中`<Type>`標記代表查詢的結果已更新。|  
  
## <a name="message-action-for-the-notification-operation"></a>通知作業的訊息動作  
 通知作業的訊息動作是 「 http://Microsoft.LobServices.OracleDB/2007/03/Notification"。  
  
## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for Oracle 資料庫](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)