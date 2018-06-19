---
title: 建立 TIBCO EMS 的分支機構應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 191e5b56-dab9-4bf3-9f89-a900907d64e0
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce5df15794886f9177f12f2a9e9a33e3ffdc335f
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24015285"
---
# <a name="create-affiliate-applications"></a><span data-ttu-id="13738-102">建立分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="13738-102">Create Affiliate Applications</span></span>
<span data-ttu-id="13738-103">下列步驟說明如何開始使用分支機構應用程式和單一登入 (SSO)。</span><span class="sxs-lookup"><span data-stu-id="13738-103">The following steps describe how to start using affiliate applications and Single Sign-On (SSO).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13738-104">收到 SSO 錯誤時，請確認您設定 BizTalk Server 時有使用網域帳戶，因為企業單一登入服務的功能會受影響。</span><span class="sxs-lookup"><span data-stu-id="13738-104">If you receive SSO errors, verify that you used a domain account when you configured BizTalk Server; this affects the function of the Enterprise SSO service.</span></span> <span data-ttu-id="13738-105">SSO 僅能在網域帳戶運作</span><span class="sxs-lookup"><span data-stu-id="13738-105">SSO only functions under a domain account</span></span>  
  
## <a name="create-an-affiliate-application"></a><span data-ttu-id="13738-106">建立分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="13738-106">Create an affiliate application</span></span>  
  
1.  <span data-ttu-id="13738-107">在控制台中開啟**服務**，並確認企業單一登入服務正在執行。</span><span class="sxs-lookup"><span data-stu-id="13738-107">In Control Panel, open **Services**, and verify that the Enterprise Single Sign-On service is running.</span></span>  
  
2.  <span data-ttu-id="13738-108">在命令提示中，將目錄變更為 [Enterprise Single Sign-On] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="13738-108">In a command prompt, change directories to the Enterprise Single Sign-On folder.</span></span>  
  
     <span data-ttu-id="13738-109">例如：</span><span class="sxs-lookup"><span data-stu-id="13738-109">For example:</span></span>  
  
     <span data-ttu-id="13738-110">**C:\Program Files\Common Files\Enterprise Single Sign-on >**</span><span class="sxs-lookup"><span data-stu-id="13738-110">**C:\Program Files\Common Files\Enterprise Single Sign-On>**</span></span>  
  
3.  <span data-ttu-id="13738-111">使用 [企業單一登入] 命令。</span><span class="sxs-lookup"><span data-stu-id="13738-111">Use the Enterprise Single Sign-On commands.</span></span> <span data-ttu-id="13738-112">如需命令清單，請使用 **-協助**切換。</span><span class="sxs-lookup"><span data-stu-id="13738-112">For a list of commands, use the **-help** switch.</span></span>  
  
4.  <span data-ttu-id="13738-113">若要使用 \*.XML 為啟動程序來建立分支機構應用程式，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="13738-113">To create the affiliate application by using \*.XML as a start, type the following command:</span></span>  
  
     `ssomanage.exe -createapps C:\SSOtest\AffiliateApplication.xml`  
  
     <span data-ttu-id="13738-114">其中：</span><span class="sxs-lookup"><span data-stu-id="13738-114">where:</span></span>  
  
    -   <span data-ttu-id="13738-115">C:\SSOtest 是應用程式 XML 所在的資料夾。</span><span class="sxs-lookup"><span data-stu-id="13738-115">C:\SSOtest is the folder that contains your application XML.</span></span>  
  
    -   <span data-ttu-id="13738-116">AffiliateApplication.xml 就是您建立的應用程式 XML，其中包含登入資訊。</span><span class="sxs-lookup"><span data-stu-id="13738-116">AffiliateApplication.xml is the application XML you created that contains the Sign-On information.</span></span>  
  
     <span data-ttu-id="13738-117">例如：</span><span class="sxs-lookup"><span data-stu-id="13738-117">For example:</span></span>  
  
    ```  
    <?xml version="1.0"?>  
    <SSO>  
        <application name="TIBCO EMS App">  
            <description>TIBCO EMS SSO Application</description>  
            <contact>someone@example.com</contact>  
            <appUserAccount>DomainName\AppUserGroup</appUserAccount>  
            <!—an existing group on the domain controller - >   
            <appAdminAccount>DomainName\AppAdminGroup</appAdminAccount>  
            <!-- an existing account in the domain group - >   
            <field ordinal="0" label="User ID" masked="no" />  
            <field ordinal="1" label="Password" masked="yes" />  
            <flags groupApp="no" allowTickets="yes" enableApp="yes"/>  
        </application>  
    </SSO>  
    ```  
  
 <span data-ttu-id="13738-118">藉由使用範例 XML，分支機構應用程式 TIBCO EMS App 會包含命令提示字元中所顯示的值。</span><span class="sxs-lookup"><span data-stu-id="13738-118">By using the example XML, the affiliate application, TIBCO EMS App, contains the values as shown in the command prompt.</span></span>  
  
