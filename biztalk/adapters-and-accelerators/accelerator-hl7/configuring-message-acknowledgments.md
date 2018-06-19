---
title: 設定訊息通知 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- acknowledgements, configuring
- messages, acknowledgements
- configuring, acknowledgements
ms.assetid: 6ebcfc32-0a0b-4388-938f-6569a2014b91
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 339e80776dac32e25f96da5c62675f1a8d6075ee
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25962572"
---
# <a name="configuring-message-acknowledgments"></a>設定訊息通知
您使用[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]Configuration 總管**通知**指定輸入和產生通知的通知屬性的索引標籤。  
  
 下圖顯示[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管**通知** 索引標籤。  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-ops-ack.gif "hl7_ops_ack")  
  
 使用下列程序來開啟[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管，並設定通知訊息。  
  
### <a name="to-open-btahl7-configuration-explorer"></a>若要開啟 BTAHL7 組態總管  
  
-   按一下**啟動**，指向 **程式**，指向  **Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下  **BTAHL7 Configuration 總管**。  
  
### <a name="to-configure-message-acknowledgments"></a>若要設定訊息通知  
  
1.  BTAHL7 組態總管 中，在上**合作對象**索引標籤上，選取您想要設定的合作對象，然後在**通知**索引標籤上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**通知類型**|然後選取下列選項：<br /><br /> -   **無**。 如果您不要設定任何通知，請選取此選項。<br />-   **OriginalMode**。 選取此選項即可設定**MSH1 – 欄位分隔符號**， **MSH2 – 編碼字元**，和**MSH8 – 安全性**只選項。<br />-   **EnhancedMode**。 選取此選項來設定所有可用的通知選項。<br />-   **DeferredMode**。 選取此選項即可設定**MSH1 – 欄位分隔符號**， **MSH2 – 編碼字元**，和**MSH8 – 安全性**只選項。<br />-   **StaticMode**。 選取此選項即可設定**成功**和**失敗**通知選項。|  
    |**MSH 15 接受通知類型**|然後選取下列選項：<br /><br /> -   **AL**。 選取此選項，如果您一定想要傳送接受通知。<br />-   **NE**。 選取此選項，如果您不想要傳送接受通知。<br />-   **SU**。 選取此選項，如果您想要傳送訊息成功傳輸之後接受通知。<br />-   **ER**。 如果您想要傳送，請選取此選項只會發生錯誤時接受通知。|  
    |**MSH 16 的應用程式的通知類型**|然後選取下列選項：<br /><br /> -   **AL**。 如果您一定想要傳送的應用程式通知，請選取此選項。<br />-   **NE**。 如果您不想要傳送應用程式通知，請選取此選項。<br />-   **SU**。 如果您想要將訊息傳輸成功之後傳送應用程式通知，請選取此選項。<br /><br /> **ER**。 如果您想要傳送的應用程式通知只會發生錯誤時，請選取此選項。|  
    |**MSH1 – 欄位的分隔符號**|請輸入唯一的字元做為欄位分隔符號。 預設值是縱線字元 (**&#124;**)，以及允許的字元數目上限是一個字元。 請注意，是否您需要修改 MSH1，那麼您必須使用適當的 MSH1 值寫入至您 HL7 訊息內容的協調流程。 BTAHL7 序列化程式讀取從內容的值，並序列化訊息中使用它。|  
    |**MSH2 – 編碼的字元**|輸入唯一的字元做為根據 HL7 標準編碼的字元。 預設編碼的字元是 ^，~， \\，和 （& s)。 所需的最小字元是兩個字元，而允許的上限是四個字元。 請注意，如果 MSH2_3 或 MSH2_4 （逸出和子元件動態分隔符號） 中未指定您的原始訊息，通知訊息會自動填入這些欄位。 例如，如果您的原始訊息 MSH 區段`MSH&#124;^~&#124;`，其中指定只元件和重複分隔符號，則通知訊息會自動填入該欄位加入包含做為第三個和第四個元件`MSH&#124;^~\&`如果這些BTAHL7 組態總管 中的通知區段中未設定的值。|  
    |**MSH 3**|輸入產生通知，傳送應用程式的欄位值。 允許的長度上限 180 個字元以下合稱。<br /><br /> 產生的通知時未設定，包含傳入**MSH5**訊息值。 **注意：** 這個選項只適用於 2.X 訊息。 **注意：** 若要覆寫現有的值為 null，請輸入 **\\** 。|  
    |**MSH 5**|輸入產生通知的目的端應用程式的欄位值。 允許的長度上限 180 個字元以下合稱。<br /><br /> 產生的通知時未設定，包含傳入**MSH3**訊息值。 **注意：** 這個選項只適用於 2.X 訊息。 **注意：** 若要覆寫現有的值為 null，請輸入 **\\** 。|  
    |**MSH8-安全性**|輸入選擇性的安全性字元。|  
    |**MSH 9**|輸入產生的通知訊息類型的欄位值。<br /><br /> 產生的通知時未設定，包含傳入**MSH9**訊息值。 **注意：** 這個選項只適用於 2.X 訊息。 **注意：** 若要覆寫現有的值為 null，請輸入 **\\** 。|  
    |**MSH15 – 接受通知類型**|選取從接受通知類型的下列選項：<br /><br /> -   **AL**。 選取此選項，如果您一定想要傳送接受通知。<br />-   **NE**。 選取此選項，如果您不想要傳送接受通知。<br />-   **SU**。 選取此選項，如果您想要傳送訊息成功傳輸之後接受通知。<br />-   **ER**。 如果您想要傳送，請選取此選項只會發生錯誤時接受通知。|  
    |**如果成功**|輸入用於靜態成功的訊息傳遞通知的文字。|  
    |**失敗**|輸入用於靜態通知傳遞失敗的訊息文字。|  
    |**路由通知設定為要求-回應上的傳送管線的傳送埠**|選取此選項可將同步的 ACK 訊息傳送到 LOB 應用程式的來源。 請求-回應傳送埠上，才可用這個選項。<br /><br /> 如果未選取此選項，接收管線會產生通知訊息，根據您的通知設定。|  
  
2.  按一下 **[儲存]**。  
  
## <a name="see-also"></a>請參閱  
 [通知設定](../../adapters-and-accelerators/accelerator-hl7/ack-configuration-settings.md)   
 [通知設定](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-settings.md)   
 [建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)