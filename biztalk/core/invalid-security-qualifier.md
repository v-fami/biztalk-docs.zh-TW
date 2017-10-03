---
title: "無效的安全性辨識符號 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dce36f4b-ab59-41c0-8b92-3020f6393db9
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f4d16b4295bd8d01f93db964d4e45e8363205ee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-security-qualifier"></a>無效的安全性辨識符號
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12Ta1InvalidSecurityQualifierDescription|  
|訊息文字|無效的安全性辨識符號|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為安全性辨識符號中 ISA03 欄位或 [UNB6.2] 欄位中的收件者參考密碼辨識符號不符合中的值列舉服務結構描述 (x12serviceschema BaseArtifacts.dll 中的 EdifactServiceSchema) 所建立。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定 ISA03 欄位或 [UNB6.2] 欄位符合其中一個服務結構描述所建立的列舉值。 重新傳送交換。