---
title: 如何設定 MSMQ 配接器的憑證 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 922a171d-705f-4465-acda-212aa3797c57
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c73c695423ac8b0e9a08ee375e1294f74f832a5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972439"
---
# <a name="how-to-configure-certificates-with-an-msmq-adapter"></a>如何設定 MSMQ 配接器的憑證
MSMQ 傳送配接器可以協助保護與接受或要求用戶端憑證的伺服器的連線。 如果指定的用戶端憑證，則 MSMQ 傳送配接器與要求或接受用戶端憑證的伺服器連接時，就會使用的憑證。 如果未指定用戶端憑證和目的地伺服器需要用戶端憑證，寄件者未經過驗證，而且 MSMQ 傳送配接器無法傳送訊息，並依照標準重試邏輯。  

 MSMQ 傳送配接器使用的用戶端憑證所使用的帳戶的個人存放區從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理序正在執行。 憑證是由其指紋指定。 如果 MSMQ 傳送配接器無法載入憑證，因為任何原因，它所傳送的訊息將遭擱置。  

 當使用 MSMQ 配接器來傳送加密或簽署訊息時，設定傳送埠的憑證指紋 MSMQ 傳輸屬性。 在這個屬性，指定要用於訊息驗證憑證的指紋。 將此屬性與 [使用驗證] 屬性搭配使用以驗證訊息。 使用 [使用者名稱] 和 [密碼] 屬性以取得佇列的存取權。  

## <a name="prerequisites"></a>必要條件  
 若要執行本主題中的程序，您必須登入的成員身分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。  

### <a name="to-configure-biztalk-server-to-send-messages-over-an-msmq-connection"></a>若要設定透過 MSMQ 連接來傳送訊息的 BizTalk Server  

1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，建立新的 MSMQ 傳送埠，或開啟現有的 MSMQ 傳送埠屬性。  

2. 按一下 [**設定**中**傳輸**一節**傳送埠屬性**] 對話方塊。  

3. 在 [ **MSMQ 傳輸屬性**] 對話方塊中，如**驗證**，選取 **，則為 True**。  

4. 針對**憑證指紋**，輸入適當的憑證指紋。  

5. 按一下  **確定**，然後按一下**確定**一次。
