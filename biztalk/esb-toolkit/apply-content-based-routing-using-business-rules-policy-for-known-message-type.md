---
title: "如何： 實作內容架構路由使用商務規則原則已知的訊息類型 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 44451c85-929a-4d13-b0dd-53ea600d0859
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b384c63b26f98a866390a001c7d7c2ec6f3f7cb2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-implement-content-based-routing-using-a-business-rules-policy-for-a-known-message-type"></a><span data-ttu-id="42491-102">如何： 實作內容架構路由使用商務規則原則已知的訊息類型</span><span class="sxs-lookup"><span data-stu-id="42491-102">How to: Implement Content-Based Routing Using a Business Rules Policy for a Known Message Type</span></span>
## <a name="goal"></a><span data-ttu-id="42491-103">目標</span><span class="sxs-lookup"><span data-stu-id="42491-103">Goal</span></span>  
 <span data-ttu-id="42491-104">本節示範如何建立動態路由傳送訊息時，基礎行程上已知的訊息類型 （結構描述部署到 Microsoft BizTalk Server 組態資料庫） 的內容，使用商務規則原則。</span><span class="sxs-lookup"><span data-stu-id="42491-104">This section demonstrates how to create an itinerary that dynamically routes a message, based on the content of a known message type (schema deployed to the Microsoft BizTalk Server Configuration database), using a business rules policy.</span></span>  
  
 <span data-ttu-id="42491-105">在此 「 如何 」 主題，您將完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="42491-105">In this How-to topic, you will complete the following steps:</span></span>  
  
-   <span data-ttu-id="42491-106">建立商務規則原則將用來路由訊息的內容。</span><span class="sxs-lookup"><span data-stu-id="42491-106">Create a business rules policy that will be used to route a message based on content.</span></span>  
  
-   <span data-ttu-id="42491-107">建立 BRE 解析程式，以動態方式將訊息路由傳送路線的路由受控滑動。</span><span class="sxs-lookup"><span data-stu-id="42491-107">Create an itinerary routing slip with a BRE resolver to dynamically route a message.</span></span>  
  
-   <span data-ttu-id="42491-108">測試使用路線測試用戶端範例應用程式的路線。</span><span class="sxs-lookup"><span data-stu-id="42491-108">Test the itinerary using the Itinerary Test Client sample application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="42491-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="42491-109">Prerequisites</span></span>  
 <span data-ttu-id="42491-110">在此 「 如何 」 主題中的程序需要完成[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="42491-110">The procedures in this How-to topic require the completion of the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md).</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="42491-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="42491-111">Before You Begin</span></span>  
 <span data-ttu-id="42491-112">在執行本使用說明主題中稍後的步驟之前，請完成下列工作：</span><span class="sxs-lookup"><span data-stu-id="42491-112">Complete the following tasks before you perform the steps later in this How-to topic:</span></span>  
  
-   <span data-ttu-id="42491-113">建立 GlobalBank 西測試訊息。</span><span class="sxs-lookup"><span data-stu-id="42491-113">Create the GlobalBank West test message.</span></span>  
  
-   <span data-ttu-id="42491-114">建立 GlobalBank 東部測試訊息。</span><span class="sxs-lookup"><span data-stu-id="42491-114">Create the GlobalBank East test message.</span></span>  
  
 <span data-ttu-id="42491-115">下列程序說明如何執行每一種。</span><span class="sxs-lookup"><span data-stu-id="42491-115">The following procedures describe how to do each of these.</span></span>  
  
#### <a name="to-create-the-globalbank-west-test-message"></a><span data-ttu-id="42491-116">若要建立 GlobalBank 西測試訊息</span><span class="sxs-lookup"><span data-stu-id="42491-116">To create the GlobalBank West test message</span></span>  
  
1.  <span data-ttu-id="42491-117">在 Windows 檔案總管，瀏覽至 C:\HowTos。</span><span class="sxs-lookup"><span data-stu-id="42491-117">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
2.  <span data-ttu-id="42491-118">建立一份 NAOrderDoc.xml，，然後複製 West.xml。</span><span class="sxs-lookup"><span data-stu-id="42491-118">Create a copy of NAOrderDoc.xml, and then name the copy West.xml.</span></span>  
  
3.  <span data-ttu-id="42491-119">在 [記事本] 開啟 West.xml，並將值**customerName**元素**GlobalBankWest**。</span><span class="sxs-lookup"><span data-stu-id="42491-119">In Notepad, open West.xml, and then change the value of the **customerName** element to **GlobalBankWest**.</span></span>  
  
4.  <span data-ttu-id="42491-120">儲存 West.xml 為 utf-8，，然後關閉 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="42491-120">Save West.xml as UTF-8, and then close Notepad.</span></span>  
  
#### <a name="to-create-the-globalbank-east-test-message"></a><span data-ttu-id="42491-121">若要建立 GlobalBank 東部測試訊息</span><span class="sxs-lookup"><span data-stu-id="42491-121">To create the GlobalBank East test message</span></span>  
  
1.  <span data-ttu-id="42491-122">在 Windows 檔案總管，瀏覽至 C:\HowTos。</span><span class="sxs-lookup"><span data-stu-id="42491-122">In Windows Explorer, browse to C:\HowTos.</span></span>  
  
2.  <span data-ttu-id="42491-123">建立一份 NAOrderDoc.xml，，然後複製 East.xml。</span><span class="sxs-lookup"><span data-stu-id="42491-123">Create a copy of NAOrderDoc.xml, and then name the copy East.xml.</span></span>  
  
