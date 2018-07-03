---
title: 使用 WCF LOB 配接器 SDK 配接器在 BizTalk Server 專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 041f14cc-d00f-450d-b1e9-40a3e423c510
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b75a3fb19f10188c91120ec816e59996e18c644
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998263"
---
# <a name="consume-a-wcf-lob-adapter-sdk-adapter-in-a-biztalk-server-project"></a><span data-ttu-id="33acf-102">使用 WCF LOB 配接器 SDK 配接器在 BizTalk Server 專案</span><span class="sxs-lookup"><span data-stu-id="33acf-102">Consume a WCF LOB Adapter SDK adapter in a BizTalk Server project</span></span>
<span data-ttu-id="33acf-103">本主題描述如何使用配接器使用來建置[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="33acf-103">This topic describes how to consume an adapter built using the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] from [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].</span></span>  

> [!NOTE]
>  <span data-ttu-id="33acf-104">若要使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，您必須安裝[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]工具在相同的電腦裝載[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="33acf-104">In order to use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], you must install the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] tools on the same computer hosting [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  


## <a name="use-the-consume-adapter-service-add-in"></a><span data-ttu-id="33acf-105">使用取用配接器服務增益集</span><span class="sxs-lookup"><span data-stu-id="33acf-105">Use the Consume Adapter Service Add-in</span></span>  


1. <span data-ttu-id="33acf-106">開啟您的.NET 應用程式中[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="33acf-106">Open your .NET application in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  

2. <span data-ttu-id="33acf-107">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，請在**專案**窗格中，以滑鼠右鍵按一下您[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案，，然後選擇**新增**&#124;**新增產生的項目** &#124; **使用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="33acf-107">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], in the **Project** pane, right-click your [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] project, and then choose **Add**&#124;**Add Generated Items** &#124; **Consume Adapter Service**.</span></span>  

3. <span data-ttu-id="33acf-108">在 [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]畫面上，選取的配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="33acf-108">In the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] screen, select an adapter binding.</span></span>  

4. <span data-ttu-id="33acf-109">按一下 **設定**設定選取的配接器繫結的連接 URI，並提供任何認證、 URI 屬性和繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="33acf-109">Click **Configure** to configure the connection URI for the selected adapter binding and to provide any credentials, URI properties, and binding properties.</span></span> <span data-ttu-id="33acf-110">實際需求會依選取的配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="33acf-110">Actual requirements will vary based on the selected adapter binding.</span></span>  

5. <span data-ttu-id="33acf-111">按一下 **確定**當您已設定的 URI。</span><span class="sxs-lookup"><span data-stu-id="33acf-111">Click **OK** when you have configured the URI.</span></span>  

6. <span data-ttu-id="33acf-112">按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="33acf-112">Click **Connect**.</span></span> <span data-ttu-id="33acf-113">連線 URI 是否有效，且接受用戶端認證 （如果有的話），則**分類**窗格應該填入的類別和配接器所提供的作業。</span><span class="sxs-lookup"><span data-stu-id="33acf-113">If the connection URI is valid and client credentials (if any) are accepted, the **Category** pane should be populated with the categories and operations provided by the adapter.</span></span>  

7. <span data-ttu-id="33acf-114">如果配接器支援搜尋，則可使用 [搜尋] 欄位。</span><span class="sxs-lookup"><span data-stu-id="33acf-114">If the adapter support search, the search field will be active.</span></span> <span data-ttu-id="33acf-115">否則您可以在 依合約類型篩選，並探索類型和作業中的節點，即可**分類**窗格。</span><span class="sxs-lookup"><span data-stu-id="33acf-115">Otherwise, you can filter by contract type and explore types and operations by clicking nodes in the **Category** pane.</span></span>  

8. <span data-ttu-id="33acf-116">按一下 **確定**產生 proxy 成品。</span><span class="sxs-lookup"><span data-stu-id="33acf-116">Click **OK** to generate the proxy artifacts.</span></span> <span data-ttu-id="33acf-117">成品數目會根據合約類型而不同：</span><span class="sxs-lookup"><span data-stu-id="33acf-117">The number of artifacts varies based on the contract type:</span></span>  


   | <span data-ttu-id="33acf-118">合約型別</span><span class="sxs-lookup"><span data-stu-id="33acf-118">Contract Type</span></span> |  <span data-ttu-id="33acf-119">成品</span><span class="sxs-lookup"><span data-stu-id="33acf-119">Artifact</span></span>   |                         <span data-ttu-id="33acf-120">描述</span><span class="sxs-lookup"><span data-stu-id="33acf-120">Description</span></span>                         |                                                             |
   |---------------|-------------|-------------------------------------------------------------|-------------------------------------------------------------|
   |   <span data-ttu-id="33acf-121">輸出</span><span class="sxs-lookup"><span data-stu-id="33acf-121">Outbound</span></span>    | <span data-ttu-id="33acf-122">XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="33acf-122">XML Schemas</span></span> | <span data-ttu-id="33acf-123">包含所選的類型和作業的結構描述。</span><span class="sxs-lookup"><span data-stu-id="33acf-123">Contains the schemas for the selected types and operations.</span></span> |                                                             |
   |   <span data-ttu-id="33acf-124">輸出</span><span class="sxs-lookup"><span data-stu-id="33acf-124">Outbound</span></span>    |             |        <span data-ttu-id="33acf-125">WCF 自訂傳送連接埠繫結資訊的 XML</span><span class="sxs-lookup"><span data-stu-id="33acf-125">WCF-Custom send port binding information XML</span></span>         |  <span data-ttu-id="33acf-126">包含針對 Wcf-custom 傳送埠的組態 XML。</span><span class="sxs-lookup"><span data-stu-id="33acf-126">Contains configuration XML for the WCF-Custom send port.</span></span>   |
   |    <span data-ttu-id="33acf-127">輸入</span><span class="sxs-lookup"><span data-stu-id="33acf-127">Inbound</span></span>    | <span data-ttu-id="33acf-128">XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="33acf-128">XML Schemas</span></span> | <span data-ttu-id="33acf-129">包含所選的類型和作業的結構描述。</span><span class="sxs-lookup"><span data-stu-id="33acf-129">Contains the schemas for the selected types and operations.</span></span> |                                                             |
   |    <span data-ttu-id="33acf-130">輸入</span><span class="sxs-lookup"><span data-stu-id="33acf-130">Inbound</span></span>    |             |       <span data-ttu-id="33acf-131">WCF 自訂接收 XML 的連接埠繫結資訊</span><span class="sxs-lookup"><span data-stu-id="33acf-131">WCF-Custom receive port binding information XML</span></span>       | <span data-ttu-id="33acf-132">WCF 自訂接收埠，請包含組態 XML。</span><span class="sxs-lookup"><span data-stu-id="33acf-132">Contains configuration XML for the WCF-Custom receive port.</span></span> |


9. <span data-ttu-id="33acf-133">您現在可以使用 XML 結構描述檔案，在您[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="33acf-133">You can now use the XML Schema files in your [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application.</span></span>  

## <a name="deploy-the-biztalk-server-project"></a><span data-ttu-id="33acf-134">部署 BizTalk Server 專案</span><span class="sxs-lookup"><span data-stu-id="33acf-134">Deploy the BizTalk Server project</span></span>  

1. <span data-ttu-id="33acf-135">開啟 [BizTalk Server 管理] 。</span><span class="sxs-lookup"><span data-stu-id="33acf-135">Open **BizTalk Server Administration**.</span></span>  

2. <span data-ttu-id="33acf-136">匯入所要建立實體連接埠的連接埠繫結 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="33acf-136">Import the port binding XML file(s) to create the physical ports.</span></span> <span data-ttu-id="33acf-137">以滑鼠右鍵按一下待測應用程式**應用程式**群組中，選取**匯入繫結**，然後瀏覽至並選取適當的連接埠繫結資訊 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="33acf-137">Right-click your application under the **Applications** group, select **Import Bindings**, and then navigate to and select the appropriate port binding information XML file(s).</span></span>  

3. <span data-ttu-id="33acf-138">對應中所定義的邏輯連接埠您[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]至新建立的實體連接埠的協調流程。</span><span class="sxs-lookup"><span data-stu-id="33acf-138">Map the logical ports defined in your [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] orchestrations to the newly created physical ports.</span></span>  

4. <span data-ttu-id="33acf-139">按一下 **協調流程**您的應用程式，以滑鼠右鍵按一下協調流程登錄，然後按一下**登錄**。</span><span class="sxs-lookup"><span data-stu-id="33acf-139">Click **Orchestrations** under your application, right-click the orchestration to enlist, and then click **Enlist**.</span></span>  

5. <span data-ttu-id="33acf-140">按一下 **協調流程**您的應用程式，以滑鼠右鍵按一下協調流程登錄，然後按一下**開始**。</span><span class="sxs-lookup"><span data-stu-id="33acf-140">Click **Orchestrations** under your application, right-click the orchestration to enlist, and then click **Start**.</span></span>  

6. <span data-ttu-id="33acf-141">以滑鼠右鍵按一下您[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式，，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="33acf-141">Right-click your [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application, and then click **Start**.</span></span>  

## <a name="generate-multiple-schemas"></a><span data-ttu-id="33acf-142">產生多個結構描述</span><span class="sxs-lookup"><span data-stu-id="33acf-142">Generate Multiple Schemas</span></span>  
 <span data-ttu-id="33acf-143">如果您使用 取用配接器服務精靈來產生多個結構描述時，一或多個項目可能會導致編譯失敗的結構描述中重複[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="33acf-143">If you use the Consume Adapter Service Wizard to generate multiple schemas, one or more elements may be duplicated in the schemas resulting in compilation failure for the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] project.</span></span> <span data-ttu-id="33acf-144">您可以選取來避免這**產生唯一的結構描述型別**核取方塊，以確保結構描述型別會產生具有唯一的命名空間。</span><span class="sxs-lookup"><span data-stu-id="33acf-144">You can avoid this by selecting the **Generate Unique Schema Type** check box to ensure that schema types are generated with unique namespaces.</span></span>  

## <a name="see-also"></a><span data-ttu-id="33acf-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33acf-145">See Also</span></span>  
 [<span data-ttu-id="33acf-146">使用配接器使用 WCF LOB 配接器 SDK 所建立</span><span class="sxs-lookup"><span data-stu-id="33acf-146">Consume an adapter created using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/consume-an-adapter-created-using-the-wcf-lob-adapter-sdk.md)