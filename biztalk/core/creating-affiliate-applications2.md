---
title: "建立分支機構 Applications2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Single Sign-On, creating tickets
- creating affiliate applications
- tickets, SSO
- affiliate applications, enabling XML
- affiliate applications, creating
- SSO tickets
ms.assetid: 95151163-5aaf-4683-afb7-02949ccda3e1
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f39fbbfb62a9081937891b98e2b01a5e7f046e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-affiliate-applications"></a><span data-ttu-id="c0480-102">建立分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="c0480-102">Creating Affiliate Applications</span></span>
<span data-ttu-id="c0480-103">下列步驟說明，如何開始使用分支機構應用程式和單一登入 (SSO)。</span><span class="sxs-lookup"><span data-stu-id="c0480-103">The following steps show how to start using affiliate applications and Single Sign-On (SSO).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c0480-104">收到 SSO 錯誤時，請確認您設定 BizTalk Server 時有使用網域帳戶，因為企業單一登入服務的功能會受影響。</span><span class="sxs-lookup"><span data-stu-id="c0480-104">If you receive SSO errors, verify that you used a domain account when you were configuring BizTalk Server, as this affects the function of the Enterprise SSO service.</span></span> <span data-ttu-id="c0480-105">SSO 僅能在網域帳戶運作。</span><span class="sxs-lookup"><span data-stu-id="c0480-105">SSO only functions under a domain account.</span></span>  
  
### <a name="to-create-an-affiliate-application"></a><span data-ttu-id="c0480-106">若要建立分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="c0480-106">To create an affiliate application</span></span>  
  
1.  <span data-ttu-id="c0480-107">在控制台中開啟**服務**，並確認企業單一登入服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="c0480-107">In Control Panel, open **Services**, and verify that the Enterprise Single Sign-On service is running.</span></span>  
  
2.  <span data-ttu-id="c0480-108">在命令提示中，將目錄變更為 [Enterprise Single Sign-On] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c0480-108">In a command prompt, change directories to the Enterprise Single Sign-On folder.</span></span>  
  
     <span data-ttu-id="c0480-109">例如：</span><span class="sxs-lookup"><span data-stu-id="c0480-109">For example:</span></span>  
  
     <span data-ttu-id="c0480-110">**C:\Program Files\Common Files\Enterprise Single Sign-on >**</span><span class="sxs-lookup"><span data-stu-id="c0480-110">**C:\Program Files\Common Files\Enterprise Single Sign-On>**</span></span>  
  
3.  <span data-ttu-id="c0480-111">使用 [企業單一登入] 命令。</span><span class="sxs-lookup"><span data-stu-id="c0480-111">Use the Enterprise Single Sign-On commands.</span></span> <span data-ttu-id="c0480-112">如需命令清單，請使用**-協助**切換。</span><span class="sxs-lookup"><span data-stu-id="c0480-112">For a list of commands, use the **-help** switch.</span></span>  
  
     ![](../core/media/siebeladapter-23-sso-commands.gif "SiebelAdapter_23_SSO_Commands")  
  
4.  <span data-ttu-id="c0480-113">若要使用 *.XML 為啟動程序來建立分支機構應用程式，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="c0480-113">To create the affiliate application by using *.XML as a start, type the following command:</span></span>  
  
     `ssomanage.exe -createapps C:\SSOtest\AffiliateApplication.xml`  
  
     <span data-ttu-id="c0480-114">其中：</span><span class="sxs-lookup"><span data-stu-id="c0480-114">where:</span></span>  
  
    -   <span data-ttu-id="c0480-115">C:\SSOtest 是應用程式 XML 所在的資料夾。</span><span class="sxs-lookup"><span data-stu-id="c0480-115">C:\SSOtest is the folder that contains your application XML.</span></span>  
  
    -   <span data-ttu-id="c0480-116">AffiliateApplication.xml 就是您建立的應用程式 XML，其中包含登入資訊。</span><span class="sxs-lookup"><span data-stu-id="c0480-116">AffiliateApplication.xml is the application XML you created that contains the sign-on information.</span></span>  
  
     <span data-ttu-id="c0480-117">例如：</span><span class="sxs-lookup"><span data-stu-id="c0480-117">For example:</span></span>  
  
    ```  
    <?xml version="1.0"?>  
    <SSO>  
         <application name="PeopleSoftApp">  
              <description>PeopleSoft SSO Application</description>  
              <contact>someone@microsoft.com</contact>  
             <appUserAccount>DomainName\AppUserGroup</appUserAccount>  
              <!—-an existing group on the domain controller - >   
              <appAdminAccount>DomainName\AppAdminGroup<appAdminAccount>   
              <!-- an existing account in the domain group - >   
              <field ordinal="0" label="User ID" masked="no" />  
              <field ordinal="1" label="Password" masked="yes" />  
              <flags groupApp="no" allowTickets="yes" enableApp="yes"/>  
         </application>  
    </SSO>  
    ```  
  
