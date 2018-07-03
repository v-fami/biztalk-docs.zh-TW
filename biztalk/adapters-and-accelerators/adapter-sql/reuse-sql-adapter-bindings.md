---
title: 重複使用 SQL 配接器繫結 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8bc8140f-1d40-492c-bce1-b85e992b3567
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6995f62b6dc94734b6e5dac01fad4284e6fcf7fd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009983"
---
# <a name="reuse-sql-adapter-bindings"></a><span data-ttu-id="5b195-102">重複使用 SQL 配接器繫結</span><span class="sxs-lookup"><span data-stu-id="5b195-102">Reuse SQL adapter bindings</span></span>
<span data-ttu-id="5b195-103">繫結會建立邏輯端點 （例如協調流程連接埠或角色連結） 與實體端點之間的對應 (例如傳送和接收埠)。</span><span class="sxs-lookup"><span data-stu-id="5b195-103">A binding creates a mapping between a logical endpoint (such as an orchestration port or a role link) and a physical endpoint (such as a send and receive port).</span></span> <span data-ttu-id="5b195-104">這讓通訊能在不同的 BizTalk 商務方案元件之間進行。</span><span class="sxs-lookup"><span data-stu-id="5b195-104">This enables communication between different components of a BizTalk business solution.</span></span> <span data-ttu-id="5b195-105">您可以使用，以建立繫結[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="5b195-105">You can create bindings by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
## <a name="what-is-a-binding-file"></a><span data-ttu-id="5b195-106">什麼是繫結檔案？</span><span class="sxs-lookup"><span data-stu-id="5b195-106">What is a Binding File?</span></span>  
 <span data-ttu-id="5b195-107">繫結檔案是 XML 檔案，其中包含 BizTalk 組件、 應用程式或群組的範圍中每個 BizTalk 協調流程的繫結資訊。</span><span class="sxs-lookup"><span data-stu-id="5b195-107">A binding file is an XML file that contains binding information for each BizTalk orchestration in the scope of a BizTalk assembly, application, or group.</span></span> <span data-ttu-id="5b195-108">描述繫結檔案：</span><span class="sxs-lookup"><span data-stu-id="5b195-108">The binding file describes:</span></span>  
  
- <span data-ttu-id="5b195-109">每個協調流程繫結至主應用程式。</span><span class="sxs-lookup"><span data-stu-id="5b195-109">The host to which each orchestration is bound.</span></span>  
  
- <span data-ttu-id="5b195-110">主控件的信任層級。</span><span class="sxs-lookup"><span data-stu-id="5b195-110">The trust level of the host.</span></span>  
  
- <span data-ttu-id="5b195-111">每個設定傳送埠、 接收埠、 接收位置，以及已設定的合作對象。</span><span class="sxs-lookup"><span data-stu-id="5b195-111">The settings for each send port, receive port, receive location, and party that has been configured.</span></span>  
  
  <span data-ttu-id="5b195-112">您可以產生繫結檔案，然後將它們包含的繫結套用至組件、 應用程式或群組。</span><span class="sxs-lookup"><span data-stu-id="5b195-112">You can generate binding files and then apply the bindings that they contain to an assembly, application, or group.</span></span> <span data-ttu-id="5b195-113">這可避免必須以手動方式設定在不同的部署環境中的 繫結，並加快應用程式部署。</span><span class="sxs-lookup"><span data-stu-id="5b195-113">This prevents having to manually configure bindings in different deployment environments and speeds up application deployment.</span></span>  
  
  <span data-ttu-id="5b195-114">BizTalk 組件、 應用程式或群組不會自動產生繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="5b195-114">A binding file is not automatically generated for a BizTalk assembly, application, or group.</span></span> <span data-ttu-id="5b195-115">不過，您可以產生繫結檔案匯出繫結。</span><span class="sxs-lookup"><span data-stu-id="5b195-115">However, you can generate a binding file by exporting bindings.</span></span> <span data-ttu-id="5b195-116">同樣地，您可以接著將繫結檔案匯入的應用程式或群組。</span><span class="sxs-lookup"><span data-stu-id="5b195-116">Similarly, you can then import the binding file into an application or group.</span></span> <span data-ttu-id="5b195-117">本節提供有關如何匯入和匯出繫結的指示。</span><span class="sxs-lookup"><span data-stu-id="5b195-117">This section provides instructions on how to import and export bindings.</span></span>  
  
  <span data-ttu-id="5b195-118">如需有關繫結和繫結檔案的詳細資訊，請參閱[繫結檔案和應用程式部署](../../core/binding-files-and-application-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="5b195-118">For more information about bindings and about binding files, see [Binding Files and Application Deployment](../../core/binding-files-and-application-deployment.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5b195-119">必要條件</span><span class="sxs-lookup"><span data-stu-id="5b195-119">Prerequisites</span></span>  
<span data-ttu-id="5b195-120">使用成員的帳戶登入[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理員 」 或 「 BizTalk 操作員群組。</span><span class="sxs-lookup"><span data-stu-id="5b195-120">Sign in with an account that is a member of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administrators or BizTalk Operators group.</span></span> <span data-ttu-id="5b195-121">如需詳細的權限的相關資訊，請參閱[部署和管理 BizTalk 應用程式所需的權限](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md)，並[最低安全性權限](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx)。</span><span class="sxs-lookup"><span data-stu-id="5b195-121">For more detailed information about permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), and [Minimum Security Rights](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx).</span></span>
 
## <a name="export-bindings"></a><span data-ttu-id="5b195-122">匯出繫結</span><span class="sxs-lookup"><span data-stu-id="5b195-122">Export bindings</span></span>
<span data-ttu-id="5b195-123">本節說明如何匯出到 XML 檔案的 BizTalk 應用程式的繫結。</span><span class="sxs-lookup"><span data-stu-id="5b195-123">This section describes how to export bindings for a BizTalk application into an XML file.</span></span> <span data-ttu-id="5b195-124">您接著可以從 XML 檔案的繫結匯入至另一個 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="5b195-124">You can then import the bindings from the XML file into another BizTalk application.</span></span> <span data-ttu-id="5b195-125">匯入繫結會覆寫任何現有的繫結的應用程式中相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="5b195-125">Importing bindings overwrites any existing bindings of the same name in the application.</span></span> <span data-ttu-id="5b195-126">您也可以將繫結加入應用程式中，這樣並不會覆寫現有的繫結。</span><span class="sxs-lookup"><span data-stu-id="5b195-126">You can also add bindings to an application, which does not overwrite existing bindings.</span></span> <span data-ttu-id="5b195-127">加入的繫結會在您匯入該應用程式之後才生效。</span><span class="sxs-lookup"><span data-stu-id="5b195-127">The bindings that you add do not take effect until you import the application.</span></span>  
  
1. <span data-ttu-id="5b195-128">開啟[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="5b195-128">Open the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="5b195-129">依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="5b195-129">Expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3. <span data-ttu-id="5b195-130">以滑鼠右鍵按一下 應用程式，選取您想要匯出其繫的結**匯出**，然後選取**繫結**。</span><span class="sxs-lookup"><span data-stu-id="5b195-130">Right-click the application whose bindings you want to export, select **Export**, and then select **Bindings**.</span></span>  
  
4. <span data-ttu-id="5b195-131">在 **匯出繫結**頁面上，於**匯出至檔案**，輸入要匯出繫結至 XML 檔案的絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="5b195-131">On the **Export Bindings** page, in **Export to file**, type the absolute path of the XML file to which to export the bindings.</span></span>  
  
    <span data-ttu-id="5b195-132">例如，輸入 `C:\Bindings\Application1Bindings.Binding1.xml`</span><span class="sxs-lookup"><span data-stu-id="5b195-132">For example, enter `C:\Bindings\Application1Bindings.Binding1.xml`</span></span>  
  
5. <span data-ttu-id="5b195-133">確認**從目前的應用程式匯出所有繫結**已選取。</span><span class="sxs-lookup"><span data-stu-id="5b195-133">Confirm that **Export all bindings from the current application** is selected.</span></span>  
  
6. <span data-ttu-id="5b195-134">若要匯出群組的所有合作對象資訊，請選取**匯出全域合作對象資訊**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="5b195-134">To export all party information for the group, select the **Export Global Party information** check box.</span></span>  
  
7. <span data-ttu-id="5b195-135">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="5b195-135">Select **OK**.</span></span> <span data-ttu-id="5b195-136">繫結都會匯出至 XML 檔案中您所指定的位置。</span><span class="sxs-lookup"><span data-stu-id="5b195-136">The bindings are exported into an XML file in the location that you specified.</span></span>  

## <a name="import-bindings"></a><span data-ttu-id="5b195-137">匯入繫結</span><span class="sxs-lookup"><span data-stu-id="5b195-137">Import bindings</span></span>
<span data-ttu-id="5b195-138">匯入繫結使用 BizTalk Server 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="5b195-138">Import bindings using the BizTalk Server Administration console.</span></span>
  
1. <span data-ttu-id="5b195-139">開啟[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="5b195-139">Open the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
2. <span data-ttu-id="5b195-140">依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="5b195-140">Expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3. <span data-ttu-id="5b195-141">以滑鼠右鍵按一下想要匯入繫結，請選取的應用程式**匯入**，然後選取**繫結**。</span><span class="sxs-lookup"><span data-stu-id="5b195-141">Right-click the application into which you want to import bindings, select **Import**, and then select **Bindings**.</span></span>  
  
4. <span data-ttu-id="5b195-142">選取繫結檔案，然後選取**開啟**。</span><span class="sxs-lookup"><span data-stu-id="5b195-142">Select the binding file, and then select **Open**.</span></span>  
  
<span data-ttu-id="5b195-143">繫結檔案中的成品會寫入此應用程式，</span><span class="sxs-lookup"><span data-stu-id="5b195-143">The artifacts in the binding file are written to the application.</span></span> <span data-ttu-id="5b195-144">這些成品會顯示在應用程式的適當資料夾中。</span><span class="sxs-lookup"><span data-stu-id="5b195-144">They display in appropriate folders of the application.</span></span> <span data-ttu-id="5b195-145">例如，傳送埠匯入繫結顯示下一部分**傳送埠**資料夾。</span><span class="sxs-lookup"><span data-stu-id="5b195-145">For example, the send ports imported as part of the bindings display under the **Send Ports** folder.</span></span>  

## <a name="passwords-are-removed"></a><span data-ttu-id="5b195-146">密碼會移除</span><span class="sxs-lookup"><span data-stu-id="5b195-146">Passwords are removed</span></span>  
<span data-ttu-id="5b195-147">基於安全性理由，當您匯出繫結檔案，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]從檔案移除繫結密碼。</span><span class="sxs-lookup"><span data-stu-id="5b195-147">For security reasons, when you export a binding file, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] removes the passwords for the bindings from the file.</span></span> <span data-ttu-id="5b195-148">匯入繫結後，您必須重新設定密碼，傳送埠和接受位置才能正常運作。</span><span class="sxs-lookup"><span data-stu-id="5b195-148">After importing the bindings, you must reconfigure passwords for send ports and receive locations before they will function.</span></span> <span data-ttu-id="5b195-149">您在的 [傳輸屬性] 對話方塊中設定密碼[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]系統管理主控台的 傳送埠或接收位置。</span><span class="sxs-lookup"><span data-stu-id="5b195-149">You configure passwords in the Transport Properties dialog box of the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console for the send port or receive location.</span></span> 

<span data-ttu-id="5b195-150">指定使用者名稱和密碼的相關資訊，請參閱[適用於 SQL Server，設定登入認證](../../adapters-and-accelerators/adapter-sql/configure-the-sign-in-credentials-for-the-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="5b195-150">For information about specifying user name and passwords, see [Configure the sign in credentials for the SQL Server](../../adapters-and-accelerators/adapter-sql/configure-the-sign-in-credentials-for-the-sql-adapter.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5b195-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b195-151">See Also</span></span>  
[<span data-ttu-id="5b195-152">若要開發使用 SQL 配接器的 BizTalk 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="5b195-152">Building blocks to develop BizTalk applications with the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)