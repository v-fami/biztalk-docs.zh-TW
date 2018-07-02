---
title: 無法序列化批次訊息，因為沒有任何相關聯的合作對象傳送埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d697ff9c-a6d1-4a3c-9ec3-4cd496f7eec2
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84915c3544ed6e4222dd7fb035808617b51e5280
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969559"
---
# <a name="batch-message-cannot-be-serialized-as-there-is-no-party-associated-with-send-port"></a>無法序列化批次訊息，因為沒有合作對象與傳送埠相關聯
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                            |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                             |
| 產品版本 |                                         [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                         |
|    事件識別碼     |                                                                     -                                                                      |
|  事件來源   |                           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                           |
|    元件    |                                                              批次引擎                                                               |
|  符號名稱  |                                             BatchMessageSerializationFailureDueToMissingParty                                              |
|  訊息文字   | 批次訊息無法序列化，因為沒有任何相關聯的合作對象傳送埠{0}。 請確定合作對象相關聯的連接埠 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，傳送管線無法處理保留的交換因為無法判斷訊息應傳送至合作對象。 因為未設定 DestinationPartyName 內容屬性，它無法判斷合作對象。 如此一來，傳送管線無法判斷信封設定。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，讓訊息通過傳送管線，並再決定 DestinationPartyName 內容屬性的訊息。 驗證合作對象存在。 如果不是，建立合作對象，然後再重新傳送訊息。