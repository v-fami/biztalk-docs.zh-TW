---
title: 步驟 7： 設定 MDN 傳送埠 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 983033ac-9d32-47c8-9bb8-b4161bcdf183
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d0f70df6846553e2d64711f33e8c5a0b0e4d2cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277958"
---
# <a name="step-7-configure-the-mdn-send-port"></a>步驟 7： 設定 MDN 傳送埠
![步驟 7 11](../core/media/tut-step7-of-11.gif "Tut_Step7_of_11")  
  
 在此步驟中，您將設定動態傳送埠傳送非同步 MDN \\_MDNToFabrikam 資料夾。 此傳送埠會使用 AS2Send 傳送管線產生外寄 MDN 回應。 由於這是動態傳送埠時，它會使用位址的訊息標頭中的回條傳遞選項列中將訊息路由至\\_MDNToFabrikam 資料夾。 該位址是 Fabrikam 虛擬目錄。 與該虛擬目錄相關的 Default.aspx.cs 檔案會以 .msg 副檔名建立 MDN，並傳送檔案至目的資料夾 (也是於 Receipt-Delivery-Option 中所指定)。  
  
> [!NOTE]
>  您也可以透過用協議設定覆寫訊息設定，將協議設定成將 MDN 傳送至其他位址。 如需詳細資訊，請參閱  
  
 在這個範例中，會使用動態傳送埠來傳送 MDN；但是，您也可以使用靜態傳送埠將 MDN 傳送至靜態位址。 如需詳細資訊，請參閱[設定透過 AS2 之非同步 Mdn 的靜態傳送埠](../core/configuring-a-static-send-port-for-asynchronous-mdns-over-as2.md)和[設定透過 AS2 之非同步 Mdn 的動態傳送埠](../core/configuring-a-dynamic-send-port-for-asynchronous-mdns-over-as2.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="to-create-the-sendasyncmdn-send-port"></a>若要建立 Send_Async_MDN 傳送埠  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，在 [BizTalk Application 1] 節點中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **動態單向傳送連接埠**.  
  
2.  在**傳送埠屬性**對話方塊中，將傳送埠為**Send_Async_MDN**。  
  
3.  選取**AS2Send**如**傳送管線**。  
  
    > [!NOTE]
    >  要使用 AS2Send 管線是因為 MDN 完全不需要 EDI 處理。  
  
4.  按一下**篩選**在主控台樹狀目錄中。 在 [篩選] 窗格中，選取**EdiIntAS.IsAS2AsynchronousMdn**如**屬性**，  **==** 的**運算子**，然後輸入**True**如**值**。  
  
    > [!NOTE]
    >  此篩選條件可確保動態傳送埠僅會從 MessageBox 挑選非同步 MDN。  
  
5.  按一下 **[確定]**。  
  
6.  在**傳送埠**窗格[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**Send_Async_MDN**，然後按一下 **啟動**。  
  
## <a name="next-steps"></a>後續步驟  
 設定傳送埠 (**Send_Async_997**) 將 997 通知送回給 Fabrikam，如中所述[步驟 8： 設定 997 傳送埠](../core/step-8-configure-the-997-send-port.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 傳送 AS2 訊息的方式](../core/how-biztalk-server-sends-as2-messages.md)   
 [設定透過 AS2 之非同步 Mdn 的靜態傳送埠](../core/configuring-a-static-send-port-for-asynchronous-mdns-over-as2.md)   
 [透過 AS2 的訊息設定動態傳送埠](../core/configuring-a-dynamic-send-port-for-messages-over-as2.md)