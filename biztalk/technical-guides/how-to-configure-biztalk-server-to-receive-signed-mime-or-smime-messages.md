---
title: "如何設定 BizTalk Server 來接收簽署 MIME 或 SMIME 訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50570257-7bb6-4ede-9026-873eefd06483
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88487fb96c89b8a611ab591223fa1820f70de1cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-biztalk-server-to-receive-signed-mime-or-smime-messages"></a>如何設定 BizTalk Server 來接收簽署 MIME 或 SMIME 訊息
本主題描述如何設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]以使用憑證來接收簽署的 MIME/SMIME 訊息。 下列程序也適用於透過 AS2 傳輸設定接收簽署的訊息。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行本主題中的程序，您必須登入的成員身分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。  
  
### <a name="to-configure-biztalk-server-to-receive-signed-messages"></a>若要設定 BizTalk Server 來接收簽署的訊息  
  
1.  建立管線來接收簽署的訊息，如下所示：  
  
    > [!NOTE]
    >  設定 AS2 傳輸接收簽署的訊息，因為 AS2Receive 和 AS2EdiReceive 管線，在中時，不需要這個步驟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]做這個函式。  
  
    1.  建立接收管線，然後將 MIME/SMIME 解碼器管線元件拖曳至接收管線的 「 解碼 」 階段。  
  
    2.  在**屬性**視窗中，設定 MIME/SMIME 解碼器管線元件屬性。  
  
        > [!NOTE]
        >  當您使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台將此管線部署到 BizTalk 群組後，您可以為接收位置設定管線屬性。 您可以針對 BizTalk 群組中的每一個接收位置設定不同的管線屬性。  
  
    3.  建置和部署接收管線。  
  
2.  設定接收位置來接收簽署的訊息，如下所示：  
  
    1.  將您建立包含 BizTalk 應用程式包括的接收位置來接收簽署的訊息的接收管線的 BizTalk 組件。  
  
        > [!NOTE]
        >  設定 AS2 傳輸接收簽署的訊息，因為在 「 BizTalk EDI 應用程式中包含 AS2Receive 和 AS2EdiReceive 管線時，不需要這個步驟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
    2.  您在上一個程序中建立的接收管線的 BizTalk 應用程式中設定接收位置。  
  
3.  設定合作對象的憑證來接收簽署的訊息，如下所示：  
  
    -   開啟**合作對象屬性**對話方塊在 BizTalk Server 管理主控台中，按一下**憑證**索引標籤上，按一下 **瀏覽**，選取適當的憑證，然後按一下 **確定**。  
  
        > [!NOTE]
        >  驗證某個合作對象的簽章時所使用的憑證，必須不同於驗證其他合作對象的簽章時所使用的憑證。  
  
## <a name="see-also"></a>另請參閱  
 [設定 MIME 或 SMIME 訊息的憑證](../technical-guides/configuring-certificates-for-mime-or-smime-messages.md)