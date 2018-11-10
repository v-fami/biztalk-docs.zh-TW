---
title: 建立分支機構 Applications4 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tickets, Single Sign-On
- affiliate applications, setting credentials
- affiliate applications
- Single Sign-On, creating tickets
- SSO tickets
ms.assetid: 790fbe21-8081-4d57-803f-23014c8a3135
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a62a8c2c6d2bb74c9e68fcdcf1304e6d0cd99d67
ms.sourcegitcommit: 53b16fe6c1b1707ecf233dbd05f780653eb19419
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2018
ms.locfileid: "50752622"
---
# <a name="creating-affiliate-applications"></a><span data-ttu-id="2155f-102">建立分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="2155f-102">Creating Affiliate Applications</span></span>
<span data-ttu-id="2155f-103">下列步驟說明如何開始使用採用 SSO 的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="2155f-103">The following steps describe how to get started with affiliate applications using SSO.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2155f-104">收到 SSO 錯誤時，請確認您設定 BizTalk Server 時有使用網域帳戶，因為企業單一登入服務的功能會受影響。</span><span class="sxs-lookup"><span data-stu-id="2155f-104">If you get SSO errors, verify that you used a domain account when you configured BizTalk Server, as this affects the function of the Enterprise SSO service.</span></span> <span data-ttu-id="2155f-105">SSO 僅能在網域帳戶運作。</span><span class="sxs-lookup"><span data-stu-id="2155f-105">SSO only functions under a domain account.</span></span>  
  
### <a name="to-create-an-affiliate-application"></a><span data-ttu-id="2155f-106">若要建立分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="2155f-106">To create an affiliate application</span></span>  
  
1. <span data-ttu-id="2155f-107">在控制台中，開啟**Services**，並確認企業單一登入服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="2155f-107">In Control Panel, open **Services**, and verify that the Enterprise Single Sign-On service is running.</span></span>  
  
2. <span data-ttu-id="2155f-108">在命令提示中，將目錄變更為 [Enterprise Single Sign On] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2155f-108">In a command prompt, change directories to the Enterprise Single Sign On folder.</span></span>  
  
    <span data-ttu-id="2155f-109">例如：</span><span class="sxs-lookup"><span data-stu-id="2155f-109">For example:</span></span>  
  
    <span data-ttu-id="2155f-110">**C:\Program Files\Common Files\Enterprise Single Sign-on >**</span><span class="sxs-lookup"><span data-stu-id="2155f-110">**C:\Program Files\Common Files\Enterprise Single Sign-On>**</span></span>  
  
3. <span data-ttu-id="2155f-111">使用 [企業單一登入] 命令。</span><span class="sxs-lookup"><span data-stu-id="2155f-111">Use the Enterprise Single Sign-On commands.</span></span> <span data-ttu-id="2155f-112">如需命令的清單，請使用 **-協助**切換。</span><span class="sxs-lookup"><span data-stu-id="2155f-112">For a list of commands, use the **-help** switch.</span></span>  
  
