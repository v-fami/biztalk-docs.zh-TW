---
title: 如何建立 BizTalk Server WCF 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7ddaeb72-d263-4291-bd79-485fc736e6e7
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ebe1bbb9282db88f1b4370cea4b59ff4fcbfe6a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249342"
---
# <a name="how-to-create-a-wcf-adapter-for-biztalk-server"></a><span data-ttu-id="afd6f-102">如何建立 BizTalk Server 的 WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="afd6f-102">How to Create a WCF Adapter for BizTalk Server</span></span>
<span data-ttu-id="afd6f-103">建立 BizTalk [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] 配接器可分為三個部分。</span><span class="sxs-lookup"><span data-stu-id="afd6f-103">There are three parts to creating a BizTalk [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] adapter.</span></span>  
  
-   <span data-ttu-id="afd6f-104">使用「BizTalk [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 服務發佈精靈」建立 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Web 服務。</span><span class="sxs-lookup"><span data-stu-id="afd6f-104">Create a [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Web service using the BizTalk [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Service Publishing Wizard.</span></span> <span data-ttu-id="afd6f-105">如需使用 「 BizTalk[!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]服務發佈精靈 」，請參閱[發佈 WCF 服務](../core/publishing-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="afd6f-105">For information about using the BizTalk [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Service Publishing Wizard, see [Publishing WCF Services](../core/publishing-wcf-services.md).</span></span>  
  
-   <span data-ttu-id="afd6f-106">使用「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台」來設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收與傳送位置以及連接埠。</span><span class="sxs-lookup"><span data-stu-id="afd6f-106">Configure the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive and send locations and ports by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="afd6f-107">如需如何執行此動作的範例，請參閱[如何設定接收和傳送位置以及連接埠的 BAM WCF 攔截](../core/how-to-configure-receive-and-send-locations-and-ports-for-bam-wcf-interception.md)。</span><span class="sxs-lookup"><span data-stu-id="afd6f-107">For an example of how to do this, see [How to Configure Receive and Send Locations and Ports for BAM WCF Interception](../core/how-to-configure-receive-and-send-locations-and-ports-for-bam-wcf-interception.md).</span></span>  
  
-   <span data-ttu-id="afd6f-108">如果您是在 IIS 中裝載方案，您必須使用「IIS 管理員」設定 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Web 服務。</span><span class="sxs-lookup"><span data-stu-id="afd6f-108">If you are hosting your solution in IIS, you must configure the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Web service by using IIS Manager.</span></span>  
  
    -   <span data-ttu-id="afd6f-109">您必須授與權限給應用程式集區使用者。</span><span class="sxs-lookup"><span data-stu-id="afd6f-109">You must grant permissions to the App pool user.</span></span> <span data-ttu-id="afd6f-110">若要這樣做，請參閱[IIS 模擬的安全性考量](../core/security-considerations-for-iis-impersonation.md)。</span><span class="sxs-lookup"><span data-stu-id="afd6f-110">To do this, see [Security Considerations for IIS Impersonation](../core/security-considerations-for-iis-impersonation.md).</span></span>  
  
    -   <span data-ttu-id="afd6f-111">您必須依照下列程序所述，設定應用程式的目錄安全性。</span><span class="sxs-lookup"><span data-stu-id="afd6f-111">You must set the directory security for your application as described in the following procedure.</span></span>  
  
## <a name="setting-the-directory-security"></a><span data-ttu-id="afd6f-112">設定目錄安全性</span><span class="sxs-lookup"><span data-stu-id="afd6f-112">Setting the Directory Security</span></span>  
 <span data-ttu-id="afd6f-113">確定 [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] 服務的「目錄安全性存取控制」允許匿名存取，這樣可簡化應用程式的存取。</span><span class="sxs-lookup"><span data-stu-id="afd6f-113">Ensure that the Directory Security Access Control for the [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service allows for anonymous access; this simplifies the application access.</span></span>  
  
 <span data-ttu-id="afd6f-114">例如，您的應用程式名為 MyBizTalkService3，而且 [預設的網站] 中有 MyBizTalkService3，則請遵循這個程序來設定存取控制。</span><span class="sxs-lookup"><span data-stu-id="afd6f-114">For example, if your application is named MyBizTalkService3 and you have a MyBizTalkService3 that is in Default Websites, you would follow this procedure to set the access control.</span></span>  
  
#### <a name="to-set-the-access-control-in-windows-server-2008"></a><span data-ttu-id="afd6f-115">若要在 Windows Server 2008 中設定存取控制</span><span class="sxs-lookup"><span data-stu-id="afd6f-115">To set the access control in Windows Server 2008</span></span>  
  
1.  <span data-ttu-id="afd6f-116">按一下**啟動**，按一下 **所有程式**，依序展開**系統管理工具**，然後按一下 **網際網路資訊服務 (IIS) 管理員**.</span><span class="sxs-lookup"><span data-stu-id="afd6f-116">Click **Start**, click **All Programs**, expand **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="afd6f-117">在網際網路資訊服務 (IIS) 管理員 視窗中，展開您的伺服器名稱，再展開**網站**，依序展開**Internet Information Services**，然後展開**Default Web Site**.</span><span class="sxs-lookup"><span data-stu-id="afd6f-117">In the Internet Information Services (IIS) Manager window, expand your server name, expand **Sites**, expand **Internet Information Services**, and then expand **Default Web Site**.</span></span>  
  
3.  <span data-ttu-id="afd6f-118">以滑鼠右鍵按一下**MyBizTalkService3**，然後按一下 **編輯權限**。</span><span class="sxs-lookup"><span data-stu-id="afd6f-118">Right-click **MyBizTalkService3**, and then click **Edit Permissions**.</span></span>  
  
4.  <span data-ttu-id="afd6f-119">在**安全性** 索引標籤**MyBizTalkService3 屬性**對話方塊中，按一下 **編輯**。</span><span class="sxs-lookup"><span data-stu-id="afd6f-119">On the **Security** tab of the **MyBizTalkService3 Properties** dialog box, click **Edit**.</span></span>  
  
5.  <span data-ttu-id="afd6f-120">在**MyBizTalkService3 的權限**對話方塊中，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="afd6f-120">In the **Permissions for MyBizTalkService3** dialog box, click **Add**.</span></span>  
  
6.  <span data-ttu-id="afd6f-121">在**選取使用者、 電腦或群組**] 對話方塊中，輸入`anonymous logon`，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="afd6f-121">In the **Select Users, Computers, or Groups** dialog box, type `anonymous logon` and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="afd6f-122">選取**ANONYMOUS LOGON**中**群組或使用者名稱**區段中，選取**讀取 & 執行**中**匿名登入的權限**區段，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="afd6f-122">Select **ANONYMOUS LOGON** in the **Group or user names** section, select **Read & execute** in the **Permissions for ANONYMOUS LOGON** section, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="afd6f-123">按一下**確定**關閉 **[MyBizTalkService3 屬性**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="afd6f-123">Click **OK** to close the **MyBizTalkService3 Properties** dialog box.</span></span>  
  
 <span data-ttu-id="afd6f-124">若要確認服務已正確設定，以滑鼠右鍵按一下服務，然後**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="afd6f-124">To confirm that the service is configured correctly, right-click the service, and then click **Browse**.</span></span>  
  
 <span data-ttu-id="afd6f-125">如果服務的設定正確，您所看到的畫面會與以下相似。</span><span class="sxs-lookup"><span data-stu-id="afd6f-125">If the service is configured correctly, you will see a screen similar to the one below.</span></span>  
  
 <span data-ttu-id="afd6f-126">![BizTalkServiceInstance 服務畫面](../core/media/ff0e4ba0-59e7-47d9-a252-2859179f5645.gif "ff0e4ba0-59e7-47d9-a252-2859179f5645")</span><span class="sxs-lookup"><span data-stu-id="afd6f-126">![BizTalkServiceInstance Service Screen](../core/media/ff0e4ba0-59e7-47d9-a252-2859179f5645.gif "ff0e4ba0-59e7-47d9-a252-2859179f5645")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afd6f-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="afd6f-127">See Also</span></span>  
 [<span data-ttu-id="afd6f-128">設定 WCF 配接器攔截 BAM 資料</span><span class="sxs-lookup"><span data-stu-id="afd6f-128">Configuring the WCF Adapter to Intercept BAM Data</span></span>](../core/configuring-the-wcf-adapter-to-intercept-bam-data.md)