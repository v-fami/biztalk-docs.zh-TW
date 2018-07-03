---
title: 無效的元件元素分隔符號 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 738a1107-86e6-4475-a61d-ed1d9ab7e5d2
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 927a33124fdb624df79d3b2f99b07f61345289e9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997551"
---
# <a name="invalid-component-element-separator"></a>無效的元件元素分隔符號
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                   X12Ta1InvalidComponentElementSeparatorDescription\                   |
|  訊息文字   |                          無效的元件元素分隔符號                           |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為交換中的元件分隔符號的值不是限制為 ASCII 字元集中的字元。 在 X12 中，區段結束字元是 [ISA16] 欄位。 在 EDIFACT 中，區段結束字元是 UNA1 欄位。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確認區段結束字元 (ISA16 欄位中的 X12 交換 或 UNA1 欄位，EDIFACT 交換中的) 僅限於 ASCII 字元集中的字元。 重新傳送交換。