---
title: "是無效的配置通知選項 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a1b807a8-eec9-45a5-83cc-075c91b4bc9e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72221c98dfcac42f735f63a1ce01a7c26bc45387
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="disposition-notification-option-is-invalid"></a>Disposition-Notification-Option 無效
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|AS2 引擎|  
|符號名稱|-|  
|訊息文字|配置通知選項的值:"{0}"無效。 {1}|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，由於 Disposition-Notification-Option 標頭無效，因此 AS2 接收管線無法產生 MDN。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確認 AS2 訊息中的 Disposition-Notification-Option 標頭符合 RFC 4130「使用 HTTP 以 MIME 為基礎的安全點對點商務資料交換 Applicability Statement 2 (AS2)」描述的語法。 請確認簽署回條通訊協定標頭設為 「 選用 」 或 「 pcks7-簽章 」，且簽章-回條-MICAlg 標頭，設定為 「 選用 」，"MD5"或"SHA1"。 （這兩個這些標頭包含配置通知選項標頭中。）