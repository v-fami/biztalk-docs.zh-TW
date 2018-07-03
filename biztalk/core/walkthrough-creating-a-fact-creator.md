---
title: 逐步解說： 建立事實建立者 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 041c8f73-c72e-43fd-8446-144cecdc95ef
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fbe1e856ad97d81a153828a4d5ae45795670ed1f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37017319"
---
# <a name="walkthrough-creating-a-fact-creator"></a>逐步解說： 建立事實建立者
本逐步解說建立事實建立者元件，提供逐步程序**POFactCreator**，可用來測試**ProcessPurchaseOrder**您稍早建立的原則逐步解說。  

## <a name="prerequisites"></a>必要條件  
 您必須先完成[逐步解說： 建立簡單商務原則](../core/walkthrough-creating-a-simple-business-policy.md)逐步解說之前執行此逐步解說。  

## <a name="overview-of-this-walkthrough"></a>此逐步解說的概觀  
 此逐步解說包含兩個程序，如下表所示。  

|程序標題|程序說明|  
|---------------------|---------------------------|  
|建立 POFactCreator 元件|提供建立事實建立者元件的逐步指示**POFactCreator**。|  
|使用 POFactCreator 測試 ProcessPurchaseOrder 原則|提供逐步指示，使用 「 商務規則編輯器 」 工具來測試**ProcessPurchaseOrder**使用的原則**POFactCreator**元件。|  

### <a name="to-create-the-pofactcreator-component"></a>建立 POFactCreator 元件  

1. 開始**Microsoft Visual Studio**。  

2. 在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。  

3. 在 **新的專案**對話方塊方塊中，執行下列動作：  


   |             使用              |                             以進行此動作                              |
   |-----------------------------------|---------------------------------------------------------------------|
   |         **專案類型**         |                        按一下  **Visual C#**。                         |
   |           **範本**           |                      按一下 **類別庫**。                       |
   |             **名稱**              |                     型別**POFactCreatorLib**。                      |
   |           **位置**            |          指定**C:\BRE-Walkthroughs**做為位置。           |
   |         **方案名稱**         |                     型別**POFactCreatorSol**。                      |
   | **為解決方案建立目錄** | 選取此核取方塊以建立方案檔案的目錄。 |


4. 按一下 [確定] 。 **POFactCreatorLib**專案應該會出現在 [方案總管] 中。 如果看不到方案總管 中，按一下**方案總管**上**檢視**功能表。  

5. 在 [屬性] 視窗中，變更名稱的檔案，請**Class1.cs**至**POFactCreator.cs**。  

6. 在 [方案總管] 視窗中，以滑鼠右鍵按一下**參考**，然後按一下**加入參考**。  

7. 按一下 **瀏覽**，瀏覽至**C:\Program Files\Common Files\Microsoft BizTalk**，然後按兩下**Microsoft.RuleEngine.dll**。  

8. 將下列幾行加入至頂端**POFactCreator.cs**在現有的檔案`using`陳述式：  

   ```  
   //To use the XmlDocument class  
   using System.Xml;  
   //To use the TypedXmlDocument and Policy classes  
   using Microsoft.RuleEngine;   
   ```  

9. 修改**POFactCreator**類別來衍生自**IFactCreator**介面：  

    ```  
    public class POFactCreator : IFactCreator  
    {  
    }  
    ```  

