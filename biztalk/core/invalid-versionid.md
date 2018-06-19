---
title: 無效的 VersionId |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 563af6e8-f496-46c9-8b5f-7b941b2d08a5
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5edd2dddc5df19d99c434ec60cad46664ba378e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22261902"
---
# <a name="invalid-versionid"></a>無效的 VersionId
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12Ta1InvalidVersionIdDescription|  
|訊息文字|無效的 VersionId|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換，因為交換中的版本識別項 (GS08 欄位中的 X12 交換] 或 [EDIFACT 交換中的 [UNG7] 欄位) 不提供支援符合的資料類型和服務結構描述 (x12serviceschema BaseArtifacts.dll 中的 EdifactServiceSchema) 所建立的數字的數目。 GS08 欄位必須是 X12_AN 資料類型，而且介於 1 到 12 的數字。 UNG7.1 中的版本必須是 EDIFACT_AN 資料類型，而且介於 1 到 3 的數字。 EDIFACT_AN 資料型別且 1 和 3 個數字之間，必須是 UNG7.2 中的發行。 關聯指派碼 UNG7.3 中的必須是 EDIFACT_AN 資料類型，而且介於 1 到 6 的數字。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定在 GS08 或 UNG7 版本符合的資料類型和服務結構描述所指定的位數，而且再重新傳送交換。