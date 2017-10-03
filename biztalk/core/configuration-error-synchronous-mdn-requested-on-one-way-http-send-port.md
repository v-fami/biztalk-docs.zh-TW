---
title: "組態錯誤。 對單向 HTTP 要求同步 MDN 的傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bd38eb3-321f-4738-b35e-390f4f54673e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a0a240593aa21b102c401a2a6886ea24baa42c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuration-error-synchronous-mdn-requested-on-one-way-http-send-port"></a>組態錯誤。 對單向 HTTP 要求同步 MDN 的傳送埠
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|-|  
|訊息文字|組態錯誤。 對單向 HTTP 傳送埠要求同步 MDN。|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 無法接收同步 MDN 傳送 AS2 訊息，因為 HTTP 傳送埠傳送 AS2 訊息是單向連接埠之後。 雙向請求-回應傳送埠，才能由連接埠傳送 AS2 訊息的回應傳回同步 MDN 的程序。 在此情況下，因為在做為 AS2 訊息接收者的合作對象設定中，勾選 [要求 MDN] 屬性，並清除 [要求非同步 MDN] 屬性，必須是以同步方式傳回 MDN。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，變更傳送埠傳送 AS2 訊息靜態請求-回應傳送埠，而非單向傳送埠。 設定接收管線的請求-回應傳送埠的非 EDI 交換的是 AS2EdiReceive EDI 交換或 AS2Receive。