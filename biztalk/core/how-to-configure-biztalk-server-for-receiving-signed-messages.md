---
title: 如何設定 BizTalk Server 來接收簽署的訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 48479532-24a9-41d9-a3b8-2a23f4e76457
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f805758bab1818f7f97fe1cb1bac1b0cf4b4316c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986847"
---
# <a name="how-to-configure-biztalk-server-for-receiving-signed-messages"></a>如何設定 BizTalk Server 來接收簽署的訊息
下列程序列出在設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 以接收加密訊息時，所必須遵循的步驟。  
  
-   若要建立管線來接收簽署的訊息  
  
-   若要設定接收簽署之訊息的接收位置  
  
## <a name="prerequisites"></a>必要條件  
 在設定之前先[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]來接收簽署的訊息，您必須執行中的步驟[如何安裝數位簽章憑證](../core/how-to-install-the-certificates-for-digital-signatures.md)。  
  
### <a name="to-create-a-pipeline-to-receive-signed-messages"></a>若要建立管線來接收簽署的訊息  
  
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
  
3. 建置和部署接收管線。  
  
### <a name="to-configure-the-receive-location-for-receiving-signed-messages"></a>若要設定接收簽署之訊息的接收位置  
  
1.  將您在上一個程序中所建立的 BizTalk 組件加入到 BizTalk 應用程式中，包括用來接收簽署之訊息的接收位置。 如需如何新增 BizTalk 組件的詳細資訊，請參閱[如何將 BizTalk 組件新增至應用程式](../core/how-to-add-a-biztalk-assembly-to-an-application.md)。  
  
2.  使用您在前述程序中建立的接收管線，在 BizTalk 應用程式中設定接收位置。 如需有關如何設定接收位置，請參閱 <<c0> [ 如何編輯接收位置屬性](../core/how-to-edit-the-properties-of-a-receive-location.md)。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 用於簽章訊息的憑證](../core/certificates-that-biztalk-server-uses-for-signed-messages.md)   
 [如何設定 BizTalk Server 來傳送簽署的訊息](../core/how-to-configure-biztalk-server-for-sending-signed-messages.md)   
 [驗證訊息的寄件者](../core/authenticating-the-sender-of-a-message.md)   
 [傳送和接收簽署的訊息](../core/sending-and-receiving-signed-messages.md)