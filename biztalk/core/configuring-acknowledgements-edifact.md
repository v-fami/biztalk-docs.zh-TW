---
title: "設定通知 (EDIFACT) |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9436feb7-4c29-4b7c-b5c2-991660e6c1a9
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4fe376437c2d6657acb98d548c2c1373b050d599
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-acknowledgements-edifact"></a>設定通知 (EDIFACT)
在夥伴協議中，您可以指定要將何種類型的通知傳回給合作對象，以及要在傳送通知時使用何種傳送埠。 您也可以指定是否要批次處理通知、通知的開始交易集參考編號為何，以及是否要針對接受的交易集產生 SG1/SG4 迴圈。  
  
> [!IMPORTANT]
>  下列屬性會停用此頁面上清除**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。  
>   
>  -   **產生 SG1/SG4 迴圈接受的交易集 （如果未選取，會產生迴圈在 UCM.5 不等於 7 時，才）**。  
>   
>  只有在對應於合作對象送出交換屬性的單向協議索引標籤上，這些屬性才會變成停用狀態。 例如，如果您建立兩個合作對象的合作對象 A 與 Party B，並為合作對象 A 清除核取方塊，上述屬性清單會停用上**合作對象 a-> 合作對象 B**單向協議索引標籤。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-edifact-ack-contrl-properties"></a>若要設定 EDIFACT 通知 (CONTRL) 屬性  
  
1.  建立 EDIFACT 編碼協議中所述[設定一般設定 (EDIFACT)](../core/configuring-general-settings-edifact.md)。 若要更新現有的協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2.  在單向協議索引標籤底下**交換設定**區段中，按一下**通知**。  
  
3.  在**EDIFACT ACK （控制） 區段**，執行下列動作：  
  
    1.  選取**訊息回條 (CONTRL 必須是)**技術 (CONTRL) 通知傳回給交換傳送者。 如果**訊息回條 (CONTRL 必須是)**選取，請選取**不要批次處理訊息 (CONTRL) 訊息回條**可分別傳送每個通知，或是不選取該項即可批次處理通知。  
  
    2.  選取**通知 (CONTRL) 必須是**功能 (CONTRL) 通知傳回給交換傳送者。 如果**通知 (CONTRL) 必須是**選取，請選取**不要批次處理通知 (CONTRL)**分別傳送每個功能通知，或不選取可批次處理功能通知。  
  
4.  在**交易集狀態認可報告**區段中，若要接受的交易集功能 CONTRL 通知中強制產生 SG1/SG4 迴圈選取**產生 SG1/SG4 迴圈的接受交易集 （如果未選取，會產生迴圈在 UCM.5 不等於 7 時，才）**。 如需 SG1/SG4 迴圈的詳細資訊，請參閱[EDIFACT CONTRL 訊息做為功能通知](../core/edifact-contrl-message-as-functional-acknowledgment.md)。  
  
5.  按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定交換設定 (EDIFACT)](../core/configuring-interchange-settings-edifact.md)