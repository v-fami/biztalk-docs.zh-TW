---
title: 逐步解說： 測試原則 |Microsoft Docs
ms.custom: ''
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53ed915d-0f3a-48ea-bfd5-a1f89b9b689c
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ddf9dcc459fbee7494a913846f1c9d2a7137579
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001764"
---
# <a name="walkthrough-testing-the-policy"></a>逐步解說： 測試原則
本逐步解說提供逐步程序來測試您在中建立的原則[逐步解說： 建立簡單商務原則](../core/walkthrough-creating-a-simple-business-policy.md)逐步解說。  

## <a name="prerequisites"></a>必要條件  
 您必須先完成[逐步解說： 建立簡單商務原則](../core/walkthrough-creating-a-simple-business-policy.md)逐步解說之前執行此逐步解說。  

## <a name="overview-of-this-walkthrough"></a>此逐步解說的概觀  
 此逐步解說包含兩個程序，如下表所示。  

|程序標題|程序說明|  
|---------------------|---------------------------|  
|若要建立測試檔案|提供逐步指示，如建立兩個範例 XML 檔，其中一個值是 [數量] 欄位為 400 (\<= 500)，另一個為 700 (> 500) 的 [數量] 欄位的值。|  
|若要測試 ProcessPurchaseOrder 原則|提供逐步指示，說明如何使用「商務規則編輯器」測試 ProcessPurchaseOrder 原則。|  

### <a name="to-create-the-test-files"></a>若要建立測試檔案  

1.  在 **開始**功能表中，開啟**記事本**。  

2.  將下列 XML 文字複製到 [記事本] 中：  

    ```  
    <ns0:PurchaseOrder xmlns:ns0="http://EAISolution.PurchaseOrder">  
      <Header>  
        <ReqID>ReqID_0</ReqID>  
        <Date>Date_0</Date>  
      </Header>  
      <Item>  
        <Description>Description_0</Description>  
        <Quantity>400</Quantity>  
        <UnitPrice>20</UnitPrice>  
      </Item>  
      <Status>XYZ</Status>  
    </ns0:PurchaseOrder>    
    ```  

3.  在 **檔案**功能表上，按一下**另存 TextFile1.txt 為**。  

4.  值變更**另存為型別**從**文字文件 (\*.txt)** 來**的所有檔案**。  

5.  將目錄變更**C:\BRE-Walkthroughs**。  

6.  型別**SamplePO.xml** for**檔名**，然後按一下**儲存**。  

7.  在 [檔案]  功能表上，按一下 [新增] 。  

8.  將下列 XML 文字複製到 [記事本] 中：  

    ```  
    <ns0:PurchaseOrder xmlns:ns0="http://EAISolution.PurchaseOrder">  
      <Header>  
        <ReqID>ReqID_0</ReqID>  
        <Date>Date_0</Date>  
      </Header>  
      <Item>  
        <Description>Description_0</Description>  
        <Quantity>700</Quantity>  
        <UnitPrice>20</UnitPrice>  
      </Item>  
      <Status>XYZ</Status>  
    </ns0:PurchaseOrder>   
    ```  

9. 在 **檔案**功能表上，按一下**另存 TextFile1.txt 為**。  

10. 值變更**另存為型別**從**文字文件 (\*.txt)** 來**的所有檔案**。  

11. 將目錄變更**C:\BRE-Walkthroughs**。  

12. 型別**SamplePO2.xml** for**檔名**，然後按一下**儲存**。  

13. 關閉 [記事本]。  

### <a name="to-test-the-processpurchaseorder-policy"></a>若要測試 ProcessPurchaseOrder 原則  

1.  在 **開始**功能表中，開啟**商務規則編輯器 」**。 如果已開啟 [商務規則編輯器]，請按下 F5 重新整理。  

    > [!NOTE]
    >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。 若要這樣做，以滑鼠右鍵按一下 應用程式，然後按**系統管理員身分執行**。  

2.  在 原則總管 視窗中，依序展開**原則**，展開**ProcessPurchaseOrder**，以滑鼠右鍵按一下**1.0 版**，然後按一下 **測試原則**.  

