---
title: 如何維護詞彙版本 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, vocabularies
- vocabularies, creating
- vocabularies, versioning
- vocabularies, publishing
- versioning, vocabularies
- updating, vocabularies
- vocabularies, updating
ms.assetid: 43593c6f-4590-4940-ac17-4015928e5838
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b3c67d79878c59e3b0dcba6dcd15955f34ad97c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254366"
---
# <a name="how-to-maintain-vocabulary-versions"></a><span data-ttu-id="e88c9-102">如何維護詞彙版本</span><span class="sxs-lookup"><span data-stu-id="e88c9-102">How to Maintain Vocabulary Versions</span></span>
<span data-ttu-id="e88c9-103">當您已新增詞彙定義到詞彙版本時，可以將版本儲存至規則存放區以供進一步開發之用，或是您可以發佈版本以建立定義正確且不變的一組資料繫結詞彙，讓使用者在開發原則時可用以新增至規則。</span><span class="sxs-lookup"><span data-stu-id="e88c9-103">When you have added vocabulary definitions to a version of your vocabulary, you can save the version to the rule store for further development, or you can publish the version to create a well-defined, immutable set of data-bound terms that are available to users to add to rules as they develop their policies.</span></span> <span data-ttu-id="e88c9-104">請注意，現有規則將仍然指向舊版本。</span><span class="sxs-lookup"><span data-stu-id="e88c9-104">Note that fact that existing rules will still point to the old versions.</span></span>  
  
 <span data-ttu-id="e88c9-105">本主題包含下列工作的程序：</span><span class="sxs-lookup"><span data-stu-id="e88c9-105">This topic contains procedures for the following tasks:</span></span>  
  
-   <span data-ttu-id="e88c9-106">儲存詞彙版本</span><span class="sxs-lookup"><span data-stu-id="e88c9-106">To save a vocabulary version</span></span>  
  
-   <span data-ttu-id="e88c9-107">發佈詞彙版本</span><span class="sxs-lookup"><span data-stu-id="e88c9-107">To publish a vocabulary version</span></span>  
  
-   <span data-ttu-id="e88c9-108">建立詞彙更新版本</span><span class="sxs-lookup"><span data-stu-id="e88c9-108">To create an updated version of a vocabulary</span></span>  
  
-   <span data-ttu-id="e88c9-109">建立空的詞彙新版本</span><span class="sxs-lookup"><span data-stu-id="e88c9-109">To create an empty new version of a vocabulary</span></span>  
  
### <a name="to-save-a-vocabulary-version"></a><span data-ttu-id="e88c9-110">儲存詞彙版本</span><span class="sxs-lookup"><span data-stu-id="e88c9-110">To save a vocabulary version</span></span>  
  
-   <span data-ttu-id="e88c9-111">以滑鼠右鍵按一下版本，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="e88c9-111">Right-click the version, and then click **Save**.</span></span>  
  
### <a name="to-publish-a-vocabulary-version"></a><span data-ttu-id="e88c9-112">發佈詞彙版本</span><span class="sxs-lookup"><span data-stu-id="e88c9-112">To publish a vocabulary version</span></span>  
  
-   <span data-ttu-id="e88c9-113">以滑鼠右鍵按一下版本，然後按一下**發行**。</span><span class="sxs-lookup"><span data-stu-id="e88c9-113">Right-click the version, and then click **Publish**.</span></span>  
  
### <a name="to-create-an-updated-version-of-a-vocabulary"></a><span data-ttu-id="e88c9-114">建立詞彙更新版本</span><span class="sxs-lookup"><span data-stu-id="e88c9-114">To create an updated version of a vocabulary</span></span>  
  
1.  <span data-ttu-id="e88c9-115">以滑鼠右鍵按一下現有的版本，然後按一下**複製**。</span><span class="sxs-lookup"><span data-stu-id="e88c9-115">Right-click an existing version, and then click **Copy**.</span></span>  
  
2.  <span data-ttu-id="e88c9-116">以滑鼠右鍵按一下詞彙資料夾，然後**貼上**。</span><span class="sxs-lookup"><span data-stu-id="e88c9-116">Right-click the vocabulary folder, and then click **Paste**.</span></span>  
  
     <span data-ttu-id="e88c9-117">具有與複製版本相同項目的新版本已建立。</span><span class="sxs-lookup"><span data-stu-id="e88c9-117">A new version is created, with the same elements as the copied version.</span></span>  
  
### <a name="to-create-an-empty-new-version-of-a-vocabulary"></a><span data-ttu-id="e88c9-118">建立空的詞彙新版本</span><span class="sxs-lookup"><span data-stu-id="e88c9-118">To create an empty new version of a vocabulary</span></span>  
  
-   <span data-ttu-id="e88c9-119">以滑鼠右鍵按一下詞彙資料夾，然後**新增版本**。</span><span class="sxs-lookup"><span data-stu-id="e88c9-119">Right-click the vocabulary folder, and then click **Add New Version**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e88c9-120">您只能使用已發佈詞彙的詞彙定義。</span><span class="sxs-lookup"><span data-stu-id="e88c9-120">You can only use vocabulary definitions from published vocabularies.</span></span>