---
title: 不是唯一分隔符號 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1c37cc55-8923-4124-9004-91ee5093df9c
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d724533fb89d3f4d43654aadaf43094adb80e06
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966741"
---
# <a name="delimiters-are-not-unique"></a>不是唯一分隔符號
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                                           -                                            |
|  訊息文字   |                               不是唯一分隔符號                                |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，EDI 傳送管線無法處理外寄交換因為兩個或多個分隔符號在交換中，識別與用來區隔的交換、 facet 都相同。 分隔符號都會列在 ISA 區段的 X12 交換和 EDIFACT 的 UNA 區段中交換。 具有相同值的兩個或多個分隔符號可能會發生在保留批次案例中，或如果交換是透過通過傳輸接收，然後挑選最多的傳送埠即 MessageBox 中的 XML 檔案。 這個錯誤狀況會導致失敗之交換的處理。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，找出在交換中使用的分隔符號有相同的值，並變更其中一個分隔符號的值。