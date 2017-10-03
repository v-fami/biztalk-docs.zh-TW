---
title: "無效的日期 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a41da9c5-9dcf-44cd-be5b-922e6c267ec3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 259456e781f5f5255f9fed8a51c8eb0569dd57b4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-date"></a>無效的日期
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12DeInvalidDateDescription|  
|訊息文字|無效的日期|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示接收管線無法處理內送交換，或傳送管線無法處理外寄交換，因為資料元素中的 date 值不符合所指定之資料類型EDI 結構描述或 GS04 欄位標頭服務結構描述不符合交換的 X12 中的日期值 (BaseArtifacts.dll 中的 X12ServiceSchema)。 對於 X12，服務結構描述會定義日期為準，X12_DT 資料類型和長度為六個到八個字元之間的 GS04 欄位中。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定的時間中的資料元素的值符合 EDI 結構描述或 GS04 標頭的 X12 交換服務，符合結構描述中的日期值所指定的資料型別，然後重新傳送交換。