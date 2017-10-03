---
title: "步驟 8： 設定 997 傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4780c491-9f1a-4f13-b346-6a2e1801ec09
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec3c022ec1236d760c69250a2faecc7cacdb543c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-8-configure-the-997-send-port"></a>步驟 8： 設定 997 傳送埠
![步驟 11-8](../core/media/tut-step8-of-11.gif "Tut_Step8_of_11")  
  
 在此步驟中，您會設定傳送埠，以將 997 訊息傳送給夥伴。 這個傳送埠會使用 AS2EdiSend 傳送管線，將 EDIINT/AS2 編碼的 997 通知傳送至 _997ToFabrikam 資料夾。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="to-create-the-sendasync997-send-port"></a>若要建立 Send_Async_997 傳送埠  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，在 [BizTalk Application 1] 節點中，以滑鼠右鍵按一下**傳送埠**，指向 **新增**，然後按一下 **靜態單向傳送埠**.  
  
    > [!NOTE]
    >  使用靜態單向傳送埠的原因是，Fabrikam 合作對象並沒有設定 MDN 做為 AS2 訊息接收者。  
  
2.  在**傳送埠屬性**對話方塊方塊中，將傳送埠命名**Send_Async_997**。 選取**HTTP**如**類型**，然後按一下 **設定**。  
  
3.  在**HTTP 傳輸屬性**對話方塊中，針對**目的地 URL**，輸入`http://localhost/Fabrikam/Default.aspx?Destination=_997ToFabrikam`。 清除**啟用區塊編碼**，然後按一下 **確定**。  
  
    > [!NOTE]
    >  **目的地 URL**設定可確保傳送埠會將 997 訊息傳送至 Fabrikam 虛擬目錄。 與該虛擬目錄相關的 Default.aspx.cs 檔案會以 .msg 副檔名建立 997，並將它傳送至目的資料夾。  
  
4.  在**傳送埠屬性**對話方塊中，選取**AS2EdiSend**如**傳送管線**。  
  
5.  按一下**篩選**在主控台樹狀目錄中。 如**屬性**，選取**BTS。MessageType**。 如**運算子**，選取 **==** 。 如**值**，輸入`http://schemas.microsoft.com/Edi/X12#X12_997_Root`。  
  
    > [!NOTE]
    >  此篩選條件可確保傳送埠僅會從 MessageBox 挑選 997 通知。  
  
6.  按一下 **[確定]**。  
  
7.  在**傳送埠**窗格[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**Send_Async_997**傳送埠，然後**啟動**。  
  
## <a name="next-steps"></a>後續步驟  
 設定傳送埠 (**Send_Payload_EdiXml**) 中所述，EDI 內容傳送至 Contoso，[步驟 9： 設定 EDI 內容傳送埠](../core/step-9-configure-the-edi-payload-send-port.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 傳送 AS2 訊息的方式](../core/how-biztalk-server-sends-as2-messages.md)   
 [透過 AS2 的訊息設定靜態傳送埠](../core/configuring-a-static-send-port-for-messages-over-as2.md)