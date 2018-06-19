---
title: 欄位可以重複執行個體產生-期間發生錯誤，但尚未定義重複分隔符號 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c7a6783c-cb35-4ce8-9164-ec34ae500de1
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 366caec69fd84b91cf815a58e4975e8e5d7b4d06
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22290102"
---
# <a name="error-encountered-during-instance-generation--field-can-repeat-but-repetition-delimiter-has-not-been-defined"></a>欄位可以重複執行個體產生-期間發生錯誤，但尚未定義重複分隔符號
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|-|  
|訊息文字|執行個體產生期間發生錯誤。 欄位 {0} 可以重複，但尚未定義重複分隔符號。|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 無法產生的 X12 訊息執行個體，因為指定的欄位可以重複 （如指定結構描述），但尚未定義任何重複分隔符號。 發生這種情況的欄位結構描述中的有 minOccurs 等於超過 1，但已定義標準識別項，而非重複分隔符號。 （若為 EDIFACT 交換重複分隔符號定義預設。）  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，選取 重複分隔符號而非標準識別項 ISA11 ISA 區段定義 頁面中做為交換接收者的合作對象和輸入字元的分隔符號。 如果沒有合作對象已解析的交換，定義為重複分隔符號的全域屬性 [ISA 區段定義] 頁面中 （對於 X12 交換）。