3.  <span data-ttu-id="42491-124">在 [記事本] 開啟 East.xml，並將值**customerName**元素**GlobalBankEast**。</span><span class="sxs-lookup"><span data-stu-id="42491-124">In Notepad, open East.xml, and then change the value of the **customerName** element to **GlobalBankEast**.</span></span>  
  
4.  <span data-ttu-id="42491-125">儲存 East.xml 為 utf-8，，然後關閉 [記事本]。</span><span class="sxs-lookup"><span data-stu-id="42491-125">Save East.xml as UTF-8, and then close Notepad.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="42491-126">步驟</span><span class="sxs-lookup"><span data-stu-id="42491-126">Steps</span></span>  
  
#### <a name="to-create-a-bre-policy-to-route-using-custom-message-properties"></a><span data-ttu-id="42491-127">若要建立 BRE 原則路由傳送使用自訂訊息屬性</span><span class="sxs-lookup"><span data-stu-id="42491-127">To create a BRE policy to route using custom message properties</span></span>  
 <span data-ttu-id="42491-128">此規則會使用客戶的名稱，以動態方式設定用來將訊息路由的端點。</span><span class="sxs-lookup"><span data-stu-id="42491-128">This rule will use the customer's name to dynamically set the endpoint used to route the message.</span></span>  
  
1.  <span data-ttu-id="42491-129">按一下**啟動**在工作列上，指向**所有程式**，指向   **[!INCLUDE[prague](../includes/prague-md.md)]** ，然後按一下**商務規則編輯器 」**。</span><span class="sxs-lookup"><span data-stu-id="42491-129">Click **Start** on the taskbar, point to **All Programs**, point to **[!INCLUDE[prague](../includes/prague-md.md)]**, and then click **Business Rule Composer**.</span></span>  
  
2.  <span data-ttu-id="42491-130">在 [原則總管] 中，以滑鼠右鍵按一下**原則**，然後按一下**新增原則**。</span><span class="sxs-lookup"><span data-stu-id="42491-130">In Policy Explorer, right-click **Policies**, and then click **Add New Policy**.</span></span> <span data-ttu-id="42491-131">命名原則**RouteBasedOnCustomerKnownType**。</span><span class="sxs-lookup"><span data-stu-id="42491-131">Name the policy **RouteBasedOnCustomerKnownType**.</span></span>  
  
#### <a name="to-add-a-routing-rule-for-customer-globalbank-west"></a><span data-ttu-id="42491-132">若要加入客戶 GlobalBank 西的路由規則</span><span class="sxs-lookup"><span data-stu-id="42491-132">To add a routing rule for customer GlobalBank West</span></span>  
  
1.  <span data-ttu-id="42491-133">在**RouteBasedOnCustomerKnownType**原則，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下**新增規則**。</span><span class="sxs-lookup"><span data-stu-id="42491-133">In the **RouteBasedOnCustomerKnownType** policy, right-click **Version 1.0 (not saved)**, and then click **Add New Rule**.</span></span> <span data-ttu-id="42491-134">命名規則**SetWestEndpoint**。</span><span class="sxs-lookup"><span data-stu-id="42491-134">Name the rule **SetWestEndpoint**.</span></span>  
  
2.  <span data-ttu-id="42491-135">在 事實總管 中，按一下  **XML 結構描述**索引標籤上，以滑鼠右鍵按一下**結構描述**，然後按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="42491-135">In Facts Explorer, click the **XML Schemas** tab, right-click **Schemas**, and then click **Browse**.</span></span>  
  
3.  <span data-ttu-id="42491-136">在**結構描述檔案**對話方塊中，瀏覽至 C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB。選取 DynamicResolution.Schemas **NAOrderDoc.xsd**，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="42491-136">In the **Schema Files** dialog box, browse to C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Source\ESB.DynamicResolution.Schemas, select **NAOrderDoc.xsd**, and then click **Open**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="42491-137">這是定義用來建立將用於測試的西和東訊息 NAOrderDoc.xml 訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="42491-137">This is the schema that defines the NAOrderDoc.xml message, which was used to create the West and East messages you will use for testing.</span></span>  
  
4.  <span data-ttu-id="42491-138">在 事實總管 中，按一下  **NAOrderDoc.xsd**，然後在 屬性 窗格中，按一下 **文件類型**屬性，，然後輸入**GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**.</span><span class="sxs-lookup"><span data-stu-id="42491-138">In Facts Explorer, click **NAOrderDoc.xsd**, and then in the Properties pane, click the **Document Type** property, and then type **GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="42491-139">這是結構描述的完整的名稱。</span><span class="sxs-lookup"><span data-stu-id="42491-139">This is the fully qualified name of the schema.</span></span>  
  
5.  <span data-ttu-id="42491-140">在 [事實總管] 中，展開**NAOrderDoc.xsd**，然後展開**OrderDoc**。</span><span class="sxs-lookup"><span data-stu-id="42491-140">In Facts Explorer, expand **NAOrderDoc.xsd**, and then expand **OrderDoc**.</span></span>  
  
6.  <span data-ttu-id="42491-141">在 規則 視窗中，以滑鼠右鍵按一下**條件**，指向 **述詞**，然後按一下**等於**。</span><span class="sxs-lookup"><span data-stu-id="42491-141">In the Rule window, right-click **Conditions**, point to **Predicates**, and then click **Equal**.</span></span>  
  
