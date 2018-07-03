---
title: 無效的 Doctype |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67233aae-65c0-4689-a4b3-60a48132343a
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0676653df3124de72740a18c1d29b58f9282f684
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001847"
---
# <a name="doctype-is-invalid"></a>無效的 Doctype
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                 |
|-----------------|-----------------------------------------------------------------------------------------------------------------|
|  產品名稱   |               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                |
| 產品版本 |                           [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                            |
|    事件識別碼     |                                                        -                                                        |
|  事件來源   |             [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI              |
|    元件    |                                                   將 EDI 引擎                                                    |
|  符號名稱  |                                              DocTypeInvalidFormat                                               |
|  訊息文字   | Doctype{0}無效。 不可能決定一或多個命名空間、 版本或交易集識別碼 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 接收管線無法處理內送的交換，因為結構描述無法正確探索到。  
  
 對於 X12，目標命名空間由決定在 「 啟用自訂交易集定義 方格中的 x12 交換處理屬性頁面的 EDI 屬性 對話方塊。 訊息中的 GS02 和 ST01 值必須符合方格中，以正確識別的目標命名空間的資料列中。 內送交易設定為指定的目標命名空間中新增的版本 （GS08 的前五個字元） 和文件類型 (ST01) 時，會建立要用於交易集結構描述名稱。  
  
 對於 EDIFACT，目標命名空間是由在 「 啟用自訂交易集定義 方格中 EDIFACT 交換處理屬性 頁面的 EDI 屬性 對話方塊中的決定。 訊息中 UNH2.1，UNH2.2，UNH2.3、 UNH2.5，UNG2.1 和 UNG2.2 值必須符合方格中，以正確識別的目標命名空間的資料列中。 UNH2.2、 訊息版次號碼，UNH2.3、 中的和訊息類型 UNH2.1 中的內送的交易集的目標命名空間中新增訊息版本號碼時，會建立要用於交易集結構描述名稱。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請執行下列步驟：  
  
1.  請確定交易集的結構描述的命名空間會正確識別的 「 啟用自訂交易集定義 方格中的 EDI 屬性 對話方塊中的 交換處理屬性 頁面的一個資料列。 否則，請變更方格中的值。  
  
2.  如果命名空間已被正確識別，判斷用來識別結構描述的值是否正確。 對於 X12，它們是版本 （GS08 的前五個字元） 和內送交易集的文件類型 (ST01)。 對於 EDIFACT，它們是 UNH2.2、 訊息版次號碼，UNH2.3、 中的和訊息類型 UNH2.1 中內送交易集的訊息版本號碼。 如果值不正確，讓傳送者交易集的變更這些欄位的值，然後再重新傳送訊息。