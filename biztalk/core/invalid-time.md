---
title: 無效的時間 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6942eb77-3ef1-460c-ac4f-8f1339c25d1b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aae508a945cc6934e83408b2a9b78c324947e0e8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22261974"
---
# <a name="invalid-time"></a>無效的時間
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12Ta1InvalidTimeDescription|  
|訊息文字|無效的時間|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換的 EDI 結構描述或 GS05 欄位標頭在 X12 中的時間值所指定的資料類型不符合時間值中的資料元素因為服務結構描述不符合交換 (BaseArtifacts.dll 中的 X12ServiceSchema)。 對於 X12，服務結構描述會定義時間為準，X12_TM 資料類型，及介於四到八個字元的長度 GS05 欄位中。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定時間，資料元素中的值符合 EDI 結構描述或 GS05 標頭的 X12 交換服務，符合結構描述中的時間值所指定的資料型別，然後重新傳送交換。