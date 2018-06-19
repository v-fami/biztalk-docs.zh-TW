---
title: AddResource 命令 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b09bd8d-5e07-4443-b626-60401a158540
caps.latest.revision: 33
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 875a087fa3afe7515aee2c406cbc47551bea1f4d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25964444"
---
# <a name="addresource-command"></a><span data-ttu-id="a23b4-102">AddResource 命令</span><span class="sxs-lookup"><span data-stu-id="a23b4-102">AddResource Command</span></span>
<span data-ttu-id="a23b4-103">本節主題提供 AddResource 命令相關參數的參考資訊。</span><span class="sxs-lookup"><span data-stu-id="a23b4-103">The topics in this section provide reference information about the parameters of the AddResource command.</span></span> <span data-ttu-id="a23b4-104">這個命令使用的參數會根據您想要加入的成品類型而有所不同。</span><span class="sxs-lookup"><span data-stu-id="a23b4-104">The parameters that you use with this command vary according to the type of artifact that you want to add.</span></span> <span data-ttu-id="a23b4-105">若要取得成品類型的完整清單，請使用**ListTypes**命令中所述[ListTypes 命令](../core/listtypes-command.md)。</span><span class="sxs-lookup"><span data-stu-id="a23b4-105">To obtain complete lists of artifact types, use the **ListTypes** command, as described in [ListTypes Command](../core/listtypes-command.md).</span></span>  
  
 <span data-ttu-id="a23b4-106">如需有關加入特定成品類型的輔助說明，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="a23b4-106">To get help for adding a particular artifact type, type the following command:</span></span>  
  
 <span data-ttu-id="a23b4-107">**BTSTask AddResource/類型：**\<*型別名稱*\> **/？**</span><span class="sxs-lookup"><span data-stu-id="a23b4-107">**BTSTask AddResource /Type:**\<*type name*\> **/?**</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a23b4-108">如果您要加入的成品所在的路徑名稱 (包含檔案名稱) 太長，加入成品至應用程式的作業可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="a23b4-108">If the artifact you are adding has a very long path name, including the file name, the operation to add the artifact to an application may fail.</span></span> <span data-ttu-id="a23b4-109">路徑不得超過 260 個字元。</span><span class="sxs-lookup"><span data-stu-id="a23b4-109">A path cannot exceed 260 characters.</span></span>  
>   
>  <span data-ttu-id="a23b4-110">加入作業一旦失敗，則作業期間採取的所有動作都將回復，只會保留此命令已加入至全域組件快取中的組件，以及在 Windows 登錄中增修的項目。</span><span class="sxs-lookup"><span data-stu-id="a23b4-110">If an add operation fails, all actions taken during the operation are rolled back, except that assemblies are not removed from the global assembly cache if they were added by this command, and entries are not removed from the Windows registry if any entries were made.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a23b4-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="a23b4-111">In This Section</span></span>  
  
-   [<span data-ttu-id="a23b4-112">AddResource 命令：BizTalk 組件</span><span class="sxs-lookup"><span data-stu-id="a23b4-112">AddResource Command: BizTalk Assembly</span></span>](../core/addresource-command-biztalk-assembly.md)  
  
-   [<span data-ttu-id="a23b4-113">AddResource 命令：BizTalk 繫結</span><span class="sxs-lookup"><span data-stu-id="a23b4-113">AddResource Command: BizTalk Binding</span></span>](../core/addresource-command-biztalk-binding.md)  
  
-   [<span data-ttu-id="a23b4-114">AddResource 命令：.NET 組件</span><span class="sxs-lookup"><span data-stu-id="a23b4-114">AddResource Command: .NET Assembly</span></span>](../core/addresource-command-net-assembly.md)  
  
-   [<span data-ttu-id="a23b4-115">AddResource 命令：BAM 成品</span><span class="sxs-lookup"><span data-stu-id="a23b4-115">AddResource Command: BAM Artifact</span></span>](../core/addresource-command-bam-artifact.md)  
  
-   [<span data-ttu-id="a23b4-116">AddResource 命令：憑證</span><span class="sxs-lookup"><span data-stu-id="a23b4-116">AddResource Command: Certificate</span></span>](../core/addresource-command-certificate.md)  
  
-   [<span data-ttu-id="a23b4-117">AddResource 命令：COM 元件</span><span class="sxs-lookup"><span data-stu-id="a23b4-117">AddResource Command: COM Component</span></span>](../core/addresource-command-com-component.md)  
  
-   [<span data-ttu-id="a23b4-118">AddResource 命令：檔案</span><span class="sxs-lookup"><span data-stu-id="a23b4-118">AddResource Command: File</span></span>](../core/addresource-command-file.md)  
  
-   [<span data-ttu-id="a23b4-119">AddResource 命令：前置處理指令碼</span><span class="sxs-lookup"><span data-stu-id="a23b4-119">AddResource Command: Preprocessing Script</span></span>](../core/addresource-command-preprocessing-script.md)  
  
-   [<span data-ttu-id="a23b4-120">AddResource 命令：後置處理指令碼</span><span class="sxs-lookup"><span data-stu-id="a23b4-120">AddResource Command: Postprocessing Script</span></span>](../core/addresource-command-postprocessing-script.md)  
  
-   [<span data-ttu-id="a23b4-121">AddResource 命令：原則</span><span class="sxs-lookup"><span data-stu-id="a23b4-121">AddResource Command: Policy</span></span>](../core/addresource-command-policy.md)  
  
-   [<span data-ttu-id="a23b4-122">AddResource 命令：虛擬目錄</span><span class="sxs-lookup"><span data-stu-id="a23b4-122">AddResource Command: Virtual Directory</span></span>](../core/addresource-command-virtual-directory.md)