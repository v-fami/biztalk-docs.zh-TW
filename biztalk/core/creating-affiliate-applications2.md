---
title: "建立 PeopleSoft Enterprise 的分支機構應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95151163-5aaf-4683-afb7-02949ccda3e1
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a77926fa9d98606770ad2fe7715a3b0ff66ea5c
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="creating-affiliate-applications"></a><span data-ttu-id="7d9fe-102">建立分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="7d9fe-102">Creating Affiliate Applications</span></span>
<span data-ttu-id="7d9fe-103">下列步驟說明，如何開始使用分支機構應用程式和單一登入 (SSO)。</span><span class="sxs-lookup"><span data-stu-id="7d9fe-103">The following steps show how to start using affiliate applications and Single Sign-On (SSO).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d9fe-104">收到 SSO 錯誤時，請確認您設定 BizTalk Server 時有使用網域帳戶，因為企業單一登入服務的功能會受影響。</span><span class="sxs-lookup"><span data-stu-id="7d9fe-104">If you receive SSO errors, verify that you used a domain account when you were configuring BizTalk Server, as this affects the function of the Enterprise SSO service.</span></span> <span data-ttu-id="7d9fe-105">SSO 僅能在網域帳戶運作。</span><span class="sxs-lookup"><span data-stu-id="7d9fe-105">SSO only functions under a domain account.</span></span>  
  
## <a name="create-an-affiliate-application"></a><span data-ttu-id="7d9fe-106">建立分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="7d9fe-106">Create an affiliate application</span></span>  
  
1.  <span data-ttu-id="7d9fe-107">在控制台中開啟**服務**，並確認企業單一登入服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="7d9fe-107">In Control Panel, open **Services**, and verify that the Enterprise Single Sign-On service is running.</span></span>  
  
2.  <span data-ttu-id="7d9fe-108">在命令提示中，將目錄變更為 [Enterprise Single Sign-On] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="7d9fe-108">In a command prompt, change directories to the Enterprise Single Sign-On folder.</span></span>  
  
     <span data-ttu-id="7d9fe-109">例如：</span><span class="sxs-lookup"><span data-stu-id="7d9fe-109">For example:</span></span>  
  
     <span data-ttu-id="7d9fe-110">**C:\Program Files\Common Files\Enterprise Single Sign-on >**</span><span class="sxs-lookup"><span data-stu-id="7d9fe-110">**C:\Program Files\Common Files\Enterprise Single Sign-On>**</span></span>  
  
3.  <span data-ttu-id="7d9fe-111">使用 [企業單一登入] 命令。</span><span class="sxs-lookup"><span data-stu-id="7d9fe-111">Use the Enterprise Single Sign-On commands.</span></span> <span data-ttu-id="7d9fe-112">如需命令清單，請使用**-協助**切換。</span><span class="sxs-lookup"><span data-stu-id="7d9fe-112">For a list of commands, use the **-help** switch.</span></span>  
  
     ![](../core/media/siebeladapter-23-sso-commands.gif "SiebelAdapter_23_SSO_Commands")  
  
4.  <span data-ttu-id="7d9fe-113">若要使用 *.XML 為啟動程序來建立分支機構應用程式，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="7d9fe-113">To create the affiliate application by using *.XML as a start, type the following command:</span></span>  
  
     `ssomanage.exe -createapps C:\SSOtest\AffiliateApplication.xml`  
  
     <span data-ttu-id="7d9fe-114">其中：</span><span class="sxs-lookup"><span data-stu-id="7d9fe-114">where:</span></span>  
  
    -   <span data-ttu-id="7d9fe-115">C:\SSOtest 是應用程式 XML 所在的資料夾。</span><span class="sxs-lookup"><span data-stu-id="7d9fe-115">C:\SSOtest is the folder that contains your application XML.</span></span>  
  
    -   <span data-ttu-id="7d9fe-116">AffiliateApplication.xml 就是您建立的應用程式 XML，其中包含登入資訊。</span><span class="sxs-lookup"><span data-stu-id="7d9fe-116">AffiliateApplication.xml is the application XML you created that contains the sign-on information.</span></span>  
  
     <span data-ttu-id="7d9fe-117">例如：</span><span class="sxs-lookup"><span data-stu-id="7d9fe-117">For example:</span></span>  
  
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
  
## <a name="create-single-sign-on-tickets"></a><span data-ttu-id="7d9fe-118">建立單一登入票證</span><span class="sxs-lookup"><span data-stu-id="7d9fe-118">Create Single Sign-On Tickets</span></span>  
  
