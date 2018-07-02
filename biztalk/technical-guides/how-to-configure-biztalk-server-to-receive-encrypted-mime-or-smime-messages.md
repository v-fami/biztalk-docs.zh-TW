---
title: 如何設定 BizTalk Server 接收加密的 MIME 或 SMIME 訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d72002c8-6bd8-458f-8149-1c0c4cbbb682
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ffb471a5c40ed61be45f40e842cb755023aa26b5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968079"
---
# <a name="how-to-configure-biztalk-server-to-receive-encrypted-mime-or-smime-messages"></a>如何設定 BizTalk Server 接收加密的 MIME 或 SMIME 訊息
本主題描述如何設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]以使用憑證來接收加密的 MIME/SMIME 訊息。 下列程序也適用於透過 AS2 傳輸設定的加密訊息接收。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行本主題中的程序，您必須登入的成員身分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。  
  
### <a name="to-configure-biztalk-server-to-receive-encrypted-messages"></a>若要設定 BizTalk Server 接收加密的訊息  
  
1. 建立管線來接收加密的訊息，如下所示：  
  
   > [!NOTE]
   >  設定 AS2 傳輸來接收加密的訊息，因為 AS2Receive 和 AS2EdiReceive 管線包含在 BizTalk Server 中提供這個函式時，不需要此步驟。  
   > 
   > [!NOTE]
   >  MIME/SMIME 解碼器管線元件會執行解密及數位簽章驗證 (當設定為執行這兩項功能時)。 因此，如果您要設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 來接收加密及簽署的訊息，您可以使用相同的接收管線。 換句話說，您不需要針對解密和數位簽章驗證建立個別的管線。  
  
   1. 建立接收管線，然後將 MIME/SMIME 解碼器管線元件拖曳至管線的 「 解碼 」 階段。  
  
   2. 在 [**屬性**] 視窗中，設定 MIME/SMIME 解碼器管線元件屬性。  
  
      > [!NOTE]
      >  設定 MIME/SMIME 解碼器管線元件屬性包含檢查撤銷清單 屬性設為 True，如果您想要檢查憑證撤銷清單之憑證的傳送者用來簽署訊息會傳送至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. 停用此選項會提高元件的效能。 與憑證相關聯的憑證撤銷清單會從適當的憑證服務的網站下載。 如果[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]無法連線到遠端網站上，管線中，訊息就會失敗。  
      > 
      > [!NOTE]
      >  當您使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台將此管線部署到 BizTalk 群組後，您可以為接收位置設定管線屬性。 您可以針對 BizTalk 群組中的每一個接收位置設定不同的管線屬性。  
  
   3. 建置和部署接收管線。  
  
2. 設定接收位置來接收加密的訊息，如下所示：  
  
   1. 新增您建立的資料包含 BizTalk 應用程式包括的接收位置來接收加密的訊息的接收管線的 BizTalk 組件。  
  
      > [!NOTE]
      >  設定 AS2 傳輸來接收加密的訊息，因為在 「 BizTalk EDI 應用程式中包含 AS2Receive 和 AS2EdiReceive 管線時，不需要此步驟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
   2. 您在上一個步驟中建立的接收管線的 BizTalk 應用程式中設定接收位置。  
  
3. 設定用來主控件的接收處理常式為解密的憑證、 接收位置，如下所示：  
  
   1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下 BizTalk 也就是裝載的處理常式來接收加密的訊息，然後按一下**屬性**。  
  
      > [!NOTE]
      >  此程序不適用於隨附的 AS2 傳輸[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 它適用於 BizTalk MIME 解碼器，而不是 「 AS2 解碼器。 AS2 解碼器會決定訊息中的憑證資訊為基礎的憑證。  
  
   2. 在 **主機內容** 對話方塊中，按一下**憑證**，然後按一下 **瀏覽**。  
  
      > [!NOTE]
      >  上述程序可讓您設定您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境，因此，只有特定主機可以接收和處理特定訊息。 當您設定要用於訊息解碼和解密，憑證的指紋的主控件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]裝載 MessageBox 資料庫中建立的應用程式屬性。 保護接收的訊息，並解密使用此指紋僅路由傳送至此網站與其他已具有此指紋的主機。  
  
   3. 在 [**選取憑證**] 對話方塊中，選取的解密憑證，您已安裝，然後再關閉所有對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定憑證以 MIME 或 SMIME 訊息](../technical-guides/configuring-certificates-for-mime-or-smime-messages.md)