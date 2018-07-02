---
title: 跨欄位驗證規則違規 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d606a80-9046-4572-9cfb-a3434ed8073e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d590fc318e7d833a067f4275986bef88da10364
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976655"
---
# <a name="cross-field-validation-rule-violated"></a>違反欄位交互驗證規則
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                                           -                                            |
|  訊息文字   |                          違反欄位交互驗證規則                          |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線或傳送管線中的 X12 交換無法通過欄位交互驗證。 這代表 X12ConditionDesignator_Check 旗標已設為 [是]，且交換中至少有一個元素無法通過依首碼 "X12ConditionDesignatorX" 識別的規則。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列其中一項：  
  
-   找出無法通過欄位交互驗證規則的資料元素。 請連絡交換的寄件者，並指出建立交換時，必須遵循的規則。  
  
-   開啟結構描述的交換，並設定為 [否] 的驗證失敗的資料元素的 X12ConditionDesignator_Check 旗標。