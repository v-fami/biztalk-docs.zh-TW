---
title: "設定通知 (Mdn) (AS2) |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb2bf98a-deb4-460f-a1fc-3d2397c39470
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2df8c92d37d5f6bc8fbf8d6d77fb698e6178036
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-acknowledgements-mdns-as2"></a>設定通知 (MDN) (AS2)
在夥伴協議中，您可以指定收到 AS2 訊息的合作對象如何產生並傳回 MDN 回應。  
  
> [!IMPORTANT]
>  下列屬性會停用此頁面上清除**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。  
>   
>  -   **重新傳送 AS2 訊息，若未收到 MDN**核取方塊和相關聯的屬性  
> -   **覆寫傳送埠設定**核取方塊和相關聯的屬性  
>   
>  只有在對應於合作對象送出交換屬性的單向協議索引標籤上，這些屬性才會變成停用狀態。 例如，如果您建立兩個合作對象的合作對象 A 與 Party B，並為合作對象 A 清除核取方塊，上述屬性清單會停用上**合作對象 a-> 合作對象 B**單向協議索引標籤。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-configure-acknowledgements"></a>若要設定通知  
  
1.  建立 AS2 協議中所述[設定一般設定 (AS2)](../core/configuring-general-settings-as2.md)。 若要更新現有的 AS2 協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。  
  
2.  在單向協議索引標籤上，按一下 **通知 (Mdn)**。  
  
3.  選取**針對路由/傳遞選項處理 MessageBox 中的輸入的 MDN**核取方塊，以透過 as2 解碼器將 MDN 路由，以通過訊息，然後放入 MessageBox。 選取這個屬性時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會基於路由目的升級 `IsAS2MdnResponseMessage` 屬性。  
  
4.  如果您核取**使用協議設定進行驗證，並 MSDN，取代訊息標頭**屬性**驗證**頁面上，選取**要求 MDN**如果核取方塊交易夥伴必須產生 MDN 以回應 AS2 訊息。  
  
     如果**要求 MDN**核取方塊已選取，您也可以設定下列屬性：  
  
    1.  選取**要求簽署的 MDN**核取方塊，並從**簽署演算法**下拉式清單選取交易夥伴必須用來簽署 MDN 的 MIC 演算法。 [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]支援 MD5、 SHA1、 和 SHA2 (SHA256 （預設）、 SHA384 及 SHA512)。
    
        > [!NOTE] 
        > **從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]和較新版本**，SHA2 支援會自動包含。 如先前[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]版本中，請參閱[KB 3123748](https://support.microsoft.com/kb/3123748)。
  
    2.  選取**要求非同步 MDN**核取方塊，然後在**回條傳遞選項 (URL)**文字方塊中，輸入接收合作對象應該傳送 MDN 的 URL。  
  
         如果**要求非同步 MDN**核取方塊已選取，您也可以設定下列屬性：  
  
        1.  選取**重新傳送 AS2 訊息，若未收到 MDN**核取方塊以啟用重新傳輸 AS2 訊息。 輸入一個值**最小值 AS2 訊息重新傳送間隔**，**數目的 AS2 訊息重新傳送嘗試**和**停止嘗試之後會重新傳送訊息的 AS2**欄位，即可指定重試間隔、 最大嘗試次數和何時停止重新傳送訊息。  
  
            > [!NOTE]
            >  您必須選取**開啟報告** 核取方塊**一般屬性**頁面**一般** 索引標籤，然後再選取**重新傳送 AS2 訊息，如果 MDN 不收到**。  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用追蹤針對 AS2 報告，以判斷何時重新傳送 AS2 訊息儲存的資訊。  
  
        2.  如果**重新傳送 AS2 訊息，若未收到 MDN**選取核取方塊時，請檢查**覆寫傳送埠設定**指定**最小值的 HTTP 重試間隔**和**HTTP 重試嘗試次數**。 輸入一個值**停止嘗試 HTTP 重試後**欄位來指定要使用 HTTP 配接器嘗試重試時間的最大數量。  
  
    3.  如果您選取**要求非同步 MDN**核取方塊，而且指定的 URL**回條傳遞選項 (URL)**屬性，**配置通知至**文字方塊中，依預設設定為相同的 URL。 如果您未選取**要求非同步 MDN**核取方塊，您必須輸入的值**配置通知至**。 在處理 AS2 的過程中並不會使用這個欄位的值。  
  
5.  按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定 AS2 協議屬性](../core/configuring-as2-agreement-properties.md)