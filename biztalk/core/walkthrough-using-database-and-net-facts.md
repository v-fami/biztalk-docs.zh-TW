---
title: 逐步解說： 使用資料庫和.NET 事實 |Microsoft 文件
ms.custom: ''
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 676d6e46-d9f8-477e-979e-1ac051ad4451
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b18b9b3188ce3d9fb478c3f2d4390d167e5566a9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25976044"
---
# <a name="walkthrough-using-database-and-net-facts"></a><span data-ttu-id="347e0-102">逐步解說： 使用資料庫和.NET 事實</span><span class="sxs-lookup"><span data-stu-id="347e0-102">Walkthrough: Using Database and .NET Facts</span></span>
<span data-ttu-id="347e0-103">此逐步解說提供逐步程序，說明如何透過「商務規則編輯器」建立使用資料庫和 .NET 事實的原則。</span><span class="sxs-lookup"><span data-stu-id="347e0-103">This walkthrough provides step-by-step procedures for using the Business Rule Composer to create a policy that uses database and .NET facts.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="347e0-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="347e0-104">Prerequisites</span></span>  
 <span data-ttu-id="347e0-105">您必須設定的值**StaticSupport**為 1 或 2，然後再執行此逐步解說的登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="347e0-105">You must set the value of the **StaticSupport** registry key to 1 or 2 before performing the walkthrough.</span></span> <span data-ttu-id="347e0-106">這可讓原則叫用 .NET 類別的靜態方法，而不需用戶端判斷提示類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="347e0-106">This allows the policy to invoke the static methods of a .NET class without requiring the client to assert an instance of the class.</span></span> <span data-ttu-id="347e0-107">如需詳細資訊，請參閱[叫用類別的靜態成員](../core/invoking-static-members-of-a-class.md)。</span><span class="sxs-lookup"><span data-stu-id="347e0-107">For more information, see [Invoking Static Members of a Class](../core/invoking-static-members-of-a-class.md).</span></span>  
  
## <a name="overview-of-this-walkthrough"></a><span data-ttu-id="347e0-108">此逐步解說的概觀</span><span class="sxs-lookup"><span data-stu-id="347e0-108">Overview of This Walkthrough</span></span>  
 <span data-ttu-id="347e0-109">此逐步解說包含五個程序，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="347e0-109">This walkthrough contains five procedures, as described in the following table.</span></span>  
  
|<span data-ttu-id="347e0-110">程序標題</span><span class="sxs-lookup"><span data-stu-id="347e0-110">Procedure title</span></span>|<span data-ttu-id="347e0-111">程序說明</span><span class="sxs-lookup"><span data-stu-id="347e0-111">Procedure description</span></span>|  
|---------------------|---------------------------|  
|<span data-ttu-id="347e0-112">建立 TestDB 資料庫和 PO 資料表</span><span class="sxs-lookup"><span data-stu-id="347e0-112">To create the TestDB database and the PO table</span></span>|<span data-ttu-id="347e0-113">提供逐步指示，建立**TestDB**資料庫和**PO**資料表。</span><span class="sxs-lookup"><span data-stu-id="347e0-113">Provides step-by-step instructions for creating the **TestDB** database and the **PO** table.</span></span>|  
|<span data-ttu-id="347e0-114">建立 POUtility 元件</span><span class="sxs-lookup"><span data-stu-id="347e0-114">To create the POUtility component</span></span>|<span data-ttu-id="347e0-115">提供逐步指示，建立**POUtility**元件。</span><span class="sxs-lookup"><span data-stu-id="347e0-115">Provides step-by-step instructions for creating the **POUtility** component.</span></span>|  
|<span data-ttu-id="347e0-116">建立 ProcessPurchaseOrderDbNet 商務原則</span><span class="sxs-lookup"><span data-stu-id="347e0-116">To create the ProcessPurchaseOrderDbNet business policy</span></span>|<span data-ttu-id="347e0-117">提供逐步指示，建立**ProcessPurchaseOrderDbNet**原則。</span><span class="sxs-lookup"><span data-stu-id="347e0-117">Provides step-by-step instructions for creating the **ProcessPurchaseOrderDbNet** policy.</span></span>|  
|<span data-ttu-id="347e0-118">使用商務規則編輯器測試 ProcessPurchaseOrderDbNet 原則</span><span class="sxs-lookup"><span data-stu-id="347e0-118">To test the ProcessPurchaseOrderDbNet policy by using the Business Rule Composer</span></span>|<span data-ttu-id="347e0-119">提供逐步指示，請使用 「 商務規則編輯器 」 測試**ProcessPurchaseOrderDbNet**原則。</span><span class="sxs-lookup"><span data-stu-id="347e0-119">Provides step-by-step instructions for using the Business Rule Composer to test the **ProcessPurchaseOrderDbNet** policy.</span></span>|  
|<span data-ttu-id="347e0-120">使用 Policy.Execute 方法測試 ProcessPurchaseOrderDbNet 原則</span><span class="sxs-lookup"><span data-stu-id="347e0-120">To test the ProcessPurchaseOrderDbNet policy by using the Policy.Execute method</span></span>|<span data-ttu-id="347e0-121">提供逐步指示，測試**ProcessPurchaseOrderDbNet**原則使用**Policy.Execute**方法。</span><span class="sxs-lookup"><span data-stu-id="347e0-121">Provides step-by-step instructions for testing the **ProcessPurchaseOrderDbNet** policy by using the **Policy.Execute** method.</span></span>|  
  
### <a name="to-create-the-testdb-database-and-the-po-table"></a><span data-ttu-id="347e0-122">建立 TestDB 資料庫和 PO 資料表</span><span class="sxs-lookup"><span data-stu-id="347e0-122">To create the TestDB database and the PO table</span></span>  
  
