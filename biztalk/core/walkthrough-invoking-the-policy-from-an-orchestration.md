---
title: 逐步解說： 叫用的協調流程的原則 |Microsoft Docs
ms.custom: ''
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb2d2974-8a36-4d36-905c-799e4236ef99
caps.latest.revision: 30
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 33bef51b2c702e71fcf6ef0ea0c4fd63b28fbde8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976553"
---
# <a name="walkthrough-invoking-the-policy-from-an-orchestration"></a>逐步解說： 叫用原則與協調流程
您可以使用下列其中一種方式，從協調流程叫用原則：  

- 藉由使用**呼叫規則**圖形  

- 藉由使用**運算式**圖形，並以程式設計方式叫用規則引擎來執行原則 (**Policy.Execute**方法)  

  使用**呼叫規則**圖案是最常見的方式，而叫用原則，以從協調流程的建議的方式。 本逐步解說提供逐步程序使用**呼叫規則**圖形來叫用**ProcessPurchaseOrder**原則。  

## <a name="prerequisites"></a>必要條件  
 您必須先完成[逐步解說： 測試原則](../core/walkthrough-testing-the-policy.md)逐步解說，然後再執行本逐步解說。  

## <a name="overview-of-this-walkthrough"></a>此逐步解說的概觀  
 此逐步解說包含七個程序，如下表所示。  

|程序標題|程序說明|  
|---------------------|---------------------------|  
|使用結構描述和協調流程建立 BizTalk 專案|提供逐步指示來建立結構描述和協調流程叫用**ProcessPurchaseOrder**原則。|  
|建立訊息變數|提供逐步指示，說明如何建立協調流程中所使用的訊息變數。|  
|設定圖形|提供逐步指示，說明如何在協調流程中設定圖形。|  
|建立連接埠|提供逐步指示，說明如何在協調流程中建立連接埠。|  
|連接連接埠與圖形|提供逐步指示，說明如何連接連接埠與圖形。|  
|建置和部署解決方案|提供逐步指示，說明如何建置和測試解決方案。|  
|測試方案|提供測試方案的逐步指示。|  

### <a name="to-create-a-biztalk-project-with-a-schema-and-an-orchestration"></a>使用結構描述和協調流程建立 BizTalk 專案  

1. 開始**Microsoft Visual Studio**。  

2. 在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**新增**，然後按一下 **專案**。  

3. 在 **新的專案**對話方塊方塊中，執行下列動作：  


   |             使用              |                             以進行此動作                              |
   |-----------------------------------|---------------------------------------------------------------------|
   |         **專案類型**         |                     按一下  **BizTalk 專案**。                     |
   |           **範本**           |               按一下 **空白 BizTalk Server 專案**。               |
   |             **名稱**              |                         型別**RuleTest**。                          |
   |           **位置**            |                  指定**C:\BRE-Walkthroughs**。                   |
   |         **方案名稱**         |                        型別**RuleTestSol**。                        |
   | **為解決方案建立目錄** | 選取此核取方塊以建立方案檔案的目錄。 |


4. 按一下 [確定] 。 **RuleTest**專案應該會出現在 [方案總管] 中。 如果看不到方案總管 中，按一下**方案總管**上**檢視**功能表。  

5. 在 [方案總管] 中，以滑鼠右鍵按一下**RuleTest**，指向**新增**，然後按一下**現有項目**。  

6. 瀏覽並新增**PO.xsd**您在建立的結構描述檔案[逐步解說： 建立簡單商務原則](../core/walkthrough-creating-a-simple-business-policy.md)逐步解說。 Visual Studio 會建立一份**PO.xsd**檔案，並將它新增至專案。  

7. 在 [方案總管] 中，以滑鼠右鍵按一下**RuleTest**，指向**新增**，然後按一下**新項目**。  

8. 在 **加入新項目**對話方塊方塊中，執行下列動作：  


   |    使用    |            以進行此動作            |
   |----------------|----------------------------------|
   | **類別** |  按一下 **協調流程檔案**。  |
   | **範本**  | 按一下  **BizTalk 協調流程**。 |
   |    **名稱**    |      型別**RuleTest.odx**。      |


9. 按一下 **[加入]**。  

10. 以滑鼠右鍵按一下**從 [工具箱] 拖曳圖形**，指向**插入圖形**，然後按一下**接收**。  

11. 在 [屬性] 視窗中，變更名稱**接收**圖形至**ReceivePO**，並將值**啟動**屬性設`true`。  

12. 在工具箱中，在**BizTalk 協調流程**索引標籤，拖曳**呼叫規則**圖形下方的連接線到**接收**圖形。  

13. 在 [屬性] 視窗中，變更名稱**呼叫規則**圖形至**CallProcessPOPolicy**。  

14. 以滑鼠右鍵按一下下面的**呼叫規則**圖形中，指向**插入圖形**，然後按一下**傳送**。  

