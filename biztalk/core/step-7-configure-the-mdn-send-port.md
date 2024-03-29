---
title: 步驟 7： 設定 MDN 傳送埠 |Microsoft Docs
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
ms.openlocfilehash: 3e65ac8f264e1d8784c97645383b055391397da1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987743"
---
# <a name="step-7-configure-the-mdn-send-port"></a>步驟 7： 設定 MDN 傳送埠
![步驟 11-7](../core/media/tut-step7-of-11.gif "Tut_Step7_of_11")  
  
 在此步驟中，您設定動態傳送埠傳送非同步 MDN \\_MDNToFabrikam 資料夾。 此傳送埠會使用 AS2Send 傳送管線產生外寄 MDN 回應。 由於這是動態傳送埠時，它會使用訊息的標頭中的回條傳遞選項一行的位址來將訊息路由至\\_MDNToFabrikam 資料夾。 該位址是 Fabrikam 虛擬目錄。 與該虛擬目錄相關的 Default.aspx.cs 檔案會以 .msg 副檔名建立 MDN，並傳送檔案至目的資料夾 (也是於 Receipt-Delivery-Option 中所指定)。  
  
> [!NOTE]
>  您也可以透過用協議設定覆寫訊息設定，將協議設定成將 MDN 傳送至其他位址。 如需相關資訊，請參閱  
  
 在這個範例中，會使用動態傳送埠來傳送 MDN；但是，您也可以使用靜態傳送埠將 MDN 傳送至靜態位址。 如需詳細資訊，請參閱 <<c0> [ 透過 AS2 之非同步 Mdn 設定靜態傳送埠](../core/configuring-a-static-send-port-for-asynchronous-mdns-over-as2.md)並[透過 AS2 之非同步 Mdn 設定動態傳送埠](../core/configuring-a-dynamic-send-port-for-asynchronous-mdns-over-as2.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="to-create-the-sendasyncmdn-send-port"></a>若要建立 Send_Async_MDN 傳送埠  
  
1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，在 [BizTalk Application 1] 節點中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下 **動態的單向傳送埠**.  
  
2. 在 [**傳送埠屬性**] 對話方塊中，將傳送埠命名為**Send_Async_MDN**。  
  
3. 選取  **AS2Send** for**傳送管線**。  
  
   > [!NOTE]
   >  要使用 AS2Send 管線是因為 MDN 完全不需要 EDI 處理。  
  
4. 按一下 **篩選器**在主控台樹狀目錄中。 在 [篩選] 窗格中，選取**EdiIntAS.IsAS2AsynchronousMdn** for**屬性**， **==** 如**運算子**，並輸入**真**for**值**。  
  
   > [!NOTE]
   >  此篩選條件可確保動態傳送埠僅會從 MessageBox 挑選非同步 MDN。  
  
5. 按一下 [確定] 。  
  
6. 在**傳送埠**窗格[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**Send_Async_MDN**，然後按一下**啟動**。  
  
## <a name="next-steps"></a>後續步驟  
 設定傳送埠 (**Send_Async_997**) 以傳回 997 通知回給 Fabrikam，如中所述[步驟 8： 設定 997 傳送埠](../core/step-8-configure-the-997-send-port.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何傳送 AS2 訊息](../core/how-biztalk-server-sends-as2-messages.md)   
 [透過 AS2 之非同步 Mdn 設定靜態傳送埠](../core/configuring-a-static-send-port-for-asynchronous-mdns-over-as2.md)   
 [為透過 AS2 的訊息設定動態傳送埠](../core/configuring-a-dynamic-send-port-for-messages-over-as2.md)