1.  <span data-ttu-id="347e0-123">開啟 [SQL Server Management Studio]。</span><span class="sxs-lookup"><span data-stu-id="347e0-123">Open **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="347e0-124">確認伺服器名稱和驗證，然後按一下**連接**。</span><span class="sxs-lookup"><span data-stu-id="347e0-124">Verify the server name and authentication, and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="347e0-125">在左側物件總管] 視窗中，以滑鼠右鍵按一下 [電腦名稱，然後**新查詢**。</span><span class="sxs-lookup"><span data-stu-id="347e0-125">In the Object Explorer window on the left, right-click the computer name, and then click **New Query**.</span></span>  
  
4.  <span data-ttu-id="347e0-126">將下列 SQL 陳述式複製到查詢視窗中：</span><span class="sxs-lookup"><span data-stu-id="347e0-126">Copy the following SQL statements to the query window:</span></span>  
  
    ```  
    CREATE DATABASE [TestDB]  
    GO  
  
    Use TestDB  
    CREATE TABLE [dbo].[PO]([PONumber] [nvarchar](50) NOT NULL,  
    [Quantity] [int] NOT NULL,  
    [Status] [nchar](10) NULL  
    CONSTRAINT [PK_PO] PRIMARY KEY CLUSTERED ([PONumber] ASC))   
    GO  
  
    INSERT INTO PO VALUES ('PO1', 400, NULL)  
    INSERT INTO PO VALUES ('PO2', 700, NULL)  
    GO  
    ```  
  
5.  <span data-ttu-id="347e0-127">按 F5 執行 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="347e0-127">Press F5 to execute the SQL query.</span></span>  
  
6.  <span data-ttu-id="347e0-128">在物件總管] 視窗中，展開 [電腦名稱，再展開**資料庫**，然後確認**TestDB**存在。</span><span class="sxs-lookup"><span data-stu-id="347e0-128">In the Object Explorer window, expand the computer name, expand **Databases**, and then verify that **TestDB** exists.</span></span>  
  
7.  <span data-ttu-id="347e0-129">展開**TestDB**，依序展開**資料表**，然後確認**dbo。PO**存在。</span><span class="sxs-lookup"><span data-stu-id="347e0-129">Expand **TestDB**, expand **Tables**, and then verify that **dbo.PO** exists.</span></span>  
  
8.  <span data-ttu-id="347e0-130">以滑鼠右鍵按一下**dbo。PO**，然後按一下 **開啟資料表**驗證資料表中有下列的資料。</span><span class="sxs-lookup"><span data-stu-id="347e0-130">Right-click **dbo.PO**, and then click **Open Table** to verify that the following data exists in the table.</span></span>  
  
    |<span data-ttu-id="347e0-131">PONumber</span><span class="sxs-lookup"><span data-stu-id="347e0-131">PONumber</span></span>|<span data-ttu-id="347e0-132">Quantity</span><span class="sxs-lookup"><span data-stu-id="347e0-132">Quantity</span></span>|<span data-ttu-id="347e0-133">狀態</span><span class="sxs-lookup"><span data-stu-id="347e0-133">Status</span></span>|  
    |--------------|--------------|------------|  
    |<span data-ttu-id="347e0-134">PO1</span><span class="sxs-lookup"><span data-stu-id="347e0-134">PO1</span></span>|<span data-ttu-id="347e0-135">400</span><span class="sxs-lookup"><span data-stu-id="347e0-135">400</span></span>|<span data-ttu-id="347e0-136">NULL</span><span class="sxs-lookup"><span data-stu-id="347e0-136">NULL</span></span>|  
    |<span data-ttu-id="347e0-137">PO2</span><span class="sxs-lookup"><span data-stu-id="347e0-137">PO2</span></span>|<span data-ttu-id="347e0-138">700</span><span class="sxs-lookup"><span data-stu-id="347e0-138">700</span></span>|<span data-ttu-id="347e0-139">NULL</span><span class="sxs-lookup"><span data-stu-id="347e0-139">NULL</span></span>|  
  
### <a name="to-create-the-poutility-component"></a><span data-ttu-id="347e0-140">建立 POUtility 元件</span><span class="sxs-lookup"><span data-stu-id="347e0-140">To create the POUtility component</span></span>  
  
1.  <span data-ttu-id="347e0-141">啟動**Microsoft Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="347e0-141">Start **Microsoft Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="347e0-142">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="347e0-142">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="347e0-143">在**新專案**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="347e0-143">In the **New Project** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="347e0-144">使用</span><span class="sxs-lookup"><span data-stu-id="347e0-144">Use this</span></span>|<span data-ttu-id="347e0-145">動作</span><span class="sxs-lookup"><span data-stu-id="347e0-145">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="347e0-146">**專案類型**</span><span class="sxs-lookup"><span data-stu-id="347e0-146">**Project types**</span></span>|<span data-ttu-id="347e0-147">按一下**Visual C#**。</span><span class="sxs-lookup"><span data-stu-id="347e0-147">Click **Visual C#**.</span></span>|  
    |<span data-ttu-id="347e0-148">**範本**</span><span class="sxs-lookup"><span data-stu-id="347e0-148">**Templates**</span></span>|<span data-ttu-id="347e0-149">按一下**類別庫**。</span><span class="sxs-lookup"><span data-stu-id="347e0-149">Click **Class Library**.</span></span>|  
    |<span data-ttu-id="347e0-150">**名稱**</span><span class="sxs-lookup"><span data-stu-id="347e0-150">**Name**</span></span>|<span data-ttu-id="347e0-151">型別**POUtilityLib**。</span><span class="sxs-lookup"><span data-stu-id="347e0-151">Type **POUtilityLib**.</span></span>|  
    |<span data-ttu-id="347e0-152">**位置**</span><span class="sxs-lookup"><span data-stu-id="347e0-152">**Location**</span></span>|<span data-ttu-id="347e0-153">指定**C:\BRE-Walkthroughs**做為位置。</span><span class="sxs-lookup"><span data-stu-id="347e0-153">Specify **C:\BRE-Walkthroughs** as the location.</span></span>|  
    |<span data-ttu-id="347e0-154">**方案名稱**</span><span class="sxs-lookup"><span data-stu-id="347e0-154">**Solution Name**</span></span>|<span data-ttu-id="347e0-155">型別**POUtilitySol**。</span><span class="sxs-lookup"><span data-stu-id="347e0-155">Type **POUtilitySol**.</span></span>|  
    |<span data-ttu-id="347e0-156">**為方案建立目錄**</span><span class="sxs-lookup"><span data-stu-id="347e0-156">**Create directory for solution**</span></span>|<span data-ttu-id="347e0-157">選取此核取方塊以建立方案檔案的目錄。</span><span class="sxs-lookup"><span data-stu-id="347e0-157">Select this check box to create a directory for the solution files.</span></span>|  
  
4.  <span data-ttu-id="347e0-158">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="347e0-158">Click **OK**.</span></span> <span data-ttu-id="347e0-159">**POUtilityLib**專案應該會出現在 [方案總管]。</span><span class="sxs-lookup"><span data-stu-id="347e0-159">The **POUtilityLib** project should appear in Solution Explorer.</span></span> <span data-ttu-id="347e0-160">如果看不到方案總管 中，按一下**方案總管 中**上**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="347e0-160">If you do not see Solution Explorer, click **Solution Explorer** on the **View** menu.</span></span>  
  
5.  <span data-ttu-id="347e0-161">在 [屬性] 視窗中，變更名稱的檔案，請**Class1.cs**至**POUtility.cs**。</span><span class="sxs-lookup"><span data-stu-id="347e0-161">In the Properties window, change the name of the file, **Class1.cs**, to **POUtility.cs**.</span></span>  
  
6.  <span data-ttu-id="347e0-162">將下列程式碼中顯示的公用建構函式加入類別：</span><span class="sxs-lookup"><span data-stu-id="347e0-162">Add a public constructor to the class as shown in the following code:</span></span>  
  
    ```  
    public POUtility()  
    {  
    }  
    ```  
  
7.  <span data-ttu-id="347e0-163">加入名為的靜態方法 **[getmaxallowed]** 至**POUtility**類別，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="347e0-163">Add a static method named **GetMaxAllowed** to the **POUtility** class as shown in the following code:</span></span>  
  
    ```  
    public static int GetMaxAllowed()  
    {  
    return 500;  
    }   
    ```  
  
8.  <span data-ttu-id="347e0-164">啟動**Visual Studio 命令提示字元**。</span><span class="sxs-lookup"><span data-stu-id="347e0-164">Start **Visual Studio Command Prompt**.</span></span>  
  
9. <span data-ttu-id="347e0-165">將目錄變更**C:\BRE-Walkthroughs\POUtilitySol**，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="347e0-165">Change the directory to **C:\BRE-Walkthroughs\POUtilitySol**, and then execute the following command:</span></span>  
  
     <span data-ttu-id="347e0-166">**Sn-k POUtility.snk**</span><span class="sxs-lookup"><span data-stu-id="347e0-166">**Sn -k POUtility.snk**</span></span>  
  
10. <span data-ttu-id="347e0-167">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，在 [方案總管] 中，展開**屬性**，然後按兩下**AssemblyInfo.cs**。</span><span class="sxs-lookup"><span data-stu-id="347e0-167">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], in Solution Explorer, expand **Properties**, and then double-click **AssemblyInfo.cs**.</span></span>  
  
