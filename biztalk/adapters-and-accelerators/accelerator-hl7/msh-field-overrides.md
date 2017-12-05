---
title: "MSH 欄位覆寫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- headers, overriding
- MSH Map tab [Configuration Explorer]
- headers, MSH Map tab
- messages, message headers
ms.assetid: f5b2c820-57e7-4a56-9d9f-713563bd7335
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7303de4a8054cfe9f7140bd6eb548c228248777c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="msh-field-overrides"></a>MSH 欄位覆寫
每個 HL7 訊息具有訊息標頭。 使用[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]，您可以覆寫您的商務需求為基礎的任何訊息標頭值。 您使用[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管**MSH 對應** 索引標籤，以手動方式覆寫訊息標頭值而不使用任何對應或協調流程。  
  
## <a name="configuring-msh-field-overrides"></a>MSH 欄位的設定會覆寫  
 您使用**MSH 對應**索引標籤中[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管 (在高階**合作對象** 索引標籤) 設定 MSH 欄位覆寫。 MSH 中現有的值輸出 HL7 訊息時使用的值覆寫這個索引標籤的 MSH 欄位中輸入值[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]將傳送至選取的合作對象。 您可以輸入新的值，有許多的 MSH 欄位，或從 MSH15 和 MSH16 欄位的下拉式清單中選取值。  
  
 下圖顯示[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管**MSH 對應** 索引標籤。  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-ops-msh.gif "hl7_ops_msh")  
  
 使用下列程序來開啟[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管並設定 MSH 欄位覆寫。  
  
#### <a name="to-open-btahl7-configuration-explorer"></a>若要開啟 BTAHL7 組態總管  
  
-   按一下**啟動**，按一下 **程式**，按一下  **Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下  **BTAHL7 Configuration 總管**。  
  
#### <a name="to-configure-msh-field-overrides"></a>若要設定的覆寫 MSH 欄位  
  
1.  BTAHL7 組態總管 中，在上**MSH 對應**索引標籤上，執行下列動作：  
  
    > [!NOTE]
    >  若要覆寫現有的值為 null，請輸入 **\\** 。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**MSH.3**|訊息類型 欄位會覆寫此訊息標頭。|  
    |**MSH.4**|訊息類型 欄位會覆寫此訊息標頭。|  
    |**MSH.5**|訊息類型 欄位會覆寫此訊息標頭。|  
    |**MSH.6**|訊息類型 欄位會覆寫此訊息標頭。|  
    |**MSH.8**|訊息類型 欄位會覆寫此訊息標頭。|  
    |**MSH.9**|訊息類型 欄位會覆寫此訊息標頭|  
    |**MSH.12**|訊息類型 欄位會覆寫此訊息標頭。|  
    |**MSH.15**|選取從接受通知類型的通知覆寫下列選項：<br /><br /> -   **AL**。 選取此選項，如果您一定想要傳送接受通知。<br />-   **NE**。 選取此選項，如果您不想要傳送接受通知。<br />-   **SU**。 選取此選項，如果您想要傳送訊息成功傳輸之後接受通知。<br />-   **ER**。 如果您想要傳送，請選取此選項只會發生錯誤時接受通知。|  
    |**MSH.16**|選取此選項，從應用程式通知類型的通知覆寫下列選項：<br /><br /> -   **AL**。 如果您一定想要傳送的應用程式通知，請選取此選項。<br />-   **NE**。 如果您不想要傳送應用程式通知，請選取此選項。<br />-   **SU**。 如果您想要將訊息傳輸成功之後傳送應用程式通知，請選取此選項。<br />-   **ER**。 如果您想要傳送的應用程式通知只會發生錯誤時，請選取此選項。|  
  
2.  按一下 **[儲存]**。  
  
## <a name="see-also"></a>請參閱  
 [記錄設定](../../adapters-and-accelerators/accelerator-hl7/logging-configuration.md)   
 [訊息批次](../../adapters-and-accelerators/accelerator-hl7/message-batching.md)   
[作業記錄、訊息批次處理、驗證和通知設定](../../adapters-and-accelerators/accelerator-hl7/operational-logging-message-batching-validation-and-asknowledgment-settings.md)