3.  在  **XMLDocuments**節點中，選取**RuleTest.PO**，然後按一下 **新增執行個體**。  

     ![商務規則編輯器 」&#45;TestPolicySelectFacts](../core/media/7115f0d4-0c12-4292-81a5-eb78d62c5543.gif "7115f0d4-0c12-4292-81a5-eb78d62c5543")  

4.  選取  **SamplePO.xml**稍早建立的檔案，然後按一下**開啟**。  

5.  按一下 **測試**。  

6.  在 [輸出] 視窗中檢視輸出。 如需輸出的說明，請參閱「第一個測試 (samplepo.xml) 的輸出分析」一節。  

7.  開啟**SamplePO.xml**在 [記事本]，請注意，值**狀態**欄位設定為**Approved**。  

8.  以滑鼠右鍵按一下**1.0 版**，然後按一下**測試原則**。  

9. 選取  **SamplePO.xml**，按一下**移除執行個體**，然後按一下**新增執行個體**。  

10. 選取  **SamplePO2.xml**稍早建立的檔案，然後按一下**開啟**。  

11. 按一下 **測試**。 如需輸出的說明，請參閱「第二個測試 (samplepo2.xml) 的輸出分析」一節。  

12. 開啟**SamplePO2.xml** [記事本] 中，並請注意，值**狀態**欄位仍**XYZ**。  

## <a name="analysis-of-the-output-from-the-first-test-samplepoxml"></a>第一個測試 (samplepo.xml) 的輸出分析  

> [!NOTE]
>  輸出文字是粗體，說明在輸出文字之後。  

 **規則集的規則引擎追蹤： ProcessPurchaseOrder 8/31/2006年下午 1:33:10**  

 執行原則的規則引擎追蹤**ProcessPurchaseOrder**開始 8/31/2006年下午 1:33:10。  

 **事實活動 8/31/2006年下午 1:33:10**  

 **規則引擎執行個體識別碼： bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**  

 **規則集名稱： ProcessPurchaseOrder**  

 **作業： 判斷提示**  

 **物件類型： TypedXmlDocument:PurchaseOrder**  

 **物件執行個體識別碼： 14626574**  

 當您按一下 **測試**，會發生下列情況：  

1. 「 商務規則編輯器 」 建立**RuleEngine.Policy**物件，進而建立新的規則引擎執行個體，或取得從規則引擎快取規則引擎執行個體。  

2. 「 商務規則編輯器 」 建立**TypedXmlDocument** SamplePO.xml 檔案為基礎的物件。  

3. 「 商務規則編輯器 」 會叫用**Policy.Execute**方法**TypedXmlDocument**物件做為參數。  

4. **Policy.Execute**方法會判斷提示 （新增） **TypedXmlDocument**物件當做事實到規則引擎工作記憶體。  

5. 規則引擎會使用**TypedXmlDocument**物件當做事實並執行**ProcessPurchaseOrder**原則。  

   **事實活動 8/31/2006年下午 1:33:10**  

   **規則引擎執行個體識別碼： bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**  

   **規則集名稱： ProcessPurchaseOrder**  

   **作業： 判斷提示**  

   **物件類型： TypedXmlDocument:PurchaseOrder: / PurchaseOrder**  

   **物件執行個體識別碼： 64530307**  

   **事實活動 8/31/2006年下午 1:33:10**  

   **規則引擎執行個體識別碼： bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**  

   **規則集名稱： ProcessPurchaseOrder**  

   **作業： 判斷提示**  

   **物件類型： TypedXmlDocument:PurchaseOrder: / PurchaseOrder/項目**  

   **物件執行個體識別碼： 43901854**  

6. 規則引擎會決定哪一個子系**TypedXmlDocument**物件，以建立根據規則中所定義的 XPath 選取器。 當您建置商務規則編輯器 」 中的規則時，XPath 選取器的預設值為節點中選取之節點上方**XML 結構描述**事實總管 中的索引標籤。 XPath 欄位的值預設為選取的節點本身 (相對於其父節點而言)。 不過，如果選取的節點有子系，則只會建立 XPath 選取器繫結指向選取的節點，而不會建立 XPath 欄位繫結。  

7. 下表顯示的 XPath 選取器和 XPath 欄位繫結中使用之欄位的值**ProcessPurchaseOrder**原則。 (此原則只有一個規則：ApprovalRule)。  

| 欄位名稱 |                                                             XPath 選取器                                                              |                    XPath 欄位                     | XPath 選取器 (簡化形式) | XPath 欄位<br /><br /> (簡化形式) |
|------------|-----------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------|----------------------------------|-------------------------------------------|
|  Quantity  | /\*[local-name = 'PurchaseOrder' and namespace-uri （) ='http://EAISolution.PurchaseOrder'] /\*[local-name = 'Item' and namespace-uri （) ='] | \*[local-name = 'Quantity' and namespace-uri （) = '] |       /PurchaseOrder/Item        |                 Quantity                  |
|   [狀態]   |                       /\*[local-name = 'PurchaseOrder' and namespace-uri （) ='<http://EAISolution.PurchaseOrder>']                        |  \*[local-name = 'Status' and namespace-uri （) = ']  |          /PurchaseOrder          |                  [狀態]                   |