11. <span data-ttu-id="347e0-168">加入下列陳述式來**AssemblyInfo.cs**檔案結尾：</span><span class="sxs-lookup"><span data-stu-id="347e0-168">Add the following statement to the **AssemblyInfo.cs** file at the end:</span></span>  
  
    ```  
    [assembly: AssemblyKeyFile(@"C:\BRE-Walkthroughs\POUtilitySol\POUtility.snk")]  
    ```  
  
12. <span data-ttu-id="347e0-169">在方案總管] 視窗中，以滑鼠右鍵按一下**POUtilityLib**，然後按一下 [**建置**。</span><span class="sxs-lookup"><span data-stu-id="347e0-169">In the Solution Explorer window, right-click **POUtilityLib**, and then click **Build**.</span></span>  
  
13. <span data-ttu-id="347e0-170">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]命令提示字元中，將目錄變更**C:\BRE-Walkthroughs\POUtilitySol\POUtilityLib\Bin\Debug**，然後執行下列命令，在 GAC （全域註冊 POUtility 元件組件快取）。</span><span class="sxs-lookup"><span data-stu-id="347e0-170">At the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Command Prompt, change the directory to **C:\BRE-Walkthroughs\POUtilitySol\POUtilityLib\Bin\Debug**, and then execute the following command to register the POUtility component with the GAC (global assembly cache).</span></span> <span data-ttu-id="347e0-171">如果您沒有開啟，請依照下列步驟 8 以開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="347e0-171">If you do not have the command prompt open, follow step 8 to open it.</span></span>  
  
     <span data-ttu-id="347e0-172">**Gacutil-i POUtilityLib.dll**</span><span class="sxs-lookup"><span data-stu-id="347e0-172">**Gacutil -i POUtilityLib.dll**</span></span>  
  
### <a name="to-create-the-processpurchaseorderdbnet-business-policy"></a><span data-ttu-id="347e0-173">建立 ProcessPurchaseOrderDbNet 商務原則</span><span class="sxs-lookup"><span data-stu-id="347e0-173">To create the ProcessPurchaseOrderDbNet business policy</span></span>  
  
