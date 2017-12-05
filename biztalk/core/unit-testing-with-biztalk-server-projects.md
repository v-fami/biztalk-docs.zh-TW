---
title: "使用 BizTalk Server 專案執行單元測試 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2594f29-fc34-4dda-9316-2afd4e0056d7
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da7147f4c2500946fb97c47592a2a4a35d3dcf62
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="unit-testing-with-biztalk-server-projects"></a><span data-ttu-id="5b804-102">使用 BizTalk Server 專案執行單元測試</span><span class="sxs-lookup"><span data-stu-id="5b804-102">Unit Testing with BizTalk Server Projects</span></span>
<span data-ttu-id="5b804-103">BizTalk Server 在引進了單元測試可在啟用的功能**部署**BizTalk 專案的屬性頁。</span><span class="sxs-lookup"><span data-stu-id="5b804-103">BizTalk Server introduced a unit testing feature that can be enabled on the **Deployment** property page of a BizTalk project.</span></span> <span data-ttu-id="5b804-104">下列螢幕擷取畫面顯示存取專案設計工具中，當您以滑鼠右鍵按一下專案，然後按一下此專案設定**屬性**。</span><span class="sxs-lookup"><span data-stu-id="5b804-104">The following screenshot shows this project setting accessed from Project Designer when you right-click a project and click the **Properties**.</span></span>  
  
 <span data-ttu-id="5b804-105">![](../core/media/projectdesignerenableunittesting.gif "ProjectDesignerEnableUnitTesting")</span><span class="sxs-lookup"><span data-stu-id="5b804-105">![](../core/media/projectdesignerenableunittesting.gif "ProjectDesignerEnableUnitTesting")</span></span>  
  
 <span data-ttu-id="5b804-106">**公開啟用單元測試專案屬性的專案設計工具中的 [部署] 索引標籤的螢幕擷取畫面。**</span><span class="sxs-lookup"><span data-stu-id="5b804-106">**Screenshot of the Deployment tab in Project Designer exposing the Enable Unit Testing project property.**</span></span>  
  
 <span data-ttu-id="5b804-107">這項功能可讓您建立結構描述、對應和管線的單元測試。</span><span class="sxs-lookup"><span data-stu-id="5b804-107">This feature allows you to create unit tests for schemas, maps, and pipelines.</span></span> <span data-ttu-id="5b804-108">本節中的主題提供一些使用單元測試功能的方法範例。</span><span class="sxs-lookup"><span data-stu-id="5b804-108">The topics in this section provide some example approaches to using the unit testing feature.</span></span> <span data-ttu-id="5b804-109">啟用此功能並重新建置專案後，就會從下列基底類別衍生成品類別以支援單元測試。</span><span class="sxs-lookup"><span data-stu-id="5b804-109">When this feature is enabled and the project rebuilt, the artifact classes will be derived from the following base classes to support unit testing.</span></span>  
  
|<span data-ttu-id="5b804-110">成品類型</span><span class="sxs-lookup"><span data-stu-id="5b804-110">Artifact type</span></span>|<span data-ttu-id="5b804-111">基底類別</span><span class="sxs-lookup"><span data-stu-id="5b804-111">Base class</span></span>|  
|-------------------|----------------|  
|<span data-ttu-id="5b804-112">結構描述</span><span class="sxs-lookup"><span data-stu-id="5b804-112">Schema</span></span>|<span data-ttu-id="5b804-113">**Microsoft.BizTalk.TestTools.Schema.TestableSchemaBase**</span><span class="sxs-lookup"><span data-stu-id="5b804-113">**Microsoft.BizTalk.TestTools.Schema.TestableSchemaBase**</span></span>|  
|<span data-ttu-id="5b804-114">對應</span><span class="sxs-lookup"><span data-stu-id="5b804-114">Map</span></span>|<span data-ttu-id="5b804-115">**Microsoft.BizTalk.TestTools.Mapper.TestableMapBase**</span><span class="sxs-lookup"><span data-stu-id="5b804-115">**Microsoft.BizTalk.TestTools.Mapper.TestableMapBase**</span></span>|  
|<span data-ttu-id="5b804-116">管線</span><span class="sxs-lookup"><span data-stu-id="5b804-116">Pipeline</span></span>|<span data-ttu-id="5b804-117">**Microsoft.BizTalk.TestTools.Pipeline.TestablePipelineBase**</span><span class="sxs-lookup"><span data-stu-id="5b804-117">**Microsoft.BizTalk.TestTools.Pipeline.TestablePipelineBase**</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="5b804-118">本節內容</span><span class="sxs-lookup"><span data-stu-id="5b804-118">In This Section</span></span>  
  
-   [<span data-ttu-id="5b804-119">使用單元測試的結構描述和對應的功能</span><span class="sxs-lookup"><span data-stu-id="5b804-119">Using the Unit Testing Feature with Schemas and Maps</span></span>](../core/using-the-unit-testing-feature-with-schemas-and-maps.md)  
  
-   [<span data-ttu-id="5b804-120">使用單元測試功能搭配管線</span><span class="sxs-lookup"><span data-stu-id="5b804-120">Using the Unit Testing Feature with Pipelines</span></span>](../core/using-the-unit-testing-feature-with-pipelines.md)  
  
## <a name="related-sections"></a><span data-ttu-id="5b804-121">相關章節</span><span class="sxs-lookup"><span data-stu-id="5b804-121">Related Sections</span></span>  
 [<span data-ttu-id="5b804-122">使用單元測試 (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="5b804-122">Working with Unit Tests (Visual Studio)</span></span>](http://go.microsoft.com/fwlink/?LinkId=128890)