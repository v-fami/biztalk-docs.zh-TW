---
title: 逐步解說： 使用資料庫和.NET 事實 |Microsoft Docs
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
ms.openlocfilehash: 94eb3f34a529950a7344f6cc4579aa6f6909f813
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966951"
---
# <a name="walkthrough-using-database-and-net-facts"></a>逐步解說： 使用資料庫和.NET 事實
此逐步解說提供逐步程序，說明如何透過「商務規則編輯器」建立使用資料庫和 .NET 事實的原則。  

## <a name="prerequisites"></a>必要條件  
 您必須設定的值**StaticSupport**登錄機碼設為 1 或 2，然後再執行此逐步解說。 這可讓原則叫用 .NET 類別的靜態方法，而不需用戶端判斷提示類別的執行個體。 如需詳細資訊，請參閱 <<c0> [ 叫用類別的靜態成員](../core/invoking-static-members-of-a-class.md)。  

## <a name="overview-of-this-walkthrough"></a>此逐步解說的概觀  
 此逐步解說包含五個程序，如下表所示。  

|程序標題|程序說明|  
|---------------------|---------------------------|  
|建立 TestDB 資料庫和 PO 資料表|提供逐步指示，建立**TestDB**資料庫並**PO**資料表。|  
|建立 POUtility 元件|提供逐步指示，建立**POUtility**元件。|  
|建立 ProcessPurchaseOrderDbNet 商務原則|提供逐步指示，建立**ProcessPurchaseOrderDbNet**原則。|  
|使用商務規則編輯器測試 ProcessPurchaseOrderDbNet 原則|提供逐步指示，使用 「 商務規則編輯器 」 來測試**ProcessPurchaseOrderDbNet**原則。|  
|使用 Policy.Execute 方法測試 ProcessPurchaseOrderDbNet 原則|提供用於測試的逐步指示**ProcessPurchaseOrderDbNet**使用的原則**Policy.Execute**方法。|  

### <a name="to-create-the-testdb-database-and-the-po-table"></a>建立 TestDB 資料庫和 PO 資料表  

1.  開啟 [SQL Server Management Studio]。  

2.  確認伺服器名稱和驗證，然後按一下**Connect**。  

3.  在左側的 物件總管 視窗，以滑鼠右鍵按一下 電腦名稱，然後**新的查詢**。  

4.  將下列 SQL 陳述式複製到查詢視窗中：  

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

5.  按 F5 執行 SQL 查詢。  

6.  在 物件總管 視窗中，展開 電腦名稱，展開**資料庫**，然後確認**TestDB**存在。  

7.  依序展開**TestDB**，展開**資料表**，然後確認**dbo。PO**存在。  

8.  以滑鼠右鍵按一下**dbo。PO**，然後按一下**開啟資料表**來驗證資料表中有下列的資料。  

    |PONumber|Quantity|[狀態]|  
    |--------------|--------------|------------|  
    |PO1|400|NULL|  
    |PO2|700|NULL|  

### <a name="to-create-the-poutility-component"></a>建立 POUtility 元件  

1. 開始**Microsoft Visual Studio**。  

2. 在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。  

3. 在 **新的專案**對話方塊方塊中，執行下列動作：  


   |             使用              |                             以進行此動作                              |
   |-----------------------------------|---------------------------------------------------------------------|
   |         **專案類型**         |                        按一下  **Visual C#**。                         |
   |           **範本**           |                      按一下 **類別庫**。                       |
   |             **名稱**              |                       型別**POUtilityLib**。                        |
   |           **位置**            |          指定**C:\BRE-Walkthroughs**做為位置。           |
   |         **方案名稱**         |                       型別**POUtilitySol**。                        |
   | **為解決方案建立目錄** | 選取此核取方塊以建立方案檔案的目錄。 |


4. 按一下 [確定] 。 **POUtilityLib**專案應該會出現在 [方案總管] 中。 如果看不到方案總管 中，按一下**方案總管**上**檢視**功能表。  

5. 在 [屬性] 視窗中，變更名稱的檔案，請**Class1.cs**至**POUtility.cs**。  

