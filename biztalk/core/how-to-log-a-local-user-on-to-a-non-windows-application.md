---
title: "如何將本機使用者登入非 Windows 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b55957f4-22c4-48b5-827a-ab41d8f846ac
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3c2e9ffaede20e29987938a436ad2a091920fce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-log-a-local-user-on-to-a-non-windows-application"></a>如何登入非 Windows 應用程式的本機使用者
當您以分支機構應用程式設定使用者之後，就可以使用「單一登入」(SSO) 存取外部使用者名稱和目前使用者的認證。 然後您可以使用這些認證將使用者登入在主控件伺服器上執行的分支機構應用程式。  
  
> [!NOTE]
>  除了為 SSO 設定適當的安全性通訊協定之外，您可能也需要設定其他安全性，好讓您的應用程式能夠在正確的資訊安全內容中呼叫 SSO。 如果您的應用程式無法在正確的資訊安全內容中呼叫 SSO，SSO 將會拒絕對應用程式的存取。  
  
### <a name="to-set-the-security-context-for-an-sso-application"></a>若要為 SSO 應用程式設定資訊安全內容  
  
1.  識別讓您的應用程式順利執行所需的認證為何。  
  
     例如，使用 Web 服務或 IIS 中裝載的.NET Framework 遠端處理的應用程式需要模擬用戶端，才能將傳遞適當的認證傳遞 SSO。  
  
2.  確認相關的安全性設定 (如虛擬目錄、應用程式集區和 web.config 檔案上的設定) 已妥善設定，以便為您的應用程式提供這些認證。  
  
     如需如何設定安全性認證的詳細資訊，請參閱[建構安全 ASP.NET 應用程式： 驗證、 授權和安全通訊](http://go.microsoft.com/fwlink/?LinkId=193906)。  
  
     如需 ASP.NET Web 服務傳遞認證的詳細資訊，請參閱[HOW TO： 將傳遞至 ASP.NET Web 服務的目前認證](http://go.microsoft.com/fwlink/?LinkId=193907)。  
  
### <a name="to-log-a-local-user-on-to-a-host-application"></a>將本機使用者登入主控件應用程式  
  
1.  接收讓目前使用者登入在主控件伺服器上執行之應用程式的要求。  
  
     您要負責決定目前使用者以何種方式要求登入主控件應用程式。  
  
2.  為使用 `ISSOLookup1.GetCredentials` 或 `ISSOLookup2.GetCredentials` 的目前使用者擷取認證。  
  
     您必須提供主應用程式，以及任何相關旗標的名稱。 `GetCredentials`傳回的相關聯的使用者名稱與主應用程式的認證。  
  
     請注意，您可以使用 `ISSOLookup1` 或 `ISSOLookup2`。 唯一的差別是 `ISSOLookup2` 也有一個將遠端使用者登入本機 Windows 應用程式的方法。  
  
3.  使用外部使用者名稱和認證登入主控件應用程式。  
  
     您要負責決定如何使用認證登入主控件應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [如何將遠端使用者登入本機應用程式](../core/how-to-log-a-remote-user-on-to-a-local-application.md)