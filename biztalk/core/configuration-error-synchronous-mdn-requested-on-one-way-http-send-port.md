---
title: 組態錯誤。 對單向 HTTP 要求同步 MDN 的傳送埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3bd38eb3-321f-4738-b35e-390f4f54673e
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0118789db8e45b096f3852aef3487416d388961d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014143"
---
# <a name="configuration-error-synchronous-mdn-requested-on-one-way-http-send-port"></a>組態錯誤。 對單向 HTTP 要求同步 MDN 的傳送埠
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                                           -                                            |
|  訊息文字   |       組態錯誤。 對單向 HTTP 傳送埠要求同步 MDN。        |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 無法在之後因為 HTTP 傳送埠傳送 AS2 訊息是單向連接埠傳送 AS2 訊息接收同步 MDN。 雙向請求-回應傳送埠，才能使用連接埠傳送 AS2 訊息的回應傳回同步 MDN 的程序。 在此情況下，因為在做為 AS2 訊息接收者的合作對象設定中，勾選 [要求 MDN] 屬性，並清除 [要求非同步 MDN] 屬性，必須是以同步方式傳回 MDN。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，變更傳送埠傳送 AS2 訊息為 靜態請求-回應傳送埠，而不是單向傳送埠。 請求-回應的接收管線設定為 AS2EdiReceive EDI 交換或 AS2Receive，適用於非 EDI 交換的傳送埠。