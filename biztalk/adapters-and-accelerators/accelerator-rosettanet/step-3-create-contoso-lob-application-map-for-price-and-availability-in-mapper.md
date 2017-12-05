---
title: "步驟 3： 建立 Contoso LOB 應用程式會將對應為價格與可用性專案使用的 BizTalk 對應工具 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: private process tutorial, creating LOB maps
ms.assetid: a947e0ac-f0cb-4be9-85a8-09daf3675b1a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fef0f6e951798dd2453aa387d8dcde9853968f3a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-3-creating-the-contoso-lob-application-maps-for-the-price-and-availability-project-using-biztalk-mapper"></a><span data-ttu-id="fa51a-102">步驟 3： 建立 Contoso LOB 應用程式對應的價格與可用性專案使用 BizTalk 對應工具</span><span class="sxs-lookup"><span data-stu-id="fa51a-102">Step 3: Creating the Contoso LOB Application Maps for the Price and Availability Project Using BizTalk Mapper</span></span>
<span data-ttu-id="fa51a-103">在此步驟中，您將建立兩種對應，用以定義兩個交易夥伴之間成功交換訊息所需的轉換。</span><span class="sxs-lookup"><span data-stu-id="fa51a-103">In this step, you create two maps that define the transformation required to successfully exchange messages between the two trading partners.</span></span> <span data-ttu-id="fa51a-104">就本實例而言，Contoso ERP 系統已經標準化「價格與可用性」要求的訊息格式。</span><span class="sxs-lookup"><span data-stu-id="fa51a-104">For this scenario, the Contoso ERP system has already standardized on a message format for a Price and Availability request.</span></span> <span data-ttu-id="fa51a-105">這兩種對應會在交易夥伴 Fabrikam 傳來的要求及回應訊息與內部定義的 Contoso 訊息之間建立對應關係。</span><span class="sxs-lookup"><span data-stu-id="fa51a-105">The two maps will map the request and response messages from the trading partner, Fabrikam, to and from those internally defined Contoso messages, respectively.</span></span>  
  
### <a name="to-add-a-reference-for-the-3a2-priceandavailability-request-schema"></a><span data-ttu-id="fa51a-106">為 3A2 PriceAndAvailability 要求結構描述加入參考</span><span class="sxs-lookup"><span data-stu-id="fa51a-106">To add a reference for the 3A2 PriceAndAvailability Request schema</span></span>  
  
1.  <span data-ttu-id="fa51a-107">在 [方案總管] 中，以滑鼠右鍵按一下 [contosopriceandavailability] 專案，然後**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="fa51a-107">In Solution Explorer, right-click the ContosoPriceAndAvailability project, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="fa51a-108">在 [加入參考] 對話方塊中，按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="fa51a-108">In the Add Reference dialog box, click **Browse**.</span></span>  
  
3.  <span data-ttu-id="fa51a-109">移至資料夾*\<磁碟機\>*: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\Bin，然後選取**Microsoft.Solutions.BTARN.Schemas.RNPIPs.dll**組件。</span><span class="sxs-lookup"><span data-stu-id="fa51a-109">Move to the folder *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\Bin, and then select the **Microsoft.Solutions.BTARN.Schemas.RNPIPs.dll** assembly.</span></span>  
  
4.  <span data-ttu-id="fa51a-110">按一下**新增**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="fa51a-110">Click **Add**, and then click **OK**.</span></span>  
  
### <a name="to-create-the-3a2-priceandavailability-request-to-contoso-priceandavailability-request-map"></a><span data-ttu-id="fa51a-111">建立從 3A2 PriceAndAvailability 要求到 Contoso PriceAndAvailability 要求的對應</span><span class="sxs-lookup"><span data-stu-id="fa51a-111">To create the 3A2 PriceAndAvailability request to Contoso PriceAndAvailability request map</span></span>  
  
1.  <span data-ttu-id="fa51a-112">在 方案總管 中，以滑鼠右鍵按一下 contosopriceandavailability 專案，指向**新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="fa51a-112">In Solution Explorer, right-click the ContosoPriceAndAvailability project, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="fa51a-113">在 加入新項目-ContosoPriceAndAvailability 對話方塊中，選取 **對應檔**在分類窗格中，然後選取**對應**中**範本**窗格。</span><span class="sxs-lookup"><span data-stu-id="fa51a-113">In the Add New Item - ContosoPriceAndAvailability dialog box, select **Map Files** in the Categories pane, and then select **Map** in the **Templates** pane.</span></span> <span data-ttu-id="fa51a-114">在**名稱**方塊中，輸入**PIP3A2RequestToContosoPriceRequest**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="fa51a-114">In the **Name** box, type **PIP3A2RequestToContosoPriceRequest**, and then click **Add**.</span></span>  
  
### <a name="to-associate-the-schemas-for-the-pip3a2requesttocontosopricerequest-map"></a><span data-ttu-id="fa51a-115">產生 PIP3A2RequestToContosoPriceRequest 對應的結構描述關聯</span><span class="sxs-lookup"><span data-stu-id="fa51a-115">To associate the schemas for the PIP3A2RequestToContosoPriceRequest map</span></span>  
  
1.  <span data-ttu-id="fa51a-116">(已顯示 pip3a2requesttocontosopricerequest.btm)，BizTalk 對應工具中的來源結構描述窗格中，按一下 **開啟來源結構描述**。</span><span class="sxs-lookup"><span data-stu-id="fa51a-116">In BizTalk Mapper (with PIP3A2RequestToContosoPriceRequest.btm displayed), in the Source Schema pane, click **Open Source Schema**.</span></span>  
  
