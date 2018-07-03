---
title: 根據指定的分隔符號集，有效的數字找不到 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 08887f7d-8256-4de3-8db9-b890451521ff
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6fc117a9c9d08d664f397557ab08f9c6f2e7dc7c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989223"
---
# <a name="based-on-the-specified-delimiter-set-no-valid-digit-could-be-found"></a>根據指定的分隔符號集，有效的數字找不到
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                        |
|-----------------|--------------------------------------------------------------------------------------------------------|
|  產品名稱   |           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]           |
| 產品版本 |                       [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                       |
|    事件識別碼     |                                                   -                                                    |
|  事件來源   |         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI         |
|    元件    |                                               將 EDI 引擎                                               |
|  符號名稱  |                                                   -                                                    |
|  訊息文字   | 根據指定的分隔符號集，無法找到有效的數字。 請使用另一個分隔符號集。 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 傳送管線找不到有效的數字時產生外寄交換，因為欄位的外寄交換中使用的數字分隔符號字元相同。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，變更 EDI 傳送管線用來建立一則訊息，以便任何分隔符號字元會與數字欄位的外寄交換中使用相同的分隔符號值。 執行下列其中之一：  
  
-   對於傳送給已解析合作對象的 X12 交換，針對做為交換接收者的合作對象在 [ISA 區段定義] 頁面變更分隔符號設定。  
  
-   對於傳送給未解析之合作對象的 X12 交換，在 [ISA 區段定義] 全域屬性頁面中變更分隔符號設定。  
  
-   正在傳送給已解析合作對象的 EDIFACT 交換，變更做為交換接收者的合作對象 [UNA 區段定義] 頁面中的分隔符號設定。  
  
-   正在傳送給未解析的合作對象的 EDIFACT 交換，變更 [UNA 區段定義] 全域屬性頁面中的分隔符號設定。