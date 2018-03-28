---
title: 建立分支機構 Applications3 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- affiliate applications
- Single Sign-On, creating tickets
- tickets, creating Single Sign-On
- affiliate applications, creating
- SSO tickets
ms.assetid: 800644fd-2286-4e59-894b-260f584dd29f
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 857ee7edd623332e72176ac09082f0ec9fc460f4
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="creating-affiliate-applications"></a><span data-ttu-id="2cb79-102">建立分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="2cb79-102">Creating Affiliate Applications</span></span>
<span data-ttu-id="2cb79-103">下列步驟說明如何開始使用採用單一登入 (SSO) 的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="2cb79-103">The following steps describe how to get started with affiliate applications using Single Sign-On (SSO).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2cb79-104">收到 SSO 錯誤時，請確認您設定 BizTalk Server 時有使用網域帳戶，因為 ESSO 服務的功能會受影響。</span><span class="sxs-lookup"><span data-stu-id="2cb79-104">If you get SSO errors, verify that you used a domain account when you configured BizTalk Server, because this affects the function of the ESSO service.</span></span> <span data-ttu-id="2cb79-105">SSO 僅能在網域帳戶運作。</span><span class="sxs-lookup"><span data-stu-id="2cb79-105">SSO only functions under a domain account.</span></span>  
  
## <a name="creating-an-affiliate-application"></a><span data-ttu-id="2cb79-106">建立分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="2cb79-106">Creating an Affiliate Application</span></span>  
  
#### <a name="to-create-an-affiliate-application"></a><span data-ttu-id="2cb79-107">若要建立分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="2cb79-107">To create an affiliate application</span></span>  
  
1.  <span data-ttu-id="2cb79-108">在 **控制台**, ，開啟 **服務**, ，並確認企業單一登入服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="2cb79-108">In **Control Panel**, open **Services**, and verify that the Enterprise Single Sign-On service is running.</span></span>  
  
2.  <span data-ttu-id="2cb79-109">在命令提示中，將目錄變更為 [Enterprise Single Sign-On] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2cb79-109">In a command prompt, change directories to the Enterprise Single Sign-On folder.</span></span>  
  
     <span data-ttu-id="2cb79-110">例如：</span><span class="sxs-lookup"><span data-stu-id="2cb79-110">For example:</span></span>  
  
     <span data-ttu-id="2cb79-111">**C:\Program Files\Common Files\Enterprise Single Sign-on >**</span><span class="sxs-lookup"><span data-stu-id="2cb79-111">**C:\Program Files\Common Files\Enterprise Single Sign-On>**</span></span>  
  
3.  <span data-ttu-id="2cb79-112">使用 [企業單一登入] 命令。</span><span class="sxs-lookup"><span data-stu-id="2cb79-112">Use the Enterprise Single Sign-On commands.</span></span> <span data-ttu-id="2cb79-113">如需命令清單，請使用 -help 切換參數。</span><span class="sxs-lookup"><span data-stu-id="2cb79-113">For a list of commands, use the -help switch.</span></span>  
  
     <span data-ttu-id="2cb79-114">![](../core/media/siebeladapter-23-sso-commands.gif "SiebelAdapter_23_SSO_Commands")</span><span class="sxs-lookup"><span data-stu-id="2cb79-114">![](../core/media/siebeladapter-23-sso-commands.gif "SiebelAdapter_23_SSO_Commands")</span></span>  
  
4.  <span data-ttu-id="2cb79-115">若要以 \*.XML 開始建立分支機構應用程式，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="2cb79-115">To create the affiliate application using the \*.XML as a beginning, type in the following command:</span></span>  
  
     <span data-ttu-id="2cb79-116">**ssomanage.exe createapps C:\SSOtest\AffiliateApplication.xml**</span><span class="sxs-lookup"><span data-stu-id="2cb79-116">**ssomanage.exe -createapps C:\SSOtest\AffiliateApplication.xml**</span></span>  
  
     <span data-ttu-id="2cb79-117">其中：</span><span class="sxs-lookup"><span data-stu-id="2cb79-117">where:</span></span>  
  
     <span data-ttu-id="2cb79-118">C:\SSOtest 是應用程式 XML 所在的資料夾。</span><span class="sxs-lookup"><span data-stu-id="2cb79-118">C:\SSOtest is the folder containing your application XML.</span></span>  
  
     <span data-ttu-id="2cb79-119">AffiliateApplication.xml 就是您建立的應用程式 XML，其中包含登入資訊。</span><span class="sxs-lookup"><span data-stu-id="2cb79-119">AffiliateApplication.xml is the application XML you created containing the Sign On information.</span></span>  
  
     <span data-ttu-id="2cb79-120">例如：</span><span class="sxs-lookup"><span data-stu-id="2cb79-120">For example:</span></span>  
  
    ```  
    <?xml version="1.0"?>  
    <SSO>  
         <application name="JDEdwardsApp">  
              <description>JDEdwards SSO Application</description>  
              <contact>someone@microsoft.com</contact>  
              <userGroup>ibi\Domain Users</userGroup>  
              <!—-an existing group on the domain controller - >   
              <appAdminGroup>ibi\YourID</appAdminGroup>  
              <!-- an existing account within the domain group - >   
              <field ordinal="0" label="User ID" masked="no" />  
              <field ordinal="1" label="Password" masked="yes" />  
              <flags groupApp="no" allowTickets="yes" enableApp="yes"/>  
         </application>  
    </SSO>  
    ```  
  