4. <span data-ttu-id="2155f-113">若要建立分支機構應用程式使用\*。將 XML 當做開頭，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="2155f-113">To create the affiliate application using \*.XML as a beginning, type the following command:</span></span>  
  
    `ssomanage.exe -createapps C:\SSOtest\AffiliateApplication.xml`  
  
    <span data-ttu-id="2155f-114">其中：</span><span class="sxs-lookup"><span data-stu-id="2155f-114">where:</span></span>  
  
   - <span data-ttu-id="2155f-115">C:\SSOtest 是應用程式 XML 所在的資料夾。</span><span class="sxs-lookup"><span data-stu-id="2155f-115">C:\SSOtest is the folder that contains your application XML.</span></span>  
  
   - <span data-ttu-id="2155f-116">AffiliateApplication.xml 就是您建立的應用程式 XML，其中包含登入資訊。</span><span class="sxs-lookup"><span data-stu-id="2155f-116">AffiliateApplication.xml is the application XML you created that contains the Sign-On information.</span></span>  
  
     <span data-ttu-id="2155f-117">例如：</span><span class="sxs-lookup"><span data-stu-id="2155f-117">For example:</span></span>  
  
   ```  
   <?xml version="1.0"?>  
   <SSO>  
       <application name="JDEdwardsApp">  
           <description>JDEdwards SSO Application</description>  
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
  
### <a name="to-create-single-sign-on-tickets"></a><span data-ttu-id="2155f-118">若要建立單一登入票證</span><span class="sxs-lookup"><span data-stu-id="2155f-118">To create Single Sign-On tickets</span></span>  
  
1.  <span data-ttu-id="2155f-119">輸入下列命令以控制 SSO 票證行為：</span><span class="sxs-lookup"><span data-stu-id="2155f-119">Type the following command to control SSO ticket behavior:</span></span>  
  
     `ssomanage.exe -tickets yes yes`  
  
2.  <span data-ttu-id="2155f-120">回答如下所示的問題：</span><span class="sxs-lookup"><span data-stu-id="2155f-120">Answer the following questions as shown:</span></span>  
  
     `ssomanage -tickets <allowed yes | no> <validate yes | no>`  
  
     <span data-ttu-id="2155f-121">一完成就會收到下列確認：</span><span class="sxs-lookup"><span data-stu-id="2155f-121">On completion, you receive the following confirmation:</span></span>  
  
     <span data-ttu-id="2155f-122">**在此電腦使用 SSO 伺服器。已成功完成此作業。**</span><span class="sxs-lookup"><span data-stu-id="2155f-122">**Using SSO server on this computer. The operation completed successfully.**</span></span>  
  
### <a name="to-enable-affiliate-application-xml"></a><span data-ttu-id="2155f-123">若要啟用分支機構應用程式 XML</span><span class="sxs-lookup"><span data-stu-id="2155f-123">To enable affiliate application XML</span></span>  
  
1. <span data-ttu-id="2155f-124">輸入以下命令：</span><span class="sxs-lookup"><span data-stu-id="2155f-124">Type the following command:</span></span>  
  
    `ssomanage -enableapp JDEdwardsApp`  
  
2. <span data-ttu-id="2155f-125">輸入下列命令，列出應用程式並驗證已建立的應用程式：</span><span class="sxs-lookup"><span data-stu-id="2155f-125">Type the following command to list the applications and to verify that the application was created:</span></span>  
  
    `ssoclient.exe –listapps`  
  
    <span data-ttu-id="2155f-126">可供使用的分支機構應用程式隨即列在清單中：</span><span class="sxs-lookup"><span data-stu-id="2155f-126">The affiliate applications that are available for use display in a list:</span></span>  
  
    <span data-ttu-id="2155f-127">**IBI\YourID-JDEdwardsApp 的應用程式**</span><span class="sxs-lookup"><span data-stu-id="2155f-127">**Applications available for IBI\YourID - JDEdwardsApp**</span></span>  
  
3. <span data-ttu-id="2155f-128">輸入下列命令，設定分支機構應用程式認證：</span><span class="sxs-lookup"><span data-stu-id="2155f-128">Type the following command to set the affiliate application credentials:</span></span>  
  
    `ssoclient.exe -setcredentials JDEdwardsApp`  
  
4. <span data-ttu-id="2155f-129">在提示下輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="2155f-129">Enter the user name and password at the prompts.</span></span> <span data-ttu-id="2155f-130">輸入 JDEdwardsApp 分支機構應用程式的登入認證。</span><span class="sxs-lookup"><span data-stu-id="2155f-130">Enter the logon credentials for the JDEdwardsApp affiliate application.</span></span>  
  
    <span data-ttu-id="2155f-131">例如，針對透過 SSO 伺服器進入系統的使用者，輸入使用者識別和密碼。</span><span class="sxs-lookup"><span data-stu-id="2155f-131">For example, enter the user identification and the password for that user to enter into the system through the SSO server.</span></span>  
  
   - <span data-ttu-id="2155f-132">使用者識別碼：**使用者**</span><span class="sxs-lookup"><span data-stu-id="2155f-132">User ID: **user**</span></span>  
  
   - <span data-ttu-id="2155f-133">密碼： `******`</span><span class="sxs-lookup"><span data-stu-id="2155f-133">Password: `******`</span></span>  
  
   - <span data-ttu-id="2155f-134">確認？</span><span class="sxs-lookup"><span data-stu-id="2155f-134">Confirm?</span></span> <span data-ttu-id="2155f-135">密碼： `******`</span><span class="sxs-lookup"><span data-stu-id="2155f-135">Password: `******`</span></span>  
  
     <span data-ttu-id="2155f-136">分支機構應用程式會出現在 BizTalk Adapter for JD Edwards EnterpriseOne**傳輸屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2155f-136">The affiliate application appears in the BizTalk Adapter for JD Edwards EnterpriseOne **Transport Properties** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2155f-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2155f-137">See Also</span></span>  
 [<span data-ttu-id="2155f-138">BizTalk Adapter for JD Edwards EnterpriseOne 中的安全性</span><span class="sxs-lookup"><span data-stu-id="2155f-138">Security in BizTalk Adapter for JD Edwards EnterpriseOne</span></span>](../core/security-in-biztalk-adapter-for-jd-edwards-enterpriseone.md)