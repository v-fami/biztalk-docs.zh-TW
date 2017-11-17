---
title: "將成品新增至應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9b5e92e-2e55-41d7-9959-f62753bbeb04
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2c08fa95dddad06efb2c51d93df56b757ae4caca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="adding-artifacts-to-an-application"></a><span data-ttu-id="80073-102">將成品新增至應用程式</span><span class="sxs-lookup"><span data-stu-id="80073-102">Adding Artifacts to an Application</span></span>
<span data-ttu-id="80073-103">您可以加入和設定成品，例如傳送和接收埠、 接收位置和協調流程，使用 [管理] 主控台。</span><span class="sxs-lookup"><span data-stu-id="80073-103">You can add and configure artifacts, such as send and receive ports, receive locations, and orchestrations, by using the Administration console.</span></span> <span data-ttu-id="80073-104">您也可以產生繫結檔案，並將它們加入至應用程式中，如果您想要套用不同的繫結的不同的環境，您將匯入到應用程式。</span><span class="sxs-lookup"><span data-stu-id="80073-104">You can also generate binding files and add them to the application if you want to apply different bindings for the different environments that you will import the application into.</span></span>  
  
 <span data-ttu-id="80073-105">您可以加入其他 (通常非 BizTalk Server) 成品，例如指令碼、 憑證和讀我檔案的檔案，以在 [資源] 節點下的應用程式。</span><span class="sxs-lookup"><span data-stu-id="80073-105">You can add additional (typically non-BizTalk Server) artifacts, such as scripts, certificates, and Readme files, to the application under the Resources node.</span></span> <span data-ttu-id="80073-106">若要這樣做，請使用管理主控台或 BTSTask。</span><span class="sxs-lookup"><span data-stu-id="80073-106">To do so, use the Administration console or BTSTask.</span></span>  
  
 <span data-ttu-id="80073-107">如需成品的詳細資訊，請參閱[如何建立或新增成品](http://go.microsoft.com/fwlink/?LinkID=154724)(http://go.microsoft.com/fwlink/?LinkID = 154724)，[管理成品](http://go.microsoft.com/fwlink/?LinkID=154725)(http://go.microsoft.com/fwlink/?LinkID = 154725) 和[繫結檔案和應用程式部署](http://go.microsoft.com/fwlink/?LinkID=154726)(http://go.microsoft.com/fwlink/?LinkID = 154726)。</span><span class="sxs-lookup"><span data-stu-id="80073-107">For more information about artifacts, see [How to Create or Add an Artifact](http://go.microsoft.com/fwlink/?LinkID=154724) (http://go.microsoft.com/fwlink/?LinkID=154724), [Managing Artifacts](http://go.microsoft.com/fwlink/?LinkID=154725) (http://go.microsoft.com/fwlink/?LinkID=154725) and [Binding Files and Application Deployment](http://go.microsoft.com/fwlink/?LinkID=154726) (http://go.microsoft.com/fwlink/?LinkID=154726).</span></span>  
  
## <a name="factoring-artifacts-into-multiple-biztalk-applications"></a><span data-ttu-id="80073-108">成品分解成多個 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="80073-108">Factoring Artifacts into Multiple BizTalk Applications</span></span>  
 <span data-ttu-id="80073-109">在開發過程中，為了方便起見，您可能已經將組件部署到單一應用程式。</span><span class="sxs-lookup"><span data-stu-id="80073-109">During the development process, you may have deployed your assemblies into a single application for convenience.</span></span> <span data-ttu-id="80073-110">您可能會為了各種理由，而想要將成品分解到多個應用程式中，然後再部署到實際執行環境。</span><span class="sxs-lookup"><span data-stu-id="80073-110">For various reasons, you may want to factor the artifacts into multiple applications before they are deployed into production.</span></span>  
  
 <span data-ttu-id="80073-111">在部署之前，您應該執行深入分析的組件的建構。</span><span class="sxs-lookup"><span data-stu-id="80073-111">Before deploying, you should perform an in-depth analysis of the factoring of an assembly.</span></span> <span data-ttu-id="80073-112">判斷是否應該執行任何建構、 完整的建構或最佳的建構。</span><span class="sxs-lookup"><span data-stu-id="80073-112">Determine whether you should perform No factoring, Full factoring, or Optimal factoring.</span></span>  
  
 <span data-ttu-id="80073-113">**沒有建構**</span><span class="sxs-lookup"><span data-stu-id="80073-113">**No Factoring**</span></span>  
  
 <span data-ttu-id="80073-114">所有的 BizTalk 成品是在一個組件。</span><span class="sxs-lookup"><span data-stu-id="80073-114">All BizTalk artifacts are in one assembly.</span></span> <span data-ttu-id="80073-115">這是容易了解和部署，但可提供最大的彈性。</span><span class="sxs-lookup"><span data-stu-id="80073-115">This is the easiest to understand and deploy, but provides the least amount of flexibility.</span></span>  
  
 <span data-ttu-id="80073-116">**完整的建構**</span><span class="sxs-lookup"><span data-stu-id="80073-116">**Full Factoring**</span></span>  
  
 <span data-ttu-id="80073-117">每個 BizTalk 成品是在它自己組件中。</span><span class="sxs-lookup"><span data-stu-id="80073-117">Each BizTalk artifact is in its own assembly.</span></span> <span data-ttu-id="80073-118">這會提供最大的彈性，但最為複雜部署並了解。</span><span class="sxs-lookup"><span data-stu-id="80073-118">This provides the most flexibility, but is the most complex to deploy and understand.</span></span>  
  
 <span data-ttu-id="80073-119">**最佳建構**</span><span class="sxs-lookup"><span data-stu-id="80073-119">**Optimal Factoring**</span></span>  
  
 <span data-ttu-id="80073-120">最佳建構介於無分解和完整的建構基礎 BizTalk 應用程式的深入分析。</span><span class="sxs-lookup"><span data-stu-id="80073-120">Optimal factoring falls between No Factoring and Full Factoring based on in-depth analysis of your BizTalk applications.</span></span> <span data-ttu-id="80073-121">除了版本控制，這可讓您更輕鬆地實作您的 BizTalk 主控件設計。</span><span class="sxs-lookup"><span data-stu-id="80073-121">In addition to versioning, this allows you to more easily implement your BizTalk host design.</span></span> <span data-ttu-id="80073-122">藉由尋找 BizTalk 成品之間的關聯性來達到此目的。</span><span class="sxs-lookup"><span data-stu-id="80073-122">This is achieved by looking for relationships among BizTalk artifacts.</span></span> <span data-ttu-id="80073-123">可能的話，請將一律具有版本設定一起在相同的組件中的成品。</span><span class="sxs-lookup"><span data-stu-id="80073-123">If possible, put artifacts that are always versioned together in the same assembly.</span></span> <span data-ttu-id="80073-124">如果需要之成品的獨立版本設定，然後將它們必須放在不同的組件中。</span><span class="sxs-lookup"><span data-stu-id="80073-124">If independent versioning of the artifacts is required, then they must be put in different assemblies.</span></span> <span data-ttu-id="80073-125">這是您想要達到的分解層級。</span><span class="sxs-lookup"><span data-stu-id="80073-125">This is the level of factoring that you want to achieve.</span></span>