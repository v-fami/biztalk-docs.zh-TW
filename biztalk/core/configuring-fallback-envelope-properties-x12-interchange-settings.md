---
title: "設定後援信封屬性 （X12 交換設定） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e9b05ea-2a0f-42d6-adc2-c1f1f2b7a993
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a2b0c43a43f5b003015378ecc52c05405877c5e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-envelope-properties-x12-interchange-settings"></a>設定後援信封屬性 (X12 交換的設定)
產生 X12 交換信封設定會定義 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 如何產生傳送至接收合作對象的 X12 編碼交換信封。 在此後援協議中，您會定義 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 針對其傳送至合作對象的 X12 編碼交換來產生 ISA 區段的方式。 ISA 區段則是 X12 編碼交換的交換控制標頭。  
  
> [!NOTE]
>  對於 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段而言，英數 ISA 欄位的長度是固定的。 不過，如果是 [!INCLUDE[TPM](../includes/tpm-md.md)] 使用者介面，則您可以針對英數 ISA 欄位輸入單一字元。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用尾端的空格字元來填補這些欄位，確保符合標準的需求。  
  
> [!NOTE]
>  此處所述設定同樣適用於 HIPAA 交換信封產生作業。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-define-the-envelope"></a>若要定義信封  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**X12 後援設定**。  
  
2.  在**X12 後援設定**對話方塊中，於**X12 協議頁面**索引標籤，下方**交換設定**區段中，按一下**信封**.  
  
3.  在下**ISA11 使用狀況**，保留**標準識別項**選取以指定標準的識別項，而非重複分隔符號，然後從下拉式清單中選取標準識別項的值。 選取**重複分隔符號**指定重複分隔符號而非標準的識別項，並接著輸入單一字元做為重複分隔符號。 用來區隔交易集合中重複之區段的重複分隔符號，僅限使用 ASCII 字元集中的值。  
  
4.  如**控制版本號碼 (ISA12)**，選取的 x12 標準所使用的版本[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]產生外寄交換。  
  
5.  如**使用狀況指示符號 (ISA15)**，選取以表示所產生的交換[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]是資訊、 生產資料還是測試資料。  
  
6.  按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定 X12 後援協議屬性的交換處理](../core/configuring-x12-fallback-agreement-properties-for-interchange-processing.md)