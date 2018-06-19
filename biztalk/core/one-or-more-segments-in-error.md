---
title: 一或多個區段發生錯誤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4ee86667-e72a-4f1b-8d5c-15ca710dbe5d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 340c722bc96ec8efdf2f48e6b40260aa5323e675
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263366"
---
# <a name="one-or-more-segments-in-error"></a>一或多個區段發生錯誤
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12TsOneOrMoreSegmentsInErrorDescription|  
|訊息文字|一或多個區段發生錯誤|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，來管理它們的結構描述不符合交換中的一個或多個區段。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，判斷哪一個區段中錯誤、 開啟結構描述控管該區段，並從該區段處於錯誤的結構描述判斷。