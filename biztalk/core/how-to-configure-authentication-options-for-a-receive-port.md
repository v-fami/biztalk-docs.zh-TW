---
title: 如何設定驗證選項的接收埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [receive ports], configuring
- authenticating, configuring
- managing [receive ports], authenticating
- receive ports, configuring
- configuring, authenticating
- configuring, receive ports
- authenticating, receive ports
ms.assetid: ce213ef0-ae91-47cf-84bf-0f86cc684bce
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52ca3f5d4636f0592c98528d481a8d3f0a1bc96b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001775"
---
# <a name="how-to-configure-authentication-options-for-a-receive-port"></a>如何設定接收埠的驗證選項
本主題描述如何使用 BizTalk Server 管理主控台來設定接收埠的訊息驗證選項。 這些選項會在設定合作對象解析驗證後生效。 選項包括：  
  
- **沒有驗證。** 如果選取此選項，接收埠將會讓訊息通過，而不檢查訊息認證。  
  
- **如果驗證失敗時，請卸除訊息。** 如果選取此選項，接收埠將會使用「合作對象」解析來檢查訊息認證，並且在驗證失敗時捨棄該訊息。  
  
- **驗證失敗時保留訊息。** 如果選取此選項，接收埠將會使用「合作對象」解析來檢查訊息認證，並且在驗證失敗時，將該訊息保留在擱置的佇列中。  
  
  如需建立和設定合作對象的指示，請參閱[如何建立合作對象](http://msdn.microsoft.com/library/f6feca1d-bc83-4fb6-981d-26c9e0d53044)。 如需合作對象解析驗證的詳細資訊，請參閱[驗證訊息的寄件者](../core/authenticating-the-sender-of-a-message.md)並[輸入訊息驗證](../core/inbound-message-authentication.md)。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。 如需詳細的權限的詳細資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。  
  
### <a name="to-configure-authentication-options-for-a-receive-port"></a>設定接收埠的驗證選項  
  
1. 按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。  
  
2. 在主控台樹狀結構中，展開您要為其設定接收埠驗證的 BizTalk 群組和 BizTalk 應用程式。  
  
3. 按一下 **接收連接埠**，以滑鼠右鍵按一下接收埠，然後按一下 **屬性**。  
  
4. 在 **驗證**區段中，選取的選項，然後按一下**確定**。  
  
## <a name="see-also"></a>另請參閱  
 [管理接收埠](../core/managing-receive-ports.md)