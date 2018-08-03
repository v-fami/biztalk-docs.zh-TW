---
title: 步驟 9： 設定 EDI 內容傳送埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 71a8a4a7-7c3e-4e33-a9c0-a6445a3cc236
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11f12d57a0aee016055412b9221ff2b2de442c17
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005551"
---
# <a name="step-9-configure-the-edi-payload-send-port"></a>步驟 9： 設定 EDI 內容傳送埠
![步驟 11-9](../core/media/tut-step9-of-11.gif "Tut_Step9_of_11")  
  
 在此步驟中，您可以設定為傳送至後端 Contoso 應用程式中，從 EDI 內容產生的 XML 傳送埠以\\_EDIXMLToContoso 資料夾。 這個傳送埠會使用 PassThruTransmit 傳送管線。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="to-create-the-sendpayloadedixml-send-port"></a>若要建立 Send_Payload_EdiXml 傳送埠  
  
1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**，指向**新增**，然後按一下 **靜態單向傳送埠**。  
  
2. 在 **傳送埠屬性**對話方塊中，將傳送埠作為**Send_Payload_EdiXml**。 選取 **檔案**for**型別**，然後按一下**設定**。  
  
   > [!NOTE]
   >  因為傳送管線並不會針對該內容檔案執行 AS2 處理，所以要設定 FILE 類型。 該管線只是將內容檔案路由到本機資料夾，以便您可以檢視 EDI 交易集。  
  
3. 在**FILE 傳輸屬性** 對話方塊中，如**目的地資料夾**中，瀏覽並選取[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_EDIXMLToContoso。 離開**檔名**作為 **%MessageID%.xml**。 按一下 [確定] 。  
  
4. 接受預設值是**PassThruTransmit** for**傳送管線**。  
  
   > [!NOTE]
   >  由於此時是使用 PassThruTransmit 傳送管線，所以此管線不會對內容訊息執行任何 EDI 處理，反而是以 XML 格式傳送到 AS2EdiReceive 接收管線產生的本機資料夾。  
  
5. 按一下 **篩選器**在主控台樹狀目錄中。 針對**屬性**，輸入**BTS。MessageType**。 針對**運算子**，輸入**==**。 針對**值**，輸入`http://schemas.microsoft.com/BizTalk/Edi/X12/2006#X12_00401_864`。  
  
   > [!NOTE]
   >  此篩選條件可確保這個傳送埠僅會收取來自 MessageBox 的 X12 864 內容通知。  
  
6. 按一下 [確定] 。  
  
7. 在**傳送埠**窗格[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**Send_Payload_EdiXml**傳送埠，，然後按一下**啟動**。  
  
## <a name="next-steps"></a>後續步驟  
 您建立的 AS2 與 X12 協議兩個交易合作夥伴中所述[步驟 10： 設定 X12 和 AS2 交易夥伴協議](../core/step-10-configure-the-x12-and-as2-trading-partner-agreement.md)  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 3: AS2 教學課程](../core/tutorial-3-as2-tutorial.md)