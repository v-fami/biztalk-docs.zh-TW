---
title: "私用程序協調流程中定義的商務規則 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, policies
- vocabularies, saving
- private processes, orchestrations
- business rules, private processes
- creating, vocabularies
- vocabularies, business rules
- business rules, vocabularies
- policies, deploying
- vocabularies, creating
- orchestrations, private-process orchestrations
- private processes, customizing
- policies, publishing
- business rules, Set elements
- creating, policies
- customizing private processes
- Set elements
- business rules, orchestrations
- publishing, vocabularies
- vocabularies, publishing
- creating, rules
- business rules, Get elements
- policies, saving
- publishing, policies
- Get elements
- orchestrations, business rules
- rules
- private processes, business rules
- policies, creating
ms.assetid: 5d2b0257-1b15-482b-a562-798b808e9a2d
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8dd0ebb22bcf6253604e4e8bf7fd858deb776b0
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="defining-a-business-rule-for-a-private-process-orchestration"></a>私用程序協調流程中定義的商務規則
您可以定義要在通知私用程序中使用的商務規則。 這讓您可以動態地修改商務規則，而不需停止私用程序協調流程。 這個程序會使用「[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 商務規則引擎」。 這個程序包含下列步驟：  
  
1.  加入新詞彙。 這需要定義至少一個詞彙常數值。 這會設定商務規則閾值， 也需要定義 XML 文件 `Get` 和 `Set` 項目。 這會建立如何[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]使用臨界值。  
  
2.  加入新原則。 這需要建立一個原則和一組規則，然後再儲存、發佈及部署該原則。  
  
3.  從私用程序協調流程呼叫商務規則。 此涉及新增**呼叫規則**圖形至協調流程。  
  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK 包含的範例，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]商務原則、 samplebtarnpolicy.xml 中\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for rosettanet\sdk\pipautomation\3a4。 如需詳細資訊，請參閱[BTARN 商務原則範例](../../adapters-and-accelerators/accelerator-rosettanet/sample-btarn-business-policy.md)。  
  
 PIP3A4PrivateResponder.odx 範例屬於私用程序協調流程，示範如何實作特定夥伴介面程序 (PIP) 的回應者私用程序，以整合商務規則。 如需有關此範例的詳細資訊，請參閱[3A4 私用回應者協調流程使用商務規則](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)。  
  
 如需有關詞彙和原則的詳細資訊，請參閱 BizTalk Server 中的 < 開發與商務規則 > 主題。  
  
### <a name="to-add-a-new-vocabulary"></a>加入新詞彙  
  
1.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下 **商務規則編輯器 」**。  
  
2.  如果**開啟規則存放區**對話方塊隨即開啟，請選取**BizTalk 規則引擎**資料庫，您目前的伺服器上設定，然後按一下**確定**。  
  
3.  在[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]商務規則編輯器 」，在 [事實總管] 窗格中，以滑鼠右鍵按一下**詞彙**，然後按一下 **新增詞彙**。  
  
4.  在 [屬性] 窗格 （左下方），設定**名稱**屬性名稱的適當的詞彙，然後按下**Enter**。  
  
5.  展開您剛才建立的詞彙資料夾，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下 **新增定義**。  
  
6.  在**詞彙定義精靈**頁面上，選取**常數值、 值的範圍或值的集合**，然後按一下 **下一步**。  
  
7.  在**常數值、 值的範圍或值的集合**頁面上，於**定義名稱**方塊中，輸入適當詞彙常數值的名稱，例如**數量允許的最大**，然後按一下 **下一步**。  
  
8.  在**定義常數值**頁面上，於**值欄位**方塊中輸入臨界值，然後再按一下**完成**。  
  
### <a name="to-define-get-and-set-elements"></a>定義 Get 和 Set 項目  
  
1.  商務規則編輯器 中的事實總管 窗格中，在 要加入新詞彙程序，建立的詞彙資料夾底下以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下 **新增定義**.  
  
2.  在**詞彙定義精靈**頁面上，選取**XML 文件項目或屬性**，然後按一下 **下一步**。  
  
3.  在**XML 文件項目或屬性** 頁面上，在 定義名稱 文字方塊中輸入的名稱**取得**項目。  
  
4.  按一下**瀏覽**，移至您想要使用選取結構描述檔案，然後按一下 結構描述的位置**開啟**。  
  
5.  如果**選取根節點**頁面隨即開啟，請選取要瀏覽的根節點。  
  
6.  在**選取繫結**頁面上，移到您要定義的臨界值的欄位，然後按一下**確定**。  
  
7.  在**文件類型**方塊中，輸入文件的名稱。  
  
8.  在**作業類型**區段中，選取**執行 「 取得 」 作業**。  
  
9. 按一下 **[完成]**。  
  
10. 重複這些步驟，以定義一個或多個`Set`作業中，選取**執行 「 設定 」 作業**如**作業類型**。  
  
### <a name="to-save-and-publish-the-vocabulary"></a>儲存和發佈詞彙  
  
1.  在商務規則編輯器，在 事實總管 窗格中，您建立詞彙資料夾底下以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下 **儲存**。  
  
2.  在事實總管 窗格的 3a4purchaseordervocabulary 資料夾底下，以滑鼠右鍵按一下**1.0 版**，然後選取**發行**。  
  
