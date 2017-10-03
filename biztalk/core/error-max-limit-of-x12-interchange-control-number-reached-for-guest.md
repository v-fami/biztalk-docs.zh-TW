---
title: "可接受的 X12 交換控制編號已達到 Guest 設定的最高上限 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9737053d-6065-4c88-8dfa-5f69b48e0e82
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c72fc565367477d9dbd09f3c0d4c4f9d6ab686a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-x12-interchange-control-number-has-reached-for-guest-settings"></a>可接受的 X12 交換控制編號已達到 Guest 設定的最高上限
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|GlobalX12IsaNumberError|  
|訊息文字|可接受的 X12 交換控制編號已達到 Guest 設定的最高上限。 瀏覽到全域組態接收者角色畫面，欄位 ISA 13 在夥伴協議管理員 中，重設計數器|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示傳送管線無法處理外寄 X12 交換，因為全域設定中指定 [ISA13] 欄位中的交換控制編號大於允許的最大值。 交換控制編號的字元數目上限是 9。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，重設交換控制編號，如下所示：  
  
1.  在 EDI 全域屬性 對話方塊中，開啟 ISA 區段定義頁面。  
  
2.  按一下 [ISA13] 欄位相關聯的編輯欄位。  
  
3.  設定為新值，欄位具有可接受的數量的數字的交換控制編號。