2.  <span data-ttu-id="fa51a-117">在 [BizTalk 型別選擇器] 對話方塊中，依序展開**ContosoPriceAndAvailability**，依序展開**參考**，依序展開**Microsoft.Solutions.BTARN.Schemas.RNPIPs**，然後展開**結構描述。**</span><span class="sxs-lookup"><span data-stu-id="fa51a-117">In the BizTalk Type Picker dialog box, expand **ContosoPriceAndAvailability**, expand **References**, expand **Microsoft.Solutions.BTARN.Schemas.RNPIPs**, and then expand **Schemas.**</span></span>  
  
3.  <span data-ttu-id="fa51a-118">選取**Microsoft.Solutions.BTARN.Schemas.RNPIPs。**</span><span class="sxs-lookup"><span data-stu-id="fa51a-118">Select **Microsoft.Solutions.BTARN.Schemas.RNPIPs.**</span></span>  
  
     <span data-ttu-id="fa51a-119">**_3a2priceandavailabilityquerymessageguideline_v1_3]**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="fa51a-119">**_3A2PriceAndAvailabilityQueryMessageGuideline_v1_3**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="fa51a-120">在 [目的結構描述] 窗格中，按一下**開啟目的結構描述**。</span><span class="sxs-lookup"><span data-stu-id="fa51a-120">In the Destination Schema pane, click **Open Destination Schema**.</span></span>  
  
5.  <span data-ttu-id="fa51a-121">在 [BizTalk 型別選擇器] 對話方塊中，依序展開**ContosoPriceAndAvailability**，然後展開**結構描述**。</span><span class="sxs-lookup"><span data-stu-id="fa51a-121">In the BizTalk Type Picker dialog box, expand **ContosoPriceAndAvailability**, and then expand **Schemas**.</span></span>  
  
6.  <span data-ttu-id="fa51a-122">選取**ContosoPriceAndAvailability.ContosoPriceSchema**結構描述，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="fa51a-122">Select the **ContosoPriceAndAvailability.ContosoPriceSchema** schema, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="fa51a-123">在根節點目標結構描述 對話方塊中，選取**rootPriceRequest**結構描述，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="fa51a-123">In the Root Node for Target Schema dialog box, select the **rootPriceRequest** schema, and then click **OK**.</span></span>  
  
### <a name="to-link-schema-fields-in-the-pip3a2requesttocontosopricerequest-map"></a><span data-ttu-id="fa51a-124">連結 PIP3A2RequestToContosoPriceRequest 對應中的結構描述欄位</span><span class="sxs-lookup"><span data-stu-id="fa51a-124">To link schema fields in the PIP3A2RequestToContosoPriceRequest map</span></span>  
  
1.  <span data-ttu-id="fa51a-125">在目的結構描述窗格中，以滑鼠右鍵按一下**\<結構描述\>**節點，然後再按一下**展開樹狀結構節點**。</span><span class="sxs-lookup"><span data-stu-id="fa51a-125">In the Destination Schema pane, right-click the **\<Schema\>** node, and then click **Expand Tree Node**.</span></span>  
  
2.  <span data-ttu-id="fa51a-126">在來源結構描述窗格中，以滑鼠右鍵按一下**\<結構描述\>**節點，然後再按一下**展開樹狀結構節點**。</span><span class="sxs-lookup"><span data-stu-id="fa51a-126">In the Source Schema pane, right-click the **\<Schema\>** node, and then click **Expand Tree Node**.</span></span>  
  
3.  <span data-ttu-id="fa51a-127">拖曳**GlobalProductIdentifier**欄位設為**ProductID**在目的結構描述 窗格中的欄位。</span><span class="sxs-lookup"><span data-stu-id="fa51a-127">Drag the **GlobalProductIdentifier** field to the **ProductID** field in the Destination Schema pane.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fa51a-128">您可以找到**GlobalProductIdentifier**欄位中的節點 Pip3A2PriceAndAvailabilityQuery/ProductPriceAndAvailabilityQuery /</span><span class="sxs-lookup"><span data-stu-id="fa51a-128">You can find the **GlobalProductIdentifier** field in the node Pip3A2PriceAndAvailabilityQuery/ProductPriceAndAvailabilityQuery/</span></span>  
    >   
    >  <span data-ttu-id="fa51a-129">欄位</span><span class="sxs-lookup"><span data-stu-id="fa51a-129">ProductPriceAndAvailability/ProductLineItem/productUnit/</span></span>  
    >   
    >  <span data-ttu-id="fa51a-130">。</span><span class="sxs-lookup"><span data-stu-id="fa51a-130">ProductPackageDescription/ProductIdentification.</span></span>  
  
4.  <span data-ttu-id="fa51a-131">在**檔案**功能表上，按一下 **全部儲存**以儲存變更。</span><span class="sxs-lookup"><span data-stu-id="fa51a-131">On the **File** menu, click **Save All** to save your changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa51a-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="fa51a-132">See Also</span></span>  
 [<span data-ttu-id="fa51a-133">建立與設定 BizTalk 連接埠以供 Contoso 使用</span><span class="sxs-lookup"><span data-stu-id="fa51a-133">Creating and Configuring BizTalk Ports for Contoso</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-and-configuring-biztalk-ports-for-contoso.md)