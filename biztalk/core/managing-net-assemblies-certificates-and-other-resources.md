---
title: 管理.NET 組件、 憑證和其他資源 |Microsoft 文件
description: 若要加入繫結檔案、 憑證、 組件、 虛擬目錄、 檔案和多個 BizTalk Server 中的連結
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efe27a11-19d8-4eb3-9f8c-f4336e4c3d66
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fdb74762bdf08e6e9e2a79650a26dedb0915ea8f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262726"
---
# <a name="manage-net-assemblies-certificates-and-other-resources"></a><span data-ttu-id="a1918-103">管理.NET 組件、 憑證和其他資源</span><span class="sxs-lookup"><span data-stu-id="a1918-103">Manage .NET Assemblies, Certificates, and Other Resources</span></span>

## <a name="overview"></a><span data-ttu-id="a1918-104">概觀</span><span class="sxs-lookup"><span data-stu-id="a1918-104">Overview</span></span>
<span data-ttu-id="a1918-105">本節提供相關指示，說明如何使用 BizTalk Server 管理主控台和 BTSTask 命令列工具來管理下列類型的 BizTalk 應用程式資源成品。</span><span class="sxs-lookup"><span data-stu-id="a1918-105">This section provides instructions on using the BizTalk Server Administration console and the BTSTask command-line tool to manage the following types of resource artifacts for a BizTalk application.</span></span> <span data-ttu-id="a1918-106">這些資源成品無法從 Visual Studio 自動部署到 BizTalk 應用程式，所以必須以手動方式將它們新增至應用程式。</span><span class="sxs-lookup"><span data-stu-id="a1918-106">These resource artifacts cannot be automatically deployed into a BizTalk application from Visual Studio, so you must add them manually to the application.</span></span> <span data-ttu-id="a1918-107">不過，一旦新增至應用程式後，您就可以將這些資源成品當做一個單位，搭配應用程式和應用程式的其他成品而進行匯入、匯出及安裝。</span><span class="sxs-lookup"><span data-stu-id="a1918-107">Once added to an application, however, you can import, export, and install them as a unit with the application and its other artifacts.</span></span>  
  
-   <span data-ttu-id="a1918-108">**檔案。**</span><span class="sxs-lookup"><span data-stu-id="a1918-108">**Files.**</span></span> <span data-ttu-id="a1918-109">您可以包含特定的檔案，例如讀我檔案。</span><span class="sxs-lookup"><span data-stu-id="a1918-109">You can include ad hoc files, such as a Readme file.</span></span> <span data-ttu-id="a1918-110">當您在安裝應用程式時，檔案會複製到安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="a1918-110">When you install the application, files are copied to the installation folder.</span></span>  
  
-   <span data-ttu-id="a1918-111">**憑證。**</span><span class="sxs-lookup"><span data-stu-id="a1918-111">**Certificates.**</span></span> <span data-ttu-id="a1918-112">您可以將憑證檔案新增至應用程式，如此就可以將憑證封裝於應用程式中，從一個 BizTalk 群組傳輸到另一個群組。</span><span class="sxs-lookup"><span data-stu-id="a1918-112">You can add a certificate file to an application so that you can transport the certificate from one BizTalk group to another, packaged with an application.</span></span> <span data-ttu-id="a1918-113">您要將憑證指定給傳送埠和接收位置，以確認識別並建立安全的連結。</span><span class="sxs-lookup"><span data-stu-id="a1918-113">You assign certificates to send ports and receive locations to verify identities and to establish secure links.</span></span>  
  
-   <span data-ttu-id="a1918-114">**COM 和 COM + 元件。**</span><span class="sxs-lookup"><span data-stu-id="a1918-114">**COM and COM+ components.**</span></span> <span data-ttu-id="a1918-115">您可以包含 Managed COM 和 Managed COM+ 元件，以在 BizTalk 應用程式中提供其他功能。</span><span class="sxs-lookup"><span data-stu-id="a1918-115">You can include managed COM and managed COM+ components to provide additional functionality in a BizTalk application.</span></span>  
  
-   <span data-ttu-id="a1918-116">**.NET 組件。**</span><span class="sxs-lookup"><span data-stu-id="a1918-116">**.NET assemblies.**</span></span> <span data-ttu-id="a1918-117">您可以在 BizTalk 應用程式中，包含並非確實為 BizTalk 組件的 .NET 組件</span><span class="sxs-lookup"><span data-stu-id="a1918-117">You can include .NET assemblies that are not specifically BizTalk assemblies in a BizTalk application.</span></span> <span data-ttu-id="a1918-118">(BizTalk 組件是包含 BizTalk 協調流程、管線、結構描述或對應的 .NET 組件)。</span><span class="sxs-lookup"><span data-stu-id="a1918-118">(BizTalk assemblies are .NET assemblies that contain BizTalk orchestrations, pipelines, schemas, or maps.)</span></span>  
  
