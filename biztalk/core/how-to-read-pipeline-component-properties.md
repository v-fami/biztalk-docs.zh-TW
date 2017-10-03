---
title: "如何讀取管線元件屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: pipeline components, properties
ms.assetid: 10b1c59c-7ba4-453f-9aaa-1ce9ecf31fac
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 19a6ccbcbe7588a0a75b4dbe6bf821a19fab965c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-read-pipeline-component-properties"></a>如何讀取管線元件屬性
元件的 [屬性] 視窗包含兩個部分：一般屬性和元件屬性。 一般屬性為所有元件通用，不過，其值則依元件的不同各異。  
  
### <a name="to-read-the-general-properties-for-a-pipeline-component"></a>讀取管線元件的一般屬性  
  
1.  將管線元件拖曳至管線的某個階段中，或選取管線中已經存在的元件。  
  
2.  在 [屬性] 視窗中**一般**區段中，執行下列動作。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|指示元件名稱。|  
    |**組件**|指示元件的組件與關聯的 .NET 資訊。|  
    |**說明**|指示管線元件的易記名稱。|  
    |**受管理**|指示管線元件是否受管理。 **[是]**如果元件為.NET 受管理的元件。**否**如果管線元件是 COM 元件。|  
    |**路徑**|指示 .NET 元件的完整路徑。|  
    |**型別**|指示元件的元件類型、組件以及關聯的 .NET 資訊。|  
  
## <a name="see-also"></a>另請參閱  
 [設定原生管線元件](../core/configuring-native-pipeline-components.md)   
 [使用管線設計師建立管線](../core/creating-pipelines-with-pipeline-designer.md)