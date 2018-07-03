---
title: 如何建立另一個節點或類型的參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c60be9ad-01a9-40e7-b43b-8c3d09bbb32f
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 025826673538b0272c3ce79d6e748c559b3eefe7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984455"
---
# <a name="create-references-to-another-node-or-type"></a>建立另一個節點或類型的參考
您可以使用全域節點建立可重複使用的資料型別 (結構片段)，以在適合該結構的結構描述中使用。 您可以只使用節點的直接子系**結構描述**來建立全域類型的節點。  
  
 您也可以建立使用資料類型的節點不是直接子系的循環參考**結構描述**節點。 這在結構描述中代表遞迴結構時很有用。  
  
 本主題提供各種全域節點類型及如何參照它們來加以使用的逐步說明。  
  
 **建立全域宣告**  
  
 您可以使用記錄、欄位或屬性，建立全域類型。 從記錄建立的全域類型只能用在記錄，從欄位建立的類型只能用在欄位，而從屬性建立的類型只能用在屬性。 下列程序說明如何定義和使用全域宣告。  
  
## <a name="create-a-global-declaration-from-a-node"></a>從節點建立全域宣告  
  
1.  選取 **記錄**， **Field 屬性**，或**欄位項目**節點類型，您想要變更為全域。  
  
2.  在**屬性** 視窗中，輸入的名稱，在**資料結構型別**清單會用作複雜類型中，全域名稱，然後按 ENTER 鍵。  
  
## <a name="create-a-globally-defined-sequence-group-node-choice-group-node-or-all-group-node"></a>建立全域定義的 Sequence 群組 節點、 Choice 群組 節點中或 All 群組節點  
  
1.  選取 **記錄**您要在其中插入全域定義的群組節點的節點。  
  
2.  在上**BizTalk**功能表上，指向**插入結構描述節點**，然後按一下**Sequence 群組**， **Choice 群組**，或**所有群組**視需要。  
  
3.  在新插入的群組中建立結構。 例如，插入**記錄**或是**欄位項目**節點，以表示群組節點內的資料結構。  
  
    > [!NOTE]
    >  Sequence 群組**Choice 群組**，並**All 群組**節點只能包含節點對應至 XML 項目，因此不能包含**欄位屬性**節點。  
  
4.  選取在步驟 2 插入的群組節點  
  
5.  在 屬性 視窗中，按一下**Group Reference**，在 值 欄位中，輸入名稱，然後按 ENTER。  
  
     藉由提供中的名稱**Group Reference**屬性，就能全域定義群組節點之後，您可以將其他群組節點與此全域定義的類型 （結構）。  
  
## <a name="create-a-globally-defined-attribute-group-node"></a>建立全域定義的屬性群組節點  
  
1.  選取 **記錄**您想在其中插入全域定義的節點**屬性群組**節點。  
  
2.  在  **BizTalk**功能表上，指向**插入結構描述節點**，然後按一下**屬性群組**。  
  
     這會新增**屬性群組**節點中所選的子節點結尾**記錄**節點。  
  
3.  新增適當**Field 屬性**或是**屬性群組**節點，以您**屬性群組**。  
  
4.  （選擇性） 如果您想要重新命名**屬性群組**節點中，選取**屬性群組**節點，並變更其**Group Reference**您所選擇的新名稱的屬性。  
  
     屬性群組一律為全域性，且在使用時會從其位置參照。  
  
## <a name="use-a-type-or-group-that-has-been-globally-defined"></a>使用型別或已全域定義的群組  
  
1. 選取要使用全域定義類型的節點。  
  
2. 在 屬性 視窗中，從下拉式清單選取 全域定義的型別**資料結構型別**屬性 (**記錄**節點)，**資料類型**屬性 (**欄位項目**並**Field 屬性**節點)，或**Group Reference** (**Sequence 群組**， **Choice 群組**，**所有群組**，並**屬性群組**節點)。 這些屬性的更多有關[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
   > [!NOTE]
   >  您可以在全域定義的類型或群組出現的任何結構描述位置，對其進行後續的變更。 在這些位置的單一任意位置中進行變更時，會在所有這類位置上套用變更。  
  
   建立全域宣告之後，您無法在單一步驟中刪除它。 不過，您可以藉由刪除它**清除全域資料型別**儲存結構描述時，使用下列程序 對話方塊。  
  
## <a name="delete-a-global-declaration"></a>刪除全域宣告  
  
1.  刪除使用此全域類型或群組的所有節點，或指定不同的類型或群組供所有這些節點使用，或將兩種方法的組合使用。 如需刪除節點的逐步指示，請參閱[刪除節點](../core/how-to-delete-nodes.md)。  
  
2.  儲存您的規格時**清除全域資料型別** 對話方塊隨即出現。 選取您要完全刪除從您的規格，然後按一下 全域宣告**確定**。  
  
    > [!NOTE]
    >  **清除全域資料型別** 對話方塊隨即出現，每次您未使用的資料類型與儲存結構描述。 若未出現此對話方塊，則表示結構描述中的其他位置已使用所有的資料型別，或是結構描述自開啟後未曾修改過 (在後者的情況中，它可能仍包含先前保留的未使用資料型別)。  
  
## <a name="create-cyclical-references-to-another-node"></a>建立另一個節點的循環參考  
 您可以建立節點的循環參考來代表遞迴的結構描述項目。 若要這麼做，您可以建立一個類型由封閉式記錄所定義的節點。 例如，假設有一個執行個體訊息是包裝在具有相同結構的任意數目信封中。 使用循環參考時，您可以建立一個定義此種執行個體訊息的結構描述。  
  
### <a name="create-a-cyclical-reference"></a>建立循環參考  
  
1.  選取 **記錄**您要建立遞迴參考的節點。 這是代表遞迴結構頂端的節點。  
  
2.  在 [屬性] 視窗中，確認**資料結構型別**的值。  
  
     確認**記錄**具名節點都有與其相關聯的類型是必要的因為遞迴結構在類型包含其本身時定義。 只有透過巢狀方式使用具名的全域類型，類型才能包含其本身。  
  
3.  選取子系**記錄**節點或插入子系**記錄**節點。  
  
4.  子系**記錄**節點，在 [屬性] 視窗中，在**資料結構型別**清單中，選取在步驟 2 中識別的資料結構。  
  
> [!IMPORTANT]
>  - **Min Occurs**重複的節點屬性必須設定為零 (**0**)。 將它設定為其中一個 (**1**) 會造成無限迴圈。  
>
>  - 匯入包含遞迴項目的結構描述時，「BizTalk 編輯器」並不會自動檢查來確認遞迴項目是否有效。  
  
## <a name="see-also"></a>另請參閱  
 [管理結構描述中的節點](../core/managing-the-nodes-within-a-schema.md)