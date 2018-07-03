---
title: 相關文件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- queries [BAM], document references
- definition files [BAM], related documents
- Query Builder [BAM portal], viewing details
- document references [BAM]
- Query Builder [BAM portal], document references
- queries [BAM], viewing details
ms.assetid: 9c5f2175-fe7c-40ec-910d-1ac5c8142045
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 56338d268bac6568f8e175b6e70da202715fd7a8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006729"
---
# <a name="related-documents"></a>相關文件
查詢結果詳細資料的 [相關文件] 區域會顯示活動相關參考文件的清單。 文件可以是任何類型，包括 CAD 影像、.WAV 檔案或訂單。 例如，「訂單」活動通常以「訂單」做為基本的文件類型。 其清單中包含訂單的連結。  
  
## <a name="adding-document-references"></a>新增文件參考  
 相關文件的清單是由下列兩種方式之一產生：  
  
- 開發追蹤設定檔時，在活動樹狀結構中納入 Document Reference URL 節點，再將該節點從含有參考指標的來源對應到實際文件。  
  
- 整合開發人員以程式設計的方式，呼叫自訂應用程式以填入清單內容。  
  
  定義使用其中一種方法的文件參考中加入資料列\<activityname\>_References 資料表具有文件的位置。  
  
  如果已執行任一這些工作，**相關文件**區域則為空白。  
  
## <a name="see-also"></a>另請參閱  
 [追蹤設定檔編輯器](../core/tracking-profile-editor.md)