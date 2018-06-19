---
title: 如何包含和排除結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e9206458-e5d6-48d7-87a6-9471ba60dca7
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8dfa1f610cef6e67f17ca14737c6ca853dd5cd16
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254342"
---
# <a name="how-to-include-and-exclude-schemas"></a><span data-ttu-id="9898f-102">如何包含和排除結構描述</span><span class="sxs-lookup"><span data-stu-id="9898f-102">How to Include and Exclude Schemas</span></span>
<span data-ttu-id="9898f-103">結構描述檔案可存在於 BizTalk 專案資料夾中，但不能包含在該專案中。</span><span class="sxs-lookup"><span data-stu-id="9898f-103">A schema file can exist in a BizTalk project folder and not be included in that project.</span></span> <span data-ttu-id="9898f-104">這類結構描述會排除在專案之外。</span><span class="sxs-lookup"><span data-stu-id="9898f-104">Such a schema is said to be excluded from the project.</span></span> <span data-ttu-id="9898f-105">當您建置 BizTalk 專案時，不會編譯排除的結構描述。</span><span class="sxs-lookup"><span data-stu-id="9898f-105">Excluded schemas are not compiled when you build the BizTalk project.</span></span> <span data-ttu-id="9898f-106">本主題描述在 BizTalk 專案中包含排除的結構描述，以及從 BizTalk 專案排除結構描述所需的步驟。</span><span class="sxs-lookup"><span data-stu-id="9898f-106">This topic describes the steps required to include an excluded schema in a BizTalk project, and to exclude a schema from a BizTalk project.</span></span>  
  
### <a name="to-include-a-schema-in-a-biztalk-project"></a><span data-ttu-id="9898f-107">在 BizTalk 專案中包含結構描述</span><span class="sxs-lookup"><span data-stu-id="9898f-107">To include a schema in a BizTalk project</span></span>  
  
1.  <span data-ttu-id="9898f-108">在 [方案總管] 中，開啟包含要在其專案資料夾中包含的結構描述之 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="9898f-108">In Solution Explorer, open the BizTalk project that contains the schema to be included in its project folder.</span></span>  
  
2.  <span data-ttu-id="9898f-109">如果所有檔案尚未都顯示，在**專案**功能表上，按一下 **顯示所有檔案**。</span><span class="sxs-lookup"><span data-stu-id="9898f-109">If all files are not already showing, on the **Project** menu, click **Show All Files**.</span></span>  
  
3.  <span data-ttu-id="9898f-110">在 方案總管 中，以滑鼠右鍵按一下您想要包含，然後按一下 已排除結構描述**包含在專案**。</span><span class="sxs-lookup"><span data-stu-id="9898f-110">In Solution Explorer, right-click the excluded schema that you want to include, and then click **Include In Project**.</span></span>  
  
     <span data-ttu-id="9898f-111">在 [方案總管] 中先前排除的結構描述圖示會從空的外框變成一般結構描述圖示。</span><span class="sxs-lookup"><span data-stu-id="9898f-111">The icon for the previously excluded schema in Solution Explorer changes from an empty outline to the normal schema icon.</span></span>  
  
4.  <span data-ttu-id="9898f-112">（選擇性） 在**專案**功能表上，按一下 **顯示所有檔案**隱藏專案資料夾中不包含在專案中的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="9898f-112">Optionally, on the **Project** menu, click **Show All Files** to hide all files in the project folder that are not included in the project.</span></span>  
  
### <a name="to-exclude-a-schema-from-a-biztalk-project"></a><span data-ttu-id="9898f-113">從 BizTalk 專案中排除結構描述</span><span class="sxs-lookup"><span data-stu-id="9898f-113">To exclude a schema from a BizTalk project</span></span>  
  
-   <span data-ttu-id="9898f-114">在 方案總管 中，以滑鼠右鍵按一下您想要排除，然後按一下 結構描述**從專案移除**。</span><span class="sxs-lookup"><span data-stu-id="9898f-114">In Solution Explorer, right-click the schema that you want to exclude, and then click **Exclude From Project**.</span></span>  
  
     <span data-ttu-id="9898f-115">結構描述現在已從 BizTalk 專案排除。</span><span class="sxs-lookup"><span data-stu-id="9898f-115">The schema is now excluded from the BizTalk project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9898f-116">當您從專案排除結構描述時，並不會從檔案系統移除結構描述。</span><span class="sxs-lookup"><span data-stu-id="9898f-116">When you exclude a schema from a project, the schema is not removed from the file system.</span></span> <span data-ttu-id="9898f-117">不過，當您建置專案時，不會包含結構描述。</span><span class="sxs-lookup"><span data-stu-id="9898f-117">However, the schema is not included when you build the project.</span></span> <span data-ttu-id="9898f-118">您可以選擇是否要在專案資料夾中顯示排除的檔案，藉由切換**顯示所有檔案**工具在 [方案總管] 視窗的頂端。</span><span class="sxs-lookup"><span data-stu-id="9898f-118">You can choose whether or not to display excluded files in the project folder by toggling the **Show All Files** tool at the top of the Solution Explorer window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9898f-119">若您想要從檔案系統刪除結構描述，並從專案移除結構描述檔案，則您需要刪除該結構描述。</span><span class="sxs-lookup"><span data-stu-id="9898f-119">If you want to delete the schema from the file system as well as removing the schema file from the project, you need to delete the schema.</span></span> <span data-ttu-id="9898f-120">如需有關刪除結構描述的詳細資訊，請參閱[刪除結構描述](../core/how-to-delete-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="9898f-120">For more information about deleting schemas, see [Deleting Schemas](../core/how-to-delete-schemas.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9898f-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9898f-121">See Also</span></span>  
 [<span data-ttu-id="9898f-122">管理專案中的結構描述</span><span class="sxs-lookup"><span data-stu-id="9898f-122">Managing Schemas Within Projects</span></span>](../core/managing-schemas-within-projects.md)