---
title: "逐步解說： 以程式設計方式執行原則 |Microsoft 文件"
ms.custom: 
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6398e7af-2ed1-4596-879c-3b7d000b8de2
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5afbe8bd29f18e71999ff32e0a1100de8a65fcc4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-executing-the-policy-programmatically"></a>逐步解說： 以程式設計方式執行原則
本逐步解說提供逐步程序來叫用您在中建立的原則[逐步解說： 建立簡單商務原則](../core/walkthrough-creating-a-simple-business-policy.md)從主控台應用程式的逐步解說以程式設計的方式。  
  
## <a name="prerequisites"></a>必要條件  
 您必須先完成[逐步解說： 建立簡單商務原則](../core/walkthrough-creating-a-simple-business-policy.md)逐步解說之前執行此逐步解說。  
  
## <a name="overview-of-this-walkthrough"></a>此逐步解說的概觀  
 此逐步解說包含兩個程序，如下表所示。  
  
|程序標題|程序說明|  
|---------------------|---------------------------|  
|使用 Policy.Execute 方法叫用 ProcessPurchaseOrder 原則|提供逐步指示，藉由叫用原則**Policy.Execute**方法。|  
|使用 RuleEngine.Execute 方法叫用 ProcessPurchaseOrder 原則|提供逐步指示，藉由叫用原則**RuleEngine.Execute**方法。|  
  
### <a name="to-invoke-the-processpurchaseorder-policy-by-using-the-policyexecute-method"></a>使用 Policy.Execute 方法叫用 ProcessPurchaseOrder 原則  
  
1.  啟動**Microsoft Visual Studio**。  
  
2.  在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。  
  
3.  在**新專案**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**專案類型**|按一下**Visual C#**。|  
    |**範本**|按一下**主控台應用程式**。|  
    |**名稱**|型別**ConsoleClient**。|  
    |**位置**|指定要儲存專案檔案的資料夾。|  
    |**方案名稱**|型別**ConsoleClientSol**。|  
    |**為方案建立目錄**|選取此核取方塊以建立方案檔案的目錄。|  
  
4.  按一下 **[確定]**。 **ConsoleClient**專案應該會出現在 [方案總管]。 如果看不到方案總管 中，按一下**方案總管 中**上**檢視**功能表。  
  
5.  在 方案總管 中，以滑鼠右鍵按一下**參考**，然後按一下 **加入參考**。  
  
6.  按一下**瀏覽**，瀏覽至**\Program Files\Common Files\Microsoft BizTalk**，然後按兩下**Microsoft.RuleEngine.dll**。  
  
7.  將下列行加入至頂端**Program.cs**檔案的現有`using`陳述式：  
  
    ```  
    //To use the XmlDocument class  
    using System.Xml;  
    //To use the TypedXmlDocument and Policy classes  
    using Microsoft.RuleEngine;   
    ```  
  
8.  將下列程式碼加入**Main**函式來建立**TypedXmlDocument**物件會根據 XML 文件：  
  
    ```  
    XmlDocument doc = new XmlDocument();  
    //Loading the XML from SamplePO.xml file.  
    //Change the directory as needed  
    doc.Load(@"C:\BRE-Walkthroughs\SamplePO.xml");  
    TypedXmlDocument txd = new TypedXmlDocument("RuleTest.PO", doc);  
    ```  
  
9. 將下列程式碼加入**Main**函式來執行此原則：  
  
    ```  
    //Create a policy object based on the name, ProcessPurchaseOrder  
    Policy policy = new Policy("ProcessPurchaseOrder");  
    //Execute the policy by invoking Policy.Execute method and   
    //by passing the typed xml document as a fact.   
    policy.Execute(txd);   
    ```  
  
10. 值列印輸出 XML 檔，確認**狀態**欄位設定為**Approved**。 請注意，不同於 「 商務規則編輯器 」 中，叫用**Policy.Execute**方法不會變更原始文件。  
  
    ```  
    //Print the output document  
    Console.WriteLine(txd.Document.OuterXml);   
    ```  
  
11. 在**建置**功能表上，按一下 [**建置 consoleclient]**。  
  
12. 按 CTRL+F5 執行應用程式。 確認已選取的值**狀態**欄位設定為**Approved**。  
  
### <a name="to-invoke-the-processpurchaseorder-policy-by-using-the-ruleengineexecute-method"></a>使用 RuleEngine.Execute 方法叫用 ProcessPurchaseOrder 原則  
  
1.  在 方案總管 中，以滑鼠右鍵按一下**參考**，然後按一下 **加入參考**。  
  
2.  按一下**瀏覽**，瀏覽至**\Program Files\Common Files\Microsoft BizTalk**，然後按兩下**Microsoft.BizTalk.RuleEngineExtensions.dll**。  
  
3.  註解中的下列程式**Program.cs**檔案：  
  
    ```  
    //Create a policy object based on the name, ProcessPurchaseOrder  
    Policy policy = new Policy("ProcessPurchaseOrder");  
    //Execute the policy by invoking Policy.Execute method and   
    //by passing the typed xml document as a fact.   
    policy.Execute(txd);   
    ```  
  
