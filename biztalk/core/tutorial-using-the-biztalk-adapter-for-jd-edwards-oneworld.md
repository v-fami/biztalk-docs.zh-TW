---
title: "教學課程： 使用 BizTalk Adapter for JD Edwards OneWorld |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e13a648-7eaf-40c4-a71b-b66999087a69
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab54a0fe0f4a036e0045938951cf44337087853b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-using-the-biztalk-adapter-for-jd-edwards-oneworld"></a><span data-ttu-id="b4b4a-102">教學課程： 使用 BizTalk Adapter for JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="b4b4a-102">Tutorial: Using the BizTalk Adapter for JD Edwards OneWorld</span></span>
<span data-ttu-id="b4b4a-103">下列示範如何使用 BizTalk 內容屬性來控制 J.D.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-103">The following demonstrates using BizTalk Context Properties to control the J.D.</span></span> <span data-ttu-id="b4b4a-104">Edwards OneWorld 工作階段在協調流程中。</span><span class="sxs-lookup"><span data-stu-id="b4b4a-104">Edwards OneWorld session in your orchestration.</span></span> <span data-ttu-id="b4b4a-105">本教學課程假設您有協調流程會傳送 BeginDoc、 EditLine 及 EndDoc 呼叫至傳送埠繫結至 Microsoft BizTalk Adapter for J.D.</span><span class="sxs-lookup"><span data-stu-id="b4b4a-105">The tutorial assumes you have an orchestration that sends BeginDoc, EditLine and EndDoc calls to a send port bound to the Microsoft BizTalk Adapter for J.D.</span></span> <span data-ttu-id="b4b4a-106">Edwards OneWorld。</span><span class="sxs-lookup"><span data-stu-id="b4b4a-106">Edwards OneWorld.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b4b4a-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="b4b4a-107">In This Section</span></span>  
  
-   [<span data-ttu-id="b4b4a-108">步驟 1： 參考結構描述 DLL</span><span class="sxs-lookup"><span data-stu-id="b4b4a-108">Step 1: Reference the Schema DLL</span></span>](../core/step-1-reference-the-schema-dll2.md)  
  
-   [<span data-ttu-id="b4b4a-109">步驟 2： 建立協調流程</span><span class="sxs-lookup"><span data-stu-id="b4b4a-109">Step 2: Create the Orchestration</span></span>](../core/step-2-create-the-orchestration1.md)  
  
-   [<span data-ttu-id="b4b4a-110">步驟 3： 完成及執行專案</span><span class="sxs-lookup"><span data-stu-id="b4b4a-110">Step 3: Complete and Run the Project</span></span>](../core/step-3-complete-and-run-the-project2.md)  
  
-   [<span data-ttu-id="b4b4a-111">步驟 4： 建立範例 XML BeginDoc</span><span class="sxs-lookup"><span data-stu-id="b4b4a-111">Step 4: Create a Sample XML BeginDoc</span></span>](../core/step-4-create-a-sample-xml-begindoc1.md)