---
title: "不正確的 Doctype |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67233aae-65c0-4689-a4b3-60a48132343a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fec7dc4f2dfed0c8e8b8fcde13593d4e29997f7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="doctype-is-invalid"></a>文件類型不正確
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|EDI 引擎|  
|符號名稱|DocTypeInvalidFormat|  
|訊息文字|Doctype {0} 無效。 不可能決定一或多個命名空間、 版本或交易集識別碼|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 EDI 接收管線無法處理內送的交換，因為結構描述不正確地探索到。  
  
 對於 X12，目標命名空間由決定在 「 啟用自訂交易集定義 方格中的 x12 交換處理屬性頁面的 EDI 屬性 對話方塊。 訊息中的 GS02 和 ST01 值必須符合資料列的方格中，為了正確識別目標命名空間中。 在 內送交易集識別的目標命名空間中新增的版本 （GS08 的前五個字元） 和文件類型 (ST01) 時，會建立用於交易集的結構描述名稱。  
  
 對於 EDIFACT，目標命名空間是由決定在 「 啟用自訂交易集定義 方格中的 EDI 屬性 對話方塊的 EDIFACT 交換處理屬性頁面。 訊息中的 UNH2.1、 UNH2.2、 UNH2.3、 UNH2.5、 UNG2.1 和 UNG2.2 值必須符合資料列的方格中，為了正確識別目標命名空間中。 UNH2.2、 UNH2.3、 在訊息版次號碼和中的訊息類型 UNH2.1 中內送交易集識別的目標命名空間中新增訊息版本號碼會建立要用於交易集的結構描述名稱。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行作業，如下所示：  
  
1.  請在 「 啟用自訂交易集定義 方格中的資料列，交換處理屬性頁面的 EDI 屬性 對話方塊的正確識別交易集的結構描述的命名空間。 如果沒有，則變更方格中的值。  
  
2.  如果已正確識別命名空間，判斷用來識別結構描述的值是否正確。 對於 X12，它們是版本 （GS08 的前五個字元） 和內送交易集的文件類型 (ST01)。 對於 EDIFACT，它們是 UNH2.2、 UNH2.3、 在訊息版次號碼和訊息類型 UNH2.1 中內送交易集的訊息版本號碼。 如果值不正確，讓傳送者的交易集變更的值，這些欄位，然後再重新傳送訊息。