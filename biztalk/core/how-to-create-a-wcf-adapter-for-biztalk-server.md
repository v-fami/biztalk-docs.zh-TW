---
title: 如何建立 BizTalk Server WCF 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7ddaeb72-d263-4291-bd79-485fc736e6e7
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ebe1bbb9282db88f1b4370cea4b59ff4fcbfe6a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249342"
---
# <a name="how-to-create-a-wcf-adapter-for-biztalk-server"></a>如何建立 BizTalk Server 的 WCF 配接器
建立 BizTalk [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] 配接器可分為三個部分。  
  
-   使用「BizTalk [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 服務發佈精靈」建立 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Web 服務。 如需使用 「 BizTalk[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務發佈精靈 」，請參閱[發佈 WCF 服務](../core/publishing-wcf-services.md)。  
  
-   使用「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台」來設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收與傳送位置以及連接埠。 如需如何執行此動作的範例，請參閱[如何設定接收和傳送位置以及連接埠的 BAM WCF 攔截](../core/how-to-configure-receive-and-send-locations-and-ports-for-bam-wcf-interception.md)。  
  
-   如果您是在 IIS 中裝載方案，您必須使用「IIS 管理員」設定 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Web 服務。  
  
    -   您必須授與權限給應用程式集區使用者。 若要這樣做，請參閱[IIS 模擬的安全性考量](../core/security-considerations-for-iis-impersonation.md)。  
  
    -   您必須依照下列程序所述，設定應用程式的目錄安全性。  
  
## <a name="setting-the-directory-security"></a>設定目錄安全性  
 確定 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 服務的「目錄安全性存取控制」允許匿名存取，這樣可簡化應用程式的存取。  
  
 例如，您的應用程式名為 MyBizTalkService3，而且 [預設的網站] 中有 MyBizTalkService3，則請遵循這個程序來設定存取控制。  
  
#### <a name="to-set-the-access-control-in-windows-server-2008"></a>若要在 Windows Server 2008 中設定存取控制  
  
1.  按一下**啟動**，按一下 **所有程式**，依序展開**系統管理工具**，然後按一下 **網際網路資訊服務 (IIS) 管理員**.  
  
2.  在網際網路資訊服務 (IIS) 管理員 視窗中，展開您的伺服器名稱，再展開**網站**，依序展開**Internet Information Services**，然後展開**Default Web Site**.  
  
3.  以滑鼠右鍵按一下**MyBizTalkService3**，然後按一下 **編輯權限**。  
  
4.  在**安全性** 索引標籤**MyBizTalkService3 屬性**對話方塊中，按一下 **編輯**。  
  
5.  在**MyBizTalkService3 的權限**對話方塊中，按一下 **新增**。  
  
6.  在**選取使用者、 電腦或群組**] 對話方塊中，輸入`anonymous logon`，然後按一下 [**確定**。  
  
7.  選取**ANONYMOUS LOGON**中**群組或使用者名稱**區段中，選取**讀取 & 執行**中**匿名登入的權限**區段，然後再按一下**確定**。  
  
8.  按一下**確定**關閉 **[MyBizTalkService3 屬性**] 對話方塊。  
  
 若要確認服務已正確設定，以滑鼠右鍵按一下服務，然後**瀏覽**。  
  
 如果服務的設定正確，您所看到的畫面會與以下相似。  
  
 ![BizTalkServiceInstance 服務畫面](../core/media/ff0e4ba0-59e7-47d9-a252-2859179f5645.gif "ff0e4ba0-59e7-47d9-a252-2859179f5645")  
  
## <a name="see-also"></a>另請參閱  
 [設定 WCF 配接器攔截 BAM 資料](../core/configuring-the-wcf-adapter-to-intercept-bam-data.md)