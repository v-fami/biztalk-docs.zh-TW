---
title: 逐步解說： 修改的原則 |Microsoft 文件
ms.custom: ''
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9dd74440-2a45-4a1a-8e36-98796e1e1392
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7292d541adaf0ae2242d1c504f1a845dde66f5dd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289670"
---
# <a name="walkthrough-modifying-the-policy"></a>逐步解說： 修改原則
本逐步解說提供建立新版的逐步指示**POVocabulary**，建立新版本的**ProcessPurchaseOrder**原則，並使用最新版**POVocabulary**在新版的**ProcessPurchaseOrder**原則。  
  
## <a name="prerequisites"></a>必要條件  
 您必須先完成[逐步解說： 將規則新增至原則](../core/walkthrough-adding-a-rule-to-the-policy.md)逐步解說，然後再執行本逐步解說。  
  
## <a name="overview-of-this-walkthrough"></a>此逐步解說的概觀  
 此逐步解說包含三個程序，如下表所示。  
  
|程序標題|程序說明|  
|---------------------|---------------------------|  
|若要修改 POVocabulary 詞彙|提供逐步指示來建立新的詞彙版本的值修改為**允許的項目數目上限**從**500**至**1000年**。|  
|若要修改 ProcessPurchaseOrder 原則來使用更新的詞彙|提供建立新版的逐步指示**ProcessPurchaseOrder**原則以使用新版本的**POVocabulary**。|  
|測試方案|提供測試方案及驗證新原則已生效的逐步指示。|  
  
### <a name="to-modify-the-povocabulary-vocabulary"></a>若要修改 POVocabulary 詞彙  
  
1.  在**啟動**功能表中，開啟**商務規則編輯器 」**。 如果您有商務規則編輯器已開啟，請按 F5 或按一下**重新載入**上**檔案**重新整理的功能表。  
  
    > [!NOTE]
    >  在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。 若要這樣做，應用程式，以滑鼠右鍵按一下，然後選取**系統管理員身分執行**。  
  
2.  在 [事實總管] 視窗中，依序展開**詞彙**，然後展開**POVocabulary**。  
  
3.  以滑鼠右鍵按一下**1.0 版-已發佈**，然後按一下 **複製**。  
  
4.  以滑鼠右鍵按一下**POVocabulary**，然後按一下 **貼上詞彙版本**。  
  
5.  按兩下**數目的項目允許的最大**中**版本 1.1 （未儲存）** 啟動 [詞彙定義精靈]。  
  
6.  按一下 **[下一步]**。  
  
7.  按一下 **[下一步]**。  
  
8.  將值從變更**500**至**1000年**。  
  
9. 按一下 **[完成]**。  
  
10. 以滑鼠右鍵按一下**版本 1.1 （未儲存）**，然後按一下 **儲存**。  
  
11. 以滑鼠右鍵按一下**1.1 版**，然後按一下 **發行**。  
  
### <a name="to-modify-the-processpurchaseorder-policy-to-use-the-updated-vocabulary"></a>若要修改 ProcessPurchaseOrder 原則來使用更新的詞彙  
  
1.  在 [原則總管] 中，展開**原則**，然後展開**ProcessPurchaseOrder**。  
  
2.  以滑鼠右鍵按一下**1.2 版**，然後按一下 **複製**。  
  
3.  以滑鼠右鍵按一下**ProcessPurchaseOrder**，然後按一下  **pastepolicyversion**。  
  
4.  按一下**ApprovalRule**中 **（未儲存） 1.3 版**。  
  
5.  在 [事實總管] 中，展開**詞彙**，依序展開**POVocabulary**，然後展開**1.1 版-已發佈**。  
  
6.  拖曳**數目的項目允許的最大**中**1.1 版-已發佈**取代**數目的項目允許的最大**IF 窗格中的 版本 1.0。  
  
7.  重複步驟 4-6 **DeniedRule**。  
  
8.  以滑鼠右鍵按一下 **（未儲存） 1.3 版**，然後按一下 **儲存**。  
  
9. 以滑鼠右鍵按一下**1.3 版**，然後按一下 **發行**。  
  
10. 以滑鼠右鍵按一下**1.3 版**，然後按一下 **部署**。  
  
### <a name="to-test-the-solution"></a>測試方案  
  
1.  按一下**啟動**，開啟**BizTalk Server 管理**。 如果已經開啟 BizTalk Server 管理主控台，請按 F5 重新整理它。  
  
2.  以滑鼠右鍵按一下**RuleTestApp**，然後按一下 **啟動**。 如果**啟動**是停用，應用程式已經在執行且您可以略過下一個步驟。  
  
3.  按一下 **[啟動]**。  
  
4.  複製**SamplePO2.xml**檔案從 C:\BRE-Walkthroughs 目錄到 C:\BRE-Walkthroughs\RuleTestSol\Input 目錄，協調流程。  
  
5.  您應該會在 C:\BRE-Walkthroughs\RuleTestSol\Output 目錄中看到輸出檔。 開啟輸出 XML 檔案，並請注意，值**狀態**欄位設定為**Approved**。  
  
    > [!NOTE]
    >  值**數量**SamplePO2.xml 中的欄位為 700。 1.3 版**ProcessPurchaseOrder**原則會比較此值與 1000，而不是比較它與 500 1.2 版一樣。  
  
## <a name="comments"></a>註解  
  
-   已發佈的原則便無法加以修改。 您必須建立新版的原則，才能加以修改。 同樣地，已發佈的詞彙便無法加以修改。 您必須建立新版的詞彙，才能加以修改。  
  
-   協調流程叫用原則使用**呼叫規則**圖形會使用最新部署的原則版本。 例如，如果您已部署 1.0、1.1、1.2 和 1.3 版的原則，則協調流程會使用 1.3 版。 如果未部署 1.3 版，但是已部署 1.2 版，則協調流程會使用 1.2 版。 因此，如果您想要切換回 1.2 版，只需要解除部署 1.3 版，並確定 1.2 版已經部署。  
  
-   若要使用特定版本的原則，以從協調流程，您應該使用**運算式**圖形，並叫用規則引擎來執行原則以程式設計方式使用**Policy.Execute**方法。  
  
-   請注意，1.3 版的原則會使用來自 1.0 和 1.1 版 POVocabulary 詞彙的詞彙定義。 如果您將 1.3 版的原則匯出到 XML 檔案，並在另一部電腦上匯入它來建立原則，則此匯入程序會尋找這兩個版本的詞彙。 因此，在您匯入 1.3 版的原則之前，必須先匯出 1.0 和 1.1 版的詞彙，並將其匯入。  
  
-   在您部署更新版的原則之後，您應該等候大約 60 秒鐘，才能開始測試方案。 根據預設，規則引擎更新服務會每隔 60 秒鐘 (1 分鐘) 尋找一次原則的任何更新。 如果有更新，它會以更新的資訊重新整理快取。  
  
## <a name="next-steps"></a>後續步驟  
  
-   現在您已完成此逐步解說中，執行[逐步解說： 追蹤原則執行](../core/walkthrough-tracking-policy-execution.md)逐步解說，它提供追蹤原則執行細節的逐步指示。