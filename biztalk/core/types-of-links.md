---
title: 類型的連結 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- compiler directives, links
- elastic links [maps]
- maps, links
- BizTalk Mapper, links
- partial links [maps]
- fixed links [maps]
ms.assetid: 348fae77-2e25-4b79-93bb-d42f3d18a3f7
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f2eb8d5546698cc611072ccff1e9f0bf4abf9a2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009607"
---
# <a name="types-of-links"></a>連結的類型
下列清單摘要敘述可在「BizTalk 對應工具」中使用的各種連結類型：  
  
- **彈性連結。** 「彈性」這個詞表示這個連結已建立但兩邊端點尚未連接。 例如，當您從來源結構描述的欄位拖曳連結，但尚未連接到其在目的結構描述的對應欄位時，該連結就是彈性連結。 當您完成整個連接時，此彈性連結就變成固定連結。  
  
   您可以將連結的其中一個端點拖曳至另一個節點或運算質。 如需連結取代的詳細資訊，請參閱[如何建立連結](../core/how-to-create-links.md)。  
  
- **固定連結。** 「固定」這個詞是指連結已明確建構以代表某值從某來源執行個體訊息移動到目的執行個體訊息，或至少部分代表該移動的特性。 固定直接連接的連結**記錄**或**欄位**來源結構描述中的節點**記錄**或是**欄位**目的地中的節點結構描述代表直接複製資料在執行階段。 從端點或是另一個端點連接到運算質的固定連結，可代表資料在執行階段時從輸入執行個體訊息到輸出執行個體訊息的移動部分。 透過幾個這類連結共同構成來源與目的結構描述之間的連結，便可以代表資料項目的整個移動部分。  
  
- **部分連結。** 部分字詞套用至連結，您無法為其目前看到的確切**記錄**或是**欄位**將它們所連接的來源或目的結構描述中的節點。 發生這種情況時**記錄**或是**欄位**所連接的節點不會顯示因為結構描述樹狀結構表示法中摺疊的其中一個上階節點。 如需部分連結的詳細資訊，請參閱[如何最佳化連結顯示的](../core/how-to-optimize-the-display-of-links.md)。  
  
- **編譯器連結。** 「編譯器」這個詞是指建置 BizTalk 專案時，BizTalk 對應工具自動建立連結的特性。 例如，當您設定表格驅動迴圈時，編譯器連結會顯示分別位於來源結構描述和目的結構描述之記錄和欄位之間的關係和連結。 這類連結可以依編譯器指示詞自動產生，或是由使用者指示產生。  
  
  依照預設，BizTalk 對應工具會應用不同顏色的線條顯示這些不同類型的連結，協助您辨識對應的詳細資料。 您可以變更用於這些不同類型的連結色彩**選項**命令**工具**功能表。 如需有關如何變更的色彩呈現不同連結類別的詳細資訊，請參閱 <<c0> [ 如何自訂色彩和字型，在 BizTalk 對應工具](../core/how-to-customize-colors-and-font-in-biztalk-mapper.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用連結指定記錄和欄位對應](../core/using-links-to-specify-record-and-field-mappings.md)