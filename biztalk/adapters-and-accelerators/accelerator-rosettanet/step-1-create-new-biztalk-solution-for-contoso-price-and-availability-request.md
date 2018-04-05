---
title: 步驟 1： 為 Contoso 價格與可用性要求建立新的 BizTalk 解決方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- private process tutorial, creating solutions
ms.assetid: e323ce26-2031-4293-95bd-a3bf02e535a5
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee09981b11be8892eefe8d73d526e5712145c9c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-creating-a-new-biztalk-solution-for-the-contoso-price-and-availability-request"></a><span data-ttu-id="1f0f1-102">步驟 1： 為 Contoso 價格與可用性要求建立新的 BizTalk 解決方案</span><span class="sxs-lookup"><span data-stu-id="1f0f1-102">Step 1: Creating a New BizTalk Solution for the Contoso Price and Availability Request</span></span>
<span data-ttu-id="1f0f1-103">在此步驟中，您會建立[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] Contoso 價格與可用性要求專案的方案。</span><span class="sxs-lookup"><span data-stu-id="1f0f1-103">In this step, you create a [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] solution for the Contoso Price and Availability Request project.</span></span> <span data-ttu-id="1f0f1-104">此專案將包含「3A2 價格與可用性」訊息之要求和回應的結構描述與對應。</span><span class="sxs-lookup"><span data-stu-id="1f0f1-104">This project will contain the schemas and maps for the requests and responses for the 3A2 Price and Availability messages.</span></span>  
  
### <a name="to-create-a-blank-solution"></a><span data-ttu-id="1f0f1-105">建立空白方案</span><span class="sxs-lookup"><span data-stu-id="1f0f1-105">To create a blank solution</span></span>  
  
1.  <span data-ttu-id="1f0f1-106">啟動**Microsoft Visual Studio 2012**。</span><span class="sxs-lookup"><span data-stu-id="1f0f1-106">Start **Microsoft Visual Studio 2012**.</span></span>  
  
2.  <span data-ttu-id="1f0f1-107">在 **[檔案]** 功能表上，指向 **[開新檔案]**，然後按一下 **[專案]**。</span><span class="sxs-lookup"><span data-stu-id="1f0f1-107">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="1f0f1-108">在 [新增專案] 對話方塊中**專案類型**區段中，展開**其他專案類型**，選取**Visual Studio 方案**，然後在**範本**區段中，選取**空白方案**。</span><span class="sxs-lookup"><span data-stu-id="1f0f1-108">In the New Project dialog box, in the **Project Types** section, expand **Other Project Types**, select **Visual Studio Solutions**, and then in the **Templates** section, select **Blank Solution**.</span></span>  
  
4.  <span data-ttu-id="1f0f1-109">在**名稱**方塊中，輸入**Contoso**作為方案名稱，然後按一下**確定**開啟新的方案。</span><span class="sxs-lookup"><span data-stu-id="1f0f1-109">In the **Name** box, type **Contoso** as the solution name, and then click **OK** to open the new solution.</span></span>  
  
### <a name="to-create-the-price-and-availability-project"></a><span data-ttu-id="1f0f1-110">建立價格與可用性專案</span><span class="sxs-lookup"><span data-stu-id="1f0f1-110">To create the Price and Availability project</span></span>  
  
1.  <span data-ttu-id="1f0f1-111">在 Visual Studio 中，在**檔案**功能表上，指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="1f0f1-111">In Visual Studio, on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="1f0f1-112">在 [新增專案] 對話方塊中**專案類型**區段中，選取**BizTalk 專案**，然後在**範本**區段中，選取**空白 BizTalk伺服器專案**。</span><span class="sxs-lookup"><span data-stu-id="1f0f1-112">In the New Project dialog box, in the **Project Types** section, select **BizTalk Projects**, and then in the **Templates** section, select **Empty BizTalk Server Project**.</span></span>  
  
3.  <span data-ttu-id="1f0f1-113">在**名稱**方塊中，輸入**ContosoPriceAndAvailability**做為專案名稱。</span><span class="sxs-lookup"><span data-stu-id="1f0f1-113">In the **Name** box, type **ContosoPriceAndAvailability** as the project name.</span></span> <span data-ttu-id="1f0f1-114">如**方案**，選取**將加入至方案**。</span><span class="sxs-lookup"><span data-stu-id="1f0f1-114">For **Solution**, select **Add to Solution**.</span></span> <span data-ttu-id="1f0f1-115">按一下**確定**開啟新的專案。</span><span class="sxs-lookup"><span data-stu-id="1f0f1-115">Click **OK** to open the new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f0f1-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f0f1-116">See Also</span></span>  
 <span data-ttu-id="1f0f1-117">[步驟 2： 建立 Contoso LOB 應用程式的結構描述的價格與可用性專案中使用 [BizTalk 編輯器]](../../adapters-and-accelerators/accelerator-rosettanet/step-2-create-contoso-lob-application-schema-for-price-and-availability.md)</span><span class="sxs-lookup"><span data-stu-id="1f0f1-117">[Step 2: Creating the Contoso LOB Application Schemas for the Price and Availability Project Using BizTalk Editor](../../adapters-and-accelerators/accelerator-rosettanet/step-2-create-contoso-lob-application-schema-for-price-and-availability.md)</span></span>