<!---Loc Comment: Please, verify strucutre in line 183 and 184--->

#### <a name="to-view-the-xpath-selector-and-xpath-field-bindings-for-the-quantity-and-status-fields"></a>若要檢視 Quantity 和 Status 欄位的 Xpath 選取器和 Xpath 欄位繫結  

1. 在 [原則總管] 視窗中，依序展開**原則**，展開**ProcessPurchaseOrder**，然後展開**1.0 版**。  

2. 按一下  **ApprovalRule**。  

3. 在右側 [IF] 窗格中，按一下**PO: / PurchaseOrder/Item/Quantity**。  

4. 確認您看到上述資料表中所顯示的值**XPath 選取器**並**XPath 欄位**屬性 視窗中的繫結。  

5. 重複步驟 3 和 4 **PO: / PurchaseOrder/Status**欄位。  

   規則引擎建立的子系**TypedXmlDocument**物件從原始**TypedXmlDocument**您提交的每個 XPath 選取器。 因為有兩個不同 XPath 選取器用於原則 (**/PurchaseOrder/項目**如**Quantity**欄位並 **/PurchaseOrder**的**狀態**欄位)，規則引擎會建立兩個子**TypedXmlDocument**物件，並它們判斷提示至規則引擎工作記憶體。  

> [!NOTE]
>  若要查看追蹤一次輸出中，按一下**1.0 版**[原則總管] 視窗中。  

 **條件評估測試 （符合） 8/31/2006年下午 1:33:10**  

 **規則引擎執行個體識別碼： bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**  

 **規則集名稱： ProcessPurchaseOrder**  

 **測試運算式： TypedXmlDocument:PurchaseOrder:/PurchaseOrder/Item.Quantity < = 500**  

 **左運算元值： 400**  

 **右運算元值： 500**  

 **測試結果： True**  

 **議程更新 8/31/2006年下午 1:33:10**  

 **規則引擎執行個體識別碼： bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**  

 **規則集名稱： ProcessPurchaseOrder**  

 **作業： 新增**  

 **規則名稱： ApprovalRule**  

 **衝突解決準則： 0**  

 此規則引擎會使用「條件評估」、「衝突解決」和「動作執行」三階段演算法來執行原則。 在「條件評估」階段中，此規則引擎會評估所有原則之規則中的條件，並將條件評估為 `true` 的規則新增至議程中。 在此簡單範例中， **ProcessPurchaseOrder**原則有只有一個規則， **ApprovalRule**。 因此，規則引擎會評估條件， **Quantity < = 500**，請在**ApprovalRule**使用的值**Quantity**提交 XML 文件中的欄位這是**400**。 以上輸出顯示左運算元、右運算元和測試結果的值。  

 在第二個階段「衝突解決準則」中，條件評估為 `true` 的規則會依照其優先順序新增至議程中。 在此案例中，加入規則引擎**ApprovalRule**議程因為條件**ApprovalRule**評估為`true`。 上述輸出中顯示 「 衝突解決準則是規則的優先順序 (**ApprovalRule**)。 如果您按一下**ApprovalRule** [原則總管] 視窗中的節點，您可以看到的值**優先順序**做為 [屬性] 視窗中的規則屬性**0**，也就是規則的預設值。 如果原則有多個規則，而且要確定某個規則的動作會在另一個規則的動作之後執行，則必須適當設定優先順序。 數字愈大，優先順序愈高。  

 **規則被引發 8/31/2006年下午 1:33:10**  

 **規則引擎執行個體識別碼： bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**  

 **規則集名稱： ProcessPurchaseOrder**  

 **規則名稱： ApprovalRule**  

 **衝突解決準則： 0**  

 在最後一個階段「動作執行」中，規則引擎會開始執行規則中的動作。 中的一個動作**ApprovalRule**，可設定的值**狀態**提交 XML 文件中的欄位**Approved**。  

 **事實活動 8/31/2006年下午 1:33:10**  

 **規則引擎執行個體識別碼： bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**  

 **規則集名稱： ProcessPurchaseOrder**  

 **作業： 撤銷**  

 **物件類型： TypedXmlDocument:PurchaseOrder**  

 **物件執行個體識別碼： 14626574**  

 **事實活動 8/31/2006年下午 1:33:10**  

 **規則引擎執行個體識別碼： bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**  

 **規則集名稱： ProcessPurchaseOrder**  

 **作業： 撤銷**  

 **物件類型： TypedXmlDocument:PurchaseOrder: / PurchaseOrder/項目**  

 **物件執行個體識別碼： 43901854**  

 **事實活動 8/31/2006年下午 1:33:10**  

 **規則引擎執行個體識別碼： bc4f1cf5-e9a2-49d0-9cdd-76a2ac057240**  

 **規則集名稱： ProcessPurchaseOrder**  

 **作業： 撤銷**  

 **物件類型： TypedXmlDocument:PurchaseOrder: / PurchaseOrder**  

 **物件執行個體識別碼：** 64530307  

 送出的所有事實 (**PurchaseOrder**) 至規則引擎 」 和 「 規則引擎所建立的子事實根據 XPath 選取器 (**\PurchaseOrder**和**\PurchaseOrder\Item**)會撤回 （移除） 從規則引擎工作記憶體。  

