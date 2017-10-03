---
title: "步驟 6 （內部部署）： 建立轉換，將訊息從佇列插入結構描述對應 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30a55f1e-32cc-409a-a814-084026f51b35
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02b2be9659714beb4b9a52f4c2a9dd1e5b3ea47f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-6-on-premises-create-a-transform-to-map-the-message-from-the-queue-to-the-insert-schema"></a><span data-ttu-id="3f9b9-102">步驟 6 （內部部署）： 建立轉換，將訊息從佇列插入結構描述對應</span><span class="sxs-lookup"><span data-stu-id="3f9b9-102">Step 6 (On Premises): Create a Transform to Map the Message from the Queue to the Insert Schema</span></span>
<span data-ttu-id="3f9b9-103">接收的訊息[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]來自服務匯流排佇列，都屬於**ECommerceSalesOrder.xsd**結構描述。</span><span class="sxs-lookup"><span data-stu-id="3f9b9-103">The message that is received by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] from the Service Bus Queue will be of the **ECommerceSalesOrder.xsd** schema.</span></span> <span data-ttu-id="3f9b9-104">不過，若要將訊息插入**SalesOrder**資料表中，訊息必須是**插入**中產生的結構描述[步驟 5 （內部部署）： 產生用於插入訊息插入至結構描述SalesOrder 資料表](../core/step-5-generate-the-schema-for-inserting-a-message-into-salesorder-table.md)。</span><span class="sxs-lookup"><span data-stu-id="3f9b9-104">However, to insert a message into the **SalesOrder** table, the message must be of **Insert** schema that you generated in [Step 5 (On Premises): Generate the Schema for Inserting a Message inito SalesOrder Table](../core/step-5-generate-the-schema-for-inserting-a-message-into-salesorder-table.md).</span></span> <span data-ttu-id="3f9b9-105">因此，在本主題中，我們要建立對應，以轉換**ECommerceSalesOrder.xsd**成插入作業結構描述的結構描述。</span><span class="sxs-lookup"><span data-stu-id="3f9b9-105">So, in this topic, we create a map to transform the **ECommerceSalesOrder.xsd** schema into the Insert operation schema.</span></span>  
  
### <a name="to-create-a-map"></a><span data-ttu-id="3f9b9-106">若要建立對應</span><span class="sxs-lookup"><span data-stu-id="3f9b9-106">To create a map</span></span>  
  
1.  <span data-ttu-id="3f9b9-107">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]您已建立，以滑鼠右鍵按一下專案，指向**新增**，然後按一下 **新項目**。</span><span class="sxs-lookup"><span data-stu-id="3f9b9-107">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] you already created, right-click the project, point to **Add**, and then click **New Item**.</span></span> <span data-ttu-id="3f9b9-108">在**新項目**對話方塊中，選取**對應**，輸入對應名稱為`SalesOrder_SQL.btm`，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="3f9b9-108">In the **New Item** dialog box, select **Map**, enter the map name as `SalesOrder_SQL.btm`, and then click **Add**.</span></span>  
  
2.  <span data-ttu-id="3f9b9-109">在對應中，針對來源結構描述中，選取**ECommerceSalesOrder.xsd**。</span><span class="sxs-lookup"><span data-stu-id="3f9b9-109">In the map, for the source schema, select **ECommerceSalesOrder.xsd**.</span></span> <span data-ttu-id="3f9b9-110">針對目的地結構描述中，選取**TableOperations.SalesOrder.xsd (Insert)**結構描述。</span><span class="sxs-lookup"><span data-stu-id="3f9b9-110">For the destination schema, select **TableOperations.SalesOrder.xsd (Insert)** schema.</span></span>  
  
