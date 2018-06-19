---
title: 第 3 課： 加入 SWIFT 的結構描述至專案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- schemas, adding to projects
- projects
ms.assetid: e17ef4b8-f060-44cc-b988-0f9f54deab90
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12fb5741b75fb9792cbabf46bf7a0402972d7bb4
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
ms.locfileid: "25961988"
---
# <a name="lesson-3-adding-swift-schemas-to-a-project"></a><span data-ttu-id="5d3c4-102">第 3 課： 加入 SWIFT 的結構描述至專案</span><span class="sxs-lookup"><span data-stu-id="5d3c4-102">Lesson 3: Adding SWIFT Schemas to a Project</span></span>
<span data-ttu-id="5d3c4-103">現在您的方案和新的專案，您可以新增項目至專案。</span><span class="sxs-lookup"><span data-stu-id="5d3c4-103">Now that you have a solution and a new project, you can add items to the project.</span></span> <span data-ttu-id="5d3c4-104">您加入的第一個項目是 MT103 SWIFT 付款訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="5d3c4-104">The first item you add is a schema for an MT103 SWIFT Payment message.</span></span> <span data-ttu-id="5d3c4-105">當您選取的結構描述範本時，BizTalk 編輯器會啟動。</span><span class="sxs-lookup"><span data-stu-id="5d3c4-105">When you select the Schema template, BizTalk Editor starts.</span></span>  
  
### <a name="to-add-a-new-schema-to-the-project"></a><span data-ttu-id="5d3c4-106">新增新結構描述至專案</span><span class="sxs-lookup"><span data-stu-id="5d3c4-106">To add a new schema to the project</span></span>  
  
1.  <span data-ttu-id="5d3c4-107">在 方案總管 中，以滑鼠右鍵按一下**SWIFTSchemas**專案，指向**新增**，然後按一下 **現有項目**。</span><span class="sxs-lookup"><span data-stu-id="5d3c4-107">In Solution Explorer, right-click the **SWIFTSchemas** project, point to **Add**, and then click **Existing Item**.</span></span>  
  
2.  <span data-ttu-id="5d3c4-108">在 [加入現有項目-SWIFTSchemas] 對話方塊中，瀏覽至 **\<*磁碟機*\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\<版本\>MessagePack\SWIFT Messages\A4SWIFT SRG\<版本\>\Base 結構描述**。</span><span class="sxs-lookup"><span data-stu-id="5d3c4-108">In the Add Existing Item-SWIFTSchemas dialog box, browse to **\<*drive*\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT \<version\> MessagePack\SWIFT Messages\A4SWIFT-SRG\<version\>\Base Schemas**.</span></span>  
  
3.  <span data-ttu-id="5d3c4-109">選取**SWIFT 基底 Types.xsd**和**SWIFT 常見資料 Types.xsd**結構描述，然後再按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="5d3c4-109">Select the **SWIFT Base Types.xsd** and the **SWIFT Common Data Types.xsd** schemas, and then click **Add**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5d3c4-110">SWIFT 基底 Types.xsd 和 SWIFT 常見資料 Types.xsd 結構描述會出現在 方案總管 SWIFTSchemas 專案底下。</span><span class="sxs-lookup"><span data-stu-id="5d3c4-110">The SWIFT Base Types.xsd and the SWIFT Common Data Types.xsd schemas appear in Solution Explorer under the SWIFTSchemas project.</span></span>  
  
4.  <span data-ttu-id="5d3c4-111">在 方案總管 中，以滑鼠右鍵按一下**SWIFTSchemas**專案，指向**新增**，然後按一下 **現有項目**。</span><span class="sxs-lookup"><span data-stu-id="5d3c4-111">In Solution Explorer, right-click the **SWIFTSchemas** project, point to **Add**, and then click **Existing Item**.</span></span>  
  
5.  <span data-ttu-id="5d3c4-112">在 [加入現有項目-SWIFTSchemas] 對話方塊中，瀏覽至 **\<*磁碟機*\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\<版本\>MessagePack\SWIFT Messages\A4SWIFT SRG\<版本\>\Category 1\MT103**資料夾。</span><span class="sxs-lookup"><span data-stu-id="5d3c4-112">In the Add Existing Item-SWIFTSchemas dialog box, browse to the **\<*drive*\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT \<version\> MessagePack\SWIFT Messages\A4SWIFT-SRG\<version\>\Category 1\MT103** folder.</span></span>  
  
6.  <span data-ttu-id="5d3c4-113">選取**MT103.xsd**結構描述，然後再按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="5d3c4-113">Select the **MT103.xsd** schema, and then click **Add**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5d3c4-114">新的結構描述 MT103.xsd，會出現在方案總管 中，SWIFTSchemas 專案底下。</span><span class="sxs-lookup"><span data-stu-id="5d3c4-114">The new schema, MT103.xsd, appears in Solution Explorer under the SWIFTSchemas project.</span></span>  
  
7.  <span data-ttu-id="5d3c4-115">在 方案總管 中，按兩下**MT103.xsd** BizTalk 編輯器 中檢視結構描述。</span><span class="sxs-lookup"><span data-stu-id="5d3c4-115">In Solution Explorer, double-click **MT103.xsd** to view the schema in BizTalk Editor.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5d3c4-116">結構描述樹狀結構 （左窗格） 和 XSD 檢視 （右窗格） 會出現在 [BizTalk 編輯器] 中。</span><span class="sxs-lookup"><span data-stu-id="5d3c4-116">The schema tree (left pane) and XSD view (right pane) appear in BizTalk Editor.</span></span>  
  
8.  <span data-ttu-id="5d3c4-117">在**檔案**功能表上，按一下 **全部儲存**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="5d3c4-117">On the **File** menu, click **Save All** to save your changes.</span></span>  
  
 <span data-ttu-id="5d3c4-118">若要繼續[第 4 課： 建立和部署組件](../../adapters-and-accelerators/accelerator-swift/lesson-4-building-and-deploying-the-assembly.md)。</span><span class="sxs-lookup"><span data-stu-id="5d3c4-118">Proceed to [Lesson 4: Building and Deploying the Assembly](../../adapters-and-accelerators/accelerator-swift/lesson-4-building-and-deploying-the-assembly.md).</span></span>