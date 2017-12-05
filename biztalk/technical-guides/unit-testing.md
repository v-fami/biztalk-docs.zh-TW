---
title: "單元測試 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c40e5b82-dbb2-4767-8286-88e2de4129f3
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d5f792adf73fb1e3791f0dfe6c8c5f60a3bb81e6
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="unit-testing"></a><span data-ttu-id="78ed1-102">單元測試</span><span class="sxs-lookup"><span data-stu-id="78ed1-102">Unit Testing</span></span>
<span data-ttu-id="78ed1-103">BizTalk Server 導入的單元測試功能，可在啟用**部署**BizTalk 專案的屬性頁。</span><span class="sxs-lookup"><span data-stu-id="78ed1-103">BizTalk Server introduces a unit testing feature that can be enabled on the **Deployment** property page of a BizTalk project.</span></span> <span data-ttu-id="78ed1-104">下列螢幕擷取畫面顯示存取專案設計工具中，當您以滑鼠右鍵按一下專案，然後按一下此專案設定**屬性**。</span><span class="sxs-lookup"><span data-stu-id="78ed1-104">The following screenshot shows this project setting accessed from Project Designer when you right-click a project and click **Properties**.</span></span>  
  
 <span data-ttu-id="78ed1-105">![](../core/media/projectdesignerenableunittesting.gif "ProjectDesignerEnableUnitTesting")</span><span class="sxs-lookup"><span data-stu-id="78ed1-105">![](../core/media/projectdesignerenableunittesting.gif "ProjectDesignerEnableUnitTesting")</span></span>  
  
 <span data-ttu-id="78ed1-106">**公開啟用單元測試專案屬性的專案設計工具中的 [部署] 索引標籤的螢幕擷取畫面**</span><span class="sxs-lookup"><span data-stu-id="78ed1-106">**Screenshot of the Deployment tab in Project Designer exposing the Enable Unit Testing project property**</span></span>  
  
 <span data-ttu-id="78ed1-107">這項功能可讓您建立結構描述、對應和管線的單元測試。</span><span class="sxs-lookup"><span data-stu-id="78ed1-107">This feature allows you to create unit tests for schemas, maps, and pipelines.</span></span> <span data-ttu-id="78ed1-108">BizTalk Server 文件中的主題提供使用單元測試功能時，某些方法範例。</span><span class="sxs-lookup"><span data-stu-id="78ed1-108">The topics in the BizTalk Server documentation provide some example approaches to using the unit testing feature.</span></span> <span data-ttu-id="78ed1-109">啟用此功能並重新建置專案後，就會從下列基底類別衍生成品類別以支援單元測試。</span><span class="sxs-lookup"><span data-stu-id="78ed1-109">When this feature is enabled and the project rebuilt, the artifact classes will be derived from the following base classes to support unit testing.</span></span>  
  
|<span data-ttu-id="78ed1-110">成品類型</span><span class="sxs-lookup"><span data-stu-id="78ed1-110">Artifact type</span></span>|<span data-ttu-id="78ed1-111">基底類別</span><span class="sxs-lookup"><span data-stu-id="78ed1-111">Base class</span></span>|  
|-------------------|----------------|  
|<span data-ttu-id="78ed1-112">結構描述</span><span class="sxs-lookup"><span data-stu-id="78ed1-112">Schema</span></span>|<span data-ttu-id="78ed1-113">**Microsoft.BizTalk.TestTools.Schema.TestableSchemaBase**</span><span class="sxs-lookup"><span data-stu-id="78ed1-113">**Microsoft.BizTalk.TestTools.Schema.TestableSchemaBase**</span></span>|  
|<span data-ttu-id="78ed1-114">對應</span><span class="sxs-lookup"><span data-stu-id="78ed1-114">Map</span></span>|<span data-ttu-id="78ed1-115">**Microsoft.BizTalk.TestTools.Mapper.TestableMapBase**</span><span class="sxs-lookup"><span data-stu-id="78ed1-115">**Microsoft.BizTalk.TestTools.Mapper.TestableMapBase**</span></span>|  
|<span data-ttu-id="78ed1-116">管線</span><span class="sxs-lookup"><span data-stu-id="78ed1-116">Pipeline</span></span>|<span data-ttu-id="78ed1-117">**Microsoft.BizTalk.TestTools.Pipeline.TestablePipelineBase**</span><span class="sxs-lookup"><span data-stu-id="78ed1-117">**Microsoft.BizTalk.TestTools.Pipeline.TestablePipelineBase**</span></span>|  
  
 <span data-ttu-id="78ed1-118">如需單元測試所導入的 BizTalk Server 功能的詳細資訊，請參閱 BizTalk Server 說明中的下列主題：</span><span class="sxs-lookup"><span data-stu-id="78ed1-118">For more information about the unit testing feature introduced with BizTalk Server, see the following topics in the BizTalk Server Help:</span></span>  
  
-   <span data-ttu-id="78ed1-119">[使用單元測試的結構描述和對應的功能](http://go.microsoft.com/fwlink/?LinkId=150482)(http://go.microsoft.com/fwlink/?LinkId=150482)。</span><span class="sxs-lookup"><span data-stu-id="78ed1-119">[Using the Unit Testing Feature with Schemas and Maps](http://go.microsoft.com/fwlink/?LinkId=150482) (http://go.microsoft.com/fwlink/?LinkId=150482).</span></span>  
  
-   <span data-ttu-id="78ed1-120">[使用單元測試功能搭配管線](http://go.microsoft.com/fwlink/?LinkId=150483)(http://go.microsoft.com/fwlink/?LinkId=150483)</span><span class="sxs-lookup"><span data-stu-id="78ed1-120">[Using the Unit Testing Feature with Pipelines](http://go.microsoft.com/fwlink/?LinkId=150483) (http://go.microsoft.com/fwlink/?LinkId=150483)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78ed1-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="78ed1-121">See Also</span></span>  
 [<span data-ttu-id="78ed1-122">實作自動化的測試</span><span class="sxs-lookup"><span data-stu-id="78ed1-122">Implementing Automated Testing</span></span>](../technical-guides/implementing-automated-testing.md)