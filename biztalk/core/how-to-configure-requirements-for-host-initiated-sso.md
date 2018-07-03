---
title: 如何設定主機的需求初始化的 SSO |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 829deaba6782cb6e72f004c4fa96a6f8e2831be4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36982823"
---
# <a name="how-to-configure-requirements-for-host-initiated-sso"></a><span data-ttu-id="8b879-102">如何設定主控件初始化的 SSO 的需求</span><span class="sxs-lookup"><span data-stu-id="8b879-102">How to Configure Requirements for Host Initiated SSO</span></span>
<span data-ttu-id="8b879-103">雖然 Enterprise SSO 與主控件初始化的 SSO 在某些方面有共同的特點，但是某些平台和 Active Directory 需求對於主控件初始化的 SSO 而言則是唯一的。</span><span class="sxs-lookup"><span data-stu-id="8b879-103">Although Enterprise SSO and host initiated SSO have certain aspects in common, certain platform and Active Directory requirements are unique to host initiated SSO.</span></span> <span data-ttu-id="8b879-104">本主題將討論這些需求，並列出在系統上檢查或建立它們的步驟。</span><span class="sxs-lookup"><span data-stu-id="8b879-104">This topic discusses those requirements, and lists the steps to check or create them on your system.</span></span>  
  
- <span data-ttu-id="8b879-105">主控件初始化的 SSO 僅能在原生的 Windows Server 2008 網域環境上執行。</span><span class="sxs-lookup"><span data-stu-id="8b879-105">Host initiated SSO can be executed only on a native Windows Server 2008 domain environment.</span></span>  
  
- <span data-ttu-id="8b879-106">必須設定執行主控件初始化之 SSO 服務的服務帳戶，才能擁有 TCB 權限。</span><span class="sxs-lookup"><span data-stu-id="8b879-106">The service account for SSO Service that is performing host initiated SSO must be configured to have TCB privileges.</span></span> <span data-ttu-id="8b879-107">(您可以為網域安全性原則中的服務帳戶來設定此項。)</span><span class="sxs-lookup"><span data-stu-id="8b879-107">(You can configure this for the service account in the domain security policy.)</span></span>  
  
  <span data-ttu-id="8b879-108">此外，在使用「主控件初始化的處理」的「交易整合器」時，某些需求是必要的。</span><span class="sxs-lookup"><span data-stu-id="8b879-108">In addition, certain requirements are necessary when using Transaction Integrator for Host Initiated Processing.</span></span> <span data-ttu-id="8b879-109">TI for HIP 會利用主控件初始化的 SSO，來達成非 Windows 使用者的「單一登入」。</span><span class="sxs-lookup"><span data-stu-id="8b879-109">TI for HIP leverages host initiated SSO to achieve Single Sign-On for non-Windows users.</span></span>  
  
  <span data-ttu-id="8b879-110">例如，TI for HIP 服務的服務帳戶是在 domainname\hipsvc 服務帳戶下執行。</span><span class="sxs-lookup"><span data-stu-id="8b879-110">For example, service account for TI for HIP service runs under a service account domainname\hipsvc.</span></span> <span data-ttu-id="8b879-111">這項服務可以裝載想要存取遠端或本機資源在 Windows 上的 Windows 帳戶對應至非 Windows 帳戶的應用程式。</span><span class="sxs-lookup"><span data-stu-id="8b879-111">This service can host applications that want to access remote or local resources on Windows with the Windows account that correspond to the non-Windows account.</span></span>  
  
  <span data-ttu-id="8b879-112">domainname\hipsvc 帳戶必須隸屬於用來「單一登入」之「分支機構應用程式」的「應用程式系統管理員」群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="8b879-112">The domainname\hipsvc account must belong to the Application Administrator group account for the Affiliate Application that is being used for Single Sign-On.</span></span>  
  
  <span data-ttu-id="8b879-113">domainname\hipsvc 帳戶必須已約束委派權限，才能使用主控件初始化的「單一登入」。</span><span class="sxs-lookup"><span data-stu-id="8b879-113">The domainname\hipsvc account must have constrained delegation privileges to use host initiated Single Sign-On.</span></span> <span data-ttu-id="8b879-114">這可由 Active Directory 中的網域管理員來設定。</span><span class="sxs-lookup"><span data-stu-id="8b879-114">This can be configured by the domain administrator in Active Directory.</span></span> <span data-ttu-id="8b879-115">您可以為具有註冊之 SPN 的帳戶設定委派。</span><span class="sxs-lookup"><span data-stu-id="8b879-115">Delegation can be configured for accounts that have registered SPNs.</span></span> <span data-ttu-id="8b879-116">約束委派可讓服務帳戶只能存取由系統管理員所指定的元件。</span><span class="sxs-lookup"><span data-stu-id="8b879-116">Constrained delegation allows the service account to access only components that are specified by the administrator.</span></span>  
  
