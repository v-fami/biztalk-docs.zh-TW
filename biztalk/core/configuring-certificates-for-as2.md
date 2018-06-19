---
title: 設定 AS2 的憑證 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c160f294-7529-4e0a-876c-5827feaed067
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb2f9c22ddf41eec4133710de8a775bf8ff0b044
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22234654"
---
# <a name="configuring-certificates-for-as2"></a>設定 AS2 的憑證
為了使用加密和數位簽章來保護 AS2 資料傳輸，除了在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 適當設定 AS2 之外，您還必須安裝適當的憑證。 本主題會描述所需的憑證、如何設定憑證，以及憑證的常見問題。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
## <a name="certificates-required-for-as2-transport"></a>AS2 傳輸所需的憑證  
 為了保護 AS2 資料傳輸，您必須將適當憑證加入適當的憑證存放區，並使憑證與適當的 BizTalk 成品產生關聯。 下列憑證可用來保護 AS2 訊息：  
  
|憑證使用方式|憑證類型|管線元件|使用者內容|憑證存放區|定義於|  
|-----------------------|----------------------|------------------------|------------------|-----------------------|-------------------|  
|簽章 (輸出)|自有私密金鑰 (.pfx)|AS2 編碼器|與傳送處理常式相關聯之主控件執行個體所使用的帳戶|每個以主控件執行個體服務帳戶身分裝載 AS2 編碼器管線的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的目前使用者\個人存放區。|-   **憑證**頁面**群組內容** 對話方塊。 這是傳送已簽署的文件時所使用的預設簽署憑證。<br />-您可以覆寫預設的憑證設定，並針對不同的合作對象改用不同的憑證。 您可以藉由選取**覆寫群組簽章憑證**中**簽章憑證**單向協議索引標籤的頁面**協議屬性**對話方塊方塊中，並指定簽署憑證。 如果設定這個屬性，無論 AS2 訊息會解析為協議將會使用憑證簽署中提供**簽章憑證**頁面上，並不是由憑證提供做為 BizTalk 群組屬性的一部分。|  
|簽章驗證 (輸入)|交易夥伴的公開金鑰 (.cer)|AS2 解碼器|與接收處理常式相關聯之主控件執行個體所使用的帳戶|每個以主控件執行個體服務帳戶身分裝載 AS2 解碼器管線的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的本機電腦\其他人存放區。|**憑證**頁面**合作對象屬性**對話方塊**附註：** 用來驗證合作對象必須是唯一從用來驗證簽章憑證的簽章的憑證其他合作對象。|  
|加密 (輸出)|交易夥伴的公開金鑰 (.cer)|AS2 編碼器|與傳送處理常式相關聯之主控件執行個體所使用的帳戶|每個裝載 AS2 編碼器管線的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的本機電腦\其他人存放區|**憑證**頁面**傳送埠屬性**對話方塊|  
|解密 (輸入)|自有私密金鑰 (.pfx)|AS2 解碼器|與接收處理常式相關聯之主控件執行個體所使用的帳戶|每個以主控件執行個體服務帳戶身分裝載 AS2 解碼器管線的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的目前使用者\個人存放區。|「AS2 解碼器」會根據訊息中的憑證資訊來判斷憑證。<br /><br /> 對於 BizTalk MIME 解碼器，憑證必須位於**憑證**用來接收訊息的主控件的頁面。 這不一定適用於「AS2 解碼器」。|  
  
## <a name="certificate-signing-for-outgoing-messages"></a>外寄訊息的憑證簽署  
 外寄 AS2 訊息會以 BizTalk 群組屬性所定義的預設憑證簽署。 但在某些情況下，接收訊息的合作對象可能希望訊息是以他們提供的私人憑證來簽署，或希望傳送給他們的外寄訊息是以不同的憑證來簽署。 如果您選取 啟用此案例的簽署外寄訊息，使用其他憑證**覆寫群組簽章憑證**中**簽章憑證**頁面的單向協議索引標籤**協議屬性**對話方塊方塊中，並指定簽署憑證。 如果某個憑證指定在合作對象的 AS2 協議中，即會使用該憑證簽署外寄訊息。 如果未針對合作對象定義任何憑證，則會使用 BizTalk 群組屬性所指定的預設憑證。  
  
## <a name="adding-certificates-to-the-certificate-stores"></a>將憑證加入憑證存放區  
 如需詳細資訊，請參閱 < 顯示憑證管理主控台 > 一節[安裝 WCF 配接器的憑證](../core/installing-certificates-for-the-wcf-adapters.md)，並將[憑證精靈公用程式](../core/certificate-wizard-utility.md)主題。  
  
> [!IMPORTANT]
>  只有在針對其登入認證與主控件執行個體相關聯的使用者載入使用者設定檔時，個人憑證存放區才能用於訊息處理。 個人存放區是用於簽章和解密憑證 (使用者專屬的私密金鑰)。 預設會為內含式主控件執行個體載入使用者設定檔，但是不會為外掛式主控件執行個體載入使用者設定檔。 您可以讓應用程式針對外掛式主控件載入使用者設定檔。 或者，您也可以為內含式主控件執行個體和外掛式主控件執行個體使用相同的登入，以解決這個問題。  
  
## <a name="generating-certificates"></a>產生憑證  
 您可以向憑證授權單位 (CA) 取得憑證；但要求憑證的步驟可能會隨 CA 而不同。 在提交憑證要求之前，請先檢閱憑證授權單位的網站所提供的資訊。  
  
