---
title: 如何調整大小的結構描述選擇器，以及展開和摺疊結構描述樹狀結構 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 267ea17d-54fe-4031-a044-719606489f24
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 682077ffc044c3f293d5bf7f2d3c2a1d81a4c918
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993047"
---
# <a name="how-to-resize-the-schema-picker-and-expand-and-collapse-the-schema-trees"></a>如何調整大小的結構描述選擇器，以及展開和摺疊結構描述樹狀結構
開發 BizTalk 對應時，您往往需要展開和摺疊來源與目的結構描述樹狀結構，以顯示或隱藏各個結構描述節點。 本主題提供逐步指示來調整大小的結構描述選擇器，以及展開和摺疊結構描述樹狀結構。  

## <a name="resize-the-schema-picker"></a>調整大小的結構描述選擇器

當您建立地圖時，您會將來源結構描述和目的結構描述。 當您新增或取代結構描述時，[BizTalk 型別選擇器] 視窗隨即開啟，並選取您的結構描述。 

**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** ，您可以調整此型別選擇器 視窗的大小。 這項功能可讓您查看您的結構描述的完整名稱。

1. 在對應中，選取**開啟目的結構描述**，或**開啟來源結構描述**。
2. 在 [ **BizTalk 型別選擇器**] 視窗中，拖曳右下角，以增加或減少的視窗大小。
  
## <a name="expand-all-or-part-of-a-schema-tree"></a>展開所有或部分結構描述樹狀結構  
  
1.  選取要完全展開其結構描述樹狀結構的節點。  
  
     選取的節點旁必須有加號 (+) 或減號 (-) 圖示。  
  
2.  在  **BizTalk**功能表上，或在該節點的捷徑功能表，按一下 **展開樹狀結構節點**。 所選節點下的所有節點都會完全展開。  
  
     所選節點下的結構描述樹狀結構已經完全展開，如果**展開樹狀結構節點**功能表項目已停用。  
  
    > [!NOTE]
    >  或者，您也可以按 CTRL+M、E 展開結構描述樹狀節點。 如需鍵盤快速鍵的清單，請參閱 < [BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。  
  
    > [!NOTE]
    >  大型且複雜結構描述中，當您按一下 **展開樹狀結構節點**節點上，其中包含複雜型別，結構描述中的某些節點可能會維持在摺疊的狀態。 這是因為此遞迴程序只會展開第一個出現的給定複雜型別， 您必須手動展開之後出現的相同型別。 這個行為的設計目的是要在大型和複雜結構描述中展開節點時，讓效能最佳化。  
  
## <a name="collapse-all-or-part-of-a-schema-tree"></a>摺疊所有或部分結構描述樹狀結構  
  
1. 選取要完全摺疊其結構描述樹狀結構的節點。  
  
    選取的節點旁必須有加號 (+) 或減號 (-) 圖示。  
  
2. 在  **BizTalk**功能表上，或在該節點的捷徑功能表，按一下 **摺疊樹狀節點**。  
  
    所選節點下的所有節點都會完全摺疊。  
  
   > [!NOTE]
   >  或者，您也可以按 CTRL+M、C 摺疊結構描述樹狀節點。 如需鍵盤快速鍵的清單，請參閱 < [BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。  
  
    如果所選節點下的結構描述樹狀結構已經完全摺疊，**摺疊樹狀節點**功能表項目已停用。  
  
   這項作業不會記得個人在所選節點下做出的節點展開和摺疊設定。 當您重新展開已摺疊的節點時，先前的設定會遺失，而您必須依逐個節點展開該點下的結構描述樹狀結構，或完全展開。  
  
### <a name="expand-a-node"></a>展開節點
  
- 按一下要展開之節點旁的加號 (+) 圖示。  
  
  就會展開選取的節點。 其底下的節點是展開還是摺疊，視選取的節點當初摺疊的方式，以及先前的展開和摺疊設定而異。  
  
### <a name="collapse-a-node"></a>摺疊節點
  
- 按一下要摺疊之節點旁的減號 (-) 圖示。  
  
  就會摺疊選取的節點。  
  
  這項作業會記得個人在所選節點下做出的節點展開和摺疊設定。 當您使用加號 (+) 圖示重新展開已摺疊的節點時，先前的個人設定不會遺失，而該節點下的結構描述樹狀目錄會回到先前的狀態。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk 對應工具](../core/using-biztalk-mapper.md)