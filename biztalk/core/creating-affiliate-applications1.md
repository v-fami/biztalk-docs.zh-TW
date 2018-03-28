---
title: 建立分支機構應用程式的 TIBCO Rendezvous |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f3603fcb-3594-460b-b74a-618e22d9c4e0
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a286a80ef2c867dd196fcdce414f2d0ff3c8255c
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="creating-affiliate-applications"></a><span data-ttu-id="30eb2-102">建立分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="30eb2-102">Creating Affiliate Applications</span></span>
<span data-ttu-id="30eb2-103">下列步驟說明如何開始使用分支機構應用程式和單一登入 (SSO)。</span><span class="sxs-lookup"><span data-stu-id="30eb2-103">The following steps describe how to start working with affiliate applications and Single Sign-On (SSO).</span></span> <span data-ttu-id="30eb2-104">如需如何使用企業單一登入的完整資訊，請參閱 Microsoft 文件。</span><span class="sxs-lookup"><span data-stu-id="30eb2-104">For complete information about how to use Enterprise Single Sign-On, see the Microsoft documentation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30eb2-105">收到 SSO 錯誤時，請確認您設定 BizTalk Server 時有使用網域帳戶，因為企業單一登入服務的功能會受影響。</span><span class="sxs-lookup"><span data-stu-id="30eb2-105">If you receive SSO errors, verify that you used a domain account when you configured BizTalk Server, as this affects the function of the Enterprise SSO service.</span></span> <span data-ttu-id="30eb2-106">SSO 僅能在網域帳戶運作。</span><span class="sxs-lookup"><span data-stu-id="30eb2-106">SSO only functions under a domain account.</span></span>  
  
## <a name="create-an-affiliate-application"></a><span data-ttu-id="30eb2-107">建立分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="30eb2-107">Create an affiliate application</span></span>  
  
1.  <span data-ttu-id="30eb2-108">在 [控制台] 中開啟 **服務**, ，並確認企業單一登入服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="30eb2-108">In Control Panel, open **Services**, and verify that the Enterprise Single Sign-On service is running.</span></span>  
  
2.  <span data-ttu-id="30eb2-109">在命令提示中，將目錄變更為 [Enterprise Single Sign-On] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="30eb2-109">In a command prompt, change directories to the Enterprise Single Sign-On folder.</span></span> <span data-ttu-id="30eb2-110">例如：</span><span class="sxs-lookup"><span data-stu-id="30eb2-110">For example:</span></span>  
  
     <span data-ttu-id="30eb2-111">**C:\Program Files\Common Files\Enterprise Single Sign-on >**</span><span class="sxs-lookup"><span data-stu-id="30eb2-111">**C:\Program Files\Common Files\Enterprise Single Sign-On>**</span></span>  
  
3.  <span data-ttu-id="30eb2-112">使用 [企業單一登入] 命令。</span><span class="sxs-lookup"><span data-stu-id="30eb2-112">Use the Enterprise Single Sign-On commands.</span></span> <span data-ttu-id="30eb2-113">對於命令清單，請使用 **-協助** 切換。</span><span class="sxs-lookup"><span data-stu-id="30eb2-113">For a list of commands, use the **-help** switch.</span></span>  
  
4.  <span data-ttu-id="30eb2-114">若要使用 \*.XML 為啟動程序來建立分支機構應用程式，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="30eb2-114">To create the affiliate application by using \*.XML as a start, type the following command:</span></span>  
  
     `ssomanage.exe -createapps C:\SSOtest\AffiliateApplication.xml`  
  
     <span data-ttu-id="30eb2-115">其中：</span><span class="sxs-lookup"><span data-stu-id="30eb2-115">Where:</span></span>  
  
     <span data-ttu-id="30eb2-116">C:\SSOtest 是應用程式 XML 所在的資料夾。</span><span class="sxs-lookup"><span data-stu-id="30eb2-116">C:\SSOtest is the folder that contains your application XML.</span></span>  
  
     <span data-ttu-id="30eb2-117">AffiliateApplication.xml 就是您建立的應用程式 XML，其中包含登入資訊。</span><span class="sxs-lookup"><span data-stu-id="30eb2-117">AffiliateApplication.xml is the application XML you created that contains the Sign-On information.</span></span>  
  
     <span data-ttu-id="30eb2-118">例如：</span><span class="sxs-lookup"><span data-stu-id="30eb2-118">For example:</span></span>  
  
    ```  
    <?xml version="1.0"?>  
    <SSO>  
        <application name="TIBCO RendezvousApp">  
            <description> TIBCO Rendezvous SSO Application</description>  
            <contact>someone@microsoft.com</contact>  
            <userGroup>ibi\Domain Users</userGroup>  
            <!—an existing group on the domain controller - >   
            <appAdminGroup>ibi\YourID</appAdminGroup>  
            <!-- an existing account within the domain group - >   
  
            <field ordinal="0" label="User ID" masked="no" />  
            <field ordinal="1" label="Password" masked="yes" />  
            <flags groupApp="no" allowTickets="yes" enableApp="yes"/>  
  
        </application>  
    </SSO>  
    ```  
  
