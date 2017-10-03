---
title: "WCF 配接器安裝憑證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tools, Certificates Management Console
- certificates, installing [WCF adapters]
- certificates, Certificates Management Console
- certificates, WCF adapters
- WCF adapters, send locations
- receive locations, WCF adapters
- send locations, WCF adapters
- WCF adapters, receive locations
- WCF adapters, certificates
ms.assetid: 04dc065f-a6e8-4359-8696-2a3de24d531d
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 654e5300c253bbf4cede2113c9282b6a2f02862c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="installing-certificates-for-the-wcf-adapters"></a>安裝 WCF 配接器的憑證
WCF 配接器可以基於下列用途使用公開金鑰基礎結構 (PKI) 數位憑證：訊息加密和解密、訊息簽章和驗證 (Verification) (不可否認性) 和用戶端驗證 (Authentication)。 本主題描述各種憑證使用方式案例和組態選項指導方針，以搭配 WCF 配接器使用數位憑證。  
  
## <a name="certificate-usage-scenarios-for-the-wcf-receive-locations"></a>WCF 接收位置的憑證使用方式案例  
 下表顯示如何安裝 WCF 接收位置的憑證。  
  
|憑證使用方式|使用者內容|憑證存放區位置|憑證類型|安裝憑證的時機|  
|-----------------------|------------------|--------------------------------|----------------------|--------------------------------------|  
|依據接收位置的安全性設定進行解密和簽章|與接收處理常式關聯之主控件執行個體所使用的帳戶|登入執行每一部電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，以便為每個主控件執行個體服務帳戶 」，裝載接收位置，並且將服務憑證匯入**目前使用者 \ 個人 (My)**儲存。|自有私用憑證|指定的值**服務憑證-憑證指紋**下列組態屬性：<br /><br /> -**安全性模式**屬性 Wcf-basichttp 接收位置設定為**訊息**。<br />-**傳輸用戶端認證類型**屬性 Wcf-basichttp 接收位置設定為**憑證**如**TransportCredentialOnly**安全性模式。<br />-**訊息用戶端認證類型**屬性 Wcf-wshttp 接收位置設定為**無**，**憑證**，或**UserName**如**訊息**安全性模式。<br />-**傳輸用戶端認證類型**屬性 Wcf-nettcp 接收位置設定為**無**或**憑證**如**傳輸**安全性模式。<br />-**訊息用戶端認證類型**屬性 Wcf-nettcp 接收位置設定為**無**， **UserName**，或**憑證**如**訊息**安全性模式。<br />-**訊息用戶端認證類型**屬性 Wcf-nettcp 接收位置設定為**Windows**， **UserName**，或**憑證**如**TransportWithMessageCredential**安全性模式。<br />-**安全性模式**Wcf-netmsmq 屬性設定為**訊息**或**兩者**。|  
|用戶端驗證|不適用|以系統管理員的身分，登入執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 並將裝載接收位置的每個電腦，再將用戶端 X.509 憑證的 CA 憑證鏈結匯入電腦的「信任的根憑證授權」憑證存放區中，這樣就可以驗證這個接收位置的用戶端。|X.509 憑證的 CA 憑證鏈結|依據下列組態，將用戶端 X.509 憑證的 CA 憑證鏈結安裝在「信任的根憑證授權」憑證存放區：<br /><br /> -**訊息用戶端認證類型**或**傳輸用戶端認證類型**屬性 Wcf-basichttp 接收位置設定為**憑證**。<br />-**訊息用戶端認證類型**或**傳輸用戶端認證類型**屬性 Wcf-wshttp 接收位置設定為**憑證**。<br />-**訊息用戶端認證類型**或**傳輸用戶端認證類型**屬性 Wcf-nettcp 接收位置設定為**憑證**。<br />-**訊息用戶端認證類型**或**MSMQ 驗證模式**屬性 Wcf-netmsmq 接收位置設定為**憑證**。|  
  
