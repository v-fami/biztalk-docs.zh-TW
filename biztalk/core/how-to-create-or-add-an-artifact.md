---
title: "如何建立或新增成品 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, artifacts
- artifacts, creating
- applications, artifacts
ms.assetid: fea7487c-b5fa-457f-8c74-a20ea3a6df85
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b231cdf6a25c4ca316c9620ee789e6e3a715fd6c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-or-add-an-artifact"></a><span data-ttu-id="57aa5-102">如何建立或新增成品</span><span class="sxs-lookup"><span data-stu-id="57aa5-102">How to Create or Add an Artifact</span></span>
<span data-ttu-id="57aa5-103">在建立 BizTalk 應用程式之後，可以從檔案系統新增以檔案為基礎的成品 (例如，BizTalk 組件、.NET 組件、指令碼和憑證)，或從「規則引擎」資料庫新增原則。</span><span class="sxs-lookup"><span data-stu-id="57aa5-103">After you create a BizTalk application, you can add file-based artifacts (for example BizTalk assemblies, .NET assemblies, scripts, and certificates) from the file system or add policies from the Rule Engine database.</span></span> <span data-ttu-id="57aa5-104">也可以在應用程式內建立傳送埠、傳送埠群組、接收位置和接收埠。</span><span class="sxs-lookup"><span data-stu-id="57aa5-104">You can also create send ports, send port groups, receive locations, and receive ports within the application.</span></span> <span data-ttu-id="57aa5-105">建立或新增成品會將成品新增至 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="57aa5-105">Creating or adding artifacts adds them to the BizTalk Management database.</span></span> <span data-ttu-id="57aa5-106">然後您可以部署應用程式和其成品當做單一實體中所述[部署 BizTalk 應用程式](../core/deploying-biztalk-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="57aa5-106">You can then deploy the application and its artifacts as a single entity, as described in [Deploying BizTalk Applications](../core/deploying-biztalk-applications.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57aa5-107">BizTalk 應用程式或群組中的某些類型成品必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="57aa5-107">Certain types of artifacts must be unique in a BizTalk application or group.</span></span> <span data-ttu-id="57aa5-108">如需詳細資訊，請參閱[成品，必須是唯一的應用程式或群組](../core/artifacts-that-must-be-unique-in-an-application-or-group.md)。</span><span class="sxs-lookup"><span data-stu-id="57aa5-108">For more information, see [Artifacts That Must Be Unique in an Application or Group](../core/artifacts-that-must-be-unique-in-an-application-or-group.md).</span></span>  
  
 <span data-ttu-id="57aa5-109">如需新增或建立每種成品類型的程序，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="57aa5-109">For procedures on adding or creating each artifact type, see the following topics:</span></span>  
  
-   [<span data-ttu-id="57aa5-110">如何建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="57aa5-110">How to Create a Send Port</span></span>](../core/how-to-create-a-send-port2.md)  
  
-   [<span data-ttu-id="57aa5-111">如何建立傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="57aa5-111">How to Create a Send Port Group</span></span>](../core/how-to-create-a-send-port-group.md)  
  
-   [<span data-ttu-id="57aa5-112">如何建立接收埠</span><span class="sxs-lookup"><span data-stu-id="57aa5-112">How to Create a Receive Port</span></span>](../core/how-to-create-a-receive-port.md)  
  
-   [<span data-ttu-id="57aa5-113">如何建立接收位置</span><span class="sxs-lookup"><span data-stu-id="57aa5-113">How to Create a Receive Location</span></span>](../core/how-to-create-a-receive-location.md)  
  
-   [<span data-ttu-id="57aa5-114">如何新增原則至應用程式</span><span class="sxs-lookup"><span data-stu-id="57aa5-114">How to Add a Policy to an Application</span></span>](../core/how-to-add-a-policy-to-an-application.md)  
  
-   [<span data-ttu-id="57aa5-115">如何將 BizTalk 組件新增至應用程式</span><span class="sxs-lookup"><span data-stu-id="57aa5-115">How to Add a BizTalk Assembly to an Application</span></span>](../core/how-to-add-a-biztalk-assembly-to-an-application.md)  
  
-   [<span data-ttu-id="57aa5-116">如何新增前置或後置處理指令碼至應用程式</span><span class="sxs-lookup"><span data-stu-id="57aa5-116">How to Add a Pre- or Post-processing Script to an Application</span></span>](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md)  
  
-   [<span data-ttu-id="57aa5-117">如何將檔案新增至應用程式</span><span class="sxs-lookup"><span data-stu-id="57aa5-117">How to Add a File to an Application</span></span>](../core/how-to-add-a-file-to-an-application.md)  
  
-   [<span data-ttu-id="57aa5-118">如何將憑證新增至應用程式</span><span class="sxs-lookup"><span data-stu-id="57aa5-118">How to Add a Certificate to an Application</span></span>](../core/how-to-add-a-certificate-to-an-application.md)  
  
-   [<span data-ttu-id="57aa5-119">如何將 COM 元件新增至應用程式</span><span class="sxs-lookup"><span data-stu-id="57aa5-119">How to Add a COM Component to an Application</span></span>](../core/how-to-add-a-com-component-to-an-application.md)  
  
-   [<span data-ttu-id="57aa5-120">如何將.NET 組件新增至應用程式</span><span class="sxs-lookup"><span data-stu-id="57aa5-120">How to Add a .NET Assembly to an Application</span></span>](../core/how-to-add-a-net-assembly-to-an-application.md)  
  
-   [<span data-ttu-id="57aa5-121">如何將 BAM 成品新增至應用程式</span><span class="sxs-lookup"><span data-stu-id="57aa5-121">How to Add a BAM Artifact to an Application</span></span>](../core/how-to-add-a-bam-artifact-to-an-application.md)  
  
-   [<span data-ttu-id="57aa5-122">如何將繫結檔案新增至應用程式</span><span class="sxs-lookup"><span data-stu-id="57aa5-122">How to Add a Binding File to an Application</span></span>](../core/how-to-add-a-binding-file-to-an-application2.md)  
  
> [!NOTE]
>  <span data-ttu-id="57aa5-123">如果您要加入的成品所在的路徑 (例如，路徑及檔案名稱) 太長，加入成品至應用程式的作業可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="57aa5-123">If the artifact you are adding has a very long path (e.g., the path and file name), the operation to add the artifact to an application may fail.</span></span> <span data-ttu-id="57aa5-124">路徑不得超過 260 個字元。</span><span class="sxs-lookup"><span data-stu-id="57aa5-124">A path can't exceed 260 characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57aa5-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57aa5-125">See Also</span></span>  
 <span data-ttu-id="57aa5-126">[建立和修改 BizTalk 應用程式](../core/creating-and-modifying-biztalk-applications.md) </span><span class="sxs-lookup"><span data-stu-id="57aa5-126">[Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md) </span></span>  
 [<span data-ttu-id="57aa5-127">如何將 64 位元成品新增至應用程式</span><span class="sxs-lookup"><span data-stu-id="57aa5-127">How to Add a 64-Bit Artifact to an Application</span></span>](../core/how-to-add-a-64-bit-artifact-to-an-application.md)