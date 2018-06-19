---
title: 如何建置協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- building, orchestrations
- building, solutions
- building, projects
- solutions, building
- projects, building
- orchestrations, building
ms.assetid: f12d5da0-fbae-4f0e-85bf-1ca2e9bf7d62
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79e91ec6ecfa061aa4621effba9a1f868cad5d96
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22248142"
---
# <a name="how-to-build-orchestrations"></a><span data-ttu-id="6fb97-102">如何建置協調流程</span><span class="sxs-lookup"><span data-stu-id="6fb97-102">How to Build Orchestrations</span></span>
<span data-ttu-id="6fb97-103">在您完成協調流程繪製後，就可以將 BizTalk 專案建置到封裝可執行協調流程的組件中。</span><span class="sxs-lookup"><span data-stu-id="6fb97-103">After you have completed an orchestration drawing, you build your BizTalk project into an assembly that encapsulates an executable orchestration.</span></span>  
  
 <span data-ttu-id="6fb97-104">在建置程序期間，BizTalk 協調流程設計師會檢視每個圖形以判斷它是否完整且正確，若不是，則在工作清單中報告錯誤。</span><span class="sxs-lookup"><span data-stu-id="6fb97-104">During the build process, BizTalk Orchestration Designer examines each shape to determine whether it is complete and correct, and reports an error in the task list if it is not.</span></span>  
  
 <span data-ttu-id="6fb97-105">在 Visual Studio 中建置時有數個選項可使用：</span><span class="sxs-lookup"><span data-stu-id="6fb97-105">You have several options for building in Visual Studio:</span></span>  
  
-   <span data-ttu-id="6fb97-106">您可以建置協調流程所在的整個解決方案。</span><span class="sxs-lookup"><span data-stu-id="6fb97-106">You can build the entire solution in which your orchestration resides.</span></span>  
  
-   <span data-ttu-id="6fb97-107">您可以在解決方案中建置單一專案。</span><span class="sxs-lookup"><span data-stu-id="6fb97-107">You can build a single project within the solution.</span></span>  
  
-   <span data-ttu-id="6fb97-108">您可以在建置專案或解決方案時略過協調流程。</span><span class="sxs-lookup"><span data-stu-id="6fb97-108">You can skip the orchestration when building the project or solution.</span></span>  
  
 <span data-ttu-id="6fb97-109">若您要建置其他元件 (包括其他協調流程)，但不想建置某個特定的協調流程，則您可以在協調流程的 .odx 檔案之檔案屬性中指示不想建置它，如此就會略過它。</span><span class="sxs-lookup"><span data-stu-id="6fb97-109">If you want to build other components, including other orchestrations, but do not want to build a particular orchestration, you can indicate in the file properties for the orchestration's .odx file that you do not want to build it, and it will be skipped.</span></span>  
  
### <a name="to-build-an-orchestration"></a><span data-ttu-id="6fb97-110">建置協調流程</span><span class="sxs-lookup"><span data-stu-id="6fb97-110">To build an orchestration</span></span>  
  
-   <span data-ttu-id="6fb97-111">在建立協調流程之後，您需要先建置包含它的 BizTalk 專案，才能測試或使用協調流程。</span><span class="sxs-lookup"><span data-stu-id="6fb97-111">After creating your orchestration, you need to build the BizTalk project that contains it before you can test or use the orchestration.</span></span> <span data-ttu-id="6fb97-112">您可以建置整個解決方案，或是在解決方案中建置單一專案。</span><span class="sxs-lookup"><span data-stu-id="6fb97-112">You can build the entire solution, or a single project within the solution.</span></span>  
  
### <a name="to-build-a-solution"></a><span data-ttu-id="6fb97-113">建置解決方案</span><span class="sxs-lookup"><span data-stu-id="6fb97-113">To build a solution</span></span>  
  
-   <span data-ttu-id="6fb97-114">在 [方案總管] 中，以滑鼠右鍵按一下方案，然後選取**建置方案**。</span><span class="sxs-lookup"><span data-stu-id="6fb97-114">In Solution Explorer, right-click the solution and select **Build Solution**.</span></span>  
  
### <a name="to-build-a-project"></a><span data-ttu-id="6fb97-115">建置專案</span><span class="sxs-lookup"><span data-stu-id="6fb97-115">To build a project</span></span>  
  
-   <span data-ttu-id="6fb97-116">以滑鼠右鍵按一下專案，然後選取**建置**。</span><span class="sxs-lookup"><span data-stu-id="6fb97-116">Right-click a project and select **Build**.</span></span>  
  
### <a name="to-build-a-project-or-solution-without-compiling-a-particular-orchestration"></a><span data-ttu-id="6fb97-117">建置專案或解決方案，而不編譯特定協調流程</span><span class="sxs-lookup"><span data-stu-id="6fb97-117">To build a project or solution without compiling a particular orchestration</span></span>  
  
-   <span data-ttu-id="6fb97-118">按一下對應的.odx 檔案到協調流程，然後在 [屬性] 視窗中，按一下**建置動作**屬性，並選取**無**。</span><span class="sxs-lookup"><span data-stu-id="6fb97-118">Click the .odx file corresponding to the orchestration, and in the Properties window, click the **Build Action** property and select **None**.</span></span>