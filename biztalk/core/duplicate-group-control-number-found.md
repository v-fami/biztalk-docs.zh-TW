---
title: "重複的群組控制編號找到 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1badc033-42fd-4992-ad36-b53047ba7817
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9165414d1a9a743c77c28b087730745d3dcc4c0b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="duplicate-group-control-number-found"></a>找到重複的群組控制編號
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|-|  
|訊息文字|找到重複的群組控制編號|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 接收管線無法不處理內送交換因為它的相同交換、 群組或交易集控制編號和先前已接收交換。 只要適當的重複控制編號檢查已啟用，這會導致失敗。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列其中一項：  
  
-   請確定傳送至 BizTalk Server 的交換，並沒有相同的群組控制編號和之前的交換，如果對應的重複控制編號檢查已啟用。  
  
-   停用重複群組控制編號檢查。 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下適當的合作對象，然後開啟 [EDIFACT 交換處理屬性] 或 [X12 交換處理屬性] 對話方塊的合作對象做為交換傳送者。 若要停用檢查 EDIFACT 交換，清除 檢查重複項目 UNG5 （群組控制編號） 交換屬性中。 若要停用檢查的 X12 交換，請清除核取的重複 GS6 （群組控制編號） 交換屬性中。