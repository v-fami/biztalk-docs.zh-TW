---
title: 步驟 10： 建立協調流程 |Microsoft Docs
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
ms.openlocfilehash: e896b5a5723b84cfc94d735aa51b8bee848b41b9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989775"
---
# <a name="step-10-create-an-orchestration"></a>步驟 10： 建立協調流程
在此步驟中，您可以使用 協調流程設計師建立協調流程代表商務程序來擷取其他的病患詳細資料，以完全填入 ADT_A04 訊息。 使用協調流程設計師 」，選取表示此商務程序的動作所需的協調流程圖形。 在更新版本的練習中，您可以提供其他的資訊，來設定圖形，以便它們可以正確運作。  
  
> [!NOTE]
>  在下列步驟中建立的協調流程僅適用於本教學課程的內容中。 為了讓協調流程才能正常運作，它需要的組件參考、 對應和您在使用本教學課程時所建立的成品。  
  
### <a name="to-create-an-orchestration"></a>建立協調流程  
  
1. 在 [方案總管] 中，以滑鼠右鍵按一下**BTAHL7 專案**，指向**新增**，然後按一下**新項目**。  
  
2. 在 **加入新項目**對話方塊的 **類別**窗格中，按一下**協調流程檔案**。  
  
3. 在 **範本**窗格中，按一下**BizTalk 協調流程**。  
  
4. 在 **名稱**欄位中，輸入**Doorbell Orchestration.odx** (請注意這個字之間沒有空格**Doorbell**並**協調流程**) 作為協調流程的名稱，然後按一下**新增**以建立新的協調流程檔案。  
  
5. 在 **檢視**功能表上，按一下**工具箱**。  
  
6. 在 **工具箱**窗格拖曳到**接收**圖形至 設計 檢視介面並將它放在標示為區域上**從 工具箱 拖曳圖形**。  
  
7. 在 屬性 視窗 （在右下方的螢幕） 上，按一下**名稱**屬性，並輸入**DoorbellReceive**同名**接收**圖形，然後再按  **輸入**。  
  
8. 在 [屬性] 視窗中，變更**Activate**屬性設 **，則為 True**。  
  
9. 拖曳**轉換**圖形從 [工具箱]，並把它放在正下方**DoorbellReceive**圖形。  
  
10. 在 屬性 視窗 （在右下方的螢幕） 上，按一下 **名稱**屬性來變更名稱**轉換**圖形至**DoorbellTransform**，然後按下**輸入**。  
  
11. 在 **工具箱**窗格拖曳到**訊息指派**圖形至 設計 檢視介面並將它放在正下方的區域**constructmessage_1**圖形。  
  
12. 在 協調流程設計檢視 介面中，按一下  **MessageAssignment_1**圖形，然後在**屬性**窗格中，按一下 **名稱**，輸入新名稱**DoorbellFinalTransform**，然後按下**Enter**。  
  
13. 拖曳**傳送**圖形從 [工具箱]，並放在正下方的連接線**DoorbellFinalTransform**圖形。  
  
14. 在 屬性 視窗 （在右下方的螢幕） 上，按一下 **名稱**屬性來變更名稱**傳送**圖形至**DoorbellSend**，然後按  **輸入**。  
  
    請繼續進行[步驟 11： 建立協調流程變數](../../adapters-and-accelerators/accelerator-hl7/step-11-create-orchestration-variables.md)。  
  
## <a name="see-also"></a>另請參閱  
 [訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)