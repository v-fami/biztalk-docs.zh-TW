---
title: "建立分支機構 Applications3 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- affiliate applications
- Single Sign-On, creating tickets
- tickets, creating Single Sign-On
- affiliate applications, creating
- SSO tickets
ms.assetid: 800644fd-2286-4e59-894b-260f584dd29f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 857ee7edd623332e72176ac09082f0ec9fc460f4
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="creating-affiliate-applications"></a><span data-ttu-id="51191-102">建立分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="51191-102">Creating Affiliate Applications</span></span>
<span data-ttu-id="51191-103">下列步驟說明如何開始使用採用單一登入 (SSO) 的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="51191-103">The following steps describe how to get started with affiliate applications using Single Sign-On (SSO).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51191-104">收到 SSO 錯誤時，請確認您設定 BizTalk Server 時有使用網域帳戶，因為 ESSO 服務的功能會受影響。</span><span class="sxs-lookup"><span data-stu-id="51191-104">If you get SSO errors, verify that you used a domain account when you configured BizTalk Server, because this affects the function of the ESSO service.</span></span> <span data-ttu-id="51191-105">SSO 僅能在網域帳戶運作。</span><span class="sxs-lookup"><span data-stu-id="51191-105">SSO only functions under a domain account.</span></span>  
  
## <a name="creating-an-affiliate-application"></a><span data-ttu-id="51191-106">建立分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="51191-106">Creating an Affiliate Application</span></span>  
  
#### <a name="to-create-an-affiliate-application"></a><span data-ttu-id="51191-107">若要建立分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="51191-107">To create an affiliate application</span></span>  
  
1.  <span data-ttu-id="51191-108">在**控制台**，開啟**服務**，並確認企業單一登入服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="51191-108">In **Control Panel**, open **Services**, and verify that the Enterprise Single Sign-On service is running.</span></span>  
  
2.  <span data-ttu-id="51191-109">在命令提示中，將目錄變更為 [Enterprise Single Sign-On] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="51191-109">In a command prompt, change directories to the Enterprise Single Sign-On folder.</span></span>  
  
     <span data-ttu-id="51191-110">例如：</span><span class="sxs-lookup"><span data-stu-id="51191-110">For example:</span></span>  
  
     <span data-ttu-id="51191-111">**C:\Program Files\Common Files\Enterprise Single Sign-on >**</span><span class="sxs-lookup"><span data-stu-id="51191-111">**C:\Program Files\Common Files\Enterprise Single Sign-On>**</span></span>  
  
3.  <span data-ttu-id="51191-112">使用 [企業單一登入] 命令。</span><span class="sxs-lookup"><span data-stu-id="51191-112">Use the Enterprise Single Sign-On commands.</span></span> <span data-ttu-id="51191-113">如需命令清單，請使用 -help 切換參數。</span><span class="sxs-lookup"><span data-stu-id="51191-113">For a list of commands, use the -help switch.</span></span>  
  
     ![](../core/media/siebeladapter-23-sso-commands.gif "SiebelAdapter_23_SSO_Commands")  
  
4.  <span data-ttu-id="51191-114">若要以 *.XML 開始建立分支機構應用程式，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="51191-114">To create the affiliate application using the *.XML as a beginning, type in the following command:</span></span>  
  
     <span data-ttu-id="51191-115">**ssomanage.exe createapps C:\SSOtest\AffiliateApplication.xml**</span><span class="sxs-lookup"><span data-stu-id="51191-115">**ssomanage.exe -createapps C:\SSOtest\AffiliateApplication.xml**</span></span>  
  
     <span data-ttu-id="51191-116">其中：</span><span class="sxs-lookup"><span data-stu-id="51191-116">where:</span></span>  
  
     <span data-ttu-id="51191-117">C:\SSOtest 是應用程式 XML 所在的資料夾。</span><span class="sxs-lookup"><span data-stu-id="51191-117">C:\SSOtest is the folder containing your application XML.</span></span>  
  
     <span data-ttu-id="51191-118">AffiliateApplication.xml 就是您建立的應用程式 XML，其中包含登入資訊。</span><span class="sxs-lookup"><span data-stu-id="51191-118">AffiliateApplication.xml is the application XML you created containing the Sign On information.</span></span>  
  
     <span data-ttu-id="51191-119">例如：</span><span class="sxs-lookup"><span data-stu-id="51191-119">For example:</span></span>  
  
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
  
## <a name="creating-single-sign-on-tickets"></a><span data-ttu-id="51191-120">建立單一登入票證</span><span class="sxs-lookup"><span data-stu-id="51191-120">Creating Single Sign-On Tickets</span></span>  
  