> [!IMPORTANT]
>  AS2 傳輸所使用的憑證必須有憑證預定使用方式的必要屬性。 簽署和簽章驗證，**金鑰使用方法**憑證的屬性必須是**數位簽章**。 加密和解密，**金鑰使用方法**憑證的屬性必須是**資料編密**或**金鑰編密**。 您可以確認**金鑰使用方法**屬性，請按兩下憑證，然後按一下**詳細資料**索引標籤中**憑證**對話方塊中，並檢查**金鑰使用方法**欄位。  
  
 您也可以使用「憑證服務」，在 Windows Server 2003 或 Windows Server 2000 中產生憑證，但您的合作對象可能只會將這些憑證用於測試目的，因為這些憑證是自我簽署的憑證，而非公用 CA 所簽署的憑證。 如需有關如何使用憑證服務來要求憑證的詳細資訊，請下載**Windows Server 2008 Active Directory 憑證服務逐步指南**從[Windows Server 2008 逐步指南](http://go.microsoft.com/fwlink/?LinkId=187916) ([http://go.microsoft.com/fwlink/?LinkId=187916](http://go.microsoft.com/fwlink/?LinkId=187916))。  
  
### <a name="to-configure-a-certificate-for-signing-outgoing-as2-messages"></a>若要設定用以簽署外寄 AS2 訊息的憑證  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**BizTalk 群組**節點，然後再按一下**屬性**。  
  
2.  在主控台樹狀目錄中的**群組內容**對話方塊中，按一下 **憑證**。  
  
3.  在**憑證**] 窗格中，按一下 [**瀏覽**，尋找您想要用於簽署的憑證，然後按一下**確定**。  
  
    > [!NOTE]
    >  您可以只輸入憑證指紋，而不需要輸入憑證的一般名稱。 您可以按兩下在 MMC 或檔案系統中，按一下 憑證存放區中的憑證來取得憑證指紋**詳細資料**索引標籤上，按一下**指紋**欄位，然後複製憑證指紋.  
  
4.  按一下 **[確定]**。  
  
### <a name="to-configure-a-certificate-for-signing-outgoing-as2-messages-for-a-specific-party"></a>若要為特定合作對象設定用以簽署外寄 AS2 訊息的憑證  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下 **合作對象**節點。 從**合作對象與商務設定檔**] 窗格中，從**協議**區段中以滑鼠右鍵按一下 [建立與特定合作對象交換訊息的協議，然後按一下**屬性**。  
  
2.  在單向協議索引標籤上，按一下 **簽章憑證**。  
  
3.  選取**覆寫群組簽章憑證**使用此頁面中的憑證簽署外寄 AS2 訊息和 MDN 核取方塊。  
  
4.  按一下**瀏覽**顯示**選取憑證**對話方塊中，選取要套用此合作對象所傳輸訊息的簽章憑證的位置。  
  
5.  **一般名稱**文字方塊會顯示所選憑證的描述。  
  
6.  **指紋**文字方塊會顯示憑證的指紋。 憑證指紋的格式為 HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH HHHH，其中 H 是十六進位數字 (0 到 9 的數字或是 A 到 F 的字母)。  
  
7.  按一下**移除憑證**若要移除選取的憑證。  
  
8.  按一下**確定**來驗證變更，然後關閉對話方塊。  
  
### <a name="to-configure-a-certificate-for-verifying-the-digital-signature-of-an-incoming-as2-messages"></a>若要設定憑證來確認內送 AS2 訊息的數位簽章  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，開啟**BizTalk 群組**節點，然後再按一下**合作對象**節點。  
  
2.  在**合作對象與商務設定檔**窗格中，以滑鼠右鍵按一下您將接收的合作對象簽章的訊息，然後按一下 **屬性**。  
  
3.  在主控台樹狀目錄中，按一下**憑證**。  
  
4.  在**憑證**] 窗格中，按一下 [**瀏覽**，找到您想要用來驗證數位簽章的憑證，然後按一下**確定**。  
  
    > [!NOTE]
    >  您可以只輸入憑證指紋，而不需要輸入憑證的一般名稱。 您可以按兩下在 MMC 或檔案系統中，按一下 憑證存放區中的憑證來取得憑證指紋**詳細資料**索引標籤上，按一下**指紋**欄位，然後複製憑證指紋.  
  
5.  按一下 **[確定]**。  
  
### <a name="to-configure-a-certificate-for-encrypting-an-outgoing-as2-messages"></a>若要設定憑證來加密外寄 AS2 訊息  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，開啟**BizTalk 群組**節點，開啟**應用程式** 節點，並開啟的節點**應用程式**包含傳送埠，您會在傳送加密的訊息。  
  
2.  開啟**傳送埠** 節點，以滑鼠右鍵按一下傳送埠，然後**屬性**。  
  
3.  在主控台樹狀目錄中，按一下**憑證**。  
  
4.  在**憑證** 窗格中，按一下 **瀏覽**，找不到您想要使用加密，然後按一下 憑證**確定**。  
  
    > [!NOTE]
    >  您可以只輸入憑證指紋，而不需要輸入憑證的一般名稱。 您可以按兩下在 MMC 或檔案系統中，按一下 憑證存放區中的憑證來取得憑證指紋**詳細資料**索引標籤上，按一下**指紋**欄位，然後複製憑證指紋.  
  
5.  按一下 **[確定]**。  
  
## <a name="see-also"></a>另請參閱  
 [AS2 安全性](../core/as2-security.md)   
 [設定簽署、 壓縮和加密 AS2 傳輸中](../core/configuring-signing-compression-and-encryption-in-as2-transport.md)   
 [AS2 方案架構](../core/as2-solution-architecture.md)   
 [WCF 配接器安裝憑證](../core/installing-certificates-for-the-wcf-adapters.md)