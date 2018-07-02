---
title: 逐步解說： 建立和使用的原則中的詞彙 |Microsoft Docs
ms.custom: ''
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2c306a6e-3384-4f43-9c75-c5407cd9aed2
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 92a2f458d3ae4aa43befff248d564c92d78ef132
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974767"
---
# <a name="walkthrough-creating-and-using-a-vocabulary-in-the-policy"></a>逐步解說： 建立和使用的原則中的詞彙
本逐步解說提供逐步的程序建立的詞彙和使用中的詞彙**ProcessPurchaseOrder**原則。  
  
## <a name="prerequisites"></a>必要條件  
 您必須先完成[逐步解說： 建立簡單商務原則](../core/walkthrough-creating-a-simple-business-policy.md)逐步解說，然後再執行本逐步解說。 不過，我們建議您先完成在此文件中列在此逐步解說之前的所有逐步解說。  
  
## <a name="overview-of-this-walkthrough"></a>此逐步解說的概觀  
 此逐步解說包含三個程序，如下表所示。  
  
|程序標題|程序描述|  
|---------------------|---------------------------|  
|建立 POVocabulary 詞彙|提供逐步指示，建立**POVocabulary**含有三個定義的詞彙： 要求數量、 最大項目允許的數目，以及要求狀態。|  
|在 ProcessPurchaseOrder 原則中使用 POVocabulary|提供逐步指示來建立新版**ProcessPurchaseOrder**原則使用**POVocabulary**。|  
|測試方案|提供測試方案的逐步指示。|  
  
### <a name="to-create-the-povocabulary-vocabulary"></a>建立 POVocabulary 詞彙  
  
1.  在 **開始**功能表中，開啟**商務規則編輯器 」**。 如果已經開啟 [商務規則編輯器]，請按 F5 重新整理。  
  
    > [!NOTE]
    >  在支援 [使用者帳戶控制] \(UAC) 的系統上，您必須以系統管理權限執行此工具。 若要這樣做，以滑鼠右鍵按一下 應用程式，然後按**系統管理員身分執行**。  
  
2.  在 事實總管 視窗中，按一下**詞彙** 索引標籤。  
  
3.  以滑鼠右鍵按一下**詞彙**，按一下**新增詞彙**，然後輸入**POVocabulary**做為詞彙的名稱。  
  
4.  如果您沒有變更名稱的詞彙來 POVocabulary 步驟 3 中，變更將詞彙的名稱**POVocabulary**屬性 視窗中。  
  
5.  以滑鼠右鍵按一下**版本 1.0 （未儲存）** 中**POVocabulary**，然後按一下**新增定義**。  
  
6.  在 詞彙定義精靈 中，選取**XML 文件項目或屬性**，然後按一下**下一步**。  
  
7.  針對**定義名稱**，型別**要求數量**。  
  
8.  按一下 **瀏覽**，然後選取**PO.xsd**檔案中建立您[逐步解說： 建立簡單商務原則](../core/walkthrough-creating-a-simple-business-policy.md)。  
  
9. 在**選取繫結**對話方塊方塊中，展開**PurchaseOrder**，展開**項目**，然後按兩下**數量**。  
  
