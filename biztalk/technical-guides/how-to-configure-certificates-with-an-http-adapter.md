---
title: "如何設定憑證與 HTTP 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc2f454f-22b5-4113-9a23-e00a816d5e48
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f74b0a88983ede90899dac908a5407f8406ec1e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-certificates-with-an-http-adapter"></a>如何設定憑證與 HTTP 配接器
HTTP 傳送配接器可以協助保護與接受或要求用戶端憑證的伺服器的連線。 若已指定用戶端憑證，則 HTTP 傳送配接器在與要求或接受用戶端憑證的伺服器連線時會使用憑證。 如果未指定用戶端憑證，且目的地伺服器需要用戶端憑證，寄件者未經過驗證，HTTP 傳送配接器就無法傳送訊息，並依照標準重試邏輯。  
  
 HTTP 傳送配接器會使用執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 程序的帳戶之個人存放區中的用戶端憑證。 憑證是由其指紋指定。 若 HTTP 傳送配接器因故無法載入憑證，則會擱置所傳送的訊息。  
  
 當使用 HTTP 配接器來傳送加密或簽署訊息時，設定 SSL 憑證指紋的傳送埠的 HTTP 傳輸屬性。 在這個屬性，指定要用於訊息驗證憑證的指紋。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行本主題中的程序，您必須登入的成員身分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。  
  
### <a name="to-configure-biztalk-server-to-send-messages-over-an-http-connection"></a>若要設定 BizTalk Server 透過 HTTP 連線傳送訊息  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，建立新的 HTTP 傳送埠，或開啟現有的 HTTP 傳送埠屬性。  
  
2.  按一下**設定**中的 傳輸 區段**傳送埠屬性** 對話方塊。  
  
3.  按一下**驗證**中**HTTP 傳輸屬性** 對話方塊。  
  
4.  在**驗證類型**，選取**匿名**，**基本**，**摘要**，或**Kerberos**。  
  
5.  如果驗證類型為**基本**或**摘要**，選取**不會使用單一登入**（在此情況下您必須指定使用者名稱和密碼），或選取**使用單一登入**（在此情況下您必須選取分支機構應用程式）。  
  
6.  在**SSL 用戶端憑證指紋**，輸入適當的憑證指紋。  
  
7.  按一下**確定**，然後按一下 **確定**一次。