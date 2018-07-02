---
title: 欄位可以重複執行個體產生--期間發生錯誤，但未定義重複分隔符號 |Microsoft Docs
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
ms.openlocfilehash: c6e5ed96162adac55de0bda042a12d45b4243eef
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971143"
---
# <a name="error-encountered-during-instance-generation--field-can-repeat-but-repetition-delimiter-has-not-been-defined"></a>欄位可以重複的執行個體產生--期間發生錯誤，但未定義重複分隔符號
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                       |
|-----------------|-----------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                   |
| 產品版本 |                              [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                               |
|    事件識別碼     |                                                           -                                                           |
|  事件來源   |                [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                 |
|    元件    |                                                      將 EDI 引擎                                                       |
|  符號名稱  |                                                           -                                                           |
|  訊息文字   | 執行個體產生期間發生的錯誤。 欄位{0}可以重複，但未定義重複分隔符號。 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 無法產生的 X12 訊息執行個體，因為指定的欄位可以重複 （如所指定的結構描述），但尚未定義任何重複分隔符號。 會發生這種情況是當結構描述中的欄位有 minOccurs 等於 1 個以上，但已定義的標準識別項，而不是重複分隔符號。 （若為 EDIFACT 交換重複分隔符號定義預設。）  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請選取重複分隔符號，而不是標準的識別碼 isa11 ISA 區段定義 頁面中做為交換接收者的合作對象的輸入做為分隔符號的字元。 如果沒有合作對象已解析的交換，定義為重複分隔符號的全域屬性的 [ISA 區段定義] 頁面中 （對於 X12 交換）。