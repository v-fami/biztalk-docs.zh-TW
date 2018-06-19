---
title: 如何自動連結記錄 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc2926c7-07c2-45d1-afde-d3f894f6b88d
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc5ab4e18a291321247655101d32d2bf7e35ff92
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254846"
---
# <a name="how-to-link-records-automatically"></a>如何自動連結記錄
當您在來源與目的結構描述的兩個記錄項目間建立連結時，BizTalk 對應工具可透過捷徑功能表為您提供即時的協助。 本主題提供如何使用捷徑功能表來執行連結作業的相關資訊。  
  
 您可以使用下列方式來自動建立記錄與記錄間的連結：  
  
-   **直接連結。** 使用此技術，BizTalk 對應工具會將來源結構描述中的記錄連結到目的結構描述中的選定記錄。  
  
-   **依結構連結。** 使用這項技術，BizTalk 對應工具會嘗試比對**記錄**和**欄位**節點內**記錄**節點所根據的那些結構連結**記錄**節點，不論這些結構內之相對應節點的名稱。  
  
-   **依名稱連結。** 使用這項技術，BizTalk 對應工具會嘗試比對**記錄**和**欄位**節點內**記錄**根據名稱所連結的節點在對應節點，不論其結構，**記錄**所連結的節點。  
  
-   **大量複製。** **大量複製**運算質可讓您使用包含的結構描述的對應**任何**和**anyAttribute**項目。 提供在 BizTalk 對應工具運算質的詳細資訊，請參閱[更加建立複雜的對應使用運算質](../core/using-functoids-to-create-more-complex-mappings.md)。  
  
 若要使用捷徑功能表，必須有個連結源自某個子階層父節點，並且終於另一個子階層父節點。 捷徑功能表的作用，在於協助您判斷在兩個結構描述節點之間應建立哪種類型的連結。 以下是捷徑功能表上可用的選項清單。  
  
|對應自|對應至|連結行為|  
|--------------|------------|-------------------|  
|欄位|欄位|直接連結|  
|記錄|欄位|直接連結|  
|欄位|記錄|直接連結|  
|記錄|記錄|會出現捷徑功能表|  
  
## <a name="prerequisites"></a>必要條件  
 這些作業需要執行中的 BizTalk 對應工具。  
  
### <a name="to-link-the-record-elements-directly"></a>若要直接連結記錄項目  
  
1.  從來源結構描述的子階層父節點拖曳滑鼠，然後在目標結構描述的子階層父節點放開滑鼠。  
  
2.  在捷徑功能表，按一下 **直接連結**。 下圖顯示隨即出現的從所選來源節點到目標節點的直接連結。  
  
     ![從來源節點至目標節點的直接連結](../core/media/linkrecordelements-directly.gif "Linkrecordelements_directly")  
  
    > [!IMPORTANT]
    >  您可以建立從來源結構描述的子階層父節點，到目標結構描述的非子階層父節點的直接連結。 下圖顯示從 “Root” (來源結構描述的父節點) 到 “Record1” (目標結構描述中 “Root” 的子項) 的直接連結。  
  
     ![直接連結記錄元素](../core/media/linkrecordelements-directly2.gif "Linkrecordelements_directly2")  
  
### <a name="to-link-the-record-elements-by-structure"></a>若要依結構來連結記錄項目  
  
1.  從來源結構描述的子階層父節點拖曳滑鼠，然後在目標結構描述的子階層父節點放開滑鼠。  
  
2.  在捷徑功能表，按一下 **依結構連結**。 BizTalk 對應工具符合**記錄**和**欄位**節點內**記錄**節點的結構根據要進行連結**記錄**節點，不論這些結構內之相對應節點的名稱。  
  
     ![連結記錄項目) (&#95; 結構](../core/media/linkrecordelements-bystructure.gif "Linkrecordelements_bystructure")  
  
    > [!IMPORTANT]
    >  當您嘗試將來源結構描述的子階層父節點連結到目標結構描述的非子階層父節點時，BizTalk 對應工具會依結構，將來源父節點的子項，分別對應到目標父節點的子項。 下圖顯示依結構進行的連結。  
  
     ![依結構連結記錄元素](../core/media/linkrecordelements-bystructure2.gif "Linkrecordelements_bystructure2")  
  
### <a name="to-link-the-record-elements-by-name"></a>若要依名稱來連結記錄項目  
  
1.  從來源結構描述的子階層父節點拖曳滑鼠，然後在目標結構描述的子階層父節點放開滑鼠。  
  
2.  在捷徑功能表，按一下 **依名稱連結**。 BizTalk 對應工具會嘗試比對**記錄**和**欄位**節點內**記錄**根據對應的節點名稱，不論所連結的節點其結構的內**記錄**您要連結的節點。  
  
     ![依名稱連結記錄元素](../core/media/linkrecordelements-byname.gif "Linkrecordelements_byname")  
  
    > [!IMPORTANT]
    >  您可以將來源結構描述的子階層父節點，依名稱連結到目標結構描述的非子階層父節點。 BizTalk 對應工具會將來源節點子項與目標節點子項的名稱進行對應。 如果找到相同的子項，就會在相應的子項之間建立連結。 下圖說明此概念。  
  
## <a name="to-link-using-a-mass-copy-functoid"></a>若要使用大量複製運算質來進行連結  
 **大量複製**運算質可讓您使用包含的結構描述的對應**任何**和**anyAttribute**項目。 這些項目實際上是以 XML 結構描述定義語言提供的萬用字元對應未知的結構或屬性。  
  
 除了處理具有未知結構的資料**大量複製**運算質可讓您簡化結構描述開發： 需要詳細指定只將處理結構描述的部分。  
  
 ![依大量複製運算質連結記錄元素](../core/media/linkrecordelements-masscopyfunctoid.gif "Linkrecordelements_MassCopyfunctoid")  
  
 如需有關**大量複製**運算質，請參閱[大量複製運算質](../core/mass-copy-functoid.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用連結指定記錄和欄位對應](../core/using-links-to-specify-record-and-field-mappings.md)   
 [如何新增大量複製運算質至對應](../core/how-to-add-mass-copy-functoids-to-a-map.md)