15. 在 [屬性] 視窗中，變更名稱**傳送**圖形至**SendPO**。 協調流程的外觀應該如下圖所示：  

     ![BRE&#45;逐步解說&#45;UnconfiguredOrch](../core/media/1f3502ac-82a9-40bf-ae31-6e8356a283e2.gif "1f3502ac-82a9-40bf-ae31-6e8356a283e2")  

### <a name="to-create-message-variables"></a>建立訊息變數  

1.  在 [協調流程檢視] 視窗中，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。 如果看不到協調流程檢視 視窗中，按一下**檢視**功能表上，指向**其他 Windows**，然後按一下**協調流程檢視**。 [協調流程檢視] 視窗通常是顯示在 [方案總管] 索引標籤旁邊的索引標籤上。根據預設，新的訊息會命名為**Message_1**。  

     ![BRE&#45;逐步解說&#45;OrchViewNewMsg](../core/media/a0b7fee3-af90-4c01-9464-146f0ca449e5.gif "a0b7fee3-af90-4c01-9464-146f0ca449e5")  

2.  在 [協調流程檢視] 視窗中，按一下**Message_1**。  

3.  在 [屬性] 視窗中，執行下列步驟：  

    |使用|以進行此動作|  
    |--------------|----------------|  
    |**識別碼**|型別 **[poinst]**，然後按 ENTER 鍵。|  
    |**訊息類型**|從下拉式清單中，依序展開**結構描述**，然後選取**RuleTest.PO**。|  

     ![BRE&#45;Walkthrough&#45;MsgProps](../core/media/c82cfb67-63f6-4133-95bf-daadac0e213a.gif "c82cfb67-63f6-4133-95bf-daadac0e213a")  

### <a name="to-configure-shapes"></a>設定圖形  

1. 選取 **接收**協調流程設計師中的圖形。  

2. 在 [屬性] 視窗中，選取 **[poinst]** for**訊息**屬性。  

3. 按兩下**呼叫規則**協調流程設計師中的圖形。  

4. 在 **呼叫規則原則組態**對話方塊中，選取**ProcessPurchaseOrder**原則。  

5. 按一下 下一步**\\**<em>下面的 * * 參數名稱</em><em>，然後選取 **poinst</em>* 做為原則的參數。  

    ![BRE&#45;逐步解說&#45;ConfigureCallRules](../core/media/0e7dab04-41db-433b-bbf5-b13901033b41.gif "0e7dab04-41db-433b-bbf5-b13901033b41")  

6. 按一下 [確定] 。  

7. 選取 **傳送**協調流程中的圖形。  

8. 在 [屬性] 視窗中設定的值**訊息類型**屬性設 **[poinst]**。  

### <a name="to-create-ports"></a>建立連接埠  

1.  建立兩個資料夾**輸入**並**輸出**，在 C:\BRE-Walkthroughs\RuleTestSol 資料夾中。  

2.  以滑鼠右鍵按一下協調流程，在左側連接埠介面，然後按一下**新設定連接埠**。  

3.  按 [下一步] 。 型別 **[receivepoprt]** 連接埠名稱。  

4.  按一下 [**下一步]** 兩次。  

5.  選取 **立即指定**for**連接埠繫結**。  

6.  指定**檔案**for**傳輸**，然後輸入做為輸入的目錄名稱**C:\BRE-Walkthroughs\RuleTestSol\Input\\\*.xml**與檔案遮罩 (**\*.xml**) uri。  

7.  按 **[下一步]**，再按一下 **[完成]**。  

8.  以滑鼠右鍵按一下協調流程，在右側連接埠介面，然後按一下**新設定連接埠**。  

9. 按 [下一步] 。 型別**SendPOPort**連接埠名稱。  

10. 按一下 [**下一步]** 兩次。  

11. 變更**連接埠通訊方向**要**我將總是傳送的訊息在此連接埠**。  

12. 選取 **立即指定**for**連接埠繫結**。  

13. 指定**檔案**for**傳輸**，並輸入與輸出目錄的名稱**C:\BRE-Walkthroughs\RuleTestSol\Output**，和 %MessageID%.xml 與輸出檔案名稱。  

14. 按 **[下一步]**，再按一下 **[完成]**。  

### <a name="to-connect-ports-with-the-shapes"></a>連接連接埠與圖形  

1.  連接 **[receivepoprt]** 連接埠連接到**ReceivePO**圖形。 (將連接埠介面上 [ReceivePOPrt] 連接埠右邊的箭號，拖曳到 [ReceivePO] 上的方塊)。  

     ![BRE&#45;Walkthrough&#45;ConnectRP](../core/media/75bdf79e-ca98-43bb-8ff6-5f46005a6490.gif "75bdf79e-ca98-43bb-8ff6-5f46005a6490")  

2.  連接**SendPO**圖形至 **[sendpoprt]** 連接埠。  

     ![BRE&#45;Walkthrough&#45;ConnectSP](../core/media/7513f52b-2782-4357-b8eb-1874dec33869.gif "7513f52b-2782-4357-b8eb-1874dec33869")  

### <a name="to-build-and-deploy-the-solution"></a>建置和部署解決方案  

1. 開始**Microsoft Visual Studio**。  

2. 在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，在 [方案總管] 中，以滑鼠右鍵按一下**RuleTest**專案，然後再按一下**屬性**。  

3. 在 專案設計工具 （在中間窗格） 中，按一下**簽署**。  

4. 在 簽署 索引標籤，核取**簽署組件**核取方塊;在下拉式清單**選擇強式名稱金鑰檔**，按一下**新增**;在 **金鑰檔案名稱**欄位中，輸入規則測試;在 **密碼**欄位 （選擇性），設定密碼，然後按一下 **確定**。  

5. 在 專案設計工具中，按一下**部署**切換至 部署 索引標籤。  

6. 指定**RuleTestApp**做為應用程式名稱。  

    ![BRE&#45;逐步解說&#45;RuleTestApp](../core/media/b153e5b0-ca46-4d27-bfa1-9ad4e58e9787.gif "b153e5b0-ca46-4d27-bfa1-9ad4e58e9787")  

7. 按一下 [確定] 。  

8. 以滑鼠右鍵按一下**RuleTest**專案，然後再按一下**建置**。  

9. 以滑鼠右鍵按一下**RuleTest**專案，然後再按一下**部署**。  

### <a name="to-test-the-solution"></a>測試方案  

1. 在 商務規則編輯器 中，展開**原則**，展開**ProcessPurchaseOrder**，以滑鼠右鍵按一下**1.0 版**，然後按一下 **發行**.  

2. 以滑鼠右鍵按一下**1.0 版-已發佈**，然後按一下**部署**。  

3. 在 **開始**功能表中，開啟**BizTalk Server 管理**。 如果已經開啟 BizTalk Server 管理主控台，請按 F5 重新整理它。  

4. 依序展開**主控台根目錄**，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，展開**BizTalk 群組**，然後展開**應用程式**。  

5. 以滑鼠右鍵按一下**RuleTestApp**，然後按一下**設定**。  

6. 按一下  **Orchestration_1**，並指定**BizTalkServerApplication**為主機。  

    ![BRE&#45;逐步解說&#45;AppHost](../core/media/ba348a98-661f-4e71-8b9b-b8c5fadf035a.gif "ba348a98-661f-4e71-8b9b-b8c5fadf035a")  

7. 按一下 [確定] 。  

8. 以滑鼠右鍵按一下**RuleTestApp**，然後按一下**開始**。  

9. 在 [**啟動 'RuleTestApp' 應用程式**] 對話方塊中，按一下**開始**，應用程式已成功啟動，然後等到。  

10. 開啟**SamplePO.xml**並**SamplePO2.xml** [記事本] 中的值變更**狀態**欄位設為**XYZ**。  

11. 複製**SamplePO.xml**檔案從 C:\BRE-Walkthroughs 目錄到 C:\BRE-Walkthroughs\RuleTestSol\Input 目錄，協調流程。  

12. 您應該會在 C:\BRE-Walkthroughs\RuleTestSol\Output 目錄中看到協調流程的輸出檔。 開啟輸出 XML 檔案，並請注意，值**狀態**欄位設定為**Approved**。  

13. 重複步驟 11 和 12 與**SamplePO2.xml**，並請注意，值**狀態**輸出文件中的欄位是相同的輸入文件 (**xyz**)。  

## <a name="comments"></a>註解  

-   在此逐步解說中，將圖形新增至協調流程時，您並未使用 [工具箱] 中的圖形， 而是按一下滑鼠右鍵，並選取想要插入的圖形。  

-   組態**呼叫規則**圖形會判斷使用的型別時查看最新的儲存版本。 在執行階段，則將使用最新的已部署版本。  

-   如果您打算使用最新的部署版本以外的原則版本，您應該使用**運算式**圖形，並叫用規則引擎以程式設計方式來執行該特定版本的原則。 如需詳細資訊，請參閱 <<c0> [ 如何執行原則來](../core/how-to-execute-policies.md)。  

-   **呼叫規則**圖形會使用一樣，重新建構訊息**建構訊息**圖形，接著可能會導致遺失訊息內容屬性。  

-   您無法修改已發佈的原則。  

-   用戶端應用程式只能存取已部署的原則。 如果用戶端應用程式會叫用未部署的原則，就會產生 「 規則引擎**RuleEngineDeploymentNotDeployedException**例外狀況。 您可以在應用程式事件日誌中查看詳細的錯誤訊息。  

## <a name="next-steps"></a>後續步驟  
 既然您已完成本逐步解說中，執行[逐步解說： 建立和使用詞彙的原則中](../core/walkthrough-creating-and-using-a-vocabulary-in-the-policy.md)逐步解說，它可讓您建立的詞彙和使用詞彙的逐步指示**ProcessPurchaseOrder**原則。  

## <a name="see-also"></a>另請參閱  
 [條件評估與動作執行](../core/condition-evaluation-and-action-execution.md)   
 [議程與優先順序](../core/agenda-and-priority.md)   
 [在協調流程中叫用商務規則](../core/invoking-business-rules-in-orchestrations.md)