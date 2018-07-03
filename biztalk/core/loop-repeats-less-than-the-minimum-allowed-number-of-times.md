---
title: 小於允許的最小的數次迴圈重複項目 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0be21d1d-86da-456b-83e6-c91f1dc9fb48
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5457110830a2e38e592ff58e7da672373a139d1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012311"
---
# <a name="loop-repeats-less-than-the-minimum-allowed-number-of-times"></a>迴圈重複次數少於允許次數下限
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                          X12SeLoopRepeatsLessTimesDescription                          |
|  訊息文字   |               迴圈重複次數少於允許次數下限               |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為交換包含迴圈重複次數比訊息結構描述所需的最小次數。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定迴圈重複的交換中至少指定如訊息結構描述中迴圈的 minOccurs 屬性中的次數，然後重新傳送交換。