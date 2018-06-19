---
title: 教學課程 3： 裝載在 IIS 中的回應配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3044cdea-e9b2-4cc2-b66e-799da1dfc07e
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74addb5a69e8f17319a7019167eac1415a3a88d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225182"
---
# <a name="tutorial-3-hosting-the-echo-adapter-in-iis"></a><span data-ttu-id="57624-102">教學課程 3： 裝載在 IIS 中的回應配接器</span><span class="sxs-lookup"><span data-stu-id="57624-102">Tutorial 3: Hosting the Echo Adapter in IIS</span></span>
<span data-ttu-id="57624-103">本教學課程提供逐步指示以裝載回應配接器開發[教學課程 1： 開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="57624-103">This tutorial provides step-by-step instructions for hosting the Echo Adapter developed in [Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md).</span></span> <span data-ttu-id="57624-104">更具體來說，步驟將示範如何使用可以裝載在網際網路資訊服務 (IIS) 的介面卡[!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="57624-104">More specifically, the steps show how you can host the adapter in Internet Information Services (IIS) by using the [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)].</span></span> <span data-ttu-id="57624-105">您會也在 SharePoint 中使用商務資料目錄功能來呼叫 EchoGreetings 作業 (IIS） 裝載配接器，並且顯示結果 Web 組件中。</span><span class="sxs-lookup"><span data-stu-id="57624-105">You will also use the Business Data Catalog feature in SharePoint to call the EchoGreetings operation of the IIS-hosted adapter, and then display the results in a Web Part.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="57624-106">回應配接器的測試程式碼，安裝指令碼會在您 BizTalk 安裝檔案包含的`\BizTalk Server\ASDK_x86\Program Files\WCF LOB Adapter SDK\Documents\Samples`或`\BizTalk Server\ASDK_x64\Program Files\WCF LOB Adapter SDK\Documents\Samples`。</span><span class="sxs-lookup"><span data-stu-id="57624-106">The Echo Adapter, test code, and installation script are included with your BizTalk installation files at `\BizTalk Server\ASDK_x86\Program Files\WCF LOB Adapter SDK\Documents\Samples` or `\BizTalk Server\ASDK_x64\Program Files\WCF LOB Adapter SDK\Documents\Samples`.</span></span> 
  
## <a name="in-this-section"></a><span data-ttu-id="57624-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="57624-107">In This Section</span></span>  
  
-   [<span data-ttu-id="57624-108">步驟 1： 建立 Web 專案中使用配接器服務開發精靈</span><span class="sxs-lookup"><span data-stu-id="57624-108">Step 1: Use the Adapter Service Development Wizard to Create the Web Project</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-1-use-the-adapter-service-development-wizard-to-create-the-web-project.md)  
  
-   [<span data-ttu-id="57624-109">步驟 2： 部署 Web 專案</span><span class="sxs-lookup"><span data-stu-id="57624-109">Step 2: Deploy the Web Project</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-deploy-the-web-project.md)  
  
-   [<span data-ttu-id="57624-110">步驟 3： 建立應用程式定義檔</span><span class="sxs-lookup"><span data-stu-id="57624-110">Step 3: Create an Application Definition File</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-3-create-an-application-definition-file.md)  
  
-   [<span data-ttu-id="57624-111">步驟 4： 建立 Sharepoint 應用程式存取配接器</span><span class="sxs-lookup"><span data-stu-id="57624-111">Step 4: Create a Sharepoint Application to Access the Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-create-a-sharepoint-application-to-access-the-adapter.md)  
  
## <a name="see-also"></a><span data-ttu-id="57624-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57624-112">See Also</span></span>  
 <span data-ttu-id="57624-113">[教學課程 1： 在開發回應配接器](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="57624-113">[Tutorial 1: Develop the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md) </span></span>  
  [<span data-ttu-id="57624-114">WCF LOB 配接器 SDK 教學課程</span><span class="sxs-lookup"><span data-stu-id="57624-114">WCF LOB Adapter SDK Tutorials</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorials-to-learn-the-wcf-lob-adapter-sdk.md)