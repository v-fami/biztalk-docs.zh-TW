---
title: 功能群組控制編號已達到合作對象的 X12 可接受的最高上限 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a920a66c-1e38-4f4a-8113-cbad01940839
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 527f6709d48124f7ffcc0823bdc5ff84e92256ff
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978399"
---
# <a name="max-limit-of-acceptable-x12-functional-group-control-number-has-reached-for-party"></a>功能群組控制編號已達到合作對象的 X12 可接受的最高上限
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                              |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                      |
| 產品版本 |                                                                  [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                  |
|    事件識別碼     |                                                                                              -                                                                                               |
|  事件來源   |                                                    [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                    |
|    元件    |                                                                                          將 EDI 引擎                                                                                          |
|  符號名稱  |                                                                                    PartyX12GsNumberError                                                                                     |
|  訊息文字   | 功能群組控制編號已達到合作對象的 X12 可接受的最高上限{0}。 瀏覽至合作對象中接收者角色畫面中，在夥伴協議 管理員中的欄位 GS 6，重設計數器 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示傳送管線無法處理外寄 X12 交換，因為合作對象設定中指定的 GS06 欄位中的群組控制編號大於允許的最大值。 群組控制編號的字元數目上限是 9。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，重設群組控制編號，如下所示：  
  
1.  在 EDI 屬性 對話方塊中的 合作對象的交換解析，開啟 GS 和 ST 區段定義頁面做為交換接收者的合作對象。  
  
2.  按一下 GS06 欄位相關聯的編輯欄位。  
  
3.  使欄位具有九個或更少的數字，則您可以設為新的值的群組控制編號。