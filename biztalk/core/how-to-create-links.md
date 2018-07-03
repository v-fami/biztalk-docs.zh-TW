---
title: 如何建立連結 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 670b831f-be03-4612-93d5-a894f7bb3c11
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f7315b4cd568c6107dcab25cf1fe471428b58da8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014743"
---
# <a name="how-to-create-links"></a>如何建立連結
建立的連結**記錄**或**欄位**來源結構描述中的節點**記錄**或是**欄位**目的結構描述中的節點是最基本建立對應的活動。 本主題提供此活動數個變化的逐步指示，包括建立運算質的連結。 如需有關使用運算質的詳細資訊，請參閱[更加建立複雜的對應使用運算質](../core/using-functoids-to-create-more-complex-mappings.md)。  
  
 本主題中的指示假設您已開啟 BizTalk 對應，且您已選擇對應的來源與目的結構描述。 如需有關開啟對應以及選擇對應結構描述的詳細資訊，請參閱 < [Managing 對應內 Projects](../core/managing-maps-within-projects.md)。  
  
### <a name="to-create-links-between-field-and-record-nodes"></a>建立欄位和記錄節點之間的連結  
  
1. 在 BizTalk 對應工具中，拖曳**欄位**或**記錄**從來源結構描述樹狀結構節點**欄位**或**記錄**目的結構描述的節點樹狀結構。  
  
    **-或者-**  
  
2. 在 BizTalk 對應工具中，拖曳**欄位**或**記錄**節點從目的結構描述樹狀結構，以**欄位**或是**記錄**來源結構描述中的節點樹狀結構。  
  
   建立連結時必須考慮以下事項：  
  
-   資料類型**欄位**或**記錄**來源結構描述樹狀結構中的節點應該符合的資料型別**欄位**或是**記錄**它的節點已連結在目的結構描述樹狀結構中。  
  
-   如果**欄位**或是**記錄**來源結構描述中的節點是選擇性的與特定的來源執行個體訊息不包含對應的項目或屬性，BizTalk 對應工具將不會建立對應項目或屬性，在目的地執行個體訊息中，即使**欄位**或是**記錄**節點有其間對應中的直接連結。  
  
-   您無法連結到**欄位**或是**記錄**具有與其相關聯的常數值與目的結構描述的節點。 相反地，您可以連結至包含所需**欄位**或是**記錄**與其相關聯的預設值到目的結構描述的節點。 不過，請注意當您測試對應時，將會使用預設值。  
  
-   您無法建立連結，或從**Any 項目**， **Any 屬性**， **Sequence 群組**，或**Choice 群組**節點。 如需這些類型的節點的詳細資訊，請參閱下列主題，請參閱 < [Any 項目節點](../core/any-element-nodes.md)， [Sequence 群組節點](../core/sequence-group-nodes.md)或是[Choice 群組節點](../core/choice-group-nodes.md)。  
  
-   您可能需要展開結構描述樹狀結構以檢視您要對應的欄位。 如需詳細資訊，請參閱 <<c0> [ 如何展開和摺疊結構描述樹狀結構](https://msdn.microsoft.com/library/ee253802(v=bts.10).aspx)。  
  
#### <a name="to-create-links-between-record-or-field-nodes-and-functoids"></a>建立記錄或欄位節點與運算質之間的連結  
  
1.  在 BizTalk 對應工具中，拖曳**記錄**或是**欄位**格線頁中運算質從來源或目的結構描述的節點。  
  
     **-或者-**  
  
2.  從格線頁，以將運算質**記錄**或**欄位**來源或目的結構描述中的節點。  
  
     當您建立之間的連結**記錄**或是**欄位**來源結構描述和運算質中的節點，您會建立該運算質的輸入。 當您建立之間的連結**記錄**或是**欄位**目的結構描述和運算質中的節點，您會從該運算質建立輸出。  
  
    > [!IMPORTANT]
    >  您無法連結運算質之間及**Any 項目** 節點或有**Any 屬性**節點。  
  
    > [!NOTE]
    >  您必須先新增運算質至格線頁之間的連結新增之前**記錄**或是**欄位**節點與該運算質。 如需新增運算質至格線頁的詳細資訊，請參閱[如何新增基本運算質加入至地圖](../core/how-to-add-basic-functoids-to-a-map.md)。 另請參閱[新增進階運算質至對應](../core/adding-advanced-functoids-to-a-map.md)。  
  
    > [!NOTE]
    >  您無法連結到**欄位**具有與其相關聯的常數值與目的結構描述的節點。 相反地，您可以連結至包含所需**欄位**與其相關聯的預設值到目的結構描述的節點。 不過，請注意當您測試對應時，將會使用預設值。  
  
#### <a name="to-create-links-between-functoids"></a>建立運算質之間的連結  
  
-   在 BizTalk 對應工具中，將某個運算質拖曳至格線頁中的另一個運算質。  
  
    > [!NOTE]
    >  格線頁中的連結是由左向右處理。 您無法建立從某個運算質連至其正上方或正下方的另一個運算質的連結。 運算質之間的連結將解譯為某個連結表示從運算質往左的輸出，及往右到運算值的輸入。  
  
### <a name="to-change-the-endpoint-of-a-link"></a>變更連結的端點  
 在對應中，您可以拖曳連結的端點並放在另一個節點或運算質上。  
  
 若要變更連結的端點：  
  
1. 按一下您要變更來源或目的地節點/運算質的連結。 連結的端點變成粗體。  
  
2. 按住滑鼠上的索引鍵的任何粗體的端點，並將所需的節點/運算質的連結。 這會變更至新的節點/運算質從先前的節點/運算質連結。  
  
   不過，您無法執行這項作業無效連結，例如：  
  
-   將連結加入做為日期/時間運算質的輸入。 日期/時間運算質不需要任何輸入的連結。  
  
-   複製與中繼的運算質的連結。  
  
     如果到 Node2，以及從 Node1 到 Node3 連結 Node1，您就無法變更，並將連結到 Node3 Node2 在拖曳連結的端點。  
  
## <a name="see-also"></a>另請參閱  
 [使用連結指定記錄和欄位對應](../core/using-links-to-specify-record-and-field-mappings.md)