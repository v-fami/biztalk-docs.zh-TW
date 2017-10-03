---
title: "如何設定 「 轉換 」 圖形 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [Orchestration Designer], Transform shape
- Transform shape [Orchestration Designer]
ms.assetid: ca81d153-77a6-4bcc-b14f-8f48469fffe0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 48cdca50620262581469e924fbb2975dde7e91fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-transform-shape"></a>如何設定轉換圖形
![](../core/media/ebiz-orch-transform.gif "ebiz_orch_transform")  
轉換圖形  
  
 當您建構訊息，因此時，才會使用轉換程式**轉換**圖形只會出現在**建構訊息**圖形。 您可以卸除**建構訊息**圖形設計介面上，然後再卸除**轉換**圖形內，或者您可以只需卸除**轉換**設計上的圖形介面和建立封入協調流程設計師 」 將**建構訊息**圖形。  
  
> [!NOTE]
>  中的任何來源或目的訊息**轉換**必須根據結構描述。  
  
## <a name="procedure"></a>程序  
  
#### <a name="to-configure-a-transform-shape"></a>設定轉換圖形  
  
1.  在 [屬性] 視窗中，按一下**省略**(**...**) 按鈕**輸入訊息**，**輸出訊息**，或**對應名稱**屬性。  
  
2.  使用**轉換組態**對話方塊來設定**轉換**圖形。  
  
> [!NOTE]
>  A**轉換**圖形只能存在於**建構訊息**圖形。 如果您拖曳**訊息指派**圖形設計介面上，其他地方新**建構訊息**圖形將會建立。  
  
### <a name="important-performance-considerations"></a>重要的效能考量  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 藉由在套用轉換時 (而非將整個文件載入記憶體時) 將文件資料流處理至記憶體的方式，最佳化在大型訊息上執行轉換的能力。 這項最佳化能夠對應/轉換比舊版 BizTalk Server 所能處理的更大型文件。 當協調流程接受轉換圖形的多個輸入及/或輸出時，此最佳化的效果會受到限制。  
  
 如果協調流程接受轉換圖形的多個輸入及/或輸出，便不會執行文件資料流處理，且記憶體用量會增加。 這個問題可行的解決方法之一就是在接收管線套用一或多個轉換，如此一來協調流程將永不接受一個以上的轉換圖形輸入或輸出。  
  
### <a name="newexisting-map-file"></a>新的/現有的對應檔案？  
 在本節中，您可以按一下 **新對應**或**現有對應**選項按鈕，選取要指派給對應**轉換**圖形。  
  
 使用**名稱**欄位下方選取的選項按鈕，以指定對應。 如果您選取**新對應**，您可以輸入您想要指派的對應的目的地。 當您使用**新對應**選項，您必須在文字方塊中指定對應的完整的名稱。 在文字方塊中預設會顯示這類名稱的範例，因為它是根據專案命名空間的唯一識別項名稱預先填入和**轉換**圖形名稱：\<專案命名空間 >。\<轉換圖形名稱 > _ m a p (例如 MyProject.Transform3_Map)。  
  
 如果您選取**現有對應**，按一下向下的箭號，在**名稱**欄位來選取要使用的對應檔。 這個清單方塊會依字母順序顯示專案中所有現有對應的排序清單。 在此清單中，如果您按一下文字\<從參考組件選取 >，則**選取成品類型**對話方塊隨即出現。 多個可用選項的相關資訊，請參閱[如何使用選取成品類型對話方塊](../core/how-to-use-the-select-artifact-type-dialog-box.md)。  
  
### <a name="select-source-and-destination-messages"></a>選取來源訊息和目的訊息  
 使用此部分**轉換組態**對話方塊來設定您在選取的對應**新的/現有對應檔案？** > 一節。 如果您選取**新對應**在該區段中，您會建立對應藉由設定這一節。  
  
 如果您選取**現有對應**，您可以使用本節來進行下列兩個步驟：  
  
-   選取現有對應，於目前轉換中依原狀重複使用。  
  
-   選取現有對應，變更 (重新設定) 該對應，然後將對應運用在目前轉換的新設定中。  
  
 使用指定來源和目的訊息**來源訊息**和**目的訊息**方格控制項。 您可以使用這些方格控制項以數種方式變更對應檔案。 如果您刪除訊息 (也就是兩個方格控制項中的列)、新增訊息或選取不同類型的訊息，您就改變了對應的結構。 當您改變對應的結構時，必須變更所有其他使用該結構的轉換，以符合對應的新結構。 其他變更 (例如移除訊息和插入相同類型的訊息) 則不會改變對應的結構。  
  
 **來源訊息**和**目的訊息**方格控制項是相同的外觀和行為。 每個方格控制項都有兩個資料行：訊息和類型。 您可以選取訊息資料行中的訊息以填入方格控制項 (請只在訊息資料行加入資料，因為類型資料行是唯讀的)。訊息資料行中的儲存格具有下拉式清單，此清單已填入了目前協調流程範圍內的訊息執行個體。  
  
 您也可以按一下任一方格控制項中選取一個資料列*向右箭號*方格控制項左側 (>) 按鈕。 在選取一列之後，您可以按下 DELETE 鍵以刪除列。 刪除列 (訊息) 會改變包含它之對應檔案的結構。 您只可以修改對專案而言是本機的對應檔案。  
  
### <a name="when-i-click-ok-launch-the-biztalk-mapper"></a>當我按 [確定] 時，啟動 BizTalk 對應工具  
 按一下**當我按 [確定] 時，啟動 BizTalk 對應工具**會自動開啟 BizTalk 對應工具，當您按一下**確定**關閉**轉換組態**對話方塊並儲存您的變更。 但是，如果沒有填寫必要的資訊，您便無法儲存變更。 在此情況下，完成填寫對話方塊中的欄位，然後按一下 **確定**。  
  
## <a name="see-also"></a>另請參閱  
 [關於對應](../core/about-maps.md)   
 [建構訊息](../core/constructing-messages.md)   
 [如何使用運算式動態地轉換訊息](../core/how-to-use-expressions-to-dynamic-transform-messages.md)