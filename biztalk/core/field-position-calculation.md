---
title: 欄位位置計算 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7e315f09-f2c9-49cc-8d2f-0f4f2d48fd45
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 55c58f532ea64300518667d677d2248f5c1c2b6b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246070"
---
# <a name="field-position-calculation"></a>欄位位置計算

## <a name="overview"></a>概觀
當您使用**Positional Length**和**Positional Offset**屬性**欄位項目**和**欄位屬性**節點中的您結構描述以定義在一般檔案訊息中，序數記錄的版面配置**開始位置**和**長度**的資料行**一般檔案** 索引標籤BizTalk 編輯器 中顯示的導出的起始位置和長度，分別相關欄位及記錄。  
  
> [!NOTE]
>  **一般檔案** 索引標籤會顯示為替代索引標籤式檢視與 XSD 檢視在 BizTalk 編輯器 中，當您完成設定一般檔案延伸模組使用**Schema Editor Extensions**屬性**結構描述**節點。 這個屬性的詳細[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
 一般而言，特定欄位的開始位置*N*是前一個欄位中，開始位置，加上前一個欄位中，加上您指定的欄位 （位置） 位移的長度*N*.  
  
 在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的所有欄位位置計算會即時自動執行，完全不需要執行命令 (在舊版 BizTalk Server 中則需要)。  
  
## <a name="see-also"></a>另請參閱  
-  [位置記錄的考量](../core/positional-record-considerations.md)   
-  **Positional Length （一般檔案結構描述中的節點屬性）** 和**Positional Offset （一般檔案結構描述中的節點屬性）**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]