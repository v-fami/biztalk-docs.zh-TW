---
title: 如何插入 Any 項目或 Any 屬性節點 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4cbfdc04-6c83-4639-82de-169b6f009a2e
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8bce55126fe800841aef325f22de0afe62e03cec
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37021073"
---
# <a name="how-to-insert-an-any-element-or-any-attribute-node"></a>如何插入 Any 項目或 Any 屬性節點
BizTalk 編輯器支援兩種 any 節點： **Any 項目**並**Any 屬性**。 這些節點可讓您建立您的結構描述對應至您不知道什麼項目或屬性會出現在對應的執行個體訊息中位置的位置。 如需有關處理執行個體訊息時如何解譯這些節點的詳細資訊，請直接參考網站上 XML 結構描述定義 (XSD) 語言的相關資訊。 如需這項資訊的連結，請參閱[網站上的 XSD 資源](../core/xsd-resources-on-the-web.md)。  

## <a name="insert-an-any-element-node-or-an-any-attribute-node"></a>插入 Any 項目或 Any 屬性節點  

1.  在結構描述樹狀結構檢視中，選取**記錄**想要插入的節點**Any 項目**節點或**Any 屬性**節點。  

2.  上**BizTalk**功能表上，指向**插入結構描述節點**，然後按一下**Any 項目**或是**Any 屬性**視需要。  

> [!IMPORTANT]
>  設定**Process Contents**屬性設**Lax** for **Any 項目**或是**Any 屬性**節點可能無法正確運作。 通過驗證**Any 項目**或是**Any 屬性**節點，將屬性設定為**略過**。  這個屬性的更多有關[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
> 
>  若要建立包含地圖**Any 項目**或**Any 屬性**節點，您必須使用[大量複製](mass-copy-functoid.md)運算質或[指令碼處理](scripting-functoid.md)運算質 （與內嵌 XSLT 或內嵌 XSLT 呼叫範本） 來執行這類節點中，對應，或直接不對應這些節點。  

## <a name="see-also"></a>另請參閱  
- [將節點插入至結構描述](../core/inserting-nodes-into-a-schema.md)
- **運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
