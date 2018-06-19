---
title: 重複使用 SAP 配接器繫結 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- binding file, definition
- adapter bindings, reusing
ms.assetid: 5748c22f-20a2-4eb9-ad45-a1bef7290802
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df4c878f8eb6a5e1fd52dfe749b10d1d89716679
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22217694"
---
# <a name="reuse-sap-adapter-bindings"></a><span data-ttu-id="2ee47-102">重複使用 SAP 配接器繫結</span><span class="sxs-lookup"><span data-stu-id="2ee47-102">Reuse SAP adapter bindings</span></span>
<span data-ttu-id="2ee47-103">繫結之間建立對應的邏輯端點 （例如協調流程連接埠或角色連結） 與實體端點 (例如傳送和接收埠)。</span><span class="sxs-lookup"><span data-stu-id="2ee47-103">A binding creates a mapping between a logical endpoint (such as an orchestration port or a role link) and a physical endpoint (such as a send and receive port).</span></span> <span data-ttu-id="2ee47-104">這讓通訊能在不同的 BizTalk 商務方案元件之間進行。</span><span class="sxs-lookup"><span data-stu-id="2ee47-104">This enables communication between different components of a BizTalk business solution.</span></span> <span data-ttu-id="2ee47-105">您可以使用 [BizTalk Server 管理主控台] 建立繫結。</span><span class="sxs-lookup"><span data-stu-id="2ee47-105">You can create bindings by using the BizTalk Server Administration console.</span></span>  
  
## <a name="what-is-a-binding-file"></a><span data-ttu-id="2ee47-106">什麼是繫結檔案？</span><span class="sxs-lookup"><span data-stu-id="2ee47-106">What is a Binding File?</span></span>  
 <span data-ttu-id="2ee47-107">繫結檔案是 XML 檔案，其中包含每個 BizTalk 協調流程範圍中的 BizTalk 組件、 應用程式或群組的繫結資訊。</span><span class="sxs-lookup"><span data-stu-id="2ee47-107">A binding file is an XML file that contains binding information for each BizTalk orchestration in the scope of a BizTalk assembly, application, or group.</span></span> <span data-ttu-id="2ee47-108">描述繫結檔案：</span><span class="sxs-lookup"><span data-stu-id="2ee47-108">The binding file describes:</span></span>  
  
-   <span data-ttu-id="2ee47-109">每個協調流程繫結至主機</span><span class="sxs-lookup"><span data-stu-id="2ee47-109">The host to which each orchestration is bound</span></span>
  
-   <span data-ttu-id="2ee47-110">主控件的信任層級</span><span class="sxs-lookup"><span data-stu-id="2ee47-110">The trust level of the host</span></span>
  
-   <span data-ttu-id="2ee47-111">每個設定傳送埠、 接收埠、 接收位置，以及已設定合作對象</span><span class="sxs-lookup"><span data-stu-id="2ee47-111">The settings for each send port, receive port, receive location, and party that has been configured</span></span>
  
 <span data-ttu-id="2ee47-112">您可以產生繫結檔案，然後將它們包含的繫結套用至組件、 應用程式或群組。</span><span class="sxs-lookup"><span data-stu-id="2ee47-112">You can generate binding files and then apply the bindings they contain to an assembly, application, or group.</span></span> <span data-ttu-id="2ee47-113">這可避免必須手動設定在不同的部署環境中的 繫結，並可加速應用程式部署。</span><span class="sxs-lookup"><span data-stu-id="2ee47-113">This prevents having to manually configure bindings in different deployment environments and speeds up application deployment.</span></span>  
  
<span data-ttu-id="2ee47-114">繫結檔案不會自動產生 BizTalk 組件、 應用程式或群組。</span><span class="sxs-lookup"><span data-stu-id="2ee47-114">A binding file is not automatically generated for a BizTalk assembly, application, or group.</span></span> <span data-ttu-id="2ee47-115">不過，您可以產生繫結檔案匯出繫結。</span><span class="sxs-lookup"><span data-stu-id="2ee47-115">However, you can generate a binding file by exporting bindings.</span></span> <span data-ttu-id="2ee47-116">您可以再將繫結檔案匯入的應用程式或群組。</span><span class="sxs-lookup"><span data-stu-id="2ee47-116">You can then import the binding file into an application or group.</span></span>  
  
