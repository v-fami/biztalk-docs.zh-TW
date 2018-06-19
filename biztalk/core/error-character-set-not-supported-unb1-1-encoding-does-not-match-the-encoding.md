---
title: 不支援，因為 UNB1.1 中的編碼資訊不符合實際的編碼字元集 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 085ea8e3-e0d8-45bd-9985-6787b00e4d5a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41a6eafbb0e71de5f13e792361cdc0d1fc338088
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239902"
---
# <a name="character-set-not-supported-because-the-encoding-information-in-unb11-does-not-match-the-actual-encoding"></a>因為 UNB1.1 中的編碼資訊不符合交換的實際編碼，不支援字元集
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|-|  
|訊息文字|不支援字元集。 這可能是因為 UNB1.1 中的編碼資訊不符合交換的實際編碼。|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，由於在內送 EDIFACT 交換中使用的字元和在交換之 [UNB1.1] 欄位中識別的字元集不符，因此 EDI 接收管線無法處理該交換。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列其中一項：  
  
-   變更讓它們符合指定的字元集中欄位 UNB1.1 交換的交換中使用的字元。  
  
-   變更指定的字元集中的交換，UNB1.1 欄位以便交換中的所有字元都是組件的字元集。