---
title: 步驟 9： 測試 EDI 解決方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a7a44e0f-496c-462f-bf03-1c2f842d13b6
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6e308ae230ea2d78ff03ed02a81310c38fbcabc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278646"
---
# <a name="step-9-test-the-edi-solution"></a>步驟 9： 測試 EDI 解決方案
![步驟 9 / 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-9of9.gif "Step_9of9")  
  
 在這個主題，您會測試輸入處理，並檢視處理資訊的 [EDI-交換狀態報告]。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="testing-the-solution"></a>測試解決方案  
  
1.  在 Windows 檔案總管中，移至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations。 複製**SamplePO.txt**檔案。  
  
2.  貼上**SamplePO.txt**檔案[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\Scenario A\fromTHEM 資料夾。  
  
3.  移至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\Scenario A\toOrderSystem 資料夾。 確認該資料夾包含輸出 txt 檔案。  
  
4.  開啟 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\Scenario A\toOrderSystem 中的輸出檔以及 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations 中的 SamplePO.txt 輸入檔。 確認輸出訊息中的資料對應至原始資料**SamplePO.txt**檔案。  
  
    > [!NOTE]
    >  開啟 Visual Studio 中的 Inbound4010850_to_OrderFile.btm 檔案及檢查對應，即可驗證輸出檔中的資料是否已從輸入檔中的資料轉換過來。  
  
5.  移至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\Scenario A\toTHEM_997 資料夾。 確認該資料夾包含輸出 997 通知 txt 檔案，且檔案中的 ST01 資料元素為 "997"。  
  
6.  在主控台樹狀目錄中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下  **BizTalk 群組**。 在右窗格的底部，按一下  **EDI 交換和相互關聯的 ACK 狀態**。  
  
7.  查詢運算式中的運算子變更**狀態**欄位設為**等於**並變更**值**欄位**狀態**欄位設為**所有**。 刪除**交換日期時間欄位**（選取資料列並按下 DELETE 鍵面板上）。  
  
8.  按一下**執行查詢**。  
  
9. 確認兩則訊息都顯示在狀態報告中，一則的接收方向是從 THEM (Fabrikam) 至 US (OrderSystem) (850 訊息)，另一則的傳送方向是從 US (OrderSystem) 至 THEM (Fabrikam) (997 通知)。  
  
10. 按兩下從 THEM 至 US 的訊息。 在**交換狀態和通知詳細資料**對話方塊方塊中，確認該交換的詳細資料會顯示在右窗格中。  
  
11. 按一下**功能通知**。 確認右窗格中是否顯示通知的報告詳細資料。  
  
12. 關閉 [交換狀態和通知詳細資料] 對話方塊。  
  
13. 在**交換/通知狀態**] 窗格中，以滑鼠右鍵按一下從 THEM 至 US 的訊息，然後按一下 [**交易集詳細資料**。 以滑鼠右鍵按一下中的項目**查詢結果** 窗格中，然後再按一下**檢視交易集內容**。 確認交易集資料會顯示在**訊息詳細資料** 對話方塊。 在 Windows 檔案總管中，開啟 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\ProcessEDI_TestLocations 中的 SamplePO.txt 檔案。 確認交易集顯示在**訊息詳細資料**對話方塊等同於可在輸入訊息中，不含交換和群組標頭和結尾。  
  
## <a name="next-steps"></a>後續步驟  
 您已經完成了「EDI 介面開發人員教學課程」。  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 2: EDI 介面開發人員教學課程](../core/tutorial-2-edi-interface-developer-tutorial.md)   
 [步驟 1： 準備 EDI 介面開發人員教學課程](../core/step-1-prepare-for-the-edi-interface-developer-tutorial.md)