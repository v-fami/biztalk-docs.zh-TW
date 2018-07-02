---
title: 在 分隔記錄中標記處理 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 568eb804-bea5-46d4-8547-8bc30b87156c
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c50a3daad9bb77ba4a9cbc264f018e29601edfff
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972463"
---
# <a name="tag-handling-in-delimited-records"></a>在分隔記錄中處理標記

## <a name="overview"></a>概觀
分隔記錄可包含熟知的字元順序 (稱為標記)，可用來區別記錄中的不同類型。 這可讓一般檔案解譯器適當地識別 適當**記錄**結構描述中包含正確剖析一般檔案記錄所需的節點。  

 您可以使用**標記識別項**屬性，以指定分隔記錄中的標記。 與位置記錄中的標記不同，分隔記錄中的標記必須出現在分隔記錄的開頭，且在記錄轉譯為對等的 XML 格式時，自動排除在資料外。  

## <a name="see-also"></a>另請參閱  
- [分隔記錄考量](../core/delimited-record-considerations.md)   
- **標記識別項 （一般檔案結構描述中的節點屬性）** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