#### <a name="to-create-sso-tickets"></a><span data-ttu-id="51191-121">若要建立 SSO 票證</span><span class="sxs-lookup"><span data-stu-id="51191-121">To create SSO tickets</span></span>  
  
1.  <span data-ttu-id="51191-122">輸入下列命令以控制 SSO 票證行為：</span><span class="sxs-lookup"><span data-stu-id="51191-122">Type in the following command to control SSO ticket behavior:</span></span>  
  
     `ssomanage.exe -tickets yes yes`  
  
2.  <span data-ttu-id="51191-123">回答問題：</span><span class="sxs-lookup"><span data-stu-id="51191-123">Answer the questions:</span></span>  
  
     `ssomanage -tickets <allowed yes | no> <validate yes | no>`  
  
     <span data-ttu-id="51191-124">一完成就會收到確認：</span><span class="sxs-lookup"><span data-stu-id="51191-124">On completion you receive a confirmation:</span></span>  
  
     <span data-ttu-id="51191-125">**在此電腦使用 SSO 伺服器。已成功完成此作業。**</span><span class="sxs-lookup"><span data-stu-id="51191-125">**Using SSO server on this computer. The operation completed successfully.**</span></span>  
  
## <a name="enabling-the-affiliate-application-xml"></a><span data-ttu-id="51191-126">啟用分支機構應用程式 XML</span><span class="sxs-lookup"><span data-stu-id="51191-126">Enabling the Affiliate Application XML</span></span>  
  
#### <a name="to-enable-affiliate-application-xml"></a><span data-ttu-id="51191-127">若要啟用分支機構應用程式 XML</span><span class="sxs-lookup"><span data-stu-id="51191-127">To enable affiliate application XML</span></span>  
  
1.  <span data-ttu-id="51191-128">輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="51191-128">Type in the following command:</span></span>  
  
     `ssomanage -enableapp JDEdwardsApp`  
  
2.  <span data-ttu-id="51191-129">輸入下列命令，列出應用程式並驗證已建立的應用程式：</span><span class="sxs-lookup"><span data-stu-id="51191-129">Type in the following command to list the applications and to verify that the application was created:</span></span>  
  
     `ssoclient.exe –listapps`  
  
     <span data-ttu-id="51191-130">可供使用的分支機構應用程式隨即列在清單中。</span><span class="sxs-lookup"><span data-stu-id="51191-130">The Affiliate Applications available for use appear in a list.</span></span>  
  
     <span data-ttu-id="51191-131">**IBI\YourID-JDEdwardsApp 的應用程式**</span><span class="sxs-lookup"><span data-stu-id="51191-131">**Applications available for IBI\YourID - JDEdwardsApp**</span></span>  
  
3.  <span data-ttu-id="51191-132">輸入下列命令，設定分支機構應用程式認證：</span><span class="sxs-lookup"><span data-stu-id="51191-132">Type in the following command to set the affiliate application credentials:</span></span>  
  
     `ssoclient.exe -setcredentials JDEdwardsApp`  
  
4.  <span data-ttu-id="51191-133">在提示下輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="51191-133">Enter the user name and password at the prompts.</span></span> <span data-ttu-id="51191-134">輸入 JDEdwardsApp 分支機構應用程式的登入認證。</span><span class="sxs-lookup"><span data-stu-id="51191-134">Enter the logon credentials for the JDEdwardsApp affiliate application.</span></span> <span data-ttu-id="51191-135">例如，針對透過 SSO 伺服器進入系統的使用者，輸入使用者識別和密碼。</span><span class="sxs-lookup"><span data-stu-id="51191-135">For example, enter the user identification and the password for that user to enter into the system through the SSO server.</span></span>  
  
    -   <span data-ttu-id="51191-136">**使用者識別碼：**使用者</span><span class="sxs-lookup"><span data-stu-id="51191-136">**User ID:** user</span></span>  
  
    -   <span data-ttu-id="51191-137">**密碼：** ******</span><span class="sxs-lookup"><span data-stu-id="51191-137">**Password:** ******</span></span>  
  
    -   <span data-ttu-id="51191-138">**確認密碼：** ******</span><span class="sxs-lookup"><span data-stu-id="51191-138">**Confirm? Password:** ******</span></span>  
  
5.  <span data-ttu-id="51191-139">分支機構應用程式會出現在 BizTalk Adapter for JD Edwards OneWorld 的 [傳輸屬性] 對話方塊的下拉式清單中。</span><span class="sxs-lookup"><span data-stu-id="51191-139">The affiliate application appears in the drop-down list of the BizTalk Adapter for JD Edwards OneWorld Transport Properties dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51191-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51191-140">See Also</span></span>  
 [<span data-ttu-id="51191-141">在配接器的安全性</span><span class="sxs-lookup"><span data-stu-id="51191-141">Security in the adapter</span></span>](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)