---
title: "如何安裝加密訊息的憑證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e11fdb81-041c-4ba6-849d-d511ead0e8be
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b1df2e9e5bf42a215420dac155fafac8e92ae21
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-install-the-certificates-for-encrypted-messages"></a>如何安裝加密訊息的憑證
下列程序列出在安裝憑證來接收及傳送加密訊息時，所必須遵循的高層級步驟。  
  
-   在憑證存放區中安裝用於解密的憑證  
  
-   在憑證存放區中安裝用於加密的憑證  
  
-   設定用於接收加密訊息的 BizTalk 主控件  
  
> [!NOTE]
>  您可以使用一個憑證來進行簽署及解密作業，或者也可以針對每一個功能使用一個憑證。  
  
### <a name="to-install-the-decryption-certificates-in-the-certificates-store"></a>在憑證存放區中安裝解密憑證  
  
1.  您組織中的系統管理員向憑證授權單位 (CA) 要求加密的私密-公開金鑰組，以供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 使用。  
  
2.  系統管理員將加密的公開金鑰傳送給夥伴 A。  
  
3.  在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，針對執行處理常式 (此處理常式將從夥伴 A 接收訊息) 的主控件執行個體，以其服務帳戶的身分登入。安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 私密金鑰憑證，以便為此服務帳戶之個人存放區中的訊息解密。 下圖顯示您安裝此憑證的憑證存放區。  
  
     ![接收安全訊息所需的憑證](../core/media/bpi-sp-msgsec-certmgmt-certstores-receive.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Receive")  
  
4.  在夥伴 A 中，安裝 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 公開金鑰憑證，以便在適當的存放區中加密傳送給夥伴 A 的訊息 (如果夥伴 A 使用 [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)]、[!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] 或 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，請在「其他人」存放區中安裝公開金鑰)。  
  
### <a name="to-install-the-encryption-certificates-in-the-certificates-store"></a>在憑證存放區中安裝加密憑證  
  
1.  夥伴 A 從 CA 要求加密的私密-公開金鑰組。  
  
2.  夥伴 A 會在適當的存放區中安裝解密訊息的私密金鑰憑證 (如果夥伴 A 使用 [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)]、[!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] 或 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，請在個人憑證存放區中安裝私密金鑰)。  
  
3.  夥伴 A 會把公開金鑰傳送給您，這個金鑰是用於加密傳送給夥伴 A 的訊息。  
  
4.  在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，登入有執行處理常式之主控件執行個體的伺服器 (此處理常式將會傳送訊息給夥伴 A)。安裝夥伴 A 公開金鑰憑證，以便在「其他人」存放區中加密傳送給夥伴 A 的訊息。 下圖顯示您安裝此憑證的憑證存放區。  
  
     ![傳送安全訊息所需的憑證](../core/media/bpi-sp-msgsec-certmgmt-certstores-send.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Send")  
  
### <a name="to-configure-biztalk-hosts-for-receiving-encrypted-messages"></a>設定用於接收加密訊息的 BizTalk 主控件  
  
1.  按一下**啟動**，指向 **所有程式**，指向  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。  
  
2.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，展開**平台設定**，依序展開**主機**。  
  
    1.  在右窗格中，以滑鼠右鍵按一下 BizTalk 主控件的處理常式來接收加密的訊息，然後**屬性**。  
  
    2.  在**主控件屬性**對話方塊中，按一下 **憑證**，按一下 **瀏覽**。  
  
    3.  在**選取憑證**對話方塊中，選取您已安裝，解密憑證，然後關閉所有對話方塊。  
  
        > [!NOTE]
        >  如需詳細資訊，請參閱[如何修改主機內容](../core/how-to-modify-host-properties.md)。  
  
## <a name="next-steps"></a>後續步驟  
 建立管線來接收加密的訊息[如何設定 BizTalk Server 接收加密訊息](../core/how-to-configure-biztalk-server-for-receiving-encrypted-messages.md)  
  
 您建立管線來傳送加密的訊息[如何設定 BizTalk Server 傳送加密訊息](../core/how-to-configure-biztalk-server-for-sending-encrypted-messages.md)  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 會使用加密訊息的憑證](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md)   
 [傳送和接收加密的訊息](../core/sending-and-receiving-encrypted-messages.md)