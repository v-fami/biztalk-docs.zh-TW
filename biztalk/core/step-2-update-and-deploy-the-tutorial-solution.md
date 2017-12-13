---
title: "步驟 2： 更新和部署教學課程解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d03adfdd-1160-4e8c-a564-3acb2ecd0476
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67fd3d34f25dd409121a3a21c9eb419b4aadce6e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-2-update-and-deploy-the-tutorial-solution"></a>步驟 2： 更新和部署教學課程解決方案
![步驟 2 的 9](../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-2of9.gif "Step_2of9")  
  
 在這個步驟中，您會更新為本教學課程所提供的解決方案，然後建置並部署教學課程組件。 必要的結構描述、自訂傳送管線和對應，已因應本教學課程目的而完成建立。 對應是用來將 850 EDI 資料轉換為「訂單系統」所需的格式。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="to-enable-the-edi-inbound-processing-solution-to-be-built-in-visual-studio"></a>若要啟用在 Visual Studio 中建置 EDI 輸入處理解決方案  
  
1.  啟動**Microsoft Visual Studio**身為系統管理員。  
  
    > [!CAUTION]
    >  如果您未以系統管理員權限啟動 Visual Studio，則您將方案部署至 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 時將會收到錯誤。  
  
2.  在 Visual Studio 中，按一下 **檔案**，指向 **開啟**，然後按一下 **專案/方案**。 移至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial，選取**EDI Inbound processing.sln]**，然後按一下 [**開啟**。  
  
    > [!NOTE]
    >  本主題假設您已經在「BizTalk EDI 應用程式」中加入了自己應用程式的參考 (包含 EDI 結構描述、管線和協調流程)， 如果沒有，請參閱[如何將參考加入至 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。  
  
3.  以滑鼠右鍵按一下**Inbound_EDI**專案在 [方案總管] 中，然後選取**屬性**。  
  
4.  在主控台樹狀目錄中的**Inbound_EDI 屬性頁面**對話方塊中，選取**部署**和**伺服器**欄位確保，輸入您的電腦名稱。  
  
5.  在主控台樹狀目錄中，按一下**簽署**，然後選取 **簽署組件**。 如**選擇強式金鑰名稱檔**，選取\<**新增...** \>輸入**keyfile.snk**為**金鑰檔名稱**。 清除**保護我的密碼金鑰檔**，然後按一下 **確定**。  
  
6.  關閉**[Inbound_EDI 屬性頁面**] 對話方塊。  
  
### <a name="to-deploy-the-project"></a>若要部署此專案  
  
1.  在 [方案總管] 中，按兩下**X12_00401_850.xsd**結構描述。 確認它已開啟。  
  
2.  在 [方案總管] 中，按兩下**Inbound4010850_to_OrderFile.btm**對應。 確認它已開啟。  
  
    > [!NOTE]
    >  專案中的 Inbound4010850_to_OrderFile.btm 對應會將輸入 850 測試訊息中的資料，對應到已傳遞到 OrderSystem 資料夾 (\toOrderSystem) 的輸出 XML 檔案。  
  
3.  在 [方案總管] 中，以滑鼠右鍵按一下**Inbound_EDI**專案，然後選取**建置**建置專案。  
  
4.  在 [方案總管] 中，以滑鼠右鍵按一下**Inbound_EDI**專案，然後選取**部署**部署專案。  
  
5.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開 **BizTalk Server 管理**， **BizTalk 群組**，**應用程式**， \< **所有成品**\> ，然後選取 **資源**。 確認**Inbound_EDI**有列出組件。  
  
## <a name="next-steps"></a>後續步驟  
 您為您的組織設定合作對象與商務設定檔 (**OrderSystem**) 中所述，[步驟 3： 設定適用於您組織的合作對象與商務設定檔](../core/step-3-configure-a-party-and-business-profile-for-your-organization1.md)  
  
## <a name="see-also"></a>請參閱  
 [步驟 1：準備 EDI 介面開發人員教學課程](../core/step-1-prepare-for-the-edi-interface-developer-tutorial.md)