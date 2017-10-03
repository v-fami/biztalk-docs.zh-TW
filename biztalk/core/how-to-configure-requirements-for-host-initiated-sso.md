---
title: "如何設定主機的需求初始化的 SSO |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service accounts, granting privileges [SSO]
- host initiated SSO, configuring
- domain function level [SSO]
- host initiated SSO, Transaction Integrator (TI)
- SPN [SSO]
- managing [SSO], granting TCB privileges
- Transaction Integrator (TI)
- host initiated SSO, SPN
- host initiated SSO, TCB privileges
- configuring, host initiated SSO
- creating, SPNs [SSO]
- TCB privileges [SSO]
- managing [SSO], host initiated
- host initiated SSO, domain function level
- service accounts, SSO
- SSO, host initiated
- managing [SSO], creating SPNs
- SSO, service accounts
ms.assetid: 91d77c9f-bab2-4f6e-8bce-e31c59cebb20
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9f8a004c1883a05c3fcf60324f428144591cff4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-requirements-for-host-initiated-sso"></a>如何設定主控件初始化的 SSO 的需求
雖然 Enterprise SSO 與主控件初始化的 SSO 在某些方面有共同的特點，但是某些平台和 Active Directory 需求對於主控件初始化的 SSO 而言則是唯一的。 本主題將討論這些需求，並列出在系統上檢查或建立它們的步驟。  
  
-   主控件初始化的 SSO 僅能在原生的 Windows Server 2008 網域環境上執行。  
  
-   必須設定執行主控件初始化之 SSO 服務的服務帳戶，才能擁有 TCB 權限。 (您可以為網域安全性原則中的服務帳戶來設定此項。)  
  
 此外，在使用「主控件初始化的處理」的「交易整合器」時，某些需求是必要的。 TI for HIP 會利用主控件初始化的 SSO，來達成非 Windows 使用者的「單一登入」。  
  
 例如，TI for HIP 服務的服務帳戶是在 domainname\hipsvc 服務帳戶下執行。 這項服務可以裝載應用程式想要存取遠端或本機上的資源 Windows 與 Windows 帳戶對應至非 Windows 帳戶。  
  
 domainname\hipsvc 帳戶必須隸屬於用來「單一登入」之「分支機構應用程式」的「應用程式系統管理員」群組帳戶。  
  
 domainname\hipsvc 帳戶必須已約束委派權限，才能使用主控件初始化的「單一登入」。 這可由 Active Directory 中的網域管理員來設定。 您可以為具有註冊之 SPN 的帳戶設定委派。 約束委派可讓服務帳戶只能存取由系統管理員所指定的元件。  
  
### <a name="to-check-your-domain-function-level"></a>檢查網域功能層級  
  
1.  在您**Active Directory 網域及信任**MMC 嵌入式管理單元，右邊按一下節點**Active Directory 網域及信任**，然後按一下 **提高樹系功能等級**。  
  
2.  確認功能等級為**Windows Server 2008**。 若不是，請參閱 Active Directory 文件，再嘗試變更設定。  
  
### <a name="to-create-an-spn"></a>建立 SPN  
  
1.  下載**setspn**公用程式，從下列位置： [http://go.microsoft.com/fwlink/?LinkId=33178](http://go.microsoft.com/fwlink/?LinkId=33178)。  
  
2.  在 **[開始]** 功能表上，按一下 **[執行]**。  
  
3.  在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。  
  
4.  在命令列，移至「企業單一登入」安裝目錄。 預設值是\<磁碟機 >: \Program Files\Common Files\Enterprise Single Sign-on。  
  
5.  型別**setpsn-a hipsvc\computername.domain.com domain\hissvc**  
  
     其中**hipsvc\computername.domain.com**是將執行作業，但電腦，執行的服務和**domain\hissvc**是 hipsvc 的服務帳戶。  
  
 這麼做之後，您就可以為此服務帳戶 (domain\hissvc) 在 Active Directory 中設定約束委派，以存取網路中的適當資源。  
  
#### <a name="to-give-tcb-privileges-for-the-sso-service-account"></a>提供 TCB 權限給 SSO 服務帳戶  
  
-   在您**網域安全性原則-本機原則的使用者權限指派**，將 SSO 服務帳戶加入**做為作業系統的一部分**原則。  
  
     如需有關 Kerberos 通訊協定轉換與限制委派的詳細資訊，請移至[http://go.microsoft.com/fwlink/?LinkId=195484](http://go.microsoft.com/fwlink/?LinkId=195484)。  
  
## <a name="see-also"></a>另請參閱  
 [主控件初始化的 SSO](../core/host-initiated-sso.md)