---
title: "如何更新分支機構應用程式的屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [SSO applications], updating properties
- applications [SSO], properties
ms.assetid: b06eefdd-a5ca-4a32-93d7-72246e31a2e4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ef4a2fb99d423f7c7ccb08cec58c3c49928e1ed
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-update-the-properties-of-an-affiliate-application"></a><span data-ttu-id="4d2fa-102">如何更新分支機構應用程式的內容</span><span class="sxs-lookup"><span data-stu-id="4d2fa-102">How to Update the Properties of an Affiliate Application</span></span>
<span data-ttu-id="4d2fa-103">您可以使用 MMC 嵌入式管理單元或此命令來更新一或多個應用程式屬性，如 XML 檔案所指定。</span><span class="sxs-lookup"><span data-stu-id="4d2fa-103">You can use the MMC Snap-In or this command to update one or more application properties, as specified by the XML file.</span></span> <span data-ttu-id="4d2fa-104">您必須是分支機構系統管理員，才能執行此工作。</span><span class="sxs-lookup"><span data-stu-id="4d2fa-104">You must be an Affiliate Administrator to perform this task.</span></span> <span data-ttu-id="4d2fa-105">下列是一個範例 XML 檔案，其中列出您可以更新的欄位。</span><span class="sxs-lookup"><span data-stu-id="4d2fa-105">The following is an example XML file that lists the fields you can update.</span></span>  
  
```  
<SSO>  
<application name="SSOApplication">  
<description>An SSO Application</description>  
<contact>someone@companyname.com</contact>  
<appUserAccount>DomainName\AppUserGroup</appUserAccount>  
<appAdminAccount>DomainName\AppAdminGroup</appAdminAccount>  
<flags allowTickets="no" validateTickets="yes"  timeoutTickets="yes" enableApp="no" />  
</application>  
</SSO>  
  
```  
  
 <span data-ttu-id="4d2fa-106">建立分支機構應用程式後，無法修改以下屬性：</span><span class="sxs-lookup"><span data-stu-id="4d2fa-106">After you create an affiliate application, you cannot modify the following properties:</span></span>  
  
-   <span data-ttu-id="4d2fa-107">分支機構應用程式的名稱</span><span class="sxs-lookup"><span data-stu-id="4d2fa-107">Name of the affiliate application</span></span>  
  
-   <span data-ttu-id="4d2fa-108">與分支機構應用程式關聯的欄位</span><span class="sxs-lookup"><span data-stu-id="4d2fa-108">Fields associated with the affiliate application</span></span>  
  
-   <span data-ttu-id="4d2fa-109">分支機構應用程式類型 (主控件群組、個別或組態存放區)</span><span class="sxs-lookup"><span data-stu-id="4d2fa-109">Affiliate application type (host group, individual, or configuration store)</span></span>  
  
-   <span data-ttu-id="4d2fa-110">與分支機構系統管理員群組相同的管理帳戶。</span><span class="sxs-lookup"><span data-stu-id="4d2fa-110">Administration account same as affiliate administrators group.</span></span> <span data-ttu-id="4d2fa-111">(指定這個旗標會永遠使用分支機構系統管理員群組做為此分支機構應用程式的系統管理員帳戶)</span><span class="sxs-lookup"><span data-stu-id="4d2fa-111">(Specifying this flag will always use the affiliate administrators group as the administrator account for this affiliate application)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4d2fa-112">您可以將 allowLocalAccounts 旗標設為 [是]，以使用系統管理員帳戶和使用者帳戶的本機帳戶。</span><span class="sxs-lookup"><span data-stu-id="4d2fa-112">You can use local accounts for the administration account and user account by setting the allowLocalAccounts flag to yes.</span></span> <span data-ttu-id="4d2fa-113">不過，您只可以在單一電腦的情況下使用這個旗標。</span><span class="sxs-lookup"><span data-stu-id="4d2fa-113">However, you can only use this flag in single-computer scenarios.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4d2fa-114">您必須是 SSO 系統管理員、SSO 分支機構系統管理員或應用程式系統管理員，才能執行這項工作。</span><span class="sxs-lookup"><span data-stu-id="4d2fa-114">You must be an SSO administrator, SSO affiliate administrator, or application administrator to perform this task.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4d2fa-115">您必須是 SSO 系統管理員才能修改票證旗標 (validateTickets 和 timeoutTickets)。</span><span class="sxs-lookup"><span data-stu-id="4d2fa-115">You must be an SSO administrator to modify the ticketing flags (validateTickets and timeoutTickets).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4d2fa-116">您必須是 SSO 系統管理員或 SSO 分支機構系統管理員，才能修改應用程式管理帳戶。</span><span class="sxs-lookup"><span data-stu-id="4d2fa-116">You must be an SSO administrator or an SSO affiliate administrator to modify the application administration account.</span></span>  
  
