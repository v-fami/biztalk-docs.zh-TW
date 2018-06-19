---
title: 相互關聯類型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- correlation sets, correlation types
- correlation types, correlation sets
- correlation types
- validating, correlation types
- correlation types, about correlation types
- correlation types, validating
ms.assetid: 1aa5ca5c-c37d-4091-9f5d-331a6b202d4e
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3da5fad8cb4edc1d6a528f481616b4f10efb71d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22237774"
---
# <a name="correlation-types"></a>相互關聯類型
每個相互關聯集根據**相互關聯類型**，這是直接的屬性清單。 這些屬性可以是資料屬性 (存在於訊息本身中)，也可以是內容屬性 (描述與訊息中傳遞之資料無關的系統或訊息詳細資料)。  
  
 您可以在一個以上的相互關聯集中使用相互關聯類型。 如果您必須在相互關聯類型中的不同屬性值上相互關聯，則必須建立新的相互關聯集 (每個相互關聯集只能初始化一次)。  
  
 您可以升級屬性結構描述中的屬性，宣告訊息中的某個屬性可由您的協調流程存取。 如需詳細資訊，請參閱[升級屬性](../core/promoting-properties.md)。  
  
> [!CAUTION]
>  未設定的系統定義屬性**BTS。CorrelationToken**與每個訊息相關聯。 引擎會在相互關聯訊息中使用這個屬性，加以設定可能導致協調流程遺失訊息。  
  
## <a name="validating-message-correlation-on-send-actions"></a>驗證傳送動作上的訊息相互關聯  
 您可以驗證您從協調流程所傳送之訊息的屬性，確保該訊息能反映其相互關聯集中的屬性。 根據預設，會停用此項驗證。 如需如何啟用此功能的資訊，請參閱[協調流程引擎的執行階段驗證](../core/runtime-validation-for-the-orchestration-engine.md)。