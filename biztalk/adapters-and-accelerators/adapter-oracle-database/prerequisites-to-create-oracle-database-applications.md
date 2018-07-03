---
title: 若要建立 Oracle 資料庫應用程式的必要條件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- strong-name key file, creating a
ms.assetid: 7a6b2e50-8153-468c-a25e-c15612792773
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5ed7056ad860af9f54a247a7014189fb3b45527
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979975"
---
# <a name="prerequisites-to-create-oracle-database-applications"></a><span data-ttu-id="ea6f0-102">若要建立 Oracle 資料庫應用程式的必要條件</span><span class="sxs-lookup"><span data-stu-id="ea6f0-102">Prerequisites to create Oracle Database applications</span></span>
<span data-ttu-id="ea6f0-103">您必須執行在開發 BizTalk 應用程式使用之前[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ea6f0-103">What you must do before developing BizTalk applications using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="ea6f0-104">區段也會列出一些用來開發 BizTalk 應用程式的 BizTalk Server 工具。</span><span class="sxs-lookup"><span data-stu-id="ea6f0-104">The section also lists some BizTalk Server tools that are used to develop BizTalk applications.</span></span>  

## <a name="create-a-strong-named-key-file"></a><span data-ttu-id="ea6f0-105">建立強式名稱金鑰檔</span><span class="sxs-lookup"><span data-stu-id="ea6f0-105">Create a strong-named key file</span></span>

<span data-ttu-id="ea6f0-106">您必須建立強式名稱金鑰檔來建置專案，在 Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ea6f0-106">You must create a strong-name key file to build projects in Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="ea6f0-107">強式名稱包含專案的身分識別-其簡單文字名稱、 版本號碼和文化特性資訊 （如果有提供）;再加上公開金鑰和數位簽章。</span><span class="sxs-lookup"><span data-stu-id="ea6f0-107">A strong name consists of the project's identity — its simple text name, version number, and culture information (if provided); plus a public key and a digital signature.</span></span> <span data-ttu-id="ea6f0-108">強式名稱金鑰檔案包含公開金鑰和私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="ea6f0-108">The strong-name key file contains the public key and the private key.</span></span>  

> [!IMPORTANT]
>  <span data-ttu-id="ea6f0-109">建立強式名稱金鑰檔是一次性的工作。</span><span class="sxs-lookup"><span data-stu-id="ea6f0-109">Creating a strong-name key file is a one-time task.</span></span> <span data-ttu-id="ea6f0-110">您可以使用相同的金鑰，如您所開發的所有 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ea6f0-110">You can use the same key for all the BizTalk applications you develop.</span></span>  

### <a name="prerequisites"></a><span data-ttu-id="ea6f0-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="ea6f0-111">Prerequisites</span></span>  
 <span data-ttu-id="ea6f0-112">您必須有 Microsoft[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]安裝在您要建立強式名稱金鑰的電腦上。</span><span class="sxs-lookup"><span data-stu-id="ea6f0-112">You must have Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] installed on the computer where you want to create a strong-name key.</span></span>  

### <a name="create-a-strong-name-key-file"></a><span data-ttu-id="ea6f0-113">建立強式名稱金鑰檔</span><span class="sxs-lookup"><span data-stu-id="ea6f0-113">Create a strong-name key file</span></span>  

1.  <span data-ttu-id="ea6f0-114">開啟 Visual Studio 開發人員命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="ea6f0-114">Open the developer command prompt for Visual Studio.</span></span>  

2.  <span data-ttu-id="ea6f0-115">在命令提示字元中，瀏覽至您要建立金鑰檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="ea6f0-115">At the command prompt, navigate to the location where you want to create the key file.</span></span> <span data-ttu-id="ea6f0-116">例如，輸入`cd C:\Sample`，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="ea6f0-116">For example, type `cd C:\Sample`, and then press ENTER.</span></span>  

