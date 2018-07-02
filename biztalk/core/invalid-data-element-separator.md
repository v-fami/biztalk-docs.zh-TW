---
title: 無效的資料元素分隔符號 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76c50a8b-274f-4f4a-9826-4f6f8123e9d1
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3fbc355c6a89bd69364200dcd20ca257fc9dc54
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972591"
---
# <a name="invalid-data-element-separator"></a>無效的資料元素分隔符號
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                      X12Ta1InvalidDataElementSeparatorDescription                      |
|  訊息文字   |                             無效的資料元素分隔符號                             |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，由於內送交換中的區段結束字元值有 ASCII 字元集之外的字元，因此接收管線無法處理該交換。 在 X12 中，區段結束字元定義為 ISA 區段中的第四個字元。 在 EDIFACT 中，區段結束字元是 UNA2 欄位。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確認區段結束字元 (x12 ISA 區段的第四個字元交換] 或 [EDIFACT 交換中的 [UNA2] 欄位) 限制為 ASCII 字元集中的字元。 重新傳送交換。