### <a name="to-add-a-new-policy-and-rules"></a>加入新原則和規則  
  
1.  在商務規則編輯器] 中 [原則總管] 窗格中，以滑鼠右鍵按一下**原則**，然後按一下 [**新增原則**。  
  
2.  按一下**[policy1]**。  
  
3.  在 [屬性] 窗格中，設定**名稱**屬性設為適當的原則名稱。  
  
4.  在 [原則總管] 窗格中，為新的原則] 資料夾底下以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下 [**新增規則**。  
  
5.  按一下**Rule1**。  
  
6.  在 [屬性] 窗格中，設定**名稱**規則名稱的屬性，然後再按**Enter**。  
  
7.  在 規則編輯器 下**如果** 窗格中，以滑鼠右鍵按一下**條件**，如果適當，然後選取的邏輯條件。  
  
8.  在事實總管 窗格中，在**詞彙**，依序展開**述詞**，依序展開**1.0 版-已發佈**，選取您想要將它拖曳至編輯器介面，則述的詞然後將它放在**條件**或邏輯運算子。  
  
9. 在 [事實總管] 窗格中，詞彙資料夾底下，依序展開您所建立的詞彙、 **1.0 版-已發佈**，選取`Get`或`Set`項目，將它拖曳至編輯器介面，並將它放在**引數 1**。  
  
10. 在 [詞彙] 資料夾底下選取`Get`或`Set`項目，將它拖曳至編輯器介面並將它放在**引數 2**。  
  
11. 在 [詞彙] 資料夾底下選取`Set`項目，將它拖曳至編輯器介面，並將其放置**動作**方塊 [THEN] 窗格中。  
  
12. 如果變數相關聯`Set`項目，按一下變數，請視需要變更，然後按**Enter**。 如果適當，請對其他 `Set` 項目重複執行上述步驟。  
  
### <a name="to-save-publish-and-deploy-the-policy"></a>儲存、發佈和部署原則  
  
1.  當您完成定義商務規則編輯器 中的規則，在原則總管 窗格中，您建立原則資料夾下，以滑鼠右鍵按一下**版本 1.0 （未儲存）**，然後按一下 **儲存**。  
  
2.  在 原則總管 窗格中，您建立原則資料夾下滑鼠右鍵按一下**1.0 版**，然後按一下 **發行**。  
  
3.  在 原則總管 窗格中，您建立原則資料夾下滑鼠右鍵按一下**1.0 版**，然後按一下 **部署**。  
  
### <a name="to-call-the-business-rule-from-the-orchestration"></a>從協調流程呼叫商務規則  
  
1.  啟動**Microsoft Visual Studio 2012**。  
  
2.  在**檔案**功能表上，指向 [開啟]，然後**專案/方案**。  
  
3.  找出包含協調流程，您必須呼叫，從商務規則，然後按一下方案**開啟**。  
  
4.  按一下**檢視**，指向 **其他視窗**，然後按一下 **協調流程檢視**。  
  
5.  展開**變數**。 請確認協調流程變數清單含有對應至商務原則 (您從協調流程呼叫的商務原則) 中每個參數的變數。 確認變數類型與原則參數相同。 如果清單未包含協調流程變數的每個原則參數，以滑鼠右鍵按一下**變數**，然後按一下 **新變數**。 在 [協調流程檢視] 中，輸入變數名稱，然後在 [屬性] 視窗中，輸入參數的類型。  
  
6.  從**工具箱**，拖曳**呼叫規則**圖形至協調流程設計介面，然後再卸除在**接收**圖形。  
  
7.  按兩下**呼叫規則**圖形。  
  
8.  在**選取您想要呼叫的商務原則**方塊中，從下拉式清單中選取的商務原則。  
  
9. 第一個參數會顯示，如**參數名稱**，從下拉式清單中選取名稱。  
  
    > [!NOTE]
    >  BTARN 會填入**原則參數**商務原則中的所有參數的清單。 每個參數清單中，BTARN 輸入中的值**參數型別**透過商務原則。 與相關聯的下拉式清單中**參數名稱**，BTARN 從與原則參數相同類型的協調流程變數清單輸入所有的變數名稱。 藉由選取協調流程變數，就能與原則參數產生關聯。 您可以在 [協調流程檢視] 中檢視這些協調流程變數。  
  
10. 對所有其他參數重複執行步驟 9。  
  
11. 在 [協調流程設計] 視窗中，輸入與商務原則，包括加入相關聯的處理所需的所有其他圖形**決策**圖形下**呼叫規則**圖形。  
  
    > [!NOTE]
    >  如需如何使用的範例**呼叫規則**圖形的協調流程中，請參閱 BTARN SDK 隨附的 PIP3A4PrivateResponder.odx 協調流程。 它位於\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\PipAutomation\3A4\PR。 如需詳細資訊，請參閱[3A4 私用回應者協調流程使用商務規則](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)。  
  
12. 按一下 **[確定]**。  
  
## <a name="see-also"></a>請參閱  
 [程式設計手冊](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)   
 [BTARN 商務原則範例](../../adapters-and-accelerators/accelerator-rosettanet/sample-btarn-business-policy.md)   
 [使用商務規則的 3A4 私用回應者協調流程](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)