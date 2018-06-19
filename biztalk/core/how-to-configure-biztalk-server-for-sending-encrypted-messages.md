---
title: 如何設定 BizTalk Server 來傳送加密訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb751d7c-49cd-46f0-9630-254cf06c497e
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0b3ef721c263c892690b9ac5b7d2dd15155f0dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248870"
---
# <a name="how-to-configure-biztalk-server-for-sending-encrypted-messages"></a>如何設定 BizTalk Server 來傳送加密的訊息
下列程序列出在設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 來傳送加密的訊息時，所必須遵循的步驟。  
  
-   建立管線來傳送加密的訊息  
  
-   設定傳送埠來傳送加密的訊息  
  
## <a name="prerequisites"></a>必要條件  
 然後再設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]s 傳送加密的訊息，您必須執行中的步驟[如何安裝加密訊息的憑證](../core/how-to-install-the-certificates-for-encrypted-messages.md)。  
  
### <a name="to-create-a-pipeline-to-send-encrypted-messages"></a>建立管線來傳送加密的訊息  
  
1.  在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的 [方案總管] 中，選取您要在其中建立管線的專案。  
  
    1.  在**檔案**功能表上，按一下 **加入新項目**。  
  
    2.  在**加入新項目**對話方塊方塊中，展開 BizTalk 專案項目，按一下**管線檔案**，然後按一下 **傳送管線**範本。  
  
    3.  在**名稱**欄位中，輸入管線的名稱。  
  
    4.  按一下 **[加入]**。  
  
         新管線隨即出現在 [方案總管] 中。  
  
2.  將 MIME/SMIME 編碼器管線元件拖曳至接收管線的「編碼」階段中。  
  
     ![MIME &#47;SMIME 編碼器管線元件](../core/media/bts-dev-mimesmimeencoder.gif "BTS_DEV_MIMESMIMEEncoder")  
  
    -   在 [屬性] 視窗中設定 MIME/SMIME 編碼器管線元件**啟用加密**屬性`True`。 如需有關**啟用加密**屬性，請參閱[如何設定 MIME SMIME 編碼器管線元件](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md)。  
  
    > [!NOTE]
    >  將管線部署至 BizTalk 群組之後，您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台來設定管線元件屬性。 如需詳細資訊，請參閱[的傳送埠中設定每個執行個體管線屬性如何](../core/how-to-configure-per-instance-pipeline-properties-for-a-send-port.md)。  
  
    > [!NOTE]
    >  MIME/SMIME 編碼器管線元件會執行加密及數位簽章 (當設定為執行這兩項功能時)。 因此，如果您要設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 來傳送已加密及已簽署的訊息，可以使用相同的傳送管線。 也就是說，您不需要針對加密和數位簽章建立個別的管線。  
  
3.  建置和部署傳送管線。  
  
### <a name="to-configure-the-send-port-for-sending-encrypted-messages"></a>設定傳送埠來傳送加密的訊息  
  
1.  將您在上一個程序中所建立的 BizTalk 組件加入到 BizTalk 應用程式中，包括用來傳送加密訊息的傳送埠。 如需如何新增 BizTalk 組件的詳細資訊，請參閱[如何將 BizTalk 組件新增至應用程式](../core/how-to-add-a-biztalk-assembly-to-an-application.md)。  
  
2.  您在先前的程序中建立的傳送管線的 BizTalk 應用程式中設定的傳送埠，然後將指派您在安裝的加密憑證[如何安裝的憑證加密的訊息](../core/how-to-install-the-certificates-for-encrypted-messages.md). 如需如何設定傳送埠的詳細資訊，請參閱[如何指派憑證給傳送埠](../core/how-to-assign-a-certificate-to-a-send-port.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何設定 BizTalk Server 來接收加密的訊息](../core/how-to-configure-biztalk-server-for-receiving-encrypted-messages.md)   
 [BizTalk Server 會使用加密訊息的憑證](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md)   
 [傳送和接收加密的訊息](../core/sending-and-receiving-encrypted-messages.md)