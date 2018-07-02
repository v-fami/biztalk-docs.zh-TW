---
title: 若要建立的 SAP 應用程式的必要條件 |Microsoft Docs
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
ms.openlocfilehash: 72225a059d5b655555f46f06758df11de3eaa8e5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36978567"
---
# <a name="prerequisites-to-create-sap-applications"></a><span data-ttu-id="7a105-102">若要建立的 SAP 應用程式的必要條件</span><span class="sxs-lookup"><span data-stu-id="7a105-102">Prerequisites to create SAP applications</span></span>
<span data-ttu-id="7a105-103">本節提供有關開發 BizTalk 應用程式使用之前，您必須執行的工作資訊[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7a105-103">This section provides information about tasks that you must perform before developing BizTalk applications using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="7a105-104">區段也會列出一些用來開發 BizTalk 應用程式的 BizTalk Server 工具。</span><span class="sxs-lookup"><span data-stu-id="7a105-104">The section also lists some BizTalk Server tools that are used to develop BizTalk applications.</span></span>  

## <a name="create-a-strong-name-key-file"></a><span data-ttu-id="7a105-105">建立強式名稱金鑰檔</span><span class="sxs-lookup"><span data-stu-id="7a105-105">Create a strong-name key file</span></span>

<span data-ttu-id="7a105-106">您必須建立強式名稱金鑰檔來建置專案，在 Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7a105-106">You must create a strong-name key file to build projects in Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="7a105-107">強式名稱包含專案的身分識別-其簡單文字名稱、 版本號碼和文化特性資訊 （如果有提供）-加上公開金鑰和數位簽章。</span><span class="sxs-lookup"><span data-stu-id="7a105-107">A strong name consists of the project's identity—its simple text name, version number, and culture information (if provided)—plus a public key and a digital signature.</span></span> <span data-ttu-id="7a105-108">強式名稱金鑰檔案包含公開金鑰和私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="7a105-108">The strong-name key file contains the public key and the private key.</span></span>  

> [!IMPORTANT]
>  <span data-ttu-id="7a105-109">建立強式名稱金鑰檔是一次性的工作。</span><span class="sxs-lookup"><span data-stu-id="7a105-109">Creating a strong-name key file is a one-time task.</span></span> <span data-ttu-id="7a105-110">您可以使用相同的金鑰，如您所開發的所有 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7a105-110">You can use the same key for all the BizTalk applications you develop.</span></span>  

1.  <span data-ttu-id="7a105-111">開啟 Visual Studio 開發人員命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="7a105-111">Open the developer command prompt for Visual Studio.</span></span>  

2.  <span data-ttu-id="7a105-112">在命令提示字元中瀏覽至您要建立金鑰檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="7a105-112">At the command prompt navigate to the location where you want to create the key file.</span></span> <span data-ttu-id="7a105-113">例如，輸入**cd C:\Sample**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="7a105-113">For example, type **cd C:\Sample**,and then press ENTER.</span></span>  

3.  <span data-ttu-id="7a105-114">在命令提示字元中輸入 `sn -k <key file name\>.snk`，然後按下 ENTER。</span><span class="sxs-lookup"><span data-stu-id="7a105-114">At the command prompt, type `sn -k <key file name\>.snk`, and then press ENTER.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="7a105-115">您應該會收到訊息，指出金鑰組已寫入至強式名稱金鑰檔的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="7a105-115">You should receive a message at the command prompt stating that the key pair was written to the strong-name key file.</span></span>  

4.  <span data-ttu-id="7a105-116">在命令提示字元中，輸入**結束**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="7a105-116">At the command prompt, type **exit**, and then press ENTER.</span></span>  

## <a name="learn-the-biztalk-server-tools"></a><span data-ttu-id="7a105-117">了解 BizTalk Server 工具</span><span class="sxs-lookup"><span data-stu-id="7a105-117">Learn the BizTalk Server tools</span></span>

<span data-ttu-id="7a105-118">如何使用主題[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]中[開發 BizTalk 應用程式](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)假設您有數個 BizTalk Server 工具的實用知識。</span><span class="sxs-lookup"><span data-stu-id="7a105-118">The topics on how to use the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] in [Develop BizTalk applications](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md) assume that you have working knowledge of a number of BizTalk Server tools.</span></span> <span data-ttu-id="7a105-119">您將使用下列工具來開發 BizTalk 應用程式使用[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="7a105-119">You will use the following tools to develop BizTalk applications using [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]:</span></span>  

- <span data-ttu-id="7a105-120">Microsoft [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a105-120">Microsoft [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)]</span></span> 

- <span data-ttu-id="7a105-121">協調流程 eesigner</span><span class="sxs-lookup"><span data-stu-id="7a105-121">Orchestration eesigner</span></span>  

- <span data-ttu-id="7a105-122">管線設計師</span><span class="sxs-lookup"><span data-stu-id="7a105-122">Pipeline designer</span></span>  

- <span data-ttu-id="7a105-123">BizTalk 對應工具</span><span class="sxs-lookup"><span data-stu-id="7a105-123">BizTalk mapper</span></span>  

- [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7a105-124"> 管理主控台</span><span class="sxs-lookup"><span data-stu-id="7a105-124"> Administration console</span></span>  


### <a name="prerequisites"></a><span data-ttu-id="7a105-125">必要條件</span><span class="sxs-lookup"><span data-stu-id="7a105-125">Prerequisites</span></span>  
 <span data-ttu-id="7a105-126">您必須安裝 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 才能存取 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 工具。</span><span class="sxs-lookup"><span data-stu-id="7a105-126">You must install [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] before you can access the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] tools.</span></span>  

### <a name="biztalk-server-tools"></a><span data-ttu-id="7a105-127">BizTalk Server 工具</span><span class="sxs-lookup"><span data-stu-id="7a105-127">BizTalk Server Tools</span></span>  
 <span data-ttu-id="7a105-128">下表包含主題[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]文件說明如何使用每個列出的工具。</span><span class="sxs-lookup"><span data-stu-id="7a105-128">The following table includes topics in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] documentation that explain how to use each of the listed tools.</span></span>  


|                                   <span data-ttu-id="7a105-129">工具</span><span class="sxs-lookup"><span data-stu-id="7a105-129">Tool</span></span>                                    |                                                                                                                                                                                              <span data-ttu-id="7a105-130">中的主題[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]核心文件集</span><span class="sxs-lookup"><span data-stu-id="7a105-130">Topics in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] core documentation</span></span>                                                                                                                                                                                               |
|---------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] | <span data-ttu-id="7a105-131">-   [使用 Visual Studio](../../core/using-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="7a105-131">-   [Using Visual Studio](../../core/using-visual-studio.md)</span></span> <br /><span data-ttu-id="7a105-132">-   [使用 BizTalk 專案](../../core/working-with-biztalk-projects.md)</span><span class="sxs-lookup"><span data-stu-id="7a105-132">-   [Working with BizTalk Projects](../../core/working-with-biztalk-projects.md)</span></span><br /><span data-ttu-id="7a105-133">-   [部署 BizTalk 組件從 Visual Studio 到 BizTalk 應用程式](../../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)</span><span class="sxs-lookup"><span data-stu-id="7a105-133">-   [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)</span></span><br /><br /> <span data-ttu-id="7a105-134">深入了解 Visual Studio 方案、 專案和項目會在[Visual Studio 中方案和專案](https://msdn.microsoft.com/library/b142f8e7.aspx)。</span><span class="sxs-lookup"><span data-stu-id="7a105-134">Learn more about Visual Studio solutions, projects, and items at [Solutions and Projects in Visual Studio](https://msdn.microsoft.com/library/b142f8e7.aspx).</span></span> |
|                          <span data-ttu-id="7a105-135">協調流程設計師</span><span class="sxs-lookup"><span data-stu-id="7a105-135">Orchestration Designer</span></span>                           |                                                                                                                                                                                          [<span data-ttu-id="7a105-136">使用協調流程設計師建立協調流程</span><span class="sxs-lookup"><span data-stu-id="7a105-136">Creating orchestrations using orchestration designer</span></span>](../../core/creating-orchestrations-using-orchestration-designer.md)                                                                                                                                                                                           |
|                             <span data-ttu-id="7a105-137">管線設計師</span><span class="sxs-lookup"><span data-stu-id="7a105-137">Pipeline Designer</span></span>                             |                                                                                                                                                                                                    [<span data-ttu-id="7a105-138">使用管線設計師建立管線</span><span class="sxs-lookup"><span data-stu-id="7a105-138">Creating pipelines using pipeline designer</span></span>](../../core/creating-pipelines-using-pipeline-designer.md)                                                                                                                                                                                                     |
|                              <span data-ttu-id="7a105-139">BizTalk Mapper (BizTalk 對應工具)</span><span class="sxs-lookup"><span data-stu-id="7a105-139">BizTalk Mapper</span></span>                               |                                                                                                                                                                                                            [<span data-ttu-id="7a105-140">使用 BizTalk 對應工具建立對應</span><span class="sxs-lookup"><span data-stu-id="7a105-140">Creating maps using BizTalk mapper</span></span>](../../core/creating-maps-using-biztalk-mapper.md)                                                                                                                                                                                                             |
|                   <span data-ttu-id="7a105-141">BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="7a105-141">BizTalk Server Administration console</span></span>                   |                                                                                                                                                                                               [<span data-ttu-id="7a105-142">使用 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="7a105-142">Using the BizTalk Server Administration console</span></span>](../../core/using-the-biztalk-server-administration-console.md)                                                                                                                                                                                                |

## <a name="next"></a><span data-ttu-id="7a105-143">下一個</span><span class="sxs-lookup"><span data-stu-id="7a105-143">Next</span></span>
[<span data-ttu-id="7a105-144">建立 SAP 應用程式的建構元素</span><span class="sxs-lookup"><span data-stu-id="7a105-144">Building blocks to create SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)