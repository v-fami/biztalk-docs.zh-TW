---
title: 如何列出分支機構應用程式屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- applications [SSO], listing properties
- managing [SSO applications], listing properties
ms.assetid: a120acd7-2f0b-4c72-8a8a-f8e500a773c8
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5920263006a9188da83f82dcf65dad8fb8faada
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002719"
---
# <a name="how-to-list-the-properties-of-an-affiliate-application"></a><span data-ttu-id="8672b-102">如何列出分支機構應用程式屬性</span><span class="sxs-lookup"><span data-stu-id="8672b-102">How to List the Properties of an Affiliate Application</span></span>
<span data-ttu-id="8672b-103">此命令顯示分支機構應用程式的下列相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8672b-103">This command shows the following information about the affiliate application.</span></span> <span data-ttu-id="8672b-104">如需分支機構應用程式屬性的詳細資訊，請參閱[SSO 分支機構應用程式](../core/sso-affiliate-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="8672b-104">For more information about the properties for an affiliate application, see [SSO Affiliate Applications](../core/sso-affiliate-applications.md).</span></span>  
  
 <span data-ttu-id="8672b-105">SSO 系統從 xml 檔案取得您用來更新分支機構應用程式的這項資訊。</span><span class="sxs-lookup"><span data-stu-id="8672b-105">The SSO system obtains this information from the xml file that you used to update the affiliate application.</span></span> <span data-ttu-id="8672b-106">如需詳細資訊，請參閱 <<c0> [ 如何更新分支機構應用程式的內容](../core/how-to-update-the-properties-of-an-affiliate-application.md)。</span><span class="sxs-lookup"><span data-stu-id="8672b-106">For more information, see [How to Update the Properties of an Affiliate Application](../core/how-to-update-the-properties-of-an-affiliate-application.md).</span></span>  
  
### <a name="to-display-the-properties-of-an-affiliate-application-using-the-administration-utility"></a><span data-ttu-id="8672b-107">使用管理公用程式顯示分支機構應用程式的屬性</span><span class="sxs-lookup"><span data-stu-id="8672b-107">To display the properties of an affiliate application using the administration utility</span></span>  
  
1. <span data-ttu-id="8672b-108">在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="8672b-108">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2. <span data-ttu-id="8672b-109">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="8672b-109">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="8672b-110">預設的安裝目錄\<*磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="8672b-110">The default installation directory is \<*drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3. <span data-ttu-id="8672b-111">類型 * * ssomanage-displayapp *\<應用程式名稱\>**<em>，其中 *\<應用程式名稱\></em>是您想要顯示的分支機構應用程式名稱屬性。</span><span class="sxs-lookup"><span data-stu-id="8672b-111">Type **ssomanage –displayapp *\<application name\>**<em>, where *\<application name\></em> is the name of the Affiliate Application you want to display the properties for.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="8672b-112">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="8672b-112">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
### <a name="to-display-the-properties-of-an-affiliate-application-using-the-client-utility"></a><span data-ttu-id="8672b-113">使用用戶端公用程式顯示分支機構應用程式的屬性</span><span class="sxs-lookup"><span data-stu-id="8672b-113">To display the properties of an affiliate application using the client utility</span></span>  
  
1. <span data-ttu-id="8672b-114">在上**開始**功能表上，按一下**執行**，然後輸入**cmd**。</span><span class="sxs-lookup"><span data-stu-id="8672b-114">On the **Start** menu, click **Run**, and then type **cmd**.</span></span>  
  
2. <span data-ttu-id="8672b-115">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="8672b-115">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="8672b-116">預設的安裝目錄\<*安裝磁碟機*\>: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="8672b-116">The default installation directory is \<*install drive*\>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
3. <span data-ttu-id="8672b-117">類型 * * ssoclient-displayapp *\<應用程式名稱\>**<em>，其中 *\<應用程式名稱\></em>是您想要顯示的分支機構應用程式名稱屬性。</span><span class="sxs-lookup"><span data-stu-id="8672b-117">Type **ssoclient –displayapp *\<application name\>**<em>, where *\<application name\></em> is the name of the Affiliate Application you want to display the properties for.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="8672b-118">在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。</span><span class="sxs-lookup"><span data-stu-id="8672b-118">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8672b-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8672b-119">See Also</span></span>  
 <span data-ttu-id="8672b-120">[管理使用者對應](../core/managing-user-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="8672b-120">[Managing User Mappings](../core/managing-user-mappings.md) </span></span>  
 [<span data-ttu-id="8672b-121">管理分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="8672b-121">Managing Affiliate Applications</span></span>](../core/managing-affiliate-applications.md)