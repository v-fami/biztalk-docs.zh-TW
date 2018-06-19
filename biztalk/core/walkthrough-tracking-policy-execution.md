---
title: 逐步解說： 追蹤 BizTalk Server 中的原則執行 |Microsoft 文件
description: 若要啟用追蹤，並檢視追蹤詳細資料原則的 BizTalk Server 中的教學課程
ms.custom: ''
ms.date: 04/05/2016
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef88eae7-f0f8-4f3f-85d0-3961a47395b6
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f20b35aca2c4fb35419153ccfb149aa34501b21a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25975092"
---
# <a name="walkthrough-tracking-policy-execution"></a>逐步解說： 追蹤原則執行
啟用追蹤的逐步程序**ProcessPurchaseOrder**原則，以及在執行原則之後檢視追蹤資訊。  
  
## <a name="prerequisites"></a>必要條件  
完成[逐步解說： 修改原則](../core/walkthrough-modifying-the-policy.md)逐步解說，然後再執行本逐步解說。  
  
## <a name="enable-tracking-for-the-processpurchaseorder-policy"></a>啟用 ProcessPurchaseOrder 原則的追蹤  
  
1.  開啟 [BizTalk Server 管理] 。 如果您已經開啟，請按 F5 重新整理。  
  
2.  展開**主控台根目錄**，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開**RuleTestApp**。  
  
3.  以滑鼠右鍵按一下**原則**，選取**新增**，然後選取**原則**。  
  
    > [!NOTE]
    >  若要啟用原則的追蹤，您必須使用 [BizTalk Server 管理] 主控台，將原則新增至 BizTalk 應用程式。  
  
4.  在**新增原則**對話方塊方塊中，展開  **ProcessPurchaseOrder**，然後選取版本**1.3**。  
  
5.  按一下 **[確定]**。  
  
6.  如果您沒有看到**ProcessPurchaseOrder**在清單中，選取 F5 重新整理檢視。
  
7.  以滑鼠右鍵按一下**ProcessPurchaseOrder**，然後選取**追蹤。**  
  
8.  在**原則追蹤選項**對話方塊中，選取所有核取方塊**事實活動**，**條件評估**，**規則引發**，和**議程更新**。  
  
9. 按一下 **[確定]**。  
  
## <a name="test-the-solution-and-view-the-tracking-information"></a>測試方案，並檢視追蹤資訊  
  
1.  開啟**SamplePO.xml**和**SamplePO2.xml** [記事本]，然後將值變更**狀態**欄位設為**XYZ**。  
  
2.  複製**SamplePO.xml**您在建立[逐步解說： 測試原則](../core/walkthrough-testing-the-policy.md)協調流程的輸入目錄。  
  
3.  您應該會在協調流程的輸出目錄中看到輸出檔案。 開啟輸出 XML 檔案，並請注意，值**狀態**欄位設定為**Approved**。  
  
4.  在**BizTalk Server 管理**，請移至**群組概觀**頁面上，按一下**群組中樞**索引標籤，然後再按一下**追蹤服務執行個體**.  
  
5.  以滑鼠右鍵按一下協調流程 (RuleTest.Orchestration_1)，名稱，然後按一下**訊息流程**。  
  
