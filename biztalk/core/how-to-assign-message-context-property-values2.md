---
title: 如何指派訊息內容屬性 Values2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 137f82ab-f301-465d-be78-a6e67971dd3b
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f0e19a425a4842e3bfac150d1cac851e4686f17
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247206"
---
# <a name="how-to-assign-message-context-property-values"></a>如何指派訊息內容屬性值
若要從 BizTalk 協調流程管理 JD Edwards OneWorld 連接工作階段，您必須在專案中加入對 Microsoft.BizTalk.Adapters.JDEProperties.dll 的參照。 這個組件位於 %SystemDrive%\Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\bin。  
  
 在參考這個屬性結構描述之後，即可讓各種 BizTalk 開發工具存取其他的內容屬性。例如，在「協調流程設計師」內的「訊息指派」圖形。  
  
 若要存取某個內容屬性，您必須在 JD Edwards OneWorld 命名空間內指定其中一個可用的內容屬性。 若要讀取已繫結至 Microsoft BizTalk Adapter for JD Edwards OneWorld 之連接埠所接收訊息的內容屬性，請在運算式中使用 Message(JDE.Property) 的語法。 如需屬性的清單，請參閱 JD Edwards OneWorld 工作階段管理。  
  
 在 BizTalk 中，訊息都是不變的。  
  
### <a name="to-assign-a-message-context-property-value"></a>若要指派訊息內容屬性值  
  
1.  建立新的訊息。  
  
2.  設定訊息內容，例如，藉由指派現有的訊息。  
  
3.  設定屬性。  
  
 若要指派訊息到傳送埠繫結至 Microsoft BizTalk Adapter for JD Edwards OneWorld 內容屬性，請使用訊息指派運算子。 然後，指定其中一個可用的內容屬性中的 JD Edwards OneWorld 命名空間。  
  
 語法如下：`Message(JDE.Property) = value;`  
  
## <a name="see-also"></a>另請參閱  
 [使用訊息內容屬性](../core/using-message-context-properties2.md)   
 [關於工作階段管理](../core/about-session-management1.md)   
 [教學課程： 使用 BizTalk Adapter for JD Edwards OneWorld](../core/tutorial-using-the-biztalk-adapter-for-jd-edwards-oneworld.md)