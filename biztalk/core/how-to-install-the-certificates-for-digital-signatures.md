---
title: "如何安裝數位簽章的憑證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 910ccd84-c022-46a5-a9de-b99046a480b8
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a755e59c7c916f3abe037513ddbc9e2a89892fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-install-the-certificates-for-digital-signatures"></a>如何安裝數位簽章的憑證
下列程序列出在安裝憑證來接收及傳送簽署的訊息時，所必須遵循的高層級步驟。  
  
-   在憑證存放區中安裝憑證以接收簽署的訊息  
  
-   在憑證存放區中安裝用於傳送簽署訊息的簽署憑證  
  
-   設定 BizTalk 群組來傳送簽署的訊息  
  
> [!NOTE]
>  您可以使用一個憑證來進行簽署及解密作業，或者也可以針對每一個功能使用一個憑證。  
  
> [!IMPORTANT]
>  您只能指定一個簽署憑證，讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 用來簽署所有輸出訊息。 換句話說，您無法根據訊息的傳送對象來使用不同的簽署憑證。  
  
### <a name="to-install-the-certificates-in-the-certificates-store-to-receive-signed-messages"></a>在憑證存放區中安裝憑證以接收簽署的訊息  
  
1.  夥伴 A 從憑證授權單位 (CA) 要求數位簽章的私密-公開金鑰組。  
  
2.  夥伴 A 將其數位簽章的公開金鑰傳送給您。  
  
3.  在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，登入有執行處理常式之主控件執行個體的伺服器 (此處理常式將會從夥伴 A 接收訊息)。安裝夥伴 A 公開金鑰憑證，以驗證其在「其他人」存放區中的簽章。 下圖顯示您安裝此憑證的憑證存放區。  
  
     ![接收安全訊息所需的憑證](../core/media/bpi-sp-msgsec-certmgmt-certstores-receive.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Receive")  
  
4.  在夥伴 A 中，安裝夥伴 A 私密金鑰憑證，在適當的存放區中簽署訊息 (如果夥伴 A 使用 [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)]、[!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] 或 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，請在要用於簽署傳送給 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的訊息的帳戶之個人存放區中，安裝私密金鑰)。  
  
### <a name="to-install-the-signing-certificates-for-sending-signed-messages-in-the-certificates-store"></a>在憑證存放區中安裝用於傳送簽署訊息的簽署憑證  
  
1.  您組織中的系統管理員從 CA 要求數位簽章的私密-公開金鑰組，以供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 使用。  
  
2.  系統管理員會將數位簽章的公開金鑰傳送給夥伴 A (及所有其他夥伴)。  
  
3.  在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，針對執行處理常式 (此處理常式將傳送訊息給夥伴 A) 的主控件執行個體，以其服務帳戶的身分登入。在該服務帳戶的個人存放區中，安裝簽署訊息所需的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 私密金鑰憑證。 下圖顯示您安裝此憑證的憑證存放區。  
  
     ![傳送安全訊息所需的憑證](../core/media/bpi-sp-msgsec-certmgmt-certstores-send.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Send")  
  
4.  在夥伴 A 中，安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 公開金鑰憑證，以便驗證其在適當存放區中的數位簽章 (如果夥伴 A 使用 [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)]、[!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] 或 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，請在「其他人」存放區中安裝公開金鑰)。  
  
### <a name="to-configure-the-biztalk-group-for-sending-signed-messages"></a>設定 BizTalk 群組來傳送簽署的訊息  
  
1.  按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  以滑鼠右鍵按一下**BizTalk 群組**，然後按一下 **屬性**。  
  
3.  在**群組內容**對話方塊中，按一下 **憑證**，按一下 **瀏覽**。  
  
4.  在**選取憑證**對話方塊中，選取您已安裝，簽署憑證，然後關閉所有對話方塊。  
  
## <a name="next-steps"></a>後續步驟  
 建立管線來接收簽署的訊息[如何設定接收簽署訊息的 BizTalk 伺服器](../core/how-to-configure-biztalk-server-for-receiving-signed-messages.md)。  
  
 您建立管線來傳送簽署的訊息[傳送簽署的訊息設定 BizTalk Server 如何](../core/how-to-configure-biztalk-server-for-sending-signed-messages.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 用於簽章訊息的憑證](../core/certificates-that-biztalk-server-uses-for-signed-messages.md)   
 [傳送及接收簽署的訊息](../core/sending-and-receiving-signed-messages.md)