3.  <span data-ttu-id="ea6f0-117">在命令提示字元中輸入 `sn -k <key file name>.snk`，然後按下 ENTER。</span><span class="sxs-lookup"><span data-stu-id="ea6f0-117">At the command prompt, type `sn -k <key file name>.snk`, and then press ENTER.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="ea6f0-118">您應該會收到訊息，指出金鑰組已寫入至強式名稱金鑰檔的命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="ea6f0-118">You should receive a message at the command prompt stating that the key pair was written to the strong-name key file.</span></span>  

4.  <span data-ttu-id="ea6f0-119">在命令提示字元中輸入 `exit`，然後按下 ENTER。</span><span class="sxs-lookup"><span data-stu-id="ea6f0-119">At the command prompt, type `exit`, and then press ENTER.</span></span>  

## <a name="learn-the-biztalk-server-tools"></a><span data-ttu-id="ea6f0-120">了解 BizTalk Server 工具</span><span class="sxs-lookup"><span data-stu-id="ea6f0-120">Learn the BizTalk Server tools</span></span>

<span data-ttu-id="ea6f0-121">如何使用主題[!INCLUDE[adapteroracle_short_md](../../includes/adapteroracle-short-md.md)]中[開發與 Oracle 資料庫的 BizTalk 應用程式的建置組塊](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)都已寫明是假設您有數個實用知識，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]工具。</span><span class="sxs-lookup"><span data-stu-id="ea6f0-121">The topics on how to use the [!INCLUDE[adapteroracle_short_md](../../includes/adapteroracle-short-md.md)] in [Building Blocks to develop BizTalk Applications with Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md) are written with the assumption that you have working knowledge of a number of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] tools.</span></span> <span data-ttu-id="ea6f0-122">您可以使用下列工具來開發 BizTalk 應用程式使用[!INCLUDE[adapteroracle_md](../../includes/adapteroracle-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="ea6f0-122">You use the following tools to develop BizTalk applications using the [!INCLUDE[adapteroracle_md](../../includes/adapteroracle-md.md)]:</span></span>  

- <span data-ttu-id="ea6f0-123">Microsoft [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea6f0-123">Microsoft [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)]</span></span> 

- <span data-ttu-id="ea6f0-124">BizTalk Explorer (BizTalk 總管)</span><span class="sxs-lookup"><span data-stu-id="ea6f0-124">BizTalk Explorer</span></span>  

- <span data-ttu-id="ea6f0-125">協調流程 eesigner</span><span class="sxs-lookup"><span data-stu-id="ea6f0-125">Orchestration eesigner</span></span>  

- <span data-ttu-id="ea6f0-126">管線設計師</span><span class="sxs-lookup"><span data-stu-id="ea6f0-126">Pipeline designer</span></span>  

- <span data-ttu-id="ea6f0-127">BizTalk 對應工具</span><span class="sxs-lookup"><span data-stu-id="ea6f0-127">BizTalk mapper</span></span>  

- <span data-ttu-id="ea6f0-128">BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="ea6f0-128">BizTalk Server Administration console</span></span>  

### <a name="prerequisites"></a><span data-ttu-id="ea6f0-129">必要條件</span><span class="sxs-lookup"><span data-stu-id="ea6f0-129">Prerequisites</span></span>  
 <span data-ttu-id="ea6f0-130">您必須先安裝 Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]才能存取[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]工具。</span><span class="sxs-lookup"><span data-stu-id="ea6f0-130">You must install Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] before you can access the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] tools.</span></span>  

### <a name="biztalk-server-tools"></a><span data-ttu-id="ea6f0-131">BizTalk Server 工具</span><span class="sxs-lookup"><span data-stu-id="ea6f0-131">BizTalk Server Tools</span></span>  
 <span data-ttu-id="ea6f0-132">下表包含主題[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]文件說明如何使用每個列出的工具。</span><span class="sxs-lookup"><span data-stu-id="ea6f0-132">The following table includes topics in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] documentation that explain how to use each of the listed tools.</span></span>  