## <a name="creating-single-sign-on-tickets"></a><span data-ttu-id="2cb79-121">建立單一登入票證</span><span class="sxs-lookup"><span data-stu-id="2cb79-121">Creating Single Sign-On Tickets</span></span>  
  
#### <a name="to-create-sso-tickets"></a><span data-ttu-id="2cb79-122">若要建立 SSO 票證</span><span class="sxs-lookup"><span data-stu-id="2cb79-122">To create SSO tickets</span></span>  
  
1.  <span data-ttu-id="2cb79-123">輸入下列命令以控制 SSO 票證行為：</span><span class="sxs-lookup"><span data-stu-id="2cb79-123">Type in the following command to control SSO ticket behavior:</span></span>  
  
     `ssomanage.exe -tickets yes yes`  
  
2.  <span data-ttu-id="2cb79-124">回答問題：</span><span class="sxs-lookup"><span data-stu-id="2cb79-124">Answer the questions:</span></span>  
  
     `ssomanage -tickets <allowed yes | no> <validate yes | no>`  
  
     <span data-ttu-id="2cb79-125">一完成就會收到確認：</span><span class="sxs-lookup"><span data-stu-id="2cb79-125">On completion you receive a confirmation:</span></span>  
  
     <span data-ttu-id="2cb79-126">**在此電腦使用 SSO 伺服器。作業順利完成。**</span><span class="sxs-lookup"><span data-stu-id="2cb79-126">**Using SSO server on this computer. The operation completed successfully.**</span></span>  
  
## <a name="enabling-the-affiliate-application-xml"></a><span data-ttu-id="2cb79-127">啟用分支機構應用程式 XML</span><span class="sxs-lookup"><span data-stu-id="2cb79-127">Enabling the Affiliate Application XML</span></span>  
  
#### <a name="to-enable-affiliate-application-xml"></a><span data-ttu-id="2cb79-128">若要啟用分支機構應用程式 XML</span><span class="sxs-lookup"><span data-stu-id="2cb79-128">To enable affiliate application XML</span></span>  
  
1.  <span data-ttu-id="2cb79-129">輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="2cb79-129">Type in the following command:</span></span>  
  
     `ssomanage -enableapp JDEdwardsApp`  
  
2.  <span data-ttu-id="2cb79-130">輸入下列命令，列出應用程式並驗證已建立的應用程式：</span><span class="sxs-lookup"><span data-stu-id="2cb79-130">Type in the following command to list the applications and to verify that the application was created:</span></span>  
  
     `ssoclient.exe –listapps`  
  
     <span data-ttu-id="2cb79-131">可供使用的分支機構應用程式隨即列在清單中。</span><span class="sxs-lookup"><span data-stu-id="2cb79-131">The Affiliate Applications available for use appear in a list.</span></span>  
  
     <span data-ttu-id="2cb79-132">**IBI\YourID-JDEdwardsApp 的應用程式**</span><span class="sxs-lookup"><span data-stu-id="2cb79-132">**Applications available for IBI\YourID - JDEdwardsApp**</span></span>  
  
3.  <span data-ttu-id="2cb79-133">輸入下列命令，設定分支機構應用程式認證：</span><span class="sxs-lookup"><span data-stu-id="2cb79-133">Type in the following command to set the affiliate application credentials:</span></span>  
  
     `ssoclient.exe -setcredentials JDEdwardsApp`  
  
4.  <span data-ttu-id="2cb79-134">在提示下輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="2cb79-134">Enter the user name and password at the prompts.</span></span> <span data-ttu-id="2cb79-135">輸入 JDEdwardsApp 分支機構應用程式的登入認證。</span><span class="sxs-lookup"><span data-stu-id="2cb79-135">Enter the logon credentials for the JDEdwardsApp affiliate application.</span></span> <span data-ttu-id="2cb79-136">例如，針對透過 SSO 伺服器進入系統的使用者，輸入使用者識別和密碼。</span><span class="sxs-lookup"><span data-stu-id="2cb79-136">For example, enter the user identification and the password for that user to enter into the system through the SSO server.</span></span>  
  
    -   <span data-ttu-id="2cb79-137">**使用者識別碼︰** 使用者</span><span class="sxs-lookup"><span data-stu-id="2cb79-137">**User ID:** user</span></span>  
  
    -   <span data-ttu-id="2cb79-138">**密碼︰** ******</span><span class="sxs-lookup"><span data-stu-id="2cb79-138">**Password:** ******</span></span>  
  
    -   <span data-ttu-id="2cb79-139">**確認密碼︰** ******</span><span class="sxs-lookup"><span data-stu-id="2cb79-139">**Confirm? Password:** ******</span></span>  
  
5.  <span data-ttu-id="2cb79-140">分支機構應用程式會出現在 BizTalk Adapter for JD Edwards OneWorld 的 [傳輸屬性] 對話方塊的下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="2cb79-140">The affiliate application appears in the drop-down list of the BizTalk Adapter for JD Edwards OneWorld Transport Properties dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cb79-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2cb79-141">See Also</span></span>  
 [<span data-ttu-id="2cb79-142">在配接器的安全性</span><span class="sxs-lookup"><span data-stu-id="2cb79-142">Security in the adapter</span></span>](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)