---
title: 在深度找不到結束項目 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a1edb60a-122a-4fe9-8d73-96521fe7326b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a90265b4348e4d35b66099f426b6f6177851ccc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22229910"
---
# <a name="an-end-element-could-not-be-found-at-depth"></a>在深度找不到結束項目
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|EndElementNotFoundAtDepth|  
|訊息文字|找不到結尾處的項目深度 {0}|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，BizTalk Server 無法處理外寄交換的 XML 訊息驗證失敗。 XML 訊息不包含標頭或資料元素的結束標記。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，將適當的結束標記或結尾加入 XML 訊息，然後再重新傳送。