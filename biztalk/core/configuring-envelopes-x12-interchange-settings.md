---
title: 設定信封 （X12 交換設定） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4fade73-14cf-475c-81b5-6102c75db991
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf4f88ee1e5d786367c1a4bc0f5b2404fd5c1a37
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233414"
---
# <a name="configuring-envelopes-x12-interchange-settings"></a>設定信封 (X12 交換設定)
產生 X12 交換信封設定會定義 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 如何產生傳送至接收合作對象的 X12 編碼交換信封。 在本節中，您會定義 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 針對其傳送至合作對象的 X12 編碼交換來產生 ISA 區段的方式。 ISA 區段則是 X12 編碼交換的交換控制標頭。  
  
> [!NOTE]
>  對於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段而言，英數 ISA 欄位的長度是固定的。 不過，如果是 [!INCLUDE[TPM](../includes/tpm-md.md)] 使用者介面，則您可以針對英數 ISA 欄位輸入單一字元。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用尾端的空格字元來填補這些欄位，確保符合標準的需求。  
  
> [!NOTE]
>  此處所述設定同樣適用於 HIPAA 交換信封產生作業。  
  
> [!IMPORTANT]
>  所有屬性會停都用此頁面上清除**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。  
>   
>  只有在對應於合作對象送出交換屬性的單向協議索引標籤上，這些屬性才會變成停用狀態。 例如，如果您建立兩個合作對象的合作對象 A 與 Party B，並為合作對象 A 清除核取方塊，上述屬性清單會停用上**合作對象 a-> 合作對象 B**單向協議索引標籤。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-define-the-envelope"></a>若要定義信封  
  
1.  建立 X12 編碼協議中所述[設定一般設定 (X12)](../core/configuring-general-settings-x12.md)。 若要更新現有的協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2.  在單向協議索引標籤底下**交換設定**區段中，按一下**信封**。  
  
3.  在下**ISA11 使用狀況**，保留**標準識別項**選取以指定標準的識別項，而非重複分隔符號，然後從下拉式清單中選取標準識別項的值。 選取**重複分隔符號**指定重複分隔符號而非標準的識別項，並接著輸入單一字元做為重複分隔符號。 用來區隔交易集合中重複之區段的重複分隔符號，僅限使用 ASCII 字元集中的值。  
  
4.  如**控制版本號碼 (ISA12)**，選取的 x12 標準所使用的版本[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]產生外寄交換。  
  
5.  如**使用狀況指示符號 (ISA15)**，選取以表示所產生的交換[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]是資訊、 生產資料還是測試資料。  
  
6.  按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定交換設定 (X12)](../core/configuring-interchange-settings-x12.md)