1.  <span data-ttu-id="347e0-174">在**啟動**功能表中，開啟**商務規則編輯器 」**。</span><span class="sxs-lookup"><span data-stu-id="347e0-174">On the **Start** menu, open **Business Rule Composer**.</span></span> <span data-ttu-id="347e0-175">如果已經開啟 [商務規則編輯器]，請按 F5 重新整理。</span><span class="sxs-lookup"><span data-stu-id="347e0-175">If you have the Business Rule Composer already open, press F5 to refresh it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="347e0-176">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="347e0-176">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="347e0-177">若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="347e0-177">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="347e0-178">在 [事實總管] 視窗中，按一下**資料庫**。</span><span class="sxs-lookup"><span data-stu-id="347e0-178">In the Facts Explorer window, click **Databases**.</span></span>  
  
3.  <span data-ttu-id="347e0-179">以滑鼠右鍵按一下**伺服器**，然後按一下 **瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="347e0-179">Right-click **Servers**, and then click **Browse**.</span></span>  
  
4.  <span data-ttu-id="347e0-180">驗證的伺服器和驗證資訊，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="347e0-180">Verify the server and authentication information, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="347e0-181">展開**TestDB**，然後展開**PO**。</span><span class="sxs-lookup"><span data-stu-id="347e0-181">Expand **TestDB**, and then expand **PO**.</span></span>  
  
6.  <span data-ttu-id="347e0-182">在 [事實總管] 視窗中，按一下 **.NET 類別**。</span><span class="sxs-lookup"><span data-stu-id="347e0-182">In the Facts Explorer window, click **.NET Classes**.</span></span>  
  
7.  <span data-ttu-id="347e0-183">以滑鼠右鍵按一下 **。NETAssemblies**，然後按一下 **瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="347e0-183">Right-click **.NETAssemblies**, and then click **Browse**.</span></span>  
  
8.  <span data-ttu-id="347e0-184">選取**POUtility**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="347e0-184">Select **POUtility**, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="347e0-185">展開**Class1**。</span><span class="sxs-lookup"><span data-stu-id="347e0-185">Expand **Class1**.</span></span>  
  