6. 將下列程式碼中顯示的公用建構函式加入類別：  

   ```  
   public POUtility()  
   {  
   }  
   ```  

7. 新增名為的靜態方法**GetMaxAllowed**要**POUtility**類別，如下列程式碼所示：  

   ```  
   public static int GetMaxAllowed()  
   {  
   return 500;  
   }   
   ```  

8. 開始**Visual Studio 命令提示字元**。  

9. 將目錄變更**C:\BRE-Walkthroughs\POUtilitySol**，然後執行下列命令：  

     **Sn-k POUtility.snk**  

10. 在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，在 [方案總管] 中，展開**屬性**，然後按兩下**AssemblyInfo.cs**。  

11. 新增下列陳述式**AssemblyInfo.cs**結尾的檔案：  

    ```  
    [assembly: AssemblyKeyFile(@"C:\BRE-Walkthroughs\POUtilitySol\POUtility.snk")]  
    ```  

12. 在 [方案總管] 視窗中，以滑鼠右鍵按一下**POUtilityLib**，然後按一下**建置**。  

13. 在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]命令提示字元，變更目錄至以下**C:\BRE-Walkthroughs\POUtilitySol\POUtilityLib\Bin\Debug**，然後執行下列命令，以在 GAC （全域註冊 POUtility 元件組件快取）。 如果您沒有開啟，請依照下列步驟 8，開啟命令提示字元。  

     **Gacutil-i POUtilityLib.dll**  

### <a name="to-create-the-processpurchaseorderdbnet-business-policy"></a>建立 ProcessPurchaseOrderDbNet 商務原則  

1.  在 **開始**功能表中，開啟**商務規則編輯器 」**。 如果已經開啟 [商務規則編輯器]，請按 F5 重新整理。  

    > [!NOTE]
    >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。 若要這樣做，以滑鼠右鍵按一下 應用程式，然後按**系統管理員身分執行**。  

2.  在 [事實總管] 視窗中，按一下**資料庫**。  

3.  以滑鼠右鍵按一下**伺服器**，然後按一下**瀏覽**。  

4.  驗證的伺服器和驗證資訊，然後再按一下**確定**。  

5.  依序展開**TestDB**，然後展開**PO**。  

6.  在 [事實總管] 視窗中，按一下 **.NET 類別**。  

7.  以滑鼠右鍵按一下 **。NETAssemblies**，然後按一下**瀏覽**。  

8.  選取  **POUtility**，然後按一下**確定**。  

9. 依序展開**Class1**。  

10. 在 [原則總管] 視窗中，以滑鼠右鍵按一下**原則**，然後按一下**新增新的原則**。  

11. 變更的原則名稱**Policy1**要**ProcessPurchaseOrderDbNet**然後按 ENTER 鍵。 您也可以在 [屬性] 視窗中變更原則的名稱。  

12. 以滑鼠右鍵按一下**1.0 版**，然後按一下**AddNewRule**。  

13. 變更規則的名稱**Rule1**要**ApprovalRule**然後按 ENTER 鍵。 您也可以在 [屬性] 視窗中變更規則的名稱。  

14. 在 [IF] 窗格 （上方） 右邊，以滑鼠右鍵按一下**條件**，按一下**述詞**，然後按一下**小於或等於**。  

15. 在 [事實總管] 視窗中，按一下**資料庫**。  

16. 拖曳**Quantity**節點從 事實總管 視窗，來**引數 1** IF 窗格中。  

17. 在 [事實總管] 視窗中，按一下 **.NET 類別**。  

18. 拖曳**GetMaxAllowed**節點從 事實總管 視窗，來**引數 2** IF 窗格中。  

19. 在 [事實總管] 視窗中，按一下**資料庫**。  

20. 拖曳**狀態**節點從 事實總管 視窗右下角的 商務規則編輯器 THEN 窗格。  

21. 在 [THEN] 窗格中，按一下**\<輸入值\>** ，然後輸入**Approved**。  

22. 在 [事實總管] 視窗中，以滑鼠右鍵按一下**1.0 版**中**ProcessPurchaseOrderDbNet**，然後按一下**AddNewRule**。  

