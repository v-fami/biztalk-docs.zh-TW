---
title: 處理傳送埠上的 Edifact 訊息時發生錯誤： 沒有合作對象名稱 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 678baacb-1f21-4081-b788-ef346c3598ca
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 823b0d1315c82676017f0cc5e1bfa45b9ed9e342
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979335"
---
# <a name="a-failure-occurred-in-processing-edifact-message-on-send-port-no-party-with-name"></a>處理傳送埠上的 Edifact 訊息時發生錯誤： 沒有合作對象名稱
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                   |
|-----------------|---------------------------------------------------------------------------------------------------|
|  產品名稱   |        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]         |
| 產品版本 |                    [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                     |
|    事件識別碼     |                                                 -                                                 |
|  事件來源   |                                        BizTalk Server EDI                                         |
|    元件    |                                            將 EDI 引擎                                             |
|  符號名稱  |                                                 -                                                 |
|  訊息文字   | 處理傳送埠上的 Edifact 訊息時發生失敗{0}。 沒有合作對象有名稱{1}。 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 無法解析合作對象的 EDIFACT 交換，因為 BizTalk Server 無法比對與合作對象相關聯的傳送埠訂閱該交換的傳送埠。 會發生這種情況是如果沒有 [DestinationPartyName] 屬性，也不傳送者辨識符號和識別項以及接收者辨識符號和識別項屬性會升級，因此無法用於傳送端合作對象解析。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定傳送埠訂閱該交換的比對與合作對象關聯的傳送埠。