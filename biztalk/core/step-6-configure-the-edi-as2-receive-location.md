---
title: 步驟 6： 設定 EDI AS2 接收位置 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 167f8ba2-d38b-4088-863b-2bd90c2a12a2
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4bbf1fce88301960a28c19fa20c9996282ce4619
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276254"
---
# <a name="step-6-configure-the-edi-as2-receive-location"></a>步驟 6： 設定 EDI AS2 接收位置
![步驟 11-6](../core/media/tut-step6-of-11.gif "Tut_Step6_of_11")  
  
 在這個步驟中，您會設定從 Fabrikam 合作對象接收 EDI 訊息的單向接收位置。 這個接收位置會使用 AS2EdiReceive 接收管線來處理內送的 EDI/AS2 訊息。 sender.exe 應用程式將會透過 Contoso 虛擬目錄，利用 BTSHTTPReceive.dll ISAPI 延伸模組，將訊息傳送到接收位置。  
  
 在本教學課程中，您將設定動態傳送埠，以非同步方式傳送 MDN 回應。 在這個案例中，您只需要單向的接收埠。 不過，您也可以變更 Sender.exe 來傳送指定同步 MDN 的 AS2 訊息。 這樣您就必須建立雙向的要求-回應接收埠來傳回 MDN。 如需詳細資訊，請參閱的 「 測試方案 > 一節的[逐步解說 (AS2): 使用同步 MDN 透過 AS2 接收的 EDI](../core/walkthrough-as2-receiving-edi-over-as2-with-a-synchronous-mdn.md)。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="to-create-the-biztalk-http-receive-location"></a>若要建立 BizTalk HTTP 接收位置  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，在 [BizTalk Application 1] 節點中，以滑鼠右鍵按一下**接收埠**，指向 **新增**，然後按一下**單向接收埠**.  
  
2.  接收埠命名為**Receive_AS2**。  
  
3.  按一下**接收位置**在主控台樹狀目錄中，然後按一下**新增**。  
  
4.  在**接收位置屬性**對話方塊中，名稱您接收位置**Receive_AS2**，選取**HTTP**如**類型**，然後按一下**設定**。  
  
5.  在**HTTP 傳輸屬性**對話方塊方塊中，輸入 **/Contoso/BTSHTTPReceive.dll**如**虛擬目錄加 ISAPI 延伸模組**。 清除**成功時傳回相互關聯控制代碼**選取**擱置失敗的要求**。 按一下 **[確定]**。  
  
6.  選取**AS2EdiReceive**如**接收管線**。 按一下**確定**，然後按一下**確定**一次。  
  
    > [!NOTE]
    >  AS2EdiReceive 接收管線會執行 AS2 解碼和 EDI 解譯。  
  
7.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下 [**接收位置**BizTalk Application 1] 節點下，以滑鼠右鍵按一下**Receive_AS2**，然後按一下**啟用**.  
  
## <a name="next-steps"></a>後續步驟  
 設定傳送埠 (**Send_Asynch_MDN**) 中所述，傳送埠以將非同步 MDN 傳回 Fabrikam，[步驟 7： 設定 MDN 傳送埠](../core/step-7-configure-the-mdn-send-port.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 如何接收 AS2 訊息](../core/how-biztalk-server-receives-as2-messages.md)   
 [設定透過 AS2 接收訊息的連接埠](../core/configuring-a-receive-port-for-messages-over-as2.md)