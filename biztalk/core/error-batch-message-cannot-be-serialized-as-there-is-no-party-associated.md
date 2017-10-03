---
title: "無法序列化批次訊息，因為沒有任何相關聯的合作對象傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d697ff9c-a6d1-4a3c-9ec3-4cd496f7eec2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b20d10a2c7b584eccc7d1fb57e5132a4ac0d608
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="batch-message-cannot-be-serialized-as-there-is-no-party-associated-with-send-port"></a>無法序列化批次訊息，因為沒有任何傳送埠相關聯的合作對象
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|批次處理引擎|  
|符號名稱|BatchMessageSerializationFailureDueToMissingParty|  
|訊息文字|無法序列化批次訊息，因為沒有任何相關聯的合作對象傳送埠 {0}。 請確定合作對象連接埠相關聯|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，傳送管線無法處理保留的交換因為無法判定應該要傳送訊息的合作對象。 因為沒有設定 DestinationPartyName 內容屬性，它無法判斷合作對象。 如此一來，傳送管線無法判斷信封設定。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，讓訊息通過傳送管線，並接著判斷訊息的 DestinationPartyName 內容屬性。 驗證合作對象存在。 如果沒有，請建立合作對象，，然後再重新傳送訊息。