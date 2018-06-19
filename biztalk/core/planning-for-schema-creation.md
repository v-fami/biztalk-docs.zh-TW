---
title: 規劃建立結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4ecb9154-b457-4209-b9b9-572c186bf5e7
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60fc7a3cafb3f13a189383df70d4b9ea0bf98f54
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22264638"
---
# <a name="planning-for-schema-creation"></a>規劃建立結構描述
您可以使用結構描述以驗證要符合結構描述的訊息執行個體、定義如何雙向轉譯不同格式 (XML 和非 XML) 的執行個體訊息，以及定義如何將某個結構的 XML 執行個體訊息轉換為不同結構的 XML 執行個體訊息。 如需有關執行個體訊息轉譯與執行個體訊息轉換之間差別的詳細資訊，請參閱[轉換 vs。轉譯](../core/data-transformation.md)。  
  
 下表列出在「BizTalk 編輯器」中規劃建立結構描述時需要回答的一些問題。  
  
|規劃問題|建議|  
|-----------------------|--------------------|  
|我需要建立哪些結構描述？|為您將使用 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 處理的商務文件建立一份清單。 例如，這類清單可能包含訂單、發票、交貨確認等。 此清單還可能包含多份這種商務文件，例如當您從某個交易夥伴接收的訂單結構不同於從另一位交易夥伴接收的訂單結構時。|  
|我所傳送和接收的文件都已經以 XML 呈現嗎？|將您所傳送和接收的每個商務文件格式之相關資訊新增到文件清單中，不管是 XML 或分隔式或序數一般檔案格式等其他格式。|  
|在我的清單上建立結構描述有哪些可用的起點？|雖然有時建立結構描述是必要的，但建立結構描述比從其中一個支援的來源產生結構描述較困難。 若您的結構描述已經是以 XML 結構描述定義 (XSD) 語言呈現，便不需要再產生，您只要在「BizTalk 編輯器」中將它開啟即可。<br /><br /> 若您有格式正確的 XML 執行個體訊息、結構描述的文件類型定義 (DTD) 表示法或結構描述的 XML-Data Reduced (XDR) 表示法，就可以自動產生結構描述。 您可能需要使用「BizTalk 編輯器」精簡產生的結構描述，但要自己儲存部分工作。 逐步指示，請參閱 < 從非 XSD 來源產生結構描述 」 程序，在[建立 XML 訊息的結構](../core/how-to-create-schemas-for-xml-messages.md)。<br /><br /> 若您清單上的一或多個商務文件都無法使用這些起點，您必須使用「BizTalk 編輯器」建立新的結構描述並定義其結構。|  
  
## <a name="see-also"></a>另請參閱  
 [如何建立 XML 訊息的結構描述](../core/how-to-create-schemas-for-xml-messages.md)   
 [使用 BizTalk 編輯器建立結構描述](../core/creating-schemas-using-biztalk-editor.md)