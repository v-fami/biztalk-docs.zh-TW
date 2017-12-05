---
title: "使用資料提供者的 DDEX 外掛程式與 SAP |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DDEX plug-in
- DDEX plug-in, Data Provider for SAP
- Data Provider for SAP, using with DDEX plug-in
ms.assetid: b16c8634-172a-4630-87ed-2073a75afdec
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2a1dd348b6d897e147d6add49499e9716a67aeb
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="use-the-data-provider-for-sap-with-the-ddex-plug-in"></a><span data-ttu-id="9a7e8-102">使用資料提供者的 DDEX 外掛程式的 sap</span><span class="sxs-lookup"><span data-stu-id="9a7e8-102">Use the Data Provider for SAP with the DDEX Plug-in</span></span>
<span data-ttu-id="9a7e8-103">如果您選擇要安裝[!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)]連同[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝，安裝程式安裝[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]DDEX 外掛程式。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-103">If you chose to install the [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)] along with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation, the setup program installs a [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] DDEX plug-in.</span></span> <span data-ttu-id="9a7e8-104">您可以使用此外掛程式來瀏覽使用 SAP 物件[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-104">You can use this plug-in to browse SAP objects using [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="9a7e8-105">本節提供使用 DDEX 外掛程式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-105">This section provides information about using the DDEX plug-in.</span></span>  
  
 <span data-ttu-id="9a7e8-106">您可以使用外掛程式，建立與 SAP 系統中，從 SAP 系統中，加入資料表，並從 SAP 系統加入函式模組。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-106">You can use the plug-in to establish connectivity with the SAP system, add tables from the SAP system, and add function modules from the SAP system.</span></span> <span data-ttu-id="9a7e8-107">加入資料表和函式的模組，使用 Visual Studio 外掛程式之後，新加入的資料表和函式的模組會反映在 SAPDiscoveredObjects.xml 檔案中。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-107">After you have added the tables and function modules using the Visual Studio plug-in, the newly added tables and function modules are reflected in the SAPDiscoveredObjects.xml file.</span></span> <span data-ttu-id="9a7e8-108">如需有關這個檔案的詳細資訊，請參閱[有關 SAPDiscoveredObjects.xml File sap](../../adapters-and-accelerators/adapter-sap/about-the-sapdiscoveredobjects-xml-file-in-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-108">For more information about this file, see [About the SAPDiscoveredObjects.xml File in SAP](../../adapters-and-accelerators/adapter-sap/about-the-sapdiscoveredobjects-xml-file-in-sap.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9a7e8-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="9a7e8-109">Prerequisites</span></span>  
 <span data-ttu-id="9a7e8-110">請確定您選擇要安裝[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]連同[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]安裝。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-110">Make sure you chose to install the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] along with the [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] installation.</span></span>  
  
### <a name="to-connect-to-an-sap-system-using-the-ddex-plug-in"></a><span data-ttu-id="9a7e8-111">若要連接至 SAP 系統使用 DDEX 外掛程式</span><span class="sxs-lookup"><span data-stu-id="9a7e8-111">To connect to an SAP system using the DDEX plug-in</span></span>  
  
1.  <span data-ttu-id="9a7e8-112">啟動 Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-112">Start Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="9a7e8-113">在[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]上**檢視**功能表上，按一下 **伺服器總管**。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-113">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **View** menu, click **Server Explorer**.</span></span>  
  
3.  <span data-ttu-id="9a7e8-114">在**伺服器總管**，以滑鼠右鍵按一下**資料連接**，然後選取**加入連接**。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-114">In the **Server Explorer**, right-click **Data Connections**, and select **Add Connection**.</span></span>  
  
4.  <span data-ttu-id="9a7e8-115">在**變更資料來源**對話方塊中，從**資料來源**方塊中，選取**\<其他\>**。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-115">In the **Change Data Source** dialog box, from the **Data source** box, select **\<other\>**.</span></span>  
  
5.  <span data-ttu-id="9a7e8-116">從**資料提供者**下拉式清單中，選取**.NET Framework Data Provider for mySAP Business Suite**按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-116">From the **Data provider** drop-down list, select **.NET Framework Data Provider for mySAP Business Suite** and click **OK**.</span></span> <span data-ttu-id="9a7e8-117">**加入連接**對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-117">The **Add Connection** dialog box opens.</span></span>  
  
6.  <span data-ttu-id="9a7e8-118">**加入連接**對話方塊會列出不同的連線參數，以連接至 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-118">The **Add Connection** dialog box lists the different connection parameters to connect to an SAP system.</span></span> <span data-ttu-id="9a7e8-119">一般連接字串來連接 SAP 系統使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]需要：</span><span class="sxs-lookup"><span data-stu-id="9a7e8-119">A typical connection string to connect to an SAP system using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] requires:</span></span>  
  
    -   <span data-ttu-id="9a7e8-120">輸入連接的連接參數。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-120">The connection parameters for a connection type.</span></span> <span data-ttu-id="9a7e8-121">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]支援連線類型 A、 B 和 d。若要連接到 SAP 系統必須提供連接參數的任何*一個*一種連線類型。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-121">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] supports connection types A, B, and D. To connect to an SAP system you must provide connection parameters for any *one* of these connection types.</span></span> <span data-ttu-id="9a7e8-122">比方說，連接類型的您必須提供應用程式伺服器主機和系統編號的名稱。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-122">For example, for connection type A, you must provide the name of the application server host and the system number.</span></span>  
  
    -   <span data-ttu-id="9a7e8-123">若要連接到 SAP 系統，例如使用者名稱和密碼登入資訊。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-123">The login information to connect to an SAP system such as username and password.</span></span>  
  
     <span data-ttu-id="9a7e8-124">如需有關連接字串來連接 SAP 系統使用[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]，請參閱[閱讀 SAP 連接字串的資料提供者類型](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md)。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-124">For more information about the connection string to connect to an SAP system using the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)], see [Read about Data Provider types for the SAP Connection String](../../adapters-and-accelerators/adapter-sap/read-about-data-provider-types-for-the-sap-connection-string.md).</span></span>  
  
     <span data-ttu-id="9a7e8-125">在**加入連接**對話方塊方塊中，指定：</span><span class="sxs-lookup"><span data-stu-id="9a7e8-125">In the **Add Connection** dialog box, specify:</span></span>  
  
    -   <span data-ttu-id="9a7e8-126">連接類型之參數的任何一個連線。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-126">The connection parameters for any one connection type.</span></span>  
  
    -   <span data-ttu-id="9a7e8-127">要連接至 SAP 系統的登入資訊。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-127">The login information to connect to an SAP system.</span></span>  
  
    -   <span data-ttu-id="9a7e8-128">您是否要啟用 SAP GUI 偵錯。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-128">Whether you want to enable SAP GUI debugging.</span></span>  
  
    -   <span data-ttu-id="9a7e8-129">您是否要使用 RFC SDK 追蹤。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-129">Whether you want to use RFC SDK tracing.</span></span>  
  
     <span data-ttu-id="9a7e8-130">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-130">Click **OK**.</span></span> <span data-ttu-id="9a7e8-131">下方會建立新的連線節點**資料連接**您在上一個步驟中指定的伺服器名稱的節點。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-131">A new connection node is created under the **Data Connections** node with the server name you specified in the previous step.</span></span>  
  
7.  <span data-ttu-id="9a7e8-132">展開以檢視新的連線節點**資料表**和**函式模組**節點。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-132">Expand the new connection node to view the **Tables** and **Function Modules** nodes.</span></span>  
  
     <span data-ttu-id="9a7e8-133">在連線建立之後下, 圖顯示 [伺服器總管] 中。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-133">The following figure shows the Server Explorer after the connection is established.</span></span>  
  
     <span data-ttu-id="9a7e8-134">![DDEX 外掛程式 &#45; 在 SAP ADO.NET 提供者](../../adapters-and-accelerators/adapter-sap/media/158afc11-9c90-4333-bc62-5901f8d0c794.gif "158afc11-9c90-4333-bc62-5901f8d0c794")</span><span class="sxs-lookup"><span data-stu-id="9a7e8-134">![DDEX plug&#45;in for SAP ADO.NET Provider](../../adapters-and-accelerators/adapter-sap/media/158afc11-9c90-4333-bc62-5901f8d0c794.gif "158afc11-9c90-4333-bc62-5901f8d0c794")</span></span>  
  
### <a name="to-add-tables-from-an-sap-system-using-the-ddex-plug-in"></a><span data-ttu-id="9a7e8-135">若要加入使用 DDEX 外掛程式的 SAP 系統中的資料表</span><span class="sxs-lookup"><span data-stu-id="9a7e8-135">To add tables from an SAP system using the DDEX plug-in</span></span>  
  
1.  <span data-ttu-id="9a7e8-136">在**伺服器總管**，以滑鼠右鍵按一下**資料表**節點，然後按一下**搜尋與新增資料表**。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-136">In the **Server Explorer**, right-click the **Tables** node and click **Search and Add Tables**.</span></span>  
  
2.  <span data-ttu-id="9a7e8-137">在**搜尋資料表名稱**文字方塊中，指定搜尋字串以搜尋資料表中的 SAP 系統，然後按一下**搜尋**。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-137">In the **Search table name** text box, specify a search string to search tables in the SAP system, and click **Search**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9a7e8-138">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]支援只星號 （*） 萬用字元的使用，以搜尋資料表。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-138">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] supports the use of only the asterisk (*) wildcard character for searching tables.</span></span>  
  
3.  <span data-ttu-id="9a7e8-139">**搜尋結果**方塊會列出符合搜尋準則的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-139">The **Search results** box lists the table names that satisfy the search criteria.</span></span>  
  
     <span data-ttu-id="9a7e8-140">![DDEX 外掛程式 &#45; 在搜尋與新增資料表名稱對話方塊](../../adapters-and-accelerators/adapter-sap/media/737fc9c3-5258-4693-a2f3-5b5b8d2483e9.gif "737fc9c3-5258-4693-a2f3-5b5b8d2483e9")</span><span class="sxs-lookup"><span data-stu-id="9a7e8-140">![DDEX plug&#45;in Search and Add Tables name dialog box](../../adapters-and-accelerators/adapter-sap/media/737fc9c3-5258-4693-a2f3-5b5b8d2483e9.gif "737fc9c3-5258-4693-a2f3-5b5b8d2483e9")</span></span>  
  
4.  <span data-ttu-id="9a7e8-141">選取對應至您想要新增，然後按一下資料表的核取方塊**新增**。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-141">Select the check box corresponding to the tables you want to add and click **Add**.</span></span> <span data-ttu-id="9a7e8-142">若要選取所有資料表，請按一下**都全選**。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-142">To select all the tables, click **Select All**.</span></span> <span data-ttu-id="9a7e8-143">若要清除所有選取項目，請按一下**全部清除**。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-143">To clear all the selections, click **Clear All**.</span></span>  
  
5.  <span data-ttu-id="9a7e8-144">對話方塊會通知您所加入的表格會顯示，您在重新整理後**資料表**節點。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-144">A dialog box informs you that the added tables would be visible after you refresh the **Tables** node.</span></span> <span data-ttu-id="9a7e8-145">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-145">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="9a7e8-146">以滑鼠右鍵按一下**資料表**節點，然後選取**重新整理**。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-146">Right-click the **Tables** node and select **Refresh**.</span></span> <span data-ttu-id="9a7e8-147">選取的資料表會出現在**資料表**節點。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-147">The selected tables appear under the **Tables** node.</span></span> <span data-ttu-id="9a7e8-148">按一下資料表名稱，請參閱中的資料表屬性才能**屬性**窗格。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-148">Click a table name to see the table properties in the **Properties** pane.</span></span>  
  
7.  <span data-ttu-id="9a7e8-149">展開資料表名稱，才能查看資料表的欄位。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-149">Expand a table name to see the fields for the table.</span></span> <span data-ttu-id="9a7e8-150">按一下以查看欄位的屬性中的欄位名稱**屬性**窗格。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-150">Click a field name to see the field properties in the **Properties** pane.</span></span>  
  
### <a name="to-add-rfcs-from-an-sap-system-using-the-ddex-plug-in"></a><span data-ttu-id="9a7e8-151">若要從使用 DDEX 外掛程式的 SAP 系統加入 Rfc</span><span class="sxs-lookup"><span data-stu-id="9a7e8-151">To add RFCs from an SAP system using the DDEX plug-in</span></span>  
  
1.  <span data-ttu-id="9a7e8-152">在**伺服器總管**，以滑鼠右鍵按一下**函式模組**節點，然後按一下**搜尋與新增函式模組**。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-152">In the **Server Explorer**, right-click the **Function Modules** node and click **Search and Add Function Modules**.</span></span>  
  
2.  <span data-ttu-id="9a7e8-153">在**搜尋函式模組**文字方塊中，指定搜尋字串以搜尋 SAP 系統中的函式的模組，然後按一下**搜尋**。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-153">In the **Search function module** text box, specify a search string to search function modules in the SAP system, and click **Search**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9a7e8-154">[!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]支援只星號 （*） 萬用字元使用搜尋功能的模組。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-154">The [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] supports the use of only the asterisk (*) wildcard character for searching functional modules.</span></span>  
  
3.  <span data-ttu-id="9a7e8-155">**搜尋結果**方塊會列出符合搜尋條件的函式模組。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-155">The **Search results** box lists the function modules that satisfy the search criteria.</span></span>  
  
     <span data-ttu-id="9a7e8-156">![DDEX 外掛程式 &#45; 在搜尋與新增模組對話方塊](../../adapters-and-accelerators/adapter-sap/media/8c7f9081-80aa-4bfe-8f06-2c751758ddd0.gif "8c7f9081-80aa-4bfe-8f06-2c751758ddd0")</span><span class="sxs-lookup"><span data-stu-id="9a7e8-156">![DDEX plug&#45;in Search and Add Modules dialog box](../../adapters-and-accelerators/adapter-sap/media/8c7f9081-80aa-4bfe-8f06-2c751758ddd0.gif "8c7f9081-80aa-4bfe-8f06-2c751758ddd0")</span></span>  
  
4.  <span data-ttu-id="9a7e8-157">選取您想要新增，然後按一下函式模組對應的核取方塊**新增**。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-157">Select the check box corresponding to the function modules you want to add and click **Add**.</span></span> <span data-ttu-id="9a7e8-158">若要選取所有的模組，請按一下**全選**。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-158">To select all the modules, click **Select All**.</span></span> <span data-ttu-id="9a7e8-159">若要清除所有選取項目，請按一下**全部清除**。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-159">To clear all the selections, click **Clear All**.</span></span>  
  
5.  <span data-ttu-id="9a7e8-160">對話方塊會通知您，您在重新整理後，加入函式模組會是可見**函式模組**節點。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-160">A dialog box informs you that the added function modules would be visible after you refresh the **Function Modules** node.</span></span> <span data-ttu-id="9a7e8-161">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-161">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="9a7e8-162">以滑鼠右鍵按一下**函式模組**節點，然後選取**重新整理**。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-162">Right-click the **Function Modules** node and select **Refresh**.</span></span> <span data-ttu-id="9a7e8-163">選取的函式模組出現在**函式模組**節點。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-163">The selected function modules appear under the **Function Modules** node.</span></span> <span data-ttu-id="9a7e8-164">按一下函數模組名稱，請參閱中的屬性**屬性**窗格。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-164">Click a function module name to see the properties in the **Properties** pane.</span></span>  
  
7.  <span data-ttu-id="9a7e8-165">展開以查看節點以進行匯入、 匯出、 變更和資料表參數的函式模組名稱。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-165">Expand a function module name to see nodes for import, export, changing, and table parameters.</span></span>  
  
8.  <span data-ttu-id="9a7e8-166">展開**匯入**列出函式模組的匯入參數 節點。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-166">Expand the **Import** node to list the import parameters for the function module.</span></span> <span data-ttu-id="9a7e8-167">同樣地，依序展開**匯出**和**資料表**節點，以查看函式模組匯出和資料表的參數清單。</span><span class="sxs-lookup"><span data-stu-id="9a7e8-167">Similarly, expand the **Export** and **Tables** nodes to see the list of export and table parameters for the function module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a7e8-168">請參閱</span><span class="sxs-lookup"><span data-stu-id="9a7e8-168">See Also</span></span>  
 [<span data-ttu-id="9a7e8-169">使用 .NET Framework Data Provider for mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="9a7e8-169">Use the .NET Framework Data Provider for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/use-the-net-framework-data-provider-for-mysap-business-suite.md)