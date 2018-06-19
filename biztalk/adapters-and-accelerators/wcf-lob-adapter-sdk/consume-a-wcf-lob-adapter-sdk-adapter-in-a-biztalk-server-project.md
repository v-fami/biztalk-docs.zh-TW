---
title: 使用 WCF LOB 配接器 SDK 配接器在 BizTalk Server 專案 |Microsoft 文件
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
ms.openlocfilehash: 84f81d23b56c2631879f366e6fe502840408a0d7
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
ms.locfileid: "22225718"
---
# <a name="consume-a-wcf-lob-adapter-sdk-adapter-in-a-biztalk-server-project"></a><span data-ttu-id="5d65e-102">使用 WCF LOB 配接器 SDK 配接器在 BizTalk Server 專案</span><span class="sxs-lookup"><span data-stu-id="5d65e-102">Consume a WCF LOB Adapter SDK adapter in a BizTalk Server project</span></span>
<span data-ttu-id="5d65e-103">本主題描述如何使用配接器使用建置[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]從[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5d65e-103">This topic describes how to consume an adapter built using the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] from [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d65e-104">若要使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]，您必須安裝[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]上相同的電腦裝載的工具[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5d65e-104">In order to use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], you must install the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] tools on the same computer hosting [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 
## <a name="use-the-consume-adapter-service-add-in"></a><span data-ttu-id="5d65e-105">使用使用配接器服務增益集</span><span class="sxs-lookup"><span data-stu-id="5d65e-105">Use the Consume Adapter Service Add-in</span></span>  
 
  
1.  <span data-ttu-id="5d65e-106">開啟.NET 應用程式中的[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5d65e-106">Open your .NET application in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="5d65e-107">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，請在**專案** 窗格中，以滑鼠右鍵按一下您[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案，然後再選擇**新增**&#124;**新增產生的項目** &#124; **使用配接器服務**。</span><span class="sxs-lookup"><span data-stu-id="5d65e-107">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], in the **Project** pane, right-click your [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] project, and then choose **Add**&#124;**Add Generated Items** &#124; **Consume Adapter Service**.</span></span>  
  
3.  <span data-ttu-id="5d65e-108">在[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]畫面上，選取配接器繫結。</span><span class="sxs-lookup"><span data-stu-id="5d65e-108">In the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] screen, select an adapter binding.</span></span>  
  
4.  <span data-ttu-id="5d65e-109">按一下**設定**設定選取的配接器繫結的連線 URI，並提供任何認證、 URI 屬性和繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="5d65e-109">Click **Configure** to configure the connection URI for the selected adapter binding and to provide any credentials, URI properties, and binding properties.</span></span> <span data-ttu-id="5d65e-110">實際需求依選取的配接器繫結上。</span><span class="sxs-lookup"><span data-stu-id="5d65e-110">Actual requirements will vary based on the selected adapter binding.</span></span>  
  
5.  <span data-ttu-id="5d65e-111">按一下**確定**URI 的設定時。</span><span class="sxs-lookup"><span data-stu-id="5d65e-111">Click **OK** when you have configured the URI.</span></span>  
  
6.  <span data-ttu-id="5d65e-112">按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="5d65e-112">Click **Connect**.</span></span> <span data-ttu-id="5d65e-113">連線 URI 是否有效且用戶端認證 （如果有的話） 已被接受，**類別**窗格應填入的類別和配接器所提供的作業。</span><span class="sxs-lookup"><span data-stu-id="5d65e-113">If the connection URI is valid and client credentials (if any) are accepted, the **Category** pane should be populated with the categories and operations provided by the adapter.</span></span>  
  
7.  <span data-ttu-id="5d65e-114">如果配接器支援搜尋，[搜尋] 欄位將會啟用。</span><span class="sxs-lookup"><span data-stu-id="5d65e-114">If the adapter support search, the search field will be active.</span></span> <span data-ttu-id="5d65e-115">否則，您可以依合約類型和篩選中的節點，即可瀏覽型別和作業**類別**窗格。</span><span class="sxs-lookup"><span data-stu-id="5d65e-115">Otherwise, you can filter by contract type and explore types and operations by clicking nodes in the **Category** pane.</span></span>  
  
8.  <span data-ttu-id="5d65e-116">按一下**確定**產生 proxy 成品。</span><span class="sxs-lookup"><span data-stu-id="5d65e-116">Click **OK** to generate the proxy artifacts.</span></span> <span data-ttu-id="5d65e-117">成品數目會根據合約型別而異：</span><span class="sxs-lookup"><span data-stu-id="5d65e-117">The number of artifacts varies based on the contract type:</span></span>  
  
    |<span data-ttu-id="5d65e-118">合約型別</span><span class="sxs-lookup"><span data-stu-id="5d65e-118">Contract Type</span></span>|<span data-ttu-id="5d65e-119">成品</span><span class="sxs-lookup"><span data-stu-id="5d65e-119">Artifact</span></span>|<span data-ttu-id="5d65e-120">Description</span><span class="sxs-lookup"><span data-stu-id="5d65e-120">Description</span></span>||  
    |-------------------|--------------|-----------------|-|  
    |<span data-ttu-id="5d65e-121">輸出</span><span class="sxs-lookup"><span data-stu-id="5d65e-121">Outbound</span></span>|<span data-ttu-id="5d65e-122">XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="5d65e-122">XML Schemas</span></span>|<span data-ttu-id="5d65e-123">包含所選的類型和作業的結構描述。</span><span class="sxs-lookup"><span data-stu-id="5d65e-123">Contains the schemas for the selected types and operations.</span></span>||  
    |<span data-ttu-id="5d65e-124">輸出</span><span class="sxs-lookup"><span data-stu-id="5d65e-124">Outbound</span></span>||<span data-ttu-id="5d65e-125">WCF 自訂傳送連接埠繫結資訊的 XML</span><span class="sxs-lookup"><span data-stu-id="5d65e-125">WCF-Custom send port binding information XML</span></span>|<span data-ttu-id="5d65e-126">包含 Wcf-custom 傳送埠組態 XML。</span><span class="sxs-lookup"><span data-stu-id="5d65e-126">Contains configuration XML for the WCF-Custom send port.</span></span>|  
    |<span data-ttu-id="5d65e-127">輸入</span><span class="sxs-lookup"><span data-stu-id="5d65e-127">Inbound</span></span>|<span data-ttu-id="5d65e-128">XML 結構描述</span><span class="sxs-lookup"><span data-stu-id="5d65e-128">XML Schemas</span></span>|<span data-ttu-id="5d65e-129">包含所選的類型和作業的結構描述。</span><span class="sxs-lookup"><span data-stu-id="5d65e-129">Contains the schemas for the selected types and operations.</span></span>||  
    |<span data-ttu-id="5d65e-130">輸入</span><span class="sxs-lookup"><span data-stu-id="5d65e-130">Inbound</span></span>||<span data-ttu-id="5d65e-131">WCF 自訂接收連接埠繫結資訊的 XML</span><span class="sxs-lookup"><span data-stu-id="5d65e-131">WCF-Custom receive port binding information XML</span></span>|<span data-ttu-id="5d65e-132">WCF 自訂接收埠，請包含組態 XML。</span><span class="sxs-lookup"><span data-stu-id="5d65e-132">Contains configuration XML for the WCF-Custom receive port.</span></span>|  
  
9. <span data-ttu-id="5d65e-133">您現在可以使用 XML 結構描述檔案，在您[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="5d65e-133">You can now use the XML Schema files in your [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application.</span></span>  
  
## <a name="deploy-the-biztalk-server-project"></a><span data-ttu-id="5d65e-134">部署 BizTalk Server 專案</span><span class="sxs-lookup"><span data-stu-id="5d65e-134">Deploy the BizTalk Server project</span></span>  
  
1.  <span data-ttu-id="5d65e-135">開啟 [BizTalk Server 管理] 。</span><span class="sxs-lookup"><span data-stu-id="5d65e-135">Open **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="5d65e-136">匯入所要建立實體連接埠的連接埠繫結 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="5d65e-136">Import the port binding XML file(s) to create the physical ports.</span></span> <span data-ttu-id="5d65e-137">以滑鼠右鍵按一下待測應用程式**應用程式**群組中，選取**匯入繫結**，然後瀏覽至並選取適當的連接埠繫結資訊 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="5d65e-137">Right-click your application under the **Applications** group, select **Import Bindings**, and then navigate to and select the appropriate port binding information XML file(s).</span></span>  
  
3.  <span data-ttu-id="5d65e-138">對應中所定義的邏輯連接埠您[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]至新建立的實體連接埠的協調流程。</span><span class="sxs-lookup"><span data-stu-id="5d65e-138">Map the logical ports defined in your [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] orchestrations to the newly created physical ports.</span></span>  
  
4.  <span data-ttu-id="5d65e-139">按一下**協調流程**下您的應用程式，以滑鼠右鍵按一下協調流程登錄，然後按一下 **登錄**。</span><span class="sxs-lookup"><span data-stu-id="5d65e-139">Click **Orchestrations** under your application, right-click the orchestration to enlist, and then click **Enlist**.</span></span>  
  
5.  <span data-ttu-id="5d65e-140">按一下**協調流程**下您的應用程式，以滑鼠右鍵按一下協調流程登錄，然後按一下 **啟動**。</span><span class="sxs-lookup"><span data-stu-id="5d65e-140">Click **Orchestrations** under your application, right-click the orchestration to enlist, and then click **Start**.</span></span>  
  
6.  <span data-ttu-id="5d65e-141">以滑鼠右鍵按一下您[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式，，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="5d65e-141">Right-click your [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application, and then click **Start**.</span></span>  
  
## <a name="generate-multiple-schemas"></a><span data-ttu-id="5d65e-142">產生多個結構描述</span><span class="sxs-lookup"><span data-stu-id="5d65e-142">Generate Multiple Schemas</span></span>  
 <span data-ttu-id="5d65e-143">如果您使用 取用配接器服務精靈產生多個結構描述時，一或多個項目可能會導致編譯錯誤的結構描述中重複[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]專案。</span><span class="sxs-lookup"><span data-stu-id="5d65e-143">If you use the Consume Adapter Service Wizard to generate multiple schemas, one or more elements may be duplicated in the schemas resulting in compilation failure for the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] project.</span></span> <span data-ttu-id="5d65e-144">您可以避免這個狀況選取**產生唯一的結構描述型別**核取方塊，以確保與唯一的命名空間會產生結構描述型別。</span><span class="sxs-lookup"><span data-stu-id="5d65e-144">You can avoid this by selecting the **Generate Unique Schema Type** check box to ensure that schema types are generated with unique namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d65e-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d65e-145">See Also</span></span>  
 [<span data-ttu-id="5d65e-146">使用建立使用 WCF LOB Adapter SDK 的配接器</span><span class="sxs-lookup"><span data-stu-id="5d65e-146">Consume an adapter created using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/consume-an-adapter-created-using-the-wcf-lob-adapter-sdk.md)