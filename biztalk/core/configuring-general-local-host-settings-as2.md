---
title: "設定一般本機主機設定 (AS2) |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 980daac2-8387-44cc-ae55-38639f759668
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de5e5c076e6b245e4a662f8132d027e927df6142
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-general-local-host-settings-as2"></a>設定一般本機主機設定 (AS2)
在本機主機一般設定中，您可以指定 AS2 訊息的內容類型，以及是否保留檔案名稱做為 AS2 訊息標頭的一部分。  
  
> [!IMPORTANT]
>  所有屬性會停都用此頁面上清除**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。  
>   
>  只有在對應於合作對象送出交換屬性的單向協議索引標籤上，這些屬性才會變成停用狀態。 例如，如果您建立兩個合作對象的合作對象 A 與 Party B，並為合作對象 A 清除核取方塊，上述屬性清單會停用上**合作對象 a-> 合作對象 B**單向協議索引標籤。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-the-general-settings"></a>若要設定一般設定  
  
1.  建立 AS2 協議中所述[設定一般設定 (AS2)](../core/configuring-general-settings-as2.md)。 若要更新現有的 AS2 協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2.  在單向協議索引標籤底下**本機主機設定**區段中，按一下**一般**。  
  
3.  選取**傳送訊息之前檢查憑證撤銷清單**核取方塊，以判斷要用於簽署外寄訊息的憑證是否已包含在憑證撤銷清單中，表示它已被撤銷，或是否已經超過到期日。 如果是的話，BizTalk Server 便不會將訊息加密，但會擱置它。 如果清除這個屬性，BizTalk Server 便不會執行這項檢查。  
  
    > [!NOTE]
    >  在擷取和搜尋憑證撤銷清單時會發生延遲。  
  
4.  如**預設內容類型**，選取合作對象必須用於外寄 AS2 訊息的預設內容類型。 如果`ContentType`屬性設定的設定是用來產生外寄訊息，否則訊息內文部分內容中，這個值**預設內容類型**屬性使用。  
  
5.  選取**MIME 標頭中的傳輸檔案名稱**核取方塊做為輸出 AS2 訊息的 MIME 標頭的一部分傳送的檔案名稱。 若要指定檔案名稱，選取**指定檔案名稱**或**具有系統產生的檔案名稱**。  
  
    > [!NOTE]
    >  選取**具有系統產生的檔案名稱**會產生新的 GUID 值做為 AS2 訊息中傳送的每個附件的檔案名稱。  
  
6.  如果您選取**指定檔案名稱**，將字串值或內容屬性中的輸入**指定檔案名稱**欄位。 您也可以啟用**暫止訊息，如果找不到內容屬性 （如 %property%)**來擱置訊息，如果選取的內容屬性不存在的傳出訊息。  
  
    > [!NOTE]
    >  若要指定內容屬性，請用 %字元括住屬性名稱。 例如， `%FILE.ReceivedFileName%`。  
  
7.  按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定本機主機設定 (AS2)](../core/configuring-local-host-settings-as2.md)