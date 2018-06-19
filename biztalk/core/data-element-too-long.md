---
title: 資料元素太長 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf608cc1-d482-4e19-8f56-10d9e03feb79
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fbfe63fccc442c35411bfae04c7f27629ce066ce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238262"
---
# <a name="data-element-too-long"></a>資料元素太長
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|-|  
|訊息文字|資料元素太長|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 接收管線或 EDI 傳送管線無法處理內送交換，因為資料元素的結構描述所指定的最大長度超過。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請縮短不太長，因此它低於上限的交換中的資料元素。 若要判斷最大長度，\XSD_Schema 資料夾中開啟結構描述、 搜尋資料的項目識別碼，並識別 maxLength 值為何。