10. <span data-ttu-id="347e0-186">在原則總管] 視窗中，以滑鼠右鍵按一下**原則**，然後按一下 [**新增原則**。</span><span class="sxs-lookup"><span data-stu-id="347e0-186">In the Policy Explorer window, right-click **Policies**, and then click **Add New Policy**.</span></span>  
  
11. <span data-ttu-id="347e0-187">從原則的名稱變更 **[policy1]** 至**ProcessPurchaseOrderDbNet**然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="347e0-187">Change the name of the policy from **Policy1** to **ProcessPurchaseOrderDbNet** and then press ENTER.</span></span> <span data-ttu-id="347e0-188">您也可以在 [屬性] 視窗中變更原則的名稱。</span><span class="sxs-lookup"><span data-stu-id="347e0-188">You can also change the name of the policy in the Properties window.</span></span>  
  
12. <span data-ttu-id="347e0-189">以滑鼠右鍵按一下**1.0 版**，然後按一下  **AddNewRule**。</span><span class="sxs-lookup"><span data-stu-id="347e0-189">Right-click **Version 1.0**, and then click **AddNewRule**.</span></span>  
  
13. <span data-ttu-id="347e0-190">變更規則的名稱**Rule1**至**ApprovalRule**然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="347e0-190">Change the name of the rule from **Rule1** to **ApprovalRule** and then press ENTER.</span></span> <span data-ttu-id="347e0-191">您也可以在 [屬性] 視窗中變更規則的名稱。</span><span class="sxs-lookup"><span data-stu-id="347e0-191">You can also change the name of the rule in the Properties window.</span></span>  
  
14. <span data-ttu-id="347e0-192">在 IF 窗格 （上方） 右邊，以滑鼠右鍵按一下**條件**，按一下 **述詞**，然後按一下 **小於或等於**。</span><span class="sxs-lookup"><span data-stu-id="347e0-192">In the IF pane (top) on the right, right-click **Conditions**, click **Predicates**, and then click **LessThanEqual**.</span></span>  
  
15. <span data-ttu-id="347e0-193">在 [事實總管] 視窗中，按一下**資料庫**。</span><span class="sxs-lookup"><span data-stu-id="347e0-193">In the Facts Explorer window, click **Databases**.</span></span>  
  
16. <span data-ttu-id="347e0-194">拖曳**數量**節點從 [事實總管] 視窗**引數 1** [IF] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="347e0-194">Drag the **Quantity** node from the Facts Explorer window to **argument1** in the IF pane.</span></span>  
  
17. <span data-ttu-id="347e0-195">在 [事實總管] 視窗中，按一下 **.NET 類別**。</span><span class="sxs-lookup"><span data-stu-id="347e0-195">In the Facts Explorer window, click **.NET Classes**.</span></span>  
  
18. <span data-ttu-id="347e0-196">拖曳 **[getmaxallowed]** 節點從 [事實總管] 視窗**引數 2** [IF] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="347e0-196">Drag **GetMaxAllowed** node from the Facts Explorer window to **argument2** in the IF pane.</span></span>  
  
19. <span data-ttu-id="347e0-197">在 [事實總管] 視窗中，按一下**資料庫**。</span><span class="sxs-lookup"><span data-stu-id="347e0-197">In the Facts Explorer window, click **Databases**.</span></span>  
  
20. <span data-ttu-id="347e0-198">拖曳**狀態**節點從 事實總管 視窗右下角的 商務規則編輯器 THEN 窗格。</span><span class="sxs-lookup"><span data-stu-id="347e0-198">Drag the **Status** node from the Facts Explorer window to the THEN pane at the bottom right of the Business Rule Composer.</span></span>  
  
21. <span data-ttu-id="347e0-199">在 [THEN] 窗格中，按一下**\<輸入值\>** ，然後輸入**Approved**。</span><span class="sxs-lookup"><span data-stu-id="347e0-199">In the THEN pane, click **\<Enter a value\>** and then type **Approved**.</span></span>  
  
22. <span data-ttu-id="347e0-200">在事實總管 視窗中，以滑鼠右鍵按一下**1.0 版**中**ProcessPurchaseOrderDbNet**，然後按一下  **AddNewRule**。</span><span class="sxs-lookup"><span data-stu-id="347e0-200">In the Facts Explorer window, right-click **Version 1.0** in **ProcessPurchaseOrderDbNet**, and then click **AddNewRule**.</span></span>  
  
23. <span data-ttu-id="347e0-201">變更規則的名稱**Rule1**至**DeniedRule**然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="347e0-201">Change the name of the rule from **Rule1** to **DeniedRule** and then press ENTER.</span></span> <span data-ttu-id="347e0-202">您也可以在 [屬性] 視窗中變更規則的名稱。</span><span class="sxs-lookup"><span data-stu-id="347e0-202">You can also change the name of the rule in the Properties window.</span></span>  
  
24. <span data-ttu-id="347e0-203">在 IF 窗格 （上方） 右邊，以滑鼠右鍵按一下**條件**，按一下 **述詞**，然後按一下  **GreaterThan**。</span><span class="sxs-lookup"><span data-stu-id="347e0-203">In the IF pane (top) on the right, right-click **Conditions**, click **Predicates**, and then click **GreaterThan**.</span></span>  
  
25. <span data-ttu-id="347e0-204">在 [事實總管] 視窗中，按一下**資料庫**。</span><span class="sxs-lookup"><span data-stu-id="347e0-204">In the Facts Explorer window, click **Databases**.</span></span>  
  
26. <span data-ttu-id="347e0-205">拖曳**數量**節點從 [事實總管] 視窗**引數 1** [IF] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="347e0-205">Drag the **Quantity** node from the Facts Explorer window to **argument1** in the IF pane.</span></span>  
  
27. <span data-ttu-id="347e0-206">在 [事實總管] 視窗中，按一下 **.NET 類別**。</span><span class="sxs-lookup"><span data-stu-id="347e0-206">In the Facts Explorer window, click **.NET Classes**.</span></span>  
  
28. <span data-ttu-id="347e0-207">拖曳 **[getmaxallowed]** 節點從 [事實總管] 視窗**引數 2** [IF] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="347e0-207">Drag the **GetMaxAllowed** node from the Facts Explorer window to **argument2** in the IF pane.</span></span>  
  
29. <span data-ttu-id="347e0-208">在 [事實總管] 視窗中，按一下**資料庫**。</span><span class="sxs-lookup"><span data-stu-id="347e0-208">In the Facts Explorer window, click **Databases**.</span></span>  
  
30. <span data-ttu-id="347e0-209">拖曳**狀態**節點從 事實總管 視窗右下角的 商務規則編輯器 THEN 窗格。</span><span class="sxs-lookup"><span data-stu-id="347e0-209">Drag the **Status** node from the Facts Explorer window to the THEN pane at the bottom right of the Business Rule Composer.</span></span>  
  
31. <span data-ttu-id="347e0-210">在 [THEN] 窗格中，按一下**\<輸入值\>** ，然後輸入**拒絕**。</span><span class="sxs-lookup"><span data-stu-id="347e0-210">In the THEN pane, click **\<Enter a value\>** and then type **Denied**.</span></span>  
  
32. <span data-ttu-id="347e0-211">在原則總管] 視窗中，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下 [**儲存**。</span><span class="sxs-lookup"><span data-stu-id="347e0-211">In the Policy Explorer window, right-click **Version 1.0 (not saved)**, and then click **Save**.</span></span>  
  
### <a name="to-test-the-processpurchaseorderdbnet-policy-by-using-the-business-rule-composer"></a><span data-ttu-id="347e0-212">使用商務規則編輯器測試 ProcessPurchaseOrderDbNet 原則</span><span class="sxs-lookup"><span data-stu-id="347e0-212">To test the ProcessPurchaseOrderDbNet policy by using the Business Rule Composer</span></span>  
  
1.  <span data-ttu-id="347e0-213">在**啟動**功能表中，開啟**商務規則編輯器 」**。</span><span class="sxs-lookup"><span data-stu-id="347e0-213">On the **Start** menu, open **Business Rule Composer**.</span></span> <span data-ttu-id="347e0-214">如果已經開啟 [商務規則編輯器]，請按 F5 重新整理。</span><span class="sxs-lookup"><span data-stu-id="347e0-214">If you have the Business Rule Composer already open, press F5 to refresh it.</span></span>  
  
2.  <span data-ttu-id="347e0-215">在 原則總管 視窗中，依序展開**原則**，依序展開**ProcessPurchaseOrderDbNet**，以滑鼠右鍵按一下**1.0 版**，然後按一下 **測試原則**.</span><span class="sxs-lookup"><span data-stu-id="347e0-215">In the Policy Explorer window, expand **Policies**, expand **ProcessPurchaseOrderDbNet**, right-click **Version 1.0**, and then click **Test Policy**.</span></span>  
  
3.  <span data-ttu-id="347e0-216">按一下**testdb: Po （資料連線）**，然後按一下 **新增執行個體**。</span><span class="sxs-lookup"><span data-stu-id="347e0-216">Click **TestDB:PO (Data Connection)**, and then click **Add Instance**.</span></span>  
  
4.  <span data-ttu-id="347e0-217">在**連接到 SQL Server**對話方塊中，確認伺服器名稱和驗證資訊，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="347e0-217">In the **Connect to SQL Server** dialog box, verify the server name and authentication information, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="347e0-218">在**選取繫結**對話方塊方塊中，展開  **TestDB**，按一下**PO**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="347e0-218">In the **Select Binding** dialog box, expand **TestDB**, click **PO**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="347e0-219">按一下**測試**。</span><span class="sxs-lookup"><span data-stu-id="347e0-219">Click **Test**.</span></span>  
  
7.  <span data-ttu-id="347e0-220">在 [輸出] 視窗中，確認同時**ApprovalRule**和**DeniedRule**會引發。</span><span class="sxs-lookup"><span data-stu-id="347e0-220">In the Output window, verify that both the **ApprovalRule** and the **DeniedRule** are fired.</span></span>  
  
8.  <span data-ttu-id="347e0-221">在 SQL Server Management Studio，以滑鼠右鍵按一下**dbo。PO**，然後按一下 **開啟資料表**。</span><span class="sxs-lookup"><span data-stu-id="347e0-221">In SQL Server Management Studio, right-click **dbo.PO**, and then click **Open Table**.</span></span>  
  
9. <span data-ttu-id="347e0-222">確認值**狀態**欄位設定為**Approved**第一筆記錄。</span><span class="sxs-lookup"><span data-stu-id="347e0-222">Verify that the value of the **Status** field is set to **Approved** for the first record.</span></span>  
  
10. <span data-ttu-id="347e0-223">確認值**狀態**欄位設定為**拒絕**第二個記錄。</span><span class="sxs-lookup"><span data-stu-id="347e0-223">Verify that the value of the **Status** field is set to **Denied** for the second record.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="347e0-224">如果您仍然看到的值**狀態**欄位為 NULL，以滑鼠右鍵按一下包含資料的清單，然後按一下**執行 SQL**，會重新整理檢視。</span><span class="sxs-lookup"><span data-stu-id="347e0-224">If you still see the value of the **Status** field as NULL, right-click the list containing the data, and then click **Execute SQL**, which refreshes the view.</span></span>  
  
11. <span data-ttu-id="347e0-225">保持 SQL Server Management Studio 開啟。</span><span class="sxs-lookup"><span data-stu-id="347e0-225">Keep SQL Server Management Studio open.</span></span>  
  
### <a name="to-test-the-processpurchaseorderdbnet-policy-by-using-the-policyexecute-method"></a><span data-ttu-id="347e0-226">使用 Policy.Execute 方法測試 ProcessPurchaseOrderDbNet 原則</span><span class="sxs-lookup"><span data-stu-id="347e0-226">To test the ProcessPurchaseOrderDbNet policy by using the Policy.Execute method</span></span>  
  
1.  <span data-ttu-id="347e0-227">啟動**Microsoft Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="347e0-227">Start **Microsoft Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="347e0-228">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="347e0-228">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="347e0-229">在**新專案**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="347e0-229">In the **New Project** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="347e0-230">使用</span><span class="sxs-lookup"><span data-stu-id="347e0-230">Use this</span></span>|<span data-ttu-id="347e0-231">動作</span><span class="sxs-lookup"><span data-stu-id="347e0-231">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="347e0-232">**專案類型**</span><span class="sxs-lookup"><span data-stu-id="347e0-232">**Project types**</span></span>|<span data-ttu-id="347e0-233">按一下**Visual C#**。</span><span class="sxs-lookup"><span data-stu-id="347e0-233">Click **Visual C#**.</span></span>|  
    |<span data-ttu-id="347e0-234">**範本**</span><span class="sxs-lookup"><span data-stu-id="347e0-234">**Templates**</span></span>|<span data-ttu-id="347e0-235">按一下**主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="347e0-235">Click **Console Application**.</span></span>|  
    |<span data-ttu-id="347e0-236">**名稱**</span><span class="sxs-lookup"><span data-stu-id="347e0-236">**Name**</span></span>|<span data-ttu-id="347e0-237">型別**TestProcessPODbNet**。</span><span class="sxs-lookup"><span data-stu-id="347e0-237">Type **TestProcessPODbNet**.</span></span>|  
    |<span data-ttu-id="347e0-238">**位置**</span><span class="sxs-lookup"><span data-stu-id="347e0-238">**Location**</span></span>|<span data-ttu-id="347e0-239">指定**C:\BRE-Walkthroughs**做為位置。</span><span class="sxs-lookup"><span data-stu-id="347e0-239">Specify **C:\BRE-Walkthroughs** as the location.</span></span>|  
    |<span data-ttu-id="347e0-240">**方案名稱**</span><span class="sxs-lookup"><span data-stu-id="347e0-240">**Solution Name**</span></span>|<span data-ttu-id="347e0-241">型別**TestProcessPODbNetSol**。</span><span class="sxs-lookup"><span data-stu-id="347e0-241">Type **TestProcessPODbNetSol**.</span></span>|  
    |<span data-ttu-id="347e0-242">**為方案建立目錄**</span><span class="sxs-lookup"><span data-stu-id="347e0-242">**Create directory for solution**</span></span>|<span data-ttu-id="347e0-243">選取此核取方塊以建立方案檔案的目錄。</span><span class="sxs-lookup"><span data-stu-id="347e0-243">Select this check box to create a directory for the solution files.</span></span>|  
  
4.  <span data-ttu-id="347e0-244">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="347e0-244">Click **OK**.</span></span> <span data-ttu-id="347e0-245">**TestProcessPODbNet**專案應該會出現在 [方案總管]。</span><span class="sxs-lookup"><span data-stu-id="347e0-245">The **TestProcessPODbNet** project should appear in Solution Explorer.</span></span> <span data-ttu-id="347e0-246">如果看不到方案總管 中，按一下**方案總管 中**上**檢視**功能表。</span><span class="sxs-lookup"><span data-stu-id="347e0-246">If you do not see Solution Explorer, click **Solution Explorer** on the **View** menu.</span></span>  
  
5.  <span data-ttu-id="347e0-247">在 方案總管 中，以滑鼠右鍵按一下**參考**，然後按一下 **加入參考**。</span><span class="sxs-lookup"><span data-stu-id="347e0-247">In Solution Explorer, right-click **References**, and then click **Add Reference**.</span></span>  
  
6.  <span data-ttu-id="347e0-248">按一下**瀏覽**，瀏覽至**\Program Files\Common Files\Microsoft BizTalk**，然後按兩下**Microsoft.RuleEngine.dll**。</span><span class="sxs-lookup"><span data-stu-id="347e0-248">Click **Browse**, browse to **\Program Files\Common Files\Microsoft BizTalk**, and then double-click **Microsoft.RuleEngine.dll**.</span></span>  
  
7.  <span data-ttu-id="347e0-249">將下列程式碼加入至頂端**Program.cs**檔案的現有`using`陳述式：</span><span class="sxs-lookup"><span data-stu-id="347e0-249">Add the following code to the top of the **Program.cs** file after the existing `using` statements:</span></span>  
  
    ```  
    //To use the SQLConnection class  
    using System.Data.SqlClient;  
  
    //To use the Policy and DataConnection classes  
    using Microsoft.RuleEngine;  
    ```  
  
8.  <span data-ttu-id="347e0-250">將下列程式碼加入**Main**函式來建立並開啟**SQLConnection**物件：</span><span class="sxs-lookup"><span data-stu-id="347e0-250">Add the following code to the **Main** function to create and open a **SQLConnection** object:</span></span>  
  
    ```  
    SqlConnection cn = new SqlConnection("Data Source=(local);Initial Catalog=TestDB;Integrated Security=SSPI");  
    cn.Open();  
    ```  
  
9. <span data-ttu-id="347e0-251">將下列程式碼加入**Main**函式來建立結尾**DataConnection**物件根據**SQLConnection**您在上一個步驟中建立的物件：</span><span class="sxs-lookup"><span data-stu-id="347e0-251">Add the following code to the **Main** function at the end to create a **DataConnection** object based on the **SQLConnection** object you created in the previous step:</span></span>  
  
    ```  
    DataConnection dc = new DataConnection("TestDB", "PO", cn);  
    ```  
  
10. <span data-ttu-id="347e0-252">將下列程式碼加入**Main**函式來建立結尾**原則**物件，並執行原則：</span><span class="sxs-lookup"><span data-stu-id="347e0-252">Add the following code to the **Main** function at the end to create a **Policy** object and execute the policy:</span></span>  
  
    ```  
    Policy policy = new Policy("ProcessPurchaseOrderDbNet");  
    policy.Execute(dc);  
    ```  
  
11. <span data-ttu-id="347e0-253">將下列程式碼加入**Main**函式結尾，更新資料庫：</span><span class="sxs-lookup"><span data-stu-id="347e0-253">Add the following code to the **Main** function at the end to update the database:</span></span>  
  
    ```  
    dc.Update();  
    ```  
  
12. <span data-ttu-id="347e0-254">將下列程式碼加入**Main**函式結尾，關閉資料庫的連接：</span><span class="sxs-lookup"><span data-stu-id="347e0-254">Add the following code to the **Main** function at the end to close the connection to the database:</span></span>  
  
    ```  
    cn.Close();  
    ```  
  
13. <span data-ttu-id="347e0-255">加入 try catch 區塊來攔截任何例外狀況中產生**Main**方法。</span><span class="sxs-lookup"><span data-stu-id="347e0-255">Add a try-catch block to catch any exception generated in the **Main** method.</span></span>  
  
14. <span data-ttu-id="347e0-256">確認的完整程式碼**Main**函式是下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="347e0-256">Verify that the complete code for the **Main** function is as shown in the following code:</span></span>  
  
    ```  
    try  
    {  
    SqlConnection cn = new SqlConnection("Data Source=(local);Initial Catalog=TestDB;Integrated Security=SSPI");  
    cn.Open();  
    DataConnection dc = new DataConnection("TestDB", "PO", cn);  
    Policy policy = new Policy("ProcessPurchaseOrderDbNet");  
    policy.Execute(dc);  
    dc.Update();  
    cn.Close();  
    }  
    catch (Exception ex)  
    {  
    Console.WriteLine(ex.Message);  
    }  
    ```  
  
15. <span data-ttu-id="347e0-257">在**建置**功能表上，按一下 **建置 TestProcessPODbNet**。</span><span class="sxs-lookup"><span data-stu-id="347e0-257">On the **Build** menu, click **Build TestProcessPODbNet**.</span></span>  
  
16. <span data-ttu-id="347e0-258">在 「 商務規則編輯器 」 中，依序展開**原則**，依序展開**ProcessPurchaseOrderDbNet**，以滑鼠右鍵按一下**1.0 版**，然後按一下 **發行**.</span><span class="sxs-lookup"><span data-stu-id="347e0-258">In the Business Rule Composer, expand **Policies**, expand **ProcessPurchaseOrderDbNet**, right-click **Version 1.0**, and then click **Publish**.</span></span>  
  
17. <span data-ttu-id="347e0-259">以滑鼠右鍵按一下**1.0 版-已發佈**，然後按一下 **部署**。</span><span class="sxs-lookup"><span data-stu-id="347e0-259">Right-click **Version 1.0 - Published**, and then click **Deploy**.</span></span>  
  
18. <span data-ttu-id="347e0-260">在 SQL Server Management Studio，將值**狀態**欄位設為**NULL** PO 記錄。</span><span class="sxs-lookup"><span data-stu-id="347e0-260">In SQL Server Management Studio, set the value of the **Status** field to **NULL** for both the PO records.</span></span>  
  
19. <span data-ttu-id="347e0-261">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，按 CTRL + F5 執行**TestProcessPODbNet**應用程式。</span><span class="sxs-lookup"><span data-stu-id="347e0-261">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], Press CTRL+F5 to execute the **TestProcessPODbNet** application.</span></span>  
  
