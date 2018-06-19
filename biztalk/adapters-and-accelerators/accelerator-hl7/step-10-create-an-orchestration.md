---
title: 步驟 10： 建立協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, creating
- creating, orchestrations
- message enrichment tutorial, orchestrations
ms.assetid: 10f5cf3d-4a34-4c80-89d1-c390552cfc09
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cfc554a6f3c94a077b34ae79a36b8e484eadcd5d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206566"
---
# <a name="step-10-create-an-orchestration"></a>步驟 10： 建立協調流程
在此步驟中，您可以使用 協調流程設計師建立協調流程代表商務程序來擷取完整填入 ADT_A04 訊息的其他病患詳細資料。 使用協調流程設計師 」，您會選取協調流程圖形來表示此商務程序的動作。 在更新版本的練習中，您可以提供其他資訊以設定圖形，讓它們可以正常運作。  
  
> [!NOTE]
>  下列步驟中建立的協調流程只適用於本教學課程的內容中。 為了讓正常運作的協調流程，它需要的組件參考、 對應和其他成品，您建立同時使用本教學課程。  
  
### <a name="to-create-an-orchestration"></a>建立協調流程  
  
1.  在 方案總管 中，以滑鼠右鍵按一下**BTAHL7 專案**，指向 **新增**，然後按一下 **新項目**。  
  
2.  在**加入新項目**對話方塊中，於**類別**] 窗格中，按一下 [**協調流程檔案**。  
  
3.  在**範本**] 窗格中，按一下 [ **BizTalk 協調流程**。  
  
4.  在**名稱**欄位中，輸入**Doorbell Orchestration.odx** (請注意單字之間沒有空格**Doorbell**和**協調流程**) 作為協調流程的名稱，然後按一下**新增**建立新的協調流程檔案。  
  
5.  在**檢視**功能表上，按一下 **工具箱**。  
  
6.  在**工具箱**窗格拖曳**接收**圖形至 [設計] 檢視介面並將它放在標示為區域**從 [工具箱] 拖曳圖形**。  
  
7.  在 屬性 視窗 （在右下方的螢幕） 上，按一下 **名稱**屬性，並輸入**DoorbellReceive**做為名稱**接收**圖形，然後再按  **輸入**。  
  
8.  在 [屬性] 視窗中，變更**Activate**屬性**True**。  
  
9. 拖曳**轉換**圖形從 [工具箱]，並將它放在正下方**DoorbellReceive**圖形。  
  
10. （在右下方的螢幕） 的 [屬性] 視窗中按一下**名稱**屬性來變更名稱**轉換**圖形至**DoorbellTransform**，然後按下**輸入**。  
  
11. 在**工具箱**窗格拖曳**訊息指派**圖形至 [設計] 檢視介面並將它放在正下方的區域上 **[constructmessage_1]** 圖形。  
  
12. 在 協調流程設計檢視介面中，按一下  **MessageAssignment_1**圖形，然後在**屬性** 窗格中，按一下 **名稱**，輸入新名稱**DoorbellFinalTransform**，然後按下**Enter**。  
  
13. 拖曳**傳送**圖形從 [工具箱]，並放在正下方的連接線**DoorbellFinalTransform**圖形。  
  
14. 在 屬性 視窗 （在右下方的螢幕） 上，按一下 **名稱**屬性來變更名稱**傳送**圖形至**DoorbellSend**，然後按  **輸入**。  
  
 若要繼續[步驟 11： 建立協調流程變數](../../adapters-and-accelerators/accelerator-hl7/step-11-create-orchestration-variables.md)。  
  
## <a name="see-also"></a>另請參閱  
 [訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)