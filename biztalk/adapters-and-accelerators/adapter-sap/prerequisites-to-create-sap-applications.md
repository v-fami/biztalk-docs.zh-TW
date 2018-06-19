---
title: 若要建立的 SAP 應用程式的必要條件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51ae9569-4081-4142-9ee2-8ae0069e9d90
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b7cddc252868bf47ace0d73e81ddb1c7721bf8a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216398"
---
# <a name="prerequisites-to-create-sap-applications"></a><span data-ttu-id="398f8-102">若要建立的 SAP 應用程式的必要條件</span><span class="sxs-lookup"><span data-stu-id="398f8-102">Prerequisites to create SAP applications</span></span>
<span data-ttu-id="398f8-103">本節提供有關開發 BizTalk 應用程式使用之前，您必須執行的工作資訊[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="398f8-103">This section provides information about tasks that you must perform before developing BizTalk applications using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="398f8-104">一節也會列出一些可用來開發 BizTalk 應用程式的 BizTalk Server 工具。</span><span class="sxs-lookup"><span data-stu-id="398f8-104">The section also lists some BizTalk Server tools that are used to develop BizTalk applications.</span></span>  
  
## <a name="create-a-strong-name-key-file"></a><span data-ttu-id="398f8-105">建立強式名稱金鑰檔案</span><span class="sxs-lookup"><span data-stu-id="398f8-105">Create a strong-name key file</span></span>

<span data-ttu-id="398f8-106">您必須建立強式名稱金鑰檔案來建置專案，在 Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="398f8-106">You must create a strong-name key file to build projects in Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="398f8-107">強式名稱包含專案的身分識別-其簡單文字名稱、 版本號碼和文化特性資訊 （如果有提供）-加上公開金鑰與數位簽章。</span><span class="sxs-lookup"><span data-stu-id="398f8-107">A strong name consists of the project's identity—its simple text name, version number, and culture information (if provided)—plus a public key and a digital signature.</span></span> <span data-ttu-id="398f8-108">強式名稱金鑰檔案包含公開金鑰和私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="398f8-108">The strong-name key file contains the public key and the private key.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="398f8-109">建立強式名稱金鑰檔是一次性的工作。</span><span class="sxs-lookup"><span data-stu-id="398f8-109">Creating a strong-name key file is a one-time task.</span></span> <span data-ttu-id="398f8-110">您可以使用相同的金鑰，您所開發的所有 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="398f8-110">You can use the same key for all the BizTalk applications you develop.</span></span>  
  
1.  <span data-ttu-id="398f8-111">開啟 Visual Studio 開發人員命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="398f8-111">Open the developer command prompt for Visual Studio.</span></span>  
  
2.  <span data-ttu-id="398f8-112">在命令提示字元中瀏覽至您要建立金鑰檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="398f8-112">At the command prompt navigate to the location where you want to create the key file.</span></span> <span data-ttu-id="398f8-113">例如，輸入**cd C:\Sample**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="398f8-113">For example, type **cd C:\Sample**,and then press ENTER.</span></span>  
  
3.  <span data-ttu-id="398f8-114">在命令提示字元中輸入 `sn -k <key file name\>.snk`，然後按下 ENTER。</span><span class="sxs-lookup"><span data-stu-id="398f8-114">At the command prompt, type `sn -k <key file name\>.snk`, and then press ENTER.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="398f8-115">您應該會收到訊息，指出金鑰組已寫入至強式名稱金鑰檔的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="398f8-115">You should receive a message at the command prompt stating that the key pair was written to the strong-name key file.</span></span>  
  
4.  <span data-ttu-id="398f8-116">在命令提示字元中，輸入**結束**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="398f8-116">At the command prompt, type **exit**, and then press ENTER.</span></span>  

## <a name="learn-the-biztalk-server-tools"></a><span data-ttu-id="398f8-117">了解 BizTalk Server 工具</span><span class="sxs-lookup"><span data-stu-id="398f8-117">Learn the BizTalk Server tools</span></span>

<span data-ttu-id="398f8-118">如何使用主題[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]中[開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)假設您有數個 BizTalk Server 工具的實用知識。</span><span class="sxs-lookup"><span data-stu-id="398f8-118">The topics on how to use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] in [Develop BizTalk applications](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md) assume that you have working knowledge of a number of BizTalk Server tools.</span></span> <span data-ttu-id="398f8-119">您將使用下列工具來開發 BizTalk 應用程式使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="398f8-119">You will use the following tools to develop BizTalk applications using [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]:</span></span>  
  
-   <span data-ttu-id="398f8-120">Microsoft [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="398f8-120">Microsoft [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)]</span></span> 
  
-   <span data-ttu-id="398f8-121">協調流程 eesigner</span><span class="sxs-lookup"><span data-stu-id="398f8-121">Orchestration eesigner</span></span>  
  