10. 以滑鼠右鍵按一下**IFactCreator**，指向**實作介面**，然後按一下**實作介面**。  

     ![BRE&#45;逐步解說&#45;ImplementInterface](../core/media/ca1ae06c-ad24-4eac-94c3-5a06ad0f7305.gif "ca1ae06c-ad24-4eac-94c3-5a06ad0f7305")  

11. 新增的公用建構函式**POFactCreator**類別，如下所示：  

    ```  
    public POFactCreator()  
    {  
    }  
    ```  

12. 中的單獨陳述式中移除**CreateFacts**方法。  

13. 將下列程式碼加入**CreateFacts**方法來建立**TypedXmlDocument**物件根據**SamplePO.xml**文件：  

    ```  
    XmlDocument doc = new XmlDocument();  
    //Loading the XML from SamplePO.xml file.  
    doc.Load(@"C:\BRE-Walkthroughs\SamplePO.xml");  
    TypedXmlDocument txd = new TypedXmlDocument("RuleTest.PO", doc);  
    ```  

14. 新增下列程式碼，建立與事實陣列**TypedXmlDocument**物件做為唯一事實：  

    ```  
    object[] facts = new object[1];  
    facts[0] = txd;   
    ```  

15. 傳回事實陣列從**CreateFacts**方法：  

    ```  
    return facts;  
    ```  

16. 確認完整的程式碼中**CreateFacts**方法看起來如下：  

    ```  
    public object[] CreateFacts(RuleSetInfo ruleSetInfo)  
    {  
    XmlDocument doc = new XmlDocument();  
    //Loading the XML from SamplePO.xml file.  
    doc.Load(@"C:\BRE-Walkthroughs\SamplePO.xml");  
    TypedXmlDocument txd = new TypedXmlDocument("RuleTest.PO", doc);  

    object[] facts = new object[1];  
    facts[0] = txd;  
    return facts;  
    }  
    ```  

17. 中的單獨陳述式中移除**GetFactTypes**方法。  

18. 將下列程式碼加入**GetFactTypes**方法，以傳回包含之類型的類型陣列**TypedXmlDocument**類別：  

    ```  
    Type[] t = new Type[1];  
    t[0] = typeof(TypedXmlDocument);  
    return t;  
    ```  

19. 開始**Visual Studio 命令提示字元**。  

20. 將目錄變更**C:\BRE-Walkthroughs\POFactCreatorSol**，然後執行下列命令：  

     **Sn-k POFactCreator.snk**  

21. 在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，在 [方案總管] 中，展開**屬性**，然後按兩下**AssemblyInfo.cs**。  

22. 新增下列陳述式**AssemblyInfo.cs**結尾的檔案：  

    ```  
    [assembly: AssemblyKeyFile(@"C:\BRE-Walkthroughs\POFactCreatorSol\POFactCreator.snk")]  
    ```  

23. 在 [方案總管] 視窗中，以滑鼠右鍵按一下**POFactCreatorLib**，然後按一下**建置**。  

24. 在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]命令提示字元，變更目錄至以下**C:\BRE-Walkthroughs\POFactCreatorSol\POFactCreatorLib\Bin\Debug**，然後執行下列命令以註冊**POFactCreator**元件在 gac （全域組件快取）。 如果沒有開啟命令提示字元，請執行步驟 19 來開啟。  

     **Gacutil-i POFactCreatorLib.dll**  

### <a name="to-test-the-processpurchaseorder-policy-using-pofactcreator"></a>使用 POFactCreator 測試 ProcessPurchaseOrder 原則  

1. 在上**開始**功能表上，指向**所有程式**，指向[!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**商務規則編輯器 」**。 如果已經開啟 [商務規則編輯器]，請按 F5 重新整理。  

   > [!NOTE]
   >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。 若要這樣做，以滑鼠右鍵按一下 應用程式，然後按**系統管理員身分執行**。  

2. 在 原則總管 視窗中，依序展開**原則**，展開**ProcessPurchaseOrder**最新版本中，以滑鼠右鍵按一下，然後按一下 **測試原則**。  

    ![商務規則編輯器 」&#45;TestPolicyMenu](../core/media/af63c437-aeba-4e6a-a772-3346e7babee5.gif "af63c437-aeba-4e6a-a772-3346e7babee5")  

3. 在對話方塊的底部，按一下**新增**。  

4. 在  **.NET 組件**對話方塊中，選取**POFactCreatorLib**，然後按一下  **確定**。  

5. 在 [**選取繫結**] 對話方塊中，按一下**POFactCreator**中**POFactCreatorLib，10.0.0**，然後按一下 **[確定]**。  

6. 按一下 **測試**。  

7. 確認**ApprovalRule**引發輸出 視窗中。  

## <a name="comments"></a>註解  

-   若要使用「商務規則編輯器」來測試使用 .NET 類別之非靜態方法的原則，您必須建立事實建立者元件。  

## <a name="see-also"></a>另請參閱  
 [如何建立事實擷取器](../core/how-to-create-a-fact-retriever.md)