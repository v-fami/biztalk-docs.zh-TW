---
title: 設定批次處理 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- batching, configuring
- configuring, batching
ms.assetid: 33c72d5e-31dd-44a8-8418-1faab3239e8e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77ea79c4b96ac54e6b2d1eed281b60a261ca5cc1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976327"
---
# <a name="configuring-batching"></a>設定批次處理
您使用[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]組態總管來建立批次，批次中 / 出批次處理，，和選取可用的結構描述的輸出批次的批次。  
  
> [!NOTE]
>  您必須設定使用 BizTalk 總管 中，您可設定訊息批次處理的交易夥伴。  
  
 下圖顯示[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管**批次定義** 索引標籤。  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-ops-batchdef.gif "hl7_ops_batchdef")  
  
 使用下列程序來開啟[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管，並設定批次。  
  
### <a name="to-enable-message-batching-for-outbound-batching-create-batch"></a>若要啟用輸出批次處理 （建立批次） 的訊息批次處理  
  
1.  在 **開始**功能表中，開啟**BizTalk Server 管理**。  
  
2.  在管理主控台中，依序展開**BizTalk Server 管理**，展開**BizTalk 群組**，展開**應用程式**，然後展開**BizTalk應用程式 1**。  
  
3.  按一下 **協調流程**，以滑鼠右鍵按一下**BatchOrchestration.Orchestration_1**，然後選取**屬性**。  
  
4.  在 [協調流程屬性] 對話方塊中，按一下**繫結**在主控台樹狀目錄中。  
  
5.  在 **繫結**窗格中，選取適當的主機，如**主機**。 按一下 [確定] 。  
  
6.  以滑鼠右鍵按一下**BatchOrchestration.Orchestration_1**，然後選取**登錄**。  
  
7.  以滑鼠右鍵按一下**BatchOrchestration.Orchestration_1**，然後選取**開始**。  
  
### <a name="to-run-btahl7-configuration-explorer"></a>若要執行 BTAHL7 設定總管  
  
-   在 **開始**功能表中，開啟**Microsoft BizTalk Accelerator for HL7** ，然後按一下**BTAHL7 設定總管**。  
  
### <a name="to-configure-batching"></a>若要設定批次處理  
  
- 在 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管，請在**BTAHL7 設定總管**對話方塊的 **合作對象**索引標籤上，選取您想要設定合作對的象，然後在**批次定義**索引標籤上，執行下列動作：  
  
  |使用|以進行此動作|  
  |--------------|----------------|  
  |**需要的片段**|選取下列其中一個選項：<br /><br /> -   **是**。 若要啟用片段。<br />-   **否**。 若要停用片段。 **附註：** 新的合作對象**所需的分散程度**預設為**否**。|  
  |**選取訊息**|選取您想要從以批次傳送的訊息類型**可用的訊息** 視窗中，然後按一下 移至 向右箭號 (**>>**)。|  
  |**選取訊息通知**|選取您想要從以批次傳送通知的訊息類型**可用的訊息 Ack** ] 視窗中，然後按一下 [向右移動 (**>>**)。|  
  
  > [!NOTE]
  >  您可能不會看到您加入的結構描述您在[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]專案中[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管正在執行。 若要檢視這些檔案，您可能需要重新啟動[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管。  
  
## <a name="see-also"></a>另請參閱  
 [排程批次處理](../../adapters-and-accelerators/accelerator-hl7/scheduling-batching.md)