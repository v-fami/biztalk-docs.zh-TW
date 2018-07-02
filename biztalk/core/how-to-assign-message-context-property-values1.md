---
title: 如何指派訊息內容屬性 Values1 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7e76c62-3110-482c-8083-84d411e6f475
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4f9f5a42e208d81f8898ce85592402f675d1b361
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979739"
---
# <a name="how-to-assign-message-context-property-values"></a>如何指派訊息內容屬性值
若要從 BizTalk 協調流程管理 JD Edwards EnterpriseOne 配接器連接工作階段，則必須在專案中加入對 Microsoft.BizTalk.Adapters.JDEProperties.dll 的參照。 這個組件位於 %SystemDrive%\Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\bin。  
  
 在參考這個屬性結構描述之後，即可讓各種 BizTalk 開發工具存取其他的內容屬性。例如，在「協調流程設計師」內的「訊息指派」圖形。  
  
 若要存取內容屬性，則必須在 JD Edwards EnterpriseOne 命名空間內指定其中一個可用的內容屬性。 若要讀取已繫結至 Microsoft BizTalk Adapter for JD Edwards EnterpriseOne 之連接埠所接收訊息的內容屬性，請在運算式中使用 Message(JDE.Property) 的語法。 如需屬性清單，請參閱「JD Edwards EnterpriseOne 配接器工作階段管理」。  
  
 在 BizTalk 中，訊息都是不變的。  
  
### <a name="to-assign-context-property-value"></a>若要指派內容屬性值  
  
1. 建立新的訊息。  
  
2. 設定訊息內容，例如，藉由指派現有的訊息。  
  
3. 設定屬性。  
  
   若要為目的地為已繫結至 Microsoft BizTalk Adapter for JD Edwards EnterpriseOne 之傳送埠的訊息指派內容屬性，請使用訊息指派運算子。 然後在 JD Edwards EnterpriseOne 命名空間內指定其中一個可用的內容屬性。  
  
   語法是： `Message(JDE.Property) = value;`  
  
## <a name="see-also"></a>另請參閱  
 [使用訊息內容屬性](../core/using-message-context-properties1.md)   
 [關於工作階段管理](../core/about-session-management2.md)   
 [教學課程：使用 BizTalk Adapter for JD Edwards EnterpriseOne](../core/tutorial-using-the-biztalk-adapter-for-jd-edwards-enterpriseone.md)