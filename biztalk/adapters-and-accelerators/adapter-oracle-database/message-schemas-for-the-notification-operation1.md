---
title: 針對通知 Operation1 訊息結構描述 |Microsoft Docs
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
ms.openlocfilehash: cdf371335a1242423c4497f186fa5764f5b2fb2f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991687"
---
# <a name="message-schemas-for-the-notification-operation"></a>通知作業的訊息結構描述
[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]呈現通知作業，若要從 Oracle 資料庫接收資料庫變更通知。  
  
 您藉由設定繫結屬性設定通知作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。 如需有關的通知相關的繫結屬性的詳細資訊，請參閱[了解 Oracle 資料庫配接器繫結屬性](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md)。 您設定**NotificationStatement**繫結屬性，以指定的查詢通知的 SELECT 陳述式。  
  
## <a name="message-structure-for-the-notification-operation"></a>通知作業的訊息結構  
 下表顯示通知作業的 XML 訊息結構。  
  
|作業|XML 訊息|描述|  
|---------------|-----------------|-----------------|  
|通知|`<?xml version="1.0" encoding="utf-8" ?>  <Notification xmlns="http://Microsoft.LobServices.OracleDB/2007/03/Notification">    <Info>Value</Info>    <Source>Value</Source>    <Type>Value</Type> </Notification>`|這是 Oracle 資料庫傳送到配接器用戶端的傳入的訊息。 在 訊息：<br /><br /> -`<Info>`標記指出通知的原因。 比方說，這個標記中的"insert"值會指出已在一或多個通知的陳述式中參考的資料表中插入資料。<br /><br /> -`<Source>`標記表示通知的來源。 比方說，「 資料 」 值，這個標記中的表示受參考的物件中的資料的變更。 同樣地，這個標記中的 「 物件 」 值會指出參考的物件中的變更。<br /><br /> -`<Type>`標記表示資料變更的類型。 「 更新 」 中的值，例如`<Type>`標記代表查詢的結果，已更新。|  
  
## <a name="message-action-for-the-notification-operation"></a>通知作業的訊息動作  
 通知作業的訊息動作是 「<http://Microsoft.LobServices.OracleDB/2007/03/Notification”>。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Adapter for Oracle Database 的訊息和訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)