-   <span data-ttu-id="a1918-119">**BAM 定義檔案。**</span><span class="sxs-lookup"><span data-stu-id="a1918-119">**BAM definition files.**</span></span> <span data-ttu-id="a1918-120">若要簡化 BAM 的部署，可以建立 BizTalk 應用程式，然後再對該應用程式新增 BAM 定義。</span><span class="sxs-lookup"><span data-stu-id="a1918-120">To make BAM deployment easier, you can create a BizTalk application and add BAM definitions to it.</span></span> <span data-ttu-id="a1918-121">接下來可以使用 BizTalk 應用程式部署功能，將 BAM 定義部署到不同的環境中。</span><span class="sxs-lookup"><span data-stu-id="a1918-121">You can then use the BizTalk application deployment features to deploy the BAM definitions into different environments.</span></span>  
  
-   <span data-ttu-id="a1918-122">**繫結檔案。**</span><span class="sxs-lookup"><span data-stu-id="a1918-122">**Binding files.**</span></span> <span data-ttu-id="a1918-123">您可以將繫結檔案新增至應用程式，這樣可以更輕鬆快速地將應用程式從一個部署環境移至另一個部署環境。</span><span class="sxs-lookup"><span data-stu-id="a1918-123">You can add binding files to an application to make moving an application from one deployment environment to another quicker and easier.</span></span>  
  
-   <span data-ttu-id="a1918-124">**虛擬目錄。**</span><span class="sxs-lookup"><span data-stu-id="a1918-124">**Virtual directories.**</span></span> <span data-ttu-id="a1918-125">您可以將虛擬目錄新增至應用程式，讓虛擬目錄可以和應用程式一起部署。</span><span class="sxs-lookup"><span data-stu-id="a1918-125">You can add virtual directories to your application so that they will be deployed with the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1918-126">您可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。</span><span class="sxs-lookup"><span data-stu-id="a1918-126">You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="a1918-127">如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="a1918-127">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="a1918-128">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="a1918-128">Next steps</span></span>
  
-   [<span data-ttu-id="a1918-129">將檔案加入應用程式</span><span class="sxs-lookup"><span data-stu-id="a1918-129">Add a File to an Application</span></span>](../core/how-to-add-a-file-to-an-application.md)  
  
-   [<span data-ttu-id="a1918-130">將憑證新增至應用程式</span><span class="sxs-lookup"><span data-stu-id="a1918-130">Add a Certificate to an Application</span></span>](../core/how-to-add-a-certificate-to-an-application.md)  
  
-   [<span data-ttu-id="a1918-131">將 COM 元件加入至應用程式</span><span class="sxs-lookup"><span data-stu-id="a1918-131">Add a COM Component to an Application</span></span>](../core/how-to-add-a-com-component-to-an-application.md)  
  
-   [<span data-ttu-id="a1918-132">應用程式中加入.NET 組件</span><span class="sxs-lookup"><span data-stu-id="a1918-132">Add a .NET Assembly to an Application</span></span>](../core/how-to-add-a-net-assembly-to-an-application.md)  
  
-   [<span data-ttu-id="a1918-133">應用程式中加入 BAM 成品</span><span class="sxs-lookup"><span data-stu-id="a1918-133">Add a BAM Artifact to an Application</span></span>](../core/how-to-add-a-bam-artifact-to-an-application.md)  
  
-   [<span data-ttu-id="a1918-134">應用程式中加入繫結檔案</span><span class="sxs-lookup"><span data-stu-id="a1918-134">Add a Binding File to an Application</span></span>](../core/how-to-add-a-binding-file-to-an-application2.md)  
  
-   [<span data-ttu-id="a1918-135">應用程式中加入虛擬目錄</span><span class="sxs-lookup"><span data-stu-id="a1918-135">Add a Virtual Directory to an Application</span></span>](../core/how-to-add-a-virtual-directory-to-an-application.md)  
  
-   [<span data-ttu-id="a1918-136">修改.NET 組件、 COM 元件、 檔案或 BAM 成品的部署選項</span><span class="sxs-lookup"><span data-stu-id="a1918-136">Modify the Deployment Options of a .NET Assembly, COM Component, File, or BAM Artifact</span></span>](../core/modify-deployment-options-of-net-assembly-com-component-file-bam-artifact.md)  
  
-   [<span data-ttu-id="a1918-137">移除應用程式的.NET 組件、 憑證或其他資源成品</span><span class="sxs-lookup"><span data-stu-id="a1918-137">Remove a .NET Assembly, Certificate, or Other Resource Artifact from an Application</span></span>](../core/remove-a-net-assembly-certificate-or-resource-artifact-from-an-application.md)