## <a name="create-single-sign-on-tickets"></a><span data-ttu-id="13738-119">建立單一登入票證</span><span class="sxs-lookup"><span data-stu-id="13738-119">Create Single Sign-On tickets</span></span>  
  
1.  <span data-ttu-id="13738-120">輸入下列命令以控制 SSO 票證行為：</span><span class="sxs-lookup"><span data-stu-id="13738-120">Type the following command to control SSO ticket behavior:</span></span>  
  
     `ssomanage.exe -tickets yes yes`  
  
2.  <span data-ttu-id="13738-121">回答問題：</span><span class="sxs-lookup"><span data-stu-id="13738-121">Answer the questions:</span></span>  
  
     `ssomanage -tickets <allowed yes | no> <validate yes | no>`  
  
     <span data-ttu-id="13738-122">一完成就會收到確認：</span><span class="sxs-lookup"><span data-stu-id="13738-122">On completion, you receive a confirmation:</span></span>  
  
     <span data-ttu-id="13738-123">**在此電腦使用 SSO 伺服器。已成功完成此作業。**</span><span class="sxs-lookup"><span data-stu-id="13738-123">**Using SSO server on this computer. The operation completed successfully.**</span></span>  
  
## <a name="enable-affiliate-application-xml"></a><span data-ttu-id="13738-124">啟用分支機構應用程式 XML</span><span class="sxs-lookup"><span data-stu-id="13738-124">Enable affiliate application XML</span></span>  
  
1.  <span data-ttu-id="13738-125">輸入以下命令：</span><span class="sxs-lookup"><span data-stu-id="13738-125">Type the following command:</span></span>  
  
     `ssomanage -enableapp TIBCO EMSApp`  
  
2.  <span data-ttu-id="13738-126">輸入下列命令，列出應用程式並驗證已建立的應用程式：</span><span class="sxs-lookup"><span data-stu-id="13738-126">Type the following command to list the applications and to verify that the application was created:</span></span>  
  
     `ssoclient.exe –listapps`  
  
     <span data-ttu-id="13738-127">可供使用的分支機構應用程式隨即以清單形式列出：</span><span class="sxs-lookup"><span data-stu-id="13738-127">The affiliate applications that are available for use appear in a list:</span></span>  
  
     <span data-ttu-id="13738-128">**IBI\YourID-TIBCO EMSApp 的應用程式**</span><span class="sxs-lookup"><span data-stu-id="13738-128">**Applications available for IBI\YourID - TIBCO EMSApp**</span></span>  
  
3.  <span data-ttu-id="13738-129">輸入下列命令，設定分支機構應用程式認證：</span><span class="sxs-lookup"><span data-stu-id="13738-129">Type the following command to set the affiliate application credentials:</span></span>  
  
     `soclient.exe -setcredentials TIBCO EMSApp`  
  
4.  <span data-ttu-id="13738-130">在提示下輸入使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="13738-130">Enter the user name and password at the prompts.</span></span> <span data-ttu-id="13738-131">輸入 TIBCO EMS App 分支機構應用程式的登入認證。</span><span class="sxs-lookup"><span data-stu-id="13738-131">Enter the logon credentials for the TIBCO EMS App affiliate application.</span></span>  
  
     <span data-ttu-id="13738-132">例如，針對透過 SSO 伺服器進入系統的使用者，輸入使用者識別和密碼。</span><span class="sxs-lookup"><span data-stu-id="13738-132">For example, enter the user identification and the password for that user to enter into the system through the SSO server.</span></span>  
  
    -   <span data-ttu-id="13738-133">使用者識別碼：**使用者**</span><span class="sxs-lookup"><span data-stu-id="13738-133">User ID: **user**</span></span>  
  
    -   <span data-ttu-id="13738-134">密碼：`******`</span><span class="sxs-lookup"><span data-stu-id="13738-134">Password: `******`</span></span>  
  
    -   <span data-ttu-id="13738-135">確認？</span><span class="sxs-lookup"><span data-stu-id="13738-135">Confirm?</span></span> <span data-ttu-id="13738-136">密碼：`******`</span><span class="sxs-lookup"><span data-stu-id="13738-136">Password: `******`</span></span>  
  
     <span data-ttu-id="13738-137">分支機構應用程式會出現在 BizTalk Adapter for TIBCO EMS**傳輸屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="13738-137">The affiliate application appears in the BizTalk Adapter for TIBCO EMS **Transport Properties** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13738-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13738-138">See Also</span></span>  
[<span data-ttu-id="13738-139">保護配接器</span><span class="sxs-lookup"><span data-stu-id="13738-139">Secure the adapter</span></span>](../core/security-in-biztalk-adapter-for-tibco-ems.md)