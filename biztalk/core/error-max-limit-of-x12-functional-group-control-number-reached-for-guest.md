---
title: 可接受的 X12 功能群組控制編號已達到 Guest 設定的最高上限 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 05cba774-fa35-4694-aa34-d7151f8cd75c
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3210fb773b7093c2e28f98e0cf1aa223e1a63936
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241630"
---
# <a name="max-limit-of-acceptable-x12-functional-group-control-number-has-reached-for-guest-settings"></a>可接受的 X12 功能群組控制編號已達到 Guest 設定的最高上限
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|GlobalEdifactUnhNumberError|  
|訊息文字|可接受的 X12 功能群組控制編號已達到 Guest 設定的最高上限。 瀏覽到全域組態接收者角色畫面，欄位 GS 6 在夥伴協議管理員 中，重設計數器|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示傳送管線無法處理外寄 X12 交換，因為全域設定中指定的 GS06 欄位中的群組控制編號大於允許的最大值。 群組控制編號的字元數目上限是 9。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，重設群組控制編號，如下所示：  
  
1.  在 EDI 全域屬性 對話方塊中，開啟 GS 和 ST 區段定義頁面。  
  
2.  按一下 GS06 欄位相關聯的編輯欄位。  
  
3.  設定為新值，此欄位有九個或更少的數字的群組控制編號。