---
title: 分隔符號不是唯一，欄位與元件分隔符號相同 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cba15b30-b07d-4caa-8c43-6b4d8c4ca81c
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd6439bd307ec922b9dbdd5761f61e9e3ad557f0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979415"
---
# <a name="delimiters-are-not-unique-field-and-component-separator-are-the-same"></a>分隔符號不是唯一，欄位及元件分隔符號相同
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       將 EDI 引擎                                       |
|  符號名稱  |                                           -                                            |
|  訊息文字   |         分隔符號不是唯一，欄位及元件分隔符號相同          |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，EDI 傳送管線無法處理外寄交換因為資料元素和元件分隔符號相同的值。 在 X12 中資料元素分隔符號的交換，在 ISA 區段的第四個字元位置的字元而元件分隔符號是 ISA16 欄位中的字元。 在 EDIFACT 交換中，資料元素分隔符號 UNA2 欄位中的字元而元件分隔符號是 UNA1 欄位中的字元。 具有相同值的兩個分隔符號可能會發生 （但會導致錯誤狀況） 在保留批次案例中，或如果交換是透過通過傳輸接收，然後挑選最多的傳送埠即 MessageBox 中的 XML 檔案。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，變更此值可能是資料元素或元件分隔符號，而然後再重新送出交換。