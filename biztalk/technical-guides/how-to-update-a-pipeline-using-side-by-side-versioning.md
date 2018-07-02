---
title: 如何更新管線中使用的並存版本控制 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd884a76-71dd-4c90-b4ba-f1cd7f48eb04
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4bf978b64876a91d06acfbe4c5d34278935cfa55
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970887"
---
# <a name="how-to-update-a-pipeline-using-side-by-side-versioning"></a><span data-ttu-id="8ce31-102">如何更新管線中使用的並存版本控制</span><span class="sxs-lookup"><span data-stu-id="8ce31-102">How to Update a Pipeline Using Side-by-Side Versioning</span></span>
<span data-ttu-id="8ce31-103">使用新的管線新增--並存版本控制的簡單方式是選取的新部署的管線版本中的傳送埠或接收位置。</span><span class="sxs-lookup"><span data-stu-id="8ce31-103">The simple way to use a new pipeline added by side-by-side versioning is to select the newly deployed pipeline version in the send port or receive location.</span></span> <span data-ttu-id="8ce31-104">這會取代舊的管線，以新的。</span><span class="sxs-lookup"><span data-stu-id="8ce31-104">This will replace the old pipeline with the new one.</span></span> <span data-ttu-id="8ce31-105">不過，如果您需要針對回溯相容性的則為 true 的並排顯示功能，然後您必須建立新傳送埠和接收位置和繫結至指定的新管線版本。</span><span class="sxs-lookup"><span data-stu-id="8ce31-105">However, if you need true side-by-side functionality for backwards-compatibility, then you must create new send ports and receive locations and bind them to the new pipeline version specified.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8ce31-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="8ce31-106">Prerequisites</span></span>  
 <span data-ttu-id="8ce31-107">若要執行這個主題中的程序，您必須使用「BizTalk Server 系統管理員」群組成員的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="8ce31-107">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span>  
  
### <a name="to-add-a-new-version-of-a-pipeline-component"></a><span data-ttu-id="8ce31-108">若要加入新的管線元件的版本</span><span class="sxs-lookup"><span data-stu-id="8ce31-108">To add a new version of a pipeline component</span></span>  
  
1. <span data-ttu-id="8ce31-109">在 Visual Studio 中建立新管線元件的版本，以及簽署組件。</span><span class="sxs-lookup"><span data-stu-id="8ce31-109">In Visual Studio, create a new version of the pipeline component, and sign the assembly.</span></span>  
  
2. <span data-ttu-id="8ce31-110">將管線元件中的新增**管線元件**資料夾 (\<*安裝資料夾*\>\Pipeline Components)。</span><span class="sxs-lookup"><span data-stu-id="8ce31-110">Add the pipeline component in the **Pipeline Components** folder (\<*installation folder*\>\Pipeline Components).</span></span>  
  
3. <span data-ttu-id="8ce31-111">將管線元件新增至您的管線。</span><span class="sxs-lookup"><span data-stu-id="8ce31-111">Add the pipeline component to your pipeline.</span></span>  
  
4. <span data-ttu-id="8ce31-112">建置管線，或部署您的方案之後, 移除管線元件，從**管線元件**資料夾。</span><span class="sxs-lookup"><span data-stu-id="8ce31-112">After building the pipeline or deploying your solution, remove the pipeline component from the **Pipeline Components** folder.</span></span>  
  
5. <span data-ttu-id="8ce31-113">將管線元件新增至全域組件快取 (GAC) 中。</span><span class="sxs-lookup"><span data-stu-id="8ce31-113">Add the pipeline component to the global assembly cache (GAC).</span></span>  
  
   <span data-ttu-id="8ce31-114">您已完成這些步驟之後，已編譯的管線組件將參考的管線元件的正確版本和 BizTalk Server 所使用的 AppDomain 會發現在 GAC 中，而不是尋找先前的管線元件的新版本管線元件資料夾中的管線元件的版本。</span><span class="sxs-lookup"><span data-stu-id="8ce31-114">After you have completed these steps, the compiled pipeline assembly will refer to the correct version of the pipeline component, and the AppDomain used by BizTalk Server will find the new version of the pipeline component in the GAC, rather than finding the previous version of the pipeline component in the Pipeline Components folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ce31-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ce31-115">See Also</span></span>  
 [<span data-ttu-id="8ce31-116">使用並存版本控制進行更新</span><span class="sxs-lookup"><span data-stu-id="8ce31-116">Updating Using Side-by-Side Versioning</span></span>](../technical-guides/updating-using-side-by-side-versioning.md)