> [!NOTE]
>  因為標準的 WCF 接收配接器使用[ChainTrust](http://go.microsoft.com/fwlink/?LinkId=88960)模式來驗證用戶端憑證，您必須安裝用戶端 X.509 憑證的 CA 憑證鏈結。 您可以使用 WCF-Custom 或 WCF-CustomIsolated 配接器變更此預設行為。  
  
> [!NOTE]
>  對於外掛式 WCF 接收配接器，您需要讓外掛式主控件執行個體與對應的應用程式集區間的使用者帳戶相符合。 如需 BizTalk 外掛式主控件的詳細資訊，請參閱[啟用 Web 服務](../core/enabling-web-services.md)。  
  
> [!NOTE]
>  Wcf-custom 和 Wcf-customisolated 接收位置的使用者內容、 憑證存放區位置，以及要安裝憑證的憑證類型而異**serviceCredentials**和**clientCredentials**行為項目設定。  
  
> [!NOTE]
>  如果接收位置使用的憑證項目**端點身分識別**屬性，您也必須安裝的已發佈的服務身分識別的憑證中指定的憑證存放區**端點身分識別**屬性。  
  
> [!NOTE]
>  如果不使用主控件執行個體服務帳戶或系統管理員帳戶登入電腦，您也可以改為使用「執行身分」命令搭配適用的帳戶，以執行相同的動作。  
  
## <a name="certificate-usage-scenarios-for-the-wcf-send-ports"></a>WCF 傳送埠的憑證使用方式案例  
 下表顯示如何安裝 WCF 傳送埠的憑證。  
  
|憑證使用方式|使用者內容|憑證存放區位置|憑證類型|安裝憑證的時機|  
|-----------------------|------------------|--------------------------------|----------------------|--------------------------------------|  
|用戶端驗證|與傳送埠關聯之主控件執行個體所使用的帳戶|登入執行每一部電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，以便為每個主控件執行個體服務帳戶 」，裝載傳送埠，並且將用戶端憑證匯入**目前使用者 \ 個人 (My)**儲存。|自有私用憑證|指定的值**用戶端憑證-憑證指紋**下列組態屬性：<br /><br /> -**訊息用戶端認證類型**或**傳輸用戶端認證類型**Wcf-basichttp 傳送埠的屬性設定為**憑證**。<br />-**訊息用戶端認證類型**或**傳輸用戶端認證類型**Wcf-wshttp 傳送埠的屬性設定為**憑證**。<br />-**訊息用戶端認證類型**或**傳輸用戶端認證類型**Wcf-nettcp 傳送埠的屬性設定為**憑證**。<br />-**訊息用戶端認證類型**或**MSMQ 驗證模式**Wcf-netmsmq 傳送埠的屬性設定為**憑證**。|  
|依據傳送埠的安全性設定進行服務驗證 (Authentication)、簽章驗證 (Verification) 和加密|不適用|登入執行每一部電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，以便裝載傳送埠做為系統管理員，並且將服務憑證匯入**本機電腦 \ 其他人 (AddressBook)**儲存。 您也必須將服務憑證的 CA 憑證鏈結安裝在電腦「信任的根憑證授權」憑證存放區中。|服務的公開憑證<br />的服務憑證 CA 憑證鏈結|指定的值**服務憑證-憑證指紋**下列組態屬性：<br /><br /> -**訊息用戶端認證類型**或**傳輸用戶端認證類型**Wcf-basichttp 傳送埠的屬性設定為**憑證**。<br />-**訊息用戶端認證類型**Wcf-wshttp 傳送埠的屬性設定為**無**， **UserName**，或**憑證**時**交涉服務認證**清除選項。<br />-**安全性模式**Wcf-netmsmq 傳送埠設定為**訊息**或**兩者**。|  
|依據傳送埠的安全性設定進行服務驗證 (Authentication)、簽章驗證 (Verification) 和加密|不適用|以系統管理員的身分，登入執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 並將裝載傳送埠的每個電腦，再將用戶端 X.509 憑證的 CA 憑證鏈結匯入電腦的「信任的根憑證授權」憑證存放區中，這樣就可以驗證這個傳送埠的服務。|服務憑證的 CA 憑證鏈結|如果您未明確指定的服務憑證**服務憑證-憑證指紋**屬性，安裝 CA 憑證鏈結，服務 X.509 憑證至信任的根憑證授權單位憑證存放區中的下列設定：<br /><br /> -**安全性模式**Wcf-basichttp 傳送埠設定為**傳輸**或**TransportWithMessageCredential**。<br />-**安全性模式**Wcf-wshttp 傳送埠設定為**傳輸**或**TransportWithMessageCredential**。<br />-**安全性模式**Wcf-nettcp 傳送埠設定為**TransportWithMessageCredential**。<br />-**傳輸用戶端認證類型**Wcf-nettcp 傳送埠的屬性設定為**無**或**憑證**。<br />-**訊息用戶端認證類型**Wcf-nettcp 傳送埠的屬性設定為**無**， **UserName**，或**憑證**。|  
  
> [!NOTE]
>  因為標準的 WCF 傳送配接器使用[ChainTrust](http://go.microsoft.com/fwlink/?LinkId=88960)模式來驗證服務憑證，您必須安裝服務 X.509 憑證的 CA 憑證鏈結。 您可以使用 WCF-Custom 或 WCF-CustomIsolated 配接器變更此預設行為。  
  
> [!NOTE]
>  Wcf-custom 和 Wcf-customisolated 傳送連接埠、 使用者內容、 憑證存放區位置，及安裝憑證的憑證類型而異**serviceCredentials**和**clientCredentials**行為項目設定。  
  
> [!NOTE]
>  如果傳送埠使用的憑證項目**端點身分識別**屬性，您也必須安裝憑證存放區中指定的預期的服務身分識別憑證**端點識別**屬性。  
  
> [!NOTE]
>  如果不使用主控件執行個體服務帳戶或系統管理員帳戶登入電腦，您也可以改為使用「執行身分」命令搭配適用的帳戶，以執行相同的動作。  
  
## <a name="displaying-the-certificates-management-console"></a>顯示憑證管理主控台  
 若要顯示本機電腦和目前的使用者的 [憑證管理主控台] 介面，請執行下列步驟：  
  
1.  按一下**啟動**，按一下**執行**，型別**MMC**，按一下**確定**開啟 Microsoft Management Console。  
  
2.  在**檔案**功能表上，按一下 [**新增/移除嵌入式管理單元**顯示**新增/移除嵌入式管理單元**] 對話方塊。  
  
3.  按一下**新增**顯示**新增獨立嵌入式管理單元** 對話方塊。  
  
4.  選取**憑證**從嵌入式管理單元，然後再按一下清單**新增**。  
  
5.  選取**電腦帳戶**，按一下 **下一步**，然後按一下 **完成**。 這樣會新增本機電腦的 [憑證管理主控台] 介面。  
  
6.  請確認**憑證**仍然有選取的嵌入式管理單元清單，然後按一下 **新增**一次。  
  
7.  選取**我的使用者帳戶**，然後按一下 **完成**。 這樣會新增目前的使用者的 [憑證管理主控台] 介面。  
  
    > [!NOTE]
    >  如此將會針對您目前登入所使用的帳戶顯示 [憑證管理主控台]。 如果您需要針對某個服務帳戶將憑證匯入「個人」存放區，您應該先使用該服務帳戶認證來登入。  
  
8.  按一下**關閉**中**獨立嵌入式管理單元** 對話方塊。  
  
9. 按一下**確定**中**新增/移除嵌入式管理單元** 對話方塊。