1.  <span data-ttu-id="7d9fe-119">輸入下列命令以控制 SSO 票證行為：</span><span class="sxs-lookup"><span data-stu-id="7d9fe-119">Type the following command to control SSO ticket behavior:</span></span>  
  
     `ssomanage.exe -tickets yes yes`  
  
2.  <span data-ttu-id="7d9fe-120">回答問題：</span><span class="sxs-lookup"><span data-stu-id="7d9fe-120">Answer the questions:</span></span>  
  
     `ssomanage -tickets <allowed yes | no> <validate yes | no>`  
  
     <span data-ttu-id="7d9fe-121">一完成就會收到確認：</span><span class="sxs-lookup"><span data-stu-id="7d9fe-121">On completion, you receive a confirmation:</span></span>  
  
     <span data-ttu-id="7d9fe-122">**在此電腦使用 SSO 伺服器。已成功完成此作業。**</span><span class="sxs-lookup"><span data-stu-id="7d9fe-122">**Using SSO server on this computer. The operation completed successfully.**</span></span>  
  
## <a name="enable-the-affiliate-application-xml"></a><span data-ttu-id="7d9fe-123">啟用分支機構應用程式 XML</span><span class="sxs-lookup"><span data-stu-id="7d9fe-123">Enable the Affiliate Application XML</span></span>  
  
1.  <span data-ttu-id="7d9fe-124">輸入以下命令：</span><span class="sxs-lookup"><span data-stu-id="7d9fe-124">Type the following command:</span></span>  
  
     `ssomanage -enableapp PeopleSoftApp`  
  
2.  <span data-ttu-id="7d9fe-125">輸入下列命令，列出應用程式並驗證已建立的應用程式：</span><span class="sxs-lookup"><span data-stu-id="7d9fe-125">Type the following command to list the applications and to verify that the application was created:</span></span>  
  
     `ssoclient.exe –listapps`  
  
     <span data-ttu-id="7d9fe-126">列出可供使用的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="7d9fe-126">The affiliate applications that are available for use appear in a list.</span></span>  
  
     <span data-ttu-id="7d9fe-127">**IBI\YourID-PeopleSoftApp 的應用程式**</span><span class="sxs-lookup"><span data-stu-id="7d9fe-127">**Applications available for IBI\YourID - PeopleSoftApp**</span></span>  
  
3.  <span data-ttu-id="7d9fe-128">輸入下列命令，設定分支機構應用程式認證：</span><span class="sxs-lookup"><span data-stu-id="7d9fe-128">Type the following command to set the affiliate application credentials:</span></span>  
  
     `ssoclient.exe -setcredentials PeopleSoftApp`  
  
4.  <span data-ttu-id="7d9fe-129">在提示下輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="7d9fe-129">Enter the user name and password at the prompts.</span></span> <span data-ttu-id="7d9fe-130">輸入 PeopleSoftApp 分支機構應用程式的登入認證。</span><span class="sxs-lookup"><span data-stu-id="7d9fe-130">Enter the logon credentials for the PeopleSoftApp affiliate application.</span></span>  
  
     <span data-ttu-id="7d9fe-131">例如，針對透過 SSO 伺服器進入系統的使用者，輸入使用者識別和密碼。</span><span class="sxs-lookup"><span data-stu-id="7d9fe-131">For example, enter the user identification and the password for that user to enter into the system through the SSO server.</span></span>  
  
    -   <span data-ttu-id="7d9fe-132">**使用者識別碼：**`user`</span><span class="sxs-lookup"><span data-stu-id="7d9fe-132">**User ID:** `user`</span></span>  
  
    -   <span data-ttu-id="7d9fe-133">**密碼：**`******`</span><span class="sxs-lookup"><span data-stu-id="7d9fe-133">**Password:** `******`</span></span>  
  
    -   <span data-ttu-id="7d9fe-134">**確認密碼：**`******`</span><span class="sxs-lookup"><span data-stu-id="7d9fe-134">**Confirm? Password:** `******`</span></span>  
  
5.  <span data-ttu-id="7d9fe-135">分支機構應用程式會出現在 PeopleSoft Enterprise 之 BizTalk 配接器的 [傳輸屬性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7d9fe-135">The affiliate application appears in the BizTalk Adapter for PeopleSoft Enterprise Transport Properties dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d9fe-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d9fe-136">See Also</span></span>  
 [<span data-ttu-id="7d9fe-137">保護配接器</span><span class="sxs-lookup"><span data-stu-id="7d9fe-137">Secure the adapter</span></span>](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)