4.  在加入註解的程式碼後面，再加入下列程式碼，以存取「規則引擎」資料庫：  
  
    ```  
    //Get access to the SQL rule store   
    Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver dd;  
    dd = new Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver();  
    SqlRuleStore sqlRuleStore = (SqlRuleStore)dd.GetRuleStore();  
    ```  
  
5.  下列程式碼，以取得存取權加入**RuleSetInfoCollection** ProcessPurchaseOrder 原則：  
  
    ```  
    //Get access to RuleSetInfoCollection for the   
    //ProcessPurchaseOrder policy  
    RuleSetInfoCollection rsic = sqlRuleStore.GetRuleSets("ProcessPurchaseOrder", RuleStore.Filter.All);  
    ```  
  
6.  加入下列程式碼，以建立**RuleSet**物件根據 ProcessPurchaseOrder 原則的規則集資訊：  
  
    ```  
    //Create a RuleSet object based on the rule set information   
    //for the ProcessPurchaseOrder policy  
    RuleSet rs = sqlRuleStore.GetRuleSet(rsic[0]);  
    ```  
  
7.  加入下列程式碼，以建立**RuleEngine**物件：  
  
    ```  
    //Create the RuleEngine object  
    Microsoft.RuleEngine.RuleEngine engine = new Microsoft.RuleEngine.RuleEngine(rs);  
    ```  
  
8.  加入下列程式碼，判斷提示**TypedXmlDocument**物件至規則引擎工作記憶體：  
  
    ```  
    //Assert the TypedXmlDocument object into working memory  
    //of the rule engine  
    engine.Assert(txd);  
    ```  
  
9. 現在加入程式碼來執行此原則使用**RuleEngine.Execute**方法：  
  
    ```  
    //Execute the policy by invoking RuleEngine.Execute method  
    engine.Execute();  
    ```  
  
10. 請確定**Console.WriteLine**陳述式是中的最後一個陳述式**Main**函式。  
  
11. 在**建置**功能表上，按一下 [**建置 consoleclient]**。  
  
12. 按 CTRL+F5 執行應用程式。 確認已選取的值**狀態**欄位設定為**Approved**。  
  
## <a name="comments"></a>註解  
  
-   完整程式碼**Main**函式來使用執行 ProcessPurchaseOrder 原則**Policy.Execute**方法如下所示：  
  
    ```  
    static void Main(string[] args)  
    {  
    XmlDocument doc = new XmlDocument();  
    doc.Load(@"C:\BRE-Walkthroughs\SamplePO.xml");  
    TypedXmlDocument txd = new TypedXmlDocument("RuleTest.PO", doc);  
    Policy policy = new Policy("ProcessPurchaseOrder");  
    policy.Execute(txd);  
    Console.WriteLine(txd.Document.OuterXml);   
    }  
    ```  
  
-   完整執行 ProcessPurchaseOrder 原則使用的程式碼**RuleEngine.Execute**方法如下所示：  
  
    ```  
    static void Main(string[] args)  
    {  
    XmlDocument doc = new XmlDocument();  
    doc.Load(@"C:\BRE-Walkthroughs\SamplePO.xml");  
    TypedXmlDocument txd = new TypedXmlDocument("RuleTest.PO", doc);  
    Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver dd;  
    dd = new Microsoft.BizTalk.RuleEngineExtensions.RuleSetDeploymentDriver();  
    SqlRuleStore sqlRuleStore = (SqlRuleStore)dd.GetRuleStore();  
    RuleSetInfoCollection rsic = sqlRuleStore.GetRuleSets("ProcessPurchaseOrder", RuleStore.Filter.All);  
    RuleSet rs = sqlRuleStore.GetRuleSet(rsic[0]);  
    Microsoft.RuleEngine.RuleEngine engine = new Microsoft.RuleEngine.RuleEngine(rs);  
    engine.Assert(txd);  
    engine.Execute();  
    Console.WriteLine(txd.Document.OuterXml);   
    }  
    ```  
  
-   您可能想要加入**main**陳述式結尾處**Main**函式，以便應用程式會等到您終止該應用程式。  
  
-   在此逐步解說中，用戶端只提交一個事實至 ProcessPurchaseOrder 原則。 如果用戶端必須提交一個以上的事實至原則，它必須建立事實陣列，並使用多載**Execute**接受做為參數陣列的方法。 下列程式碼範例將示範如何執行這項工作：  
  
    ```  
    Policy policy = new Policy("PolicyName");  
    object[] facts = new object[2];  
    facts[0] = txd;  
    facts[1] = new MyClass();  
    policy.Execute(facts);  
    policy.Dispose();  
    ```  
  
-   第一個參數**TypedXmlDocument**建構函式在程式碼是用來建立原則型別的名稱。  
  
-   **Policy.Execute**方法基本上是周圍的包裝函式**RuleEngine.Execute**方法。 因此，使用**Policy.Execute**如您所見這個逐步解說中，方法是叫用原則，最簡單的方式。  
  
-   如進一步控制執行原則的詳細資訊，您可能想要使用**RuleEngine.Execute**方法，而不要使用**Policy.Execute**。 例如，您可以暫時終止引擎使用**暫止**函式，並再繼續使用**Execute**函式。 如需詳細資訊，請參閱[暫止](../core/halt.md)。  
  
## <a name="see-also"></a>另請參閱  
 [如何執行原則](../core/how-to-execute-policies.md)