23. 變更規則的名稱**Rule1**要**DeniedRule**然後按 ENTER 鍵。 您也可以在 [屬性] 視窗中變更規則的名稱。  

24. 在 [IF] 窗格 （上方） 右邊，以滑鼠右鍵按一下**條件**，按一下**述詞**，然後按一下**GreaterThan**。  

25. 在 [事實總管] 視窗中，按一下**資料庫**。  

26. 拖曳**Quantity**節點從 事實總管 視窗，來**引數 1** IF 窗格中。  

27. 在 [事實總管] 視窗中，按一下 **.NET 類別**。  

28. 拖曳**GetMaxAllowed**節點從 事實總管 視窗，來**引數 2** IF 窗格中。  

29. 在 [事實總管] 視窗中，按一下**資料庫**。  

30. 拖曳**狀態**節點從 事實總管 視窗右下角的 商務規則編輯器 THEN 窗格。  

31. 在 [THEN] 窗格中，按一下**\<輸入值\>** ，然後輸入**拒絕**。  

32. 在 [原則總管] 視窗中，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下**儲存**。  

### <a name="to-test-the-processpurchaseorderdbnet-policy-by-using-the-business-rule-composer"></a>使用商務規則編輯器測試 ProcessPurchaseOrderDbNet 原則  

1.  在 **開始**功能表中，開啟**商務規則編輯器 」**。 如果已經開啟 [商務規則編輯器]，請按 F5 重新整理。  

2.  在 原則總管 視窗中，依序展開**原則**，展開**ProcessPurchaseOrderDbNet**，以滑鼠右鍵按一下**1.0 版**，然後按一下 **測試原則**.  

3.  按一下  **testdb: Po （資料連線）**，然後按一下**新增執行個體**。  

4.  在 [**連接到 SQL Server** ] 對話方塊中，確認伺服器名稱和驗證資訊，然後按一下**確定**。  

5.  中**選取繫結**對話方塊方塊中，展開**TestDB**，按一下**PO**，然後按一下**確定**。  

6.  按一下 **測試**。  

7.  在 [輸出] 視窗中，確認同時**ApprovalRule**並**DeniedRule**會引發。  

8.  在 SQL Server Management Studio，以滑鼠右鍵按一下**dbo。PO**，然後按一下**開啟資料表**。  

9. 確認的值**狀態**欄位設定為**Approved**第一筆記錄。  

10. 確認的值**狀態**欄位設定為**拒絕**第二個記錄。  

    > [!NOTE]
    >  如果您仍然看到的值**狀態**欄位為 NULL，以滑鼠右鍵按一下包含資料的清單，然後按一下**執行 SQL**，會重新整理檢視。  

11. 保持 SQL Server Management Studio 開啟。  

### <a name="to-test-the-processpurchaseorderdbnet-policy-by-using-the-policyexecute-method"></a>使用 Policy.Execute 方法測試 ProcessPurchaseOrderDbNet 原則  

1. 開始**Microsoft Visual Studio**。  

2. 在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。  

3. 在 **新的專案**對話方塊方塊中，執行下列動作：  


   |             使用              |                             以進行此動作                              |
   |-----------------------------------|---------------------------------------------------------------------|
   |         **專案類型**         |                        按一下  **Visual C#**。                         |
   |           **範本**           |                   按一下 **主控台應用程式**。                    |
   |             **名稱**              |                    型別**TestProcessPODbNet**。                     |
   |           **位置**            |          指定**C:\BRE-Walkthroughs**做為位置。           |
   |         **方案名稱**         |                   型別**TestProcessPODbNetSol**。                   |
   | **為解決方案建立目錄** | 選取此核取方塊以建立方案檔案的目錄。 |


4. 按一下 [確定] 。 **TestProcessPODbNet**專案應該會出現在 [方案總管] 中。 如果看不到方案總管 中，按一下**方案總管**上**檢視**功能表。  

5. 在 [方案總管] 中，以滑鼠右鍵按一下**參考**，然後按一下**加入參考**。  

