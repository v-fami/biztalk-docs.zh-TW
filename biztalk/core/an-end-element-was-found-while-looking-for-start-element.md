---
title: 尋找開始元素時找不到結束項目 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7690744-a795-47cc-bc66-a0314a4cc320
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9dacaa096b15a6f2969ed56b5bac2138876a6095
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22229958"
---
# <a name="an-end-element-was-found-while-looking-for-start-element"></a>尋找開始元素時找到結尾元素
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|EndElementFoundWhenLookingForStartElement|  
|訊息文字|找到名稱為 {0} EndElement，尋找與名稱 {1}，在深度 {2} StartElement 時|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，BizTalk Server 無法處理內送 XML 訊息 （之後剖析） 或外寄 XML 訊息 （在之前序列化） 因為 XML 訊息驗證失敗。 XML 訊息不包含標頭或資料元素的結束標記。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，將適當的結束標記或結尾加入 XML 訊息，然後再重新傳送訊息。