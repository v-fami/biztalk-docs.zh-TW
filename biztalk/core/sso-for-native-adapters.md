---
title: 原生配接器的 SSO |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapters, SSO
- SSO, adapters
ms.assetid: d8527f0f-910c-42ce-9bd3-83ab6d4349c0
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45aaf357d943853cc9504762437f554f1d28efb7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278054"
---
# <a name="sso-for-native-adapters"></a>原生配接器的 SSO
「企業單一登入」(SSO) 可讓您在與不同電腦系統或網站互通時，只需登入一次即可。 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的這項功能讓 BizTalk 配接器能夠提供適當的使用者識別碼和認證給網路中的多個應用程式，這些應用程式都使用以 Microsoft Windows 認證為基礎的通用驗證機制。 Windows 驗證您的認證之後，您不必提供其他認證來連接應用程式。  
  
 雖然依照預設 SSO 為停用，但 HTTP 和 SOAP 配接器仍然可以使用 SSO。 您可以設定 HTTP 配接器的傳送埠和接收位置以使用 SSO，但您只能設定 SOAP 配接器的接收位置以使用 SSO。 兩種配接器都是使用 BizTalk Server 管理主控台或設定單一登入。  
  
 SSO 的驗證主要依賴 Windows 驗證以及在 Active Directory 中建立的 Windows 群組。 使用者或系統管理員使用 SSO 完成的所有作業都需要 Windows 先驗證使用者或系統管理員。  
  
 如需有關 SSO 如何與 HTTP 和 SOAP 配接器搭配使用的詳細資訊，請參閱＜另請參閱＞中的適當主題。  
  
## <a name="see-also"></a>另請參閱  
 [使用 SSO](../core/using-sso.md)   
 [HTTP 配接器](../core/http-adapter.md)   
 [SOAP 配接器](../core/soap-adapter.md)