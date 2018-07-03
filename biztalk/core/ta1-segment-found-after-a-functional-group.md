---
title: 功能群組後發現 TA1 區段 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ee3d090a-0916-4a0e-82dc-2c9af9f97683
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87613f9482c5c54e99544b96ddd0d1cfc94d3c85
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018136"
---
# <a name="ta1-segment-found-after-a-functional-group"></a>功能群組後發現 TA1 區段
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                              TA1FoundAfterFunctionalGroup                              |
|  訊息文字   |     在功能群組後發現 TA1 區段。 因此，即將拒絕訊息      |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送通知因為通知所包含功能的群組]，然後按一下 [TA1 區段。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，有的 TA1 通知確保，交換不包含 TA1 區段中之前, 的功能群組，然後再重新傳送通知的寄件者。