### <a name="to-update-the-properties-of-an-affiliate-application-using-the-mmc-snap-in"></a><span data-ttu-id="4d2fa-117">若要使用 MMC 嵌入式管理單元更新分支機構應用程式的屬性</span><span class="sxs-lookup"><span data-stu-id="4d2fa-117">To update the properties of an affiliate application using the MMC Snap-In</span></span>  
  
1.  <span data-ttu-id="4d2fa-118">上**啟動**功能表上，按一下 **程式**，按一下  **Microsoft 企業單一登入**，然後按一下  **SSO 管理**。</span><span class="sxs-lookup"><span data-stu-id="4d2fa-118">On the **Start** menu, click **Programs**, click **Microsoft Enterprise Single Sign-On**, and then click **SSO Administration**.</span></span>  
  
2.  <span data-ttu-id="4d2fa-119">在 ENTSSO MMC 嵌入式管理單元的範圍窗格中，展開 **[企業單一登入]** 節點。</span><span class="sxs-lookup"><span data-stu-id="4d2fa-119">In the scope pane of the ENTSSO MMC Snap-In, expand the **Enterprise Single Sign-On** node.</span></span>  
  
3.  <span data-ttu-id="4d2fa-120">以滑鼠右鍵按一下分支機構應用程式，然後按一下**更新**。</span><span class="sxs-lookup"><span data-stu-id="4d2fa-120">Right-click the affililate application, and then click **Update**.</span></span>  
  
### <a name="to-update-the-properties-of-an-affiliate-application-using-the-command-line"></a><span data-ttu-id="4d2fa-121">使用命令列更新分支機構應用程式的屬性</span><span class="sxs-lookup"><span data-stu-id="4d2fa-121">To update the properties of an affiliate application using the command line</span></span>  
  
1.  <span data-ttu-id="4d2fa-122">在**啟動**功能表上，按一下 **執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="4d2fa-122">On the **Start** menu, click **run**, and then type **cmd**.</span></span>  
  
2.  <span data-ttu-id="4d2fa-123">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="4d2fa-123">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="4d2fa-124">預設安裝目錄是**\<磁碟機\>**: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="4d2fa-124">The default installation directory is **\<drive\>**:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3.  <span data-ttu-id="4d2fa-125">型別**ssomanage – updateapps\<應用程式檔案名稱\>**，其中應用程式檔案名稱是 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="4d2fa-125">Type **ssomanage –updateapps \<application file name\>**, where the application file name is the XML file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4d2fa-126">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="4d2fa-126">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d2fa-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="4d2fa-127">See Also</span></span>  
 <span data-ttu-id="4d2fa-128">[SSO 分支機構應用程式](../core/sso-affiliate-applications.md) </span><span class="sxs-lookup"><span data-stu-id="4d2fa-128">[SSO Affiliate Applications](../core/sso-affiliate-applications.md) </span></span>  
 <span data-ttu-id="4d2fa-129">[如何啟用分支機構應用程式](../core/how-to-enable-an-affiliate-application.md) </span><span class="sxs-lookup"><span data-stu-id="4d2fa-129">[How to Enable an Affiliate Application](../core/how-to-enable-an-affiliate-application.md) </span></span>  
 <span data-ttu-id="4d2fa-130">[管理使用者對應](../core/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="4d2fa-130">[Managing User Mappings](../core/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="4d2fa-131">管理分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="4d2fa-131">Managing Affiliate Applications</span></span>](../core/managing-affiliate-applications.md)