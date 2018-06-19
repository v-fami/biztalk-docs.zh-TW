---
title: 如何建立分支機構應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3be483f8-2617-459e-9081-aab886c75d93
caps.latest.revision: 3
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 5145111b2c585edab92cc10c3e3614e8bb91a85d
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "30250986"
---
# <a name="how-to-create-an-affiliate-application"></a><span data-ttu-id="518fe-102">如何建立分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="518fe-102">How to Create an Affiliate Application</span></span>
<span data-ttu-id="518fe-103">您可以使用 MMC 嵌入式管理單元或**createapps**來建立一或多個應用程式，如 XML 檔案所指定的命令。</span><span class="sxs-lookup"><span data-stu-id="518fe-103">You can use the MMC Snap-In or the **createapps** command to create one or more applications, as specified by the XML file.</span></span> <span data-ttu-id="518fe-104">以下是範例 XML 檔案的 Windows-Initiated 單一登入 (SSO):</span><span class="sxs-lookup"><span data-stu-id="518fe-104">The following is an example XML file for Windows-Initiated Single Sign-On (SSO):</span></span>  
  
```  
<sso>  
<application name="SAP">  
<description>The SAP application</description>   
<contact>someone@example.com</contact>   
<appuserAccount>domain\AppUserAccount</appuserAccount>   
<appAdminAccount>domain\AppAdminAccount</appAdminAccount>   
<field ordinal="0" label="User Id" masked="no" />   
<field ordinal="1" label="Password" masked="yes" />   
<flags groupApp="no" configStoreApp="no" allowTickets="no" validateTickets="yes" allowLocalAccounts="no" timeoutTickets="yes" adminAccountSame="no" enableApp="no" />  
</application>  
</sso>  
  
```  
  
 <span data-ttu-id="518fe-105">建立分支機構應用程式後，無法修改以下屬性：</span><span class="sxs-lookup"><span data-stu-id="518fe-105">After you create an affiliate application, you cannot modify the following properties:</span></span>  
  
-   <span data-ttu-id="518fe-106">分支機構應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="518fe-106">Name of the affiliate application.</span></span>  
  
-   <span data-ttu-id="518fe-107">分支機構應用程式相關聯的欄位。</span><span class="sxs-lookup"><span data-stu-id="518fe-107">Fields associated with the affiliate application.</span></span>  
  
-   <span data-ttu-id="518fe-108">分支機構應用程式類型 （主機群組、 個別或組態存放區）。</span><span class="sxs-lookup"><span data-stu-id="518fe-108">Affiliate application type (host group, individual, or configuration store).</span></span>  
  
-   <span data-ttu-id="518fe-109">與分支機構系統管理員群組相同的管理帳戶。</span><span class="sxs-lookup"><span data-stu-id="518fe-109">Administration account same as affiliate administrators group.</span></span> <span data-ttu-id="518fe-110">（指定這個旗標會永遠使用分支機構系統管理員群組做為系統管理員帳戶進行此分支機構應用程式）。</span><span class="sxs-lookup"><span data-stu-id="518fe-110">(Specifying this flag will always use the affiliate administrators group as the administrator account for this affiliate application.)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="518fe-111">您可以將 allowLocalAccounts 旗標設為 [是]，以使用系統管理員帳戶和使用者帳戶的本機帳戶。</span><span class="sxs-lookup"><span data-stu-id="518fe-111">You can use local accounts for the administration account and user account by setting the allowLocalAccounts flag to yes.</span></span> <span data-ttu-id="518fe-112">不過，您應該只在單一電腦的情況下使用這個旗標。</span><span class="sxs-lookup"><span data-stu-id="518fe-112">However, you should only use this flag in single-computer scenarios.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="518fe-113">您必須是 SSO 系統管理員或 SSO 分支機構系統管理員，才能執行這項工作。</span><span class="sxs-lookup"><span data-stu-id="518fe-113">You must be an SSO administrator or SSO affiliate administrator to perform this task.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="518fe-114">如果您網域控制站上執行設定時，網域本機領域群組指定應用程式系統管理員或應用程式使用者建立分支機構應用程式時，建議您啟用的本機帳戶旗標。</span><span class="sxs-lookup"><span data-stu-id="518fe-114">If you are performing the configuration on a Domain Controller, and the Domain Local scope groups are specified for Application Administrators or Application Users while creating Affiliate Applications, it is recommended that you enable the local account flag.</span></span> <span data-ttu-id="518fe-115">若要這樣做：</span><span class="sxs-lookup"><span data-stu-id="518fe-115">To do this:</span></span>  
  