6.  按一下**跟隨此連結以檢視此協調流程執行個體的原則執行詳細資料**。 請確定您看到的視窗中看起來像下圖：  
  
     ![BRE &#45;逐步解說 &#45;FirstScreen](../core/media/1e59fe9e-cf2d-407a-81cd-102b57a515d2.gif "1e59fe9e-cf2d-407a-81cd-102b57a515d2")  
  
7. 按一下時間或 **[processpurchaseorder1.3]** 看到下列畫面。 在這個畫面中，您可以看到要求原則執行的服務 (協調流程)、協調流程的識別碼、原則執行的時間，以及原則的識別碼。  
  
     ![BRE &#45;逐步解說 &#45;PolicyExecDetails](../core/media/a65fd48f-2a54-4cc5-9b45-4cd3c211da33.gif "a65fd48f-2a54-4cc5-9b45-4cd3c211da33")  
  
8. 按一下**事實活動**查看事實 （資料） 已判斷提示至規則引擎的工作記憶體與已從規則引擎工作記憶體撤回的事實。  
  
     ![BRE &#45;逐步解說 &#45;FactActivity](../core/media/27bc0d84-f202-4f5a-87a1-8b53006b3cee.gif "27bc0d84-f202-4f5a-87a1-8b53006b3cee")  
  
9. 在**檔案**功能表上，按一下 **瀏覽回**。  
  
10. 按一下**條件評估**。 您會看到有關所評估之條件的詳細資料。 在這種情況下，原則中有兩個規則，且每個原則具有一個條件。 您可以看到，評估兩個條件。其中一個評估為`true`，和另一個評估為`false`。  
  
     ![BRE &#45;逐步解說 &#45;ConditionEvaluation](../core/media/ac772d01-919f-4b22-995b-409501a96848.gif "ac772d01-919f-4b22-995b-409501a96848")  
  
11. 在**檔案**功能表上，按一下 **瀏覽回**。  
  
12. 按一下**議程更新**。 您可以看到只有 ApprovalRule 會新增至議程。 DeniedRule 不會加入到議程因為其條件評估為`false`。  
  
     ![BRE &#45;逐步解說 &#45;議程](../core/media/bc85d9ea-fc76-44de-aa75-134f47a5ec20.gif "bc85d9ea-fc76-44de-aa75-134f47a5ec20")  
  
13. 按一下**ApprovalRule**以查看 ApprovalRule 的定義。  
  
14. 在**檔案**功能表上，按一下 **瀏覽回**。  
  
15. 在**檔案**功能表上，按一下 **瀏覽回**一次。  
  
16. 按一下**規則引發**。 您可以看到只有 ApprovalRule 已經引發 (已執行 ApprovalRule 的動作)。  
  
17. 在**檔案**功能表上，按一下 **瀏覽回**。  
  
18. 按一下**未引發的規則**。 您可以看到 DeniedRule 並未引發，因為它不在議程之中。  
  
19. 重複步驟 1-18 與**SamplePO2.xml**。  
  
## <a name="key-details"></a>索引鍵的詳細資料  
  
-   追蹤資訊的原則是非常類似於您在商務規則編輯器 」 中測試原則時看到的追蹤資訊。  
  
-   雖然協調流程的名稱是 RuleTest.odx，但您看到的協調流程名稱卻是 Orchestration_1，因為協調流程的「類型名稱」是設定為 Orchestration_1，即使變更「名稱」也是如此。 追蹤中會顯示您的協調流程的名稱格式\<命名空間\>。\<輸入名稱\>。  
  
-   當您使用 BizTalk Server 管理主控台從 BizTalk 應用程式刪除原則時，該工具不但會從應用程式刪除原則，也會將該原則從規則引擎資料庫刪除。 您將無法再於「商務規則編輯器」中看到該原則 (請按 F5 以重新整理畫面)。 因此，從應用程式刪除原則時應該相當謹慎。  
  
-   當您停止 RuleTestApp 並選取**完全停止**選項時，ProcessPurchaseOrder 原則 （版本 1.3） 會自動解除部署。  
  
-   如果原則是由多個應用程式所使用，您應該針對此原則建立一個個別的應用程式，然後從用戶端應用程式建立該應用程式的參考。 如果將該原則加入所有的用戶端應用程式，則在您停止其中一個用戶端應用程式時，該原則就會解除部署，所有其他的用戶端應用程式都無法再使用該原則。 因此，針對兩個或兩個以上應用程式所共用的原則建立個別的應用程式，是較理想的作法。  
  
-   當您啟動 RuleTestApp 時，ProcessPurchaseOrder 原則 (版本 1.3) 會自動部署。  
  
## <a name="next-steps"></a>後續步驟  
 既然您已完成此逐步解說，請移至[逐步解說： 部署原則](../core/walkthrough-deploying-the-policy.md)逐步解說，它可讓您部署原則的逐步指示。  
  
## <a name="see-also"></a>請參閱  
 [如何設定原則的追蹤](../core/how-to-configure-tracking-for-a-policy.md)   
 [管理原則](../core/managing-policies.md)