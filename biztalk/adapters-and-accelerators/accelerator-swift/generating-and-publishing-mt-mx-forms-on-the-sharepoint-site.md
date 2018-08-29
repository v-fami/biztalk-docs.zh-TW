---
title: 產生和發佈 MT MX 表單在 SharePoint 網站上的 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4adf7117-11ad-4a8e-8d6a-fd78c5e496a3
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 492eda3b4bf3d3950c084bc9234b52b911b84a2b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980047"
---
# <a name="generating-and-publishing-mtmx-forms-on-the-sharepoint-site"></a><span data-ttu-id="9c488-102">產生和發佈 MT/MX 表單在 SharePoint 網站上</span><span class="sxs-lookup"><span data-stu-id="9c488-102">Generating and Publishing MT/MX Forms on the SharePoint Site</span></span>
<span data-ttu-id="9c488-103">**若要產生和發佈 MT/MX 表單在 SharePoint 網站上：**</span><span class="sxs-lookup"><span data-stu-id="9c488-103">**To generate and publish MT/MX forms on a SharePoint site:**</span></span>  

1. <span data-ttu-id="9c488-104">下載表單產生器公用程式，並將它儲存在本機電腦上。</span><span class="sxs-lookup"><span data-stu-id="9c488-104">Download the Form Generator Utility and save it locally on the computer.</span></span>  

2. <span data-ttu-id="9c488-105">開啟**FormGenerator.sln**資料夾從上述下載並編譯解決方案。</span><span class="sxs-lookup"><span data-stu-id="9c488-105">Open the **FormGenerator.sln** from the folder downloaded above and compile the solution.</span></span>  

3. <span data-ttu-id="9c488-106">在命令提示字元中，存取已編譯可執行檔 (FormGenerator.exe) 的資料夾。</span><span class="sxs-lookup"><span data-stu-id="9c488-106">At a command prompt, access the folder of compiled executable (FormGenerator.exe).</span></span> <span data-ttu-id="9c488-107">例如，如果您已建立偵錯模式中的公用程式，存取 **...\bin\debug**資料夾。</span><span class="sxs-lookup"><span data-stu-id="9c488-107">For example, if you have built the utility in debug mode, access the **..\bin\debug** folder.</span></span>  

4. <span data-ttu-id="9c488-108">輸入 FormGenerator.exe [-b] [-\<[否]。</span><span class="sxs-lookup"><span data-stu-id="9c488-108">Type FormGenerator.exe [-b] [-\<No.</span></span> <span data-ttu-id="9c488-109">範本資料夾路徑\>]</span><span class="sxs-lookup"><span data-stu-id="9c488-109">of Template folder paths\>]</span></span>  

    <span data-ttu-id="9c488-110">`<TemplateFolderPath> <DestinationFolderPath> <DocumentSchemaLocation> {[<SpaceSeparatedDocumentSchemaList>] | [-f <NameOfFileContainingSchemaList>]}`。</span><span class="sxs-lookup"><span data-stu-id="9c488-110">`<TemplateFolderPath> <DestinationFolderPath> <DocumentSchemaLocation> {[<SpaceSeparatedDocumentSchemaList>] | [-f <NameOfFileContainingSchemaList>]}`.</span></span> <span data-ttu-id="9c488-111">參數取代為新建立的資料夾名稱。</span><span class="sxs-lookup"><span data-stu-id="9c488-111">Replace the parameters with the newly-created folder names.</span></span>  

5. <span data-ttu-id="9c488-112">上述命令也會產生 MX 訊息修復所需的信封結構描述。</span><span class="sxs-lookup"><span data-stu-id="9c488-112">The above command will also generate the Envelope schema needed for MX message repair.</span></span>  

6. <span data-ttu-id="9c488-113">移至輸出資料夾\<DestinationFolderPath\>。</span><span class="sxs-lookup"><span data-stu-id="9c488-113">Go to output folder \<DestinationFolderPath\>.</span></span> <span data-ttu-id="9c488-114">在  \<DestinationFolderPath\>，開啟您要產生表單的 InfoPath 表單範本的資料夾。</span><span class="sxs-lookup"><span data-stu-id="9c488-114">In \<DestinationFolderPath\>, open the folder of the InfoPath form template for which you want to generate the form.</span></span> <span data-ttu-id="9c488-115">例如，如果您想要產生 MT103 InfoPath 表單，然後開啟 DestinationFolderPath 的 MT103 資料夾，然後開啟 TemplateDS.sln。</span><span class="sxs-lookup"><span data-stu-id="9c488-115">For example, if you want to generate the MT103 InfoPath form, then open the MT103 folder at the DestinationFolderPath and open the TemplateDS.sln.</span></span>  

7. <span data-ttu-id="9c488-116">在 [方案總管] 中，按兩下**manifest.xsf**。</span><span class="sxs-lookup"><span data-stu-id="9c488-116">In the Solution Explorer, double click the **manifest.xsf**.</span></span> <span data-ttu-id="9c488-117">它會開啟將會需要一些時間才能取得開啟的 InfoPath 表單的設計檔案。</span><span class="sxs-lookup"><span data-stu-id="9c488-117">It will open the design file of the InfoPath form which will take some time to get opened.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="9c488-118">MX 訊息 manifest.xsf 可能需要 2 到 5 分鐘，才能取得開啟。</span><span class="sxs-lookup"><span data-stu-id="9c488-118">The MX messages manifest.xsf might take 2-5 minutes to get opened.</span></span>  