-   <span data-ttu-id="398f8-122">管線設計師</span><span class="sxs-lookup"><span data-stu-id="398f8-122">Pipeline designer</span></span>  
  
-   <span data-ttu-id="398f8-123">BizTalk 對應工具</span><span class="sxs-lookup"><span data-stu-id="398f8-123">BizTalk mapper</span></span>  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="398f8-124"> 管理主控台</span><span class="sxs-lookup"><span data-stu-id="398f8-124"> Administration console</span></span>  

  
### <a name="prerequisites"></a><span data-ttu-id="398f8-125">必要條件</span><span class="sxs-lookup"><span data-stu-id="398f8-125">Prerequisites</span></span>  
 <span data-ttu-id="398f8-126">您必須安裝 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 才能存取 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 工具。</span><span class="sxs-lookup"><span data-stu-id="398f8-126">You must install [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] before you can access the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] tools.</span></span>  
  
### <a name="biztalk-server-tools"></a><span data-ttu-id="398f8-127">BizTalk Server 工具</span><span class="sxs-lookup"><span data-stu-id="398f8-127">BizTalk Server Tools</span></span>  
 <span data-ttu-id="398f8-128">下表包含本節中的主題[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]文件說明如何使用每個列出的工具。</span><span class="sxs-lookup"><span data-stu-id="398f8-128">The following table includes topics in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] documentation that explain how to use each of the listed tools.</span></span>  

|<span data-ttu-id="398f8-129">工具</span><span class="sxs-lookup"><span data-stu-id="398f8-129">Tool</span></span>|<span data-ttu-id="398f8-130">本節中的主題[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]核心文件</span><span class="sxs-lookup"><span data-stu-id="398f8-130">Topics in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] core documentation</span></span>|  
|---|---|  
|[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]|<span data-ttu-id="398f8-131">-   [使用 Visual Studio](../../core/using-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="398f8-131">-   [Using Visual Studio](../../core/using-visual-studio.md)</span></span> <br /><span data-ttu-id="398f8-132">-   [使用 BizTalk 專案](../../core/working-with-biztalk-projects.md)</span><span class="sxs-lookup"><span data-stu-id="398f8-132">-   [Working with BizTalk Projects](../../core/working-with-biztalk-projects.md)</span></span><br /><span data-ttu-id="398f8-133">-   [部署 BizTalk 組件從 Visual Studio 到 BizTalk 應用程式](../../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)</span><span class="sxs-lookup"><span data-stu-id="398f8-133">-   [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)</span></span><br /><br /> <span data-ttu-id="398f8-134">深入了解 Visual Studio 方案、 專案和項目會在[方案和專案在 Visual Studio](https://msdn.microsoft.com/library/b142f8e7.aspx)。</span><span class="sxs-lookup"><span data-stu-id="398f8-134">Learn more about Visual Studio solutions, projects, and items at [Solutions and Projects in Visual Studio](https://msdn.microsoft.com/library/b142f8e7.aspx).</span></span>|  
|<span data-ttu-id="398f8-135">協調流程設計師</span><span class="sxs-lookup"><span data-stu-id="398f8-135">Orchestration Designer</span></span>|[<span data-ttu-id="398f8-136">建立協調流程使用協調流程設計師</span><span class="sxs-lookup"><span data-stu-id="398f8-136">Creating orchestrations using orchestration designer</span></span>](../../core/creating-orchestrations-using-orchestration-designer.md)|  
|<span data-ttu-id="398f8-137">管線設計師</span><span class="sxs-lookup"><span data-stu-id="398f8-137">Pipeline Designer</span></span>| [<span data-ttu-id="398f8-138">建立管線使用管線設計師</span><span class="sxs-lookup"><span data-stu-id="398f8-138">Creating pipelines using pipeline designer</span></span>](../../core/creating-pipelines-using-pipeline-designer.md)|  
|<span data-ttu-id="398f8-139">BizTalk Mapper (BizTalk 對應工具)</span><span class="sxs-lookup"><span data-stu-id="398f8-139">BizTalk Mapper</span></span>| [<span data-ttu-id="398f8-140">使用 BizTalk 對應工具建立對應</span><span class="sxs-lookup"><span data-stu-id="398f8-140">Creating maps using BizTalk mapper</span></span>](../../core/creating-maps-using-biztalk-mapper.md)|  
|<span data-ttu-id="398f8-141">BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="398f8-141">BizTalk Server Administration console</span></span>|[<span data-ttu-id="398f8-142">使用 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="398f8-142">Using the BizTalk Server Administration console</span></span>](../../core/using-the-biztalk-server-administration-console.md)|  

## <a name="next"></a><span data-ttu-id="398f8-143">下一個</span><span class="sxs-lookup"><span data-stu-id="398f8-143">Next</span></span>
[<span data-ttu-id="398f8-144">若要建立的 SAP 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="398f8-144">Building blocks to create SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)