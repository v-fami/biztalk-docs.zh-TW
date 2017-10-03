---
title: "如何設定 BizTalk Server 來傳送簽署 MIME 或 SMIME 訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba42463b-2c12-4329-919e-aca427d14eee
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 623e8e6349494ce1d15089093b1620b4da76adbb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-biztalk-server-to-send-signed-mime-or-smime-messages"></a>如何設定 BizTalk Server 來傳送簽署 MIME 或 SMIME 訊息
本主題描述如何設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]以使用憑證來傳送簽署的 MIME/SMIME 訊息。 下列程序也適用於設定透過 AS2 傳輸的簽章訊息傳送。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行本主題中的程序，您必須登入的成員身分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。  
  
### <a name="to-configure-biztalk-server-to-send-signed-messages"></a>若要設定 BizTalk Server 來傳送簽署的訊息  
  
1.  建立管線來傳送簽署的訊息，如下所示：  
  
    > [!NOTE]
    >  設定 AS2 傳輸來傳送簽署的訊息的 AS2Send 和 AS2EdiSend 管線，因為包含在這個步驟並非必要[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]做這個函式。  
  
    1.  建立傳送管線，然後將 MIME/SMIME 編碼器管線元件拖曳到管線的 「 編碼 」 階段。  
  
    2.  在**屬性**視窗中，設定 MIME/SMIME 編碼器管線元件簽章類型屬性 ClearSign 或 BlobSign。  
  
        > [!NOTE]
        >  如果您也要使用加密，您可以只選取 BlobSign。  
  
        > [!NOTE]
        >  將管線部署至 BizTalk 群組之後，您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台來設定管線元件屬性。  
  
        > [!NOTE]
        >  MIME/SMIME 編碼器管線元件會執行加密及數位簽章 (當設定為執行這兩項功能時)。 因此，如果您要設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 來傳送已加密及已簽署的訊息，可以使用相同的傳送管線。 也就是說，您不需要針對加密和數位簽章建立個別的管線。  
  
    3.  建置和部署傳送管線。  
  
2.  設定傳送埠來傳送簽署的訊息，如下所示：  
  
    1.  將您建立包含 BizTalk 應用程式，其中包含傳送埠來傳送簽署的訊息的傳送管線的 BizTalk 組件。  
  
        > [!NOTE]
        >  設定 AS2 傳輸來傳送簽署訊息，因為在 「 BizTalk EDI 應用程式中包含的 AS2Send 和 AS2EdiSend 管線時，不需要這個步驟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
    2.  您在上一個程序中建立的傳送管線的 BizTalk 應用程式中設定的傳送埠。  
  
3.  設定群組的憑證來傳送簽署的訊息，如下所示：  
  
    1.  設定 BizTalk 群組，展開 BizTalk 群組，在您安裝的簽章憑證[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下**屬性**。  
  
    2.  按一下 憑證 索引標籤，再按一下**瀏覽**選取適當的憑證，然後按一下 **確定**。  
  
## <a name="see-also"></a>另請參閱  
 [設定 MIME 或 SMIME 訊息的憑證](../technical-guides/configuring-certificates-for-mime-or-smime-messages.md)