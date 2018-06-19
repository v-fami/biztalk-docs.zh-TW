---
title: ListTypes 命令 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94febe8a-4c1e-4581-a6d1-ef579633e745
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: afe2519fc5507ae0975d050a998faec78f2940a3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262214"
---
# <a name="listtypes-command"></a><span data-ttu-id="c23e7-102">ListTypes 命令</span><span class="sxs-lookup"><span data-stu-id="c23e7-102">ListTypes Command</span></span>
<span data-ttu-id="c23e7-103">列出所有的成品類型，您可以加入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用**AddResource**命令。</span><span class="sxs-lookup"><span data-stu-id="c23e7-103">Lists all of the artifact types that you can add to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] by using the **AddResource** command.</span></span> <span data-ttu-id="c23e7-104">如需有關**AddResource**命令，請參閱[AddResource 命令](../core/addresource-command.md)。</span><span class="sxs-lookup"><span data-stu-id="c23e7-104">For more information about the **AddResource** command, see [AddResource Command](../core/addresource-command.md).</span></span>  
  
 <span data-ttu-id="c23e7-105">受支援成品類型的完整格式名稱如下：</span><span class="sxs-lookup"><span data-stu-id="c23e7-105">The fully qualified names of the supported artifact types are as follows:</span></span>  
  
-   <span data-ttu-id="c23e7-106">.NET 組件：System.BizTalk:Assembly</span><span class="sxs-lookup"><span data-stu-id="c23e7-106">.NET assembly: System.BizTalk:Assembly</span></span>  
  
-   <span data-ttu-id="c23e7-107">BAM 定義：System.BizTalk:Bam</span><span class="sxs-lookup"><span data-stu-id="c23e7-107">BAM definition: System.BizTalk:Bam</span></span>  
  
-   <span data-ttu-id="c23e7-108">BizTalk 組件：System.BizTalk:BizTalkAssembly</span><span class="sxs-lookup"><span data-stu-id="c23e7-108">BizTalk assembly: System.BizTalk:BizTalkAssembly</span></span>  
  
-   <span data-ttu-id="c23e7-109">BizTalk 繫結檔案：System.BizTalk:BizTalkBinding</span><span class="sxs-lookup"><span data-stu-id="c23e7-109">BizTalk binding file: System.BizTalk:BizTalkBinding</span></span>  
  
-   <span data-ttu-id="c23e7-110">安全性憑證：System.BizTalk:Certificate</span><span class="sxs-lookup"><span data-stu-id="c23e7-110">Security certificate: System.BizTalk:Certificate</span></span>  
  
-   <span data-ttu-id="c23e7-111">COM 元件：System.BizTalk:Com</span><span class="sxs-lookup"><span data-stu-id="c23e7-111">COM component: System.BizTalk:Com</span></span>  
  
-   <span data-ttu-id="c23e7-112">臨機操作檔案：System.BizTalk:File</span><span class="sxs-lookup"><span data-stu-id="c23e7-112">Ad hoc file: System.BizTalk:File</span></span>  
  
-   <span data-ttu-id="c23e7-113">後置處理指令碼：System.BizTalk:PostProcessingScript</span><span class="sxs-lookup"><span data-stu-id="c23e7-113">Postprocessing script: System.BizTalk:PostProcessingScript</span></span>  
  
-   <span data-ttu-id="c23e7-114">前置處理指令碼：System.BizTalk:PreProcessingScript</span><span class="sxs-lookup"><span data-stu-id="c23e7-114">Preprocessing script: System.BizTalk:PreProcessingScript</span></span>  
  
-   <span data-ttu-id="c23e7-115">原則或規則：System.BizTalk:Rules</span><span class="sxs-lookup"><span data-stu-id="c23e7-115">Policy or rule: System.BizTalk:Rules</span></span>  
  
-   <span data-ttu-id="c23e7-116">虛擬目錄：System.BizTalk:WebDirectory</span><span class="sxs-lookup"><span data-stu-id="c23e7-116">Virtual directory: System.BizTalk:WebDirectory</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c23e7-117">為避免命名空間衝突，請始終使用完整類型名稱 (例如 System.BizTalk:Assembly)，切勿單僅使用類型名稱 (例如 Assembly)。</span><span class="sxs-lookup"><span data-stu-id="c23e7-117">To avoid namespace conflicts, you should always use the full type name (such as System.BizTalk:Assembly) rather than the type name alone (such as Assembly).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="c23e7-118">使用方式</span><span class="sxs-lookup"><span data-stu-id="c23e7-118">Usage</span></span>  
 <span data-ttu-id="c23e7-119">**BTSTask ListTypes**</span><span class="sxs-lookup"><span data-stu-id="c23e7-119">**BTSTask ListTypes**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c23e7-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c23e7-120">See Also</span></span>  
 [<span data-ttu-id="c23e7-121">BTSTask 命令列參考</span><span class="sxs-lookup"><span data-stu-id="c23e7-121">BTSTask Command-Line Reference</span></span>](../core/btstask-command-line-reference.md)