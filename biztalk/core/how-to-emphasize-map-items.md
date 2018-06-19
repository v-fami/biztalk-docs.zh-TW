---
title: 如何強調對應項目 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2732b36-ca57-4566-ba26-da27a3082f32
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6bb03969a044c6a474f5d2d1c1e5e1a5067cf81
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
ms.locfileid: "22255438"
---
# <a name="how-to-emphasize-map-items"></a>如何強調對應項目
在 BizTalk 對應工具中，當您選取對應項目時，所有相關聯的連結和運算質都會強調顯示。 當對應含有許多連結，而令人難以識別關係和相關的結構描述項目時，這項功能非常有用。  
  
 當您選取連結、運算質或結構描述項目時，BizTalk 對應工具會強調顯示相關的關係和結構描述項目。 對於選取的對應項目而言，所有的連入連結和連出連結 (採用遞迴方式) 都會以粗體醒目顯示，而所有其他對應項目則會變成灰色。下列螢幕擷取畫面顯示選取的對應項目會變成彩色粗體，而其他對應項目會變得較不醒目。  
  
> [!NOTE]
>  在此情況下，相關的關係表示所有的連結、運算質或結構描述項目都直接或間接連結至選取的對應項目。  
  
 ![強調對應項目](../core/media/mapper-intelliselect.gif "Mapper_IntelliSelect")  
  
## <a name="prerequisites"></a>필수 구성 요소  
 此作業需要執行中的 BizTalk 對應工具。  
  
## <a name="to-emphasize-a-map-item"></a>若要強調顯示對應項目  
  
-   按一下對應項目 (連結、運算質或結構描述項目)。 您可以看見，與目前格線頁中所選對應項目相關聯的所有其他連結和運算質 (包括結構描述節點) 都已醒目顯示。  
  
     有時候，選取的節點可能會有關係存在於其他格線頁中。 在此情況下，BizTalk 對應工具會在目前格線頁中強調顯示此執行個體，同時醒目顯示選取的節點的其他關係所在的頁面索引標籤。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk 對應工具中的增強的功能](../core/using-enhanced-features-in-biztalk-mapper.md)