## <a name="create-single-sign-on-tickets"></a><span data-ttu-id="30eb2-119">建立單一登入票證</span><span class="sxs-lookup"><span data-stu-id="30eb2-119">Create Single Sign-On tickets</span></span>  
  
1.  <span data-ttu-id="30eb2-120">輸入下列命令以控制 SSO 票證行為：</span><span class="sxs-lookup"><span data-stu-id="30eb2-120">Type the following command to control SSO ticket behavior:</span></span>  
  
     `ssomanage.exe -tickets yes yes`  
  
2.  <span data-ttu-id="30eb2-121">回答如下所示的問題：</span><span class="sxs-lookup"><span data-stu-id="30eb2-121">Answer the following questions as shown:</span></span>  
  
     `ssomanage -tickets <allowed yes | no> <validate yes | no>`  
  
3.  <span data-ttu-id="30eb2-122">一完成就會收到下列確認：</span><span class="sxs-lookup"><span data-stu-id="30eb2-122">On completion, you receive the following confirmation:</span></span>  
  
     <span data-ttu-id="30eb2-123">**在此電腦使用 SSO 伺服器。作業順利完成。**</span><span class="sxs-lookup"><span data-stu-id="30eb2-123">**Using SSO server on this computer. The operation completed successfully.**</span></span>  
  
## <a name="enable-affiliate-application-xml"></a><span data-ttu-id="30eb2-124">啟用分支機構應用程式 XML</span><span class="sxs-lookup"><span data-stu-id="30eb2-124">Enable affiliate application XML</span></span>  
  
1.  <span data-ttu-id="30eb2-125">輸入以下命令：</span><span class="sxs-lookup"><span data-stu-id="30eb2-125">Type the following command:</span></span>  
  
     `ssomanage -enableapp TIBCO RendezvousApp`  
  
2.  <span data-ttu-id="30eb2-126">輸入下列命令，列出應用程式並驗證已建立的應用程式：</span><span class="sxs-lookup"><span data-stu-id="30eb2-126">Type the following command to list the applications and to verify that the application was created:</span></span>  
  
     `ssoclient.exe –listapps`  
  
     <span data-ttu-id="30eb2-127">列出可供使用的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="30eb2-127">The affiliate applications that are available for use appear in a list.</span></span>  
  
     <span data-ttu-id="30eb2-128">**IBI\YourID-TIBCO RendezvousApp 的應用程式**</span><span class="sxs-lookup"><span data-stu-id="30eb2-128">**Applications available for IBI\YourID - TIBCO RendezvousApp**</span></span>  
  
3.  <span data-ttu-id="30eb2-129">輸入下列命令，設定分支機構應用程式認證：</span><span class="sxs-lookup"><span data-stu-id="30eb2-129">Type the following command to set the affiliate application credentials:</span></span>  
  
     `ssoclient.exe -setcredentials TIBCO RendezvousApp`  
  
4.  <span data-ttu-id="30eb2-130">在提示字元中輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="30eb2-130">Enter the User name and password at the prompts.</span></span>  
  
5.  <span data-ttu-id="30eb2-131">輸入 TIBCO RendezvousApp 分支機構應用程式的登入認證。</span><span class="sxs-lookup"><span data-stu-id="30eb2-131">Enter the logon credentials for the TIBCO RendezvousApp affiliate application.</span></span>  
  
     <span data-ttu-id="30eb2-132">例如，針對透過 SSO 伺服器進入系統的使用者，輸入使用者識別和密碼。</span><span class="sxs-lookup"><span data-stu-id="30eb2-132">For example, enter the user identification and the password for the user to enter into the system through the SSO server.</span></span>  
  
    -   <span data-ttu-id="30eb2-133">使用者識別碼：user</span><span class="sxs-lookup"><span data-stu-id="30eb2-133">User ID: user</span></span>  
  
    -   <span data-ttu-id="30eb2-134">密碼：******</span><span class="sxs-lookup"><span data-stu-id="30eb2-134">Password: ******</span></span>  
  
    -   <span data-ttu-id="30eb2-135">確認密碼: \* \* \*</span><span class="sxs-lookup"><span data-stu-id="30eb2-135">Confirm Password: ******</span></span>  
  
6.  <span data-ttu-id="30eb2-136">分支機構應用程式會出現在 BizTalk Adapter for TIBCO Rendezvous **傳輸屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="30eb2-136">The affiliate application appears in the BizTalk Adapter for TIBCO Rendezvous **Transport Properties** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30eb2-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30eb2-137">See Also</span></span>  
 [<span data-ttu-id="30eb2-138">BizTalk Adapter for TIBCO Rendezvous 中的安全性</span><span class="sxs-lookup"><span data-stu-id="30eb2-138">Security in BizTalk Adapter for TIBCO Rendezvous</span></span>](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md)   