20. <span data-ttu-id="347e0-262">按任意鍵關閉命令提示字元視窗。</span><span class="sxs-lookup"><span data-stu-id="347e0-262">Press any key to close the command prompt window.</span></span>  
  
21. <span data-ttu-id="347e0-263">在 SQL Server Management Studio，具有 PO 記錄的資料表上按一下滑鼠右鍵，然後按一下 **執行 SQL**。</span><span class="sxs-lookup"><span data-stu-id="347e0-263">In SQL Server Management Studio, right-click the table with PO records, and then click **Execute SQL**.</span></span>  
  
22. <span data-ttu-id="347e0-264">確認值**狀態**欄位設定為**Approved**第一筆記錄。</span><span class="sxs-lookup"><span data-stu-id="347e0-264">Verify that the value of the **Status** field is set to **Approved** for the first record.</span></span>  
  
23. <span data-ttu-id="347e0-265">確認值**狀態**欄位設定為**拒絕**第二個記錄。</span><span class="sxs-lookup"><span data-stu-id="347e0-265">Verify that the value of the **Status** field is set to **Denied** for the second record.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="347e0-266">註解</span><span class="sxs-lookup"><span data-stu-id="347e0-266">Comments</span></span>  
  
-   <span data-ttu-id="347e0-267">如果原則使用 .NET 類別的非靜態方法，您必須使用事實建立者元件，判斷提示 .NET 類別的執行個體，以透過「商務規則編輯器」測試原則。</span><span class="sxs-lookup"><span data-stu-id="347e0-267">If a policy uses the non-static methods of a .NET class, you need to use a fact creator component that asserts an instance of the .NET class to test the policy by using the Business Rule Composer.</span></span>  
  