## <a name="creating-single-sign-on-tickets"></a><span data-ttu-id="c0480-118">建立單一登入票證</span><span class="sxs-lookup"><span data-stu-id="c0480-118">Creating Single Sign-On Tickets</span></span>  
  
#### <a name="to-create-sso-tickets"></a><span data-ttu-id="c0480-119">若要建立 SSO 票證</span><span class="sxs-lookup"><span data-stu-id="c0480-119">To create SSO tickets</span></span>  
  
1.  <span data-ttu-id="c0480-120">輸入下列命令以控制 SSO 票證行為：</span><span class="sxs-lookup"><span data-stu-id="c0480-120">Type the following command to control SSO ticket behavior:</span></span>  
  
     `ssomanage.exe -tickets yes yes`  
  
2.  <span data-ttu-id="c0480-121">回答問題：</span><span class="sxs-lookup"><span data-stu-id="c0480-121">Answer the questions:</span></span>  
  
     `ssomanage -tickets <allowed yes | no> <validate yes | no>`  
  
     <span data-ttu-id="c0480-122">一完成就會收到確認：</span><span class="sxs-lookup"><span data-stu-id="c0480-122">On completion, you receive a confirmation:</span></span>  
  
     <span data-ttu-id="c0480-123">**在此電腦使用 SSO 伺服器。已成功完成此作業。**</span><span class="sxs-lookup"><span data-stu-id="c0480-123">**Using SSO server on this computer. The operation completed successfully.**</span></span>  
  
## <a name="enabling-the-affiliate-application-xml"></a><span data-ttu-id="c0480-124">啟用分支機構應用程式 XML</span><span class="sxs-lookup"><span data-stu-id="c0480-124">Enabling the Affiliate Application XML</span></span>  
  
#### <a name="to-enable-affiliate-application-xml"></a><span data-ttu-id="c0480-125">若要啟用分支機構應用程式 XML</span><span class="sxs-lookup"><span data-stu-id="c0480-125">To enable affiliate application XML</span></span>  
  
1.  <span data-ttu-id="c0480-126">輸入以下命令：</span><span class="sxs-lookup"><span data-stu-id="c0480-126">Type the following command:</span></span>  
  
     `ssomanage -enableapp PeopleSoftApp`  
  
2.  <span data-ttu-id="c0480-127">輸入下列命令，列出應用程式並驗證已建立的應用程式：</span><span class="sxs-lookup"><span data-stu-id="c0480-127">Type the following command to list the applications and to verify that the application was created:</span></span>  
  
     `ssoclient.exe –listapps`  
  
     <span data-ttu-id="c0480-128">列出可供使用的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="c0480-128">The affiliate applications that are available for use appear in a list.</span></span>  
  
     <span data-ttu-id="c0480-129">**IBI\YourID-PeopleSoftApp 的應用程式**</span><span class="sxs-lookup"><span data-stu-id="c0480-129">**Applications available for IBI\YourID - PeopleSoftApp**</span></span>  
  
3.  <span data-ttu-id="c0480-130">輸入下列命令，設定分支機構應用程式認證：</span><span class="sxs-lookup"><span data-stu-id="c0480-130">Type the following command to set the affiliate application credentials:</span></span>  
  
     `ssoclient.exe -setcredentials PeopleSoftApp`  
  
4.  <span data-ttu-id="c0480-131">在提示下輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="c0480-131">Enter the user name and password at the prompts.</span></span> <span data-ttu-id="c0480-132">輸入 PeopleSoftApp 分支機構應用程式的登入認證。</span><span class="sxs-lookup"><span data-stu-id="c0480-132">Enter the logon credentials for the PeopleSoftApp affiliate application.</span></span>  
  
     <span data-ttu-id="c0480-133">例如，針對透過 SSO 伺服器進入系統的使用者，輸入使用者識別和密碼。</span><span class="sxs-lookup"><span data-stu-id="c0480-133">For example, enter the user identification and the password for that user to enter into the system through the SSO server.</span></span>  
  
    -   <span data-ttu-id="c0480-134">**使用者識別碼：**`user`</span><span class="sxs-lookup"><span data-stu-id="c0480-134">**User ID:** `user`</span></span>  
  
    -   <span data-ttu-id="c0480-135">**密碼：**`******`</span><span class="sxs-lookup"><span data-stu-id="c0480-135">**Password:** `******`</span></span>  
  
    -   <span data-ttu-id="c0480-136">**確認密碼：**`******`</span><span class="sxs-lookup"><span data-stu-id="c0480-136">**Confirm? Password:** `******`</span></span>  
  
5.  <span data-ttu-id="c0480-137">分支機構應用程式會出現在 PeopleSoft Enterprise 之 BizTalk 配接器的 [傳輸屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c0480-137">The affiliate application appears in the BizTalk Adapter for PeopleSoft Enterprise Transport Properties dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0480-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0480-138">See Also</span></span>  
 [<span data-ttu-id="c0480-139">使用單一登入</span><span class="sxs-lookup"><span data-stu-id="c0480-139">Using Single Sign-On</span></span>](../core/using-single-sign-on2.md)