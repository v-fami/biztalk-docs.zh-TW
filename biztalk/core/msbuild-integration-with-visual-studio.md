---
title: 與 Visual Studio 的 MSBUILD 整合 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aedcabf7-b2cf-482a-9ade-7311e104bff9
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b4a639945881625dd697798080c913ec0e5e3a1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262830"
---
# <a name="msbuild-integration-with-visual-studio"></a><span data-ttu-id="6f5ea-102">與 Visual Studio 的 MSBUILD 整合</span><span class="sxs-lookup"><span data-stu-id="6f5ea-102">MSBUILD Integration with Visual Studio</span></span>
<span data-ttu-id="6f5ea-103">Visual Studio 使用 MSBUILD 專案檔案格式來儲存有關受管理專案 (包含 BizTalk 專案) 的建置資訊。</span><span class="sxs-lookup"><span data-stu-id="6f5ea-103">Visual Studio uses the MSBUILD project file format to store build information about managed projects including BizTalk projects.</span></span> <span data-ttu-id="6f5ea-104">透過 Visual Studio 新增及變更的專案設定會反映在為每個專案產生的 .btproj 檔案中。</span><span class="sxs-lookup"><span data-stu-id="6f5ea-104">Project settings added and changed through Visual Studio are reflected in the .btproj file that is generated for each project.</span></span> <span data-ttu-id="6f5ea-105">Visual Studio 會使用 MSBUILD 的受主控執行個體來建置 BizTalk 專案，這表示可以在 Visual Studio 中或從命令列建置 BizTalk 專案，兩者結果都一樣。</span><span class="sxs-lookup"><span data-stu-id="6f5ea-105">Visual Studio uses a hosted instance of MSBUILD to build BizTalk projects, meaning that a BizTalk project can be built in Visual Studio or from the command line, with identical results.</span></span>  
  
 <span data-ttu-id="6f5ea-106">如需 MSBUILD 的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=193567](http://go.microsoft.com/fwlink/?LinkId=193567)。</span><span class="sxs-lookup"><span data-stu-id="6f5ea-106">For more information on MSBUILD, see [http://go.microsoft.com/fwlink/?LinkId=193567](http://go.microsoft.com/fwlink/?LinkId=193567).</span></span>  
  
 <span data-ttu-id="6f5ea-107">下列程序顯示如何使用 MSBUILD 從命令列建置 BizTalk 專案範例。</span><span class="sxs-lookup"><span data-stu-id="6f5ea-107">The following procedure shows you how to use MSBUILD to build a sample BizTalk project from command line.</span></span>  
  
## <a name="to-build-a-biztalk-project-from-a-command-line"></a><span data-ttu-id="6f5ea-108">若要從命令列建置 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="6f5ea-108">To build a BizTalk project from a command line</span></span>  
  
1.  <span data-ttu-id="6f5ea-109">啟動**Visual Studio 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="6f5ea-109">Start **Visual Studio Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="6f5ea-110">切換至專案目錄，然後執行 MSBUILD 命令以建置 BizTalk 方案。</span><span class="sxs-lookup"><span data-stu-id="6f5ea-110">Switch to the project directory, and run a MSBUILD command to build the BizTalk solution.</span></span>  
  
    ```  
    msbuild unittesttest.sln /p:Configuration=Debug  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="6f5ea-111">方案可以包含 BizTalk 和非 BizTalk 專案，例如 C# 類別庫。</span><span class="sxs-lookup"><span data-stu-id="6f5ea-111">The solution may contain BizTalk and non-BizTalk projects, such as a C# class library.</span></span>