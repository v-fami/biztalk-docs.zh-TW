---
title: 如何建立分支機構應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [SSO applications], creating
- applications [SSO], creating
- creating, applications [SSO]
ms.assetid: d0967c4b-6201-416a-9d3a-23b5de5b83d6
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8775ea82843641600c9156d79afab49e6cd7c634
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37003103"
---
# <a name="how-to-create-an-affiliate-application"></a><span data-ttu-id="ae997-102">如何建立分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="ae997-102">How to Create an Affiliate Application</span></span>
<span data-ttu-id="ae997-103">您可以使用 MMC 嵌入式管理單元或此命令來建立一或多個應用程式，如 XML 檔案所指定。</span><span class="sxs-lookup"><span data-stu-id="ae997-103">You can use the MMC Snap-In or this command to create one or more applications, as specified by the XML file.</span></span> <span data-ttu-id="ae997-104">Windows 初始化的 SSO 範例 XML 檔案如下：</span><span class="sxs-lookup"><span data-stu-id="ae997-104">An example XML file for Windows Initiated SSO is:</span></span>  
  
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
  
 <span data-ttu-id="ae997-105">建立分支機構應用程式後，無法修改以下屬性：</span><span class="sxs-lookup"><span data-stu-id="ae997-105">After you create an affiliate application, you cannot modify the following properties:</span></span>  
  
-   <span data-ttu-id="ae997-106">分支機構應用程式的名稱</span><span class="sxs-lookup"><span data-stu-id="ae997-106">Name of the affiliate application</span></span>  
  
-   <span data-ttu-id="ae997-107">與分支機構應用程式關聯的欄位</span><span class="sxs-lookup"><span data-stu-id="ae997-107">Fields associated with the affiliate application</span></span>  
  
-   <span data-ttu-id="ae997-108">分支機構應用程式類型 (主控件群組、個別或組態存放區)</span><span class="sxs-lookup"><span data-stu-id="ae997-108">Affiliate application type (host group, individual, or configuration store)</span></span>  
  
-   <span data-ttu-id="ae997-109">與分支機構系統管理員群組相同的管理帳戶。</span><span class="sxs-lookup"><span data-stu-id="ae997-109">Administration account same as affiliate administrators group.</span></span> <span data-ttu-id="ae997-110">(指定這個旗標會永遠使用分支機構系統管理員群組做為此分支機構應用程式的系統管理員帳戶)</span><span class="sxs-lookup"><span data-stu-id="ae997-110">(Specifying this flag will always use the affiliate administrators group as the administrator account for this affiliate application)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ae997-111">您可以將 allowLocalAccounts 旗標設為 [是]，以使用系統管理員帳戶和使用者帳戶的本機帳戶。</span><span class="sxs-lookup"><span data-stu-id="ae997-111">You can use local accounts for the administration account and user account by setting the allowLocalAccounts flag to yes.</span></span> <span data-ttu-id="ae997-112">不過，您應該只在單一電腦的情況下使用這個旗標。</span><span class="sxs-lookup"><span data-stu-id="ae997-112">However, you should only use this flag in single-computer scenarios.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ae997-113">您必須是 SSO 系統管理員或 SSO 分支機構系統管理員，才能執行這項工作。</span><span class="sxs-lookup"><span data-stu-id="ae997-113">You must be an SSO administrator or SSO affiliate administrator to perform this task.</span></span>  
  
 <span data-ttu-id="ae997-114">建立分支機構應用程式後，您必須啟用它。</span><span class="sxs-lookup"><span data-stu-id="ae997-114">After you create the affiliate application, you must enable it.</span></span> <span data-ttu-id="ae997-115">如需詳細資訊，請參閱 <<c0> [ 如何啟用分支機構應用程式](../core/how-to-enable-an-affiliate-application.md)。</span><span class="sxs-lookup"><span data-stu-id="ae997-115">For more information, see [How to Enable an Affiliate Application](../core/how-to-enable-an-affiliate-application.md).</span></span>  
  
### <a name="to-create-an-affiliate-application-using-the-mmc-snap-in"></a><span data-ttu-id="ae997-116">若要使用 MMC 嵌入式管理單元建立分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="ae997-116">To create an affiliate application using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="ae997-117">上**開始**功能表上，按一下**程式**，按一下  **Microsoft 企業單一登入**，然後按一下**SSO 管理**。</span><span class="sxs-lookup"><span data-stu-id="ae997-117">On the **Start** menu, click **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="ae997-118">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="ae997-118">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="ae997-119">以滑鼠右鍵按一下**分支機構應用程式**，然後按一下**建立應用程式**。</span><span class="sxs-lookup"><span data-stu-id="ae997-119">Right-click **Affiliate Applications**, and then click **Create Application**.</span></span>  
  
4.  <span data-ttu-id="ae997-120">請依照下列中的指示**企業單一登入應用程式精靈**。</span><span class="sxs-lookup"><span data-stu-id="ae997-120">Follow the instructions in the **Enterprise Single Sign-On Application Wizard**.</span></span>  
  
### <a name="to-create-an-affiliate-application-using-the-command-line"></a><span data-ttu-id="ae997-121">使用命令列建立分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="ae997-121">To create an affiliate application using the command line</span></span>  
  
1. <span data-ttu-id="ae997-122">在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="ae997-122">On the **Start** menu, click **run**, and then type **cmd**.</span></span>  
  
2. <span data-ttu-id="ae997-123">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="ae997-123">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="ae997-124">預設的安裝目錄*\<磁碟機\>*: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="ae997-124">The default installation directory is *\<drive\>*:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3. <span data-ttu-id="ae997-125">類型 * * ssomanage – createapps *\<應用程式檔案名稱\>**<em>，其中 *\<應用程式檔案名稱\></em>是 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="ae997-125">Type **ssomanage –createapps *\<application file name\>**<em>, where *\<application file name\></em> is the XML file.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="ae997-126">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="ae997-126">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae997-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae997-127">See Also</span></span>  
 <span data-ttu-id="ae997-128">[SSO 分支機構應用程式](../core/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="ae997-128">[SSO Affiliate Applications](../core/sso-affiliate-applications.md) </span></span>  
 <span data-ttu-id="ae997-129">[如何啟用分支機構應用程式](../core/how-to-enable-an-affiliate-application.md) </span><span class="sxs-lookup"><span data-stu-id="ae997-129">[How to Enable an Affiliate Application](../core/how-to-enable-an-affiliate-application.md) </span></span>  
 <span data-ttu-id="ae997-130">[如何刪除分支機構應用程式](../core/how-to-delete-an-affiliate-application.md) </span><span class="sxs-lookup"><span data-stu-id="ae997-130">[How to Delete an Affiliate Application](../core/how-to-delete-an-affiliate-application.md) </span></span>  
 <span data-ttu-id="ae997-131">[管理使用者對應](../core/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="ae997-131">[Managing User Mappings](../core/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="ae997-132">管理分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="ae997-132">Managing Affiliate Applications</span></span>](../core/managing-affiliate-applications.md)