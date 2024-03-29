---
title: 設定驗證 (AS2) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1ff22dc8-a544-46f9-86fb-f6845e2dfe46
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c14d510f0d89a899aebf3feb308561aba2549df
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979783"
---
# <a name="configuring-validation-as2"></a>設定驗證 (AS2)
在夥伴協議中，您必須指定驗證設定來驗證輸入 AS2 訊息。  
  
> [!NOTE]
>  上的任何屬性會停用**合作對象 A]-> [合作對象 B**單向協議索引標籤，如果您清除**本機 BizTalk 可處理支援此合作對象傳送訊息的合作對象所接收的訊息**核取方塊合作對象 a。不過，下列屬性會停用在相同的頁面上**合作對象 B]-> [合作對象 A**索引標籤上，如果您在建立合作對象 a 時選取此核取方塊  
>   
>  -   **使用協議設定進行驗證，並以 MDN 取代訊息標頭**  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-validation-properties"></a>設定驗證屬性  
  
1. 建立 AS2 協議中所述[設定的一般設定 (AS2)](../core/configuring-general-settings-as2.md)。 若要更新現有的 AS2 協議，以滑鼠右鍵按一下協議**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2. 在單向協議索引標籤上，按一下 **驗證**。  
  
3. 選取 **使用協議設定進行驗證與 MDN 取代訊息標頭**核取方塊，如果您想[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]驗證數位簽章、 壓縮和加密內送訊息，並根據中的設定協議。 如果已清除此核取方塊，就會針對訊息 AS2 標頭中的屬性而不是針對協議屬性來驗證以判斷此處理。 如需 AS2 標頭的清單，請參閱 < [AS2 訊息](../core/as2-messages.md)。  
  
4. 選取 **訊息應該簽署**核取方塊，以確保輸入的訊息已簽署。  
  
5. 選取 **訊息應該壓縮**核取方塊，以確保輸入的訊息已壓縮。  
  
6. 選取 **訊息應該加密**核取方塊，以確保輸入的訊息已加密。 選取的加密演算法**加密演算法**下拉式清單。 

   **開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]和較新版本**，AES 支援會自動包含。 選項包括 DES3、 RC2，AES128 （預設）、 AES192、 和 AES256。
    
   如先前[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]版本中，選項會 DES3 和 RC2。
  
   > [!NOTE]
   >  只有在已設定適當屬性時，AS2 接收管道才會驗證數位簽章、解壓縮訊息或解密訊息。 如果**使用協議設定進行驗證與 MDN 取代訊息標頭**選取屬性，而且該訊息的簽章、 壓縮和加密協議中選取不同的傳輸屬性屬性，則 AS2 解碼器會擱置訊息並發佈錯誤。  
  
7. 選取 **檢查憑證撤銷清單**核取方塊，以判斷要用於驗證內送訊息的憑證是否已包含在憑證撤銷清單中，表示，它已被撤銷，或者，是否已經超過到期日。 如果是的話，BizTalk Server 便不會解密訊息，但會擱置它。 如果清除這個屬性，BizTalk Server 便不會執行這項檢查。  
  
   > [!NOTE]
   >  在擷取和搜尋憑證撤銷清單時會發生延遲。  
  
8. 選取 **檢查是否有重複的訊息內**核取方塊，以判斷內送訊息是否重複先前接收的訊息。  
  
    如果您已核取**檢查是否有重複的訊息內**屬性，設定**天**會複製屬性，指出先前接收的訊息時檢查所要使用的範圍，檢查**擱置重複訊息**屬性，以指示應暫止重複的訊息。  
  
   > [!NOTE]
   >  **AS2-從**並**AS2-以**欄位用來判斷訊息是否重複。 如果訊息包含與先前已接收訊息的這些欄位相同的值，即使其他標頭或內容不同，還是會標示為重複。  
  
9. 按一下 **套用**以接受變更，再繼續進行設定，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定 AS2 協議屬性](../core/configuring-as2-agreement-properties.md)