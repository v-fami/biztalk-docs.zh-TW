---
title: "屬性管理員 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 823352a0-e397-464a-a163-1dbf8feea8d7
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6aff8fc39612ed79e6e9602ed39874d014bb4a11
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="property-managers"></a>屬性管理員
「屬性管理員」允許延伸模組將自訂屬性 (一般是 XSD 註解) 新增至結構描述的 XSD 表示法中的項目與屬性，也允許延伸 [屬性] 視窗，以包含與延伸模組相關聯的自訂屬性。  
  
 屬性管理員是一個物件，實作**[ipropertymanager]**介面，其參考透過呼叫**IExtension.GetPropertyManager**，並傳遞**[Itreenode]**物件做為輸入參數。 通常延伸模組會提供一個**[ipropertymanager]**物件給每個**[itreenode]**物件。 屬性管理員會負責的自訂屬性集合，該**[itreenode]**物件。  
  
 自訂屬性由**System.ComponentModel.PropertyDescriptor**物件，可以從所傳回的集合中取得**IPropertyManager.GetProperties**方法。  
  
 使用**PropertyDescriptor**物件，以表示延伸模組相關聯的自訂屬性有助於與 Microsoft 整合[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性 視窗。 當**PropertyDescriptor**物件使用，很容易 BizTalk 編輯器的整合已經整合到 [屬性] 視窗的標準節點屬性組中的擴充功能的自訂屬性。 例如顯示名稱、 顯示值、 屬性控制項類型、 屬性描述和屬性類別目錄的自訂屬性資訊取自**PropertyDescriptor**物件。  
  
 自訂屬性儲存在結構描述的 XSD 表示法中，做為對應至結構描述樹狀結構中相關節點的項目中註解項目內的項目屬性。 結構描述樹狀結構的每個自訂屬性都可以是通用項目的屬性，或者，每個自訂屬性都可擁有與其相關聯的項目。  
  
## <a name="see-also"></a>另請參閱  
 [延伸 BizTalk 編輯器](../core/extending-biztalk-editor.md)