### <a name="to-check-your-domain-function-level"></a><span data-ttu-id="8b879-117">檢查網域功能層級</span><span class="sxs-lookup"><span data-stu-id="8b879-117">To check your domain function level</span></span>  
  
1.  <span data-ttu-id="8b879-118">在您**Active Directory 網域及信任**MMC 嵌入式管理單元，右側按一下 節點**Active Directory 網域及信任**，然後按一下**提高樹系功能等級**。</span><span class="sxs-lookup"><span data-stu-id="8b879-118">In your **Active Directory Domains and Trusts** MMC snap-in, right click the node **Active Directory Domains and Trusts**, and then click **Raise Forest Functional Level**.</span></span>  
  
2.  <span data-ttu-id="8b879-119">確認功能等級**Windows Server 2008**。</span><span class="sxs-lookup"><span data-stu-id="8b879-119">Verify that the functional level is **Windows Server 2008**.</span></span> <span data-ttu-id="8b879-120">若不是，請參閱 Active Directory 文件，再嘗試變更設定。</span><span class="sxs-lookup"><span data-stu-id="8b879-120">If it is not, refer to your Active Directory documentation before you attempt to change the setting.</span></span>  
  
### <a name="to-create-an-spn"></a><span data-ttu-id="8b879-121">建立 SPN</span><span class="sxs-lookup"><span data-stu-id="8b879-121">To create an SPN</span></span>  
  
1. <span data-ttu-id="8b879-122">下載**setspn**公用程式，從下列位置： [ http://go.microsoft.com/fwlink/?LinkId=33178 ](http://go.microsoft.com/fwlink/?LinkId=33178)。</span><span class="sxs-lookup"><span data-stu-id="8b879-122">Download the **setspn** utility from the following location: [http://go.microsoft.com/fwlink/?LinkId=33178](http://go.microsoft.com/fwlink/?LinkId=33178).</span></span>  
  
2. <span data-ttu-id="8b879-123">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="8b879-123">On the **Start** menu, click **Run**.</span></span>  
  
3. <span data-ttu-id="8b879-124">在 [**執行**] 對話方塊中，輸入**cmd**，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8b879-124">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
4. <span data-ttu-id="8b879-125">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="8b879-125">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="8b879-126">預設值是\<磁碟機\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="8b879-126">The default is \<drive\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
5. <span data-ttu-id="8b879-127">型別**setpsn-a hipsvc\computername.domain.com domain\hissvc**</span><span class="sxs-lookup"><span data-stu-id="8b879-127">Type **setpsn -a hipsvc\computername.domain.com domain\hissvc**</span></span>  
  
    <span data-ttu-id="8b879-128">何處**hipsvc\computername.domain.com**是服務將會執行作業和執行所在的電腦，以及**domain\hissvc**是 hipsvc 的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="8b879-128">where **hipsvc\computername.domain.com** is the service that will perform the operation and the computer it is running on, and **domain\hissvc** is the service account for hipsvc.</span></span>  
  
   <span data-ttu-id="8b879-129">這麼做之後，您就可以為此服務帳戶 (domain\hissvc) 在 Active Directory 中設定約束委派，以存取網路中的適當資源。</span><span class="sxs-lookup"><span data-stu-id="8b879-129">After doing this, you can configure constrained delegation in Active Directory for this service account (domain\hissvc) to access the appropriate resource in the network.</span></span>  
  
#### <a name="to-give-tcb-privileges-for-the-sso-service-account"></a><span data-ttu-id="8b879-130">提供 TCB 權限給 SSO 服務帳戶</span><span class="sxs-lookup"><span data-stu-id="8b879-130">To give TCB privileges for the SSO service account</span></span>  
  
-   <span data-ttu-id="8b879-131">在您**使用者權利指派 網域安全性原則-本機原則-**，將 SSO 服務帳戶加入**做為作業系統的一部分**原則。</span><span class="sxs-lookup"><span data-stu-id="8b879-131">Under your **Domain Security Policy - Local Policies - User Rights Assignment**, add the SSO Service account to the **Act as part of operating system** policy.</span></span>  
  
     <span data-ttu-id="8b879-132">如需有關 Kerberos 通訊協定轉換與限制委派的詳細資訊，請移至[ http://go.microsoft.com/fwlink/?LinkId=195484 ](http://go.microsoft.com/fwlink/?LinkId=195484)。</span><span class="sxs-lookup"><span data-stu-id="8b879-132">For more information about Kerberos Protocol Transition and Constrained Delegation, go to [http://go.microsoft.com/fwlink/?LinkId=195484](http://go.microsoft.com/fwlink/?LinkId=195484).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b879-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b879-133">See Also</span></span>  
 [<span data-ttu-id="8b879-134">主控件初始化的 SSO</span><span class="sxs-lookup"><span data-stu-id="8b879-134">Host Initiated SSO</span></span>](../core/host-initiated-sso.md)