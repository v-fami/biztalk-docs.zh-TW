---
title: "文件參考 URL 節點 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Document Reference URL nodes [Tracking Profile Editor]
- Tracking Profile Editor, node descriptions
- definition files [BAM], related documents
ms.assetid: 38c8ae50-ed56-451c-9549-db852d4770e5
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c7939a7e74483b8df192530fd9da2deafeda0681
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="document-reference-url-nodes"></a>Document Reference URL 節點
Document Reference URL 節點存在於開發人員從知識工作者建立的觀察模型中匯入的活動定義檔。 Document Reference URL 節點含有與此活動關聯之文件所在位置的參考。 這可以是任意類型的文件，例如，如果是代表訂單核准工作流程的活動，則 Document Reference URL 可能指向基礎訂單文件。  
  
## <a name="working-with-document-reference-url-nodes"></a>使用 Document Reference URL 節點  
 Document Reference URL 的資料來源通常是**MessageRefURL** BizTalk Server 系統屬性。 您也可以使用儲存 URL 的自訂結構描述，再從自訂結構描述將該屬性對應至 Document Reference URL。  
  
 Document Reference URL 的相關注意事項：  
  
-   您可以新增一或多個 Document Reference URL，但每個節點在活動中必須具有唯一名稱。  
  
-   **MessageRefURL**填入 Document Reference URL 節點所需的屬性只能填入值，如果是 WSS、 FILE 和 FTP 傳輸配接器。  
  
-   雖然商務使用者可以從 BAM 入口網站檢視此參考，但是參考 URL 的主要用途是讓自訂使用者介面的開發人員能夠存取關聯的文件資訊，以便向使用者呈現這些資訊。  如需檢視 BAM 入口網站中的文件參考的詳細資訊，請參閱[相關文件](../core/related-documents.md)。  
  
## <a name="see-also"></a>另請參閱  
 [TPE 活動檢視節點](../core/tpe-activity-view-nodes.md)