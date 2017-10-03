---
title: "相互關聯集 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- correlation sets, inspecting
- correlation sets, about correlation sets
- correlation sets, passing as parameters
- messages, correlation sets
- correlation sets
- correlation sets, following correlation sets
- correlation sets, initializing
ms.assetid: 528dcd6c-d364-4bb8-8deb-cd4a0791867f
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 28d11e5e174808ca7718d5fef98b3ad079cffc18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="correlation-sets"></a>相互關聯集合
您可以定義相互關聯集合以達成訊息與協調流程執行個體的相互關聯。 相互關聯集是一組屬性*具有特定值*。 這是相互關聯類型，也就是只是一份屬性不同。 如果傳入的訊息沒有所有這些屬性，並在每個屬性都有相符的值，相互關聯便會失敗，而且訊息也不會由協調流程執行個體所接收。  
  
 相互關聯類型定義屬性的集合，您會在此集合上使訊息相互關聯。 這些可以是先前在屬性結構描述中定義，以及使用某些 BizTalk 專案部署的屬性，其中包括以 GlobalPropertySchemas (安裝為基本 BizTalk 安裝的一部分) 部署的「系統」屬性， 相互關聯集合會定義一組屬性以及這些屬性的值，訊息必須包含這個組合才可以交由特定的協調流程處理。  
  
 例如，相互關聯類型可能由下列屬性組成：  
  
|相互關聯類型屬性|可能的 XML 表示法|  
|-------------------------------|---------------------------------|  
|社會安全碼|\<SSN >\</SSN >|  
|生日|\<DOB >\</DOB >|  
|Gender|\<性別 >\<性別/>|  
  
 衍生自此相互關聯類型的相互關聯集合則可能由下列屬性與值組成：  
  
|相互關聯集合屬性/值|可能的 XML 表示法|  
|-------------------------------------|---------------------------------|  
|社會安全碼 = 222112222|\<SSN > 222112222\</SSN >|  
|生日 = “1/1/1995”|\<DOB >"1/1/1995"\</DOB >|  
|性別 = 男|\<性別 > M\<性別/>|  
  
> [!NOTE]
>  每個相互關聯集合最多可支援三個參數。  
  
## <a name="initializing-correlation-sets"></a>初始化相互關聯集合  
  
-   **接收動作上初始化的相互關聯集**  
  
     在接收動作上初始化的相互關聯集合會定義必須存在於發佈訊息中的確切屬性組，以便使其由協調流程中的對應接收動作處理。 初始化的相互關聯集合會根據文件中的對應值，從相互關聯類型建立相互關聯集合。  
  
-   **傳送動作上初始化的相互關聯集**  
  
     在傳送動作上初始化的相互關聯集合會根據文件中的對應值，從相互關聯類型建立，並會升級在輸出文件中的相互關聯屬性。  
  
## <a name="following-correlation-sets"></a>沿用相互關聯集合  
 沿用相互關聯集合只能繫結至非啟動的接收動作或傳送動作。 沿用相互關聯集合是在與先前初始化之相互關聯集合的匯接中指定的。  
  
-   **繫結至接收動作的沿用相互關聯集**  
  
     繫結至接收動作的沿用相互關聯集合會定義一組文件必須包含的屬性及其值才能被接收。  沿用相互關聯集合的接收動作會接受包含先前初始化之相互關聯集合中屬性的文件。  
  
-   **繫結至傳送動作的沿用相互關聯集**  
  
     繫結至傳送動作的沿用相互關聯集合指示相互關聯集合中的屬性組會在輸出的文件中升級。  
  
## <a name="inspecting-correlation-sets"></a>檢查相互關聯集合  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供檢查相互關聯集合的能力。 您可以使用與下列相似的程式碼，在「運算式圖形」中檢查相互關聯集合：  
  
```  
MsgLen = Correlation_1(BTS.MessageLength);  
```  
  
 上述範例假設您已建立名為的變數**MsgLen**型別的**System.Int16**和您的協調流程包含相互關聯集具名**Correlation_1**. 如果您需要檢查由一個協調流程傳遞至另一個協調流程之相互關聯的值，檢查相互關聯集合這個功能相當有用。  
  
## <a name="passing-correlation-sets-as-parameters-to-orchestrations"></a>將相互關聯集合當做參數傳遞至協調流程。  
 您可以傳遞相互關聯當做*中*至其他協調流程的參數。