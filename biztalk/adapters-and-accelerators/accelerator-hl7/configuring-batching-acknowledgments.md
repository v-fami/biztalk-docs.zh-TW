---
title: "設定批次處理通知 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, acknowledgements
- acknowledgements, batching
ms.assetid: f3529638-e036-4270-ae6d-1bdc3ef98727
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a788b83614c809505d632848a5a789070948fed5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-batching-acknowledgments"></a>設定批次處理通知
您使用[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]組態總管，以指定輸入和產生通知的通知屬性。  
  
### <a name="to-run-btahl7-configuration-explorer"></a>若要執行 BTAHL7 組態總管  
  
-   按一下**啟動**，指向 **程式**，指向  **Microsoft BizTalk\<版本 > Accelerator for HL7**，然後按一下  **BTAHL7組態總管**。  
  
### <a name="to-configure-message-batching-acknowledgments"></a>若要設定批次處理通知訊息  
  
-   BTAHL7 組態總管 中，在中**BTAHL7 Configuration 總管**對話方塊**合作對象**索引標籤上，選取您想要設定的合作對象，然後在**通知**索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**通知類型**|選取下列其中一項：<br /><br /> -   **無**。 如果您不要設定任何通知，請選取。<br />-   **OriginalMode**。 選取以設定**MSH1 – 欄位分隔符號**， **MSH2 – 編碼字元**，和**MSH8 – 安全性**只選項。<br />-   **EnhancedMode**。 選取以設定所有可用的通知選項。<br />-   **DeferredMode**。 選取以設定**MSH1 – 欄位分隔符號**， **MSH2 – 編碼字元**，和**MSH8 – 安全性**只選項。<br />-   **StaticMode**。 選取以設定**成功**和**失敗**通知選項。|  
    |**MSH 15 接受通知類型**|選取下列其中一項：<br /><br /> -   **AL**。 選取要一律傳送接受通知。<br />-   **NE**。 選取要一律不傳送接受通知。<br />-   **SU**。 選取要傳送的訊息成功傳輸之後接受通知。<br />-   **ER**。 選取要傳送接受通知只會發生錯誤。|  
    |**MSH 15 應用程式的通知類型**|選取下列其中一項：<br /><br /> -   **AL**。 選取此選項，將一律傳送應用程式通知。<br />-   **NE**。 選取此選項，即可永遠不會傳送應用程式通知。<br />-   **SU**。 選取此選項，將訊息傳輸成功之後傳送應用程式通知。<br />-   **ER**。 選取即可只會發生錯誤時傳送應用程式通知。|  
    |**MSH1 – 欄位的分隔符號**|請輸入唯一的字元做為欄位分隔符號。 預設值是縱線字元 (**&#124;**)，以及允許的字元數目上限是一個字元。 請注意，是否您需要修改 MSH1，那麼您必須使用適當的 MSH1 值寫入至您 HL7 訊息內容的協調流程。 BTAHL7 序列化程式讀取從內容的值，並序列化訊息中使用它。|  
    |**MSH2 – 編碼的字元**|輸入唯一的字元做為根據 HL7 標準編碼的字元。 預設編碼的字元是 ^，~， \\，和 （& s)。 所需的最小字元是兩個字元，而允許的上限是四個字元。 請注意，如果 MSH2_3 或 MSH2_4 （逸出和子元件動態分隔符號） 中未指定您的原始訊息，通知 (ACK) 訊息會自動填入這些欄位。 例如，如果您的原始訊息 MSH 區段`MSH&#124;^~&#124;`，其中指定只元件和重複分隔符號，則通知訊息會自動填入該欄位加入包含做為第三個和第四個元件`MSH&#124;^~\&`，提供該欄位值有尚未設定 BTAHL7 組態總管 中的 通知 區段中。|  
    |**MSH3**|輸入產生通知，傳送應用程式的欄位值。 最大容許的長度共同是 180 個字元。<br /><br /> 產生的通知時未設定，包含傳入**MSH5**訊息值。 **注意：**這個選項只適用於 2.X 訊息。 **注意：**若要覆寫現有的值為 null，請輸入 **\\** 。|  
    |**MSH5**|輸入產生通知的目的端應用程式的欄位值。 最大容許的長度共同是 180 個字元。<br /><br /> 產生的通知時未設定，包含傳入**MSH3**訊息值。 **注意：**這個選項只適用於 2.X 訊息。 **注意：**若要覆寫現有的值為 null，請輸入 **\\** 。|  
    |**MSH8-安全性**|輸入選擇性的安全性字元。|  
    |**MSH15 – 接受通知類型**|選取從接受通知類型的下列選項：<br /><br /> -   **AL**。 如果您想要一律傳送，接受通知，選取。<br />-   **NE**。 如果您不想要傳送，接受通知，選取。<br />-   **SU**。 選取此選項，如果您想要傳送訊息成功傳輸之後接受通知。<br />-   **ER**。 如果您想要傳送，請選取此選項只會發生錯誤時接受通知。|  
    |**如果成功**|靜態成功的訊息傳遞通知的文字輸入。|  
    |**失敗**|輸入靜態通知傳遞失敗訊息的文字。|  
    |**路由通知設定為要求-回應上的傳送管線的傳送埠**|選取此選項可將同步的 ACK 訊息傳送到 LOB 應用程式的來源。 請求-回應傳送埠上，才可用這個選項。<br /><br /> 如果未選取此選項，接收管線會產生通知訊息，根據您的通知設定。|  
  
    > [!NOTE]
    >  通知與片段關閉產生批次訊息將包含 MSH12.1 2.4 值。 您可以手動修改的版本號碼，藉由套用在傳送管線中的對應。 如需詳細資訊，請參閱[建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設定批次處理](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md)