3.  <span data-ttu-id="3f9b9-111">直接對應來源與目的結構描述中的下列節點：</span><span class="sxs-lookup"><span data-stu-id="3f9b9-111">Directly map the following nodes in the source and destination schemas:</span></span>  
  
    |<span data-ttu-id="3f9b9-112">來源結構描述</span><span class="sxs-lookup"><span data-stu-id="3f9b9-112">Source Schema</span></span>|<span data-ttu-id="3f9b9-113">目的結構描述</span><span class="sxs-lookup"><span data-stu-id="3f9b9-113">Destination Schema</span></span>|  
    |-------------------|------------------------|  
    |<span data-ttu-id="3f9b9-114">CompanyCode</span><span class="sxs-lookup"><span data-stu-id="3f9b9-114">CompanyCode</span></span>|<span data-ttu-id="3f9b9-115">CompanyCode</span><span class="sxs-lookup"><span data-stu-id="3f9b9-115">CompanyCode</span></span>|  
    |<span data-ttu-id="3f9b9-116">PartId</span><span class="sxs-lookup"><span data-stu-id="3f9b9-116">PartId</span></span>|<span data-ttu-id="3f9b9-117">PartNum</span><span class="sxs-lookup"><span data-stu-id="3f9b9-117">PartNum</span></span>|  
    |<span data-ttu-id="3f9b9-118">Quantity</span><span class="sxs-lookup"><span data-stu-id="3f9b9-118">Quantity</span></span>|<span data-ttu-id="3f9b9-119">Qty</span><span class="sxs-lookup"><span data-stu-id="3f9b9-119">Qty</span></span>|  
    |<span data-ttu-id="3f9b9-120">AskPrice</span><span class="sxs-lookup"><span data-stu-id="3f9b9-120">AskPrice</span></span>|<span data-ttu-id="3f9b9-121">UnitAskPrice</span><span class="sxs-lookup"><span data-stu-id="3f9b9-121">UnitAskPrice</span></span>|  
    |<span data-ttu-id="3f9b9-122">註解</span><span class="sxs-lookup"><span data-stu-id="3f9b9-122">Comments</span></span>|<span data-ttu-id="3f9b9-123">CustomerComments</span><span class="sxs-lookup"><span data-stu-id="3f9b9-123">CustomerComments</span></span>|  
  
4.  <span data-ttu-id="3f9b9-124">使用**日期和時間**運算質，將值對應至**DateRequested**和**ShipDate**目的結構描述中的項目。</span><span class="sxs-lookup"><span data-stu-id="3f9b9-124">Use the **Date and Time** functoid to map values to the **DateRequested** and **ShipDate** elements in the destination schema.</span></span> <span data-ttu-id="3f9b9-125">這些節點未對應至來源結構描述中的個別節點。</span><span class="sxs-lookup"><span data-stu-id="3f9b9-125">These nodes are not mapped to the respective nodes in the source schema.</span></span> <span data-ttu-id="3f9b9-126">相反地，目前的日期和時間會傳遞給這些節點使用**日期和時間**運算質。</span><span class="sxs-lookup"><span data-stu-id="3f9b9-126">Instead, the current date and time is passed on to these nodes by using the **Date and Time** functoid.</span></span>  
  
    1.  <span data-ttu-id="3f9b9-127">將拖放**日期和時間**運算質從工具箱 拖曳至對應工具介面。</span><span class="sxs-lookup"><span data-stu-id="3f9b9-127">Drag and drop a **Date and Time** functoid from toolbox to the mapper surface.</span></span>  
  
    2.  <span data-ttu-id="3f9b9-128">連接到運算質**DateRequested**目的結構描述中的項目。</span><span class="sxs-lookup"><span data-stu-id="3f9b9-128">Connect the functoid to the **DateRequested** element in the destination schema.</span></span>  
  
    3.  <span data-ttu-id="3f9b9-129">拖放另一個**日期和時間**運算質和其連接至**ShipDate**目的結構描述中的項目。</span><span class="sxs-lookup"><span data-stu-id="3f9b9-129">Drag and drop another **Date and Time** functoid and connect it to the **ShipDate** element in the destination schema.</span></span>  
  