6. 按一下 **瀏覽**，瀏覽至**\Program Files\Common Files\Microsoft BizTalk**，然後按兩下**Microsoft.RuleEngine.dll**。  

7. 將下列程式碼加入至頂端**Program.cs**在現有的檔案`using`陳述式：  

   ```  
   //To use the SQLConnection class  
   using System.Data.SqlClient;  

   //To use the Policy and DataConnection classes  
   using Microsoft.RuleEngine;  
   ```  

8. 將下列程式碼加入**Main**函式來建立並開啟**SQLConnection**物件：  

   ```  
   SqlConnection cn = new SqlConnection("Data Source=(local);Initial Catalog=TestDB;Integrated Security=SSPI");  
   cn.Open();  
   ```  

9. 將下列程式碼加入**Main**函式來建立結尾**DataConnection**物件根據**SQLConnection**您在上一個步驟中建立的物件：  

    ```  
    DataConnection dc = new DataConnection("TestDB", "PO", cn);  
    ```  

10. 將下列程式碼加入**Main**函式來建立結尾**原則**物件，並執行原則：  

    ```  
    Policy policy = new Policy("ProcessPurchaseOrderDbNet");  
    policy.Execute(dc);  
    ```  

11. 將下列程式碼加入**Main**函式結尾，更新資料庫：  

    ```  
    dc.Update();  
    ```  

12. 將下列程式碼加入**Main**函式結尾，關閉資料庫連接：  

    ```  
    cn.Close();  
    ```  

13. 加入 try catch 區塊來攔截任何例外狀況中產生**Main**方法。  

14. 確認完整的程式碼，如**Main**函式是下列程式碼所示：  

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

15. 在 **建置**功能表上，按一下**建置 TestProcessPODbNet**。  

16. 在 「 商務規則編輯器 」 中，依序展開**原則**，展開**ProcessPurchaseOrderDbNet**，以滑鼠右鍵按一下**1.0 版**，然後按一下 **發行**.  

17. 以滑鼠右鍵按一下**1.0 版-已發佈**，然後按一下**部署**。  

18. 在 SQL Server Management Studio，將設定的值**狀態**欄位設為**NULL** PO 記錄。  

19. 在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，按 CTRL + F5 來執行**TestProcessPODbNet**應用程式。  

20. 按任意鍵關閉命令提示字元視窗。  

21. 在 SQL Server Management Studio，以滑鼠右鍵按一下含有 PO 記錄的資料表，並再按**執行 SQL**。  

22. 確認的值**狀態**欄位設定為**Approved**第一筆記錄。  

23. 確認的值**狀態**欄位設定為**拒絕**第二個記錄。  

## <a name="comments"></a>註解  

-   如果原則使用 .NET 類別的非靜態方法，您必須使用事實建立者元件，判斷提示 .NET 類別的執行個體，以透過「商務規則編輯器」測試原則。  

-   務必記住 「 商務規則編輯器 」 建立的執行個體**DataConnection**物件，並會主張至規則引擎工作記憶體會自動為您。 不過，當您叫用用戶端 （不論 BizTalk 或非 BizTalk） 應用程式，從原則時**DataConnection**物件未為您自動建立。 建立用戶端應該**DataConnection**物件，並將它傳遞做為參數或事實到規則引擎來執行此原則。  

-   您可以使用**DebugTrackingInterceptor**類別，以追蹤原則執行詳細資料。 下列範例程式碼示範如何建立的執行個體**DebugTrackingInterceptor**類別，並執行原則時，請使用它：  

    ```  
    DebugTrackingInterceptor dti = new DebugTrackingInterceptor("c:\\Trace.txt");  
    policy.Execute(dc, dti);  
    ```  

-   您可以使用**SqlTransaction**類別，以更新資料庫。 請從**ProcessPODbNet**以交易方式的原則。 下列程式碼示範如何開始交易，則會做為參數傳遞的交易**DataConnection**物件，並認可資料庫變更。 如需詳細資訊，請參閱 <<c0> [ 交易支援](../core/transaction-support.md)。  

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

## <a name="see-also"></a>另請參閱  
 [選取事實](../core/selecting-facts.md)