8. <span data-ttu-id="9c488-119">在 [manifest.xsf，移至**工具]-> [表單選項]-> 安全性和信任**功能表選項。</span><span class="sxs-lookup"><span data-stu-id="9c488-119">In the manifest.xsf, go to **Tools ->Form Options-> Security and Trust** menu option.</span></span> <span data-ttu-id="9c488-120">請檢查**完全信任**選項必須啟用權限。</span><span class="sxs-lookup"><span data-stu-id="9c488-120">Check the **Full Trust** option must be enabled for the permission.</span></span>  

9. <span data-ttu-id="9c488-121">選取 **簽章此表單範本**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="9c488-121">Select the **Sign this form Template** checkbox.</span></span> <span data-ttu-id="9c488-122">按一下 **選取憑證**。</span><span class="sxs-lookup"><span data-stu-id="9c488-122">Click **Select certificate**.</span></span> <span data-ttu-id="9c488-123">在這個中，選取您要登入表單的憑證。</span><span class="sxs-lookup"><span data-stu-id="9c488-123">In this, select the certificate with which you want to sign the form.</span></span> <span data-ttu-id="9c488-124">按一下 [確定] 。</span><span class="sxs-lookup"><span data-stu-id="9c488-124">Click **OK**.</span></span>  

10. <span data-ttu-id="9c488-125">儲存**manifest.xsf**。</span><span class="sxs-lookup"><span data-stu-id="9c488-125">Save **manifest.xsf**.</span></span>  

11. <span data-ttu-id="9c488-126">移至**檢視-> 設計工作**。</span><span class="sxs-lookup"><span data-stu-id="9c488-126">Go to **View -> Design Tasks**.</span></span> <span data-ttu-id="9c488-127">在設計工作] 窗格中，按一下 [**發佈表單範本**選項。</span><span class="sxs-lookup"><span data-stu-id="9c488-127">On the Design Tasks pane, click **Publish Form Template** option.</span></span>  

12. <span data-ttu-id="9c488-128">在 發行精靈 視窗中，選取**通往網路位置**然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="9c488-128">In the publishing wizard window, select **To a network location** and click **Next**.</span></span>  

13. <span data-ttu-id="9c488-129">在 表單範本的路徑和檔案名稱 文字方塊中輸入<strong>http://localhost/sites/BASSite/Templates/\<MessageType\>.xsn</strong>並輸入**\<MessageType\>** 表單範本中命名文字方塊，然後按一下**下一步**.</span><span class="sxs-lookup"><span data-stu-id="9c488-129">In the Form template path and file name textbox, type <strong>http://localhost/sites/BASSite/Templates/\<MessageType\>.xsn</strong> and type **\<MessageType\>** in the Form Template name textbox and click **Next**.</span></span>  

14. <span data-ttu-id="9c488-130">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="9c488-130">Click **Next**.</span></span>  

15. <span data-ttu-id="9c488-131">按一下 **發行並關閉**。</span><span class="sxs-lookup"><span data-stu-id="9c488-131">Click **Publish and close**.</span></span>  

16. <span data-ttu-id="9c488-132">在 Internet Explorer 中，開啟 SharePoint 網站**http://localhost/sites/bassite/templates**。</span><span class="sxs-lookup"><span data-stu-id="9c488-132">In the Internet Explorer, open your SharePoint site **http://localhost/sites/bassite/templates**.</span></span>  

17. <span data-ttu-id="9c488-133">指向 **\<MessageType\>**，按一下它，旁邊的向下箭號，然後按一下**編輯屬性**。</span><span class="sxs-lookup"><span data-stu-id="9c488-133">Point to **\<MessageType\>**, click the down arrow next to it, and then click **Edit Properties**.</span></span>  

18. <span data-ttu-id="9c488-134">在範本中：\< MessageType\>視窗中的，在命名空間中：</span><span class="sxs-lookup"><span data-stu-id="9c488-134">In the Templates:\< MessageType\> window, in the Namespace box:</span></span>  

    - <span data-ttu-id="9c488-135">如果您要產生 MT InfoPath 表單，輸入： **http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/EnvelopeMTxxx**</span><span class="sxs-lookup"><span data-stu-id="9c488-135">If you are generating MT InfoPath forms, type: **http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/EnvelopeMTxxx**</span></span>  

    - <span data-ttu-id="9c488-136">如果您要產生 MX InfoPath 表單，輸入： <strong>http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/EnvelopeMX_\<MessageName\></strong></span><span class="sxs-lookup"><span data-stu-id="9c488-136">If you are generating MX InfoPath forms, type: <strong>http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/EnvelopeMX_\<MessageName\></strong></span></span>  

       <span data-ttu-id="9c488-137">這有助於識別訊息執行個體與對應的範本。</span><span class="sxs-lookup"><span data-stu-id="9c488-137">This will help in identifying the message instance with the corresponding template.</span></span>  

19. <span data-ttu-id="9c488-138">按一下 **儲存並關閉**。</span><span class="sxs-lookup"><span data-stu-id="9c488-138">Click **Save and Close**.</span></span>
