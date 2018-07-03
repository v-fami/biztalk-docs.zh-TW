---
title: 步驟 5： 設定接收埠和接收位置 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 43fc8d12-5fde-4ddf-a7f0-770f078ba66b
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce84560a2444d52986a25038f96fdbc835c75f9f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993367"
---
# <a name="step-5-configure-a-receive-port-and-receive-location"></a>步驟 5： 設定接收埠和接收位置
![步驟 5 的 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-5of9.gif "Step_5of9")  
  
 在此步驟中，您將設定接收埠和接收位置，以在為 Fabrikam 合作對象設定的資料夾中接收 850 訊息。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="to-configure-a-receive-port-and-receive-location-for-receiving-the-850-message"></a>若要設定用來接收 850 訊息的接收埠和接收位置  
  
1. 在 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開**BizTalk Server 管理]**， **BizTalk 群組**，**應用程式**，然後**BizTalk應用程式 1**。 以滑鼠右鍵按一下**接收連接埠**，指向**新增**，然後按一下**單向接收埠**。  
  
2. 在接收埠屬性 對話方塊中，在**名稱**欄位中，輸入`ReceiveEDI_fromTHEM_A`。  
  
3. 按一下 **接收位置**在主控台樹狀目錄中，然後按一下**新增**右窗格中。  
  
4. 在 **接收位置屬性**對話方塊中，於**名稱**欄位中，輸入`fromTHEM_4010_850`。  
  
5. 針對**型別**，選取**檔案**，然後按一下**設定**。  
  
   > [!NOTE]
   >  接收位置的傳輸類型是 FILE，因為測試訊息是傳送到資料夾的一般檔案。  
  
6. 在 [ **FILE 傳輸屬性**] 對話方塊中，按一下**瀏覽**旁**接收資料夾**欄位。 在 [**瀏覽資料夾**] 對話方塊中，移至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\ProcessEDI_TestLocations\Scenario A\fromTHEM，然後再按一下**確定**。  
  
7. 在**FILE 傳輸屬性**] 對話方塊中，變更**檔案遮罩**來 **\*.txt** ，按一下 [**確定**。  
  
   > [!NOTE]
   >  檔案遮罩之所以設為 *.txt，是因為輸入測試訊息是文字檔案 SamplePO.txt。  
  
8. 在 **接收位置屬性**對話方塊中，於**接收管線**欄位中，選取**EdiReceive**。  
  
   > [!NOTE]
   >  用來接收 EDI 交換 (除了透過 AS2 傳輸所傳送的交換之外) 的接收管線是 EdiReceive 管線 (透過 AS2 傳輸所傳送的 EDI 交換則使用 AS2EdiReceive 接收管線接收)。  
  
   > [!NOTE]
   >  如果接收管線的下拉式清單未列有 EdiReceive，表示您的應用程式可能沒有 BizTalk EDI 應用程式的參考。 若要新增的參考，請參閱[如何將參考加入 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。  
  
9. 按一下  **確定**，然後按一下**確定**一次。  
  
   > [!NOTE]
   >  擁有 BizTalk 服務登入權限的帳戶也應獲得與 fromTHEM_4010_850 接收位置相關聯之接收資料夾 ([!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\ProcessEDI_TestLocations\fromTHEM) 的完整存取權限。 如果沒有，則當您嘗試啟用接收位置時，會收到錯誤。 若要變更接收資料夾的存取權限，請移至 安全性 索引標籤**屬性**Windows 檔案總管 中的該資料夾的對話方塊。  
  
10. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下**接收位置**，以滑鼠右鍵按一下**fromTHEM_4010_850**，然後按一下 **啟用**。  
  
## <a name="next-steps"></a>後續步驟  
 設定傳送埠 (**toOrderSystem**) 來將 850 訊息傳送到 OrderSystem 中, 所述[步驟 6： 設定傳送埠以將資料傳送到您的組織](../core/step-6-configure-a-send-port-to-send-data-to-your-organization.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設定連接埠來接收 EDI 訊息和通知](../core/configuring-a-port-to-receive-edi-messages-and-acknowledgments.md)