7.  <span data-ttu-id="42491-142">從 [事實總管] 中，拖曳**customerName**元素**引數 1**節點下的**條件**。</span><span class="sxs-lookup"><span data-stu-id="42491-142">From Facts Explorer, drag the **customerName** element to the **argument1** node under **Conditions**.</span></span>  
  
8.  <span data-ttu-id="42491-143">按一下**引數 2**  節點，然後輸入**GlobalBankWest**。</span><span class="sxs-lookup"><span data-stu-id="42491-143">Click the **argument2** node, and then type **GlobalBankWest**.</span></span>  
  
9. <span data-ttu-id="42491-144">在 事實總管 中，按一下 **詞彙**索引標籤上，依序展開**ESB。EndPointInfo**，然後展開**1.0 版**。</span><span class="sxs-lookup"><span data-stu-id="42491-144">In Facts Explorer, click the **Vocabularies** tab, expand **ESB.EndPointInfo**, and then expand **Version 1.0**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="42491-145">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含數個可用於在 ESB 中建立規則使用的詞彙。</span><span class="sxs-lookup"><span data-stu-id="42491-145">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] includes several vocabularies that can be used for creating rules for use in the ESB.</span></span> <span data-ttu-id="42491-146">這些應該取代或夾帶您自己的詞彙。</span><span class="sxs-lookup"><span data-stu-id="42491-146">Some of these should be replaced or augmented with your own vocabularies.</span></span> <span data-ttu-id="42491-147">例如， **DynamicRunTimeMaptypes**已定義中的對應**GlobalBank**範例。</span><span class="sxs-lookup"><span data-stu-id="42491-147">For example, the **DynamicRunTimeMaptypes** has definitions for the maps provided in the **GlobalBank** samples.</span></span>  
  
10. <span data-ttu-id="42491-148">從 [事實總管] 中，拖曳**設定結束點輸出傳輸位置**定義**動作**。</span><span class="sxs-lookup"><span data-stu-id="42491-148">From Facts Explorer, drag the **Set End Point Outbound Transport Location** definition to **Actions**.</span></span>  
  
11. <span data-ttu-id="42491-149">按一下**\<空字串 >** ，然後輸入**C:\HowTos\Out\West%MessageID%.xml**。</span><span class="sxs-lookup"><span data-stu-id="42491-149">Click **\<empty string>** and then type **C:\HowTos\Out\West%MessageID%.xml**.</span></span>  
  
12. <span data-ttu-id="42491-150">從 [事實總管] 中，拖曳**設定結束點輸出傳輸類型**定義**動作**。</span><span class="sxs-lookup"><span data-stu-id="42491-150">From Facts Explorer, drag the **Set End Point Outbound Transport Type** definition to **Actions**.</span></span>  
  
13. <span data-ttu-id="42491-151">在 [事實總管] 中，展開**ESB。TransportTypes**，依序展開**1.0 版**，然後將拖曳**配接器提供者**定義**\<空字串 >**。</span><span class="sxs-lookup"><span data-stu-id="42491-151">In Facts Explorer, expand **ESB.TransportTypes**, expand **Version 1.0**, and then drag the **Adaptor Providers** definition to **\<empty string>**.</span></span>  
  