-   <span data-ttu-id="347e0-268">務必記住 「 商務規則編輯器 」 建立的執行個體**DataConnection**物件，並判斷提示它至規則引擎工作記憶體會自動為您。</span><span class="sxs-lookup"><span data-stu-id="347e0-268">It is very important to remember that the Business Rule Composer creates an instance of the **DataConnection** object and asserts it into the working memory of the rule engine automatically for you.</span></span> <span data-ttu-id="347e0-269">不過，當您叫用用戶端 （不論 BizTalk 或非 BizTalk） 應用程式，從原則時**DataConnection**物件未為您自動建立。</span><span class="sxs-lookup"><span data-stu-id="347e0-269">However, when you invoke the policy from a client (BizTalk or non-BizTalk) application, the **DataConnection** object is not created automatically for you.</span></span> <span data-ttu-id="347e0-270">用戶端應該建立**DataConnection**物件，並將它做為參數或事實傳遞至規則引擎來執行原則。</span><span class="sxs-lookup"><span data-stu-id="347e0-270">The client should create a **DataConnection** object and pass it as a parameter or fact to the rule engine to execute the policy.</span></span>  
  
-   <span data-ttu-id="347e0-271">您可以使用**DebugTrackingInterceptor**類別，追蹤原則執行詳細資料。</span><span class="sxs-lookup"><span data-stu-id="347e0-271">You can use the **DebugTrackingInterceptor** class to track the policy execution details.</span></span> <span data-ttu-id="347e0-272">下列範例程式碼示範如何建立執行個體**DebugTrackingInterceptor**類別，並執行原則時使用它：</span><span class="sxs-lookup"><span data-stu-id="347e0-272">The following sample code shows how to create an instance of the **DebugTrackingInterceptor** class, and use it when executing the policy:</span></span>  
  
    ```  
    DebugTrackingInterceptor dti = new DebugTrackingInterceptor("c:\\Trace.txt");  
    policy.Execute(dc, dti);  
    ```  
  
