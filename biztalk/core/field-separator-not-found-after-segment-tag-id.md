---
title: "欄位的分隔符號，區段標記識別項後找不到 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f6f0a74-3560-4d6d-9893-85e8426e6b17
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 818a061cd723c0d8f8c58570c9e6df94a670942b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="field-separator-not-found-after-segment-tag-id"></a>欄位的分隔符號，區段標記識別項後找不到
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12SeFsNotFoundAfterTagIdDescription|  
|訊息文字|欄位的分隔符號，區段標記識別項後找不到|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法處理交換，因為交換所包含的區段時，它後面的資料元素分隔符號不具有區段識別項。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，確定交換中的所有區段識別項有資料元素分隔符號緊接，則需要重新傳送交換。