|                                   <span data-ttu-id="ea6f0-133">工具</span><span class="sxs-lookup"><span data-stu-id="ea6f0-133">Tool</span></span>                                    |                                                                                                                                                                                              <span data-ttu-id="ea6f0-134">中的主題[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]核心文件集</span><span class="sxs-lookup"><span data-stu-id="ea6f0-134">Topics in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] core documentation</span></span>                                                                                                                                                                                               |
|---------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] | <span data-ttu-id="ea6f0-135">-   [使用 Visual Studio](../../core/using-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="ea6f0-135">-   [Using Visual Studio](../../core/using-visual-studio.md)</span></span> <br /><span data-ttu-id="ea6f0-136">-   [使用 BizTalk 專案](../../core/working-with-biztalk-projects.md)</span><span class="sxs-lookup"><span data-stu-id="ea6f0-136">-   [Working with BizTalk Projects](../../core/working-with-biztalk-projects.md)</span></span><br /><span data-ttu-id="ea6f0-137">-   [部署 BizTalk 組件從 Visual Studio 到 BizTalk 應用程式](../../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)</span><span class="sxs-lookup"><span data-stu-id="ea6f0-137">-   [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)</span></span><br /><br /> <span data-ttu-id="ea6f0-138">深入了解 Visual Studio 方案、 專案和項目會在[Visual Studio 中方案和專案](https://msdn.microsoft.com/library/b142f8e7.aspx)。</span><span class="sxs-lookup"><span data-stu-id="ea6f0-138">Learn more about Visual Studio solutions, projects, and items at [Solutions and Projects in Visual Studio](https://msdn.microsoft.com/library/b142f8e7.aspx).</span></span> |
|                          <span data-ttu-id="ea6f0-139">協調流程設計師</span><span class="sxs-lookup"><span data-stu-id="ea6f0-139">Orchestration Designer</span></span>                           |                                                                                                                                                                                          [<span data-ttu-id="ea6f0-140">使用協調流程設計師建立協調流程</span><span class="sxs-lookup"><span data-stu-id="ea6f0-140">Creating orchestrations using orchestration designer</span></span>](../../core/creating-orchestrations-using-orchestration-designer.md)                                                                                                                                                                                           |
|                             <span data-ttu-id="ea6f0-141">管線設計師</span><span class="sxs-lookup"><span data-stu-id="ea6f0-141">Pipeline Designer</span></span>                             |                                                                                                                                                                                                    [<span data-ttu-id="ea6f0-142">使用管線設計師建立管線</span><span class="sxs-lookup"><span data-stu-id="ea6f0-142">Creating pipelines using pipeline designer</span></span>](../../core/creating-pipelines-using-pipeline-designer.md)                                                                                                                                                                                                     |
|                              <span data-ttu-id="ea6f0-143">BizTalk Mapper (BizTalk 對應工具)</span><span class="sxs-lookup"><span data-stu-id="ea6f0-143">BizTalk Mapper</span></span>                               |                                                                                                                                                                                                            [<span data-ttu-id="ea6f0-144">使用 BizTalk 對應工具建立對應</span><span class="sxs-lookup"><span data-stu-id="ea6f0-144">Creating maps using BizTalk mapper</span></span>](../../core/creating-maps-using-biztalk-mapper.md)                                                                                                                                                                                                             |
|                   <span data-ttu-id="ea6f0-145">BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="ea6f0-145">BizTalk Server Administration console</span></span>                   |                                                                                                                                                                                               [<span data-ttu-id="ea6f0-146">使用 BizTalk Server 管理主控台</span><span class="sxs-lookup"><span data-stu-id="ea6f0-146">Using the BizTalk Server Administration console</span></span>](../../core/using-the-biztalk-server-administration-console.md)                                                                                                                                                                                                |

## <a name="next"></a><span data-ttu-id="ea6f0-147">下一個</span><span class="sxs-lookup"><span data-stu-id="ea6f0-147">Next</span></span>
[<span data-ttu-id="ea6f0-148">若要開發與 Oracle 資料庫的 BizTalk 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="ea6f0-148">Building Blocks to develop BizTalk Applications with Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)