<span data-ttu-id="2ee47-117">如需有關繫結和繫結檔案的詳細資訊，請參閱[繫結檔案和應用程式部署](../../core/binding-files-and-application-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="2ee47-117">For more information about bindings and about binding files, see [Binding Files and Application Deployment](../../core/binding-files-and-application-deployment.md).</span></span>
  
## <a name="prerequisites"></a><span data-ttu-id="2ee47-118">必要條件</span><span class="sxs-lookup"><span data-stu-id="2ee47-118">Prerequisites</span></span>  
<span data-ttu-id="2ee47-119">使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理員 」 或 「 BizTalk 操作員群組。</span><span class="sxs-lookup"><span data-stu-id="2ee47-119">Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators or BizTalk Operators group.</span></span> <span data-ttu-id="2ee47-120">如需詳細的權限的相關資訊，請參閱[部署及管理 BizTalk 應用程式所需的權限](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="2ee47-120">For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>
 
## <a name="export-bindings"></a><span data-ttu-id="2ee47-121">匯出繫結</span><span class="sxs-lookup"><span data-stu-id="2ee47-121">Export bindings</span></span>
<span data-ttu-id="2ee47-122">本章節描述如何匯出成 XML 檔案的 BizTalk 應用程式的繫結。</span><span class="sxs-lookup"><span data-stu-id="2ee47-122">This section describes how to export bindings for a BizTalk application into an XML file.</span></span> <span data-ttu-id="2ee47-123">您接著可以從 XML 檔案的繫結匯入到另一個 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="2ee47-123">You can then import the bindings from the XML file into another BizTalk application.</span></span> <span data-ttu-id="2ee47-124">匯入繫結會覆寫任何現有的繫結的應用程式中相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="2ee47-124">Importing bindings overwrites any existing bindings of the same name in the application.</span></span> <span data-ttu-id="2ee47-125">您也可以將繫結加入應用程式中，這樣並不會覆寫現有的繫結。</span><span class="sxs-lookup"><span data-stu-id="2ee47-125">You can also add bindings to an application, which does not overwrite existing bindings.</span></span> <span data-ttu-id="2ee47-126">加入的繫結會在您匯入該應用程式之後才生效。</span><span class="sxs-lookup"><span data-stu-id="2ee47-126">The bindings that you add do not take effect until you import the application.</span></span>  
  
1.  <span data-ttu-id="2ee47-127">開啟[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="2ee47-127">Open the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="2ee47-128">展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="2ee47-128">Expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="2ee47-129">以滑鼠右鍵按一下您想要匯出其繫的結選取的應用程式**匯出**，然後選取**繫結**。</span><span class="sxs-lookup"><span data-stu-id="2ee47-129">Right-click the application whose bindings you want to export, select **Export**, and then select **Bindings**.</span></span>  
  
4.  <span data-ttu-id="2ee47-130">在**匯出繫結**頁面上，於**匯出至檔案**，輸入要匯出繫結至 XML 檔案的絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="2ee47-130">On the **Export Bindings** page, in **Export to file**, type the absolute path of the XML file to which to export the bindings.</span></span>  
  
     <span data-ttu-id="2ee47-131">例如，輸入`C:\Bindings\Application1Bindings.Binding1.xml`</span><span class="sxs-lookup"><span data-stu-id="2ee47-131">For example, enter `C:\Bindings\Application1Bindings.Binding1.xml`</span></span>  
  
5.  <span data-ttu-id="2ee47-132">確認**從目前的應用程式匯出所有繫結**已選取。</span><span class="sxs-lookup"><span data-stu-id="2ee47-132">Confirm that **Export all bindings from the current application** is selected.</span></span>  
  
6.  <span data-ttu-id="2ee47-133">若要匯出群組的所有合作對象資訊，請選取**匯出全域合作對象資訊**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2ee47-133">To export all party information for the group, select the **Export Global Party information** check box.</span></span>  
  
7.  <span data-ttu-id="2ee47-134">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="2ee47-134">Select **OK**.</span></span> <span data-ttu-id="2ee47-135">繫結會匯出到 XML 檔案中您所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="2ee47-135">The bindings are exported into an XML file in the location that you specified.</span></span>  

## <a name="import-bindings"></a><span data-ttu-id="2ee47-136">匯入繫結</span><span class="sxs-lookup"><span data-stu-id="2ee47-136">Import bindings</span></span>
<span data-ttu-id="2ee47-137">匯入繫結使用 BizTalk Server 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="2ee47-137">Import bindings using the BizTalk Server Administration console.</span></span>
  
1.  <span data-ttu-id="2ee47-138">開啟[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="2ee47-138">Open the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2.  <span data-ttu-id="2ee47-139">展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="2ee47-139">Expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="2ee47-140">以滑鼠右鍵按一下想要匯入繫結，請選取的應用程式**匯入**，然後選取**繫結**。</span><span class="sxs-lookup"><span data-stu-id="2ee47-140">Right-click the application into which you want to import bindings, select **Import**, and then select **Bindings**.</span></span>  
  
4.  <span data-ttu-id="2ee47-141">選取繫結檔案，然後選取**開啟**。</span><span class="sxs-lookup"><span data-stu-id="2ee47-141">Select the binding file, and then select **Open**.</span></span>  
  
<span data-ttu-id="2ee47-142">繫結檔案中的成品會寫入此應用程式，</span><span class="sxs-lookup"><span data-stu-id="2ee47-142">The artifacts in the binding file are written to the application.</span></span> <span data-ttu-id="2ee47-143">這些成品會顯示在應用程式的適當資料夾中。</span><span class="sxs-lookup"><span data-stu-id="2ee47-143">They display in appropriate folders of the application.</span></span> <span data-ttu-id="2ee47-144">例如，傳送埠會一併匯入繫結顯示底下的**傳送埠**資料夾。</span><span class="sxs-lookup"><span data-stu-id="2ee47-144">For example, the send ports imported as part of the bindings display under the **Send Ports** folder.</span></span>  

## <a name="passwords-are-removed"></a><span data-ttu-id="2ee47-145">密碼會移除</span><span class="sxs-lookup"><span data-stu-id="2ee47-145">Passwords are removed</span></span>  
<span data-ttu-id="2ee47-146">基於安全性理由，當您匯出繫結檔案，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]從檔案移除繫結密碼。</span><span class="sxs-lookup"><span data-stu-id="2ee47-146">For security reasons, when you export a binding file, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] removes the passwords for the bindings from the file.</span></span> <span data-ttu-id="2ee47-147">匯入繫結後，您必須重新設定密碼，傳送埠和接受位置才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="2ee47-147">After importing the bindings, you must reconfigure passwords for send ports and receive locations before they will function.</span></span> <span data-ttu-id="2ee47-148">您的 [傳輸屬性] 對話方塊中設定密碼[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理主控台的 傳送埠或接收位置。</span><span class="sxs-lookup"><span data-stu-id="2ee47-148">You configure passwords in the Transport Properties dialog box of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console for the send port or receive location.</span></span> 

<span data-ttu-id="2ee47-149">指定使用者名稱和密碼的相關資訊，請參閱[設定登入 SAP 系統的認證](../../adapters-and-accelerators/adapter-sap/configure-the-sign-in-credentials-for-the-sap-system.md)。</span><span class="sxs-lookup"><span data-stu-id="2ee47-149">For information about specifying user name and passwords, see [Configure the sign in credentials for the SAP system](../../adapters-and-accelerators/adapter-sap/configure-the-sign-in-credentials-for-the-sap-system.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2ee47-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ee47-150">See also</span></span>
[<span data-ttu-id="2ee47-151">若要建立的 SAP 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="2ee47-151">Building blocks to create SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)