---
title: 必要的資料元素遺失 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 510d54b3-13de-4735-92ec-04fd4b9d460e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b0c2d415b977c069e351d90fa5ad68b430c3f2f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262262"
---
# <a name="mandatory-data-element-missing"></a>遺失必要的資料元素
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12DeMandatoryDataElementMissingDescription|  
|訊息文字|遺失必要的資料元素|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，由於內送 X12 交換中不含訊息結構描述 (minOccurs 大於 0) 需要的資料元素，因此接收管線無法處理該交換。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定此交換包含所需的訊息結構描述中的資料元素，並再有訊息重新傳送。