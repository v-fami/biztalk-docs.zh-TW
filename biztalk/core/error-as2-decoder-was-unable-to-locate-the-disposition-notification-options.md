---
title: "AS2 解碼器找不到配置通知選項 HTTP 標頭 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6de4b9a6-17b2-4455-9dbd-a6bb69fac1d5
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 966860c7f2b7b47187b861ed6b81fb14a4753872
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-as2-decoder-was-unable-to-locate-the-disposition-notification-options-http-header"></a>AS2 解碼器找不到配置通知選項 HTTP 標頭
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|AS2 引擎|  
|符號名稱|AS2DecoderMissingDispositionNotificationOptionsHTTPHeaderError|  
|訊息文字|AS2 解碼器找不到產生 MDN 所需的 Disposition-Notification-Options HTTP 標頭。|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法產生 MDN 因為內送 AS2 訊息不含配置通知選項標頭，指出是否必須簽署 MDN 的 MIC 和必須使用演算法。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，讓傳送者的 AS2 訊息的訊息中包含配置通知選項標頭，然後再重新傳送訊息。