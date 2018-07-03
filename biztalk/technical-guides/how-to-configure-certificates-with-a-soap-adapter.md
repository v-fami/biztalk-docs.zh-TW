---
title: 如何設定 SOAP 配接器的憑證 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 20ee05c5-9cea-456d-bff6-49dd249f0ff4
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0a709ab6b28796328677e7e8ae009e3273565a3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012279"
---
# <a name="how-to-configure-certificates-with-a-soap-adapter"></a>如何設定 SOAP 配接器的憑證
SOAP 傳送配接器可以協助保護與接受或要求用戶端憑證的伺服器的連線。 若指定用戶端認證，則與要求或接收用戶端認證的伺服器連線時，SOAP 傳送配接器會使用認證。 如果您未指定用戶端憑證和目的地伺服器需要用戶端憑證、 寄件者未經過驗證和 SOAP 傳送配接器無法傳送訊息，並依照標準重試邏輯。  

 SOAP 傳送配接器使用的用戶端憑證所使用的帳戶的個人存放區從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理序正在執行。 SOAP 配接器會依照指紋來指定認證。 若 SOAP 傳送配接器因為任何原因而無法載入認證，它所傳送的訊息就會擱置。  

 當使用 SOAP 配接器來傳送加密或簽署訊息時，設定傳送埠的用戶端憑證指紋 SOAP 傳輸屬性。  

## <a name="prerequisites"></a>必要條件  
 若要執行本主題中的程序，您必須登入的成員身分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。  

### <a name="to-configure-biztalk-server-to-send-messages-over-a-soap-connection"></a>若要設定透過 SOAP 連線傳送訊息的 BizTalk Server  

1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，建立新的 SOAP 傳送埠，或開啟現有的 SOAP 傳送埠屬性。  

2. 按一下 [**設定**中**傳輸**一節**傳送埠屬性**] 對話方塊。  

3. 在上**一般**索引標籤中，於**驗證類型**，選取**Anonymous**，**基本**，**摘要**，或**NTLM**。  

4. 驗證類型是否**基本**或**摘要**，選取**不會使用單一登入**（在此情況下您必須指定使用者名稱和密碼），或選取**使用單一登入**（在此情況下您必須選取分支機構應用程式）。  

5. 在  **SSL 用戶端憑證指紋**，輸入適當的憑證指紋。  

6. 按一下  **確定**，然後按一下**確定**一次。
