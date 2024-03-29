---
title: Edifact 交換應該包含 UNA 或 UNB 作為第一個區段 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc43fd17-31d0-48df-93cd-524b40034764
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ee9d5100c8378b5ee411673c4c185dcf5def365
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37017832"
---
# <a name="edifact-interchange-should-have-contained-una-or-unb-as-the-first-segment"></a>Edifact 交換應該包含 UNA 或 UNB 作為第一個區段
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                  |
|-----------------|--------------------------------------------------------------------------------------------------|
|  產品名稱   |        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]        |
| 產品版本 |                    [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                    |
|    事件識別碼     |                                                -                                                 |
|  事件來源   |      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI      |
|    元件    |                                            將 EDI 引擎                                            |
|  符號名稱  |                                                -                                                 |
|  訊息文字   | Edifact 交換應該包含 UNA 或 UNB 作為第一個區段。 改為{0}找不到 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 接收管線無法處理內送 EDIFACT 交換，因為第一個區段不是 UNA 或 UNB 區段。 UNA 區段是選擇性的。UNB 區段是必要的。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，確定交換的寄件者包含 UNA 或 UNB 區段的第一個區段的交換，然後重新傳送交換。