10. 請確定**文件類型**設為**RuleTest.PO**。 如果不存在，請將文件類型變更為 [ruletest.po]。 這個步驟非常重要。  
  
     ![BRE&#45;逐步解說&#45;ChangeDocType2](../core/media/090f0bce-0594-4a67-87d0-3cd22fbb1796.gif "090f0bce-0594-4a67-87d0-3cd22fbb1796")  
  
11. 指定**選取作業**中**選取作業**群組列為**執行取得作業**。  
  
     ![BRE&#45;逐步解說&#45;SelectGet](../core/media/3034649a-2d81-4f08-8044-3ab66a201672.gif "3034649a-2d81-4f08-8044-3ab66a201672")  
  
12. 按一下 **[完成]**。  
  
13. 以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下**新增定義**。  
  
14. 選取 [ **XML 文件項目或屬性**，然後按一下**下一步]**。  
  
15. 針對**定義名稱**，型別**Request Status**。  
  
16. 按一下 **瀏覽**，然後選取**PO.xsd**檔案。  
  
17. 在 商務規則編輯器 中，展開**原則**，展開**ProcessPurchaseOrder**，以滑鼠右鍵按一下**1.0 版-部署**，然後按一下 解除部署.  
  
18. 以滑鼠右鍵按一下**版本 1.1-發佈**，然後按一下**部署**。 這個步驟非常重要。  
  
19. 等待大約**60**秒。**  
  
20. 按一下 **[完成]**。  
  
21. 以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下**新增定義**。  
  
22. 複製**SamplePO.xml**檔案從 C:\BRE-Walkthroughs 目錄到 C:\BRE-Walkthroughs\RuleTestSol\Input 目錄，協調流程。  
  
23. 重複步驟 5 和 6 **SamplePO2.xml**，並請注意，值**狀態**輸出文件中的欄位是相同的輸入文件 (XYZ)。  
  
24. 值**狀態**欄位會保持相同 (XYZ)，因為 「 規則引擎不會執行中的動作**ApprovalRule**規則，因為條件評估為。  
  
25. 在 「 建立 POVocabulary 詞彙 」 程序中，您可以變更的文件類型**RuleTest.PO**。  
  
26. 在 [屬性] 視窗中，請注意， **RuleTest**命名空間的名稱和**PO**名稱型別。  
  
27. 當您選取**執行 「 設定 」 作業**詞彙定義精靈 的第二頁，您可以指定**顯示格式字串**接下來的頁面上。  
  
### <a name="to-use-the-povocabulary-in-the-processpurchaseorder-policy"></a>在 ProcessPurchaseOrder 原則中使用 POVocabulary  
  
1.  比方說，您可以變更顯示的格式字串，從**Request Status**  **要**要求狀態：  後，再按一下**完成**中「 建立詞彙 」 程序步驟 20。  
  
2.  既然您已完成本逐步解說中，執行**逐步解說： 將規則新增至原則**逐步解說中，它將提供逐步指示來新增規則**ProcessPurchaseOrder**原則。  
  
3.  詞彙  
  
4.  如何開發詞彙  
  
     ![BRE&#45;逐步解說&#45;DragReqQty](../core/media/f5ec8bca-344e-4099-a347-0a2298a3f088.gif "f5ec8bca-344e-4099-a347-0a2298a3f088")  
  
     ![BRE&#45;逐步解說&#45;ReqQty](../core/media/7afddd71-31ce-4868-94c1-d7ffd81f1e47.gif "7afddd71-31ce-4868-94c1-d7ffd81f1e47")  
  
5.  拖曳**數字的項目允許的最大**來取代條件的右邊 (rhs) 引數 (**500**)。  
  
6.  然後在窗格中，按一下滑鼠右鍵，然後按一下 選取現有的動作**刪除動作**。  
  
    > [!NOTE]
    >  您也可以在選取動作之後，按下 DELETE 鍵以刪除該動作。  
  
7.  拖曳**Request Status**要**然後**窗格。  
  
8.  按一下  **\<空字串\>** ，然後輸入**Approved**。  
  
9. 以滑鼠右鍵按一下**1.1 （未儲存） 版**在原則總管 視窗，然後按一下**儲存**。  
  
10. 以滑鼠右鍵按一下**1.1 （未儲存） 版**在原則總管 視窗，然後按一下**發佈**。  
  
### <a name="to-test-the-solution"></a>測試方案  
  
1.  在 商務規則編輯器 中，展開**原則**，展開**ProcessPurchaseOrder**，以滑鼠右鍵按一下**1.0 版-部署**，然後按一下 **解除部署**.  
  
    > [!NOTE]
    >  這個步驟是選擇性的，因為協調流程一定都會挑選原則的最新部署版本，也就是在執行步驟 2 之後的 1.1。  
  
2.  以滑鼠右鍵按一下**版本 1.1-發佈**，然後按一下**部署**。  
  
3.  等待大約**60**秒。 如果有快取原則的任何更新，規則引擎更新服務便會每隔 60 秒鐘重新整理快取。 無論您是否有執行步驟 1 都沒關係，協調流程會挑選原則的最新部署版本，也就是 1.1。  
  
4.  開啟**SamplePO.xml**並**SamplePO2.xml** [記事本] 中的值變更**狀態**欄位設為**XYZ**。  
  
5.  複製**SamplePO.xml**檔案從 C:\BRE-Walkthroughs 目錄到 C:\BRE-Walkthroughs\RuleTestSol\Input 目錄，協調流程。  
  
6.  您應該會在 C:\BRE-Walkthroughs\RuleTestSol\Output 目錄中看到協調流程的輸出檔。 開啟輸出 XML 檔案，並請注意，值**狀態**欄位設定為**Approved**。  
  
7.  重複步驟 5 和 6 **SamplePO2.xml**，並請注意，值**狀態**輸出文件中的欄位是相同的輸入文件 (**XYZ**)。  
  
    > [!NOTE]
    >  值**狀態**欄位會保持相同 (XYZ)，因為 「 規則引擎不會執行中的動作**ApprovalRule**規則，因為條件評估為`false`。  
  
## <a name="comments"></a>註解  
  
- 在儲存詞彙之後，您依然能夠予以修改。 在發佈詞彙之後，您就不能夠加以修改。  
  
- 如果需要修改定義、新增定義或刪除定義，您就應該建立詞彙的新版本。  
  
- 只有已發佈的詞彙才能在原則中使用。  
  
- 在 「 建立 POVocabulary 詞彙 」 程序中，您可以變更的文件類型**RuleTest.PO**。 若要查看這項變更，結果在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，在 [方案總管] 中，按一下  **PO.xsd**。 在 [屬性] 視窗中，請注意， **RuleTest**命名空間的名稱和**PO**名稱**型別**。  
  
- 在此逐步解說中，您只有使用 XML 文件做為原則的事實。 您也可以在建立原則時使用 .NET 事實和資料庫事實。  
  
- 當您選取**執行 「 設定 」 作業**詞彙定義精靈 的第二頁，您可以指定**顯示格式字串**接下來的頁面上。 比方說，您可以變更顯示的格式字串，從**Request Status {0}** 要**要求狀態： {0}** 後，再按一下**完成**中「 建立詞彙 」 程序步驟 20。  
  
## <a name="next-steps"></a>後續步驟  
 既然您已完成本逐步解說中，執行[逐步解說： 將規則新增至原則](../core/walkthrough-adding-a-rule-to-the-policy.md)逐步解說中，它將提供逐步指示來新增規則**ProcessPurchaseOrder**原則。  
  
## <a name="see-also"></a>另請參閱  
 [詞彙](../core/vocabularies.md)   
 [如何開發詞彙](../core/how-to-develop-vocabularies.md)   
 [條件評估與動作執行](../core/condition-evaluation-and-action-execution.md)   
 [議程與優先順序](../core/agenda-and-priority.md)