---
title: 如何設定 BizTalk Server 進行合作對象解析 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ac330b9-3498-4c98-a6e8-d2c02cd641dd
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d6fc4f0f0dc61b111060aebb26b8dccfc32ec15
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991055"
---
# <a name="how-to-configure-biztalk-server-for-party-resolution"></a>如何設定 BizTalk Server 進行合作對象解析
若要設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 進行合作對象解析，您必須遵循下列程序所列的步驟。  
  
-   在憑證存放區中安裝憑證以接收簽署的訊息  
  
-   建立代表夥伴的合作對象  
  
-   使用憑證建立合作對象解析的管線  
  
-   使用憑證設定合作對象解析的接收位置  
  
### <a name="to-install-the-certificates-in-the-certificates-store-to-receive-signed-messages"></a>在憑證存放區中安裝憑證以接收簽署的訊息  
  
1. 夥伴 A 從憑證授權單位 (CA) 要求數位簽章的私密-公開金鑰組。  
  
2. 夥伴 A 將其數位簽章的公開金鑰傳送給您。  
  
3. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，登入有執行處理常式之主控件執行個體的伺服器 (此處理常式將會從夥伴 A 接收訊息)。安裝夥伴 A 公開金鑰憑證，以驗證其在「其他人」存放區中的簽章。 下圖顯示您安裝此憑證的憑證存放區。  
  
    ![接收安全訊息所需的憑證](../core/media/bpi-sp-msgsec-certmgmt-certstores-receive.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Receive")  
  
4. 在夥伴 A 中，安裝夥伴 A 私密金鑰憑證，在適當的存放區中簽署訊息 (如果夥伴 A 使用 [!INCLUDE[btsWin2kSvr](../includes/btswin2ksvr-md.md)]、[!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] 或 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，請在要用於簽署傳送給 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的訊息的帳戶之個人存放區中，安裝私密金鑰)。  
  
   > [!NOTE]
   >  此步驟會完全相同 」 步驟來接收簽署的訊息的憑證存放區中安裝憑證 」 中[如何安裝數位簽章憑證](../core/how-to-install-the-certificates-for-digital-signatures.md)。  
  
### <a name="to-create-a-party-to-represent-your-partner"></a>建立代表夥伴的合作對象  
  
1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台中，建立合作對象夥伴 a。如需如何建立合作對象的詳細資訊，請參閱[如何建立合作對象](http://msdn.microsoft.com/library/f6feca1d-bc83-4fb6-981d-26c9e0d53044)。  
  
2. 在 **憑證**屬性，選取公開金鑰簽署憑證，用來識別此合作對象，夥伴 a。  
  
### <a name="to-create-a-pipeline-for-party-resolution-using-certificates"></a>使用憑證建立合作對象解析的管線  
  
1. 在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 的 [方案總管] 中，選取您要在其中建立管線的專案。  
  
   1.  在 **檔案**功能表上，按一下**加入新項目**。  
  
   2.  在 **加入新項目**對話方塊方塊中，展開 BizTalk 專案項目，按一下**管線檔案**，然後按一下 **接收管線**範本。  
  
   3.  在 **名稱**欄位中，輸入管線的名稱。  
  
   4.  按一下 **[加入]**。  
  
        新管線隨即出現在 [方案總管] 中。  
  
2. 將 MIME/SMIME 解碼器管線元件拖曳**解碼**接收管線階段。  
  
    ![MIME&#47;SMIME 解碼器管線元件](../core/media/bts-dev-mimesmimedecoder.gif "BTS_DEV_MIMESMIMEDecoder")  
  
   -   設定 MIME/SMIME 解碼器管線元件屬性中的**屬性**視窗。 如需 MIME/SMIME 解碼器的詳細資訊，請參閱[如何設定 MIME SMIME 解碼器管線元件](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md)。  
  
   > [!NOTE]
   >  當您使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台將此管線部署到 BizTalk 群組後，您可以為接收位置設定管線屬性。 您可以針對 BizTalk 群組中的每一個接收位置設定不同的管線屬性。 如需詳細資訊，請參閱 <<c0> [ 如何設定接收位置的每個執行個體管線屬性](../core/how-to-configure-per-instance-pipeline-properties-for-a-receive-location.md)。  
   > 
   > [!NOTE]
   >  MIME/SMIME 解碼器管線元件會執行解密及數位簽章驗證 (當設定為執行這兩項功能時)。 因此，如果您要設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 來接收加密及簽署的訊息，您可以使用相同的接收管線。 換句話說，您不需要針對解密和數位簽章驗證建立個別的管線。  
  
3. 將合作對象解析管線元件拖曳**解析合作對象**接收管線階段。 如需 「 合作對象解析 」 管線元件的詳細資訊，請參閱[如何設定合作對象解析管線元件](../core/how-to-configure-the-party-resolution-pipeline-component.md)。  
  
   > [!NOTE]
   >  您也可以使用預設的 XMLReceive 管線，而不需要建立新的接收管線。 XMLReceive 管線會執行合作對象解析元件，它會解析為合作對象識別碼。 可能的憑證 請注意，XMLReceive 管線有空的解碼階段，而且您因此無法將它用於接收加密的訊息或驗證數位簽章。  
  
   -   在 屬性 視窗中，設定 合作對象解析管線屬性**依憑證解析合作對象**至`True`。  
  
4. 建置和部署接收管線。  
  
### <a name="to-configure-the-receive-location-for-party-resolution-using-certificates"></a>使用憑證設定合作對象解析的接收位置  
  
1.  將您在上一個程序中所建立的 BizTalk 組件加入到 BizTalk 應用程式中，包括用來接收簽署之訊息的接收位置。 如需如何新增 BizTalk 組件的詳細資訊，請參閱[如何將 BizTalk 組件新增至應用程式](../core/how-to-add-a-biztalk-assembly-to-an-application.md)。  
  
2.  使用您在前述程序中建立的接收管線，在 BizTalk 應用程式中設定接收位置。 如需有關如何設定接收位置，請參閱 <<c0> [ 如何編輯接收位置屬性](../core/how-to-edit-the-properties-of-a-receive-location.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何設定 BizTalk Server 來接收簽署的訊息](../core/how-to-configure-biztalk-server-for-receiving-signed-messages.md)   
 [BizTalk Server 用於簽章訊息的憑證](../core/certificates-that-biztalk-server-uses-for-signed-messages.md)   
 [輸入訊息驗證](../core/inbound-message-authentication.md)   
 [使用憑證進行合作對象解析](../core/using-certificates-for-party-resolution.md)