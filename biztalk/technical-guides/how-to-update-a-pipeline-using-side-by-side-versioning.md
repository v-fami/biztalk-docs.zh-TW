---
title: "如何更新管線中使用的並存版本控制 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd884a76-71dd-4c90-b4ba-f1cd7f48eb04
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c4e8803128f2232905229de3b5de49994e039ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-a-pipeline-using-side-by-side-versioning"></a><span data-ttu-id="02b98-102">如何更新管線中使用的並存版本控制</span><span class="sxs-lookup"><span data-stu-id="02b98-102">How to Update a Pipeline Using Side-by-Side Versioning</span></span>
<span data-ttu-id="02b98-103">使用新加入的並存版本控制的管線的簡單方式是選取的新部署的管線版本中的傳送埠或接收位置。</span><span class="sxs-lookup"><span data-stu-id="02b98-103">The simple way to use a new pipeline added by side-by-side versioning is to select the newly deployed pipeline version in the send port or receive location.</span></span> <span data-ttu-id="02b98-104">這將會以新的取代舊的管線。</span><span class="sxs-lookup"><span data-stu-id="02b98-104">This will replace the old pipeline with the new one.</span></span> <span data-ttu-id="02b98-105">不過，如果您需要則為 true 來並行功能的回溯相容性，然後您必須建立新傳送埠和接收位置和繫結至指定的新管線版本。</span><span class="sxs-lookup"><span data-stu-id="02b98-105">However, if you need true side-by-side functionality for backwards-compatibility, then you must create new send ports and receive locations and bind them to the new pipeline version specified.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="02b98-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="02b98-106">Prerequisites</span></span>  
 <span data-ttu-id="02b98-107">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="02b98-107">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span>  
  
### <a name="to-add-a-new-version-of-a-pipeline-component"></a><span data-ttu-id="02b98-108">若要新增管線元件的版本</span><span class="sxs-lookup"><span data-stu-id="02b98-108">To add a new version of a pipeline component</span></span>  
  
1.  <span data-ttu-id="02b98-109">在 Visual Studio 中，建立新版本的管線元件，並簽署組件。</span><span class="sxs-lookup"><span data-stu-id="02b98-109">In Visual Studio, create a new version of the pipeline component, and sign the assembly.</span></span>  
  
2.  <span data-ttu-id="02b98-110">新增管線元件中的**管線元件**資料夾 (\<*安裝資料夾*> \Pipeline Components)。</span><span class="sxs-lookup"><span data-stu-id="02b98-110">Add the pipeline component in the **Pipeline Components** folder (\<*installation folder*>\Pipeline Components).</span></span>  
  
3.  <span data-ttu-id="02b98-111">將管線元件加入至您的管線。</span><span class="sxs-lookup"><span data-stu-id="02b98-111">Add the pipeline component to your pipeline.</span></span>  
  
4.  <span data-ttu-id="02b98-112">建立管線，或部署方案之後, 移除管線元件從**管線元件**資料夾。</span><span class="sxs-lookup"><span data-stu-id="02b98-112">After building the pipeline or deploying your solution, remove the pipeline component from the **Pipeline Components** folder.</span></span>  
  
5.  <span data-ttu-id="02b98-113">將管線元件加入至全域組件快取 (GAC)。</span><span class="sxs-lookup"><span data-stu-id="02b98-113">Add the pipeline component to the global assembly cache (GAC).</span></span>  
  
 <span data-ttu-id="02b98-114">您已經完成這些步驟後，在已編譯的管線組件將參考的管線元件的正確版本所使用的 AppDomain[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]將在 GAC 中，尋找新版本的管線元件，而不是尋找上一個管線元件資料夾中的管線元件的版本。</span><span class="sxs-lookup"><span data-stu-id="02b98-114">After you have completed these steps, the compiled pipeline assembly will refer to the correct version of the pipeline component, and the AppDomain used by [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] will find the new version of the pipeline component in the GAC, rather than finding the previous version of the pipeline component in the Pipeline Components folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02b98-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02b98-115">See Also</span></span>  
 [<span data-ttu-id="02b98-116">更新使用-並存版本控制</span><span class="sxs-lookup"><span data-stu-id="02b98-116">Updating Using Side-by-Side Versioning</span></span>](../technical-guides/updating-using-side-by-side-versioning.md)