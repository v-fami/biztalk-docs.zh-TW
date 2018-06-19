---
title: 找不到對應至批次的商務識別 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1c9baf11-e9c6-482d-a47d-aa99852939bf
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f1027186e5b001d21e08bbabcfc100400a02d5f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22237830"
---
# <a name="could-not-find-business-identities-corresponding-to-batch"></a>找不到和批次對應的商務識別
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|IdentitiesNotFoundForBatch|  
|訊息文字|找不到和批次 {0} 對應的商務識別。|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，由於資料不足，因此 BizTalk Server 無法處理批次訊息。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確認含指定識別碼的批次存在內含協議的 [協議] 屬性中，同時也已為協議指定合適的商務識別。