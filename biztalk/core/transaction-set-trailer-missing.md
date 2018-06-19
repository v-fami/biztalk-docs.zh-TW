---
title: 交易集結尾遺失 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 07753300-fe47-47a6-a947-6abec10c1c90
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7f1c153aa0bb62b6c62f4eeebf9d1fb9bea004b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279286"
---
# <a name="transaction-set-trailer-missing"></a>交易集結尾遺失
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|X12TsTrailerMissingDescription|  
|訊息文字|交易集結尾遺失|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，由於交易集不含 SE 交易集結尾 (針對 X12 交易集) 或 UNT 訊息結尾 (針對 EDIFACT 交易集)，因此接收管線無法處理內送交易集，亦或是傳送管線無法處理外寄交易集。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，有交易集合寄件者新增至交易集 SE 交易集結尾 (x12 交易集) 或 UNT 訊息結尾 （針對 EDIFACT 交易集），然後再重新傳送交易集。