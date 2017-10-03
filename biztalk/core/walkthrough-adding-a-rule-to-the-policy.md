---
title: "逐步解說： 將規則新增至原則 |Microsoft 文件"
ms.custom: 
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2a682c0-a5d7-4550-924d-be9fa29b84d2
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 343dc2e9c7965ffb27a806d18944da99777dd3ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-adding-a-rule-to-the-policy"></a>逐步解說： 將規則新增原則
此逐步解說提供逐步程序加入名為的規則**DeniedRule**至**ProcessPurchaseOrder**原則。  
  
## <a name="prerequisites"></a>必要條件  
 您必須先完成[逐步解說： 建立和使用詞彙的原則中](../core/walkthrough-creating-and-using-a-vocabulary-in-the-policy.md)逐步解說，然後再執行本逐步解說。  
  
## <a name="overview-of-this-walkthrough"></a>此逐步解說的概觀  
 此逐步解說包含三個程序，如下表所示。  
  
|程序標題|程序說明|  
|---------------------|---------------------------|  
|若要將 DeniedRule 加入到 ProcessPurchaseOrder 原則|提供逐步指示，加入名為的新規則**DeniedRule**至**ProcessPurchaseOrder**原則。 **DeniedRule**規則設定的值**狀態**欄位設為**拒絕**如果的值**數量**大於 500。|  
|使用商務規則編輯器進行測試|提供逐步指示，測試**ProcessPurchaseOrder**使用商務規則編輯器 」 的原則。|  
|測試方案|提供測試方案的逐步指示。|  
  
### <a name="to-add-deniedrule-to-the-processpurchaseorder-policy"></a>若要將 DeniedRule 加入到 ProcessPurchaseOrder 原則  
  
1.  在**啟動**功能表中，開啟**商務規則編輯器 」**。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。 若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。  
  
2.  在 原則總管 視窗中，依序展開**原則**，依序展開**ProcessPurchaseOrder**，以滑鼠右鍵按一下**1.1 版**，然後按一下 **複製**.  
  
3.  以滑鼠右鍵按一下**ProcessPurchaseOrder**，然後按一下 **貼上原則版本**。  
  
4.  以滑鼠右鍵按一下**（未儲存） 1.2 版**，按一下 **新增規則**，然後將變更之規則的名稱**DeniedRule**。  
  
5.  如果您忘了要變更之規則的名稱**DeniedRule**在步驟 4 中，按一下**Rule1**，並將名稱變更為**DeniedRule**屬性 視窗中。  
  
6.  在 IF 窗格中，以滑鼠右鍵按一下**條件**，指向 **述詞**，然後按一下  **Greater Than**。  
  
7.  在 事實總管 視窗中，按一下**詞彙** 索引標籤。  
  
8.  展開**詞彙**，依序展開**POVocabulary**，依序展開**1.0 版-已發佈**，然後拖曳**要求數量**至**引數 1** [IF] 窗格中。  
  
9. 拖曳**允許的項目數目上限**至**引數 2** [IF] 窗格中。  
  
10. 拖曳**Request Status**到 [THEN] 窗格。  
  
11. 按一下**\<空字串 >** ，然後輸入**拒絕**。  
  
12. 以滑鼠右鍵按一下**（未儲存） 1.2 版**，然後按一下 **儲存**。  
  
13. 以滑鼠右鍵按一下**1.2 版**，然後按一下 **發行**。  
  
14. 以滑鼠右鍵按一下**1.2 版**，然後按一下 **部署**。  
  
### <a name="to-test-with-business-rule-composer"></a>使用商務規則編輯器進行測試  
  
1.  在記事本中開啟 SamplePO.xml 和 SamplePO2.xml 檔案，然後將值變更**狀態**欄位設為**XYZ**。  
  
2.  在 原則總管 視窗中，依序展開**原則**，依序展開**ProcessPurchaseOrder**，以滑鼠右鍵按一下**1.2 版**，然後按一下 **測試原則**.  
  
3.  在下**XMLDocuments**節點中，選取**ruletest.po**，然後按一下 **新增執行個體**。  
  
