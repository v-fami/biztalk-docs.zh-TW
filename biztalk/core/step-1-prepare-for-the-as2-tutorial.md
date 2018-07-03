---
title: 步驟 1： 準備 AS2 教學課程 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3421c33b-0ccd-4e9d-b1c3-b161278e4d98
caps.latest.revision: 39
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f394df645774752993064676345a371eb3135a0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003671"
---
# <a name="step-1-prepare-for-the-as2-tutorial"></a>步驟 1： 準備 AS2 教學課程
![步驟 11-1](../core/media/tut-step1-of-11.gif "Tut_Step1_of_11")  
  
 AS2 教學課程可在單一電腦上執行。 若要準備本教學課程，您必須安裝和設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中所述[BizTalk Server 2013 和 2013 R2 的安裝概觀](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5)一節。 您也必須依照本主題描述的方式新增對 BizTalk Server EDI 應用程式的參考。 AS2 教學課程所需的檔案位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial 資料夾中。  
  
> [!NOTE]
>  為了讓此教學課程順利運作，您必須同時針對內含式主控件執行個體和外掛式主控件執行個體使用相同的登入帳戶。  
  
> [!NOTE]
>  為進行此教學課程，此教學課程所用的 BizTalk Server 主控件必須標示為 32 位元。  
  
> [!NOTE]
>  此教學課程必須在 IIS 7.0 或 IIS 7.5 平台上執行，且應用程式集區的「啟用 32 位元應用程式」必須設定為 True。  
  
 AS2 教學課程的資料夾包括三個 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將在其中寫入測試輸出檔的資料夾 (EDI 內容、997 和 MDN)。 這些資料夾已經建立，但是您必須為 997 和 MDN 這兩個資料夾設定安全性權限 (請參閱下述程序)。  
  
 教學課程所需的資料夾和檔案如下：  
  
|資料夾\檔案|目的|  
|------------------|-------------|  
|\\_997ToFabrikam|這個空資料夾將接收 EDI 處理之後傳回的 997 通知訊息。 這個資料夾會模擬在 Fabrikam 合作對象中產生 EDI 訊息的應用程式。|  
|\\_EDIXMLToContoso|這個空資料夾將在 BizTalk Server 處理過 EDI 訊息之後接收 XML 內容檔。 這個資料夾會模擬商務營運應用程式，該應用程式為 EDI 內容的最終目的地。|  
|\\_MDNToFabrikam|這個空資料夾將接收 AS2 處理之後自 BizTalk Server 傳回的 MDN 訊息。 這個資料夾會在 Fabrikam 合作對象中模擬應用程式。|  
|\Fabrikam|這個資料夾包含 Default.aspx 檔，該檔案會將 997 儲存到 _997ToFabrikam 資料夾，以及將 MDN 儲存到 _MDNToFabrikam 資料夾。|  
|\Schemas|這個資料夾包含 X12_00401_864.xsd 結構描述，以及 BizTalk 用來處理 EDI 訊息的其他結構描述。 這個資料夾還包含您將建置和部署的 Schemas.btproj 專案，以便用來部署結構描述。|  
|\Sender|這個資料夾包含您將建置和編譯以建立 Sender.exe 的 Sender.csproj 專案，並且用來傳送 X12_00401_864.edi 測試訊息 (在 \AS2 Tutorial 資料夾中) 和傳回 MDN。|  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-set-the-security-permission-for-the-997-and-mdn-folders"></a>設定 997 和 MDN 資料夾的安全性權限  
  
1. 在 Windows 檔案總管中，移至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\\_997ToFabrikam 資料夾。 以滑鼠右鍵按一下\\_997ToFabrikam 資料夾，然後按一下**屬性**。  
  
2. 按一下 **安全性**索引標籤，然後再按一下**編輯**。 在 [**權限**] 對話方塊中，按一下**新增**。  
  
3. 在 **選取使用者、 電腦、 服務帳戶或群組**對話方塊中，在 物件名稱 窗格中，輸入`Everyone`，然後按一下**確定**。  
  
4. 選取**Everyone**中**群組或使用者名稱**方塊中，按一下核取方塊**撰寫**(下**允許**資料行) 中的**權限**窗格中，然後再按一下 **[確定]**。  
  
5. 按一下 [確定] 。  
  
6. 重複這些步驟\\_MDNToFabrikam 資料夾。  
  
#### <a name="to-mark-the-biztalk-server-host-as-32-bit"></a>將 BizTalk Server 主控件標示為 32 位元  
  
1. > [!NOTE]
   >  AS2 管線只能用在 32 位元處理程序中。 如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝在 64 位元的作業系統上，必須執行下列步驟以將主控件程序標示為僅限 32 位元。  
  
    選取 **開始**，選取**所有程式**，選取**Microsoft BizTalk Server**，然後選取**BizTalk Server 管理**。  
  
2. 在主控台樹狀目錄中，依序展開**BizTalk Server 管理]**、 [BizTalk 群組中，選取**平台設定**，然後選取**主機**。  
  
3. 在 [詳細資料] 窗格中，以滑鼠右鍵按一下您想要使用本教學課程，然後選取內含式主控件**屬性**。  
  
4. 中**主機內容**對話方塊的 **一般**索引標籤上，選取**僅 32 位元**，然後按一下**確定**。  
  
5. 針對外掛式主控件重複步驟 3 到 4。  
  
   如果 BizTalk Server 安裝於 64 位元作業系統上，使用 32 位元的 BizTalk 主控件程序時，您也必須將 IIS 設定為以 32 位元模式執行。 設定 IIS 的指示會顯示內[步驟 5： 設定交易夥伴網頁](../core/step-5-configure-the-trading-partner-web-pages.md)IIS 可讓您設定上的 32 位元工作者處理序中，每個應用程式集區為基礎。  
  
#### <a name="to-add-reference-to-the-biztalk-edi-application"></a>若要加入 BizTalk EDI 應用程式的參考  
  
1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，底下**應用程式**] 節點，以滑鼠右鍵按一下您想要使用 edi，例如 [BizTalk Application 1 的應用程式。 指向**新增**，然後按一下 參考。  
  
2. 在 **新增應用程式參考**對話方塊中，選取**BizTalk EDI 應用程式**，然後按一下**確定**。  
  
## <a name="next-steps"></a>後續步驟  
 您將部署範例 X12 結構描述中所述[步驟 2： 建立和部署範例 X12 結構描述](../core/step-2-create-and-deploy-the-sample-x12-schema.md)  
  
## <a name="see-also"></a>另請參閱  
 [教學課程 3: AS2 教學課程](../core/tutorial-3-as2-tutorial.md)