14. <span data-ttu-id="42491-152">在**動作**] 窗格中，展開 [**配接器提供者**下拉式清單，然後按一下**檔案**。</span><span class="sxs-lookup"><span data-stu-id="42491-152">In the **Actions** pane, expand the **Adaptor Providers** drop-down list, and then click **FILE**.</span></span>  
  
#### <a name="to-add-a-routing-rule-for-customer-globalbank-east"></a><span data-ttu-id="42491-153">若要加入客戶 GlobalBank 東部的路由規則</span><span class="sxs-lookup"><span data-stu-id="42491-153">To add a routing rule for customer GlobalBank East</span></span>  
  
1.  <span data-ttu-id="42491-154">在 [原則總管] 中，以滑鼠右鍵按一下**SetWestEndpoint**規則，，然後按一下**複製**。</span><span class="sxs-lookup"><span data-stu-id="42491-154">In Policy Explorer, right-click the **SetWestEndpoint** rule, and then click **Copy**.</span></span>  
  
2.  <span data-ttu-id="42491-155">以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下**貼上**。</span><span class="sxs-lookup"><span data-stu-id="42491-155">Right-click **Version 1.0 (not saved)**, and then click **Paste**.</span></span>  
  
3.  <span data-ttu-id="42491-156">在**新規則的名稱** 對話方塊中，輸入**SetEastEndpoint**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="42491-156">In the **New Rule Name** dialog box, type **SetEastEndpoint**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="42491-157">在 原則總管 中，按一下  **SetEastEndpoint**規則。</span><span class="sxs-lookup"><span data-stu-id="42491-157">In Policy Explorer, click the **SetEastEndpoint** rule.</span></span>  
  
5.  <span data-ttu-id="42491-158">在**條件**區段中，以滑鼠右鍵按一下**GlobalBankWest**，然後按一下**重設引數**。</span><span class="sxs-lookup"><span data-stu-id="42491-158">In the **Conditions** section, right-click **GlobalBankWest**, and then click **Reset argument**.</span></span>  
  
6.  <span data-ttu-id="42491-159">按一下**引數 2**，然後輸入**GlobalBankEast**。</span><span class="sxs-lookup"><span data-stu-id="42491-159">Click **argument2**, and then type **GlobalBankEast**.</span></span>  
  
7.  <span data-ttu-id="42491-160">在**動作**區段中，以滑鼠右鍵按一下**C:\HowTos\Out\West%MessageID%.xml**，然後按一下**重設引數**。</span><span class="sxs-lookup"><span data-stu-id="42491-160">In the **Actions** section, right-click **C:\HowTos\Out\West%MessageID%.xml**, and then click **Reset argument**.</span></span>  
  
8.  <span data-ttu-id="42491-161">按一下**\<空字串 >**，然後輸入**C:\HowTos\Out\East%MessageID%.xml**。</span><span class="sxs-lookup"><span data-stu-id="42491-161">Click **\<empty string>**, and then type **C:\HowTos\Out\East%MessageID%.xml**.</span></span>  
  
#### <a name="to-add-a-routing-rule-for-unknown-customers"></a><span data-ttu-id="42491-162">若要加入未知的客戶路由規則</span><span class="sxs-lookup"><span data-stu-id="42491-162">To add a routing rule for unknown customers</span></span>  
  
1.  <span data-ttu-id="42491-163">在 RouteBasedOnCustomerKnownType 原則中，以滑鼠右鍵按一下 1.0 版 （未儲存），然後按一下新增規則。</span><span class="sxs-lookup"><span data-stu-id="42491-163">In the RouteBasedOnCustomerKnownType policy, right-click Version 1.0 (not saved), and then click Add New Rule.</span></span> <span data-ttu-id="42491-164">命名規則 SetUnknownCustomerEndpoint。</span><span class="sxs-lookup"><span data-stu-id="42491-164">Name the rule SetUnknownCustomerEndpoint.</span></span>  
  
2.  <span data-ttu-id="42491-165">在 [規則] 視窗中，以滑鼠右鍵按一下條件，，然後按一下新增邏輯 and。</span><span class="sxs-lookup"><span data-stu-id="42491-165">In the Rule window, right-click Conditions, and then click Add logical AND.</span></span>  
  
3.  <span data-ttu-id="42491-166">在 規則 視窗中，以滑鼠右鍵按一下，指向 述詞，且然後按一下不等於。</span><span class="sxs-lookup"><span data-stu-id="42491-166">In the Rule window, right-click AND, point to Predicates, and then click NotEqual.</span></span>  
  
4.  <span data-ttu-id="42491-167">在 [事實總管] 中，按一下 [XML 結構描述] 索引標籤中，展開 NAOrderDoc.xsd，，然後展開 OrderDoc。</span><span class="sxs-lookup"><span data-stu-id="42491-167">In Facts Explorer, click the XML Schemas tab, expand NAOrderDoc.xsd, and then expand OrderDoc.</span></span>  
  
5.  <span data-ttu-id="42491-168">從事實總管 中，將 customerName 項目拖曳至條件下的引數 1 節點。</span><span class="sxs-lookup"><span data-stu-id="42491-168">From Facts Explorer, drag the customerName element to the argument1 node under Conditions.</span></span>  
  
6.  <span data-ttu-id="42491-169">按一下 引數 2 節點，然後輸入 GlobalBankWest。</span><span class="sxs-lookup"><span data-stu-id="42491-169">Click the argument2 node, and then type GlobalBankWest.</span></span>  
  
7.  <span data-ttu-id="42491-170">在 規則 視窗中，以滑鼠右鍵按一下，指向 述詞，且然後按一下不等於。</span><span class="sxs-lookup"><span data-stu-id="42491-170">In the Rule window, right-click AND, point to Predicates, and then click NotEqual.</span></span>  
  
8.  <span data-ttu-id="42491-171">從事實總管 中，將 customerName 項目拖曳至條件下的引數 1 節點。</span><span class="sxs-lookup"><span data-stu-id="42491-171">From Facts Explorer, drag the customerName element to the argument1 node under Conditions.</span></span>  
  
9. <span data-ttu-id="42491-172">按一下 引數 2 節點，然後輸入 GlobalBankEast。</span><span class="sxs-lookup"><span data-stu-id="42491-172">Click the argument2 node, and then type GlobalBankEast.</span></span>  
  
10. <span data-ttu-id="42491-173">在 事實總管 中，按一下 詞彙 索引標籤、 ESB。EndPointInfo，然後展開 1.0 版。</span><span class="sxs-lookup"><span data-stu-id="42491-173">In Facts Explorer, click the Vocabularies tab, expand ESB.EndPointInfo, and then expand Version 1.0.</span></span>  
  
11. <span data-ttu-id="42491-174">從 [事實總管] 中，拖曳設定結束點輸出傳輸位置定義的動作。</span><span class="sxs-lookup"><span data-stu-id="42491-174">From Facts Explorer, drag the Set End Point Outbound Transport Location definition to Actions.</span></span>  
  
12. <span data-ttu-id="42491-175">按一下\<空字串 >，然後輸入 C:\HowTos\Out\CustomerUnknown%MessageID%.xml。</span><span class="sxs-lookup"><span data-stu-id="42491-175">Click \<empty string>, and then type C:\HowTos\Out\CustomerUnknown%MessageID%.xml.</span></span>  
  
13. <span data-ttu-id="42491-176">從 [事實總管] 中，拖曳設定結束點輸出傳輸類型定義的動作。</span><span class="sxs-lookup"><span data-stu-id="42491-176">From Facts Explorer, drag the Set End Point Outbound Transport Type definition to Actions.</span></span>  
  
14. <span data-ttu-id="42491-177">在 事實總管 中，展開 ESB。TransportTypes，展開 1.0 版，然後將拖曳至配接器提供者定義\<空字串 >。</span><span class="sxs-lookup"><span data-stu-id="42491-177">In Facts Explorer, expand ESB.TransportTypes, expand Version 1.0, and then drag the Adaptor Providers definition to \<empty string>.</span></span>  
  
15. <span data-ttu-id="42491-178">在 [動作] 窗格中，展開 [配接器提供者] 下拉式清單，然後按一下檔案。</span><span class="sxs-lookup"><span data-stu-id="42491-178">In the Actions pane, expand the Adaptor Providers drop-down list, and then click FILE.</span></span>  
  
#### <a name="to-publish-and-deploy-the-policy"></a><span data-ttu-id="42491-179">若要發行和部署原則</span><span class="sxs-lookup"><span data-stu-id="42491-179">To publish and deploy the policy</span></span>  
  
1.  <span data-ttu-id="42491-180">在 [原則總管] 中，在**RouteBasedOnCustomerKnownType**原則，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下**發行**。</span><span class="sxs-lookup"><span data-stu-id="42491-180">In Policy Explorer, under the **RouteBasedOnCustomerKnownType** policy, right click **Version 1.0 (not saved)**, and then click **Publish**.</span></span>  
  
2.  <span data-ttu-id="42491-181">在 [原則總管] 中，在**RouteBasedOnCustomerKnownType**原則，以滑鼠右鍵按一下**1.0 版-已發佈**，然後按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="42491-181">In Policy Explorer, under the **RouteBasedOnCustomerKnownType** policy, right click **Version 1.0 - Published**, and then click **Deploy**.</span></span>  
  
#### <a name="to-create-an-esb-itinerary-dsl-model"></a><span data-ttu-id="42491-182">若要建立 ESB 路線 DSL 模型</span><span class="sxs-lookup"><span data-stu-id="42491-182">To create an ESB itinerary DSL model</span></span>  
  
1.  <span data-ttu-id="42491-183">在[!INCLUDE[vs2010](../includes/vs2010-md.md)]，開啟 C:\HowTos\Patterns\Patterns.sln。</span><span class="sxs-lookup"><span data-stu-id="42491-183">In [!INCLUDE[vs2010](../includes/vs2010-md.md)], open C:\HowTos\Patterns\Patterns.sln.</span></span>  
  
2.  <span data-ttu-id="42491-184">在 [方案總管] 中，以滑鼠右鍵按一下**ItineraryLibrary**專案，指向**新增**，然後按一下**新的行程**。</span><span class="sxs-lookup"><span data-stu-id="42491-184">In Solution Explorer, right-click the **ItineraryLibrary** project, point to **Add**, and then click **New Itinerary**.</span></span>  
  
3.  <span data-ttu-id="42491-185">在**加入新項目**對話方塊中，於**名稱**方塊中，輸入**CbrKnownType**，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="42491-185">In the **Add New Item** dialog box, in the **Name** box, type **CbrKnownType**, and then click **Add**.</span></span>  
  
#### <a name="to-configure-the-properties-of-the-itinerary"></a><span data-ttu-id="42491-186">若要設定的路線屬性</span><span class="sxs-lookup"><span data-stu-id="42491-186">To configure the properties of the itinerary</span></span>  
  
1.  <span data-ttu-id="42491-187">在 Visual Studio 中，按一下設計介面的**CbrKnownType.itinerary**。</span><span class="sxs-lookup"><span data-stu-id="42491-187">In Visual Studio, click the design surface of **CbrKnownType.itinerary**.</span></span> <span data-ttu-id="42491-188">在**CbrKnownType**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="42491-188">In the **CbrKnownType** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="42491-189">在**模型匯出工具**下拉式清單中，按一下  **XML 路線匯出工具**。</span><span class="sxs-lookup"><span data-stu-id="42491-189">In the **Model Exporter** drop-down list, click **XML Itinerary Exporter**.</span></span>  
  
    2.  <span data-ttu-id="42491-190">在**Extender 設定**區段中，旁邊**路線 XML 檔案**屬性，按一下省略符號按鈕 （...）。</span><span class="sxs-lookup"><span data-stu-id="42491-190">In the **Extender Settings** section, next to the **Itinerary XML file** property, click the ellipsis button (...).</span></span>  
  
    3.  <span data-ttu-id="42491-191">在**選取 XML 檔案** 對話方塊中，輸入**C:\HowTos\Itineraries\CbrKnownType**中**檔案名稱**方塊，然後再按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="42491-191">In the **Select XML File** dialog box, type **C:\HowTos\Itineraries\CbrKnownType** in the **File name** box, and then click **Save**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="42491-192">這個步驟可讓您匯出成 XML 的路線，到本機檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="42491-192">This step enables you to export the itinerary as XML to a local file location.</span></span> <span data-ttu-id="42491-193">藉由將行程至本機檔案的位置，而不匯出至路線的資料庫，可讓測試使用 ESB 測試用戶端應用程式的路線。</span><span class="sxs-lookup"><span data-stu-id="42491-193">By exporting an itinerary to a local file location, instead of to the itinerary database, enables testing of the itinerary using the ESB Test Client application.</span></span> <span data-ttu-id="42491-194">您將完成此程序，稍後在本使用說明主題。</span><span class="sxs-lookup"><span data-stu-id="42491-194">You will complete this process later in this How-to topic.</span></span>  
  
#### <a name="to-define-the-structure-of-the-itinerary"></a><span data-ttu-id="42491-195">若要定義路線結構</span><span class="sxs-lookup"><span data-stu-id="42491-195">To define the structure of the itinerary</span></span>  
  
1.  <span data-ttu-id="42491-196">從 [工具箱] 拖曳**上手**至設計介面的模型項目。</span><span class="sxs-lookup"><span data-stu-id="42491-196">From the Toolbox, drag an **On-Ramp** model element to the design surface.</span></span> <span data-ttu-id="42491-197">在**OnRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="42491-197">In the **OnRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="42491-198">按一下**名稱**屬性，，然後輸入**ReceiveNAOrder**。</span><span class="sxs-lookup"><span data-stu-id="42491-198">Click the **Name** property, and then type **ReceiveNAOrder**.</span></span>  
  
    2.  <span data-ttu-id="42491-199">在**Extender**下拉式清單中，按一下 **上手 ESB Extender**。</span><span class="sxs-lookup"><span data-stu-id="42491-199">In the **Extender** drop-down list, click **On-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="42491-200">在**BizTalk 應用程式**下拉式清單中，按一下  **Microsoft.Practices.ESB**。</span><span class="sxs-lookup"><span data-stu-id="42491-200">In the **BizTalk Application** drop-down list, click **Microsoft.Practices.ESB**.</span></span>  
  
    4.  <span data-ttu-id="42491-201">在**接收埠**下拉式清單中，按一下  **OnRamp.Itinerary**。</span><span class="sxs-lookup"><span data-stu-id="42491-201">In the **Receive Port** drop-down list, click **OnRamp.Itinerary**.</span></span>  
  
2.  <span data-ttu-id="42491-202">從 [工具箱] 拖曳**匝道**模型項目至設計介面，然後再將它放右邊的**ReceiveNAOrder**模型項目。</span><span class="sxs-lookup"><span data-stu-id="42491-202">From the Toolbox, drag an **Off-Ramp** model element to the design surface, and then place it to the right of the **ReceiveNAOrder** model element.</span></span> <span data-ttu-id="42491-203">在**OffRamp1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="42491-203">In the **OffRamp1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="42491-204">按一下**名稱**屬性，，然後輸入**SendRegionalOrders**。</span><span class="sxs-lookup"><span data-stu-id="42491-204">Click the **Name** property, and then type **SendRegionalOrders**.</span></span>  
  
    2.  <span data-ttu-id="42491-205">在**Extender**下拉式清單中，按一下 **匝道 ESB Extender**。</span><span class="sxs-lookup"><span data-stu-id="42491-205">In the **Extender** drop-down list, click **Off-Ramp ESB Extender**.</span></span>  
  
    3.  <span data-ttu-id="42491-206">在**BizTalk 應用程式**下拉式清單中，按一下  **GlobalBank.ESB**。</span><span class="sxs-lookup"><span data-stu-id="42491-206">In the **BizTalk Application** drop-down list, click **GlobalBank.ESB**.</span></span>  
  
    4.  <span data-ttu-id="42491-207">在**傳送埠**下拉式清單中，按一下  **DynamicResolutionOneWay**。</span><span class="sxs-lookup"><span data-stu-id="42491-207">In the **Send Port** drop-down list, click **DynamicResolutionOneWay**.</span></span>  
  
3.  <span data-ttu-id="42491-208">從 [工具箱] 拖曳**路線服務**模型項目至設計介面，並將其之間放置**ReceiveNAOrder**模型項目和**SendRegionalOrders**模型項目。</span><span class="sxs-lookup"><span data-stu-id="42491-208">From the Toolbox, drag an **Itinerary Service** model element to the design surface, and then place it between the **ReceiveNAOrder** model element and the **SendRegionalOrders** model element.</span></span> <span data-ttu-id="42491-209">在**ItineraryService1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="42491-209">In the **ItineraryService1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="42491-210">按一下**名稱**屬性，，然後輸入**SendPortFilter**。</span><span class="sxs-lookup"><span data-stu-id="42491-210">Click the **Name** property, and then type **SendPortFilter**.</span></span>  
  
    2.  <span data-ttu-id="42491-211">在**路線服務的擴充項**下拉式清單中，按一下 **匝道 Extender**。</span><span class="sxs-lookup"><span data-stu-id="42491-211">In the **Itinerary Service Extender** drop-down list, click **Off-Ramp Extender**.</span></span>  
  
    3.  <span data-ttu-id="42491-212">在**匝道**下拉式清單中，展開**SendRegionalOrders**，然後按一下**傳送處理常式**。</span><span class="sxs-lookup"><span data-stu-id="42491-212">In the **Off-Ramp** drop-down list, expand **SendRegionalOrders**, and then click **Send Handlers**.</span></span>  
  
4.  <span data-ttu-id="42491-213">以滑鼠右鍵按一下**解析程式**集合**SendPortFilter**模型項目，然後按一下**加入新的解析程式**。</span><span class="sxs-lookup"><span data-stu-id="42491-213">Right-click the **Resolver** collection of the **SendPortFilter** model element, and then click **Add new Resolver**.</span></span> <span data-ttu-id="42491-214">在**Resolver1**屬性 視窗中，設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="42491-214">In the **Resolver1** Properties window, configure the following properties:</span></span>  
  
    1.  <span data-ttu-id="42491-215">按一下**名稱**屬性，，然後輸入**RouteRegionalOrders**。</span><span class="sxs-lookup"><span data-stu-id="42491-215">Click the **Name** property, and then type **RouteRegionalOrders**.</span></span>  
  
    2.  <span data-ttu-id="42491-216">在**傳輸名稱**下拉式清單中，按一下  **BRE**。</span><span class="sxs-lookup"><span data-stu-id="42491-216">In the **Transport Name** drop-down list, click **BRE**.</span></span>  
  
    3.  <span data-ttu-id="42491-217">在**解析程式實作**下拉式清單中，按一下  **Bre 解析程式擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="42491-217">In the **Resolver Implementation** drop-down list, click **Bre Resolver Extension**.</span></span>  
  
    4.  <span data-ttu-id="42491-218">在**原則**下拉式清單中，按一下  **RouteBasedOnCustomerKnownType**。</span><span class="sxs-lookup"><span data-stu-id="42491-218">In the **Policy** drop-down list, click **RouteBasedOnCustomerKnownType**.</span></span>  
  
    5.  <span data-ttu-id="42491-219">在**辨識訊息格式**下拉式清單中按一下**True**。</span><span class="sxs-lookup"><span data-stu-id="42491-219">In the **Recognize Message Format** drop-down list click **True**.</span></span>  
  
    6.  <span data-ttu-id="42491-220">在**UseMsg**下拉式清單中，按一下  **True**。</span><span class="sxs-lookup"><span data-stu-id="42491-220">In the **UseMsg** drop-down list, click **True**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="42491-221">如果您使用 BRE 解析程式擴充功能，從協調流程， **recognizeMessageFormat**屬性必須設定為**False**。</span><span class="sxs-lookup"><span data-stu-id="42491-221">If you use the BRE Resolver Extension from orchestration, the **recognizeMessageFormat** property must be set to **False**.</span></span>  
  
5.  <span data-ttu-id="42491-222">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="42491-222">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="42491-223">拖曳連接**ReceiveNAOrder**模型項目的**SendPortFilter**模型項目。</span><span class="sxs-lookup"><span data-stu-id="42491-223">Drag a connection from the **ReceiveNAOrder** model element to the **SendPortFilter** model element.</span></span>  
  
6.  <span data-ttu-id="42491-224">在工具箱中，按一下 **連接器**。</span><span class="sxs-lookup"><span data-stu-id="42491-224">In the Toolbox, click **Connector**.</span></span> <span data-ttu-id="42491-225">拖曳連接**SendPortFilter**模型項目的**SendRegionalOrders**模型項目。</span><span class="sxs-lookup"><span data-stu-id="42491-225">Drag a connection from the **SendPortFilter** model element to the **SendRegionalOrders** model element.</span></span>  
  
#### <a name="to-export-the-model-for-use-with-the-itinerary-test-client"></a><span data-ttu-id="42491-226">若要匯出的行程測試用戶端使用的模型</span><span class="sxs-lookup"><span data-stu-id="42491-226">To export the model for use with the Itinerary Test Client</span></span>  
  
1.  <span data-ttu-id="42491-227">在 Visual Studio 中，以滑鼠右鍵按一下設計介面的**CbrKnownType**路線，然後再按一下**匯出模型**。</span><span class="sxs-lookup"><span data-stu-id="42491-227">In Visual Studio, right-click the design surface of the **CbrKnownType** itinerary, and then click **Export Model**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="42491-228">在 Visual Studio 中，開啟路線的 XML 版本。</span><span class="sxs-lookup"><span data-stu-id="42491-228">The XML version of the itinerary opens in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="42491-229">儲存專案的所有成品。</span><span class="sxs-lookup"><span data-stu-id="42491-229">Save all project artifacts.</span></span>  
  
3.  <span data-ttu-id="42491-230">在 Windows 檔案總管，瀏覽至 C:\HowTos\Itineraries 並注意您路線 XML (CbrKnownType.xml) 建立。</span><span class="sxs-lookup"><span data-stu-id="42491-230">In Windows Explorer, browse to C:\HowTos\Itineraries and notice the creation of your itinerary XML (CbrKnownType.xml).</span></span>  
  
#### <a name="to-test-the-itinerary-and-business-rules"></a><span data-ttu-id="42491-231">若要測試計劃與商務規則</span><span class="sxs-lookup"><span data-stu-id="42491-231">To test the itinerary and business rules</span></span>  
  
1.  <span data-ttu-id="42491-232">開啟路線測試用戶端範例應用程式使用期間建立的捷徑[開發活動的必要條件](../esb-toolkit/prerequisites-for-the-development-activities.md)(C:\HowTos\ESB。Itinerary.Test.exe-捷徑)。</span><span class="sxs-lookup"><span data-stu-id="42491-232">Open the Itinerary Test Client sample application using the shortcut created during the [Prerequisites for the Development Activities](../esb-toolkit/prerequisites-for-the-development-activities.md) (C:\HowTos\ESB.Itinerary.Test.exe - Shortcut).</span></span>  
  
2.  <span data-ttu-id="42491-233">在路線測試用戶端中，清除**使用 WCF 服務**核取方塊，然後**負載路線**。</span><span class="sxs-lookup"><span data-stu-id="42491-233">In the Itinerary Test Client, clear the **Use WCF Service** check box, and then click **Load Itinerary**.</span></span>  
  
3.  <span data-ttu-id="42491-234">在**開啟路線檔案**對話方塊中，瀏覽至 C:\HowTos\Itineraries。</span><span class="sxs-lookup"><span data-stu-id="42491-234">In the **Open Itinerary File** dialog box, browse to C:\HowTos\Itineraries.</span></span> <span data-ttu-id="42491-235">選取**CbrKnownType.xml**，然後按一下**開啟**載入路線。</span><span class="sxs-lookup"><span data-stu-id="42491-235">Select **CbrKnownType.xml**, and then click **Open** to load the itinerary.</span></span>  
  
4.  <span data-ttu-id="42491-236">按一下**確定**清除**路線成功載入**訊息。</span><span class="sxs-lookup"><span data-stu-id="42491-236">Click **OK** to clear the **Itinerary Loaded Successfully** message.</span></span>  
  
5.  <span data-ttu-id="42491-237">在路線測試用戶端中，按一下旁邊的省略符號按鈕 （...）**載入訊息**方塊。</span><span class="sxs-lookup"><span data-stu-id="42491-237">In the Itinerary Test Client, click the ellipsis button (...) next to the **Load Message** box.</span></span>  
  
6.  <span data-ttu-id="42491-238">在**選取要載入的 XML 文件**對話方塊中，瀏覽至 C:\HowTos。</span><span class="sxs-lookup"><span data-stu-id="42491-238">In the **Select XML Document to load** dialog box, browse to C:\HowTos.</span></span> <span data-ttu-id="42491-239">選取**West.xml**，然後按一下**開啟**載入測試訊息。</span><span class="sxs-lookup"><span data-stu-id="42491-239">Select **West.xml**, and then click **Open** to load the test message.</span></span>  
  
7.  <span data-ttu-id="42491-240">按一下**送出要求** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="42491-240">Click the **Submit Request** button.</span></span> <span data-ttu-id="42491-241">測試完成時，按一下**確定**解除顯示的確認。</span><span class="sxs-lookup"><span data-stu-id="42491-241">When the test completes, click **OK** to dismiss the confirmation that appears.</span></span>  
  
8.  <span data-ttu-id="42491-242">在 Windows 檔案總管，瀏覽至 C:\HowTos\Out。請確認 West%MessageID%.xml 訊息已寫入至目錄。</span><span class="sxs-lookup"><span data-stu-id="42491-242">In Windows Explorer, browse to C:\HowTos\Out. Verify that the West%MessageID%.xml message has been written to the directory.</span></span>  
  
9. <span data-ttu-id="42491-243">重複使用 East.xml 訊息測試程序。</span><span class="sxs-lookup"><span data-stu-id="42491-243">Repeat the test process using the East.xml message.</span></span>  
  
10. <span data-ttu-id="42491-244">在 Windows 檔案總管，瀏覽至 C:\HowTos\Out。請確認 East%MessageID%.xml 訊息已寫入至目錄。</span><span class="sxs-lookup"><span data-stu-id="42491-244">In Windows Explorer, browse to C:\HowTos\Out. Verify that the East%MessageID%.xml message has been written to the directory.</span></span>  
  
11. <span data-ttu-id="42491-245">重複使用 NAOrderDoc.xml 訊息測試程序。</span><span class="sxs-lookup"><span data-stu-id="42491-245">Repeat the test process using the NAOrderDoc.xml message.</span></span>  
  
12. <span data-ttu-id="42491-246">在 Windows 檔案總管，瀏覽至 C:\HowTos\Out。請確認 CustomerUnknown%MessageID%.xml 訊息已寫入至目錄。</span><span class="sxs-lookup"><span data-stu-id="42491-246">In Windows Explorer, browse to C:\HowTos\Out. Verify that the CustomerUnknown%MessageID%.xml message has been written to the directory.</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="42491-247">其他資源</span><span class="sxs-lookup"><span data-stu-id="42491-247">Additional Resources</span></span>  
 <span data-ttu-id="42491-248">如需詳細資訊，請參閱下列相關主題：</span><span class="sxs-lookup"><span data-stu-id="42491-248">For more information, see the following related topics:</span></span>  
  
-   [<span data-ttu-id="42491-249">如何： 選取 使用商務規則原則路線</span><span class="sxs-lookup"><span data-stu-id="42491-249">How to: Select an Itinerary Using a Business Rules Policy</span></span>](../esb-toolkit/how-to-select-an-itinerary-using-a-business-rules-policy.md)  
  
-   [<span data-ttu-id="42491-250">如何： 動態地路由傳送訊息的內容使用商務規則原則為基礎的訊息</span><span class="sxs-lookup"><span data-stu-id="42491-250">How to: Dynamically Route a Message Based on Message Context Using a Business Rules Policy</span></span>](../esb-toolkit/dynamically-route-messages-based-on-message-context-using-business-rules-policy.md)  
  
-   [<span data-ttu-id="42491-251">開發活動</span><span class="sxs-lookup"><span data-stu-id="42491-251">Development Activities</span></span>](../esb-toolkit/development-activities.md)  
  
-   [<span data-ttu-id="42491-252">訊息的路由模式</span><span class="sxs-lookup"><span data-stu-id="42491-252">Message Routing Patterns</span></span>](../esb-toolkit/message-routing-patterns.md)