## <a name="analysis-of-the-output-from-the-second-test-samplepo2xml"></a>第二個測試 (samplepo2.xml) 的輸出分析  
 **條件評估測試 （符合） 9/5/2006年 5:24:42 PM**  

 **規則引擎執行個體識別碼： b749d2fd-a883-4c2f-9974-5cf688010622**  

 **規則集名稱： ProcessPurchaseOrder**  

 **測試運算式： TypedXmlDocument:PurchaseOrder:/PurchaseOrder/Item.Quantity < = 500**  

 **左運算元值： 700**  

 **右運算元值： 500**  

 **測試結果：** False  

 規則引擎會評估條件 (**Quantity < = 500**) 中**ApprovalRule**使用獨立**項目**物件。 您可以看到左的運算元值是值**Quantity** XML 文件中的項目**700**。 測試結果`false`因為**700 < = 500**，因此，此規則不會加入至規則引擎的議程。 議程中沒有規則。 因此，有任何動作來執行，與數值**狀態**欄位會維持**XYZ**。  

## <a name="comments"></a>註解  

-   建議您先測試原則，然後從 BizTalk 應用程式之類的用戶端應用程式中使用原則。  

-   當您測試使用與資料庫事實的原則**DataConnection**中 「 商務規則編輯器 」 中，繫結**DataConnection**物件自動為您所建立。 不過，當您呼叫相同的原則，從協調流程使用**呼叫規則**圖形，否**DataConnection**物件會自動傳遞給原則。 您應該建立**DataConnection**協調流程中的物件並將它當做參數傳遞，或建立判斷提示事實擷取器元件**DataConnection**物件，並設定要使用的原則事實擷取器元件中。  

-   若要測試使用.NET 事實的原則，您應該建立事實建立者元件，並指定在**選取事實** 對話方塊。 如需建立事實建立者的詳細資訊，請參閱 <<c0> [ 如何建立事實擷取器](../core/how-to-create-a-fact-retriever.md)。 當此原則會使用資料庫事實，您可以執行相同的動作 (**TypedDataConnection**或是**TypedDataTable**或是**TypedDataRow**) 或 XML 事實 (**TypedXmlDocument**)。  

## <a name="next-steps"></a>後續步驟  
 既然您已完成本逐步解說中，執行[逐步解說： 叫用原則與協調流程](../core/walkthrough-invoking-the-policy-from-an-orchestration.md)逐步解說，它可讓您叫用的逐步指示**ProcessPurchaseOrder**從協調流程的原則。  

## <a name="see-also"></a>另請參閱  
 [原則測試追蹤輸出](../core/policy-test-trace-output.md)   
 [條件評估與動作執行](../core/condition-evaluation-and-action-execution.md)   
 [議程與優先順序](../core/agenda-and-priority.md)
