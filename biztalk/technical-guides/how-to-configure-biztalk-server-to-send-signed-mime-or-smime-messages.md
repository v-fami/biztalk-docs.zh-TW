---
title: 如何設定 BizTalk Server 來傳送簽署的 MIME 或 SMIME 訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba42463b-2c12-4329-919e-aca427d14eee
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e1f3e01179f26c825480bb3a7de8d13b8539129
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005463"
---
# <a name="how-to-configure-biztalk-server-to-send-signed-mime-or-smime-messages"></a>如何設定 BizTalk Server 來傳送簽署的 MIME 或 SMIME 訊息
本主題描述如何設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]以使用憑證來傳送簽署的 MIME/SMIME 訊息。 下列程序也適用於設定透過 AS2 傳輸的已簽署的訊息傳送。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行本主題中的程序，您必須登入的成員身分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。  
  
### <a name="to-configure-biztalk-server-to-send-signed-messages"></a>若要設定 BizTalk Server 來傳送簽署的訊息  
  
1. 建立管線來傳送簽署的訊息，如下所示：  
  
   > [!NOTE]
   >  設定 AS2 傳輸來傳送簽署的訊息，AS2EdiSend 和 AS2Send 管線，因為包含在時，不需要此步驟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]做這個函式。  
  
   1. 建立傳送管線，然後將 MIME/SMIME 編碼器管線元件拖曳至管線的 「 編碼 」 階段。  
  
   2. 在 [**屬性**] 視窗中，設定 MIME/SMIME 編碼器管線元件的簽章類型內容 ClearSign 或 [blobsign]。  
  
      > [!NOTE]
      >  如果您也會使用加密，您可以只選取 [blobsign]。  
      > 
      > [!NOTE]
      >  將管線部署至 BizTalk 群組之後，您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台來設定管線元件屬性。  
      > 
      > [!NOTE]
      >  MIME/SMIME 編碼器管線元件會執行加密及數位簽章 (當設定為執行這兩項功能時)。 因此，如果您要設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 來傳送已加密及已簽署的訊息，可以使用相同的傳送管線。 也就是說，您不需要針對加密和數位簽章建立個別的管線。  
  
   3. 建置和部署傳送管線。  
  
2. 設定傳送埠來傳送簽署的訊息，如下所示：  
  
   1. 新增您建立的資料包含 BizTalk 應用程式，其中包含傳送埠來傳送簽署的訊息的傳送管線的 BizTalk 組件。  
  
      > [!NOTE]
      >  設定 AS2 傳輸來傳送簽署訊息，因為在 「 BizTalk EDI 應用程式中包含 AS2Send 和 AS2EdiSend 管線時，不需要此步驟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
   2. 您在上一個程序中建立的傳送管線的 BizTalk 應用程式中設定的傳送埠。  
  
3. 設定群組的憑證來傳送簽署的訊息，如下所示：  
  
   1. 設定 BizTalk 群組的簽章的憑證，您藉由展開 BizTalk 群組中的安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下  **屬性**。  
  
   2. 按一下 [憑證] 索引標籤，再按一下**瀏覽**，選取適當的憑證，然後按一下**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [設定憑證以 MIME 或 SMIME 訊息](../technical-guides/configuring-certificates-for-mime-or-smime-messages.md)