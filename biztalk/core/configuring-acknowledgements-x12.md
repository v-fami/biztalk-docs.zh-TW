---
title: 設定通知 (X12) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eec2dbff-5d04-4a38-bad0-33d040b6dd12
caps.latest.revision: 26
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 28df03b8955c17888a4722c361a2e4481c63b413
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970691"
---
# <a name="configuring-acknowledgements-x12"></a>設定通知 (X12)
在夥伴協議中，您可以指定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在收到來自合作對象的 X12 編碼交換後，應如何產生通知，以及應對合作對象傳回哪種類型的通知。 您可以指定是否要批次處理通知，以及是否要針對接受的交易集產生 AK2 迴圈。 本節提供如何執行此作業的指示。  
  
> [!NOTE]
>  此處所說明的通知屬性也適用於 HIPAA 通知。  
> 
> [!IMPORTANT]
>  下列屬性會停用此頁面上清除**本機 BizTalk 可處理支援此合作對象傳送訊息的合作對象所接收的訊息**時建立您要為其建立的合作對象 核取方塊協議。  
> 
> - **包含針對接受的交易集的 AK2 迴圈 （如果未選取，將會產生迴圈只有在 AK501 不等於 A 時，才）**。  
> 
>   只有在對應於合作對象送出交換屬性的單向協議索引標籤上，這些屬性才會變成停用狀態。 例如，如果您建立兩個合作對象的合作對象 A 與 Party B，並為合作對象 A 清除核取方塊，上述屬性清單會停用上**合作對象 A]-> [合作對象 B**單向協議索引標籤。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-x12-ack-properties"></a>若要設定 X12 通知屬性  
  
1.  建立 X12 編碼協議中所述[設定的一般設定 (X12)](../core/configuring-general-settings-x12.md)。 若要更新現有的協議，以滑鼠右鍵按一下協議**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2.  在單向協議索引標籤底下**交換設定**，按一下**通知**。  
  
3.  選取  **預期 TA1**將技術 (TA1) 通知傳回給交換傳送者。 如果選取，請選取**不要批次處理 TA1**分別傳送每個技術通知，則會批次處理技術通知 核取方塊。  
  
4.  選取  **預期 997**功能 (997) 通知傳回給交換傳送者。 如果選取，請選取**不要批次處理 997**分別傳送每個功能通知，則會批次處理功能通知 核取方塊。  
  
5.  若要在 997 通知中針對接受的交易集產生 AK2 迴圈，請選取**接受的交易集的包含 AK2 迴圈 （如果未選取，將會產生迴圈只有在 AK501 不等於 A 時，才）**。 如需 AK2 迴圈的詳細資訊，請參閱[X12 997 通知](../core/x12-997-acknowledgment.md)。  
  
6.  按一下 **套用**以接受變更，再繼續進行設定，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定交換設定 (X12)](../core/configuring-interchange-settings-x12.md)