---
title: 重複的控制編號 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 331ad173-29b3-427c-8104-60d80c580a5a
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e83f685242f4c69e6a142f3abb027017657611f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239606"
---
# <a name="duplicate-control-number"></a>重複的控制編號
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|-|  
|訊息文字|重複的控制編號|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 接收管線無法不處理內送交換因為它的相同交換、 群組或交易集控制編號和先前已接收交換。 只要適當的重複控制編號檢查已啟用，這會導致失敗。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列其中一項：  
  
-   如果對應的重複控制編號檢查已啟用，請確認傳送至 BizTalk Server 之交換的交換、群組或交易集控制編號和之前的交換不同。  
  
-   停用重複控制編號檢查。 在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下適當的合作對象，然後開啟 [EDIFACT 交換處理屬性] 或 [X12 交換處理屬性] 對話方塊的合作對象做為交換傳送者。 若要停用 EDIFACT 交換的檢查，請清除 [檢查重複項目 UNB5 (交換控制編號)]、[檢查交換中的重複項目 UNG5 (群組控制編號)] 或 [檢查群組中的重複項目 UNH1 (交易集參考編號)] 屬性。 若要停用 X12 交換的檢查，請清除 [檢查重複項目 ISA13 (交換控制編號)]、[檢查交換中的重複項目 GS6 (群組控制編號)] 或 [檢查群組中的重複項目 ST2 (交易集控制編號)] 屬性。