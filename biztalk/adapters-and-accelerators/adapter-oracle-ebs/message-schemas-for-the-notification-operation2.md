---
title: 訊息結構描述的通知 Operation2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dddab2ef-94db-46c8-95c1-57517681e8dd
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8c004e83ada00b41013c2a22c5e48f29bb39ffd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22215942"
---
# <a name="message-schemas-for-the-notification-operation"></a>通知作業的訊息結構描述
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]介面上接收從 Oracle E-business Suite 中的基礎資料庫的資料庫變更通知的通知作業。  
  
 設定繫結屬性設定通知作業[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。 如需通知相關的繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Oracle E-business Suite 繫結屬性](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md)。 您設定**NotificationStatement**內容繫結至指定的查詢通知的 SELECT 陳述式。  
  
## <a name="message-structure-for-the-notification-operation"></a>通知作業的訊息結構  
 下表顯示通知作業的 XML 訊息結構。  
  
|作業|XML 訊息|Description|  
|---------------|-----------------|-----------------|  
|通知|`<?xml version="1.0" encoding="utf-8" ?>  <Notification xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Notification">    <Info>Value</Info>    <Source>Value</Source>    <Type>Value</Type> </Notification>`|這是 Oracle E-business Suite 傳送到配接器用戶端的傳入的訊息。 在訊息：<br /><br /> -`<Info>`標記指出通知的原因。 例如，這個標記中的 「 插入 」 值表示已在一或多個通知的陳述式中參考的資料表中插入資料。<br /><br /> -`<Source>`標記表示的通知來源。 例如，這個標記中的 「 資料 」 值表示參考的物件中的資料的變更。 同樣地，這個標記中的 「 物件 」 值表示參考物件的變更。<br /><br /> -`<Type>`標記表示的資料變更類型。 例如，「 更新 」 值中`<Type>`標記代表查詢的結果已更新。|  
  
## <a name="message-action-for-the-notification-operation"></a>通知作業的訊息動作  
 通知作業的訊息動作是 「 通知 」。  
  
## <a name="see-also"></a>另請參閱  
 [訊息和訊息結構描述，BizTalk adapter for Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)