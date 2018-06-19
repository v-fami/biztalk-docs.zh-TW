---
title: 管理管線 |Microsoft 文件
description: 若要啟用追蹤和傳送埠上的管線屬性，或在 BizTalk Server 接收位置的快速連結
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d60b54e0-0a5a-4264-b0e5-96bb187d782b
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0edfbdd97e134abc6f153acf136ff62a979f8b0c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262534"
---
# <a name="managing-pipelines"></a><span data-ttu-id="cad51-103">管理管線</span><span class="sxs-lookup"><span data-stu-id="cad51-103">Managing Pipelines</span></span>

## <a name="overview"></a><span data-ttu-id="cad51-104">概觀</span><span class="sxs-lookup"><span data-stu-id="cad51-104">Overview</span></span>
<span data-ttu-id="cad51-105">本節提供相關指示，說明如何使用 BizTalk Server 管理主控台管理 BizTalk 群組中的管線。</span><span class="sxs-lookup"><span data-stu-id="cad51-105">This section provides instructions on using the BizTalk Server Administration console to manage the pipelines in a BizTalk group.</span></span> <span data-ttu-id="cad51-106">您可以設定事件和訊息追蹤，也可以設定特定傳送埠或接收位置的管線屬性。</span><span class="sxs-lookup"><span data-stu-id="cad51-106">You can configure tracking for events and messages as well as configure pipeline properties for a specific send port or receive location.</span></span>  
  
 <span data-ttu-id="cad51-107">管線會對內送和外寄訊息執行動作，例如將訊息從原生格式轉換成 XML、加密或解密資料、執行屬性升級等等。</span><span class="sxs-lookup"><span data-stu-id="cad51-107">Pipelines perform actions on incoming and outgoing messages, such as transforming them from a native format into XML, encrypting or unencrypting data, performing property promotion, and so on.</span></span>  
  
 <span data-ttu-id="cad51-108">您不能將管線個別新增至應用程式；管線會在下列情況中新增至應用程式：</span><span class="sxs-lookup"><span data-stu-id="cad51-108">You cannot add a pipeline to an application individually; a pipeline is added to an application as follows:</span></span>  
  
-   <span data-ttu-id="cad51-109">當您將加入包含應用程式，管線的 BizTalk 組件中所述[如何將 BizTalk 組件新增至應用程式](../core/how-to-add-a-biztalk-assembly-to-an-application.md)。</span><span class="sxs-lookup"><span data-stu-id="cad51-109">When you add a BizTalk assembly containing a pipeline to the application, as described in [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).</span></span>  
  
-   <span data-ttu-id="cad51-110">當您匯入.msi 檔案包含包含管線的 BizTalk 組件中所述的應用程式[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="cad51-110">When you import an .msi file into an application that includes a BizTalk assembly containing a pipeline, as described in [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md).</span></span>  
  
-   <span data-ttu-id="cad51-111">當開發人員應用程式組件部署到包含從 Visual Studio 中，管線中所述[從到 BizTalk 應用程式的 Visual Studio 部署 BizTalk 組件](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="cad51-111">When a developer deploys into an application an assembly containing a pipeline from Visual Studio, as described in [Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).</span></span>  
  
 <span data-ttu-id="cad51-112">如需管線的背景資訊，請參閱[管線](../core/pipelines.md)。</span><span class="sxs-lookup"><span data-stu-id="cad51-112">For background information about pipelines, see [Pipelines](../core/pipelines.md).</span></span> <span data-ttu-id="cad51-113">如需開發管線的詳細資訊，請參閱[管線使用管線設計師建立](../core/creating-pipelines-using-pipeline-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="cad51-113">For information about developing pipelines, see [Creating Pipelines Using Pipeline Designer](../core/creating-pipelines-using-pipeline-designer.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cad51-114">您可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。</span><span class="sxs-lookup"><span data-stu-id="cad51-114">You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="cad51-115">如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="cad51-115">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="cad51-116">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="cad51-116">Next steps</span></span>
  
-   [<span data-ttu-id="cad51-117">設定管線追蹤</span><span class="sxs-lookup"><span data-stu-id="cad51-117">Configure Tracking for a Pipeline</span></span>](../core/how-to-configure-tracking-for-a-pipeline.md)  
  
-   [<span data-ttu-id="cad51-118">設定傳送埠的每個執行個體管線屬性</span><span class="sxs-lookup"><span data-stu-id="cad51-118">Configure Per-Instance Pipeline Properties for a Send Port</span></span>](../core/how-to-configure-per-instance-pipeline-properties-for-a-send-port.md)  
  
-   [<span data-ttu-id="cad51-119">設定每個執行個體管線屬性的接收位置</span><span class="sxs-lookup"><span data-stu-id="cad51-119">Configure Per-instance Pipeline Properties for a Receive Location</span></span>](../core/how-to-configure-per-instance-pipeline-properties-for-a-receive-location.md)