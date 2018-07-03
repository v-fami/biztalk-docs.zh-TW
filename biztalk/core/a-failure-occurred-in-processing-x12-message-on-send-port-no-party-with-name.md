---
title: 失敗發生在處理 X12 訊息在傳送埠： 沒有合作對象名稱 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af059a04-3b7c-48e2-a3bf-48ad62deb139
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 817840dae0db408d4f78732f5d470605a05edf71
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014791"
---
# <a name="a-failure-occurred-in-processing-x12-message-on-send-port-no-party-with-name"></a>處理傳送埠上的 X12 訊息時發生失敗：沒有名稱的合作對象
## <a name="details"></a>詳細資料  
  
|                 |                                                                                               |
|-----------------|-----------------------------------------------------------------------------------------------|
|  產品名稱   |      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]       |
| 產品版本 |                  [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                   |
|    事件識別碼     |                                               -                                               |
|  事件來源   |    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI     |
|    元件    |                                          將 EDI 引擎                                           |
|  符號名稱  |                                               -                                               |
|  訊息文字   | 失敗發生在處理 X12 訊息傳送埠上的{0}。 沒有合作對象有名稱{1}。 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 無法解析合作對象的 X12 交換，因為 BizTalk Server 無法比對與合作對象相關聯的傳送埠訂閱該交換的傳送埠。 會發生這種情況是如果沒有 [DestinationPartyName] 屬性中，或傳送者辨識符號、 寄件者識別碼、 接收者辨識符號和接收者識別項屬性，會升級，因此無法用於傳送端合作對象解析。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定傳送埠訂閱該交換的比對與合作對象關聯的傳送埠。