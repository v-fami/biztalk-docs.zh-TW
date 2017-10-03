---
title: "資料元素太短 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a22c0551-3262-476c-a6c6-2fd214331244
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 311c40d80f1299ce4abcf5f2e5aec5cac2681251
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="data-element-too-short"></a>資料元素太短
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|-|  
|訊息文字|資料元素太短|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 接收管線或 EDI 傳送管線無法處理內送交換，因為資料元素已短於結構描述所指定的最小長度。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，延長已太短，所以大於最小長度的交換中的資料元素。 若要判斷最小長度，\XSD_Schema 資料夾中開啟結構描述、 搜尋資料的項目識別碼，並識別 minLength 值為何。