5.  <span data-ttu-id="3f9b9-130">對應來源與目的結構描述使用中的下列節點**字串串連**運算質：</span><span class="sxs-lookup"><span data-stu-id="3f9b9-130">Map the following nodes in the source and destination schemas using a **String Concatenate** functoid:</span></span>  
  
    |<span data-ttu-id="3f9b9-131">來源結構描述</span><span class="sxs-lookup"><span data-stu-id="3f9b9-131">Source Schema</span></span>|<span data-ttu-id="3f9b9-132">目的結構描述</span><span class="sxs-lookup"><span data-stu-id="3f9b9-132">Destination Schema</span></span>|  
    |-------------------|------------------------|  
    |<span data-ttu-id="3f9b9-133">Address\Line1</span><span class="sxs-lookup"><span data-stu-id="3f9b9-133">Address\Line1</span></span>|<span data-ttu-id="3f9b9-134">SellToAddress</span><span class="sxs-lookup"><span data-stu-id="3f9b9-134">SellToAddress</span></span><br /><br /> <span data-ttu-id="3f9b9-135">BillToAddress</span><span class="sxs-lookup"><span data-stu-id="3f9b9-135">BillToAddress</span></span>|  
    |<span data-ttu-id="3f9b9-136">Address\Line2</span><span class="sxs-lookup"><span data-stu-id="3f9b9-136">Address\Line2</span></span>|<span data-ttu-id="3f9b9-137">SellToAddress</span><span class="sxs-lookup"><span data-stu-id="3f9b9-137">SellToAddress</span></span><br /><br /> <span data-ttu-id="3f9b9-138">BillToAddress</span><span class="sxs-lookup"><span data-stu-id="3f9b9-138">BillToAddress</span></span>|  
    |<span data-ttu-id="3f9b9-139">Address\City</span><span class="sxs-lookup"><span data-stu-id="3f9b9-139">Address\City</span></span>|<span data-ttu-id="3f9b9-140">SellToAddress</span><span class="sxs-lookup"><span data-stu-id="3f9b9-140">SellToAddress</span></span><br /><br /> <span data-ttu-id="3f9b9-141">BillToAddress</span><span class="sxs-lookup"><span data-stu-id="3f9b9-141">BillToAddress</span></span>|  
    |<span data-ttu-id="3f9b9-142">Address\State</span><span class="sxs-lookup"><span data-stu-id="3f9b9-142">Address\State</span></span>|<span data-ttu-id="3f9b9-143">SellToAddress</span><span class="sxs-lookup"><span data-stu-id="3f9b9-143">SellToAddress</span></span><br /><br /> <span data-ttu-id="3f9b9-144">BillToAddress</span><span class="sxs-lookup"><span data-stu-id="3f9b9-144">BillToAddress</span></span>|  
    |<span data-ttu-id="3f9b9-145">Address\Country</span><span class="sxs-lookup"><span data-stu-id="3f9b9-145">Address\Country</span></span>|<span data-ttu-id="3f9b9-146">SellToAddress</span><span class="sxs-lookup"><span data-stu-id="3f9b9-146">SellToAddress</span></span><br /><br /> <span data-ttu-id="3f9b9-147">BillToAddress</span><span class="sxs-lookup"><span data-stu-id="3f9b9-147">BillToAddress</span></span>|  
    |<span data-ttu-id="3f9b9-148">Address\ZipCode</span><span class="sxs-lookup"><span data-stu-id="3f9b9-148">Address\ZipCode</span></span>|<span data-ttu-id="3f9b9-149">SellToAddress</span><span class="sxs-lookup"><span data-stu-id="3f9b9-149">SellToAddress</span></span><br /><br /> <span data-ttu-id="3f9b9-150">BillToAddress</span><span class="sxs-lookup"><span data-stu-id="3f9b9-150">BillToAddress</span></span>|  
    |<span data-ttu-id="3f9b9-151">Contact\FirstName</span><span class="sxs-lookup"><span data-stu-id="3f9b9-151">Contact\FirstName</span></span>|<span data-ttu-id="3f9b9-152">PartnerContact</span><span class="sxs-lookup"><span data-stu-id="3f9b9-152">PartnerContact</span></span>|  
    |<span data-ttu-id="3f9b9-153">Contact\LastName</span><span class="sxs-lookup"><span data-stu-id="3f9b9-153">Contact\LastName</span></span>||  
  
     <span data-ttu-id="3f9b9-154">針對各字串串連對應集執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="3f9b9-154">Perform the following steps for each of the string concatenation mapping sets:</span></span>  
  
    1.  <span data-ttu-id="3f9b9-155">將拖放**字串串連**運算質從工具箱 拖曳至對應工具介面。</span><span class="sxs-lookup"><span data-stu-id="3f9b9-155">Drag and drop a **String Concatenate** functoid from toolbox to the mapper surface.</span></span>  
  
    2.  <span data-ttu-id="3f9b9-156">從來源樹狀結構的每個項目加入做為輸入**字串串連**運算質。</span><span class="sxs-lookup"><span data-stu-id="3f9b9-156">Add each element from the source tree as an input to the **String Concatenate** functoid.</span></span>  
  
    3.  <span data-ttu-id="3f9b9-157">拖曳和設定的輸出**字串串連**運算質至目的結構描述中的項目。</span><span class="sxs-lookup"><span data-stu-id="3f9b9-157">Drag and configure the output of the **String Concatenate** functoid to the element in the destination schema.</span></span>  
  
         <span data-ttu-id="3f9b9-158">完整的對應看起來如下：</span><span class="sxs-lookup"><span data-stu-id="3f9b9-158">The completed map resembles the following:</span></span>  
  
         <span data-ttu-id="3f9b9-159">![要轉換結構描述對應](../core/media/bts2010r2-tut1-map.jpg "BTS2010R2_Tut1_Map")</span><span class="sxs-lookup"><span data-stu-id="3f9b9-159">![Map to transform schemas](../core/media/bts2010r2-tut1-map.jpg "BTS2010R2_Tut1_Map")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f9b9-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f9b9-160">See Also</span></span>  
 [<span data-ttu-id="3f9b9-161">教學課程 4： 建立使用 BizTalk Server 2013 的混合式應用程式</span><span class="sxs-lookup"><span data-stu-id="3f9b9-161">Tutorial 4: Creating a Hybrid Application Using BizTalk Server 2013</span></span>](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)