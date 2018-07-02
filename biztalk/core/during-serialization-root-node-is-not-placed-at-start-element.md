---
title: 在序列化期間根節點不位於開始項目 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9ea4aa6f-0f9c-4b7b-b7f6-24a5ce954048
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce91021f966ac1179a5137373df09fe7f3c4cece
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978415"
---
# <a name="during-serialization-root-node-is-not-placed-at-start-element"></a>在序列化期間根節點不位於開始項目
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                                           -                                            |
|  訊息文字   |             在序列化期間根節點不位於開始項目              |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為不會啟動交易集，這是以 ST 或 UNH 標頭。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定每個交易集的交換中的啟動與 ST 區段 （適用於 X12 交換） 或 UNH 區段 （適用於 EDIFACT 交換），並再重新提交交換。