-   <span data-ttu-id="518fe-116">在 MMC 嵌入式管理單元中，選取 允許本機帳戶作為存取帳戶建立過程。</span><span class="sxs-lookup"><span data-stu-id="518fe-116">In the MMC Snap-in, select Allow local accounts for access accounts during the creation process.</span></span>  
  
-   <span data-ttu-id="518fe-117">從命令列指定 allowLocalAccounts = 分支機構應用程式建立的 XML 檔案中的 [是]。</span><span class="sxs-lookup"><span data-stu-id="518fe-117">From the command line, specify allowLocalAccounts=yes in the XML file for Affiliate Application creation.</span></span>  
  
 <span data-ttu-id="518fe-118">建立分支機構應用程式後，您必須啟用它。</span><span class="sxs-lookup"><span data-stu-id="518fe-118">After you create the affiliate application, you must enable it.</span></span> <span data-ttu-id="518fe-119">如需詳細資訊，請參閱[如何啟用分支機構應用程式](../esso/how-to-enable-an-affiliate-application.md)。</span><span class="sxs-lookup"><span data-stu-id="518fe-119">For more information, see [How to Enable an Affiliate Application](../esso/how-to-enable-an-affiliate-application.md).</span></span>  
  
### <a name="to-create-an-affiliate-application-using-the-microsoft-management-console-mmc-snap-in"></a><span data-ttu-id="518fe-120">若要建立分支機構應用程式使用 Microsoft Management Console (MMC) 嵌入式管理單元</span><span class="sxs-lookup"><span data-stu-id="518fe-120">To create an affiliate application using the Microsoft Management Console (MMC) Snap-In</span></span>  
  
1.  <span data-ttu-id="518fe-121">按一下**啟動**，指向 **程式**，按一下  **Microsoft 企業單一登入**，然後按一下  **SSO 管理**。</span><span class="sxs-lookup"><span data-stu-id="518fe-121">Click **Start**, point to **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="518fe-122">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="518fe-122">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="518fe-123">以滑鼠右鍵按一下**分支機構應用程式**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="518fe-123">Right-click **Affiliate Applications**, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="518fe-124">請依照下列中的指示**建立新的分支機構應用程式**精靈。</span><span class="sxs-lookup"><span data-stu-id="518fe-124">Follow the instructions in the **Create New Affiliate Application** wizard.</span></span>  
  
### <a name="to-create-an-affiliate-application-using-the-command-line"></a><span data-ttu-id="518fe-125">使用命令列建立分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="518fe-125">To create an affiliate application using the command line</span></span>  
  
1.  <span data-ttu-id="518fe-126">按一下  **啟動**, ，按一下  **執行**, ，型別 `cmd`, ，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="518fe-126">Click **Start**, click **Run**, type `cmd`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="518fe-127">在命令提示字元中，移至 「 企業單一登入 」 安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="518fe-127">At the command prompt, go to the Enterprise Single Sign-On installation directory.</span></span>  
  
     <span data-ttu-id="518fe-128">預設安裝目錄是*\<磁碟機 >*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="518fe-128">The default installation directory is *\<drive>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="518fe-129">型別`ssomanage –createapps <application file name>`，其中*\<應用程式檔案名稱 >* 是 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="518fe-129">Type `ssomanage –createapps <application file name>`, where *\<application file name>* is the XML file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="518fe-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="518fe-130">See Also</span></span>  
 <span data-ttu-id="518fe-131">[SSO 分支機構應用程式](../esso/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="518fe-131">[SSO Affiliate Applications](../esso/sso-affiliate-applications.md) </span></span>  
 <span data-ttu-id="518fe-132">[如何啟用分支機構應用程式](../esso/how-to-enable-an-affiliate-application.md) </span><span class="sxs-lookup"><span data-stu-id="518fe-132">[How to Enable an Affiliate Application](../esso/how-to-enable-an-affiliate-application.md) </span></span>  
 <span data-ttu-id="518fe-133">[如何刪除分支機構應用程式](../esso/how-to-delete-an-affiliate-application.md) </span><span class="sxs-lookup"><span data-stu-id="518fe-133">[How to Delete an Affiliate Application](../esso/how-to-delete-an-affiliate-application.md) </span></span>  
 <span data-ttu-id="518fe-134">[管理使用者對應](../esso/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="518fe-134">[Managing User Mappings](../esso/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="518fe-135">管理分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="518fe-135">Managing Affiliate Applications</span></span>](../esso/managing-affiliate-applications.md)