4.  選取**SamplePO.xml**，然後按一下 **開啟**。  
  
5.  按一下**測試**。  
  
6.  查看**議程更新**區段在輸出中，然後注意只有**ApprovalRule**新增至議程。 因此，它是引發的唯一規則 (會執行與此規則相關的動作)。  
  
7.  開啟**SamplePO.xml**在 [記事本]，請注意，值**狀態**欄位設定為**Approved**。  
  
8.  在 原則總管 視窗中，依序展開**原則**，依序展開**ProcessPurchaseOrder**，以滑鼠右鍵按一下**1.2 版**，然後按一下 **測試原則。**  
  
9. 選取**SamplePO.xml**，按一下 **移除執行個體**，然後按一下 **新增執行個體**。  
  
10. 選取**SamplePO2.xml**，然後按一下 **開啟**。  
  
11. 按一下**測試**。  
  
12. 查看**議程更新**區段在輸出中，然後注意只有**DeniedRule**新增至議程。 因此，它是引發的唯一規則。  
  
13. 開啟**SamplePO2.xml**在 [記事本]，請注意，值**狀態**欄位是**拒絕**。  
  
### <a name="to-test-the-solution"></a>測試方案  
  
1.  開啟**SamplePO.xml**和**SamplePO2.xml** [記事本] 中的值變更**狀態**欄位設為**XYZ**。  
  
2.  複製**SamplePO.xml**檔案從 C:\BRE-Walkthroughs 目錄到 C:\BRE-Walkthroughs\RuleTestSol\Input 目錄，協調流程。  
  
3.  您應該會在 C:\BRE-Walkthroughs\RuleTestSol\Output 目錄中看到協調流程的輸出檔。 開啟輸出 XML 檔案，並請注意，值**狀態**欄位設定為**Approved**。  
  
4.  重複步驟 2 和 3。 **SamplePO2.xml**，並注意值**狀態**欄位設定為**拒絕**輸出文件中。 這證明協調流程使用 1.2 版**ProcessPurchaseOrder**原則。 協調流程會使用最新的部署的版本**ProcessPurchaseOrder**原則，這是**1.2**。 您不需要解除部署 1.1 版的原則，也可以使用 1.2 版的原則。 但是，在測試此解決方案之前，您需要等候大約 60 秒鐘的時間。 如需詳細資訊，請參閱「註解」一節。  
  
## <a name="comments"></a>註解  
  
-   原則中可能有一或多個規則。 原則中的規則數目沒有邏輯限制。  
  
-   此規則引擎會使用「條件評估」、「衝突解決」和「動作執行」演算法。 在**條件評估**階段中，規則引擎會評估所有規則的條件。 條件評估為 True 的規則會變成執行的候選規則。 在**衝突解決**階段中，的候選規則新增至規則的優先權順序議程。 在**動作執行**階段中，會執行的候選規則中的動作。 如果候選規則具有相同的優先順序，執行這些規則的動作時，並沒有決定性的順序。 您應該假設這些動作是以平行方式執行。  
  
-   在此案例下，任何給定的範例檔案只會引發其中一個規則。 請確定您的值變更**狀態**欄位之前執行測試。  
  
-   在您部署新版的原則時，您應該等候大約 60 秒鐘，才能開始測試。 規則引擎更新服務會定期輪詢規則引擎資料庫 (預設為每隔 60 秒鐘)，以查看是否有新部署的原則。 規則引擎更新服務會使用規則引擎資料庫中最新部署之原則版本的相關資訊來更新記憶體中的原則物件。  
  
## <a name="next-steps"></a>後續步驟  
 現在您已完成此逐步解說中，執行[逐步解說： 修改原則](../core/walkthrough-modifying-the-policy.md)逐步解說，它可讓您修改原則的逐步指示核准採購訂單的值**數量**小於或等於 1000 （而不是 500)。  
  
## <a name="see-also"></a>另請參閱  
 [條件評估與動作執行](../core/condition-evaluation-and-action-execution.md)   
 [議程與優先順序](../core/agenda-and-priority.md)