---
title: 可接受的 X12 交換控制編號已達到合作對象的最高上限 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: adc49089-3c7b-4ce2-9fbc-68e582c3a822
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fba803260af4879e4e2a286c0f7864af7ccf2747
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262478"
---
# <a name="max-limit-of-acceptable-x12-interchange-control-number-has-reached-for-party"></a>可接受的 X12 交換控制編號已達到合作對象的最大限制
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|PartyX12IsaNumberError|  
|訊息文字|可接受的 X12 交換控制編號已達到合作對象 {0} 的最高上限。 瀏覽至合作對象中接收者角色畫面，欄位 ISA 13 在夥伴協議管理員 中，重設計數器|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示傳送管線無法處理外寄 X12 交換，因為合作對象設定中指定 [ISA13] 欄位中的交換控制編號大於允許的最大值。 交換控制編號的字元數目上限是 9。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，重設交換控制編號，如下所示：  
  
1.  在 EDI 屬性 對話方塊中的 合作對象的交換解析，開啟做為交換接收者的合作對象的 ISA 區段定義 頁面。  
  
2.  按一下 [ISA13] 欄位相關聯的編輯欄位。  
  
3.  設定為新值，欄位具有可接受的數量的數字的交換控制編號。