-   <span data-ttu-id="347e0-273">您可以使用**SqlTransaction**類別，以更新資料庫。 請從**ProcessPODbNet**原則以交易方式。</span><span class="sxs-lookup"><span data-stu-id="347e0-273">You can use the **SqlTransaction** class to update the database from the **ProcessPODbNet** policy in a transactional manner.</span></span> <span data-ttu-id="347e0-274">下列程式碼示範如何開始交易、 當做參數傳遞的交易**DataConnection**物件，以及認可資料庫變更。</span><span class="sxs-lookup"><span data-stu-id="347e0-274">The following code shows how to begin a transaction, pass the transaction as a parameter to the **DataConnection** object, and commit the database changes.</span></span> <span data-ttu-id="347e0-275">如需詳細資訊，請參閱[交易支援](../core/transaction-support.md)。</span><span class="sxs-lookup"><span data-stu-id="347e0-275">For more information, see [Transaction Support](../core/transaction-support.md).</span></span>  
  
    ```  
    SqlConnection cn = new SqlConnection("Data Source=(local);Initial Catalog=TestDB;Integrated Security=SSPI");  
    cn.Open();  
    //Begin the transaction  
    SqlTransaction  tn = cn.BeginTransaction();  
    //Pass the transaction object to the DataConnection constructor  
    DataConnection dc = new DataConnection("TestDB", "PO", cn, tn);  
    Policy policy = new Policy("ProcessPurchaseOrderDbNet");  
    DebugTrackingInterceptor dti = new DebugTrackingInterceptor("c:\\Trace.txt");  
    policy.Execute(dc, dti);  
    dc.Update();  
    //Commit the database transaction  
    tn.Commit();  
    cn.Close();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="347e0-276">請參閱</span><span class="sxs-lookup"><span data-stu-id="347e0-276">See Also</span></span>  
 [<span data-ttu-id="347e0-277">選取事實</span><span class="sxs-lookup"><span data-stu-id="347e0-277">Selecting Facts</span></span>](../core/selecting-facts.md)