---
title: "分隔符號不是唯一的欄位與元件分隔符號相同 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cba15b30-b07d-4caa-8c43-6b4d8c4ca81c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f803612a905f0be196afcfc0b43af23501ccdf0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="delimiters-are-not-unique-field-and-component-separator-are-the-same"></a>分隔符號不是唯一、 欄位和元件分隔符號相同
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|-|  
|訊息文字|分隔符號不是唯一、 欄位和元件分隔符號相同|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，EDI 傳送管線無法處理外寄交換因為資料元素和元件分隔符號相同的值。 在 X12 交換，資料元素分隔符號是 ISA 區段的第四個字元的位置中的字元和元件分隔符號是 ISA16 欄位中的字元。 在 EDIFACT 交換中，資料元素分隔符號是 UNA2 欄位中的字元和元件分隔符號是 UNA1 欄位中的字元。 兩個具有相同值的分隔符號可能 （但會導致錯誤狀況） 中保留的批次的案例中，或交換是透過傳遞傳輸接收，然後挑選向上為 MessageBox 中 XML 檔案傳送埠。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，變更值的其中一個資料元素或元件分隔符號，然後再重新提交交換。