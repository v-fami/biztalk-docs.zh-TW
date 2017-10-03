---
title: "小於允許的最小的次數執行迴圈重複 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0be21d1d-86da-456b-83e6-c91f1dc9fb48
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00d9b38712d8b8336daa9357bd20eb34148691b9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="loop-repeats-less-than-the-minimum-allowed-number-of-times"></a>迴圈重複次數少於允許次數下限
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12SeLoopRepeatsLessTimesDescription|  
|訊息文字|迴圈重複次數少於允許次數下限|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為交換包含迴圈，重複次數少於所需的訊息結構描述的最少次數。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定迴圈重複交換中至少指定訊息結構描述中迴圈的 minOccurs 屬性中的次數，並再重新傳送交換。