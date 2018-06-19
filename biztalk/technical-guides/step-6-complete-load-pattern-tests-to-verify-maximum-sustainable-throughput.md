---
title: 步驟 6： 執行常數負載模式測試，以確認最大持續輸送量 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dd790354-be9f-4278-bd15-493eac8970c9
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b6bfc0b9670366ab2f38046fcdc5497234b51ba5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22302094"
---
# <a name="step-6-perform-constant-load-pattern-tests-to-verify-maximum-sustainable-throughput"></a>步驟 6： 執行常數負載模式測試，以確認最大持續輸送量
負載測試使用 Visual Studio 2010 的 BizTalk Server 方案時，應該執行的常數負載模式測試，一旦中所述，決定大約最大持續輸送量 (MST) 解決方案的[步驟 5： 執行步驟載入模式測試，以判斷最大持續輸送量](../technical-guides/step-5-complete-step-load-tests-to-determine-maximum-sustainable-throughput.md)。 這應該確認 MST 事實上持續一段時間，以建立基準負載測試向前移到評估的任何效能調整套用至 BizTalk Server 應用程式或環境。  
  
## <a name="create-and-run-a-constant-load-pattern-test"></a>建立和執行常數負載模式測試  
 最簡單的方式來建立使用相同的測試混合、 計數器集合和使用步驟負載模式測試的計數器集合對應的常數負載模式測試僅儲存步驟負載模式測試 」 BTS_Messaging_Step.loadtest"為"BTS_Messaging_Constant.loadtest"，然後讓某些變更為"BTS_Messaging_Constant.loadtest"。 遵循下列步驟來建立以常數負載模式也就是測試根據現有的步驟負載模式測試：  
  
1.  如果不是已開啟，請開啟 BTS_Messaging_Step.loadtest。  
  
2.  按一下**檔案**選取**存 LoadTests\BTS_Messaging_Step.loadtest**。  
  
3.  在**另存新檔**對話方塊中，旁邊**檔案名稱**，輸入 C:\Projects\LoadTest\BTSLoad\LoadTests\BTS_Messaging_Constant.loadtest，然後按一下**儲存**。  
  
4.  在負載測試編輯器，重新命名情節**BTS_Messaging_Step**至**BTS_Messaging_Constant**。 情節名稱會顯示正下方**案例**資料夾。  
  
5.  保留的值**測試混合**和**網路混合**保持不變，但是按一下以選取**步驟負載模式**。  
  
6.  以滑鼠右鍵按一下**步驟負載模式**選取**屬性**。  
  
7.  在**屬性**下**負載模式**旁按一下下拉式清單**模式**和變更的模式**步驟**至**常數**。  
  
8.  在**屬性**下**參數**，變更的值**常數使用者計數**稍微小於的使用者數目的值至步驟負載模式測試已成為現象 (也就是值**BizTalk:Messaging\Documents 每秒接收到**持續超過的值開始**BizTalk:Messaging\Documents processed/Sec**和值**biztalk: Message Box: General Counters\Spool Size**開始增加 unbounded)。  
  
9. 在下**回合設定**資料夾中，以滑鼠右鍵按一下**執行 Setting1 [Active]** 選取**屬性**。  
  
10. 向下的捲動清單屬性，以**計時**區段，並輸入的值**執行持續期間**至少 10 分鐘 (00: 10:00)，並驗證的值**取樣率**已設定為 5 秒 (00: 00:05)。  
  
11. 啟動負載測試的測試名稱 (例如 BTS_Messaging_Constant) 上按一下滑鼠右鍵，然後按一下**執行測試**功能表選項。