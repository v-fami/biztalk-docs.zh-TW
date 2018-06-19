---
title: 結構描述 Validation1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 599f1bbb-2af5-4278-8b0f-0e5a6517e8e3
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20224a77530139a97647d91b0b46f9384d6c2753
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268790"
---
# <a name="schema-validation"></a>結構描述驗證
如果 BizTalk 編輯器 」 延伸模組提供**ISchemaValidator**物件時，架構會叫用**ISchemaValidator.ValidateSchema**當使用者叫用**驗證結構描述**命令，或在使用者建置包含結構描述的 BizTalk 專案的編譯期間。 延伸模組通常會驗證的自訂屬性，並將錯誤訊息傳回做為陣列的**IValidationInfo**物件。 錯誤訊息會顯示在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] [工作清單] 視窗中，包含從 BizTalk 編輯器編譯器傳回的錯誤。  
  
## <a name="see-also"></a>另請參閱  
 [延伸 BizTalk 編輯器](../core/extending-biztalk-editor.md)